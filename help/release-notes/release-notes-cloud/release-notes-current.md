---
title: Opmerkingen bij de release Adobe Experience Manager als Cloud Service voor 2020.6.0
description: Opmerkingen bij de release Experience Manager voor 2020.6.0
translation-type: tm+mt
source-git-commit: 972e6322a313c9e6afcf09262290992272406491
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---


# Opmerkingen bij de release van AEM als Cloud Service 2020.6.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager weergegeven als Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als cloudservice 2020.6.0 is 4 juni 2020.

## Nieuw in AEM-sites {#aem-sites}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor AEM-sites in AEM als Cloud Service Release 2020.6.0.

### What&#39;s New {#whats-new-2020.6.0}

Release 2.9.0 van de [kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) is nu beschikbaar als onderdeel van AEM-sites, waaronder:

* Integratie tussen [Adobe Client Data Layer](https://github.com/adobe/adobe-client-data-layer) en de Core Components
* Configureerbare HTML-id-kenmerken voor alle componenten
* Een nieuwe component ProgressBar
* Veel opgeloste problemen

### Bug Fixes {#sites-bug-fixes}

* Componenten in de lay-outcontainer zijn niet zichtbaar wanneer de container Layout is gekopieerd en opnieuw op een pagina wordt geplakt.

* Probleem opgelost met vergroten/verkleinen van lay-outcomponent.

* Toegevoegde capaciteit om het verpletteren van Hoekslechts pagina&#39;s en AEM/Hoekpagina&#39;s te beheren.

### Toegankelijkheid {#accessibility}

* De commentaarrol en de commentaarstatus zijn nu mogelijk voor de items in het menu Pagina **** maken terwijl u in de bladermodus navigeert met de pijl-omlaag.

* Er is een koppeling in de navigatie toegevoegd waarmee gebruikers de hoofdinhoud kunnen overslaan.

* Verbeteringen voor schermlezers.


## Nieuwe functies in AEM als cloudservice {#foundations}

De bouwtijden van het AEM- project zullen verbeteren door alle verwijzingen in pom.xml van het AEM- project aan de verre bewaarplaats te verwijderen `https://downloads.experiencecloud.adobe.com/content/maven/public`.

De AEM als API Jar voor de SDK van de Cloud-service, die eerder op die locatie werd gehost, bevindt zich nu in Maven Central, de standaardopslagplaats voor artefacten van Maven.

## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.6.0.

### What&#39;s New {#what-is-new-cloud-manager}

* Een gebruiker met de rol *Zakelijke eigenaar* in Cloud Manager kan nu een Sandbox-programma verwijderen van de bestemmingspagina (via de knop voor snelle actie op de programmakaart) of van binnen het programma.

   Raadpleeg [Sandbox-programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) verwijderen voor meer informatie.

* Een gebruiker van het Sandbox- programma in de rol van *bedrijfseigenaar* of *plaatsingsmanager* in de Manager van de Wolk kan nu hun Productie en milieu van het Stadium schrappen die via de UI van de Manager van de Wolk wordt geplaatst. De verwijderingsoptie is nu zowel beschikbaar op de kaart Milieu op de pagina Overzicht **van** Programma&#39;s als op de pagina **Milieu** . Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

   Raadpleeg [Sandbox-programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) verwijderen voor meer informatie.

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* Op de pagina **Programmaoverzicht** staan codetekens waarmee u de gebruiker informeert en informeert over de standaardnavigatie in Cloud Manager om deze te starten.

* Er is nu een pagina **LEREN** beschikbaar in Cloud Manager, die toegankelijk is via de bovenste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die zijn toegewezen in Cloud Manager.

* Sandboxprogramma&#39;s worden nu geïdentificeerd door middel van een **Sandbox** -badge die wordt weergegeven op de programmacode op de landingspagina en naast de programmanaam op de pagina **Program Overview** .

* Een gebruiker met de rol SysAdmin heeft nu met één muisklik toegang tot de locatie in Admin Console vanwaar gebruikersrollen of machtigingen voor Cloud Manager kunnen worden beheerd. Een knop Toegang **** beheren is nu beschikbaar op de bestemmingspagina naast de knop Programma **** toevoegen.

   Raadpleeg [SysAdmin-taken](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) voor meer informatie.

* Een gebruiker met de rol SysAdmin heeft nu met één klik rechtstreeks vanuit Cloud Manager toegang tot de instantie van de auteur.

   Zie Toegang [beheren tot instantie](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) Auteur voor meer informatie.

* Het logbestand Build bevat nu een lijst met ontdekte artefacten, waaronder overgeslagen inhoudspakketten.

* De stap Build controleert nu of alle gegenereerde inhoudspakketten alle verplichte eigenschappen (naam, groep en versie) bevatten.

* De stap Build controleert nu of de build ten minste één inhoudspakket heeft geproduceerd.

### Bug Fixes {#bug-fixes-cm}

* In bepaalde situaties zijn de pictogrammen in het dialoogvenster **Programma** maken onjuist uitgelijnd.

* De AEM-release-id wordt niet consistent weergegeven op de pagina Overzicht **van** programma&#39;s.

* Wanneer het vormen van de productiepijpleiding, was de **Geplande optie van de Plaatsing** niet zichtbaar voor sommige klanten.

### Bekende problemen {#known-issues-cm}

* De omgevingen in een Sandbox-programma worden gehiberd wanneer gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Deze status wordt niet waargenomen in Cloud Manager. De status kan echter worden waargenomen via de Developer Console. Dit probleem wordt in een komende release opgelost.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager geeft de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer. Om dit aan te pakken, één keer in de Console van de Ontwikkelaar, voeg het patroon `#release-cm-p1234-e5678` aan het eind van url toe, waar *1234* identiteitskaart van het Programma en *5678* milieu identiteitskaart is Dit probleem wordt in een komende release opgelost.

## Nieuwe functies in [!DNL Adobe Experience Manager Assets] {#aem-assets}

<!-- 
Assets RNs are being authored and are a work in progress.
PM/EM review required before publishing.
-->

**Gebruikerservaring met instructies voor verbeterde slimme tags, aangedreven door Adobe Sensei**

Met verbeterde slimme tags kunnen organisaties slimme-tagmodellen trainen om images te herkennen op basis van klantspecifieke bedrijfstags, naast algemene slimme tags.

Met deze release is er een nieuwe, geleide gebruikerservaring die helpt slimme tags te trainen voor sets klantspecifieke tags en deze te trainen met middelen die in de toekomst moeten worden herkend en gecodeerd. Dit is een meer intuïtieve ervaring.
Verbeterde slimme tags voor meer intuïtieve training voor slimme tags. Zie [hoe u slimme tags](/help/assets/smart-tags.md) kunt toepassen en slimme tags kunt [configureren](/help/assets/smart-tags-configuration.md).

**Ondersteuning voor inname, voorvertoning en levering van 3D-inhoud**

Organisaties kunnen nu 3D-bestanden opslaan en gebruiken in AEM-elementen. De gebruiker kan, een voorproef, en hefboomwerking een verscheidenheid van kern 3D dossiers, met inbegrip van .obj, .stl, .gltf, en .glb dossiers uploaden. Met de toevoeging van [!DNL Dynamic Media], kunnen 3D ervaringen worden gevormd en via agnostische URLs of kijkers worden geleverd. Dit omvat een [!DNL Dynamic Media] 3D Experience Viewer, de component Sites 3D Viewer en de mogelijkheid om 3D-bestanden te leveren via [!DNL Dynamic Media] (AR/VR). Zie [Werken met 3D-elementen in dynamische media](/help/assets/dynamic-media/assets-3d.md).

**Ondersteuning voor Adobe Asset Link voor Adobe XD**

Met de nieuwste release [!DNL Experience Manager Assets] biedt u ondersteuning voor een nieuwe [!DNL Adobe Asset Link] plug-in die wordt losgelaten met [!DNL Adobe XD] versie 29.3. Dankzij de integratie hebben ontwerpers toegang tot elementen en kunnen ze deze gebruiken vanuit [!DNL Experience Manager] hun ontwerpen, zonder dat ze de [!DNL Adobe XD] toepassing hoeven te verlaten. Zie [Adobe Asset Link voor Adobe XD-documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html).

Met deze release kunnen creatieve gebruikers en ontwerpers nu werken met middelen die worden beheerd in [!DNL AEM Assets] een groot aantal Creative Cloud-bureaubladtoepassingen, zoals [!DNL Adobe Asset Link] , [!DNL Adobe XD], [!DNL Photoshop]en [!DNL Illustrator][!DNL InDesign].

**Verbeteringen voor toegankelijkheid**

[!DNL Adobe Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG) v2.1-richtlijnen. De toegankelijkheid is verbeterd voor de volgende gebruiksgevallen of interfaces:

* Gebruikersinterface-elementen, besturingselementen, pagina&#39;s en dialoogvensters zijn schermlezervriendelijk.
* Gebruikersinterface-elementen, besturingselementen en invoerformuliervelden zijn toegankelijk via het toetsenbord.
* Verandering in kleur of contrast van sommige interface-elementen om deze beter te kunnen onderscheiden door gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie. Elementen hebben nu bijvoorbeeld het juiste contrast in de pictogrammen voor sterwaardering op de [!UICONTROL Properties] pagina en in de kaartweergave.

**Andere verbeteringen**

De release biedt de volgende aanvullende verbeteringen:

* Mogelijkheid om elementen opnieuw te verwerken met profielen voor middelenverwerking, zodat gebruikers volledige controle hebben over het proces (volledige verwerking van bedrijfsmiddelen uitvoeren, gewoon een specifiek verwerkingsprofiel toepassen en beslissen of de naverwerkingsworkflow moet worden uitgevoerd).
* Zoekopdrachten retourneren nu sneller resultaten wanneer de onderliggende clusterinstantie achter de schermen opnieuw is gestart (de eerste zoekopdracht kan in een dergelijk geval langer duren).
* Sorteren op &#39;Naam&#39; wanneer elementen in de lijstweergave in de interface Middelen en in de zoekresultaten worden weergegeven. Zie [zoekmiddelen](/help/assets/search-assets.md#sort).
* Sorteren op &#39;Gemaakt&#39; (Datum) wanneer elementen worden weergegeven in de lijstweergave in de interface Middelen en in de zoekresultaten. Zie [zoekmiddelen](/help/assets/search-assets.md#sort).
* Ondersteuning voor het converteren van EPS-bestanden naar afbeeldingen met behulp van de asset microservices.

### Bug Fixes {#assets-bug-fixes}

<!-- TBD: Add enhancements above and bug fixes below.
Seek DM bug fixes if any.
Add Nui update as shared on Slack: https://git.corp.adobe.com/nui/app/releases/tag/22
-->

Naast de bovenstaande nieuwe functies biedt de huidige release de volgende verbeteringen en foutoplossingen op basis van feedback van klanten voor [!DNL Assets].

* Voor MP3-muziekbestanden werkt de afspeelknop die op de miniatuur in de DAM-voorvertoning wordt weergegeven, niet. (CQ-4294731)
* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart. (GRANITE-26895)
* Als u te veel afbeeldingen weergeeft nadat u door een groot aantal zoekresultaten hebt geschoven, loopt de browser vast. (GRANITE-26432)
* De [!UICONTROL Options]-, [!UICONTROL Scope]- en [!UICONTROL Workflows] voortgangsindicatoren op de [!UICONTROL Manage Publication] pagina worden door de schermlezer niet gelezen als voortgangsindicatoren. In plaats daarvan zien schermlezers deze statusindicatoren als een tablijst. (CQ-4273/015)
* Als bij het downloaden van middelen de optie E-mail is geselecteerd en zelfs als een geldige e-mailadres is opgegeven, is de optie Downloaden niet beschikbaar. (CQ-4296535)

* Wanneer gebruikers tags aan [!UICONTROL Properties] pagina&#39;s van een element toevoegen, bladeren ze door een boomstructuur met codes. De structuur van de structuur is niet toegankelijk omdat gebruikers van schermlezers tijdens het navigeren niets horen. (CQ-4272964)
* In het dialoogvenster voor het delen van koppelingen navigeert de schermlezer in de bladermodus,

   * De tabelgegevens worden van commentaar voorzien zodra het dialoogvenster wordt geladen.
   * kan niet naar alle vermelde automatische suggesties navigeren.
   * maakt geen commentaar op de weergegeven automatische suggesties voor de [!UICONTROL Add Email Address/Search] keuzelijst met invoervak. (CQ-4294232)

* De sleepopties werken niet met het toetsenbord in de NVDA-bladermodus in de metagegevensschemaeditor. (CQ-4296326)
* In de gebruikersinterface Middelen zijn de weergave-instellingen niet toegankelijk via het toetsenbord. (CQ-4289038)
* Aangepaste filters die zijn opgeslagen als slimme verzamelingen, worden niet correct toegepast op elementen. (CQ-4294942)
* De veelvoudige onderzoek en indexerende verhogingen en insectenmoeilijke situaties om prestaties te verbeteren. (CQ-4286373)
* De lichtsterkteverhouding voor geelgekleurde classificatiepictogrammen is minder dan 3:1. Het is niet nuttig voor gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie. De classificatiesterren worden weergegeven in de [!UICONTROL Rating] sectie van het [!UICONTROL Advanced] tabblad in de asset- [!UICONTROL Properties] of kaartweergave (CQ-4295106)
* In de keuzelijst met keuzelijsten met invoervakken (in verschillende velden op verschillende pagina&#39;s) worden nu vermeldingen weergegeven als een lijst met opties die door schermlezers kunnen worden aangekondigd. (CQ-4294/017)
* De pijl-omhoog in het deelvenster [!UICONTROL Timeline] kan niet worden geopend met een toetsenbord om een workflow toe te passen op een element. (CQ-4289268)
* De opties (voor [!UICONTROL x]) voor het verwijderen van alle geselecteerde codes onder het [!UICONTROL Tags] veld op het [!UICONTROL Basic] tabblad [!UICONTROL Properties] zijn nu toegankelijk voor schermlezers. (CQ-4273/033)
* Alleen-lezen formuliervelden (bijvoorbeeld uitgeschakelde velden op [!UICONTROL Basic tab] element [!UICONTROL Properties]) kunnen nu met het toetsenbord worden geactiveerd. (CQ-4273031)
* De optie om filterzijbalk te openen kan nu met het toetsenbord worden geopend. (CQ-4273/018)
* Het doel van verschillende keuzelijstelelementen (zoals het veld Pad en de optie om het dialoogvenster Selectie te openen op het tabblad Standaard van Eigenschappen van element) worden nu correct door schermlezers aangekondigd. (CQ-4273/016)
* [!UICONTROL Metadata Schema Editor] De pagina en de bijbehorende elementen zijn niet toegankelijk met het toetsenbord en zijn niet compatibel met schermlezers. (CQ-4272953)
* Besturingselementen voor videovolume zijn niet toegankelijk via een toetsenbord. (CQ-4272696)
* Veel actioneerbare opties in de gebruikersinterface Elementen geven geen focus aan wanneer u het toetsenbord gebruikt. (CQ-4272694)
* Gebruikers van schermlezers weten niet dat de rijen in de lijstweergave selecteerbaar zijn wanneer ze een toetsenbord gebruiken. De informatie wordt alleen aangekondigd wanneer de muis op de rijen wordt geplaatst. (CQ-4271824)
* Sommige formuliervelden, zoals de velden gebruikersnaam en wachtwoord op de aanmeldingspagina, vertrouwen alleen op plaatsaanduidingswaarden voor een toegankelijk label. (CQ-4271716)
* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties (voor koptekst- en zoomopties op de elementenpagina, mapnavigatie), zijn nu toegankelijk met een toetsenbord. (CQ-4271412)
* De titels van alle gebrowste pagina&#39;s op [!DNL Adobe Experience Manager] Elementen zijn nu uniek. (CQ-4271409)
