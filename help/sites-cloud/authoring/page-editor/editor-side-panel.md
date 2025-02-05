---
title: Zijpaneel paginaeditor
description: Leer hoe u het zijpaneel in de AEM sites-editor kunt gebruiken om componenten en elementen aan uw pagina toe te voegen.
exl-id: 5f025828-f2ca-4cbb-9cdf-a199e9e90cc7
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 0%

---

# Zijpaneel paginaeditor {#side-panel}

Leer hoe u het zijpaneel in de AEM sites-editor kunt gebruiken om componenten en elementen aan uw pagina toe te voegen.

## Zijdeelvenstermodi {#modes}

Het zijpaneel is altijd toegankelijk in de paginaredacteur door het **pictogram van de Kant van de Knevel** in de toolbar van de paginaredacteur te tikken of te klikken.

![ Kneep van het Zijpaneel ](assets/editor-side-panel-side-panel-toggle.png)

Wanneer u het zijpaneel opent, schuift het van de linkerkant open en u kunt dan uit drie belangrijke lusjes selecteren:

* [ Componentenbrowser ](#components-browser) om nieuwe inhoud aan uw pagina toe te voegen
* [ activa browser ](#assets-browser) om nieuwe activa aan uw pagina toe te voegen
* [ de inhoudsboom ](#content-tree) om de structuur van uw pagina te doorbladeren

## Browser voor componenten {#components-browser}

[ Componenten ](/help/implementing/developing/components/overview.md) zijn de bouwstenen die worden gebruikt om inhoud met de AEM paginaredacteur tot stand te brengen. U plaatst veelvoudige componenten op een pagina en vormt hun opties om uw inhoudspagina te bouwen.

De componentenbrowser toont alle componenten die voor gebruik op uw huidige pagina beschikbaar zijn. U kunt deze naar de juiste locatie slepen en vervolgens bewerken om uw inhoud toe te voegen.

Tik of klik het **lusje van Componenten** in het zijpaneel om tot **Componenten** browser toegang te hebben.

![ het browser van Componenten pictogram in het zijpaneel ](assets/editor-side-panel-components-browser.png)

De werkelijke weergave en afhandeling is afhankelijk van het apparaattype dat u gebruikt.

### Mobiel apparaat {#mobile-device-components-browser}

Wanneer u de componentbrowser op een mobiel apparaat opent, wordt de pagina die wordt bewerkt, volledig afgedekt.

Als u een component aan de pagina wilt toevoegen, selecteert u de component en sleept u deze naar rechts. De componentbrowser wordt gesloten om de pagina weer te geven, waar u de component kunt plaatsen.

![ Browser van de Component op mobiele ](assets/editor-side-panel-mobile-device.png)

>[!NOTE]
>
>Een mobiel apparaat wordt gedetecteerd wanneer de breedte minder dan 1024 px is.

### Bureaubladapparaat {#desktop-device-components-browser}

Wanneer u de componentbrowser op een desktopapparaat opent, wordt deze aan de linkerkant van het venster weergegeven.

Als u een component aan de pagina wilt toevoegen, klikt u op de gewenste component en sleept u deze naar de gewenste locatie.

![ Browser van de Component op Desktop ](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

### De Componentenbrowser gebruiken {#using-component-browser}

De componenten in **Componenten** browser worden vertegenwoordigd door:

* Componentnaam
* Componentgroep (grijs)
* Pictogram of afkorting
   * De standaardcomponentpictogrammen zijn monochroom.
   * Afkortingen zijn altijd de eerste twee tekens van de componentnaam.

Van de hoogste toolbar in **Componenten** browser kunt u:

* Componenten filteren op naam.
* Beperk de weergave tot een specifieke groep met behulp van de vervolgkeuzelijst.

Voor een meer gedetailleerde beschrijving van de component, kunt u het informatiepictogram naast de component in **selecteren Componenten** browser (als beschikbaar). Bijvoorbeeld, voor het **Fragment van de Inhoud**:

![ Browser van de Component informatie ](assets/editor-side-panel-component-description.png)

Voor meer gedetailleerde informatie over de componenten beschikbaar aan u ziet de [ Console van de Component ](/help/sites-cloud/authoring/components-console.md)

## Assets Browser {#assets-browser}

**Assets** browser toont alle [ activa ](/help/assets/overview.md) die voor gebruik op uw huidige pagina beschikbaar zijn.

Tik of klik het **Assets** lusje op het zijpaneel om door de activa te doorbladeren.

![ Browser van Assets knoop ](assets/editor-side-panel-assets-browser-tab.png)

Met oneindig schuiven vouwt u de lijst met elementen zo nodig uit terwijl u schuift.

![ Browser van Assets ](assets/editor-side-panel-assets-browser.png)

De daadwerkelijke verschijning en behandeling zijn afhankelijk van het apparatentype u gebruikt:

### Mobiel apparaat {#mobile-device-assets-browser}

Wanneer u de middelenbrowser op een mobiel apparaat opent, wordt de pagina die wordt bewerkt, volledig afgedekt.

Als u een element aan uw pagina wilt toevoegen, selecteert u het gewenste element en sleept u het naar rechts. De middelenbrowser wordt gesloten om de pagina weer te tonen, waar u het element aan de vereiste component kunt toevoegen.

![ Browser van Assets op mobiele ](assets/editor-side-panel-assets-browser-mobile.png)

>[!NOTE]
>
>Een mobiel apparaat wordt gedetecteerd wanneer de breedte minder dan 1024 px is.

### Bureaubladapparaat {#desktop-device-assets-browser}

Wanneer u de middelenbrowser op een desktopapparaat opent, wordt deze links in het venster geopend.

Als u een element aan uw pagina wilt toevoegen, selecteert u het gewenste element en sleept u het naar de gewenste component of locatie.

![ Browser van Assets op Desktop ](assets/editor-side-panel-assets-browser-desktop.png)

### De Assets Browser gebruiken {#using-assets-browser}

Als u een element aan de pagina wilt toevoegen, selecteert u het element en sleept u het naar de gewenste locatie. Dit kan zijn:

* Een bestaand onderdeel van het desbetreffende type.
   * U kunt bijvoorbeeld een element van het type afbeelding naar een afbeeldingscomponent slepen.
* A [ placeholder ](/help/sites-cloud/authoring/page-editor/edit-content.md#component-placeholder) in het paragraafsysteem om een component van het aangewezen type tot stand te brengen.
   * U kunt bijvoorbeeld een element van het type afbeelding naar het alineasysteem slepen om een component Image te maken.

>[!NOTE]
>
>Het slepen en neerzetten van elementen is beschikbaar voor specifieke elementen en componenttypen. Zie [ Invoegend een Component gebruikend Browser van Assets ](/help/sites-cloud/authoring/page-editor/edit-content.md#adding-a-component-from) voor meer details.

Vanuit de bovenste werkbalk van de middelenbrowser kunt u de elementen filteren op:

* Naam
* Pad
* Elementtype zoals afbeeldingen, video&#39;s, documenten, alinea&#39;s, inhoudsfragmenten en ervaringsfragmenten
* Elementkenmerken zoals oriëntatie en stijl
   * Alleen beschikbaar voor bepaalde typen elementen

Als u een verandering in activa moet snel aanbrengen, kunt u de [ activaredacteur ](/help/assets/manage-digital-assets.md) van activa direct van activabrowser beginnen door het Edit pictogram naast de naam van activa te klikken wordt getoond die.

![ Activa geeft knoop uit ](assets/editor-side-panel-asset-edit-button.png)

## Inhoudsstructuur {#content-tree}

De **Boom van de Inhoud** geeft een overzicht van alle componenten op de pagina in een hiërarchie zodat kunt u in een blik zien hoe de pagina wordt samengesteld.

>[!NOTE]
>
>De inhoudsstructuur is niet beschikbaar als u een pagina bewerkt op een mobiel apparaat (als de breedte van de browser minder dan 1024 px is).

Tik of klik het **lusje van de Boom van de Inhoud** om tot de inhoudsboom toegang te hebben.

![ knoop van de Boom van de Inhoud ](assets/editor-side-panel-content-tree-tab.png)

Wanneer open kunt u een vertegenwoordiging van de boommening van uw pagina of malplaatje zien, zodat het gemakkelijker is om te begrijpen hoe zijn inhoud hiërarchisch gestructureerd is. Op een complexe pagina is het bovendien gemakkelijker om tussen componenten van de pagina te schakelen.

![ de Boom van de Inhoud ](assets/editor-side-panel-content-tree.png)

Een pagina kan gemakkelijk uit veel van hetzelfde type componenten bestaan, zodat in de inhoudsstructuur beschrijvende tekst (grijs) achter de naam van het componenttype (in zwart) wordt weergegeven. De beschrijvende tekst is afkomstig uit gemeenschappelijke eigenschappen van de component, zoals titel of tekst.

Componenttypen worden weergegeven in de taal van de gebruiker, terwijl de tekst van de componentbeschrijving uit de paginataal komt.

Als u klikt op het chevron naast een component, wordt dat niveau samengevouwen of uitgevouwen.

![ de uitbreiding van de Boomboom van de Inhoud ](assets/editor-side-panel-content-tree-chevron.png)

Wanneer u op de component klikt, wordt de component in de pagina-editor gemarkeerd. Welke acties beschikbaar zijn, is afhankelijk van de paginastatus. Bijvoorbeeld:

## Een basispagina {#basic-page}

De componenten van een basispagina hebben de gebruikelijke opties.

![ benadrukte de Boom van de Inhoud ](assets/editor-side-panel-content-tree-highlighted.png)

Als de component waarop u klikt in de structuur bewerkbaar is, wordt er een moersleutelpictogram rechts van de naam weergegeven. Wanneer u op dit pictogram klikt, wordt het dialoogvenster Bewerken voor de component gestart.

![ de Boom van de Inhoud geeft knoop uit ](assets/editor-side-panel-content-tree-edit.png)

### Een actieve kopie {#live-copy}

Een pagina die deel van a [ livecopy ](/help/sites-cloud/administering/msm/overview.md) uitmaakt, waar de componenten van een andere pagina worden geërft, zal verschillende opties hebben.

## Gekoppelde inhoudsbrowser {#associated-content-browser}

Als uw pagina de Fragmenten van de Inhoud bevat, hebt u ook toegang tot [ browser voor Verwante Inhoud ](/help/sites-cloud/authoring/fragments/content-fragments.md#using-associated-content).
