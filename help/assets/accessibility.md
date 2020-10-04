---
title: Toegankelijkheid in [!DNL Experience Manager Assets]
description: Toegankelijkheidsfuncties [!DNL Adobe Experience Manager] als Cloud Service helpen gebruikers met een handicap.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b866d9317ba1795b34f7e308426240c44bd1131c
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 1%

---


<!--
Original scope of this article for Core Assets for all a11y topics is around the following topics. This has changed since then but keeping this list of topics for posterity's sake.

* Convert the absolute doc links to relative links.
* Add an overview
* Compile a list of enhancements done in the last ~1 year.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, etc.)
* Specific user tasks supported, such as, download assets, datepicker, editing metadata, etc.
* Support matrix of user tasks with browsers and screen readers + OSes combinations
* Exceptions that users should be aware of.
* CTA – what is next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Examples of other a11y DX Docs from Elle.
  * Link to a11y-specific channels to report issues, seek support, or request enhancements, if any. Available info from Elle.
-->

# Accessibility in [!DNL Adobe Experience Manager Assets] as a Cloud Service {#accessibility-in-aem-assets}

Adobe heeft zich ertoe verbonden producten te maken voor alle gebruikers, inclusief mensen met een handicap. [!DNL Adobe Experience Manager] voortdurend wordt verbeterd om aan de behoeften van alle soorten gebruikers te voldoen. [!DNL Experience Manager] publiceert conformiteitinformatie waarin de normen worden beschreven die het hanteert, beschrijft de toegankelijkheidsfuncties in het product en beschrijft het niveau van conformiteit. Hiermee kunnen gebruikers de mate van betrokkenheid begrijpen.

[!DNL Adobe Experience Manager] voorziet in verschillende steunniveaus voor de volgende normen:

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Gereviseerde sectie 508](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines).
* [WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Zie de pagina [](https://www.adobe.com/accessibility/compliance.html) Accessibility conformance Reports (ACR) voor alle Adobe-oplossingen voor toegang tot het rapport waarin de compatibiliteitsniveaus worden beschreven.

## Hulptechnologieën {#at-support}

Gebruikers met een handicap vertrouwen vaak op hardware en software om toegang te krijgen tot webinhoud. Deze gereedschappen worden hulptechnologieën genoemd. [!DNL Adobe Experience Manager Assets] werken met de volgende soorten ondersteunende hulpmiddelen om gebruikers ondersteuning te bieden bij het gebruik van de kernfuncties van de software:

* Schermlezers.
* Spraakherkenningssoftware.
* Toetsenbordgebruik - navigatie en sneltoetsen.
* Hulpapparatuur, inclusief besturingselementen voor switches, vernieuwbare braillebeeldschermen en andere invoerapparaten voor de computer.
* Gereedschappen voor het vergroten van de gebruikersinterface.

## [!DNL Experience Manager Assets] gebruiksgevallen die toegankelijk zijn {#accessible-assets-use-cases}

In [!DNL Experience Manager]de toegankelijkheidsfuncties worden twee belangrijke vereisten van [!DNL Experience Manager] gebruikers en hun klanten behandeld.

Voor inhoudsontwerpers en makers zijn er functies om toegankelijke inhoud te maken en te publiceren die op hun beurt door hun klanten en websitebezoekers wordt gebruikt. De inhoud kan door personen met een handicap worden gebruikt met behulp van ondersteunende hulpmiddelen. Zie voor meer informatie de [webtoegankelijkheidsrichtlijnen](/help/onboarding/accessibility/web-accessibility.md).

Gebruikers en beheerders met een handicap [!DNL Experience Manager] hebben bovendien toegang tot gebruikersinterface en besturingselementen om inhoud te maken en te beheren. Personen met een handicap kunnen ondersteunende hulpmiddelen gebruiken om te navigeren, te gebruiken en de [!DNL Assets] mogelijkheden te beheren.

De kernkenmerken in [!DNL Assets] zijn toegankelijker dan voorheen en worden regelmatig bijgewerkt om de naleving van de mondiale normen te verbeteren. De CRUD-bewerkingen in Elementen hebben een bepaalde mate van toegankelijkheid die erin is ingebouwd. DAM-workflows, zoals het toevoegen, beheren, zoeken en distribueren van elementen, zijn toegankelijk via sneltoetsen, schermlezertekst, kleurcontrast, enzovoort.

## Ondersteuning voor het gebruik van het toetsenbord {#keyboard-use}

Veel elementen van de gebruikersinterface die kunnen worden aangeklikt of geactiveerd met een aanwijzer, kunnen ook worden gebruikt met het toetsenbord. Met een toetsenbord kunnen gebruikers zich richten op UI-elementen en de juiste actie ondernemen. Gebruikers kunnen rechtstreeks sneltoetsen gebruiken om een opdracht of handeling te activeren zonder de gebruikersinterface-elementen te hoeven activeren en deze met het toetsenbord te activeren. Gebruikers kunnen bijvoorbeeld de tijdlijn van een element aan de linkerkant openen door met een toetsenbord naar het besturingselement voor de gebruikersinterface te bladeren, op Return te drukken en op de `alt + 2` sneltoets te drukken.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Sneltoetsen in elementen {#keyboard-shortcuts}

<!-- TBD: Add here only those keyboard shortcuts that work for/with Assets. Do with Oct release.
-->

| Gebruikersinterface of scenario | Sneltoets | Actie |
|---|---|---|
| Kolomweergave in gebruikersinterface Elementen | Pijltoetsen omhoog en omlaag | Navigeer naar bestanden en mappen in dezelfde hiërarchie. |
| Kolomweergave in gebruikersinterface Elementen | Pijl-links en Pijl-rechts | Navigeer naar bestanden en mappen boven of onder de huidige map. |
| Bladeren door mappen in elementen | `/` | Roep zoekopdracht aan door het vak Onderzoek te openen. |
| Elementenconsole | ` | Zijsporen in-/uitschakelen |
| Elementenconsole | Alt + 1 | Open de inhoudsstructuur. |
| Elementenconsole | Alt + 2 | Open [!UICONTROL Navigation] siderail. |
| Elementenconsole | Alt + 3 | Weergave [!UICONTROL Timeline] van een geselecteerd element. |
| Elementenconsole | Alt + 4 | Open Live Copy-referenties van het geselecteerde element. |
| Elementenconsole | Alt + 5 | Roep zoekopdracht en zoeken aan in de geselecteerde map. |
| Element of map is geselecteerd | Backspace | Verwijder het geselecteerde element of de geselecteerde map. |
| Element of map is geselecteerd | `p` | Open de pagina Eigenschappen van het geselecteerde element. |
| Element of map is geselecteerd | `e` | Het geselecteerde element bewerken. |
| Element of map is geselecteerd | `m` | Verplaats het geselecteerde element. |
| Element of map is geselecteerd | Ctrl + c | Kopieer het geselecteerde element. |
| Element of map is geselecteerd | Esc | Schakel de selectie uit. |
| Dialoogvenster wordt geopend en heeft de focus | Esc | Dialoogvenster Sluiten. |
| In een map in DAM | Ctrl + v | Plak het gekopieerde element. |
| Elementenconsole | Ctrl+A | Selecteer alle elementen. |
| Elementeigenschappenpagina&#39;s | Ctrl + S | Wijzigingen opslaan. |
| Elementenconsole | `?` | Zie een lijst met sneltoetsen. |

De meeste sneltoetsen die van toepassing zijn op [!DNL Experience Manager] consoles, zijn ook van toepassing op elementen. Zie [Sneltoetsen voor consoles](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/essentials/keyboard-shortcuts.html). Zie hoe u de sneltoetsen [kunt](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)in- of uitschakelen.

## Aanmelden en navigeren door [!DNL Assets] gebruikersinterface {#login}

Gebruikers kunnen met het toetsenbord naar het aanmeldingsveld navigeren en dit invullen. De foutberichten die het gevolg zijn van onjuiste combinaties van gebruikersnaam en wachtwoord op de aanmeldingspagina worden door schermlezers gemeld wanneer de fout optreedt.

Na het aanmelden kunnen DAM-gebruikers met het toetsenbord naar de [!DNL Assets] gebruikersinterface navigeren. De volgorde van de toetsenbordnavigatie is van links naar rechts en van boven naar beneden. Wanneer u navigeert met een toetsenbord, worden actiemogelijkheden die de focus hebben, gemarkeerd met een beter kleurcontrast en doorgelicht door een schermlezer. De uitgevouwen of samengevouwen status van de opties voor focus in het menu wordt door een schermlezer aangekondigd.

Als een gebruiker de optie Help of gebruikersprofiel in het menu uitbreidt, wordt de juiste optie of status door de schermlezer aangekondigd. Als een gebruiker de optie voor het gebruikersprofiel uitbreidt, kunnen de beschikbare opties met een toetsenbord worden geselecteerd. Een gebruiker kan zich bijvoorbeeld een andere gebruiker voorstellen. De gebruikersinterface-optie en foutbericht

![Toetsenbordnavigatie met topopties in gebruikersinterface van Experience Manager](assets/keyboard-navigation-in-aem.gif)

*Afbeelding: Navigeren door de opties boven aan de gebruikersinterface van de Experience Manager met behulp van`Tab`toets.*

Als een gebruiker een tekenreeks zoekt vanuit de [!UICONTROL Help] optie, geeft een commentator &#39;Hulp zoeken&#39; aan om aan te geven dat een zoekopdracht wordt uitgevoerd.

## Door bestaande elementen bladeren en verwante informatie weergeven {#browse}

In de [!DNL Assets] gebruikersinterface kunnen gebruikers met het toetsenbord door de lijst met bestaande digitale elementen in de DAM-gegevensopslagruimte bladeren, een voorvertoning van een element weergeven of downloaden, gegenereerde vertoningen bekijken, de gegenereerde uitvoeringen bekijken, de tijdlijn en versiegeschiedenis bekijken, opmerkingen en verwijzingen bekijken en metagegevens beheren.

<!-- TBD: Not sure about the following list items mean:

In Experience Manager header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close button in a coral-dialog wasn't accessible through keyboard, due to which user cannot trigger close button through keyboard press in version preview dialog. After fix, user can close dialog through close button using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

Wanneer u in de gegevensopslagruimte bladert, verbetert de volgende functionaliteit de toegankelijkheid:

* Schermlezer kondigt tekstopties aan die het doel of de functionaliteit van de pictogrammen in plaats van hun namen weergeven.
* Gebruikers kunnen de interactieve gebruikersinterface-opties in de lijst met verwijzingen openen en activeren met behulp van toetsenbordtoetsen.
* De elementen in elke rij in de lijstweergave worden door schermlezers aangekondigd als de elementen van dezelfde rij.
* Wanneer u met `Tab` de toets navigeert, kunt u de optie Sluiten in de voorvertoning van de versie gebruiken.
* Wanneer u met het toetsenbord bladert, hebben de gemarkeerde opties voor een actiefunctie een prominentere visuele focus met een verbeterd contrast. Hierdoor wordt het gefocuste gebied beter herkenbaar voor de gebruiker.
* Als u de `Esc` toets gebruikt om de snelactiepictogrammen uit de miniatuurweergave te verwijderen, wordt de toetsenbordfocus niet van het laatste item met focus verwijderd.
* Als er een element is geselecteerd en u drukt op Alt + 4-sneltoets, wordt de lijst Verwijzingen geopend. Met behulp van `Tab` toets kunnen gebruikers door de items met de referentie-eigenschap none-zero navigeren.
* Opmerkingen over een element zijn beschikbaar in de tijdlijn van het element. Het is toegankelijk via het toetsenbord.
* De montages van de mening in Experience Manager zijn toegankelijk door toetsenbord. De gebruiker kan door de beschikbare kaartgrootten navigeren gebruikend pijlsleutels, en selecteren en door te klikken om door te navigeren en andere elementen in de bestaande mening van de Montages van de Mening te plaatsen.

<!-- TBD: Gradually,  as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?

-->

## Digitale middelen beheren {#manage-assets}

Veel taken voor middelenbeheer, zoals CRUD-bewerkingen, het downloaden van middelen en het toevoegen van metagegevens, zijn in verschillende mate toegankelijk. Met middelen kunt u de taken uitvoeren met behulp van verschillende ondersteunende hulpmiddelen, zoals een schermlezer en een toetsenbord.

Bekijk een videodemonstratie van hoe u met een toetsenbord door de opslagplaats kunt [bladeren en middelen](https://youtu.be/K3dgqMRQJys)kunt downloaden.

Voor meta-gegevensverrichtingen die typisch door rollen zoals marketers en beheerders worden gedaan verbeteren de volgende eigenschappen toegankelijkheid:

* [!UICONTROL Save & Close] op de pagina met eigenschappen van elementen kan nu via het toetsenbord worden geopend.
* Schermlezers kondigen de opties aan om de geselecteerde labels op het tabblad Standaard van de knoppen voor middeleneigenschappen te verwijderen.
* Het pop-upvenster met de datumkiezer kan worden gebruikt met een toetsenbord. Datepicker wordt gebruikt om op-tijden en off-times in te stellen.
* De sleepfunctionaliteit met het toetsenbord werkt correct in de Metadata Schema Editor in de bladermodus van schermlezers.
* Een gebruiker kan de focus verplaatsen met het toetsenbord naar het veld Gebruiker toevoegen of Groep onder Gesloten gebruikersgroep op het tabblad Machtigingen van het tabblad Eigenschappen van map.

## Digitale middelen zoeken {#search-assets}

Een snelle en naadloze zoekervaring met middelen verhoogt de snelheid van de inhoud. De gebruiksgevallen voor de snelheid van de inhoud maken deel uit van de kernfunctionaliteit [!DNL Assets] . Als u een zoekopdracht wilt starten vanaf de zoekbalk, kunnen gebruikers de sneltoets `/` of `Tab` schermlezers gebruiken om snel de zoekoptie te vinden. De schermlezer beperkt de naam van de optie op dezelfde manier als [!UICONTROL Search Button] wanneer de ![zoekoptie](assets/do-not-localize/search_icon.png)van de zoekoptie geactiveerd is. Gebruikers kunnen op deze knop drukken `Return` om het vak Zoeken te openen. De schermlezer vertelt niet alleen over het trefwoord dat in het zoekvak is getypt, maar ook over de suggesties die automatisch worden ingevuld door [!DNL Experience Manager Assets]. Gebruikers kunnen een combinatie van pijltoetsen gebruiken `Return`en toegang krijgen `Tab` tot de verschillende opties om een zoekopdracht te starten.

De zoekfunctionaliteit wordt verder toegankelijk gemaakt door de volgende functionaliteit:

* De paginatitel, die beschikbaar is voor een schermlezer, helpt de pagina te identificeren als de zoekpagina van elementen.
* Gebruikers zoeken elementen vanuit de zoekbalk. Gebruik de toetsen op het toetsenbord of de sneltoets om `/` de zoekbalk te openen.
* Typ het trefwoord in de zoekopdracht en selecteer de automatische suggesties met het toetsenbord. Druk op de toets Return om een automatisch gesuggereerde tekenreeks en zoekmiddelen ervoor te accepteren.
* Schermlezers kunnen de selectievakjes met gemengde status (waarin de selectievakjes op het eerste niveau niet zijn geselecteerd en zijn doorgehaald) identificeren en aankondigen in het deelvenster Filters wanneer u de zoekresultaten filtert. Dit geldt alleen voor alle geneste voorspelling.
* Wanneer het vak Onderzoek is gesloten, wordt de focus van de gebruiker naar de zoekopties verplaatst.

Bij het filteren van zoekresultaten:

* De pagina met zoekresultaten heeft een informatieve titel waarmee u gebruikers van schermlezers beter kunt begrijpen.
* Een schermlezer kondigt de opties in het zoekfilter aan als uitbreidbare accordeons.
* Voorvertoningen met knoppen met gemengde statussen worden door schermlezers aangekondigd.

## Assets delen {#share-assets}

<!-- TBD: Accessibility in DA, BP, AAL? Asked CCE team for AAL content?
-->

Bij het delen van elementen verbeteren de volgende functies de toegankelijkheid:

* Een gebruiker kan de focus verplaatsen met het toetsenbord in het veld Zoeken en E-mailadres toevoegen in het dialoogvenster voor het delen van koppelingen.

* In het dialoogvenster voor het delen van koppelingen kunnen de schermlezers tijdens het navigeren in de bladermodus:

   * Commentaar de tabelinformatie niet meer zodra het dialoogvenster is geladen.
   * Kan naar alle vermelde automatische suggesties navigeren.
   * Beschrijf de weergegeven automatische suggesties voor de velden E-mailadres en Zoeken toevoegen.

## Toegankelijkheid in [!DNL Dynamic Media] {#dynamic-media-accessibility}

Wanneer u Dynamische media gebruikt, kunt u deze als volgt toegankelijk maken:

* Een gebruiker kan zich op `Flyout`, `InlineZoom`, `Shoppable_Banner`, `Zoom_dark`, `Zoom_light`, `ZoomVertical_dark`, en `ZoomVertical_light` opties concentreren gebruikend sleutel in activa detailleert Kijkers in `Tab` [!DNL Dynamic Media].

## Toegankelijke documentatie {#accessible-docs}

[!DNL Experience Manager] biedt toegankelijke documentatie die kan worden gebruikt door mensen met een handicap. Met de volgende opties kunt u de inhoud die nu wordt aangeboden toegankelijk maken, terwijl Adobe de sjabloon en de inhoud blijft verbeteren:

* Schermlezers kunnen de tekst lezen.
* Afbeeldingen en illustraties hebben alternatieve tekst.
* Toetsenbordnavigatie is mogelijk.
* Contrastverhoudingen helpen u bepaalde onderdelen van de documentatiewebsite te markeren.

<!-- 
## More resources for accessibility {#a11y-resources}

TBD: If anyone is aware of AEM-specific resources that help users leverage any accessibility features or use any assistive technology with AEM, please share or leave a link here.
-->

## Verbeteringen in [!DNL Experience Manager Assets] releases {#rn-fixes}

Zie de [releaseopmerkingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/home.html) van de respectieve releases voor een lijst met specifieke verbeteringen die in elke afzonderlijke versie zijn aangebracht.

>[!MORELIKETHIS]
>
>* [Richtlijnen voor toegankelijkheid AEM](/help/onboarding/accessibility/web-accessibility.md)
>* [Conformiteitsrapporten voor Adobe-oplossingen](https://www.adobe.com/accessibility/compliance.html)

