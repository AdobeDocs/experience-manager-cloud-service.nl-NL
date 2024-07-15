---
title: Responsief ontwerp
description: Met responsief ontwerp kunnen dezelfde ervaringen effectief worden weergegeven op meerdere apparaten in verschillende richtingen.
exl-id: be645062-d6d6-45a2-97dc-d8aa235539b8
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# Responsief ontwerp {#responsive-design}

Ontwerp uw ervaringen zodat ze zich aanpassen aan de clientviewport waarin ze worden weergegeven. Met responsief ontwerp kunnen dezelfde pagina&#39;s effectief op meerdere apparaten in beide richtingen worden weergegeven. In de volgende afbeelding ziet u enkele manieren waarop een pagina kan reageren op wijzigingen in de viewportgrootte:

* Lay-out: gebruik lay-outs met één kolom voor kleinere viewports en lay-outs met meerdere kolommen voor grotere viewports.
* Tekengrootte: gebruik grotere tekstgrootte (indien van toepassing, zoals koppen) in grotere viewports.
* Inhoud: neem alleen de belangrijkste inhoud op wanneer u deze weergeeft op kleinere apparaten.
* Navigatie: er zijn apparaatspecifieke gereedschappen voor toegang tot andere pagina&#39;s.
* Afbeeldingen: afbeeldingsuitvoeringen die geschikt zijn voor de viewport van de client, worden weergegeven op basis van de afmetingen van het venster.

![ Voorbeelden van ontvankelijk ontwerp ](assets/responsive-example.png)

Ontwikkel Adobe Experience Manager (AEM) toepassingen die HTML5 produceren die zich aan veelvoudige venstergrootte en richtlijn aanpassen. De volgende bereiken van viewport-breedten komen bijvoorbeeld overeen met verschillende apparaattypen en -oriëntaties

* Maximale breedte van 480 pixels (telefoon, staand)
* Maximale breedte van 767 pixels (telefoon, liggend)
* Breedte tussen 768 pixels en 979 pixels (tablet, staand)
* Breedte tussen 980 pixels en 1199 pixels (tablet, liggend)
* Breedte van 1200 px of hoger (bureaublad)

Zie de volgende onderwerpen voor informatie over het uitvoeren van ontvankelijk ontwerpgedrag:

* [Mediaquery&#39;s](#using-media-queries)
* [Vloeiende rasters](#developing-a-fluid-grid)
* [Adaptieve afbeeldingen](#using-adaptive-images)

Aangezien u ontwerpt, gebruik de **Mededinger** toolbar aan voorproef uw pagina&#39;s voor diverse het schermgrootte.

## Voordat u ontwikkelt {#before-you-develop}

Voordat u de AEM ontwikkelt die uw webpagina&#39;s ondersteunt, moet u een aantal ontwerpbeslissingen nemen. U moet bijvoorbeeld over de volgende informatie beschikken:

* De apparaten waarvoor u zich richt
* De doelviewportgrootten
* De paginalay-outs voor elk van de beoogde viewportgrootte

### Toepassingsstructuur {#application-structure}

De typische AEM toepassingsstructuur ondersteunt alle responsieve ontwerpimplementaties:

* Paginacomponenten bevinden zich onder `/apps/<application_name>/components`
* Sjablonen bevinden zich onder `/apps/<application_name>/templates`

## Mediaquery&#39;s gebruiken {#using-media-queries}

Met mediaquery&#39;s kunt u CSS-stijlen selectief gebruiken voor het weergeven van pagina&#39;s. AEM ontwikkelingshulpmiddelen en eigenschappen laten u toe om media vragen in uw toepassingen effectief en efficiënt uit te voeren.

De W3C groep verstrekt de ](https://www.w3.org/TR/css3-mediaqueries/) aanbeveling van de Vragen van Media 0} {die deze CSS3 eigenschap en de syntaxis beschrijft.[

### Het CSS-bestand maken {#creating-the-css-file}

Definieer in uw CSS-bestand mediaquery&#39;s op basis van de eigenschappen van de apparaten waarvoor u een mediaquery maakt. De volgende implementatiestrategie is effectief voor het beheren van stijlen voor elke mediaquery:

* Gebruik de omslag van de Bibliotheek van de a [ Cliënt ](clientlibs.md) om CSS te bepalen die wordt samengesteld wanneer de pagina wordt teruggegeven.
* Definieer elke mediaquery en de bijbehorende stijlen in afzonderlijke CSS-bestanden. Het is handig bestandsnamen te gebruiken die de apparaatfuncties van de mediaquery vertegenwoordigen.
* Definieer stijlen die op alle apparaten in een afzonderlijk CSS-bestand van toepassing zijn.
* In het css.txt- dossier van de omslag van de Bibliotheek van de Cliënt, orde de lijst CSS dossiers zoals vereist in het geassembleerde CSS dossier.

Het [ WKND leerprogramma ](develop-wknd-tutorial.md) gebruikt deze strategie om stijlen in het plaatsontwerp te bepalen. Het CSS-bestand dat door WKND wordt gebruikt, bevindt zich op `/apps/wknd/clientlibs/clientlib-grid/less/grid.less` .

### Mediaquery&#39;s gebruiken met AEM pagina&#39;s {#using-media-queries-with-aem-pages}

[ het WKND steekproefproject ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) en [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) gebruiken de [ Component van de Kern van de Pagina, ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/page.html) die clientlibs via het paginabeleid omvat.

Als uw eigen paginacomponent niet op de Component van de Kern van de Pagina wordt gebaseerd, kunt u de omslag van de cliëntbibliotheek in het manuscript van HTML of JSP van het ook omvatten. Als u dit doet, wordt het CSS-bestand gegenereerd en wordt ernaar verwezen met de mediaquery&#39;s die nodig zijn om het responsieve raster te laten werken.

#### HTL {#htl}

```html
<sly data-sly-use.clientlib="${'/libs/granite/sightly/templates/clientlib.html'}">
<sly data-sly-call="${clientlib.all @ categories='apps.weretail.all'}"/>
```

#### JSP {#jsp}

```xml
<ui:includeClientLib categories="apps.weretail.all"/>
```

Met het JSP-script wordt de volgende HTML-code gegenereerd die verwijst naar de stijlpagina&#39;s:

```xml
<link rel="stylesheet" href="/etc/designs/weretail/clientlibs-all.css" type="text/css">
<link href="/etc/designs/weretail.css" rel="stylesheet" type="text/css">
```

## Voorvertonen voor specifieke apparaten {#previewing-for-specific-devices}

Met de emulator kunt u uw pagina&#39;s voorvertonen in verschillende viewportgrootten, zodat u het gedrag van uw responsieve ontwerp kunt testen. Wanneer het uitgeven van een pagina in de Console van Plaatsen, kunt u het **Emulator** pictogram tikken of klikken om de mededinger te openbaren.

![ het emulatorpictogram in de toolbar ](assets/emulator-icon.png)

In de emulatortoolbar kunt u het **pictogram van Apparaten** ontsteken of klikken om een drop-down menu te openbaren waar u een apparaat kunt selecteren. Wanneer u een apparaat selecteert, wordt de pagina aangepast aan het formaat van de viewport.

![ de mededingertoolbar ](assets/emulator.png)

### Apparaatgroepen opgeven {#specifying-device-groups}

Om de apparatengroepen te specificeren die in de **lijst van Apparaten** verschijnen, voeg a `cq:deviceGroups` bezit aan de `jcr:content` knoop van de malplaatjepagina van uw plaats toe. De waarde van de eigenschap is een array van paden naar de knooppunten van de apparaatgroep.

De sjabloonpagina van de WKND-site is bijvoorbeeld `/conf/wknd/settings/wcm/template-types/empty-page/structure` . En het knooppunt `jcr:content` eronder bevat de volgende eigenschap:

* Naam: `cq:deviceGroups`
* Type: `String[]`
* Waarde: `mobile/groups/responsive`

Apparaatgroepknooppunten bevinden zich in de map `/etc/mobile/groups` .

## Responsieve afbeeldingen {#responsive-images}

Responsieve pagina&#39;s worden dynamisch aangepast aan het apparaat waarop ze worden weergegeven en bieden een betere gebruikerservaring. Het is echter ook belangrijk dat elementen zijn geoptimaliseerd voor het onderbrekingspunt en het apparaat om de laadtijd van de pagina te minimaliseren.

[ de Component van het Beeld van de Component van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html) eigenschappen zoals adaptieve beeldselectie.

* Door gebrek, gebruikt de Component van het Beeld de [ Aangepaste Servlet van het Beeld ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/adaptive-image-servlet.html) om de juiste vertoning te leveren.
* [ Web-Geoptimaliseerde Levering van het Beeld ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) is ook beschikbaar via eenvoudige checkbox in zijn beleid, dat beeldactiva van DAM in formaat WebP levert en de downloadgrootte van een beeld met ongeveer 25% gemiddeld kan verminderen.

## De container voor lay-out {#layout-container}

AEM de Container van de Lay-out staat u toe om ontvankelijke lay-out efficiënt en effectief uit te voeren om de afmetingen van de pagina aan cliëntviewport aan te passen.

Gelieve te zien het document [ Vormende de Container van de Lay-out en Wijze van de Lay-out ](/help/sites-cloud/administering/responsive-layout.md) voor meer informatie over hoe de Container van de Lay-out werkt en hoe te om ontvankelijke lay-outs voor uw inhoud toe te laten.
