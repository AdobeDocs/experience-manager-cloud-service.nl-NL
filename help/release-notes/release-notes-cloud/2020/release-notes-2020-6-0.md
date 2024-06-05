---
title: Opmerkingen bij de release van Adobe Experience Manager as a Cloud Service voor 2020.6.0
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2020.6.0."
exl-id: fd6ebe2b-6d98-498c-a45d-b9a9c34e6be7
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1915'
ht-degree: 0%

---

# Opmerkingen bij de release voor AEM as a Cloud Service versie 2020.6.0 {#release-notes}

Deze pagina schetst de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.6.0 is 4 juni 2020.

## Nieuwe functies in AEM Sites {#aem-sites}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor AEM Sites in AEM as a Cloud Service Versie 2020.6.0.

### Nieuwe functies {#whats-new-2020.6.0}

Release 2.9.0 van de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) is nu beschikbaar als onderdeel van AEM Sites, waaronder:

* Integratie tussen [Gegevenslaag client-Adobe](https://github.com/adobe/adobe-client-data-layer) en de kerncomponenten
* Configureerbare HTML ID-kenmerken voor alle componenten
* Een nieuwe component ProgressBar
* Veel opgeloste problemen

### Opgeloste problemen {#sites-bug-fixes}

* Componenten in de lay-outcontainer zijn niet zichtbaar wanneer de container Layout is gekopieerd en opnieuw op een pagina wordt geplakt.

* Probleem opgelost met vergroten/verkleinen van layoutcomponent.

* Toegevoegde capaciteit om het verpletteren van Angular slechts pagina&#39;s en AEM/Angular pagina&#39;s te beheren.

### Toegankelijkheid {#accessibility}

* De commentaarrol en de staat zijn nu mogelijk voor de items in de metselaar in de **Pagina maken** tijdens het navigeren in de bladermodus met de pijl omlaag.

* Een koppeling in de navigatie toegevoegd waarmee gebruikers de hoofdinhoud kunnen overslaan.

* Verbeteringen voor schermlezers.

## Nieuwe functies in stichtingen in AEM as a Cloud Service {#foundations}

AEM project bouwt tijden zal verbeteren door alle verwijzingen in het AEM project pom.xml aan de verre bewaarplaats te verwijderen `https://downloads.experiencecloud.adobe.com/content/maven/public`.

De AEM as a Cloud Service SDK API Jar, die voorheen op die locatie werd gehost, bevindt zich nu in Maven Central, de standaardopslagplaats van Maven.

## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Manager in AEM as a Cloud Service release 2020.6.0.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* Een gebruiker in het dialoogvenster *Zakelijke eigenaar* rol in Cloud Manager kan nu een Sandbox-programma verwijderen van de bestemmingspagina (via de knop voor snelle actie op de programmakaart) of van binnen het programma.

  Zie [Een Sandbox-programma verwijderen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) voor meer informatie .

* Een gebruiker van het Sandbox-programma in *Zakelijke eigenaar* of *Implementatiebeheer* rol in Cloud Manager kan nu hun productie- en werkgebiedomgeving verwijderen die is ingesteld via de interface van Cloud Manager. De verwijderoptie is nu beschikbaar via de milieucaart op de **Overzicht van programma&#39;s** en de **Omgevingen** pagina. Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

  Zie [Een Sandbox-programma verwijderen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) voor meer informatie .

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* De tekens van de coating op **Programmaoverzicht** pagina om de gebruiker te informeren en te instrueren over de standaardnavigatie in Cloud Manager om deze te starten.

* A **LEREN** Deze pagina is nu beschikbaar in Cloud Manager en is toegankelijk via de bovenste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die zijn toegewezen in Cloud Manager.

* Sandbox-programma&#39;s worden nu geïdentificeerd door middel van een **Sandbox** badge die wordt weergegeven op de programmakaart op de landingspagina en naast de naam van het programma in het dialoogvenster **Programmaoverzicht** pagina.

* Een gebruiker in de rol SysAdmin heeft nu met één klik toegang tot de plaats in Admin Console van waar de gebruikersrollen of de toestemmingen aan de Manager van de Wolk kunnen worden beheerd. A **Toegang beheren** Deze knop is nu beschikbaar op de landingspagina naast de **Programma toevoegen** knop.

  Zie [SysAdmin-taken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) voor meer informatie .

* Een gebruiker met de rol SysAdmin heeft nu met één klik rechtstreeks vanuit Cloud Manager toegang tot de instantie van de auteur.

  Zie [Toegang tot instantie Auteur beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) voor meer informatie .

* Het logbestand Build bevat nu een lijst met ontdekte artefacten, waaronder overgeslagen inhoudspakketten.

* De stap Build controleert nu of alle gegenereerde inhoudspakketten alle verplichte eigenschappen (naam, groep en versie) bevatten.

* De stap Build controleert nu of de build ten minste één inhoudspakket heeft geproduceerd.

### Opgeloste problemen {#bug-fixes-cm}

* In bepaalde situaties worden de pictogrammen in de **Programma maken** is onjuist uitgelijnd.

* De AEM release-id wordt niet consistent weergegeven op het tabblad **Overzicht van programma&#39;s** pagina.

* Wanneer het vormen van de productiepijplijn, **Geplande implementatie** deze optie is voor sommige klanten niet zichtbaar.

### Bekende problemen {#known-issues-cm}

* De omgevingen in een Sandbox-programma zijn gehiberd wanneer gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Deze status wordt niet waargenomen in Cloud Manager. De status kan echter worden waargenomen via de Developer Console. Dit probleem wordt in een komende release opgelost.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager geeft de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer. Voeg het patroon toe om dit probleem te verhelpen, eenmaal in de Developer Console `#release-cm-p1234-e5678` aan het einde van de URL, waarbij *1234* is de programma-id en *5678* is de milieu-id. Dit probleem wordt in een komende release opgelost.

## Nieuwe functies in [!DNL Adobe Experience Manager Assets] {#aem-assets}

**Gebruikerservaring met instructies voor verbeterde slimme tags, aangedreven door Adobe Sensei**

Met verbeterde slimme tags kunnen organisaties slimme-tagmodellen trainen om images te herkennen op basis van klantspecifieke bedrijfstags, naast algemene slimme tags.

Met deze release is er een nieuwe, geleide gebruikerservaring die helpt slimme tags te trainen voor sets klantspecifieke tags en deze te trainen met middelen die in de toekomst moeten worden herkend en gecodeerd. De ervaring is nu intuïtiever.
Verbeterde slimme tags voor meer intuïtieve training voor slimme tags. Zie [hoe u slimme tags aan elementen kunt toevoegen](/help/assets/smart-tags.md).

**Ondersteuning voor inname, voorvertoning en levering van 3D-inhoud**

Organisaties kunnen nu 3D-bestanden opslaan en gebruiken in AEM Assets. De gebruiker kan diverse 3D-kernbestanden uploaden, voorvertonen en gebruiken, waaronder OBJ-, STL-, GLTF- en GLB-bestanden. Met toevoeging van [!DNL Dynamic Media]kunt u 3D-ervaringen configureren en leveren met behulp van agnostische URL&#39;s of viewers. Dit omvat een [!DNL Dynamic Media] 3D Experience Viewer, de component Sites 3D Viewer en de mogelijkheid om 3D-bestanden te leveren via [!DNL Dynamic Media] (AR/VR). Zie [Werken met 3D-elementen in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Adobe Asset Link-ondersteuning voor Adobe XD**

Met de nieuwste release, [!DNL Experience Manager Assets] ondersteunt een nieuwe [!DNL Adobe Asset Link] insteekmodule die wordt losgelaten met [!DNL Adobe XD] v29.3 Dankzij de integratie hebben ontwerpers toegang tot middelen en kunnen ze deze gebruiken vanuit [!DNL Experience Manager] in hun ontwerpen, zonder dat het nodig is [!DNL Adobe XD] toepassing. Zie [Adobe Asset Link voor Adobe XD-documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html).

Met deze release kunnen creatieve gebruikers en ontwerpers nu werken met middelen die worden beheerd in [!DNL AEM Assets] gebruiken [!DNL Adobe Asset Link] in een reeks bureaubladtoepassingen voor Creatives Cloud, waaronder [!DNL Adobe XD], [!DNL Photoshop], [!DNL Illustrator], en [!DNL InDesign].

**Verbeteringen voor toegankelijkheid**

[!DNL Adobe Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG) v2.1-richtlijnen. De toegankelijkheid is verbeterd voor de volgende gebruiksgevallen of interfaces:

De elementen van de gebruikersinterface zijn schermlezervriendelijk, zijn toegankelijk met een toetsenbord en hebben een beter contrast. Hieronder vindt u een gedetailleerde lijst met verbeteringen:

* De [!UICONTROL Options], [!UICONTROL Scope], en [!UICONTROL Workflows] voortgangsbalken ingeschakeld [!UICONTROL Manage Publication] De pagina wordt niet door de schermlezer gelezen als voortgangsbalk. In plaats daarvan zien schermlezers deze statusindicatoren als een tablijst. (CQ-4273/015)

* Bij het toevoegen van tags in [!UICONTROL Properties] op een elementpagina door een boomstructuur met codes te navigeren. De structuur van de structuur is niet toegankelijk omdat gebruikers van schermlezers tijdens het navigeren niets horen. (CQ-4272964)

* In het dialoogvenster voor het delen van koppelingen navigeert de schermlezer in de bladermodus,

   * Hiermee worden de tabelgegevens meteen vermeld wanneer het dialoogvenster wordt geladen.
   * Kan niet naar alle vermelde automatische suggesties navigeren.
   * De weergegeven automatische suggesties voor de [!UICONTROL Add Email Address/Search] invoervak. (CQ-4294232)

* De [!UICONTROL Metadata Schema Editor] De pagina en de bijbehorende elementen zijn nu toegankelijk via een toetsenbord en zijn schermlezervriendelijk. (CQ-4272953) Gebruikers kunnen de componenten slepen met het toetsenbord in de NVDA-bladermodus. (CQ-4296326)

* In de gebruikersinterface Middelen zijn de weergave-instellingen niet toegankelijk via het toetsenbord. (CQ-4289038)

* De lichtsterkteverhouding voor geelgekleurde classificatiepictogrammen is minder dan 3:1. Het is niet nuttig voor gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie. De classificatiesterren worden weergegeven op het tabblad in de asset- of kaartweergave

* De kleur en het contrast van bepaalde elementen van de gebruikersinterface worden bijgewerkt, zodat gebruikers met een beperkt gezichtsvermogen of gebruikers zonder kleurperceptie deze elementen van de gebruikersinterface kunnen onderscheiden. De kleur van sterrenclassificatiepictogrammen in het dialoogvenster [!UICONTROL Rating] deel van [!UICONTROL Advanced] in de [!UICONTROL Properties] van een actief en in de kaartweergave worden gewijzigd voor het juiste contrast. (CQ-4295/106)

* De schermlezers kunnen nu de items in het pop-upmenu met keuzelijsten met invoervak (in verschillende velden op verschillende pagina&#39;s) lezen als een lijst met opties. (CQ-4294/017)

* Als u een workflow wilt toepassen op een element, klikt u op de pijl chevron in het dialoogvenster [!UICONTROL Timeline] kan worden benaderd met een toetsenbord. (CQ-4289268)

* Gebruikers kunnen de geselecteerde tags uit de [!UICONTROL Tags] veld in [!UICONTROL Basic] tabblad van een element [!UICONTROL Properties] pagina gebruiken `x` symbool. De schermlezers geven nu het doel en het aantal geselecteerde labels aan (CQ-4273033).

* De formuliervelden alleen-lezen kunnen worden gebruikt met een toetsenbord. De uitgeschakelde velden op [!UICONTROL Basic] op een element [!UICONTROL Properties] pagina. (CQ-4273031)

* Open nu met een toetsenbord de opties voor het filteren van elementen in de linkerzijbalk. (CQ-4273/018)

* De schermlezer kondigt het doel aan van verschillende keuzelijstelementen, zoals het veld Pad en de optie om het dialoogvenster Selectie te openen in [!UICONTROL Basic] tabblad van een element [!UICONTROL Properties] pagina. (CQ-4273/016)

* De volumeregelaars voor video&#39;s zijn toegankelijk via een toetsenbord. (CQ-4272696)

* Veel actioneerbare opties in de gebruikersinterface Elementen geven geen focus aan wanneer u het toetsenbord gebruikt. (CQ-4272694)

* Gebruikers van schermlezers weten nu wanneer de rijen in de lijstweergave met een toetsenbord kunnen worden geselecteerd. De informatie wordt aangekondigd wanneer de aanwijzer op de rijen wordt geplaatst. (CQ-4271824)

* Sommige formuliervelden, zoals de velden voor gebruikersnaam en wachtwoord op de aanmeldingspagina, zijn afhankelijk van plaatsaanduidingswaarden voor een toegankelijk label. (CQ-4271716)

* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties, zoals opties voor koptekst en zoomen op de elementenpagina of mapnavigatie, zijn nu toegankelijk met een toetsenbord. (CQ-4271412)

* Titels van alle bladerpagina&#39;s op [!DNL Adobe Experience Manager] Elementen zijn nu uniek. (CQ-4271409)

**Andere verbeteringen**

De release biedt de volgende andere verbeteringen:

* Mogelijkheid om elementen opnieuw te verwerken met profielen voor middelenverwerking, zodat gebruikers volledige controle hebben over het proces (volledige verwerking van bedrijfsmiddelen uitvoeren, gewoon een specifiek verwerkingsprofiel toepassen en beslissen of de naverwerkingsworkflow moet worden uitgevoerd).
* Zoekopdrachten retourneren nu sneller resultaten wanneer de onderliggende clusterinstantie achter de schermen opnieuw is gestart (de eerste zoekopdracht kan in een dergelijk geval langer duren).
* Sorteren op &#39;Naam&#39; wanneer elementen in de lijstweergave in de interface Middelen en in de zoekresultaten worden weergegeven. Zie [zoekelementen](/help/assets/search-assets.md#sort).
* Sorteer op &#39;Gemaakt&#39; (Datum) wanneer u elementen weergeeft in de lijstweergave in de interface Middelen en in de zoekresultaten. Zie [zoekelementen](/help/assets/search-assets.md#sort).
* Ondersteuning voor het converteren van EPS-bestanden naar afbeeldingen met behulp van de asset microservices.

### Opgeloste problemen {#assets-bug-fixes}

Naast de bovengenoemde nieuwe eigenschappen, verstrekt de huidige versie de volgende insectenmoeilijke situaties die op klant worden gebaseerd terugkoppelt voor [!DNL Assets].

* Voor MP3-muziekbestanden werkt de afspeelknop die op de miniatuur in de DAM-voorvertoning wordt weergegeven, niet. (CQ-4294731)
* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart. (GRANITE-26895)
* Als u te veel afbeeldingen weergeeft nadat u door veel zoekresultaten hebt geschoven, loopt de browser vast. (GRANITE-26432)
* Als bij het downloaden van middelen de optie E-mail is geselecteerd en zelfs als een geldige e-mailadres is opgegeven, is de optie Downloaden niet beschikbaar. (CQ-4296535)
* Aangepaste filters die zijn opgeslagen als slimme verzamelingen, worden niet correct toegepast op elementen. (CQ-4294942)
* De veelvoudige onderzoek en indexerende verhogingen en insectenmoeilijke situaties om prestaties te verbeteren. (CQ-4286373)
* Het tabblad Eigenschappen van map kan niet worden geopend in Middelen en retourneert een fout van 500. (CQ-4295701)
