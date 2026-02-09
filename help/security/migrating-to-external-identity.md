---
title: Migreren naar externe identiteit en dynamisch groepslidmaatschap
description: Technische handleiding voor het migreren van lokale gebruikers en groepen naar een extern identiteitsmodel met dynamisch groepslidmaatschap in AEM as a Cloud Service
solution: Experience Manager Sites
feature: Security
role: Developer, Admin
source-git-commit: 1f8bd9eea249e0b2242f3fbe1490b3d51052f546
workflow-type: tm+mt
source-wordcount: '2232'
ht-degree: 0%

---

# Migreren naar externe identiteit en dynamisch groepslidmaatschap {#migrating-to-external-identity}

## Overzicht {#overview}

Wanneer [&#x200B; Synchronisatie van Gegevens &#x200B;](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization) in AEM as a Cloud Service wordt toegelaten, kan de manager van de Authentificatie van SAML worden gevormd om automatisch aan externe identiteiten met dynamisch groepslidmaatschap te migreren wanneer het gebruiker en groepsverwezenlijking beheert. Als uw project douanecode gebruikt om gebruikers of groepen tot stand te brengen, moet u het bijwerken om externe gebruikers en groepen tot stand te brengen, in tegenstelling tot lokale gebruikers en groepen.

### Waarom externe gebruikers en groepen vereist zijn {#why-external-required}

Om verschillende kritieke redenen is het van essentieel belang om van lokale gebruikers en groepen te migreren naar externe identiteiten met een dynamisch groepslidmaatschap:

**Optimalisering van Prestaties:**

* **Verminderde Bewaarplaats schrijft**: Het traditionele lokale groepslidmaatschap vereist het schrijven van lidmaatschapsverhoudingen aan de bewaarplaats in één enkel multi-getaxeerd bezit van de groepsknoop. Met dynamisch groepslidmaatschap hebben gebruikers één `rep:externalPrincipalNames` -eigenschap die alle groepshoofden bevat, zodat de groepsnode niet hoeft te worden gesynchroniseerd
* **Snellere Synchronisatie**: Wanneer het synchroniseren van gebruikers over publiceer de knopen van de rij, vereisen de externe gebruikers met dynamisch groepslidmaatschap beduidend minder gegevensoverdracht en minder schrijven verrichtingen in vergelijking met lokale gebruikers met traditionele groepslidmaatschappen
* **Schaalbaarheid**: De systemen met grote aantallen gebruikers en groepen profiteren dramatisch van verminderde bewaarplaats overheadkosten. Dynamisch groepslidmaatschap wordt efficiënt geschaald, zelfs met zeer grote groepen.

Dit document bevat technische richtsnoeren voor:

* Het externe identiteitsmodel begrijpen
* Aangepaste code wijzigen om externe gebruikers en groepen te maken
* Bestaande lokale gebruikers en groepen migreren naar het externe identiteitsmodel

## Externe identiteit {#understanding-external-identity}

### Externe gebruikers {#external-users}

Externe gebruikers worden geïdentificeerd door de eigenschap `rep:externalId` , die de gebruiker koppelt aan een externe identiteitsprovider. De indeling is:

```
userId;idpName
```

Bijvoorbeeld: `john.doe;saml-idp` .

>[!NOTE]
>
> `idpName` verwijst naar de naam van de Oak Identity Provider (Id), zoals gedefinieerd in de configuratie van de verificatiehandler. Voor integratie SAML, is dit de waarde die voor het `idpIdentifier` attribuut in de Handler van de Authentificatie van SAML wordt geplaatst.

**Zeer belangrijke Eigenschappen:**

* `rep:externalId`: Vereiste eigenschap die een gebruiker als extern markeert (bijvoorbeeld `john.doe;saml-idp`)
* `rep:externalPrincipalNames`: multi-value eigenschap met externe groepshoofden voor dynamisch lidmaatschap
* `rep:lastSynced`: Tijdstempel van laatste synchronisatie
* `rep:lastDynamicSync`: tijdstempel van laatste dynamische synchronisatie van groepslidmaatschap

### Externe groepen {#external-groups}

Externe groepen worden ook geïdentificeerd door de eigenschap `rep:externalId` en gebruiken een indeling voor de hoofdnaam:

```
groupId;idpName
```

Bijvoorbeeld: `content-authors;saml-idp`

### Dynamisch groepslidmaatschap {#dynamic-group-membership}

In plaats van directe user-to-group relaties die in de repository zijn opgeslagen, gebruikt dynamisch groepslidmaatschap de eigenschap `rep:externalPrincipalNames` op het gebruikersknooppunt. Wanneer een gebruiker een externe belangrijkste naam heeft die identiteitskaart van een externe groep aanpast, worden zij automatisch een lid van die groep. Voor meer informatie, zie de [&#x200B; documentatie van Apache Oak &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html).

**Voordelen:**

* Minder opbergingsbestanden (er worden geen knooppunten voor groepslidmaatschap gewijzigd wanneer gebruikers worden toegevoegd of verwijderd uit groepen)
* Snellere synchronisatie tussen knooppunten op publicatieniveau
* Schaalbaar groepslidmaatschapsbeheer
* Compatibel met de vereisten van de Synchronisatie van Gegevens

## Gebruikersconfiguratie service {#service-user-configuration}

Alle verrichtingen die tot externe gebruikers en groepen leiden of wijzigen zouden moeten worden uitgevoerd gebruikend a **de dienstgebruiker** die behoorlijk wordt gevormd om de standaardbescherming op de `rep:externalId` en `rep:externalPrincipalNames` eigenschappen te mijden.

### Waarom is een Gebruiker van de Dienst vereist {#why-is-a-service-user-required}

Standaard voorkomt Oak-beveiliging dat tijdens normale sessies beschermde eigenschappen worden gewijzigd, zoals:

* `rep:externalId` - Hiermee markeert u gebruikers/groepen als extern
* `rep:externalPrincipalNames` - Hiermee worden de principes van dynamisch groepslidmaatschap opgeslagen

Slechts kan een behoorlijk gevormde de de dienstgebruiker deze eigenschappen wijzigen.

### Configuratie en toewijzing van servicegebruikers {#service-user-configuration-mapping}

Voor het instellen van een servicegebruiker voor het beheer van externe identiteiten zijn drie gecoördineerde configuraties vereist:

1. De servicegebruiker maken via `repoinit`
2. `ExternalPrincipal` -beveiliging configureren
3. Wijs de de dienstgebruiker aan uw toepassingsbundel toe.

Zie hieronder voor een uitgebreide beschrijving van deze stappen.

#### Stap 1: Creeer de Gebruiker van de Dienst via Repoinit {#create-the-serviice-user-via-repoinit}

In deze stap wordt beschreven hoe de servicegebruiker met de benodigde machtigingen een `repoinit` -script kan maken.

**Dossier van de Configuratie:** `org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json`

**de plaats van de Malplaatje:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "scripts": [
    "create service user group-provisioner with path system/yourproject",
    "set ACL for group-provisioner\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/users\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/groups\nend"
  ]
}
```

**Overzicht van Toestemmingen**

* `jcr:read`: Gebruikers en groepen lezen
* `jcr:readAccessControl`: ACL&#39;s lezen
* `jcr:modifyAccessControl`: wijzig ACLs (nodig voor het plaatsen van eigenschappen)
* `rep:userManagement`: Gebruikers/groepen maken en beheren
* `rep:write`: Schrijf eigenschappen inclusief `rep:externalId` en `rep:externalPrincipalNames`

>[!NOTE]
>
>De servicegebruiker wordt onder `/home/users/system/yourproject` gemaakt om deze te organiseren met andere systeemgebruikers.

#### Stap 2: ExternalPrincipal Protection configureren {#configure-externalprincipal-protection}

Hieronder ziet u een voorbeeldconfiguratie voor het whitelisteren van de servicegebruiker, zodat deze de beveiliging kan omzeilen die is toegepast op externe identiteitseigenschappen.

**het dossier van de Configuratie naam:** `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json`

**Plaats van het Voorbeeld:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "protectExternalIdentities": "Warn",
  "systemPrincipalNames": [
    "group-provisioner",
    "saml-migration-service"
  ]
}
```

**Eigenschappen van de Configuratie:**

* `protectExternalIdentities`: bepaalt het beschermingsniveau voor externe identiteitseigenschappen:
   * `"Strict"`: alleen systeemhoofden in de whitelist kunnen externe eigenschappen wijzigen. Dit is het aanbevolen niveau voor de productie.
   * `"Warn"`: meldt waarschuwingen, maar staat wijzigingen toe. Nuttig voor ontwikkeling/testen.
   * `"None"`: Geen beveiliging. Niet aanbevolen.
* `systemPrincipalNames`: Lijst met namen van servicegebruikers die `rep:externalId` en `rep:externalPrincipalNames` mogen wijzigen. Neem alle servicegebruikers op die externe identiteiten moeten beheren (bijvoorbeeld `group-provisioner`, `saml-migration-service` ).

>[!IMPORTANT]
>
>De namen van de servicegebruikers in `systemPrincipalNames` moeten exact overeenkomen met de gebruikers-id&#39;s van de service die zijn gemaakt in het script voor het opnieuw aanwijzen.

#### Stap 3: Toewijzing van gebruikers aan de service {#service-user-mapping}

Wijs de de dienstgebruiker aan uw toepassingsbundel toe zodat kan uw code het gebruiken.

**Dossier van de Configuratie:** `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json`

**Plaats:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "user.mapping": [
    "yourproject.core:group-provisioner=[group-provisioner]"
  ]
}
```

**het Formaat van de Afbeelding:**

* `yourproject.core`: De symbolische bundelnaam (vindt u in `pom.xml` `<Bundle-SymbolicName>` )
* `group-provisioner` (voor `=` ): De naam van de subservice die u in code wilt gebruiken
* `[group-provisioner]` (na `=`): De werkelijke gebruikers-id van de service die in repoinit is gemaakt

### De gebruiker van de Dienst in Code gebruiken {#using-the-service-user-in-code}

Wanneer u een sessie opent voor het uitvoeren van migratie of het maken van gebruikers/groepen, moet u de servicegebruiker gebruiken:

```java
import org.apache.sling.jcr.api.SlingRepository;

@Reference
private SlingRepository repository;

// Login as the service user
Session serviceSession = repository.loginService("group-provisioner", null);

try {
    UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
    // Perform operations...
    serviceSession.save();
} finally {
    if (serviceSession != null && serviceSession.isLive()) {
        serviceSession.logout();
    }
}
```

>[!IMPORTANT]
>
>Als de gebruikersconfiguratie van de service niet juist is, mislukken pogingen om `rep:externalId` of `rep:externalPrincipalNames` in te stellen met machtigingsfouten. Controleer of de servicegebruiker correct is geconfigureerd in de `ExternalPrincipal` -configuratie voordat u de migratie probeert uit te voeren.

## Voorbeeld van volledige configuratie {#complete-configuration-example}

Hieronder ziet u een volledig werkvoorbeeld waarin alle drie de configuraties samen worden getoond:

### Bestandsstructuur {#file-structure}

```
ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/
└── config.publish/
    ├── org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json
    ├── org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json
    └── org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json
```

### Aangepaste code wijzigen {#modifying-custom-code}

#### Externe gebruikers maken {#creating-external-users}

**vóór (Lokale Gebruiker):**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
User user = userManager.createUser(userId, password);
```

**na (Externe Gebruiker):**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create user with principal
Principal userPrincipal = new Principal() {
    @Override
    public String getName() {
        return userId;
    }
};

User user = userManager.createUser(userId, null, userPrincipal, null);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
String externalId = externalRef.getString(); // Format: userId;idpName
user.setProperty("rep:externalId", valueFactory.createValue(externalId));

// Set sync timestamps to far future (workaround for OAK-12079)
// Set to 10 years in the future to prevent premature cleanup of external group memberships
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));

session.save();
```

#### Externe groepen maken {#creating-external-groups}

**vóór (Lokale Groep):**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
Group group = userManager.createGroup(groupId);
```

**na (Externe Groep):**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create group with principal
Principal groupPrincipal = new Principal() {
    @Override
    public String getName() {
        return groupId;
    }
};

Group group = userManager.createGroup(groupPrincipal);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(groupId, idpName);
String externalId = externalRef.getString(); // Format: groupId;idpName
group.setProperty("rep:externalId", valueFactory.createValue(externalId));

session.save();
```

#### Dynamisch groepslidmaatschap toewijzen {#assigning-dynamic-membership}

**vóór (Directe Lidmaatschap):**

```java
Group group = (Group) userManager.getAuthorizable(groupId);
User user = (User) userManager.getAuthorizable(userId);
group.addMember(user);
```

**na (Dynamisch Lidmaatschap):**

```java
User user = (User) userManager.getAuthorizable(userId);
ValueFactory valueFactory = session.getValueFactory();

// Get existing external principal names
Value[] existingValues = user.getProperty("rep:externalPrincipalNames");
List<String> principalNames = new ArrayList<>();

if (existingValues != null) {
    for (Value value : existingValues) {
        principalNames.add(value.getString());
    }
}

// Add new principal name (format: groupId;idpName)
String dynamicGroupPrincipal = groupId + ";" + idpName;
if (!principalNames.contains(dynamicGroupPrincipal)) {
    principalNames.add(dynamicGroupPrincipal);
    
    // Create new Value array
    Value[] newValues = new Value[principalNames.size()];
    for (int i = 0; i < principalNames.size(); i++) {
        newValues[i] = valueFactory.createValue(principalNames.get(i));
    }
    
    // Set the property
    user.setProperty("rep:externalPrincipalNames", newValues);
    
    // Update sync timestamps to far future (workaround for OAK-12079)
    // Set to 10 years in the future to prevent premature cleanup of external group memberships
    // See: https://issues.apache.org/jira/browse/OAK-12079
    java.util.Calendar future = java.util.Calendar.getInstance();
    future.add(java.util.Calendar.YEAR, 10);
    user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
    user.setProperty("rep:lastSynced", valueFactory.createValue(future));
}

session.save();
```

## Migratieproces {#migration-process}

Het migreren van bestaande lokale gebruikers en groepen aan de externe identiteit wordt niet vereist wanneer de douanecode vóór het toelaten van de Diensten van de Synchronisatie van Gegevens werd bijgewerkt.

Als lokale gebruikers en groepen reeds in de bewaarplaats zijn voortgeduurd en het milieu actief wordt gebruikt, adviseren wij u een multi-step migratie als het volgende uit te voeren, om verstoringen of inconsistenties te vermijden.

>[!IMPORTANT]
>
>Alle migratiestappen moeten worden uitgevoerd met een correct geconfigureerde servicegebruiker (bijvoorbeeld `group-provisioner` ) die machtigingen heeft gekregen om de beveiliging voor `rep:externalId` - en `rep:externalPrincipalNames` -eigenschappen te omzeilen. Zie [&#x200B; de Configuratie van de Gebruiker van de Dienst van 0&rbrace; voor meer details.](#service-user-configuration)

### Stap 1: Externe groepsstructuur maken {#step-1-create-external-group-structure}

Voor elke lokale groep die moet worden gemigreerd:

1. Maak een corresponderende externe groep met de hoofdnaam: `<localGroupId>;<idpName>` . Een naamgevingsconventie gebruiken die externe groepen helpt te koppelen aan lokale groepen
1. Stel de eigenschap `rep:externalId` in op de externe groep met waarden: `<localGroupId>;<idpName>`
1. Voeg de externe groep toe als lid van de oorspronkelijke lokale groep.

**Bevestiging**

* U kunt de resultaten valideren door te controleren of elke lokale groep een corresponderende externe groep heeft. Bovendien is elke externe groep lid van de corresponderende lokale groep.

**Eindpunt van Servlet van het Voorbeeld:**

```java
@SlingServletPaths("/bin/migration/step1")
public class MigrationStep1Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String groupPath = request.getParameter("groupPath");
        String idpName = request.getParameter("idpName");

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Get local group
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        String localGroupId = localGroup.getID();
        
        // Create external group
        String externalGroupPrincipalName = localGroupId + ";" + idpName;
        // The function createExternalGroup performs the following steps:
        // 1. Creates a new external group with the given principal name (format: "<localGroupId>;<idpName>").
        // 2. Sets the 'rep:externalId' property on the group to mark it as an external group (value: "<localGroupId>;<idpName>").
        // 3. Sets the 'rep:principalName' property for the group if required.
        // 4. Assigns any other required group metadata, such as a title or description, if needed.
        // 5. Persists the new group node in the repository at the appropriate path under /home/groups.
        // 6. Returns the created Group object so it can be used for further operations, such as membership assignment.
        Group externalGroup = createExternalGroup(externalGroupPrincipalName, localGroupId, idpName);
        
        // Add external group to local group
        localGroup.addMember(externalGroup);
        
        session.save();
    }
}
```

**Gebruik:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/c/content-authors&idpName=saml-idp"
```

### Stap 2: Gebruikers converteren en dynamisch lidmaatschap toewijzen {#step-2-convert-users-and-assign-dynamic-membership}

Voor elke gebruiker die lid is van een lokale groep:

1. Verzeker het heeft `rep:externalId` plaats (zet in externe gebruiker om indien nodig).
1. Voor elk groepslidmaatschap, voeg het overeenkomstige externe groepshoofd aan `rep:externalPrincipalNames` toe
1. Synchroniseer tijdstempels.

>[!IMPORTANT]
>
>Sla systeemgroepen als &quot;iedereen&quot; tijdens dit proces over.

**Eindpunt van Servlet van het Voorbeeld:**

```java
@SlingServletPaths("/bin/migration/step2")
public class MigrationStep2Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String userId = request.getParameter("userId");
        String idpName = request.getParameter("idpName");
        
        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Login as the service user
        Session serviceSession = repository.loginService("group-provisioner", null);

        try {
            UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
            User user = (User) userManager.getAuthorizable(userId);
            
            // Ensure user has rep:externalId
            Value[] externalIdValues = user.getProperty("rep:externalId");
            if (externalIdValues == null || externalIdValues.length == 0) {
                ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
                user.setProperty("rep:externalId", 
                            valueFactory.createValue(externalRef.getString()));
            }
            
            // Get all group memberships
            Iterator<Group> groupIterator = user.declaredMemberOf();
            List<String> principalNames = new ArrayList<>();
            
            while (groupIterator.hasNext()) {
                Group group = groupIterator.next();
                String groupId = group.getID();
                
                // Skip system groups
                if ("everyone".equals(groupId)) {
                    continue;
                }
                
                // Add dynamic group principal
                String dynamicGroupPrincipal = groupId + ";" + idpName;
                principalNames.add(dynamicGroupPrincipal);
            }
            
            // Set rep:externalPrincipalNames
            if (!principalNames.isEmpty()) {
                Value[] newValues = new Value[principalNames.size()];
                for (int i = 0; i < principalNames.size(); i++) {
                    newValues[i] = valueFactory.createValue(principalNames.get(i));
                }
                user.setProperty("rep:externalPrincipalNames", newValues);
            }
            
            // Update timestamps to far future (workaround for OAK-12079)
            // Set to 10 years in the future to prevent premature cleanup of external group memberships
            // See: https://issues.apache.org/jira/browse/OAK-12079
            java.util.Calendar future = java.util.Calendar.getInstance();
            future.add(java.util.Calendar.YEAR, 10);
            user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
            user.setProperty("rep:lastSynced", valueFactory.createValue(future));
        
        // Perform operations...
        serviceSession.save();
    } finally {
        if (serviceSession != null && serviceSession.isLive()) {
            serviceSession.logout();
        }
}    }
}
```

**Gebruik:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step2?userId=john.doe&idpName=saml-idp"
```

**Bevestiging**

U kunt dit valideren door te controleren of elke gebruiker de kenmerken `rep:externalId` en `rep:externalPrincipalName` heeft met de naam `principalName` van elke externe groep. De gebruikers zijn lid van de lokale groepen *en* de van de externe groepen.

### Stap 3: Directe gebruikerslidmaatschappen verwijderen {#step-3-remove-direct-user-memberships}

Nadat gebruikers dynamisch groepslidmaatschap hebben gevormd:

1. Directe gebruikerslidmaatschappen uit lokale groepen verwijderen
1. Lidmaatschappen van groep tot groep behouden (inclusief het externe groepslidmaatschap)

**Eindpunt van Servlet van het Voorbeeld:**

```java
@SlingServletPaths("/bin/migration/step3")
public class MigrationStep3Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        String groupPath = request.getParameter("groupPath");
        
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        
        // Process each member
        Iterator<Authorizable> members = localGroup.getDeclaredMembers();
        
        while (members.hasNext()) {
            Authorizable member = members.next();
            
            // Remove only user members, keep group members
            if (!member.isGroup()) {
                localGroup.removeMember(member);
            }
        }
        
        session.save();
    }
}
```

**Gebruik:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/c/content-authors"
```

**Bevestiging**

* U kunt dit bevestigen door te controleren dat elke lokale groep slechts de overeenkomstige externe groep, of andere groepen, als lid heeft.


## Migratieworkflow {#migration-workflow}

### Controlelijst voor migratie {#pre-migration-checklist}

* **vormt de Gebruiker van de Dienst**: Creeer en vorm de de dienstgebruiker (bijvoorbeeld, `group-provisioner`) met juiste toestemmingen
* **verifieer Configuratie ExternalPrincipal**: Zorg ervoor de de dienstgebruiker wordt gevormd om bescherming op `rep:externalId` en `rep:externalPrincipalNames` te mijden
* **de Toestemmingen van de Gebruiker van de Dienst van de Test**: Verifieer de de dienstgebruiker externe identiteitseigenschappen in ontwikkeling kan plaatsen
* Alle aangepaste code identificeren waarmee gebruikers of groepen worden gemaakt
* Aangepaste code controleren en bijwerken om extern identiteitsmodel te gebruiken
* Bijgewerkte code in de ontwikkelomgeving testen
* Alle bestaande lokale gebruikers en groepen inventariseren voor migratie
* Het migratieproces testen in lagere omgevingen

### Uitvoeringsstappen {#execution-steps}

1. **stelt bijgewerkte Code** op: stel de veranderingen van de douanecode op om externe gebruikers/groepen tot stand te brengen

1. **creeer Externe Groepen** (voor elke lokale groep):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/g/my-group&idpName=saml-idp"
   ```

1. **Migreer Gebruikers** (voor elke gebruiker):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step2?userId=username&idpName=saml-idp"
   ```

1. **Schoonmaakbeurt** (voor elke gemigreerde groep):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/g/my-group"
   ```

1. **verifieer**: Het lidmaatschap van de gebruikersgroep van de controle en de toestemmingen van de testtoegang

1. **laat de Synchronisatie van Gegevens** toe: De Steun van de Klant van het contact om de eigenschap toe te laten

### Validatie na migratie {#post-migration-validation}

De migratie controleren:

1. **de Eigenschappen van de Gebruiker van de Controle**:

   Controleer op gebruikersknooppunten of:

   * `rep:externalId`: Indeling moet `userId;idpName` zijn
   * `rep:externalPrincipalNames`: Array van groepshoofden in indeling `groupId;idpName`
   * `rep:lastSynced`: Tijdstempel ingesteld op verre toekomst (ongeveer 10 jaar na migratiedatum)
   * `rep:lastDynamicSync`: Tijdstempel ingesteld op verre toekomst (ongeveer 10 jaar na migratiedatum)

   **Nota**: De timestamps worden opzettelijk geplaatst aan een verre toekomstige datum als tussenoplossing voor OAK-12079. Dit wordt verwacht.

1. **de Eigenschappen van de Groep van de Controle**:

   Controleer op lokale groepsknooppunten of:

   * Extern groeplid met opmaak `groupId;idpName`
   * Geen directe gebruikersleden (alleen na Stap 3)

1. **Login van de Gebruiker van de Test**: Verifieer de gebruikers kunnen login en correcte toestemmingen hebben

1. **Controle van de Toegang van de Test**: Verifieer de gebruikers tot inhoud kunnen toegang hebben die door CUGs/ACLs wordt beschermd

## Problemen oplossen {#troubleshooting}

### Vaak voorkomende problemen {#common-issues}

**Uitgave: machtigingsfouten bij het instellen van `rep:externalId` of`rep:externalPrincipalNames`**

**de Berichten van de Fout:**

* `javax.jcr.AccessDeniedException: Access denied`
* `OakAccess0000: Access denied`
* `Cannot set property 'rep:externalId'`

**Oplossing**: De zitting moet worden geopend gebruikend een behoorlijk gevormde de de dienstgebruiker die toestemmingen is verleend om bescherming op externe identiteitseigenschappen te omzeilen.

**Stappen om op te lossen:**

1. **verifieer de dienstgebruiker bestaat**: Zorg de de dienstgebruiker (b.v., `group-provisioner`) via repoinit wordt gecreeerd
1. **de dienstgebruikerstoewijzing van de Controle**: Verifieer servlet of de dienst `repository.loginService("group-provisioner", null)` gebruikt
1. **verifieer configuratie ExternalPrincipal**: Zorg ervoor `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration` behoorlijk wordt gevormd
1. **de toestemmingen van de de dienstgebruiker van de Controle**: De de dienstgebruiker vereist `rep:write` en `rep:userManagement` toestemmingen op `/home/users` en `/home/groups`

Zie [&#x200B; de Configuratie van de Gebruiker van de Dienst van 0&rbrace; voor volledige opstellingsinstructies.](#service-user-configuration)

**Uitgave:`OakConstraint0072: Property 'rep:externalPrincipalNames' requires 'rep:externalId' to be present`**

**Oplossing**: De gebruikers moeten `rep:externalId` plaatsen hebben alvorens `rep:externalPrincipalNames` te plaatsen. Zorg ervoor dat stap 2 eerst gebruikers naar externe gebruikers converteert.

**Uitgave: De gebruikers verliezen groepslidmaatschappen na migratie**

**Oplossing**: Verifieer dat:

* Externe groep is gemaakt met de juiste indeling voor de hoofdnaam (`groupId;idpName`)
* Externe groep is toegevoegd als lid van lokale groep (stap 1)
* Gebruiker heeft correcte externe belangrijkste namen in `rep:externalPrincipalNames` (Stap 2)
* De opruiming van stap 3 werd pas uitgevoerd nadat stap 1 en 2 waren voltooid

**Uitgave: De externe groepslidmaatschappen worden onverwacht verwijderd na gebruikerslogin (OAK-12079)**

**Probleem**: Wegens Oak insect [&#x200B; OAK-12079 &#x200B;](https://issues.apache.org/jira/browse/OAK-12079), kan het de synchronisatiemechanisme van Oak externe groepslidmaatschappen voortijdig opschonen die op `rep:lastSynced` en `rep:lastDynamicSync` worden gebaseerd timestamps.

**Oplossing**: Plaats `rep:lastSynced` en `rep:lastDynamicSync` timestamps aan een verre toekomstige datum (10 jaar van nu) in plaats van de huidige tijd. Hierdoor wordt voorkomen dat het synchronisatieproces het externe groepslidmaatschap verwijdert.

**Implementatie:**

```java
// Workaround for OAK-12079
// Set to 10 years in the future to prevent premature cleanup
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
```

**waarom dit** werkt: Door timestamps aan een verre toekomstige datum te plaatsen, behandelt de de synchronisatielogica van Oak deze gebruikers als &quot;onlangs gesynchroniseerd&quot;en activeert niet het schoonmaakproces dat de externe belangrijkste namen en groepslidmaatschappen zou verwijderen.

**Nota**: Dit is een tijdelijke oplossing tot OAK-12079 in een toekomstige versie van Oak wordt opgelost. Deze tijdelijke oplossing is al opgenomen in alle codevoorbeelden in dit document.

**Uitgave: De groep van het systeem &quot;iedereen&quot;veroorzaakt fouten**

**Oplossing**: Sla altijd de &quot;iedereen&quot;systeemgroep tijdens gebruikersmigratie (Stap 2) over. Deze groep wordt automatisch beheerd door AEM.

### Terugkeerprocedure {#rollback-procedure}

Als er zich bij migratie problemen voordoen:

1. Migratieproces stoppen
1. Herstellen vanaf back-up als dit van invloed is op kritieke gegevens
1. Draai de wijzigingen in de code terug om externe gebruikers en groepen met dynamisch groepslidmaatschap te maken
1. Bekijk en los problemen op voordat u de migratie opnieuw verstuurt.

## Aanbevolen procedures {#best-practices}

* **Test grondig**: Test altijd migratie in ontwikkeling en het opvoeren milieu&#39;s vóór productie
* **de Verwerking van de Partij**: Voor grote gebruikersbasen, proces migraties in partijen om onderbrekingskwesties te vermijden
* **Prestaties van de Monitor**: De prestaties van de controlebewaarplaats tijdens migratie
* **handhaaf het Spoor van de Controle**: Logboek alle migratieverrichtingen voor het oplossen van problemen
* **de Toestemmingen van de Gebruiker van de Dienst**: Verzeker migratieservers gebruik aangewezen de dienstgebruikers met vereiste toestemmingen. De gebruiker van de dienst moet in de configuratie ExternalPrincipal worden gevormd om bescherming op `rep:externalId` en `rep:externalPrincipalNames` eigenschappen te mijden
* **Verrichtingen van de emigratie van het ontwerp**: Veilig re-runable
* **bevestigt bij Elke Stap**: De resultaten van de controle na elke migratiestap alvorens te gaan

## Migratieservers beveiligen {#securing-migration-servlets}

De migratieserves hebben verhoogde voorrechten om gebruikers en groepen tot stand te brengen en te wijzigen. Het is van essentieel belang de toegang tot deze eindpunten te beperken om ongeoorloofde toegang te voorkomen.

### Aanbevolen aanpak: IMS Technical Account Authentication {#recommended-approach-ims-technical-account}

De aanbevolen methode is om deze servers te beveiligen met behulp van de integratie met Adobe IMS, zodat alleen een geautoriseerde technische account toegang heeft tot deze servers.

#### Stap 1: Een technische account maken in AEM Developer Console {#create-a-technical-account-in-aem-developer-console}

1. Navigeer aan [&#x200B; Experience Manager &#x200B;](https://experience.adobe.com/) en dan **Cloud Manager**
1. Selecteer uw programma en klik vervolgens in de omgeving waar u de technische account wilt maken
1. Klik **Developer Console** in het de ellips van het milieu menu
1. In AEM Developer Console, ga naar het **1&rbrace; lusje van de Integraties &lbrace;**
1. Klik **creëren nieuwe technische rekening**
1. Geef een naam op voor de integratie (bijvoorbeeld &quot;Migratieserviceaccount&quot;)
1. Klik **creëren**
1. Maak een notitie van de volgende waarden uit de gemaakte integratie:
   * **identiteitskaart van de Cliënt**
   * **Geheim van de Cliënt**
   * **Technische identiteitskaart van de Rekening** (dit zal gebruiker - identiteitskaart zijn die tot uw servlets toegang heeft - formaat: `XXXXXXXXXXXXXXXXXXXXXXXX@techacct.adobe.com`)

Voor gedetailleerde instructies, zie [&#x200B; Genererend de Tokens van de Toegang voor server-zij APIs documentatie &#x200B;](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

Voorbeeldcode om te controleren of de aanroeper is geautoriseerd:

```
    private boolean isAuthorizedCaller(SlingHttpServletRequest request, 
                                       SlingHttpServletResponse response) {

        Session session = request.getResourceResolver().adaptTo(Session.class);
        String callerId = session != null ? session.getUserID() : null;
               
        if (!ALLOWED_TECHNICAL_ACCOUNT.equals(callerId)) {
            LOG.warn("Unauthorized access attempt by user: '{}' (expected: '{}')", callerId,   ALLOWED_TECHNICAL_ACCOUNT);
            response.setStatus(SlingHttpServletResponse.SC_FORBIDDEN);
            return false;
        }
        
        return true;
    }
```

### Verdediging in Diepte: IP-Gebaseerde Beperkingen {#defense-in-depth-ip-based-restrictions}

Als extra laag van veiligheid, kunt u CDN regels vormen om toegang tot migratieeindpunten door IP adres te beperken. Dit is nuttig wanneer de migraties van bekende infrastructuur worden in werking gesteld.

>[!NOTE]
>
>IP-beperkingen alleen zijn niet voldoende. Altijd combineren met verificatiecontroles zoals hierboven beschreven.

### Beveiligingscontrolelijst {#security-checklist}

Voordat u migratieserves naar productie gaat implementeren:

* IMS-integratie maken in AEM Developer Console
* Serlets configureren om de technische account-id te valideren
* Verificatiestroom testen in ontwikkelings-/testomgevingen
* Overweeg extra op IP-Gebaseerde beperkingen op CDN niveau
* Plan om migratieserlets uit te schakelen of te verwijderen nadat de migratie is voltooid
* Alle toegang tot migratie-eindpunten controleren en registreren

>[!IMPORTANT]
>
>Nadat de migratie is voltooid, kunt u overwegen de migratieserves uit uw implementatie te schakelen of te verwijderen om elk mogelijk beveiligingsrisico te elimineren.

## Aanvullende bronnen {#additional-resources}

* [User and Group Sync for Publish Tier](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md)
* [&#x200B; SAML 2.0 de Handler van de Authentificatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html)
* [&#x200B; Externe Leverancier van de Identiteit &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html)
* [&#x200B; Dynamisch Lidmaatschap van de Groep &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html)
