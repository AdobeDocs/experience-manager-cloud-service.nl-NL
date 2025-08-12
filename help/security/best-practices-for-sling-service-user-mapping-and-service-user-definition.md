---
title: Beste praktijken voor het Verkopen van de Toewijzing van de Gebruiker van de Dienst en de Definitie van de Gebruiker van de Dienst
description: Meer informatie over de beste werkwijzen voor het toewijzen van servicegebruikers en het definiëren van gebruikersdefinities voor services
exl-id: 72f0dcbf-b4e6-4a73-8232-3574a212ac19
feature: Security
role: Admin
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1883'
ht-degree: 0%

---

# Beste praktijken voor het Verkopen van de Toewijzing van de Gebruiker van de Dienst en de Definitie van de Gebruiker van de Dienst {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## Toewijzing van servicegebruikers {#service-user-mapping}

Als u een toewijzing van uw service aan de overeenkomstige systeemgebruiker(s) wilt toevoegen, moet u een fabrieksconfiguratie voor de service `ServiceUserMapper` maken. Om dit modulair te houden, kunnen dergelijke configuraties worden verstrekt gebruikend het Verschuiven &quot;wijzigt&quot;mechanisme (zie [ SLING-3578 ](https://issues.apache.org/jira/browse/SLING-3578) voor meer details). U kunt dergelijke configuraties het beste met uw bundel installeren door deze toe te voegen aan het Quickstart-inrichtingsmodel, zoals in het volgende voorbeeld wordt beschreven:

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### Toewijzingsindeling {#mapping-format}

Sinds AEM 6.4 wordt het toewijzingsformaat als volgt gedefinieerd:

>[!NOTE]
>
>`userName` is afgekeurd en mag niet meer worden gebruikt.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` en `subserviceName` identificeer de service, `userName/principalNames` identificeer de servicegebruiker en `principalNames` is een door komma&#39;s gescheiden lijst.

Houd er ook rekening mee dat `principalNames` de lijst is met hoofdnamen van servicegebruikers die uit het vak komen, gelijk zijn aan de id.


**Beste praktijken**

* Subservicenamen voor verschillende taken - als de services van uw bundel verschillende taken uitvoeren, wordt aangeraden `subserviceNames` te identificeren om deze te groeperen op taken
* Als een bepaalde service verschillende bewerkingen uitvoert (bijvoorbeeld de inhoud van elementen lezen en informatie bijwerken onder een substructuur van `/var`), wordt u aangeraden dit te weerspiegelen door verschillende serviceprincipes samen te voegen die de afzonderlijke bewerking weerspiegelen, zoals het samenvoegen van de algemene `dam-reader-service` met uw functiespecifieke `assetreport-writer-service` .
* Elke dienst is idealiter verbindend aan een zeer specifieke en beperkte reeks verrichtingen
* De nieuwe indeling met `[one,or,multiple,principalNames]` is de aanbevolen manier om servicetoewijzingen te definiëren vanaf AEM 6.4.

Hieronder vindt u een lijst met redenen waarom u de opmaak wilt wijzigen en waarom Adobe u aanraadt deze te gebruiken in plaats van de versietoewijzing alleen voor één gebruiker-id:

* De capaciteit om de dienstgebruikers te hergebruiken door de speciale behoeften van klanten met gemeenschappelijke taken te combineren
* Vermijd dubbel instellen van machtigingen
* Een beter inzicht in de effectieve machtigingen (en taken) die een bepaalde service uitvoert
* Geen behoefte aan expliciete groepslidmaatschap van de dienstgebruikers. Dit kan lastige bijwerkingen hebben wanneer de groepsmachtigingen veranderen
* Prestatieverbeteringen en schaalbaarheid

## Toewijzingsresolutie en aanmelding voor service {#mapping-resolution-and-service-login}

### Oplossing voor servicetoewijzing {#service-mapping-resolution}

De opeenvolging van vraag om de hieronder beschreven de dienstafbeelding op te lossen:

1. Zoeken naar actieve `principalNames` toewijzingen voor de opgegeven `bundleId` en `subserviceName`
1. `principalNames` toewijzen voor de tekens `bundleId` en null `subserviceName`
1. `userName` toewijzen voor de `bundleId` en `subserviceName`
1. `userName` mapping voor `bundleId` en null `subserviceName`
1. Standaardtoewijzing
1. Standaardgebruiker

### SlingRepository - Aanmelden bij service {#slingrepository-servicelogin}

De volgorde voor het verkrijgen van een service `Session/ResourceResolver` werkt als volgt:

1. Belangrijkste namen ophalen van `ServiceUserMapper` => pre-auth repository login zoals hieronder beschreven
1. Gebruikers-id ophalen uit `ServiceUserMapper`
1. Controleren op vervangen `1ServiceUserConfiguration` voor huidige gebruikers-id
1. Standaard Sling-service-aanmelding met de gebruikersnaam (bijvoorbeeld een reeks `createAdministrativeSession` en imiteren voor de id van de servicegebruiker)

De nieuwe toewijzing met belangrijkste namen resulteert in de volgende vereenvoudigde login van de bewaarplaats:

* Reeks hoofdnamen wordt beschouwd als de effectieve principal(s) die moet worden gebruikt om de `Subject` te vullen
* Aanmelding in opslagplaats kan daarom vooraf worden geverifieerd
* Geen groepslidmaatschapsresolutie

  >[!NOTE]
  >
  >Alle vereiste toestemmingen moeten voor de de dienstgebruikers worden verklaard. &#39;Iedereen&#39; en andere groepsmachtigingen worden niet meer overgeërfd.

* Geen extra admin-login om de dienst te hebben - `Session/ResourceResolver` wordt gecreeerd.

### Vervangen ServiceUserConfiguration {#deprecated-serviceUserConfiguration}

Houd er rekening mee dat het opgeven van één gebruikersnaam in de toewijzing gelijk is aan het bestaande `ServiceUserConfiguration.simpleSubjectPopulation` . Met de nieuwe indeling kan de tijdelijke oplossing die door `ServiceUserConfiguration` wordt geboden, rechtstreeks worden weerspiegeld door de servicetoewijzing van de gebruiker. `ServiceUserConfiguration` is daarom vervangen voor AEM en alle bestaande toepassingen zijn vervangen.

## Servicegebruikers {#service-users}

### Bestaande servicegebruikers opnieuw gebruiken {#reusing-existing-service-users}

Aanbevolen wordt bestaande gebruikers van services opnieuw te gebruiken als aan de volgende voorwaarden is voldaan:

* Uw behoeften komen overeen met de intentie van de bestaande servicegebruiker
* Uw dienst vereist om een gemeenschappelijke taak uit te voeren die door een bestaande gemeenschappelijke de dienstgebruiker wordt behandeld. In dit geval wordt aanbevolen de servicegebruiker opnieuw te gebruiken in plaats van duplicatie te introduceren
* Uw service vereist een specifieke taak die door een bestaande servicegebruiker wordt gedekt. Als u hierover niet zeker bent, vraag het eigenschapteam dat het bezit.

Bestaande servicegebruikers niet opnieuw gebruiken als:

* U moet de machtiging op een andere manier wijzigen om deze te laten werken
* Als u slechts een kleine ondergroep van de toestemmingen nodig hebt het verstrekt en u zou enkel het hergebruiken omdat het uw eigenschap maakt werk niet omdat het een echte gelijke is
* Als de naam een totaal andere intentie aangeeft dan u wilt. Het klikken van het omdat het werkt kan problemen onderaan de weg veroorzaken aangezien het eigenschapteam dat een specifieke dienst bezit de toestemmingen kan veranderen en uw eigenschap breken.

### Een servicegebruiker maken {#creating-a-service-user}

Nadat u hebt gecontroleerd dat er geen bestaande servicegebruiker in AEM van toepassing is voor uw gebruikscase en de bijbehorende RTC-problemen zijn goedgekeurd, kunt u doorgaan en de nieuwe gebruiker toevoegen aan de standaardinhoud. In het ideale geval is een lid van het uitgebreide beveiligingsteam betrokken bij de RTC-stemming, dus zorg dat u ook de relevante belanghebbenden erbij betrekt.

**noemend Overeenkomst**

Het AEM-beveiligingsteam heeft de volgende naamgevingsconventie voor servicegebruikers gedefinieerd om consistentie toe te voegen aan nieuwe servicegebruikers en om hun leesbaarheid en onderhoudbaarheid te verbeteren.

Een de dienstgebruikersnaam bestaat uit 3 elementen die door een streepje **&quot;-&quot;worden gescheiden**:

1. De logische entiteit/eigenschap die door de de dienstverrichtingen wordt gericht (vermijd wegelementen die kunnen veranderen)
1. De taak de diensten gaan uitvoeren
1. Navolgende **&quot;dienst&quot;** om van identiteitskaart en belangrijkste naam gemakkelijk te kunnen vlekken dat de gebruiker een de dienstgebruiker is

**Beste praktijken**

* Verwar verschillende entiteiten/functies niet. Splitsen op individuele servicegebruikers en deze samenvoegen in de toewijzing als uw service andere behoeften heeft
* Beperk uzelf tot één goed bepaalde taak per de dienstgebruiker. Splitsen als u uiteindelijk te veel of niet-verwante machtigingen toekent
* De tijd van de uitgaven identificeert de echte behoefte van uw dienst
* Besteed tijd het vinden van een goede, betekenisvolle en zelf-verklarende de dienstgebruikersnaam
* Vragen om feedback en beoordeling: ontwikkelaars die niet bekend zijn met uw functie, moeten uw intentie kunnen lezen en begrijpen. In de toekomst kunnen zij worden belast met de reparatie of het onderhoud ervan.

Aan het eind, zou de naam van de de dienstgebruiker moeten openbaren:

* Hoe wordt het gebruikt en of het opnieuw kan worden gebruikt:

   * Heel algemeen: `content-writer-service`. Veilig voor hergebruik in aggregatie als uw service(s) ook alle inhoud moet kunnen lezen
   * Zeer specifiek: `asset-linkshare-service` . Niet zo veilig om opnieuw te gebruiken tenzij uw dienst verbinding-verdeling van activa ook echt doet.

* Hoe de functieset en machtigingsinstelling eruit moeten zien:

   * De logische entiteit moet de toestemmingsopstelling aanpassen:

      * Een `content-foo-service` mag alleen worden gekoppeld aan bewerkingen op inhoud. Het verlenen van het toestemmingen om op andere entiteiten zoals configuratie of gebruikers te werken zou verkeerd zijn
      * Voor een specifieke service als `personalization-foo-service` moeten ook specifieke machtigingen worden ingesteld. Als u uiteindelijk machtigingen toekent voor alle inhoud, is dit niet meer specifiek. Weergeven dat in de naam of een algemene gebruiker opnieuw gebruiken in aggregatie
      * Voor een service die specifiek is voor bepaalde functies, zoals `msm-xyz-service` , moeten alleen bevoegdheden zijn die betrekking hebben op msm. Breid geen toestemmingen aan niet verwante eigenschappen zoals het beheren van gemeenschappen configuratie of de schermgebruikers uit.

   * De taak moet overeenkomen met de machtigingen:

      * Een `foo-reader-service` mag alleen reguliere items kunnen lezen. Schrijfmachtigingen nooit verlenen
      * Van een `foo-writer-service` kan worden verwacht dat het schrijfbewerkingen uitvoert. Het zou echter geen toestemmingen moeten worden verleend om de inhoud van de toegangscontrole te lezen/te wijzigen
      * Van een `foo-replicator-service` kan worden verwacht dat het `crx:replicate` heeft verleend.

**Voorbeelden**

Voorbeelden voor `configuration-reader-service` :

* De naam wijst erop dat het naar configuraties in het algemeen en niet configuratie van een bepaalde eigenschap, zoals configuratie van de integratie van DM verwijst. Een specifieke doelgebruiker voor het lezen van de configuratie van een dergelijke integratie zou liever `dmconfig-reader-service` of `s7config-reader-service` heten

  >[!NOTE]
  >
  >De naam bevat geen padinformatie. Configuraties zijn verplaatst van `/etc` naar `/conf` .

* Het taak-element wijst erop dat de diensten die aan die gebruiker worden gebonden slechts leesverrichtingen zullen uitvoeren.

Voorbeelden voor `userproperties-copy-service` :

* Services die aan deze servicegebruiker zijn gebonden, worden gebruikt voor gebruikers-/groepseigenschappen, zoals profielen of voorkeuren
* Het is specifiek gericht om die informatie in tegenstelling tot een naam als `userproperties-writer-service` te kopiëren die om het even welk soort schrijfverrichtingen zou omvatten. Daarom zou het mogelijk zijn dat de toestemmingsopstelling voor deze exemplaartaken slechts het toevoegen van punten bij één plaats en het verwijderen van punten bij een andere plaats toestaat.

**Beste praktijken voor de Opstelling van Toestemmingen**

* Gebruik altijd op hoofd-gebaseerde de toegangsbeheeropstelling voor de dienstgebruikers. Zie de volgende voorbeelden voor meer informatie:

   * Markeer servicegebruikers en hun machtigingen als onveranderlijke toepassingsinhoud in skyline
   * Geen paden en boomstructuren nodig

* Alleen toekenningsmachtigingen, nooit weigeren
* Machtigingen beperken

   * Toekennen van de minimale reeks benodigde machtigingen
   * Voor meer informatie, raadpleeg de [ Bevoegdheden van de Afbeelding aan Punten ](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) en [ de Vraag van API van de Afbeelding aan Privileges ](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html) documentatie
   * Geen toestemming verlenen voor `jcr:all` . Dat is hoogstwaarschijnlijk niet de minimale set.

* Bereik reduceren

   * Het toegangsbeheerbeleid van de plaats bij eigenschapspecifieke onderaannemers
   * In geval van verdeelde punten: gebruiksbeperkingen om werkingsgebied te beperken (raadpleeg [ de documentatie ](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) voor lijst van ingebouwde beperkingen).

* Consistentie garanderen

   * Machtigingen consistent maken met de entiteit en taak die u in de gebruikersnaam van de service hebt gebruikt
   * Voeg geen ongerelateerde machtigingen toe. Het zou bijvoorbeeld vreemd zijn om een `workflow-administration-service` te hebben en het toestemmingen te verlenen om gebruiker-beheer verrichtingen bij `/home/users/screens` uit te voeren of het s7-config te laten lezen.

* Volledigheid

   * Zorg ervoor dat uw service over alle machtigingen beschikt die nodig zijn om de taken uit te voeren die het bedrijf moet uitvoeren. Uw dienst moet uit de doos ook in klantenmilieu&#39;s werken.
   * Verwacht nooit of vraag klanten om de machtigingsinstelling uit te breiden (bijvoorbeeld hieronder `/apps`)

* Vermijd dubbel instellen van machtigingen

   * Hergebruik gemeenschappelijke de dienstgebruikers
   * Combineer hen met uw eigenschap-specifieke de dienstgebruikers die de specifieke toestemming verstrekken u naast nodig hebt

* U kunt de instellingen van machtigingen niet splitsen over verschillende functies. De behoefte om dit te doen wijst erop dat uw de dienstgebruiker niet goed wordt bepaald of te veel verschillende dingen doet
* Plaats geen servicegebruikers in groepen, omdat:

   * Het mengt implementatiedetails van de dienstgebruikers met &quot;openbare&quot;groepen
   * U hebt geen controle over wijzigingen in machtigingen (waarschijnlijk vanwege regressies en escalaties van bevoegdheden)
   * Aanmelding- en evaluatieprestaties
   * Werkt niet met op hoofdletters gebaseerde ac-setup

* De toegang tot de user-home knoop (of om het even welke subtree bevat daarin), die geen voorspelbare weg heeft wordt bereikt in repo init door huis (`userId`) te gebruiken. Zie de het laten vallen repo in het [ documentatie ](https://sling.apache.org/documentation/bundles/repository-initialization.html) voor details.
* RTC: maak een specifieke RTC-uitgave als u de machtigingen van een bestaande servicegebruiker wijzigt en zorg ervoor dat deze door het beveiligingsteam wordt gecontroleerd.

**Creatie met Initialisatie van de Bewaarplaats**

Gebruik altijd `repo-init` om de dienstgebruikers en hun toestemmingsopstelling te bepalen en beide in de correcte sectie van het de eigenschapmodel van Quickstart te plaatsen:

**Beste praktijken**

* Altijd `repo-init` gebruiken om de servicegebruiker te maken
* Geef altijd een tussentijds pad op voor het maken van een servicegebruiker
* Alle ingebouwde servicegebruikers voor AEM moeten zich onder `system/cq:services/internal` bevinden
* Voeg ook met de functie toe aan het tussenliggende relatieve pad naar de groep van servicegebruikers: `system/cq:services/internal/<your-feature>`
* Door de klant gedefinieerde servicegebruikers moeten zich onder `system/cq:services/<customer-intermediate-rel-path>` en nooit onder de interne structuur bevinden
* Gebruik **met gedwongen weg** in plaats van **met weg** als een gebruiker reeds bestond en aan de nieuwe plaats moet worden bewogen die op hoofd-gebaseerde vergunning steunt.

**Voorbeelden**

```
create service user my-new-feature-readcomment-service with path system/cq:services/internal/myfeature
set principal ACL for my-new-feature-readcomment-service
    allow rep:readProperties on /content/myFeature restriction(rep:itemNames,commentTitle,commentDate,commentTxt)
end
```

```
create service user my-existing-feature-addcomment-service with forced path system/cq:services/internal/myfeature
set principal ACL for my-existing-feature-addcomment-service
    allow jcr:addChildNodes,rep:addProperties on /content/myfeature restrictions(rep:glob,*/comments/*)
end
```

```
create service user myfeature-ims-service with path system/cq:services/internal/myfeature
set principal ACL for myfeature-ims-service
    allow jcr:read on home(myfeature-ims-service)
end
```

### Gebruikers en machtigingen voor opschonen {#cleanup-service-users-and-permissions}

De volgende repo init-opdracht kan worden gebruikt om ongebruikte servicegebruikers en hun machtigingen op te schonen:

```
# Remove the principal-based access control policy for principal my-feature-service
delete principal ACL for my-feature-service

# Remove all resource-based access control entries (ACEs) for principal my-feature-service
delete ACL for my-feature-service

# Disable the service user
disable service user my-feature-service : "My feature is no longer used"

# Remove the service user
delete service my-feature-service 
```

### Testservicegebruikers {#testing-service-users}

Het is van cruciaal belang om servertests voor de dienstgebruikers en hun toestemmingsopstelling te schrijven. Dit verifieert niet alleen dat uw opstelling echt werkt maar ook helpt u regressies en onbedoelde fouten wanneer het veranderen van de inhoud van de toegangscontrole of de dienstgebruikers.

De `com.adobe.granite.testing.clients` -bibliotheek biedt veel hulpprogramma&#39;s waarmee u eenvoudig SST&#39;s voor servicegebruikers kunt schrijven.
