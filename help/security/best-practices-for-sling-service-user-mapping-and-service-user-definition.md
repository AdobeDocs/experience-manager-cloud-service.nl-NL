---
title: Beste praktijken voor het Verkopen van de Toewijzing van de Gebruiker van de Dienst en de Definitie van de Gebruiker van de Dienst
description: Meer informatie over de beste werkwijzen voor het toewijzen van servicegebruikers en het definiëren van gebruikersdefinities voor services
source-git-commit: b6f7b6996b377ecfa372742ce1ad22139547ebdd
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---


# Beste praktijken voor het Verkopen van de Toewijzing van de Gebruiker van de Dienst en de Definitie van de Gebruiker van de Dienst {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## Toewijzing van servicegebruikers {#service-user-mapping}

Als u een toewijzing van uw service aan de overeenkomstige systeemgebruiker(s) wilt toevoegen, moet u een fabrieksconfiguratie voor de `ServiceUserMapper` service. Om deze modulaire configuratie te handhaven, kunnen dergelijke configuraties worden verstrekt gebruikend het Verschuivende &quot;wijzigingsmechanisme&quot; (zie [SLING-3578](https://issues.apache.org/jira/browse/SLING-3578) voor meer informatie ). U kunt dergelijke configuraties het beste met uw bundel installeren door deze toe te voegen aan het Quickstart-inrichtingsmodel, zoals in het volgende voorbeeld wordt beschreven:

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
>De `userName` is vervangen en mag niet meer worden gebruikt.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` en `subserviceName` de dienst identificeren; `userName/principalNames` identificeer de de dienstgebruiker en `principalNames` Dit is een door komma&#39;s gescheiden lijst.

Houd er ook rekening mee dat `principalNames` is de lijst van de de dienstgebruiker belangrijkste namen die uit de doos het zelfde als identiteitskaart zijn.


**Beste praktijken**

* De namen van de subdienst voor verschillende taken - als de diensten van uw bundel verschillende taken uitvoeren wordt het geadviseerd om te identificeren `subserviceNames` om hen door taken te groeperen
* Als een bepaalde service verschillende bewerkingen uitvoert (bijvoorbeeld de inhoud van elementen lezen en informatie bijwerken onder een substructuur van `/var`), wordt geadviseerd dit te weerspiegelen door verschillende de diensthoofden te groeperen die op de individuele verrichting, zoals samenvoeging van gemeenschappelijke `dam-reader-service` met uw specifieke functie `assetreport-writer-service`
* Elke dienst is idealiter verbindend aan een zeer specifieke en beperkte reeks verrichtingen
* De nieuwe indeling met `[one,or,multiple,principalNames]` is de geadviseerde manier om de afbeeldingen van de de dienstgebruiker vanaf AEM 6.4 te bepalen.

Hieronder vindt u een lijst met redenen voor het wijzigen van de indeling en waarom Adobe u aanraadt deze te gebruiken in plaats van de versietoewijzing alleen voor één gebruiker-id:

* De capaciteit om de dienstgebruikers te hergebruiken door de speciale behoeften van klanten met gemeenschappelijke taken te combineren
* Vermijd dubbel instellen van machtigingen
* Een beter inzicht in de effectieve machtigingen (en taken) die een bepaalde service uitvoert
* Geen behoefte aan expliciete groepslidmaatschap van de dienstgebruikers. Dit kan lastige bijwerkingen hebben wanneer de groepsmachtigingen veranderen
* Prestatieverbeteringen en schaalbaarheid

## Toewijzingsresolutie en aanmelding voor service {#mapping-resolution-and-service-login}

### Oplossing voor servicetoewijzing {#service-mapping-resolution}

De opeenvolging van vraag om de hieronder beschreven de dienstafbeelding op te lossen:

1. Zoeken naar actief `principalNames` afbeelding van de gegeven `bundleId` en `subserviceName`
1. `principalNames` toewijzing voor de `bundleId` en null `subserviceName`
1. `userName` toewijzing voor de `bundleId` en `subserviceName`
1. `userName` toewijzen voor `bundleId` en null `subserviceName`
1. Standaardtoewijzing
1. Standaardgebruiker

### SlingRepository - Aanmelden bij service {#slingrepository-servicelogin}

De opeenvolging voor het verkrijgen van de dienst `Session/ResourceResolver` werkt als volgt:

1. Hoofdnamen ophalen van `ServiceUserMapper` => Aanmelden voor auth-repository zoals hieronder beschreven
1. Gebruikersnaam ophalen van `ServiceUserMapper`
1. Controle voor afgekeurde 1ServiceUserConfiguration&quot;voor huidige gebruiker identiteitskaart
1. Standaard Sling-service aanmelden met de gebruikers-id (bijvoorbeeld een reeks van `createAdministrativeSession` en imiteren voor de dienstgebruiker - identiteitskaart)

De nieuwe toewijzing met belangrijkste namen resulteert in de volgende vereenvoudigde login van de bewaarplaats:

* Reeks hoofdnamen wordt beschouwd als de effectieve Opdrachtgever(s) die moet worden gebruikt om de `Subject`
* Aanmelding in opslagplaats kan daarom vooraf worden geverifieerd
* Geen groepslidmaatschapsresolutie

  >[!NOTE]
  >
  >Alle vereiste toestemmingen moeten voor de de dienstgebruikers worden verklaard. &#39;Iedereen&#39; en andere groepsmachtigingen worden niet meer overgeërfd.

* Geen extra admin-login om de dienst te hebben-`Session/ResourceResolver` worden gemaakt.

### Vervangen ServiceUserConfiguration {#deprecated-serviceUserConfiguration}

Houd er rekening mee dat het opgeven van één gebruikersnaam in de toewijzing gelijk is aan het bestaande `ServiceUserConfiguration.simpleSubjectPopulation`. Met de nieuwe indeling kunt u de tijdelijke oplossing van de `ServiceUserConfiguration` kan direct met de afbeelding van de de dienstgebruiker worden weerspiegeld. De `ServiceUserConfiguration` is daarom vervangen voor AEM en alle bestaande toepassingen zijn vervangen.

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

Nadat u hebt gecontroleerd dat er geen bestaande servicegebruiker in AEM van toepassing is voor uw use-case en de bijbehorende RTC-problemen zijn goedgekeurd, kunt u doorgaan en de nieuwe gebruiker toevoegen aan de standaardinhoud. In het ideale geval is een lid van het uitgebreide beveiligingsteam betrokken bij de RTC-stemming, dus zorg dat u ook de relevante belanghebbenden erbij betrekt.

**Naamgevingsconventie**

Het AEM veiligheidsteam heeft de volgende noemende overeenkomst voor de dienstgebruikers bepaald om consistentie aan nieuwe de dienstgebruikers toe te voegen en hun leesbaarheid en onderhoudbaarheid te verbeteren.

Een de dienstgebruikersnaam bestaat uit 3 elementen die door een streepje worden gescheiden **&#39;-&#39;**:

1. De logische entiteit/eigenschap die door de de dienstverrichtingen wordt gericht (vermijd wegelementen die kunnen veranderen)
1. De taak de diensten gaan uitvoeren
1. Trailing **&#39;service&#39;** om van identiteitskaart en belangrijkste naam gemakkelijk te kunnen merken dat de gebruiker een de dienstgebruiker is

**Aanbevolen procedures**

* Verwar verschillende entiteiten/functies niet. Splitsen op individuele servicegebruikers en deze samenvoegen in de toewijzing als uw service andere behoeften heeft
* Beperk uzelf tot één goed bepaalde taak per de dienstgebruiker. Splitsen als u uiteindelijk te veel of niet-verwante machtigingen toekent
* De tijd van de uitgaven identificeert de echte behoefte van uw dienst
* Besteed tijd het vinden van een goede, betekenisvolle en zelf-verklarende de dienstgebruikersnaam
* Vragen om feedback en beoordeling: ontwikkelaars die niet bekend zijn met uw functie, moeten uw intentie kunnen lezen en begrijpen. In de toekomst kunnen zij worden belast met de reparatie of het onderhoud ervan.

Aan het eind, zou de naam van de de dienstgebruiker moeten openbaren:

* Hoe wordt het gebruikt en of het opnieuw kan worden gebruikt:

   * Zeer algemeen: `content-writer-service`. Veilig voor hergebruik in aggregatie als uw service(s) ook alle inhoud moet kunnen lezen
   * Zeer specifiek: `asset-linkshare-service`. Niet zo veilig om opnieuw te gebruiken tenzij uw dienst verbinding-verdeling van activa ook echt doet.

* Hoe de functieset en machtigingsinstelling eruit moeten zien:

   * De logische entiteit moet de toestemmingsopstelling aanpassen:

      * A `content-foo-service` mag alleen worden gekoppeld aan bewerkingen op inhoud. Het verlenen van het toestemmingen om op andere entiteiten zoals configuratie of gebruikers te werken zou verkeerd zijn
      * Een specifieke service zoals `personalization-foo-service` moeten ook specifieke machtigingen krijgen. Als u uiteindelijk machtigingen toekent voor alle inhoud, is dit niet meer specifiek. Weergeven dat in de naam of een algemene gebruiker opnieuw gebruiken in aggregatie
      * Een functie-specifieke service zoals `msm-xyz-service` moet alleen beschikken over aan msm gerelateerde machtigingen. Breid geen toestemmingen aan niet verwante eigenschappen zoals het beheren van gemeenschappen configuratie of de schermgebruikers uit.

   * De taak moet overeenkomen met de machtigingen:

      * A `foo-reader-service` mogen alleen reguliere objecten lezen. Schrijfmachtigingen nooit verlenen
      * A `foo-writer-service` kan worden verwacht schrijfbewerkingen uit te voeren. Het zou echter geen toestemmingen moeten worden verleend om de inhoud van de toegangscontrole te lezen/te wijzigen
      * A `foo-replicator-service` verwacht kan worden dat `crx:replicate` toegekend.

**Voorbeelden**

Voorbeelden voor `configuration-reader-service`:

* De naam wijst erop dat het naar configuraties in het algemeen en niet configuratie van een bepaalde eigenschap, zoals configuratie van de integratie van DM verwijst. Een de dienstgebruiker specifiek gericht voor het lezen configuratie van zulk een integratie zou eerder worden genoemd `dmconfig-reader-service` of `s7config-reader-service`

  >[!NOTE]
  >
  >De naam bevat geen padinformatie. Configuraties zijn verplaatst van `/etc` tot `/conf`.

* Het taak-element wijst erop dat de diensten die aan die gebruiker worden gebonden slechts leesverrichtingen zullen uitvoeren.

Voorbeelden voor `userproperties-copy-service`:

* Services die aan deze servicegebruiker zijn gebonden, worden gebruikt voor gebruikers-/groepseigenschappen, zoals profielen of voorkeuren
* Het is specifiek gericht om die informatie in tegenstelling tot een naam te kopiëren zoals `userproperties-writer-service` die alle schrijfbewerkingen zouden omvatten. Daarom zou het mogelijk zijn dat de toestemmingsopstelling voor deze exemplaartaken slechts het toevoegen van punten bij één plaats en het verwijderen van punten bij een andere plaats toestaat.

**Beste praktijken voor de Opstelling van Rechten**

* Gebruik altijd op hoofd-gebaseerde de toegangsbeheeropstelling voor de dienstgebruikers. Zie de volgende voorbeelden voor meer informatie:

   * Markeer servicegebruikers en hun machtigingen als onveranderlijke toepassingsinhoud in skyline
   * Geen paden en boomstructuren nodig

* Alleen toekenningsmachtigingen, nooit weigeren
* Machtigingen beperken

   * Toekennen van de minimale reeks benodigde machtigingen
   * Voor meer informatie raadpleegt u de [Privileges toewijzen aan objecten](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) en [API-aanroepen toewijzen aan rechten](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html) documentatie
   * Geen toestemming verlenen voor `jcr:all`. Dat is hoogstwaarschijnlijk niet de minimale set.

* Bereik reduceren

   * Het toegangsbeheerbeleid van de plaats bij eigenschapspecifieke onderaannemers
   * In het geval van verdeelde punten: gebruiksbeperkingen om werkingsgebied te beperken (raadpleeg [de documentatie](http://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) voor een lijst van ingebouwde beperkingen).

* Consistentie garanderen

   * Machtigingen consistent maken met de entiteit en taak die u in de gebruikersnaam van de service hebt gebruikt
   * Voeg geen ongerelateerde machtigingen toe. Het zou bijvoorbeeld vreemd zijn om een `workflow-administration-service` en verleent het toestemmingen om gebruikers-beheer handelingen uit te voeren bij `/home/users/screens` of laat het s7-config lezen.

* Volledigheid

   * Zorg ervoor dat uw service over alle machtigingen beschikt die nodig zijn om de taken uit te voeren die het bedrijf moet uitvoeren. Uw dienst moet uit de doos ook in klantenmilieu&#39;s werken.
   * Verwacht nooit of vraag klanten om de machtigingsinstelling uit te breiden (bijvoorbeeld hieronder) `/apps`)

* Vermijd dubbel instellen van machtigingen

   * Hergebruik gemeenschappelijke de dienstgebruikers
   * Combineer hen met uw eigenschap-specifieke de dienstgebruikers die de specifieke toestemming verstrekken u naast nodig hebt

* U kunt de instellingen van machtigingen niet splitsen over verschillende functies. De behoefte om dit te doen wijst erop dat uw de dienstgebruiker niet goed wordt bepaald of te veel verschillende dingen doet
* Plaats geen servicegebruikers in groepen, omdat:

   * Het mengt implementatiedetails van de dienstgebruikers met &quot;openbare&quot;groepen
   * U hebt geen controle over wijzigingen in machtigingen (waarschijnlijk vanwege regressies en escalaties van bevoegdheden)
   * Aanmelding- en evaluatieprestaties
   * Werkt niet met op hoofdletters gebaseerde ac-setup

* De toegang tot het user-home knoop (of om het even welke subtree bevat daarin), die geen voorspelbare weg heeft wordt bereikt in repo init door home() te gebruiken`userId`). Zie de slingerrepo init [documentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html) voor meer informatie.
* RTC: maak een specifieke RTC-uitgave als u de machtigingen van een bestaande servicegebruiker wijzigt en zorg ervoor dat deze door het beveiligingsteam wordt gecontroleerd.

**Maken met initialisatie opslagruimte**

Altijd gebruiken `repo-init` om de dienstgebruikers en hun toestemmingsopstelling te bepalen en beide in de correcte sectie van het de eigenschapmodel van Quickstart te plaatsen:

**Aanbevolen procedures**

* Altijd gebruiken `repo-init` om de de dienstgebruiker te creëren
* Geef altijd een tussentijds pad op voor het maken van een servicegebruiker
* Alle ingebouwde gebruikers van de dienst voor AEM moeten hieronder worden gevestigd `system/cq:services/internal`
* Voeg ook aan de middenrelatieve weg aan de gebruikers van de groepsdienst door eigenschap toe: `system/cq:services/internal/<your-feature>`
* Door de klant gedefinieerde servicegebruikers moeten zich hieronder bevinden `system/cq:services/<customer-intermediate-rel-path>` en nooit onder de interne boom
* Gebruiken **met geforceerd pad** in plaats van **met pad** als een gebruiker reeds bestond en naar de nieuwe plaats moet worden verplaatst die op hoofd-gebaseerde vergunning steunt.

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

De `com.adobe.granite.testing.clients` De bibliotheek biedt veel hulpprogramma&#39;s die het schrijven van SST&#39;s voor servicegebruikers eenvoudig maken.





