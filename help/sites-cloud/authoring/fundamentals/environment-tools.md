---
title: Ontwerpomgeving en -gereedschappen
description: De ontwerpomgeving van AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Ontwerpomgeving en -gereedschappen {#authoring-the-environment-and-tools}

De ontwerpomgeving van AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud. De beschikbare gereedschappen zijn toegankelijk via de verschillende consoles en pagina-editors.

## Uw site beheren {#managing-your-site}

Met de **Sites** -console kunt u door uw website navigeren en deze beheren met de kopbalk, werkbalk, actiepictogrammen (van toepassing op de geselecteerde bron), broodkruimels en, indien geselecteerd, secundaire rails (bijvoorbeeld tijdlijn en verwijzingen).

Bijvoorbeeld, kolommening:

![Kolomweergave](/help/sites-cloud/authoring/assets/column-view.png)

## Pagina-inhoud bewerken {#editing-page-content}

U kunt een pagina bewerken met de pagina-editor. Bijvoorbeeld:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

![Pagina-editor](/help/sites-cloud/authoring/assets/page-editor.png)

>[!NOTE]
>
>De eerste keer dat u een pagina opent om te bewerken, wordt in een reeks dia&#39;s een overzicht van de functies weergegeven.
>
>U kunt de tour desgewenst overslaan en deze op elk gewenst moment herhalen door deze te selecteren in het menu **Pagina-informatie** .

## Toegang tot Help {#accessing-help}

Wanneer u een pagina bewerkt, kunt u de **Help** openen via:

* De kiezer [**Pagina-informatie **](/help/sites-cloud/authoring/fundamentals/page-properties.md#page-properties)die de inleidende dia&#39;s weergeeft (zoals de eerste keer dat u de editor opent)
* De [configuratiedialoog](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) voor specifieke componenten (gebruikend? pictogram in de dialoogtoolbar), die contextgevoelige hulp toont

Verdere [Help-gerelateerde bronnen zijn beschikbaar op consoles](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help).

## Browser voor componenten {#components-browser}

Componenten zijn de bouwstenen van AEM-inhoud. U plaatst veelvoudige componenten op een pagina en vormt hun opties om uw inhoudspagina met AEM te bouwen.

De componentenbrowser toont alle componenten die voor gebruik op uw huidige pagina beschikbaar zijn. U kunt deze naar de juiste locatie slepen en vervolgens bewerken om uw inhoud toe te voegen.

De componentenbrowser is een lusje binnen het zijpaneel (samen met [activa browser](#assets-browser) en [inhoudsboom](#content-tree)). Als u het zijpaneel wilt openen (of sluiten), gebruikt u het pictogram linksboven op de werkbalk:

![Zijpaneel in-/uitschakelen](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Wanneer u het zijpaneel opent, schuift het van de linkerkant open (selecteer indien nodig het tabblad **Componenten** ). Wanneer u deze optie opent, kunt u door alle componenten bladeren die beschikbaar zijn voor de pagina.

De daadwerkelijke verschijning en behandeling zijn afhankelijk van het apparatentype u gebruikt:

* **Mobiel apparaat (bijvoorbeeld iPad)**

   De componentbrowser beslaat volledig de pagina die wordt bewerkt.

   Als u een component aan de pagina wilt toevoegen, houdt u de vereiste component ingedrukt en verplaatst u deze naar rechts (de componentbrowser wordt dan gesloten om de pagina weer weer te geven), waar u de component kunt plaatsen.

   ![Componentbrowser op mobiel](/help/sites-cloud/authoring/assets/component-browser-mobile.png)

* **Bureaubladapparaat**

   De componentbrowser wordt links in het venster geopend.

   Als u een component aan de pagina wilt toevoegen, klikt u op de gewenste component en sleept u deze naar de gewenste locatie.

   ![Componentbrowser op bureaublad](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

   Componenten worden vertegenwoordigd door

   * Componentnaam
   * Componentgroep (grijs)
   * Pictogram of afkorting
      * De standaardcomponentpictogrammen zijn monochroom.
      * Afkortingen zijn altijd de eerste twee tekens van de componentnaam.
   Van de hoogste toolbar in browser van **Componenten** kunt u:

   * Componenten filteren op naam.
   * Beperk de weergave tot een specifieke groep met behulp van de keuzelijst.
   Voor een meer gedetailleerde beschrijving van de component kunt u op het informatiepictogram naast de component in de **Componentbrowser** klikken of hierop tikken (indien beschikbaar). Bijvoorbeeld voor het **inhoudsfragment**:

   ![Informatie over Componentbrowser](/help/sites-cloud/authoring/assets/component-browser-information.png)

   Zie de [componentconsole](/help/sites-cloud/authoring/features/components-console.md)voor nog meer informatie over de beschikbare componenten.

>[!NOTE]
>
>Een mobiel apparaat wordt gedetecteerd wanneer de breedte minder dan 1024 px is. Dit kan ook het geval zijn voor een klein bureaubladvenster.

## Browser voor middelen {#assets-browser}

In de middelenbrowser worden alle elementen weergegeven die beschikbaar zijn voor rechtstreeks gebruik op de huidige pagina. <!--The assets browser shows all [assets](/help/assets/home.md) that are available for direct use on your current page.-->

De middelenbrowser is een tab in het zijpaneel, samen met de [componentenbrowser](#components-browser) en de [inhoudsstructuur](#content-tree). Als u het zijpaneel wilt openen of sluiten, gebruikt u het pictogram linksboven op de werkbalk:

![Zijpaneel in-/uitschakelen](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Wanneer u het zijpaneel opent, schuift het van de linkerkant open. Selecteer indien nodig het tabblad **Middelen** .

![Knop voor middelenbrowser](/help/sites-cloud/authoring/assets/assets-browser-button.png)

Wanneer de middelenbrowser is geopend, kunt u door alle elementen bladeren die beschikbaar zijn voor uw pagina. Met oneindig schuiven wordt de lijst indien nodig uitgevouwen.

![Browser voor middelen](/help/sites-cloud/authoring/assets/assets-browser.png)

Als u een element aan de pagina wilt toevoegen, selecteert u het element en sleept u het naar de gewenste locatie. Dit kan zijn:

* Een bestaand onderdeel van het desbetreffende type.
   * U kunt bijvoorbeeld een element van het type afbeelding naar een afbeeldingscomponent slepen.
* Een [plaatsaanduiding](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-placeholder) in het alineasysteem om een nieuwe component van het juiste type te maken.
   * U kunt bijvoorbeeld een element van het type afbeelding naar het alineasysteem slepen om een component Image te maken.

>[!NOTE]
>
>Dit is beschikbaar voor specifieke elementen en componenttypen. Zie Een component [invoegen met de middelenbrowser](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-using-the-assets-browser) voor meer informatie.

Vanuit de bovenste werkbalk van de middelenbrowser kunt u de elementen filteren op:

* Naam
* Pad
* Elementtype zoals afbeeldingen, video&#39;s, documenten, alinea&#39;s, inhoudsfragmenten en ervaringsfragmenten
* Elementkenmerken zoals oriëntatie en stijl
   * Alleen beschikbaar voor bepaalde typen elementen

De daadwerkelijke verschijning en behandeling zijn afhankelijk van het apparatentype u gebruikt:

* **Mobiel apparaat**

   De elementenbrowser beslaat volledig de pagina die wordt bewerkt.

   Als u een element aan uw pagina wilt toevoegen, houdt u het vereiste element ingedrukt en verplaatst u het naar rechts. De elementenbrowser wordt dan gesloten en geeft de pagina weer, waar u het element aan de vereiste component kunt toevoegen.

   ![Berichtenbrowser op mobiele apparaten](/help/sites-cloud/authoring/assets/assets-browser-mobile.png)

* **Bureaubladapparaat**

   De middelenbrowser wordt links in het venster geopend.

   Als u een element aan de pagina wilt toevoegen, klikt u op het gewenste element en sleept u het naar de gewenste component of locatie.

   ![Elementenbrowser op bureaublad](/help/sites-cloud/authoring/assets/assets-browser-desktop.png)

>[!NOTE]
>
>Een mobiel apparaat wordt ontdekt wanneer de breedte minder dan 1024px is; dat wil zeggen ook in een klein bureaubladvenster.

Als u snel een wijziging in een element wilt aanbrengen, kunt u de middeleneditor rechtstreeks vanuit de middelenbrowser starten door op het bewerkingspictogram naast de naam van het element te klikken. <!--If you need to quickly make a change to an asset, you can start the [asset editor](/help/assets/manage-digital-assets.md) directly from the asset browser by clicking the edit icon shown next to the asset's name.-->

![De knop Element bewerken](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Inhoudsstructuur {#content-tree}

De **inhoudsstructuur** geeft een overzicht van alle componenten op de pagina in een hiërarchie, zodat u in een oogopslag kunt zien hoe de pagina is samengesteld.

De inhoudsstructuur is een tabblad in het zijpaneel (samen met de browser met componenten en elementen). Als u het zijpaneel wilt openen (of sluiten), gebruikt u het pictogram linksboven op de werkbalk:

![Knop Inhoudsstructuur](/help/sites-cloud/authoring/assets/content-tree-button.png)

Als u het zijpaneel opent, wordt het geopend (van de linkerkant). Selecteer indien nodig het tabblad **Inhoudsstructuur** . Wanneer open kunt u een vertegenwoordiging van de boommening van uw pagina of malplaatje zien, zodat het gemakkelijker is om te begrijpen hoe zijn inhoud hiërarchisch gestructureerd is. Bovendien wordt het op een complexe pagina gemakkelijker om tussen componenten van de pagina te springen.

![Inhoudsstructuur](/help/sites-cloud/authoring/assets/content-tree-editor.png)

Een pagina kan eenvoudig uit veel van hetzelfde type componenten bestaan, zodat in de structuur van de inhoud (component) beschrijvende tekst (grijs) wordt weergegeven achter de naam van het componenttype (in zwart). De beschrijvende tekst is afkomstig uit gemeenschappelijke eigenschappen van de component, zoals titel of tekst.

Componenttypen worden weergegeven in de taal van de gebruiker, terwijl de tekst van de componentbeschrijving uit de paginataal komt.

Als u klikt op het chevron naast een component, wordt dat niveau samengevouwen of uitgevouwen.

![Vergroting van chevron-inhoud](/help/sites-cloud/authoring/assets/content-tree-chevron.png)

Wanneer u op de component klikt, wordt de component in de pagina-editor gemarkeerd. Welke acties beschikbaar zijn, is afhankelijk van de paginastatus:

* Bijvoorbeeld een basispagina:

   ![Inhoudsstructuur gemarkeerd](/help/sites-cloud/authoring/assets/content-tree-highlighted.png)

   De componenten van een basispagina hebben de gebruikelijke opties.

   Als de component waarop u klikt in de structuur bewerkbaar is, wordt er een moersleutelpictogram rechts van de naam weergegeven. Als u op dit pictogram klikt, wordt het dialoogvenster Bewerken voor de component direct gestart.

   ![Knop Inhoudsstructuur bewerken](/help/sites-cloud/authoring/assets/content-tree-edit.png)

* Op een pagina die deel uitmaakt van een livecopy, waar componenten van een andere pagina worden overgeërfd, zijn minder opties beschikbaar, waaronder de overervingsopties. <!--A page that is part of a [livecopy](/help/sites-administering/msm.md), where components are inherited from another page:-->

>[!NOTE]
>
>De inhoudsstructuur is niet beschikbaar als u een pagina bewerkt op een mobiel apparaat (als de breedte van de browser minder dan 1024 px is).

## Fragmenten - gekoppelde inhoudsbrowser {#fragments-associated-content-browser}

Als uw pagina Content Fragments bevat, hebt u ook toegang tot de [browser voor Gekoppelde inhoud](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content).

## Verwijzingen {#references}

**Verwijzingen** tonen verbindingen met de geselecteerde pagina:

* Blauwdrukken
* Starten
* Live kopieën
* Taalkopieën
* Binnenkomende koppelingen
* Gebruik van de referentiecomponent: geleend en geleend materiaal

Open de vereiste console, navigeer dan aan het vereiste middel en open **Verwijzingen** gebruikend:

![Verwijzingen, optie](/help/sites-cloud/authoring/assets/references.png)

[Selecteer uw vereiste middel](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) om een lijst van verwijzingstypes relevant voor die bron te tonen:

![Details van verwijzingen](/help/sites-cloud/authoring/assets/references-detail.png)

Selecteer het juiste referentietype voor meer informatie. In bepaalde situaties zijn aanvullende acties beschikbaar wanneer u een specifieke verwijzing selecteert, zoals:

* **Binnenkomende koppelingen**, bieden een lijst met pagina&#39;s die naar de pagina verwijzen, samen met directe toegang tot **Bewerken** van een van deze pagina&#39;s wanneer u een specifieke koppeling selecteert
* Instanties van geleende en geleende inhoud die de component **Verwijzing** gebruiken, kunt u van hieruit naar de verwijzende/referenced pagina navigeren
* [Opstarten](/help/sites-cloud/authoring/launches/overview.md), biedt toegang tot gerelateerde opstarties
* Met Actieve kopieën worden de paden van alle live kopieën weergegeven die zijn gebaseerd op de geselecteerde bron. <!--[Live Copies](/help/sites-administering/msm.md) displays the paths of all live copies that are based on the selected resource.-->
* Blauwdruk bevat details en diverse handelingen <!--[Blueprint](/help/sites-administering/msm-best-practices.md), provides details and various actions-->
* Taalkopieën bevatten details en diverse handelingen <!--[Languages Copies](/help/sites-administering/tc-manage.md#creating-translation-projects-using-the-references-panel), provides details and various actions-->

## Gebeurtenissen - tijdlijn {#events-timeline}

Voor geschikte bronnen (bijvoorbeeld pagina&#39;s van de **Sites** -console of middelen van de **Assets** -console) kan de [tijdlijn worden gebruikt om de recente activiteit op geselecteerde items](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)weer te geven.

Open de vereiste console, navigeer dan aan het vereiste middel en open **Chronologie**, gebruikend:

![Tijdlijn, optie](/help/sites-cloud/authoring/assets/timeline.png)

[Selecteer uw vereiste bron](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)en **kies Alle** of **Activiteiten** tonen om recente acties op de geselecteerde bronnen weer te geven:

![Tijdlijndetails](/help/sites-cloud/authoring/assets/timeline-detail.png)

## Pagina-informatie {#page-information}

Met het pictogram Pagina-informatie (equalizer) opent u een menu dat ook informatie bevat over de laatste bewerking en de laatste publicatie. Afhankelijk van de kenmerken van de pagina, de site en uw exemplaar, zijn mogelijk meer of minder opties beschikbaar:

![Pagina-informatie, optie](/help/sites-cloud/authoring/assets/page-information.png)

* [Eigenschappen openen](/help/sites-cloud/authoring/fundamentals/page-properties.md)
* Uitrolpagina <!--[Rollout Page](/help/sites-administering/msm.md#msm-from-the-ui)-->
* [Workflow starten](/help/sites-cloud/authoring/workflows/applying.md#starting-a-workflow-from-the-page-editor)
* [Pagina vergrendelen](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page)
* [Pagina publiceren](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-pages-1)
* [Publicatie van pagina ongedaan maken](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages)
* [Sjabloon bewerken](/help/sites-cloud/authoring/features/templates.md)
* [Weergeven als gepubliceerd](/help/sites-cloud/authoring/fundamentals/editing-content.md#view-as-published)
* [Weergeven in beheerder](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
* [Help](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help)
* [Starten](/help/sites-cloud/authoring/launches/promoting.md) bevorderen (alleen als de pagina een introductie is)

Bovendien kan **Pagina-informatie** waar nodig toegang bieden tot analyses en aanbevelingen.

## Paginamodi {#page-modes}

Er zijn verschillende modi voor het bewerken van een pagina die verschillende handelingen mogelijk maken:

* [Bewerken](/help/sites-cloud/authoring/fundamentals/editing-content.md) - de modus die moet worden gebruikt voor het bewerken van de pagina-inhoud.
* [Layout](/help/sites-cloud/authoring/features/responsive-layout.md) - hiermee kunt u afhankelijk van het apparaat een responsieve lay-out maken en bewerken (als de pagina is gebaseerd op een lay-outcontainer)
* [Doelstelling](/help/sites-cloud/authoring/personalization/targeted-content.md) - vergroot de relevantie van inhoud door de inhoud op alle kanalen te richten en te meten.
* [Tijdlijn verdraaien](/help/sites-cloud/authoring/features/page-versions.md#timewarp) - hiermee kunt u de status van een pagina op een bepaald tijdstip bekijken.
* [Live Copy-status](/help/sites-cloud/authoring/fundamentals/editing-content.md#live-copy-status) : geeft een snel overzicht van de status van de live kopie en van de onderdelen die u wel of niet wilt overnemen.
* [Voorvertoning](/help/sites-cloud/authoring/fundamentals/editing-content.md#previewing-pages) : wordt gebruikt om de pagina weer te geven zoals deze wordt weergegeven in de publicatieomgeving. of om te navigeren met koppelingen in de inhoud.
* [Annoteren](/help/sites-cloud/authoring/fundamentals/annotations.md) - wordt gebruikt om annotaties op de pagina toe te voegen of weer te geven.

U kunt deze openen met de pictogrammen in de rechterbovenhoek. Het werkelijke pictogram verandert in de modus die u momenteel gebruikt:

![Paginamodi](/help/sites-cloud/authoring/assets/page-modes.png)

>[!NOTE]
>
>* Afhankelijk van de kenmerken van de pagina zijn sommige modi mogelijk niet beschikbaar.
>* Voor toegang tot bepaalde modi zijn de juiste machtigingen/bevoegdheden vereist.
>* De modus Ontwikkelaar is niet beschikbaar op mobiele apparaten vanwege ruimtebeperkingen.
>* Er is een [sneltoets](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) ( `Ctrl-Shift-M`) om te schakelen tussen **Voorvertoning** en de momenteel geselecteerde modus (bijvoorbeeld **Bewerken**, **Lay-out**, enz.).
>



## Padselectie {#path-selection}

Vaak is het tijdens het ontwerpen nodig een andere bron te selecteren, bijvoorbeeld wanneer u een koppeling naar een andere pagina of bron definieert of een afbeelding selecteert. Als u een pad gemakkelijk wilt selecteren, kunt u in [padvelden](#path-fields) automatisch aanvullen en in de [padbrowser](#path-browser) kunt u een beter gekozen pad kiezen.

### Padvelden {#path-fields}

Het voorbeeld dat hier wordt gebruikt om te illustreren is de afbeeldingscomponent. Zie [Componenten voor pagina&#39;s ontwerpen](/help/sites-cloud/authoring/fundamentals/components.md)voor meer informatie over het gebruik en bewerken van componenten.

Padvelden beschikken nu over de functionaliteit voor automatisch aanvullen en vooruitkijken, zodat u een resource gemakkelijker kunt vinden.

Als u op de knop Dialoogvenster **Selectie** openen in het padveld klikt, wordt het dialoogvenster [Padbrowser](#path-browser) geopend voor gedetailleerdere selectieopties.

![Dialoogvenster Selectie openen](/help/sites-cloud/authoring/assets/open-selection-dialog-button.png)

U kunt ook beginnen te typen in het padveld en AEM biedt tijdens het typen overeenkomende paden.

![Dialoogvenster Selectie openen](/help/sites-cloud/authoring/assets/path-selection-completion.png)

### Padbrowser {#path-browser}

De wegbrowser is georganiseerd als de [kolommening](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) van de plaatsenconsole, die voor meer gedetailleerde selectie van middelen toestaat.

![Padbrowser](/help/sites-cloud/authoring/assets/path-browser.png)

* Zodra een bron is geselecteerd, wordt de knop **Selecteren** rechtsboven in het dialoogvenster actief. Klik of tik om de selectie te bevestigen of **Annuleren** om af te breken.
* Als de context voor de selectie van veelvoudige middelen toestaat, activeert het selecteren van een middel ook de **Uitgezochte** knoop, maar voegt ook een telling van het aantal geselecteerde middelen aan het hoger-recht van het venster toe. Klik op de **X** naast het getal om de selectie van alles op te heffen.
* Wanneer u door de boom navigeert, wordt uw plaats weerspiegeld in de broodkruimels bij de bovenkant van de dialoog. Deze broodkruimels kunnen ook worden gebruikt om snel binnen de middelhiërarchie te springen.
* U kunt op elk gewenst moment het zoekveld boven in het dialoogvenster gebruiken. Klik op de **X** in het zoekveld om de zoekopdracht te wissen.
* Als u uw zoekopdracht wilt beperken, kunt u de filteropties zichtbaar maken en de resultaten filteren op basis van een bepaald pad.

   ![Filters, optie](/help/sites-cloud/authoring/assets/filters-option.png)

## Sneltoetsen {#keyboard-shortcuts}

Er zijn verschillende [sneltoetsen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) beschikbaar.
