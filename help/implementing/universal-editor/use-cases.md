---
title: De universele Redacteur gebruikt Gevallen en Lerende Wegen
description: Leer over de belangrijkste gebruiksgevallen van de Universele Redacteur en hoe het best te leren over zijn gebruik en hoe te om het op uw eigen projecten uit te voeren.
source-git-commit: 45418e5fd431980b48eda83811d5544154027d84
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# De universele Redacteur gebruikt Gevallen en Lerende Wegen {#use-cases-learning-paths}

Leer over de belangrijkste gebruiksgevallen van de Universele Redacteur en hoe het best om meer over zijn gebruik te leren en hoe te om het op uw eigen projecten uit te voeren.

## Overzicht {#overview}

De Universal Editor is een veelzijdige visuele editor die deel uitmaakt van Adobe Experience Manager Sites. Auteurs kunnen hiermee WYSIWYG-bewerkingen (what-you-see-is-what-you-get) zonder kop of met veel ervaring uitvoeren.

Dit document verklaart deze twee gebruiksgevallen in detail en toont u hoe u meer over hen kunt leren zodat kunt u de Universele Redacteur in uw eigen project uitvoeren.

>[!TIP]
>
>Als u dit nog niet hebt gedaan, kunt u het document reviseren [Introductie van Universal Editor](/help/implementing/universal-editor/introduction.md) voor een volledig overzicht en waarde van de Universal Editor.

## Gevallen gebruiken {#use-cases}

De Universal Editor biedt een handige, intuïtieve visuele editor aan de auteurs van de inhoud, ongeacht het type inhoud dat ze maken. De twee belangrijkste gebruiksgevallen zijn:

* [AEM maken](#aem-authoring) - Gebruik de AEM Sites-console om uw inhoud en auteurspagina&#39;s binnen AEM te beheren met de Universal Editor
* [Headless Authoring](#headless-authoring) - Inhoud in uw eigen aangepaste headless-toepassing ontwerpen met de Universal Editor.

### AEM maken {#aem-authoring}

Als u al vertrouwd bent met AEM, kunt u de console van Plaatsen gebruiken om uw pagina&#39;s tot stand te brengen en te beheren en hen dan uit te geven met de Universele Redacteur.

Op deze manier kunt u profiteren van de gereedschappen die beschikbaar zijn in de Sites-console, zoals paginabeheer (kopiëren, plakken, verplaatsen) en workflows, maar ook van de moderne Universal Editor.

Als dit uw gebruiksgeval is, als onmiddellijke volgende stap, gelieve de volgende documenten voor een volledig overzicht van hoe te om met de Universele Redacteur in AEM op te staan.

1. [Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) - Ga aan de slag met uw eerste Universal Editor-project in AEM
1. [Blokken maken met een instrument voor gebruik met de universele editor](/help/edge/aem-authoring/create-block.md) - Leer hoe u blokken kunt instrumenten om uw inhoud bewerkbaar te maken in de Universal Editor
1. [Inhoud modelleren voor AEM Authoring met Edge Delivery Services Projecten](/help/edge/aem-authoring/content-modeling.md) - Leer de details van hoe de blokken worden gestructureerd om uw inhoud voor gebruik met de Universele Redacteur effectief te modelleren.

Nadat u deze documenten hebt gelezen, kunt u terugkeren naar deze pagina voor meer informatie over het gebruik van koploze ontwerpen en over de algemene werking van de universele editor.

### Headless Authoring {#headless-authoring}

Als u al een app zonder koppen hebt, kunt u de Universal Editor gebruiken om inhoud voor de app te ontwerpen en de inhoud ervan in AEM als inhoudsfragmenten te handhaven. De enige vereiste is dat de app van instrumenten is voorzien om het gebruik van de Universal Editor toe te staan.

Als dit uw gebruikscase is, raadpleegt u het volgende document voor een voorbeeld van een app zonder kop die van instrumenten is voorzien om de Universal Editor te gebruiken.

* [SecurBank Sample App voor de Universal Editor](/help/implementing/universal-editor/securbank.md)

Nadat u dat document hebt gelezen, kunt u terugkeren naar deze pagina voor meer informatie over de AEM die u gebruikt voor het schrijven van programmacode en over de algemene werking van de universele editor.

## De werking van de universele editor {#how-ue-works}

De macht van de Universele Redacteur is zijn capaciteit aan auteur om het even welke inhoud op zijn plaats, die de inhoudsauteur een volledig intuïtieve en verenigde UI verstrekt ongeacht wat de inhoud.

De Universal Editor werkt als volgt.

1. Een ontwikkelaar stuurt de app of pagina om de Universal Editor te gebruiken. Deze instrumentatie vertelt de redacteur welke inhoud editable is en hoe te om het voort te zetten.
   * Voor op AEM gebaseerde ontwerpen worden pagina&#39;s die zijn gemaakt met de sjabloon boilerplate automatisch van instrumenten voorzien.
   * Voor ontwerpen zonder kop kan uw app eenvoudig van instrumenten worden voorzien.
1. De auteur van de inhoud laadt de Universal Editor, die op zijn beurt de pagina voor bewerking laadt. Omdat het van instrumenten wordt voorzien, weet het welke inhoud editable is en hoe het moet worden vertegenwoordigd en voortgeduurd.
1. De auteur van de inhoud bewerkt de pagina-inhoud in een intuïtieve WYSIWYG-interface en bewerkt deze op locatie.
1. De Universal Editor houdt de wijzigingen automatisch opnieuw in op AEM.

Raadpleeg het document als u meer wilt weten over de architectuur van de Universal Editor [Universal Editor Architecture.](/help/implementing/universal-editor/architecture.md)

## Universal Editor Concepts {#concepts}

Een pagina of toepassing kan alleen worden bewerkt met de Universal Editor als deze correct van instrumenten is voorzien. Als u deze functie eenmaal hebt voorzien, kan deze verder worden aangepast aan uw projectbehoeften.

* [Kenmerken en typen](/help/implementing/universal-editor/attributes-types.md) - Een toepassing of pagina kan alleen worden bewerkt met de Universal Editor als deze op de juiste wijze van instrumenten is voorzien. Dit omvat onder andere de juiste metagegevens, zodat de editor de inhoud van de app kan bewerken.
* [Modeldefinities, velden en componenttypen](/help/implementing/universal-editor/field-types.md) - Wanneer de metagegevens aanwezig zijn om het bewerken van een component mogelijk te maken, definieert u welke velden en componenttypen deze kunnen bewerken in de eigenschappentrack van de editor. U doet dit door een model te creëren en met dat van de component te verbinden.
* [De Universal Editor Authoring-ervaring aanpassen](/help/implementing/universal-editor/customizing.md) - Zodra de app of pagina volledig van instrumenten voorzien is, kan de Universal Editor-ervaring verder worden aangepast door de beschikbare componenten te filteren of de functionaliteit van de editor uit te breiden.
* [Universal Editor-gebeurtenissen](/help/implementing/universal-editor/events.md) - U kunt uw app verder aanpassen door te reageren op standaardgebeurtenissen die door de Universal worden verzonden bij wijzigingen in de inhoud en de gebruikersinterface.
