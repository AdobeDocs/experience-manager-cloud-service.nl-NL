---
title: Ontwerpmodus
seo-title: Developer Mode
description: In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina
seo-description: Developer mode opens a side panel with several tabs that provide a developer with information about the current page
source-git-commit: b80aaa799e1652f7a981006925b50ffef43d7ab3
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Ontwerpmodus {#developer-mode}

Bij het bewerken van pagina&#39;s in AEM zijn verschillende [modi](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) beschikbaar, waaronder de modus Ontwikkelaar. In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar technische informatie over de huidige pagina bieden.

Er zijn twee tabbladen:

* **[](#components)** Componenten voor het bekijken van structuur en prestatiesinformatie.
* **[](#errors)** Fouten om problemen te zien optreden.

Deze hulp een ontwikkelaar om:

* **Ontdek** hoe de pagina&#39;s zijn samengesteld.
* **Foutopsporing:** wat gebeurt er waar en wanneer, wat op zijn beurt weer helpt om problemen op te lossen.

>[!NOTE]
>
>Modus Ontwikkelaar:
>
>* Is niet beschikbaar op mobiele apparaten of kleine vensters op het bureaublad (vanwege ruimtebeperkingen).
>  * Dit gebeurt wanneer de breedte minder dan 1024 px is.
>* Is alleen beschikbaar voor gebruikers die lid zijn van de groep `administrators`.


## Ontwerpmodus openen {#opening-developer-mode}

De modus Ontwikkelaar wordt als een zijpaneel geïmplementeerd in de pagina-editor. Als u het deelvenster wilt openen, selecteert u **Developer** in de moduskiezer op de werkbalk van de pagina-editor:

![De modus Ontwikkelaar openen](assets/developer-mode.png)

Het deelvenster bestaat uit twee tabbladen:

* **[Componenten](#components)**  - Dit toont een componentstructuur, vergelijkbaar met de  [inhoudslijn ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree) voor auteurs
* **[Fouten](#errors)**  - Wanneer er problemen optreden, worden de details voor elke component weergegeven.

### Tabblad Componenten {#components}

![Tabblad Componenten](assets/developer-mode-components-tab.png)

Dit toont een componentenboom die:

* Hiermee wordt de keten van componenten en sjablonen op de pagina weergegeven. De structuur kan worden uitgebreid om de context binnen de hiërarchie te tonen.
* Geeft de computertijd aan de serverzijde weer die nodig is om de component te renderen.
* Hiermee kunt u de structuur uitvouwen en specifieke componenten in de structuur selecteren. De selectie biedt toegang tot componentdetails; zoals:
   * Pad naar opslagplaats
   * Koppelingen naar scripts (geopend in CRXDE Lite)
   * Componentdetails zoals weergegeven in de [Componentconsole](/help/sites-cloud/authoring/features/components-console.md)
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

* **Script bewerken:** een koppeling waarmee het componentscript in CRXDE Lite wordt geopend.

* **Componentdetails weergeven:** opent de details van de component in de  [componentconsole.](/help/sites-cloud/authoring/features/components-console.md)

U kunt een componentitem uitbreiden door te tikken op het chevron of erop te klikken. U kunt ook het volgende weergeven:

    * De hiërarchie binnen de geselecteerde component.
    * Renderingtijden voor de geselecteerde component afzonderlijk, alle afzonderlijke componenten die erin zijn genest en het gecombineerde totaal.

### Tabblad Fouten {#errors}

![Het tabblad Fouten](assets/developer-mode-errors-tab.png)

Hopelijk is het tabblad **Fouten** altijd leeg (zoals hierboven), maar wanneer er problemen optreden, kunnen de volgende details voor elke component worden weergegeven:

* Een waarschuwing als de component een ingang aan het foutenlogboek, samen met details van de fout en directe verbindingen aan de aangewezen code binnen CRXDE Lite schrijft.
* Een waarschuwing als de component een beheersessie opent.

Als bijvoorbeeld een ongedefinieerde methode wordt aangeroepen, wordt de resulterende fout weergegeven op het tabblad **Fouten** en wordt het componentitem in de boomstructuur van het tabblad **Componenten** ook gemarkeerd met een indicator wanneer een fout optreedt.
