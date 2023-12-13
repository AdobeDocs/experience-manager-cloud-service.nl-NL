---
title: Inhoud ontwerpen voor Edge Delivery Services
description: Leer hoe u inhoud ontwerpt met Edge Delivery Services en hoe u AEM inhoud ontwerpt met Edge Delivery Services.
feature: Edge Delivery Services
source-git-commit: 22a791311c618fcbd61f321b8efa79c3a52ec65d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---


# Inhoud ontwerpen voor Edge Delivery Services {#authoring-edge}

Met Edge Delivery Services is ontwerpen eenvoudig, snel en flexibel. U hebt twee opties om inhoud voor Edge Delivery Services te ontwerpen:

* [Op documenten gebaseerde ontwerpfuncties](#document-based) - zoals Microsoft Word of Google Docs
* [Universele editor](#universal-editor) - Een moderne gebruikersinterface voor het ontwerpen van inhoud binnen AEM

## Authoring op basis van documenten {#document-based}

In het geval van op documenten gebaseerde authoring kunt u werken met diverse bronnen, zoals Microsoft Word en Google Docs. Documenten uit deze bronnen worden pagina&#39;s op uw website. Koppen, lijsten, afbeeldingen, lettertype-elementen en video&#39;s kunnen allemaal van de oorspronkelijke bron naar uw website worden overgebracht. U kunt metagegevens toevoegen voor SEO-doeleinden of blokken gebruiken om met gestructureerde inhoud te werken en functionaliteit toe te voegen.

Voor meer informatie over het schrijven van documenten raadpleegt u [dit document in de documentatie van Edge Delivery Services.](/help/edge/docs/authoring.md)

## Universal Editor Authoring {#universal-editor}

Wanneer het gebruiken van Edge Delivery Services met AEM as a Cloud Service, is het meest fundamentele feit te begrijpen dat de inhoud u creeert in AEM as a Cloud Service voortduurt.

![Hoe AEM creatie met Edge Delivery Services werkt](assets/how-aem-edge-works.png)

1. [De AEM ontwerpomgeving](/help/sites-cloud/authoring/getting-started/quick-start.md) wordt gebruikt voor inhoudsbeheer, zoals het maken van nieuwe pagina&#39;s, ervaringsfragmenten, inhoudsfragmenten, enz.
   * Alle functies van AEM zijn beschikbaar, zoals workflows, MSM, transleren, Starten, enz.
1. [De Universal Editor](/help/implementing/universal-editor/authoring.md) wordt gebruikt aan auteur de inhoud die in AEM wordt beheerd.
   * De Universal Editor biedt een nieuwe en moderne UI voor het schrijven van inhoud.
   * Voor het ontwerpen, AEM geeft de HTML terug maar omvat de manuscripten, de stijlen, de pictogrammen en andere middelen van Edge Delivery Services.
   * Hoewel de Universal Editor wordt gebruikt, blijven alle wijzigingen AEM.
   * De Universal Editor heeft nog geen pariteit met de AEM Page Editor en sommige AEM zijn mogelijk niet beschikbaar in de Universal Editor.
1. De inhoud die u met de Universele Redacteur creeert en aan AEM blijft wordt gepubliceerd aan Edge Delivery Services.
   * De inhoud blijft opgeslagen in AEM.
   * AEM geeft semantische HTML die nodig is voor inname.
   * Inhoud wordt gepubliceerd naar Edge Delivery Services.
1. [Edge Delivery Services](/help/edge/developer/keeping-it-100.md) een 100% Lighthouse score behalen.

Blokken zijn basisonderdelen van een pagina die door Edge Delivery Services wordt geleverd. De auteurs kunnen van standaardblokken kiezen die door Adobe worden verstrekt of van blokken die voor uw project door uw ontwikkelaars worden aangepast.

De Universal Editor biedt een moderne en intuïtieve GUI voor het ontwerpen van uw inhoud door blokken te slepen en neer te zetten.

![Blokken slepen en neerzetten in de Universal Editor](assets/blocks.png)

De details van de blokken kunnen dan in de spoorstaaf van Eigenschappen worden gevormd.

![Blokeigenschappen configureren](assets/block-properties.png)

Zie het document voor meer informatie over hoe u de Universal Editor kunt gebruiken [Inhoud ontwerpen met de Universal Editor.](/help/implementing/universal-editor/authoring.md)

## Aan de slag {#how-to-get-started}

Neem contact op met uw Adobe voor toegang tot deze functie.
