---
title: WYSIWYG Content Authoring voor Edge Delivery Services
description: Leer hoe u inhoud ontwerpt met Edge Delivery Services en hoe u AEM-inhoud ontwerpt met Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 963ff71a-8176-4d9d-8240-dc429405d139
role: User
index: false
hide: true
hidefromtoc: true
source-git-commit: e57610e4c5e498ddfdbaa0ba39c9197ecfb5d177
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# WYSIWYG Content Authoring voor Edge Delivery Services {#authoring-edge}

Met Edge Delivery Services is ontwerpen eenvoudig, snel en flexibel. U hebt twee opties om inhoud voor Edge Delivery Services te schrijven:

* [ Universele Redacteur ](#universal-editor) - een moderne wat-u-ziet-is-wat-u-krijgt (WYSIWYG) UI voor auteursinhoud binnen AEM
* [ op document-Gebaseerde Authoring ](#document-based) - zoals Microsoft Word of Google Docs

## Universal Editor Authoring {#universal-editor}

Als u Edge Delivery Services gebruikt met AEM as a Cloud Service, is het meest fundamentele feit dat u begrijpt dat de inhoud die u maakt, in AEM as a Cloud Service blijft bestaan.

![ hoe de Authoring van WYSIWYG met Edge Delivery Services ](assets/how-aem-edge-works.png) werkt

1. [ het milieu van AEM Sites ](/help/sites-cloud/authoring/quick-start.md) wordt gebruikt voor inhoudsbeheer zoals het creëren van nieuwe pagina&#39;s, de Fragmenten van de Ervaring, de Fragmenten van de Inhoud, enz.
   * Alle functies van AEM zijn beschikbaar, zoals workflows, MSM, transleren, Starten, enzovoort.
1. [ de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) wordt gebruikt aan auteur de inhoud die in AEM wordt beheerd.
   * De Universal Editor biedt een nieuwe en moderne UI voor het schrijven van inhoud.
   * Voor ontwerpen rendert AEM de HTML, maar bevat deze de scripts, stijlen, pictogrammen en andere bronnen uit Edge Delivery Services.
   * Hoewel de Universal Editor wordt gebruikt, blijven alle wijzigingen in AEM bestaan.
   * De Universal Editor heeft nog geen pariteit met de AEM Page Editor en sommige AEM-functies zijn mogelijk niet beschikbaar in de Universal Editor.
1. Inhoud die u met de Universal Editor maakt en die nog steeds in AEM aanwezig is, wordt gepubliceerd naar Edge Delivery Services.
   * Inhoud blijft opgeslagen in AEM.
   * AEM geeft semantische HTML weer die nodig is voor inname.
   * Inhoud wordt gepubliceerd naar Edge Delivery Services.
1. [ Edge Delivery Services ](/help/edge/developer/keeping-it-100.md) verzekert een score van 100% Lighthouse.

Blokken zijn fundamentele onderdelen van een pagina die door Edge Delivery Services wordt geleverd. Auteurs kunnen kiezen uit standaardblokken die standaard door Adobe worden geleverd of uit blokken die door uw ontwikkelaars zijn aangepast voor uw project.

De Universele Redacteur verstrekt een moderne en intuïtieve GUI voor het ontwerpen van uw inhoud door blokken toe te voegen en te schikken.

![ Toevoegend en rangschikkend blokken in de Universele Redacteur ](assets/blocks.png)

De details van de blokken kunnen dan in het paneel van Eigenschappen worden gevormd.

![ Vormend blokeigenschappen ](assets/block-properties.png)

Voor details op hoe te om auteur te gebruiken de Universele Redacteur, te zien gelieve het document [ Authoring Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md).

Gelieve te zien de [ Begonnen Gids van de Ontwikkelaar Begonnen voor de Authoring van WYSIWYG met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) om te leren hoe te om uw eigen project aan auteur met AEM en Edge Delivery Services te beginnen.

## Aanvullende ontwerpmethoden  {#authoring-methods}

WYSIWYG-authoring is een krachtig en intuïtief hulpmiddel voor inhoudsauteurs. Er zijn echter veel verschillende gebruiksgevallen bij het ontwerpen, en daarom biedt AEM aanvullende oplossingen bij het ontwerpen.

Gelieve te zien het document [ Overzicht van Edge Delivery Services ](/help/edge/overview.md#authoring-method) om meer over de auteursoplossingen te leren AEM aanbiedingen met inbegrip van op document-gebaseerde creatie en zonder kop aanbiedt.
