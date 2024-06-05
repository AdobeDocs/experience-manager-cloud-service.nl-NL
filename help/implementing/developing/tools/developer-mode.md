---
title: Modus voor ontwikkelaars
seo-title: Developer Mode
description: In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina
seo-description: Developer mode opens a side panel with several tabs that provide a developer with information about the current page
exl-id: fbf11c0f-dc6e-43f3-bcf2-080eacc6ba99
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Modus voor ontwikkelaars {#developer-mode}

Bij het bewerken van pagina&#39;s in AEM, diverse [modi](/help/sites-cloud/authoring/sites-console/introduction.md#page-modes) zijn beschikbaar, inclusief de modus Ontwikkelaar. In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar technische informatie over de huidige pagina bieden.

Er zijn twee tabbladen:

* **[Componenten](#components)** voor het bekijken van structuur en prestatiesinformatie.
* **[Fouten](#errors)** om te zien welke problemen zich voordoen.

Deze hulp een ontwikkelaar om:

* **Discover** hoe de pagina&#39;s worden samengesteld.
* **Foutopsporing:** waar en wanneer gebeurt dat , wat op zijn beurt helpt om problemen op te lossen .

>[!NOTE]
>
>Modus Ontwikkelaar:
>
>* Is niet beschikbaar op mobiele apparaten of kleine vensters op het bureaublad (vanwege ruimtebeperkingen).
>  * Dit gebeurt wanneer de breedte minder dan 1024 px is.
>* Is alleen beschikbaar voor gebruikers die lid zijn van de `administrators` groep.

## Ontwerpmodus openen {#opening-developer-mode}

De modus Ontwikkelaar wordt als een zijpaneel geïmplementeerd in de pagina-editor. Als u het deelvenster wilt openen, selecteert u **Ontwikkelaar** in de moduskiezer op de werkbalk van de pagina-editor:

![De modus Ontwikkelaar openen](assets/developer-mode.png)

Het deelvenster bestaat uit twee tabbladen:

* **[Componenten](#components)** - Dit toont een componentenboom, gelijkend op [inhoudsstructuur](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#content-tree) voor auteurs
* **[Fouten](#errors)** - Als er problemen optreden, worden de details voor elke component weergegeven.

### Tabblad Componenten {#components}

![Tabblad Componenten](assets/developer-mode-components-tab.png)

Dit toont een componentenboom die:

* Hiermee wordt de keten van componenten en sjablonen op de pagina weergegeven. De structuur kan worden uitgebreid om de context binnen de hiërarchie te tonen.
* Geeft de computertijd aan de serverzijde weer die nodig is om de component te renderen.
* Hiermee kunt u de structuur uitvouwen en specifieke componenten in de structuur selecteren. De selectie biedt toegang tot componentdetails, zoals:
   * Pad naar opslagplaats
   * Koppelingen naar scripts (geopend in CRXDE Lite)
   * Componentdetails zoals weergegeven in het dialoogvenster [Componentenconsole](/help/sites-cloud/authoring/components-console.md)
* De componenten die in de boom worden geselecteerd worden vermeld door een blauwe grens in de redacteur.

Op het tabblad Deze componenten kunt u:

* Bepaal en vergelijk de rendertijd per component.
* Zie en begrijp de hiërarchie.
* Begrijp en verbeter vervolgens de laadtijd van de pagina door langzame componenten te zoeken.

Elk componentitem kan de volgende opties hebben:

![Voorbeeld van de component Developer Mode](assets/developer-mode-component-example.png)

* **Details weergeven:** Een koppeling naar een lijst met:
   * Alle componentscripts die worden gebruikt om de component te renderen.
   * Het inhoudspad van de opslagplaats voor deze specifieke component.

     ![Details weergeven](assets/developer-mode-view-details.png)

* **Script bewerken:** Een koppeling waarmee het componentscript in CRXDE Lite wordt geopend.

* **Componentdetails weergeven:** Hiermee opent u de details van de component in het dialoogvenster [Componentenconsole](/help/sites-cloud/authoring/components-console.md).

U kunt een componentitem uitbreiden door te tikken op het chevron of erop te klikken. U kunt ook het volgende weergeven:

    * De hiërarchie binnen de geselecteerde component.
    * Renderingtijden voor de geselecteerde component afzonderlijk, alle afzonderlijke componenten die erin zijn genest en het gecombineerde totaal.

### Tabblad Fouten {#errors}

![Het tabblad Fouten](assets/developer-mode-errors-tab.png)

Hopelijk **Fouten** tab zal altijd leeg zijn (zoals hierboven), maar als er problemen optreden, kunnen de volgende details voor elke component worden weergegeven:

* Een waarschuwing als de component een ingang aan het foutenlogboek, samen met details van de fout en directe verbindingen aan de aangewezen code binnen CRXDE Lite schrijft.
* Een waarschuwing als de component een beheersessie opent.

Als bijvoorbeeld een niet-gedefinieerde methode wordt aangeroepen, wordt de resulterende fout weergegeven in het dialoogvenster **Fouten** en het componentitem in de boomstructuur van het dialoogvenster **Componenten** wordt ook gemarkeerd met een indicator wanneer een fout optreedt.
