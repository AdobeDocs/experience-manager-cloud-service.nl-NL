---
title: Adobe Experience Manager als de Nota's van de Versie van de Cloud Service voor 2020.6.0
description: Opmerkingen bij de release van Experience Manager voor 2020.6.0
translation-type: tm+mt
source-git-commit: fcae90c8e24dbd2994e8700daf22f5dff039b299
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 0%

---


# Opmerkingen bij de release voor AEM als Cloud Service 2020.6.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager beschreven als Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als Cloud Service 2020.6.0 is 4 juni 2020.

## Nieuwe functies in AEM Sites {#aem-sites}

Volg deze sectie om te leren over wat nieuw en de updates voor AEM Sites in AEM als Versie van de Cloud Service 2020.6.0 is.

### What&#39;s New {#whats-new-2020.6.0}

Release 2.9.0 van de [kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) is nu beschikbaar als onderdeel van AEM Sites zoals:

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

## Nieuw in stichtingen in AEM als Cloud Service {#foundations}

De bouwtijden van het AEM- project zullen verbeteren door alle verwijzingen in pom.xml van het AEM- project aan de verre bewaarplaats te verwijderen `https://downloads.experiencecloud.adobe.com/content/maven/public`.

De AEM als Cloud Service SDK API Jar, die eerder op die locatie werd gehost, bevindt zich nu in Maven Central, de standaardopslagplaats van Maven.

## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.6.0.

### What&#39;s New {#what-is-new-cloud-manager}

* Een gebruiker met de rol *Zakelijke eigenaar* in Cloud Manager kan nu een Sandbox-programma verwijderen van de bestemmingspagina (via de knop voor snelle actie op de programmakaart) of van binnen het programma.

   Raadpleeg [Sandbox-programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) verwijderen voor meer informatie.

* Een gebruiker van het Sandbox- programma in de rol van *bedrijfseigenaar* of *plaatsingsmanager* in de Manager van de Wolk kan nu hun Productie en milieu van het Stadium schrappen die via de UI van de Manager van de Wolk wordt geplaatst. De verwijderingsoptie is nu zowel beschikbaar op de kaart Milieu op de pagina Overzicht **van** Programma&#39;s als op de pagina **Milieu** . Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

   Raadpleeg [Sandbox-programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) verwijderen voor meer informatie.

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* Op de pagina **Programmaoverzicht** staan codetekens waarmee u de gebruiker informeert en informeert over de standaardnavigatie in Cloud Manager om deze te starten.

* Er is nu een pagina **LEREN** beschikbaar in Cloud Manager, die toegankelijk is via de bovenste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die zijn toegewezen in Cloud Manager.

* Sandboxprogramma&#39;s worden nu geïdentificeerd door middel van een **Sandbox** -badge die wordt weergegeven op de programmacode op de landingspagina en naast de programmanaam op de pagina **Program Overview** .

* Een gebruiker in de rol SysAdmin heeft nu met één klik toegang tot de plaats in Admin Console van waar de gebruikersrollen of de toestemmingen aan de Manager van de Wolk kunnen worden beheerd. Een knop Toegang **** beheren is nu beschikbaar op de bestemmingspagina naast de knop Programma **** toevoegen.

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

**Gebruikerservaring met instructies voor verbeterde slimme tags, aangedreven door Adobe Sensei**

Met verbeterde slimme tags kunnen organisaties slimme-tagmodellen trainen om images te herkennen op basis van klantspecifieke bedrijfstags, naast algemene slimme tags.

Met deze release is er een nieuwe, geleide gebruikerservaring die helpt slimme tags te trainen voor sets klantspecifieke tags en deze te trainen met middelen die in de toekomst moeten worden herkend en gecodeerd. De ervaring is nu intuïtiever.
Verbeterde slimme tags voor meer intuïtieve training voor slimme tags. Zie [hoe u slimme tags aan elementen](/help/assets/smart-tags.md) kunt toevoegen en slimme tags kunt [configureren](/help/assets/smart-tags-configuration.md).

**Ondersteuning voor inname, voorvertoning en levering van 3D-inhoud**

Organisaties kunnen 3D-bestanden nu opslaan en gebruiken in AEM Assets. De gebruiker kan diverse 3D-kernbestanden uploaden, voorvertonen en gebruiken, waaronder OBJ-, STL-, GLTF- en GLB-bestanden. Met toevoeging van [!DNL Dynamic Media], kunt u 3D ervaringen vormen en leveren gebruikend agnostische URLs of kijkers. Dit omvat een [!DNL Dynamic Media] 3D Experience Viewer, de component Sites 3D Viewer en de mogelijkheid om 3D-bestanden te leveren via [!DNL Dynamic Media] (AR/VR). Zie [Werken met 3D-elementen in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Ondersteuning voor Adobe Asset Link voor Adobe XD**

Met de nieuwste release [!DNL Experience Manager Assets] wordt een nieuwe [!DNL Adobe Asset Link] plug-in ondersteund die wordt uitgebracht met [!DNL Adobe XD] versie 29.3. Dankzij de integratie hebben ontwerpers toegang tot elementen en kunnen ze deze gebruiken vanuit [!DNL Experience Manager] hun ontwerpen, zonder dat ze de [!DNL Adobe XD] toepassing hoeven te verlaten. Zie [Adobe Asset Link voor Adobe XD-documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html).

Met deze release kunnen creatieve gebruikers en ontwerpers nu werken met middelen die worden beheerd in [!DNL AEM Assets] een groot aantal Creative Cloud-bureaubladtoepassingen, zoals [!DNL Adobe Asset Link] , [!DNL Adobe XD], [!DNL Photoshop]en [!DNL Illustrator][!DNL InDesign].

**Verbeteringen voor toegankelijkheid**

[!DNL Adobe Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG) v2.1-richtlijnen. De toegankelijkheid is verbeterd voor de volgende gebruiksgevallen of interfaces:

De elementen van de gebruikersinterface zijn schermlezervriendelijk, zijn toegankelijk met een toetsenbord en hebben een beter contrast. Hieronder vindt u een gedetailleerde lijst met verbeteringen:

* De [!UICONTROL Options], [!UICONTROL Scope]en [!UICONTROL Workflows] voortgangsbalken op de [!UICONTROL Manage Publication] pagina worden niet door de schermlezer gelezen als voortgangsbalk. In plaats daarvan zien schermlezers deze statusindicatoren als een tablijst. (CQ-4273/015)

* Wanneer gebruikers tags aan [!UICONTROL Properties] pagina&#39;s van een element toevoegen, bladeren ze door een boomstructuur met codes. De structuur van de structuur is niet toegankelijk omdat gebruikers van schermlezers tijdens het navigeren niets horen. (CQ-4272964)

* In het dialoogvenster voor het delen van koppelingen navigeert de schermlezer in de bladermodus,

   * Hiermee worden de tabelgegevens meteen vermeld wanneer het dialoogvenster wordt geladen.
   * Kan niet naar alle vermelde automatische suggesties navigeren.
   * De weergegeven automatische suggesties voor de [!UICONTROL Add Email Address/Search] keuzelijst met invoervak worden niet van commentaar voorzien. (CQ-4294232)

* De [!UICONTROL Metadata Schema Editor] pagina en de bijbehorende elementen zijn nu toegankelijk met een toetsenbord en zijn schermlezervriendelijk. (CQ-4272953) Gebruikers kunnen de componenten slepen met het toetsenbord in de NVDA-bladermodus. (CQ-4296326)

* In de gebruikersinterface Middelen zijn de weergave-instellingen niet toegankelijk via het toetsenbord. (CQ-4289038)

* De lichtsterkteverhouding voor geelgekleurde classificatiepictogrammen is minder dan 3:1. Het is niet nuttig voor gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie. De classificatiesterren worden weergegeven op het tabblad in de asset- of kaartweergave

* De kleur en het contrast van bepaalde elementen van de gebruikersinterface worden bijgewerkt, zodat gebruikers met een beperkt gezichtsvermogen of gebruikers zonder kleurperceptie deze elementen van de gebruikersinterface kunnen onderscheiden. De kleur van sterrenbeoordelingspictogrammen in de [!UICONTROL Rating] sectie van het [!UICONTROL Advanced] [!UICONTROL Properties] tabblad in een element en in de kaartweergave wordt bijvoorbeeld gewijzigd voor het juiste contrast. (CQ-4295/106)

* De schermlezers kunnen nu de items in het pop-upmenu met keuzelijsten met invoervak (in verschillende velden op verschillende pagina&#39;s) lezen als een lijst met opties. (CQ-4294/017)

* Als u een workflow op een element wilt toepassen, [!UICONTROL Timeline] kunt u de chevron-pijl in het element openen met een toetsenbord. (CQ-4289268)

* Gebruikers kunnen geselecteerde tags in het [!UICONTROL Tags] veld op het [!UICONTROL Basic] tabblad van de [!UICONTROL Properties] pagina van een element verwijderen met behulp van `x` symbolen. De schermlezers geven nu het doel en het aantal geselecteerde labels aan (CQ-4273033).

* De formuliervelden alleen-lezen kunnen worden gebruikt met een toetsenbord. De uitgeschakelde velden op het [!UICONTROL Basic] tabblad op de [!UICONTROL Properties] pagina van een element. (CQ-4273031)

* Open nu met een toetsenbord de opties voor het filteren van elementen in de linkerzijbalk. (CQ-4273/018)

* De schermlezer kondigt het doel aan van verschillende keuzelijstelementen, zoals het veld Pad en de optie om het dialoogvenster Selectie te openen op het [!UICONTROL Basic] tabblad van de [!UICONTROL Properties] pagina van een element. (CQ-4273/016)

* De volumeregelaars voor video&#39;s zijn toegankelijk via een toetsenbord. (CQ-4272696)

* Veel actioneerbare opties in de gebruikersinterface Elementen geven geen focus aan wanneer u het toetsenbord gebruikt. (CQ-4272694)

* Gebruikers van schermlezers weten nu wanneer de rijen in de lijstweergave met een toetsenbord kunnen worden geselecteerd. De informatie wordt aangekondigd wanneer de aanwijzer op de rijen wordt geplaatst. (CQ-4271824)

* Sommige formuliervelden, zoals de velden voor gebruikersnaam en wachtwoord op de aanmeldingspagina, zijn afhankelijk van plaatsaanduidingswaarden voor een toegankelijk label. (CQ-4271716)

* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties, zoals opties voor koptekst en zoomen op de elementenpagina of mapnavigatie, zijn nu toegankelijk met een toetsenbord. (CQ-4271412)

* De titels van alle gebrowste pagina&#39;s op [!DNL Adobe Experience Manager] Elementen zijn nu uniek. (CQ-4271409)

**Andere verbeteringen**

De release biedt de volgende andere verbeteringen:

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

Naast de bovengenoemde nieuwe eigenschappen, verstrekt de huidige versie de volgende insectenmoeilijke situaties die op klant worden gebaseerd terugkoppelt voor [!DNL Assets].

* Voor MP3-muziekbestanden werkt de afspeelknop die op de miniatuur in de DAM-voorvertoning wordt weergegeven, niet. (CQ-4294731)
* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart. (GRANITE-26895)
* Als u te veel afbeeldingen weergeeft nadat u door veel zoekresultaten hebt geschoven, loopt de browser vast. (GRANITE-26432)
* Als bij het downloaden van middelen de optie E-mail is geselecteerd en zelfs als een geldige e-mailadres is opgegeven, is de optie Downloaden niet beschikbaar. (CQ-4296535)
* Aangepaste filters die zijn opgeslagen als slimme verzamelingen, worden niet correct toegepast op elementen. (CQ-4294942)
* De veelvoudige onderzoek en indexerende verhogingen en insectenmoeilijke situaties om prestaties te verbeteren. (CQ-4286373)
