---
title: Opmerkingen bij de release van Adobe Experience Manager as a Cloud Service voor 2020.6.0
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2020.6.0."
exl-id: fd6ebe2b-6d98-498c-a45d-b9a9c34e6be7
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1915'
ht-degree: 0%

---

# Opmerkingen bij de release voor AEM as a Cloud Service 2020.6.0 {#release-notes}

Deze pagina beschrijft de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.6.0 is 4 juni 2020.

## Nieuwe functies in AEM Sites {#aem-sites}

Volg deze sectie voor meer informatie over wat nieuw is en de updates voor AEM Sites in AEM as a Cloud Service Release 2020.6.0.

### Nieuwe functies {#whats-new-2020.6.0}

Versie 2.9.0 van de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) is nu beschikbaar als deel van AEM Sites met inbegrip van:

* De integratie tussen [&#x200B; Laag van de Gegevens van de Cliënt van de Adobe &#x200B;](https://github.com/adobe/adobe-client-data-layer) en de Componenten van de Kern
* Configureerbare HTML ID-kenmerken voor alle componenten
* Een nieuwe component ProgressBar
* Veel opgeloste problemen

### Opgeloste problemen {#sites-bug-fixes}

* Componenten in de lay-outcontainer zijn niet zichtbaar wanneer de container Layout is gekopieerd en opnieuw op een pagina wordt geplakt.

* Probleem opgelost met vergroten/verkleinen van layoutcomponent.

* Toegevoegde capaciteit om het verpletteren van Angular slechts pagina&#39;s en AEM/Angular pagina&#39;s te beheren.

### Toegankelijkheid {#accessibility}

* De rol en de staat van het commentaar zijn nu mogelijk voor de punten van de Metetijd in **creëren de dialoog van de Pagina** terwijl het navigeren op de het doorbladeren wijze gebruikend benedenpijl.

* Een koppeling in de navigatie toegevoegd waarmee gebruikers de hoofdinhoud kunnen overslaan.

* Verbeteringen voor schermlezers.

## Nieuwe functies in stichtingen in AEM as a Cloud Service {#foundations}

AEM de bouwtijden van het project zullen verbeteren door alle verwijzingen in pom.xml van het AEM project aan de verre bewaarplaats `https://downloads.experiencecloud.adobe.com/content/maven/public` te verwijderen.

De AEM as a Cloud Service SDK API Jar, die voorheen op die locatie werd gehost, bevindt zich nu in Maven Central, de standaardopslagplaats van Maven.

## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over wat nieuw is en de updates voor Cloud Manager in AEM as a Cloud Service Release 2020.6.0.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* Een gebruiker in de *rol van 0&rbrace; BedrijfsEigenaar &lbrace;in Cloud Manager kan nu een Programma Sandbox van de landende pagina (via snelle actieknoop op de kaart van het Programma) of van binnen het programma schrappen.*

  Zie [&#x200B; het Schrappen van een Programma Sandbox &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=nl-NL) voor meer details.

* Een gebruiker van het Programma van Sandbox in *BedrijfsEigenaar* of *de rol van de Manager van de Plaatsing* in Cloud Manager kan nu hun Productie en milieu schrappen van het Stadium dat via Cloud Manager UI wordt geplaatst. De schrappingsoptie is nu beschikbaar van zowel de kaart van het Milieu op de **pagina van het Overzicht van Programma&#39;s 0&rbrace; als de** pagina van Milieu **.** Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

  Zie [&#x200B; het Schrappen van een Programma Sandbox &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=nl-NL) voor meer details.

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* De tekens van de cokes op de **pagina van het Overzicht van het 0&rbrace; Programma om de gebruiker over basisnavigatie binnen Cloud Manager te informeren en te instrueren om hen te krijgen begonnen.**

* A **LEARN** pagina is nu beschikbaar in Cloud Manager, toegankelijk via de hoogste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die in Cloud Manager zijn toegewezen.

* De Programma&#39;s van zandbak worden nu geïdentificeerd door middel van a **zandbak** badge die op de programmakaart op de landende pagina en naast de programmanaam in de **pagina van het Overzicht van het Programma** wordt getoond.

* Een gebruiker in de rol SysAdmin heeft nu met één klik toegang tot de plaats in Admin Console van waar de gebruikersrollen of de toestemmingen aan Cloud Manager kunnen worden beheerd. A **beheert de knoop van de Toegang** is nu beschikbaar op de het landen pagina naast **voeg Programma** knoop toe.

  Zie &lbrace;de Taken SysAdmin [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=nl-NL#sysadmin-tasks) voor meer details.

* Een gebruiker met de rol SysAdmin heeft nu met één klik rechtstreeks vanuit Cloud Manager toegang tot de instantie van de auteur.

  Zie [&#x200B; het Leiden Toegang tot de Instantie van de Auteur &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=nl-NL#manage-access-aem) voor meer details.

* Het logbestand Build bevat nu een lijst met ontdekte artefacten, waaronder overgeslagen inhoudspakketten.

* De stap Build controleert nu of alle gegenereerde inhoudspakketten alle verplichte eigenschappen (naam, groep en versie) bevatten.

* De stap Build controleert nu of de build ten minste één inhoudspakket heeft geproduceerd.

### Opgeloste problemen {#bug-fixes-cm}

* In bepaalde situaties, werden de pictogrammen in de **Create dialoog van het Programma** verkeerd gericht.

* Het AEM versieherkenningsteken werd niet constant getoond op de **pagina van het Overzicht van Programma&#39;s**.

* Wanneer het vormen van de productiepijpleiding, was de **Geplande optie van de Plaatsing** niet zichtbaar voor sommige klanten.

### Bekende problemen {#known-issues-cm}

* De omgevingen in een Sandbox-programma zijn gehiberd wanneer gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Deze status wordt niet waargenomen in Cloud Manager. De status kan echter via Developer Console worden waargenomen. Dit probleem wordt in een komende release opgelost.

* De koppeling naar de Developer Console rechtstreeks vanuit Cloud Manager geeft niet de optie weer om de omgeving van een Sandbox-programma te dehiberneren of te hiberneren. Om dit, eens bij Developer Console te richten, voeg het patroon `#release-cm-p1234-e5678` aan het eind van url toe, waar *1234* identiteitskaart van het Programma is en *5678* is Milieu identiteitskaart Dit probleem wordt in een komende release opgelost.

## Nieuwe functies in [!DNL Adobe Experience Manager Assets] {#aem-assets}

**Geleide Ervaring van de Gebruiker voor Verbeterde Slimme Markeringen, aangedreven door Adobe Sensei**

Met verbeterde slimme tags kunnen organisaties slimme-tagmodellen trainen om images te herkennen op basis van klantspecifieke bedrijfstags, naast algemene slimme tags.

Met deze release is er een nieuwe, geleide gebruikerservaring die helpt slimme tags te trainen voor sets klantspecifieke tags en deze te trainen met middelen die in de toekomst moeten worden herkend en gecodeerd. De ervaring is nu intuïtiever.
Verbeterde slimme tags voor meer intuïtieve training voor slimme tags. Zie [&#x200B; hoe te om slimme markeringen aan activa &#x200B;](/help/assets/smart-tags.md) toe te voegen.

**Steun voor opname, voorproef, en levering van 3D inhoud**

Organisaties kunnen nu 3D-bestanden opslaan en gebruiken in AEM Assets. De gebruiker kan diverse 3D-kernbestanden uploaden, voorvertonen en gebruiken, waaronder OBJ-, STL-, GLTF- en GLB-bestanden. Met de toevoeging van [!DNL Dynamic Media] kunt u 3D-ervaringen configureren en leveren met behulp van agnostische URL&#39;s of viewers. Dit omvat een [!DNL Dynamic Media] 3D Experience Viewer, de component Sites 3D Viewer en de mogelijkheid om 3D-bestanden te leveren via [!DNL Dynamic Media] (AR/VR). Zie [&#x200B; Werkend met 3D activa in Dynamic Media &#x200B;](/help/assets/dynamic-media/assets-3d.md).

**de steun van de Verbinding van Activa van de Adobe voor Adobe XD**

Met de nieuwste versie ondersteunt [!DNL Experience Manager Assets] een nieuwe [!DNL Adobe Asset Link] -plug-in die wordt losgelaten met [!DNL Adobe XD] v29.3. Dankzij de integratie hebben ontwerpers toegang tot elementen van [!DNL Experience Manager] in hun ontwerpen en kunnen ze deze gebruiken zonder dat ze [!DNL Adobe XD] hoeven te verlaten. Zie [&#x200B; Verbinding van Activa van de Adobe voor de documentatie van Adobe XD &#x200B;](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link-for-xd.html).

Met deze release kunnen creatieve gebruikers en ontwerpers nu werken met middelen die worden beheerd in [!DNL AEM Assets] via [!DNL Adobe Asset Link] in een reeks bureaubladtoepassingen voor Creatives Cloud, zoals [!DNL Adobe XD] , [!DNL Photoshop] , [!DNL Illustrator] en [!DNL InDesign] .

**Verbeteringen van de Toegankelijkheid**

[!DNL Adobe Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG) v2.1-richtlijnen. De toegankelijkheid is verbeterd voor de volgende gebruiksgevallen of interfaces:

De elementen van de gebruikersinterface zijn schermlezervriendelijk, zijn toegankelijk met een toetsenbord en hebben een beter contrast. Hieronder vindt u een gedetailleerde lijst met verbeteringen:

* De voortgangsbalken [!UICONTROL Options] , [!UICONTROL Scope] en [!UICONTROL Workflows] op [!UICONTROL Manage Publication] -pagina worden niet door de schermlezer gelezen als voortgangsbalk. In plaats daarvan zien schermlezers deze statusindicatoren als een tablijst. (CQ-4273/015)

* Wanneer gebruikers tags toevoegen aan een [!UICONTROL Properties] -pagina van een element, navigeren ze door een boomstructuur met tags. De structuur van de structuur is niet toegankelijk omdat gebruikers van schermlezers tijdens het navigeren niets horen. (CQ-4272964)

* In het dialoogvenster voor het delen van koppelingen navigeert de schermlezer in de bladermodus,

   * Hiermee worden de tabelgegevens meteen vermeld wanneer het dialoogvenster wordt geladen.
   * Kan niet naar alle vermelde automatische suggesties navigeren.
   * De weergegeven automatische suggesties voor de keuzelijst met invoervak [!UICONTROL Add Email Address/Search] worden niet van commentaar voorzien. (CQ-4294232)

* De pagina [!UICONTROL Metadata Schema Editor] en de bijbehorende elementen zijn nu toegankelijk via een toetsenbord en zijn schermlezervriendelijk. (CQ-4272953) Gebruikers kunnen de componenten slepen met het toetsenbord in de NVDA-bladermodus. (CQ-4296326)

* In de Assets-gebruikersinterface zijn de weergave-instellingen niet toegankelijk via het toetsenbord. (CQ-4289038)

* De lichtsterkteverhouding voor geelgekleurde classificatiepictogrammen is minder dan 3:1. Het is niet nuttig voor gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie. De classificatiesterren worden weergegeven op het tabblad in de asset- of kaartweergave

* De kleur en het contrast van bepaalde elementen van de gebruikersinterface worden bijgewerkt, zodat gebruikers met een beperkt gezichtsvermogen of gebruikers zonder kleurperceptie deze elementen van de gebruikersinterface kunnen onderscheiden. De kleur van sterrenbeoordelingspictogrammen in de sectie [!UICONTROL Rating] van het tabblad [!UICONTROL Advanced] in de [!UICONTROL Properties] van een element en in de kaartweergave wordt bijvoorbeeld gewijzigd voor het juiste contrast. (CQ-4295/106)

* De schermlezers kunnen nu de items in het pop-upmenu met keuzelijsten met invoervak (in verschillende velden op verschillende pagina&#39;s) lezen als een lijst met opties. (CQ-4294/017)

* Als u een workflow op een element wilt toepassen, hebt u via het toetsenbord toegang tot de chevron-pijl in de [!UICONTROL Timeline] . (CQ-4289268)

* Gebruikers kunnen met `x` -symbool geselecteerde tags verwijderen uit het [!UICONTROL Tags] -veld op het tabblad [!UICONTROL Basic] van de pagina [!UICONTROL Properties] van een element. De schermlezers geven nu het doel en het aantal geselecteerde labels aan (CQ-4273033).

* De formuliervelden alleen-lezen kunnen worden gebruikt met een toetsenbord. De uitgeschakelde velden op het tabblad [!UICONTROL Basic] op de pagina [!UICONTROL Properties] van een element. (CQ-4273031)

* Open nu met een toetsenbord de opties voor het filteren van elementen in de linkerzijbalk. (CQ-4273/018)

* De schermlezer kondigt het doel aan van verschillende keuzelijstelementen, zoals het veld Pad en de optie om het dialoogvenster Selectie te openen op het tabblad [!UICONTROL Basic] van de pagina [!UICONTROL Properties] van een element. (CQ-4273/016)

* De volumeregelaars voor video&#39;s zijn toegankelijk via een toetsenbord. (CQ-4272696)

* Veel actiemogelijkheden in de Assets-gebruikersinterface geven geen focus wanneer u het toetsenbord gebruikt. (CQ-4272694)

* Gebruikers van schermlezers weten nu wanneer de rijen in de lijstweergave met een toetsenbord kunnen worden geselecteerd. De informatie wordt aangekondigd wanneer de aanwijzer op de rijen wordt geplaatst. (CQ-4271824)

* Sommige formuliervelden, zoals de velden voor gebruikersnaam en wachtwoord op de aanmeldingspagina, zijn afhankelijk van plaatsaanduidingswaarden voor een toegankelijk label. (CQ-4271716)

* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties, zoals opties voor koptekst en zoomen op de elementenpagina of mapnavigatie, zijn nu toegankelijk met een toetsenbord. (CQ-4271412)

* De titels van alle gebrowste pagina&#39;s op [!DNL Adobe Experience Manager] Assets zijn nu uniek. (CQ-4271409)

**Andere verhogingen**

De release biedt de volgende andere verbeteringen:

* Mogelijkheid om elementen opnieuw te verwerken met profielen voor middelenverwerking, zodat gebruikers volledige controle hebben over het proces (volledige verwerking van bedrijfsmiddelen uitvoeren, gewoon een specifiek verwerkingsprofiel toepassen en beslissen of de naverwerkingsworkflow moet worden uitgevoerd).
* Zoekopdrachten retourneren nu sneller resultaten wanneer de onderliggende clusterinstantie achter de schermen opnieuw is gestart (de eerste zoekopdracht kan in een dergelijk geval langer duren).
* Sorteren op &#39;Naam&#39; wanneer elementen in de lijstweergave in de Assets-interface en in de zoekresultaten worden weergegeven. Zie [&#x200B; onderzoeksactiva &#x200B;](/help/assets/search-assets.md#sort).
* Sorteer op &#39;Gemaakt&#39; (Datum) wanneer u elementen weergeeft in de lijstweergave in de Assets-interface en in de zoekresultaten. Zie [&#x200B; onderzoeksactiva &#x200B;](/help/assets/search-assets.md#sort).
* Ondersteuning voor het converteren van EPS-bestanden naar afbeeldingen met behulp van de asset microservices.

### Opgeloste problemen {#assets-bug-fixes}

Naast de bovenstaande nieuwe functies biedt de huidige release de volgende foutoplossingen op basis van feedback van klanten voor [!DNL Assets] .

* Voor MP3-muziekbestanden werkt de afspeelknop die op de miniatuur in de DAM-voorvertoning wordt weergegeven, niet. (CQ-4294731)
* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart. (GRANITE-26895)
* Als u te veel afbeeldingen weergeeft nadat u door veel zoekresultaten hebt geschoven, loopt de browser vast. (GRANITE-26432)
* Als bij het downloaden van middelen de optie E-mail is geselecteerd en zelfs als een geldige e-mailadres is opgegeven, is de optie Downloaden niet beschikbaar. (CQ-4296535)
* Aangepaste filters die zijn opgeslagen als slimme verzamelingen, worden niet correct toegepast op elementen. (CQ-4294942)
* De veelvoudige onderzoek en indexerende verhogingen en insectenmoeilijke situaties om prestaties te verbeteren. (CQ-4286373)
* Het tabblad Eigenschappen van map kan niet worden geopend in Assets en retourneert een fout van 500. (CQ-4295701)
