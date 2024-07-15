---
title: Omgevingen beheren
description: Leer meer over de typen omgevingen die u kunt maken en hoe u deze kunt maken voor uw Cloud Manager-project.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9defb49b2639aa8945d1fed0332400b8ab5ced8c
workflow-type: tm+mt
source-wordcount: '2377'
ht-degree: 0%

---


# Omgevingen beheren {#managing-environments}

Leer meer over de typen omgevingen die u kunt maken en hoe u deze kunt maken voor uw Cloud Manager-project.

## Omgevingstypen {#environment-types}

Een gebruiker met de vereiste toestemmingen kan de volgende milieutypes (binnen de grenzen van wat aan de specifieke huurder beschikbaar is) tot stand brengen.

* **Productie + Stadium** - de productie en het opvoeren milieu&#39;s zijn beschikbaar als paar en voor productie en testende doeleinden, respectievelijk gebruikt. Prestatie- en beveiligingstests uitvoeren op de werkgebiedomgeving. Het is even groot als de productie.

* **Ontwikkeling** - een ontwikkelomgeving kan voor ontwikkeling en het testen doeleinden worden gecreeerd en kan met niet-productiepijpleidingen slechts worden geassocieerd.  Ontwikkelomgevingen hebben niet dezelfde grootte als stadium en productie en mogen niet worden gebruikt om prestatie- en veiligheidstests uit te voeren.

* **Snelle Ontwikkeling** - een snelle ontwikkelomgeving (RDE) laat een ontwikkelaar snel veranderingen opstellen en herzien, die de hoeveelheid tijd minimaliseren wordt vereist om eigenschappen te testen die om aan een lokale ontwikkelomgeving worden bewezen te werken. Zie [ de snelle documentatie van het ontwikkelomgeving ](/help/implementing/developing/introduction/rapid-development-environments.md) voor details over hoe te om RDE te gebruiken.

De mogelijkheden van individuele milieu&#39;s hangen van de oplossingen af die in het [ programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) van het milieu worden toegelaten.

* [Sites](/help/overview/introduction.md)
* [Assets](/help/assets/overview.md)
* [Forms](/help/forms/home.md)
* [Screens](/help/screens-cloud/introduction/introduction.md)

>[!NOTE]
>
>De productie en het opvoeren milieu&#39;s worden slechts gecreeerd als paar. U kunt niet alleen een testomgeving of alleen een productieomgeving maken.

## Een omgeving toevoegen {#adding-environments}

Om een milieu toe te voegen of uit te geven, moet een gebruiker een lid van de **rol van de BedrijfsEigenaar** zijn.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, ontgrendel of klik het programma waarvoor u een milieu wilt toevoegen.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, klik **voegt Milieu** op de **kaart van Milieu** toe om een milieu toe te voegen.

   ![ kaart van Milieu&#39;s ](assets/no-environments.png)

   * **voegt de optie van het Milieu** toe is ook beschikbaar op **Milieu** tabel.

     ![ Milieu&#39;s tabel ](assets/environments-tab.png)

   * **voeg Milieu** optie toe kan wegens gebrek aan toestemmingen of afhankelijk van de vergunning gegeven middelen worden onbruikbaar gemaakt.

1. In **voeg milieu** dialoog toe die verschijnt:

   * Selecteer een [**milieutype**.](#environment-types)
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes achter de naam van het omgevingstype weergegeven.
   * Verstrek een milieu **Naam**.
      * De naam van de omgeving kan niet worden gewijzigd nadat de omgeving is gemaakt.
   * Verstrek een milieu **Beschrijving**.
   * Als u a **Productie + het milieu van het Stadium** toevoegt, moet u een milieunaam en een beschrijving voor zowel uw productie als het opvoeren milieu&#39;s verstrekken.
   * Selecteer a **Primair gebied** van drop-down.
      * Het primaire gebied kan na het maken niet meer worden gewijzigd.
      * Afhankelijk van uw beschikbare rechten, kunt u [ veelvoudige gebieden ](#multiple-regions) kunnen vormen.

   ![ voeg milieudialoog ](assets/add-environment2.png) toe

1. Klik **sparen** om het gespecificeerde milieu toe te voegen.

Het **scherm van het Overzicht** toont nu uw nieuw milieu in de **** kaart van Milieu&#39;s. U kunt nu pijpleidingen instellen voor uw nieuwe omgeving.

## Meerdere Publish-regio&#39;s {#multiple-regions}

Een gebruiker met de **rol van de BedrijfsEigenaar** kan productie en het opvoeren milieu&#39;s vormen om tot drie extra te omvatten publiceren gebieden naast het primaire gebied. Aanvullende publicatiegebieden kunnen de beschikbaarheid verbeteren. Zie de [ Extra documentatie van de Gebieden van Publish ](/help/operations/additional-publish-regions.md) voor meer details.

>[!TIP]
>
>U kunt [ Cloud Manager API ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/api-usage/creating-programs-and-environments/#creating-aem-cloud-service-environments) gebruiken om een huidige lijst van beschikbare gebieden te vragen.

### Meerdere Publish-regio&#39;s toevoegen aan een nieuwe omgeving {#add-regions}

Wanneer u een omgeving toevoegt, kunt u ervoor kiezen om naast het primaire gebied ook andere gebieden te configureren.

1. Selecteer het **Primaire gebied**.
   * Het primaire gebied kan na het creëren van het milieu niet worden veranderd.
1. Selecteer de optie **toevoegt extra publiceer gebieden** en een nieuwe **Extra publiceer gebieden** optie drop-down verschijnt.
1. In **extra publiceer gebieden** drop-down, selecteer een extra gebied.
1. Het geselecteerde gebied wordt onder de vervolgkeuzelijst toegevoegd om de selectie ervan aan te geven.
   * Selecteer de `X` naast het geselecteerde gebied zodat u de selectie ongedaan kunt maken.
1. Selecteer een ander gebied van **extra publiceer gebieden** drop-down om een ander gebied toe te voegen.
1. Selecteer **sparen** wanneer u bereid bent om uw milieu tot stand te brengen.

![ Selecterend veelvoudige gebieden ](assets/select-multiple-regions.png)

De geselecteerde gebieden zijn van toepassing op zowel productie als het opvoeren milieu&#39;s.

Als u geen extra gebieden specificeert, [ kunt u dit later doen nadat de milieu&#39;s worden gecreeerd.](#edit-regions)

Als u [ geavanceerd voorzien van een netwerk ](/help/security/configuring-advanced-networking.md) voor het programma wilt voorzien, adviseert men dat deze levering wordt gedaan alvorens extra toe te voegen publiceer gebieden aan de milieu&#39;s door Cloud Manager API te gebruiken. Anders, gaat het extra publiceer gebiedsverkeer door de volmacht van het primaire gebied.

### Meerdere Publish-gebieden bewerken {#edit-regions}

Als u in eerste instantie geen extra gebieden hebt opgegeven, kunt u dat doen nadat de omgevingen zijn gemaakt als u over de benodigde rechten beschikt.

U kunt ook extra publicatiegebieden verwijderen. U kunt echter slechts gebieden in één transactie toevoegen of verwijderen. Als u één gebied moet toevoegen en één gebied wilt verwijderen, voegt u eerst de wijziging toe, slaat u de wijziging op en verwijdert u vervolgens (of omgekeerd).

1. Van de console van het Overzicht van het Programma van uw programma, klik de ellipsknoop voor uw productiemilieu en selecteer **uitgeven** van het menu.

   ![ geef milieu ](assets/select-edit-environment.png) uit

1. In **geef de dialoog van het Milieu van de Productie uit**, breng de noodzakelijke veranderingen in extra uit publiceer gebieden.
   * Gebruik **extra publiceer gebieden** drop-down om extra gebieden te selecteren.
   * Klik op de X naast de geselecteerde aanvullende publicatiegebieden om deze te desselecteren.

   ![ geef milieu ](assets/edit-environment.png) uit

1. Selecteer **sparen** om de veranderingen te bewaren.

Wijzigingen in de productieomgeving zijn van toepassing op zowel de productie- als de testomgeving. Wijzigingen in meerdere publicatiegebieden kunnen alleen worden bewerkt in de productieomgeving.

Als u [ geavanceerd voorzien van een netwerk ](/help/security/configuring-advanced-networking.md) voor het programma wilt voorzien, adviseert men dat deze levering wordt gedaan alvorens extra toe te voegen publiceert gebieden aan de milieu&#39;s. Anders gaat het extra publicatiegebiedsverkeer door de volmacht van het primaire gebied.

## Omgevingsdetails {#viewing-environment}

Van de **pagina van het Overzicht**, kunt u tot het detail van een milieu op twee manieren toegang hebben.

1. Van de **pagina van het Overzicht**, klik het **milieu&#39;s** lusje in het paneel van de zijnavigatie.

   ![ Milieu&#39;s tabel ](assets/environments-tab2.png)

   * Alternatief, klik **tonen Al** knoop op de **** kaart van Milieu&#39;s {om rechtstreeks aan het **Milieu** lusje te springen.

     ![ toon alle optie ](assets/environment-showall.png)

1. De **Milieu&#39;s** opent en maakt een lijst van alle milieu&#39;s voor het programma.

   ![ het milieu tabel ](assets/environments-tab2.png)

1. Tik of klik op een omgeving in de lijst zodat u de details ervan kunt tonen.

   ![ de details van het Milieu ](assets/environ-preview1.png)

Alternatief, klik de elliptische knoop van het milieu u wilt en dan **Details van de Mening** selecteren.

![ het omgevingsdetails van de Mening ](assets/view-environment-details.png)

>[!NOTE]
>
>De **kaart van Milieu** maakt een lijst van slechts drie milieu&#39;s. Klik **tonen allen** zoals eerder beschreven om alle milieu&#39;s van het programma te zien.

### Toegang tot de voorvertoningsservice {#access-preview-service}

Cloud Manager biedt een voorbeeldservice (geleverd als een extra publicatieservice) aan elke AEM as a Cloud Service-omgeving.

Met de service kunt u de uiteindelijke ervaring van een website voorvertonen voordat deze de daadwerkelijke publicatieomgeving bereikt en openbaar is.

Bij het maken van de voorvertoningsservice wordt er een standaard IP-lijst van gewenste personen op toegepast, met het label `Preview Default [<envId>]` , die al het verkeer naar de voorvertoningsservice blokkeert. Hef de standaardIP lijst van gewenste personen van de voorproefdienst op zodat kunt u toegang toelaten.

![ de dienst van de Voorproef en zijn lijst van gewenste personen ](assets/preview-ip-allow.png)

Een gebruiker met de vereiste machtigingen moet de volgende stappen uitvoeren voordat de URL van de voorvertoningsservice wordt gedeeld om ervoor te zorgen dat deze toegankelijk is.

1. Creeer een aangewezen IP lijst van gewenste personen, pas het op de voorproefdienst toe, en pas onmiddellijk unapply de `Preview Default [<envId>]` lijst van gewenste personen.

   * Zie [ Toepassend en het Niet toepassen van IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) voor meer details.

1. Gebruik het update **IP Lijst van gewenste personen** werkschema om standaardIP te verwijderen en IPs toe te voegen zoals aangewezen. Zie [ het Leiden IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md) om meer te leren.

Nadat de toegang tot de voorvertoningsservice is ontgrendeld, wordt het vergrendelingspictogram vóór de naam van de voorvertoningsservice niet meer weergegeven.

Nadat de functie is geactiveerd, kunt u inhoud publiceren naar de voorbeeldservice met behulp van de interface Publicatie beheren in AEM. Zie [ het Voorproeven van Inhoud ](/help/sites-cloud/authoring/sites-console/previewing-content.md) voor meer details.

>[!NOTE]
>
>Uw omgeving moet AEM versie `2021.05.5368.20210529T101701Z` of hoger zijn om de voorvertoningsservice te kunnen gebruiken. Zorg ervoor dat een updatepijpleiding op uw milieu met succes heeft gelopen zodat kunt u de voorproefdienst gebruiken.

### Status van extra Publish-regio&#39;s {#additional-region-status}

Als u extra hebt geactiveerd publiceer gebieden, kunt u het statuut van deze gebieden van de **kaart van Milieu** controleren.

1. Voor de **pagina van het Overzicht**, bepaal de plaats van de **** kaart van Milieu&#39;s.

1. Op de **kaart van Milieu**, zal de **3} kolom van de Status {weerspiegelen als er om het even welke kwesties met gevormd extra zijn publiceer gebieden.** Klik het **pictogram van Info** voor details van de gebieden.

   ![ extra publiceer gebiedsstatusinformatie over de kaart van Milieu ](assets/additional-publish-region-status-environments-card.png)

Alternatief kunt u tot de zelfde informatie van de **Milieu&#39;s** toegang hebben tabel.

1. Voor de **pagina van het Overzicht**, selecteer de **Milieu&#39;s** tabel.

1. Voor het **lusje van Milieu&#39;s**, selecteer het milieu u in het linkernavigatievenster wilt vragen.

1. Nadat een omgeving is geselecteerd:

   * De **lijst van de Informatie van het Milieu** zal tonen welke gebieden voor het geselecteerde milieu worden gevormd.
   * De **kolom van de Status** van de **Segmenten van het Milieu** lijst zal nadenken als er om het even welke kwesties met gevormd extra zijn publiceer gebieden. Houd de status boven voor details over een kwestie.

   ![ extra publiceer gebiedsstatusinformatie over het lusje van Milieu&#39;s ](assets/additional-publish-region-status-environments-tab.png)

Als er problemen zijn gemeld met extra publicatiegebieden:

1. Wees geduldig. Cloud Manager probeert het gebied voortdurend te herstellen en kan op elk moment beschikbaar komen.
1. Als het probleem zich na enkele uren blijft voordoen, kunt u het aanvullende publicatiegebied verwijderen en het opnieuw toevoegen (hetzelfde gebied of een ander gebied) om een volledige implementatie te activeren.

Hoe lang u wacht tot het systeem op zich terugkrijgt alvorens extra actie te ondernemen hangt van de invloed af het mislukken van dat gebied op uw systemen heeft.

In elk geval, wordt het [ verkeer altijd verpletterd aan het andere dichtstbijzijnde gebied dat online is.](/help/operations/additional-publish-regions.md) Neem contact op met de klantenservice van de Adobe als de problemen zich blijven voordoen.

## Bijwerken van omgevingen {#updating-dev-environment}

Als cloudservice worden updates van uw ontwikkelings-, staging- en productieomgevingen binnen productieprogramma&#39;s automatisch door Adobe beheerd.

Updates voor omgevingen in sandboxprogramma&#39;s worden echter binnen de programma&#39;s beheerd. Wanneer zulk een milieu niet de recentste openbaar beschikbare AEM versie in werking stelt, toont de status op de **1} kaart van Milieu&#39;s {op het** 3} scherm van het Overzicht **Beschikbare Update**.****

![ de updatestatus van het Milieu ](assets/environ-update.png)

### Updates en pijpleidingen {#updates-pipelines}

De pijpleidingen zijn de enige manier aan [ code aan de milieu&#39;s van AEM as a Cloud Service op te stellen.](deploy-code.md) Om deze reden, wordt elke pijpleiding geassocieerd met een bepaalde AEM versie.

Als Cloud Manager ontdekt dat er een nieuwere versie van AEM beschikbaar is dan wat het laatst met de pijpleiding werd opgesteld, toont het de **Beschikbare Update** status voor het milieu.

Het proces van actualisering bestaat daarom uit twee stappen:

1. De pijpleiding bijwerken met de recentste AEM versie
1. De pijpleiding in werking stellen om de nieuwe versie van AEM aan een milieu op te stellen

### Uw omgevingen bijwerken {#updating-your-environments}

>[!NOTE]
> Vanaf 2024 worden ontwikkelingsinstanties en sommige sandboxprogramma&#39;s al automatisch bijgewerkt, zodat er geen noodzaak is om updates voor deze instanties handmatig te beheren. Als resultaat van deze overgang, zou de optie om milieu voor ontwikkelingsinstanties manueel bij te werken niet aan _kunnen beschikbaar zijn wat_ van uw programma&#39;s.

De **optie van de Update** is beschikbaar bij de **** kaart van Milieu&#39;s {voor sommige ontwikkelmilieu&#39;s en milieu&#39;s in zandbakprogramma&#39;s door de elliptische knoop van het milieu te klikken.

![ optie van de Update van de kaart van Milieu&#39;s ](assets/environ-update2.png)

Deze optie is ook beschikbaar door het **lusje van Milieu&#39;s** van het programma te klikken en dan de ellipsknoop van het milieu te selecteren.

![ optie van de Update van het lusje van Milieu&#39;s ](assets/environ-update3.png)

Een gebruiker met de **Manager van de Plaatsing** of **BedrijfsEigenaar** rol kan deze optie gebruiken om de pijpleiding bij te werken verbonden aan dit milieu aan de recentste AEM versie.

Zodra de pijpleidingsversie aan de recentste openbaar beschikbare AEM versie wordt bijgewerkt, wordt de gebruiker ertoe aangezet om de bijbehorende pijpleiding in werking te stellen om de recentste versie aan het milieu op te stellen.

![ Vragen om pijpleiding in werking te stellen om milieu ](assets/update-run-pipeline.png) bij te werken

Het **gedrag van de Update** optie varieert afhankelijk van de configuratie en de huidige staat van het programma.

* Als de pijpleiding reeds is bijgewerkt, veroorzaakt de **Update** optie de gebruiker om de pijpleiding uit te voeren.
* Als de pijpleiding reeds wordt bijgewerkt, informeert de **optie van de Update** de gebruiker dat een update reeds loopt.
* Als een aangewezen pijpleiding niet bestaat, veroorzaakt de **Update** optie de gebruiker om te creëren.

## Ontwikkelomgevingen verwijderen {#deleting-environment}

Een gebruiker met de **Manager van de Plaatsing** of **BedrijfsEigenaar** rol kan een ontwikkelomgeving schrappen.

Van het **scherm van het Overzicht** van het programma op de **3} kaart van Milieu&#39;s {, klik de elliptische knoop van het ontwikkelmilieu u wilt schrappen.**

![ schrapt optie ](assets/environ-delete.png)

De schrappingsoptie is ook beschikbaar bij het **Milieu** lusje van het **venster van het Overzicht** van het programma. Klik de elliptische knoop van het milieu en selecteer **Schrapping**.

![ schrapt optie van het lusje van Milieu&#39;s ](assets/environ-delete2.png)

>[!NOTE]
>
>* Productie- en staging-omgevingen die in een productieprogramma zijn gemaakt, kunnen niet worden verwijderd.
>* Productie- en staging-omgevingen in een sandboxprogramma kunnen worden verwijderd.

## Toegang beheren {#managing-access}

Selecteer **beheert Toegang** van het ellipsmenu van het milieu op de **kaart van Milieu&#39;s**. U kunt rechtstreeks naar de instantie van de auteur navigeren en de toegang voor uw omgeving beheren.

![ beheert toegangsoptie ](assets/environ-access.png)

>[!TIP]
>
>Zie [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md) als u wilt leren hoe het team en de productprofielen van AEM as a Cloud Service toegang tot uw vergunning gegeven oplossingen van de Adobe kunnen verlenen en beperken.

## Toegang tot de Developer Console {#accessing-developer-console}

Selecteer **Developer Console** van het ellipsmenu van het milieu op de **kaart van Milieu**. Een nieuw lusje wordt geopend in uw browser met het logboek op pagina aan **Developer Console**.

![ Login aan Developer Console ](assets/environ-devconsole.png)

Slechts heeft een gebruiker met de **rol van de Ontwikkelaar** toegang tot **Developer Console**. Nochtans, voor zandbakprogramma&#39;s, heeft om het even welke gebruiker met toegang tot het zandbakprogramma toegang tot **Developer Console**.

Zie [ Sluimerende en Sluiting van Sandbox Milieu&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/introduction-sandbox-programs.html#hibernation) voor meer details.

Deze optie is ook beschikbaar bij het **Milieu** lusje van het **venster van het Overzicht** wanneer het klikken van het elliptische menu van een individueel milieu.

## Lokaal aanmelden {#login-locally}

Selecteer **Lokale Login** van het elliptische menu van het milieu in de **kaart van Milieu** aan login plaatselijk aan Adobe Experience Manager.

![ Login plaatselijk ](assets/environ-login-locally.png)

Ook, kunt u plaatselijk van het **Milieu** lusje van het **Overzicht** pagina het programma openen.

![ Login plaatselijk van het lusje van Milieu&#39;s ](assets/environ-login-locally-2.png)

## Aangepaste domeinnamen beheren {#manage-cdn}

In Cloud Manager for Sites worden aangepaste domeinnamen ondersteund voor zowel publicatie- als voorvertoningsservices.

>[!TIP]
>
>Voor meer informatie, te zien gelieve de document [ Inleiding aan de Namen van het Domein van de Douane.](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

## IP-Lijsten van gewenste personen beheren {#manage-ip-allow-lists}

IP de lijsten van gewenste personen worden gesteund in Cloud Manager voor auteur, publiceren, en voorproefdiensten voor de programma&#39;s van Plaatsen.

Om IP lijsten van gewenste personen te beheren, navigeer aan het **lusje van Milieu** van de **pagina van het Overzicht** van uw programma. Klik op een afzonderlijke omgeving zodat u de details ervan kunt beheren.

### Een IP-Lijst van gewenste personen toepassen {#apply-ip-allow-list}

Het toepassen van een IP lijst van gewenste personen associeert alle IP waaiers inbegrepen in de definitie van de lijst van gewenste personen met een auteur of publiceer de dienst in een milieu.

>[!TIP]
>
>Voor meer informatie, te zien gelieve de document [ Inleiding aan IP Lijsten van gewenste personen.](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)
