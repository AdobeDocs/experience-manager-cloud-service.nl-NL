---
title: Edge Delivery Services gebruiken met bestaande AEM projecten
description: Leer hoe u de voordelen van Edge Delivery Services voor uw bestaande AEM kunt benutten
feature: Edge Delivery Services
exl-id: f54aac3a-1d0c-4be0-9aa6-616217e0e458
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Edge Delivery Services gebruiken met bestaande AEM projecten {#existing-projects}

U hoeft niet te wachten tot een nieuw AEM project van Edge Delivery Services profiteert. Edge Delivery Services kunnen worden geïntegreerd in uw bestaande AEM-project, zodat u de prestatiewinst direct kunt benutten.

## Beperkingen in paginaeditor AEM {#page-editor}

Voor de komst van Edge Delivery Services werd in AEM beheerde inhoud bewerkt met de AEM Pagina-editor. Als uw project vóór de introductie van Edge Delivery Services begon, is het bijna zeker dat u de Redacteur van de Pagina gebruikt.

De AEM Redacteur van de Pagina werkt slechts met [ AEM componenten ](/help/implementing/developing/components/overview.md) zoals de [ Componenten van de Kern.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) Deze componenten zijn niet compatibel met Edge Delivery Services. Wegens dit, worden twee fasen vereist om Edge Delivery Services aan een bestaand AEM project te introduceren:

* [Fase 1 - Voorste einde vervangen](#replace-front-end)
* [Fase 2 - Overschakelen naar Universal Editor](#switch-ue)

## Fase 1 - Voorste einde vervangen {#replace-front-end}

In fase één kunt u de bestaande AEM sitestructuur, componenten en ontwerpgereedschappen blijven gebruiken. De websiterendering wordt herbouwd met behulp van blokken die JavaScript en CSS gebruiken en wordt via Edge Delivery Services geleverd.

Gelieve te zien de [ sectie van de Bouwstijl ](/help/edge/developer/block-collection.md) van de documentatie van Edge Delivery Services voor meer details op blokken en hoe te zich voor de diensten van Edge Delivery ontwikkelen.

Een converter op App Builder is vereist om de AEM gerenderde HTML uitvoer om te zetten en naar Edge Delivery Services te verzenden.

![ de inhoudsomzetter in de het publiceren stroom ](assets/content-converter.png)

Fase twee voltooit het proces door de technologieoverlapping te elimineren: AEM de Componenten van de Kern met HTML en Java op AEM Auteur, op JS-Gebaseerde Blokken op Edge Delivery, en een op knoopJS-Gebaseerde converter.

## Fase 2 - Overschakelen naar Universal Editor {#switch-ue}

In deze fase wordt de AEM Pagina-editor vervangen door de Universal Editor. Omdat de Universal Editor rechtstreeks met blokken kan werken, zijn de AEM Core Components en converter niet meer nodig.

