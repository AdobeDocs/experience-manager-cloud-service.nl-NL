---
title: Toegankelijkheid [!DNL Experience Manager Assets]
description: Toegankelijkheidsfuncties weergeven in [!DNL Adobe Experience Manager] als [!DNL Cloud Service] gebruikers met een handicap helpen.
contentOwner: AG
feature: Accessibility,Asset Management
role: User,Architect,Leader
exl-id: a6d24ba6-3cb1-42cb-9942-f78572c93358
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---

<!--
Possible topics to cover in this article are below.

* Compile a list of enhancements done in the last ~1 year.
* Showcase a few prominent use cases (search?) in a screencast.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, pop-up dialogs, and so on.
* List all UIs that are keyboard navigable.
* Unified list of the product tasks supported, such as, search assets, download assets, add or editing metadata, use DM Viewers, and so on.
* Do we need to add support matrix of user tasks with browser and screen reader combinations. Everything may not work in all browsers and/or using all screen readers.
* Any exceptions that users should be aware of. It may help to call out (it may be done in ACR) what tasks are NOT supported.
* CTAs – what's next and more info from the team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Link to a11y-specific online methods to report issues, seek support, or request enhancements, if any. Asked the a11y team on Slack.
-->

# Toegankelijkheidsfuncties in [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] {#accessibility-in-aem-assets}

[!DNL Adobe Experience Manager] laat makers en uitgevers van inhoud ongelofelijke ervaringen op het web gebruiken. Adobe streeft ernaar de scheppers met een handicap op te nemen door de toegankelijkheid van [!DNL Experience Manager]. De software wordt voortdurend uitgebreid om te voldoen aan de behoeften van alle soorten gebruikers en voldoet aan de wereldwijde standaarden, waaronder personen met een visuele, auditieve, mobiliteitsfunctie of andere handicap.

[!DNL Experience Manager] publiceert conformiteitsinformatie die de normen beschrijft die het hanteert, de toegankelijkheidskenmerken in het product beschrijft en het niveau van naleving beschrijft. De compatibiliteitsrapporten voor toegankelijkheid helpen [!DNL Experience Manager] de gebruikers begrijpen in welke mate aan verschillende normen wordt voldaan . De verbeteringen zijn uitgevoerd in [!DNL Assets] alle gebruikers de interfaces gemakkelijk laten gebruiken via toetsenbord, schermlezer, vergrotingen en andere ondersteunende hulpmiddelen.

[!DNL Experience Manager] voorziet in verschillende steunniveaus voor de volgende normen:

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Herzien artikel 508 van de Herstelwet](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines).
* [Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) van W3C](https://www.w3.org/WAI/standards-guidelines/aria/).
* [NL 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Als u een rapport wilt lezen met details over de mate van naleving, raadpleegt u [Toegankelijkheidscompatibiliteitsrapport](https://www.adobe.com/accessibility/compliance.html) (ACR).

<!-- TBD: Add link after release.
To know how [!DNL Dynamic Media] is accessible, see [accessibility in [!DNL Dynamic Media]](). 
-->

## Hulptechnologieën {#at-support}

Gebruikers met een handicap vertrouwen vaak op hardware en software om toegang te krijgen tot webinhoud en softwareproducten te gebruiken. Deze gereedschappen worden hulptechnologieën genoemd. [!DNL Experience Manager Assets] kan met de volgende soorten ondersteunende technologieën (AT) werken wanneer het gebruiken van de kernfunctionaliteit van de software:

* Schermlezers en schermvergroting.
* Software voor spraakherkenning.
* Toetsenbordgebruik - navigatie en sneltoetsen.
* Hulpapparatuur, inclusief besturingselementen voor switches, vernieuwbare braillebeeldschermen en andere invoerapparaten voor de computer.
* Gereedschappen voor het vergroten van de gebruikersinterface.

## [!DNL Experience Manager Assets] gebruiksgevallen die toegankelijk zijn {#accessible-assets-use-cases}

In [!DNL Experience Manager], de toegankelijkheidsfuncties beantwoorden aan twee belangrijke vereisten van [!DNL Experience Manager] gebruikers en hun klanten.

* Voor inhoudsontwerpers en makers zijn er functies om toegankelijke inhoud te maken en te publiceren die op hun beurt door hun klanten en websitebezoekers wordt gebruikt. De inhoud kan door personen met een handicap worden gebruikt met behulp van ondersteunende hulpmiddelen. Zie voor meer informatie [Richtlijnen voor webtoegankelijkheid](/help/compliance/accessibility/quick-guide-wcag.md).
* [!DNL Experience Manager] Hiermee hebben gebruikers en beheerders met een handicap ook toegang tot gebruikersinterface en besturingselementen om inhoud te maken en te beheren. Het individu met een handicap kan ondersteunende hulpmiddelen gebruiken om door de [!DNL Assets] capaciteit.

De kernfuncties in [!DNL Assets] beter toegankelijk zijn dan voorheen en regelmatig worden bijgewerkt om de naleving van de mondiale normen te verbeteren. De CRUD-bewerkingen in [!DNL Assets] een zekere mate van toegankelijkheid hebben die in deze ingebouwd is. DAM-workflows, zoals het toevoegen, beheren, zoeken en distribueren van elementen, zijn toegankelijk via sneltoetsen, schermlezertekst, kleurcontrast, enzovoort.

## Ondersteuning voor toetsenbord {#keyboard-use}

Veel elementen van de gebruikersinterface die kunnen worden aangeklikt of geactiveerd met een aanwijzer, kunnen ook worden gebruikt met het toetsenbord. Met een toetsenbord kunnen gebruikers zich richten op UI-elementen en de juiste actie ondernemen. Gebruikers kunnen rechtstreeks sneltoetsen gebruiken om een opdracht of handeling te activeren zonder dat ze zich hoeven te richten op UI-elementen en deze met het toetsenbord hoeven te activeren. Gebruikers kunnen bijvoorbeeld de tijdlijn van een element aan de linkerkant openen door via het toetsenbord naar het besturingselement van de gebruikersinterface te bladeren en `Return`en selecteert u `Alt + 2` sneltoets.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into 'basic handling' info aka article to 'understand and use the workspace'.
* How to open and browse through the profile pop-up dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into 'basic handling' info aka article to 'understand and use the workspace'. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into 'basic handling' info aka article to 'understand and use the workspace'.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Sneltoetsen in [!DNL Assets] {#keyboard-shortcuts}

De volgende acties in [!DNL Assets] werken met de vermelde sneltoetsen. De meeste sneltoetsen die op [!DNL Experience Manager] Consoles gelden ook voor [!DNL Assets]. Zie [sneltoetsen voor consoles](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md). Zie hoe te [de sneltoetsen in- of uitschakelen](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md).

| Gebruikersinterface of scenario | Sneltoets | Handeling |
|---|---|---|
| Kolomweergave in [!DNL Assets] gebruikersinterface | Pijl-omhoog en -omlaag | Navigeer naar bestanden en mappen in dezelfde hiërarchie. |
| Kolomweergave in [!DNL Assets] gebruikersinterface | Pijl-links en Pijl-rechts | Navigeer naar bestanden en mappen boven of onder de huidige map. |
| Bladeren in mappen [!DNL Assets] | `/` | Roep zoekopdracht aan door het vak Onderzoek te openen. |
| [!DNL Assets] Console |  | Zijrails in-/uitschakelen |
| [!DNL Assets] Console | `Alt + 1` | Open de inhoudsstructuur. |
| [!DNL Assets] Console | `Alt + 2` | Openen [!UICONTROL Navigation] linker spoor. |
| [!DNL Assets] Console | `Alt + 3` | Weergave [!UICONTROL Timeline] van een geselecteerd element. |
| [!DNL Assets] Console | `Alt + 4` | Open Live Copy-referenties van het geselecteerde element. |
| [!DNL Assets] Console | `Alt + 5` | Roep zoekopdracht en zoeken aan in de geselecteerde map. |
| Element of map is geselecteerd | Backspace | Verwijder het geselecteerde element of de geselecteerde map. |
| Element of map is geselecteerd | `p` | Open de pagina Eigenschappen van het geselecteerde element. |
| Element of map is geselecteerd | `e` | Het geselecteerde element bewerken. |
| Element of map is geselecteerd | `m` | Verplaats het geselecteerde element. |
| Element of map is geselecteerd | `Ctrl + c` | Kopieer het geselecteerde element. |
| Element of map is geselecteerd | `Esc` | De selectie annuleren. |
| Dialoogvenster wordt geopend en heeft de focus | `Esc` | Dialoogvenster Sluiten. |
| In een map in DAM | `Ctrl + v` | Plak het gekopieerde element. |
| [!DNL Assets] Console | `Ctrl + A` | Selecteer alle elementen. |
| Elementeigenschappenpagina&#39;s | `Ctrl + S` | Wijzigingen opslaan. |
| [!DNL Assets] Console | `?` | Zie een lijst met sneltoetsen. |

## Aanmelden en navigeren [!DNL Assets] gebruikersinterface {#login}

Gebruikers kunnen met het toetsenbord naar het aanmeldingsveld navigeren en dit invullen om zich aan te melden. De foutberichten die het gevolg zijn van onjuiste combinaties van gebruikersnaam en wachtwoord op de aanmeldingspagina worden door schermlezers gemeld wanneer de fout optreedt.

Na het aanmelden kunnen DAM-gebruikers navigeren binnen [!DNL Assets] gebruikersinterface met toetsenbord. U kunt met het toetsenbord navigeren naar de elementen van de gebruikersinterface, zoals linkerspoor, menu&#39;s, gebruikersprofiel, zoekbalk, bestanden en mappen en instellingen voor beheer en configuratie. De volgorde van de toetsenbordnavigatie is van links naar rechts en van boven naar beneden. Wanneer u navigeert met een toetsenbord, wordt een optie die kan worden geactiveerd wanneer de focus wordt geplaatst, gemarkeerd met een beter kleurcontrast en door een schermlezer van commentaar voorzien. Indien van toepassing, wordt de status — bijvoorbeeld uitgevouwen, samengevouwen en gemengde staat — van de opties voor focus in het menu aangekondigd door een schermlezer. Bovendien wordt het doel van de optie waarop kan worden opgetreden, aangekondigd door een schermlezer in plaats van de weergave of plaatsing van de gebruikersinterface.

Als een gebruiker de optie Help of gebruikersprofiel in het menu uitbreidt, wordt de juiste optie of status door de schermlezer aangekondigd. Als een gebruiker de optie voor het gebruikersprofiel uitbreidt, kunnen de beschikbare opties met een toetsenbord worden geselecteerd. Een beheerder kan zich bijvoorbeeld een andere gebruiker voorstellen. Als een gebruiker een tekenreeks zoekt vanuit de [!UICONTROL Help] wordt in het commentaar &#39;&#39;Hulp zoeken&#39;&#39; weergegeven om aan te geven dat een zoekopdracht wordt uitgevoerd.

<!-- TBD: Removing for now. Add a more informative video later. Host it on tv.adobe

![Keyboard navigation of top options in [!DNL Experience Manager] user interface](assets/keyboard-navigation-in-aem.gif)

*Figure: Navigating through the options at the top of [!DNL Experience Manager] user interface using `Tab` key.*
-->

## Blader door elementen en bekijk de bijbehorende informatie {#browse}

In de [!DNL Assets] gebruikersinterface, kunnen gebruikers toetsenbord gebruiken om door de lijst van bestaande digitale activa in bewaarplaats te doorbladeren DAM, voorproef of download een middel, geproduceerde vertoningen, schakelaarmeningen, de geproduceerde vertoningen te zien, chronologie en versiegeschiedenis te zien, commentaren en verwijzingen, en meta-gegevens te bekijken en te beheren.

<!-- TBD: Not sure about the following list items mean:

In [!DNL Experience Manager] header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close button in a coral-dialog box was not accessible through keyboard, due to which user cannot trigger close button through keyboard press in version preview dialog. After fix, user can close dialog through close button using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

Wanneer u in de gegevensopslagruimte bladert, verbetert de volgende functionaliteit de toegankelijkheid:

* Schermlezer kondigt tekstopties aan die het doel of de functionaliteit van de pictogrammen in plaats van hun namen weergeven.
* Gebruikers kunnen de interactieve gebruikersinterface-opties in de lijst met verwijzingen openen en activeren met behulp van toetsenbordtoetsen.
* De elementen in elke rij in de lijstweergave worden door schermlezers aangekondigd als de elementen van dezelfde rij.
* Bij navigeren met `Tab` , kan de focus naar de sluitoptie in de versievoorvertoning worden verplaatst.
* Wanneer u met het toetsenbord bladert, hebben de gemarkeerde opties voor een actiefunctie een prominentere visuele focus met een verbeterd contrast. Hierdoor wordt het gefocuste gebied beter herkenbaar voor de gebruiker.
* Gebruik van de `Esc` Als u de snelactiepictogrammen uit de miniatuurweergave wilt verwijderen, wordt de toetsenbordfocus niet van het laatste item met focus verwijderd.
* Selecteer een element en selecteer `Alt + 4` sneltoets opent de [!UICONTROL References] lijst in de linkerrail. Gebruiken `Tab` gebruikers kunnen door de niet-nulreferentie-items navigeren. Door alleen de referentie-items te doorbladeren die niet gelijk zijn aan nul, bespaart u ook moeite en toetsaanslagen.
* Opmerkingen over een element zijn beschikbaar in de tijdlijn van het element. Het is toegankelijk als linkerspoor wordt betreden gebruikend een toetsenbord of een toetsenbordkortere weg.
* [!UICONTROL View Settings] in [!DNL Experience Manager] zijn toegankelijk via een toetsenbord. Gebruikers kunnen met de pijltoetsen door de beschikbare kaartgrootten navigeren en door de pijltoetsen bladeren en door de muis bladeren en andere elementen instellen in de bestaande weergave Weergave-instellingen.

<!-- TBD: Gradually, as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?
-->

## Digitale middelen beheren {#manage-assets}

Veel taken voor middelenbeheer, zoals CRUD-bewerkingen, het downloaden van middelen en het toevoegen van metagegevens, zijn in verschillende mate toegankelijk. [!DNL Assets] Hiermee kunt u de taken uitvoeren met behulp van verschillende ondersteunende hulpmiddelen, zoals een schermlezer en een toetsenbord.

Bekijk een videodemonstratie van hoe u een toetsenbord kunt gebruiken om [door de opslagplaats bladeren en een middel downloaden](https://youtu.be/K3dgqMRQJys).

Voor meta-gegevensverrichtingen die typisch door rollen zoals marketers en beheerders worden gedaan verbeteren de volgende eigenschappen toegankelijkheid:

* [!UICONTROL Save & Close] optie voor element [!UICONTROL Properties] De pagina kan nu met het toetsenbord worden geopend.
* Schermlezers kondigen de opties aan voor het verwijderen van de geselecteerde tags in [!UICONTROL Basic] tabblad van element [!UICONTROL Properties].
* Gebruikers kunnen het pop-updialoogvenster Datumkiezer gebruiken met een toetsenbord. Het Datepicker-gebruikersinterface-element wordt gebruikt om de gegevens in- en uit-tijden in te stellen en de datum te selecteren.
* De sleepfunctionaliteit met het toetsenbord werkt correct in [!UICONTROL Metadata Schema Editor] in de bladermodus van de schermlezer.
* Een gebruiker kan de focus met het toetsenbord verplaatsen naar het veld Gebruiker toevoegen of Groep onder [!UICONTROL Closed User Group] in de [!UICONTROL Permissions] tabblad van map [!UICONTROL Properties].

## Digitale middelen zoeken {#search-assets}

Een snelle en naadloze zoekervaring met middelen verhoogt de snelheid van de inhoud. De gebruiksscenario&#39;s voor snelheid van de inhoud maken deel uit van de kern [!DNL Assets] functionaliteit. Gebruikers kunnen een zoekopdracht starten vanaf de zoekbalk met de sneltoets `/` of gebruik `Tab` samen met schermlezers de zoekoptie snel te vinden. De schermlezer noemt de naam van de optie &#39;Knop Zoeken&#39; wanneer de zoekoptie actief is ![zoekoptie](assets/do-not-localize/search_icon.png). Gebruikers kunnen `Return` om het vak Onderzoek te openen. De schermlezer vertelt niet alleen over het trefwoord dat in het zoekvak is getypt, maar vertelt ook over de suggesties van [!DNL Experience Manager Assets]. Gebruikers kunnen een combinatie van pijltoetsen gebruiken, `Return`, en `Tab` voor toegang tot de verschillende opties voor het activeren van een zoekopdracht.

De zoekfunctionaliteit is toegankelijk via de volgende functies:

* De paginatitel, die beschikbaar is voor een schermlezer, helpt de pagina te identificeren als de zoekpagina van elementen.
* Gebruikers zoeken elementen vanuit het veld Zoeken. Gebruikers kunnen het openen met de toetsenbordnavigatie of de sneltoets `/`.
* Gebruikers kunnen het trefwoord zoeken en de automatische suggesties selecteren met de pijltoetsen. De gemarkeerde suggestie kan worden geselecteerd met de opdracht `Return` sleutel en middelen worden gezocht naar de geselecteerde suggestie.
* Schermlezers kunnen de selectievakjes met gemengde status (waarin de selectievakjes op het eerste niveau niet zijn geselecteerd en zijn doorgehaald) identificeren en aankondigen in het deelvenster Filters wanneer u de zoekresultaten filtert. Dit geldt alleen voor geneste voorspelling als u alle selectievakjes op het eerste niveau selecteert.
* Wanneer het vak Onderzoek is gesloten, wordt de focus van de gebruiker naar de zoekopties verplaatst.

Bij het filteren van zoekresultaten:

* De pagina met zoekresultaten heeft een informatieve titel voor een beter begrip van schermlezers.
* Een schermlezer kondigt de opties in het zoekfilter aan als uitbreidbare accordeons.
* Voorvertoningen met opties voor verschillende statussen worden door schermlezers aangekondigd.

## Elementen delen {#share-assets}

<!-- TBD: Anything about accessibility in DA, BP? AAL team confirmed that there's no content for AAL a11y on helpx.
-->

Bij het delen van elementen verbeteren de volgende functies de toegankelijkheid:

* Een gebruiker kan de focus verplaatsen met het toetsenbord in het veld Zoeken en E-mailadres toevoegen in het dialoogvenster voor het delen van koppelingen.

* In het dialoogvenster voor het delen van koppelingen kunnen de schermlezers tijdens het navigeren in de bladermodus:

   * Commentaar de tabelinformatie niet meer zodra het dialoogvenster is geladen.
   * Kan naar alle vermelde suggesties navigeren.
   * Beschrijf de weergegeven suggesties voor de velden E-mailadres en Zoeken toevoegen.

## Toegankelijke documentatie {#accessible-docs}

[!DNL Experience Manager] biedt toegankelijke documentatie voor gebruik door mensen met een handicap. Met de volgende opties kunt u de inhoud die nu wordt aangeboden toegankelijk maken, terwijl de Adobe de sjabloon en de inhoud blijft verbeteren:

* Schermlezers kunnen de tekst lezen.
* Afbeeldingen en illustraties hebben alternatieve tekst.
* Toetsenbordnavigatie is mogelijk.
* Contrastverhoudingen helpen u bepaalde onderdelen van de documentatiewebsite te markeren.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)

## Feedback geven {#a11y-feedback}

Gebruik de volgende methoden om feedback te geven, vragen te stellen en productverbeteringen aan te vragen met betrekking tot toegankelijkheid:

* Het formulier invullen bij [www.adobe.com/accessibility/feedback.html](https://www.adobe.com/accessibility/feedback.html).
* E-mail ons op access@adobe.com.

>[!MORELIKETHIS]
>
>* [Opmerkingen bij de release over de verbeteringen die in elke release zijn aangebracht](/help/release-notes/release-notes-cloud/release-notes-current.md).
>* [[!DNL Adobe Experience Manager] toegankelijkheidsrichtlijnen](/help/compliance/accessibility/web-accessibility.md).
>* [Conformiteitsrapporten (ACR) en VPAT-lijsten voor oplossingen voor Adoben](https://www.adobe.com/accessibility/compliance.html).
