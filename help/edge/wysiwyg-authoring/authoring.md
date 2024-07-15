---
title: Inhoud ontwerpen voor Edge Delivery Services
description: Leer hoe u inhoud ontwerpt met Edge Delivery Services en hoe u AEM inhoud ontwerpt met Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 963ff71a-8176-4d9d-8240-dc429405d139
role: User
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Inhoud ontwerpen voor Edge Delivery Services {#authoring-edge}

Met Edge Delivery Services is ontwerpen eenvoudig, snel en flexibel. U hebt twee opties om inhoud voor Edge Delivery Services te ontwerpen:

* [ Universele Redacteur ](#universal-editor) - een moderne wat-u-ziet-is-wat-u-krijgt (WYSIWYG) UI voor auteursinhoud binnen AEM
* [ document-Gebaseerde Authoring ](#document-based) - zoals Microsoft Word of Google Docs

## Universal Editor Authoring {#universal-editor}

Als u Edge Delivery Services gebruikt met AEM as a Cloud Service, is het meest fundamentele feit dat u begrijpt dat de inhoud die u maakt, in AEM as a Cloud Service blijft bestaan.

![ hoe WYSIWYG Authoring met Edge Delivery Services ](assets/how-aem-edge-works.png)

1. [ het WYSIWYG Authoring milieu ](/help/sites-cloud/authoring/quick-start.md) wordt gebruikt voor inhoudsbeheer zoals het creëren van nieuwe pagina&#39;s, de Fragmenten van de Ervaring, de Fragmenten van de Inhoud, enz.
   * Alle functies van AEM zijn beschikbaar, zoals workflows, MSM, transleren, Starten, enz.
1. [ de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) wordt gebruikt aan auteur de inhoud die in AEM wordt beheerd.
   * De Universal Editor biedt een nieuwe en moderne UI voor het schrijven van inhoud.
   * Voor het ontwerpen, AEM geeft de HTML terug maar omvat de manuscripten, de stijlen, de pictogrammen en andere middelen van Edge Delivery Services.
   * Hoewel de Universal Editor wordt gebruikt, blijven alle wijzigingen AEM.
   * De Universal Editor heeft nog geen pariteit met de AEM Page Editor en sommige AEM zijn mogelijk niet beschikbaar in de Universal Editor.
1. De inhoud die u met de Universele Redacteur creeert en aan AEM blijft wordt gepubliceerd aan Edge Delivery Services.
   * De inhoud blijft opgeslagen in AEM.
   * AEM geeft semantische HTML die nodig is voor inname.
   * Inhoud wordt gepubliceerd naar Edge Delivery Services.
1. [ Edge Delivery Services ](/help/edge/developer/keeping-it-100.md) verzekeren een score van 100% Lighthouse.

Blokken zijn basisonderdelen van een pagina die door Edge Delivery Services wordt geleverd. De auteurs kunnen van standaardblokken kiezen die door Adobe worden verstrekt of van blokken die voor uw project door uw ontwikkelaars worden aangepast.

De Universal Editor biedt een moderne en intuïtieve GUI voor het ontwerpen van uw inhoud door blokken te slepen en neer te zetten.

![ het slepen-en-droppen blokken in de Universele Redacteur ](assets/blocks.png)

De details van de blokken kunnen dan in de spoorstaaf van Eigenschappen worden gevormd.

![ Vormend blokeigenschappen ](assets/block-properties.png)

Voor details op hoe te om auteur te gebruiken de Universele Redacteur, te zien gelieve het document [ Authoring Inhoud met de Universele Redacteur.](/help/sites-cloud/authoring/universal-editor/authoring.md)

Gelieve te zien de [ Begonnen Gids van de Ontwikkelaar Begonnen voor WYSIWYG Authoring met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) om te leren hoe te om uw eigen project aan auteur met AEM en Edge Delivery Services te beginnen.

## Authoring op basis van documenten  {#document-based}

Wanneer u op documenten gebaseerde documenten gebruikt, kunt u met diverse bronnen werken, zoals Microsoft Word- en Google Docs-documenten. Documenten uit deze bronnen worden pagina&#39;s op uw website. Koppen, lijsten, afbeeldingen, lettertype-elementen en video&#39;s kunnen allemaal van de oorspronkelijke bron naar uw website worden overgebracht. U kunt metagegevens toevoegen voor SEO-doeleinden of blokken gebruiken om met gestructureerde inhoud te werken en functionaliteit toe te voegen.

Voor verdere details op document-gebaseerde creatie, gelieve te verwijzen naar [ dit document in de documentatie van Edge Delivery Services.](/help/edge/docs/authoring.md)

