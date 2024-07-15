---
title: De universele Redacteur gebruikt Gevallen en Lerende Wegen
description: Leer over de belangrijkste gebruiksgevallen van de Universele Redacteur en hoe het best te leren over zijn gebruik en hoe te om het op uw eigen projecten uit te voeren.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
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
>Als u niet reeds hebt, te herzien gelieve de document [ Universele Inleiding van de Redacteur ](/help/implementing/universal-editor/introduction.md) voor een volledig overzicht en waarde van de Universele Redacteur.

## Gevallen gebruiken {#use-cases}

De Universal Editor biedt een handige, intuïtieve visuele editor aan de auteurs van de inhoud, ongeacht het type inhoud dat ze maken. De twee belangrijkste gebruiksgevallen zijn:

* [ WYSIWYG Authoring ](#wysiwyg-authoring) - Gebruik de AEM Sites-console om uw inhoud en auteurspagina&#39;s binnen AEM te beheren met de Universal Editor
* [ Koploze Authoring ](#headless-authoring) - Inhoud van de Auteur in uw eigen toepassing zonder kop gebruikend de Universele Redacteur.

### WYSIWYG Authoring {#wysiwyg-authoring}

Als u al vertrouwd bent met AEM, kunt u de console van Plaatsen gebruiken om uw pagina&#39;s tot stand te brengen en te beheren en hen dan uit te geven met de Universele Redacteur.

Op deze manier kunt u profiteren van de gereedschappen die beschikbaar zijn in de Sites-console, zoals paginabeheer (kopiëren, plakken, verplaatsen) en workflows, maar ook van de moderne Universal Editor.

Als dit uw gebruiksgeval is, als onmiddellijke volgende stap, gelieve de volgende documenten voor een volledig overzicht van hoe te om met de Universele Redacteur in AEM op te staan.

1. [ Begonnen Begeleidende Gids van de Ontwikkelaar voor het schrijven WYSIWYG met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) - krijg begonnen met uw eerste Universele project van de Redacteur in AEM
1. [ Creërend Blokken Instrumented voor gebruik met de Universele Redacteur ](/help/edge/wysiwyg-authoring/create-block.md) - leer hoe te instrumentblokken om uw inhoud in de Universele Redacteur editable te maken
1. [ Inhoud die voor WYSIWYG creeert met de Projecten van Edge Delivery Services ](/help/edge/wysiwyg-authoring/content-modeling.md) - leer de details van hoe de blokken gestructureerd zijn om uw inhoud voor gebruik met de Universele Redacteur effectief te modelleren.

Nadat u deze documenten hebt gelezen, kunt u terugkeren naar deze pagina voor meer informatie over het gebruik van koploze ontwerpen en over de algemene werking van de universele editor.

### Headless Authoring {#headless-authoring}

Als u al een app zonder koppen hebt, kunt u de Universal Editor gebruiken om inhoud voor de app te ontwerpen en de inhoud ervan in AEM als inhoudsfragmenten te handhaven. De enige vereiste is dat de app van instrumenten is voorzien om het gebruik van de Universal Editor toe te staan.

Als dit uw gebruikscase is, raadpleegt u het volgende document voor een voorbeeld van een app zonder kop die van instrumenten is voorzien om de Universal Editor te gebruiken.

* [SecurBank Sample App voor de Universal Editor](/help/implementing/universal-editor/securbank.md)

Nadat u dat document hebt gelezen, kunt u terugkeren naar deze pagina voor meer informatie over de WYSIWYG-authoringuse case en over de algemene werking van de Universal Editor.

## De werking van de universele editor {#how-ue-works}

De macht van de Universele Redacteur is zijn capaciteit aan auteur om het even welke inhoud op zijn plaats, die de inhoudsauteur een volledig intuïtieve en verenigde UI verstrekt ongeacht wat de inhoud.

De Universal Editor werkt als volgt.

1. Een ontwikkelaar stuurt de app of pagina om de Universal Editor te gebruiken. Deze instrumentatie vertelt de redacteur welke inhoud editable is en hoe te om het voort te zetten.
   * Voor WYSIWYG-authoring worden pagina&#39;s die zijn gemaakt met de sjabloon boilerplate automatisch van instrumenten voorzien.
   * Voor ontwerpen zonder kop kan uw app eenvoudig van instrumenten worden voorzien.
1. De auteur van de inhoud laadt de Universal Editor, die op zijn beurt de pagina voor bewerking laadt. Omdat het van instrumenten wordt voorzien, weet het welke inhoud editable is en hoe het moet worden vertegenwoordigd en voortgeduurd.
1. De auteur van de inhoud bewerkt de pagina-inhoud in een intuïtieve WYSIWYG-interface en bewerkt deze op locatie.
1. De Universal Editor houdt de wijzigingen automatisch opnieuw in op AEM.

Als u meer over de architectuur van de Universele Redacteur zou willen leren, gelieve de document [ Universele Architectuur van de Redacteur te zien.](/help/implementing/universal-editor/architecture.md)

## Universal Editor Concepts {#concepts}

Een pagina of toepassing kan alleen worden bewerkt met de Universal Editor als deze correct van instrumenten is voorzien. Als u deze functie eenmaal hebt voorzien, kan deze verder worden aangepast aan uw projectbehoeften.

* [ Attributen en Types ](/help/implementing/universal-editor/attributes-types.md) - opdat een app of een pagina door de Universele Redacteur editable zijn, moet het behoorlijk van instrumenten voorzien zijn. Dit omvat onder andere de juiste metagegevens, zodat de editor de inhoud van de app kan bewerken.
* [ Modeldefinities, Gebieden, en de Types van Component ](/help/implementing/universal-editor/field-types.md) - Zodra de meta-gegevens aanwezig zijn om het uitgeven van een component toe te laten, bepaalt u welke gebieden en componententypes zij in de eigenschappen spoorstaaf van de redacteur kunnen manipuleren. U doet dit door een model te creëren en met dat van de component te verbinden.
* [ die de Universele Ervaring van de Authoring van de Redacteur ](/help/implementing/universal-editor/customizing.md) aanpassen - Zodra app of de pagina volledig-van instrumenten wordt voorzien, kan de Universele ervaring van de Redacteur verder worden aangepast door de beschikbare componenten te filtreren, of de functionaliteit van de redacteur uit te breiden.
* [ Universele Gebeurtenissen van de Redacteur ](/help/implementing/universal-editor/events.md) - u kunt uw app verder aanpassen door op standaardgebeurtenissen te antwoorden die de Universele verzendt op veranderingen in de inhoud en UI.
