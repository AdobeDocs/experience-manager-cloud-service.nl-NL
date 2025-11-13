---
title: De universele editor uitbreiden
description: Leer over de verschillende opties om de mogelijkheden van Universele Redacteur uit te breiden om de behoeften van uw inhoudsauteurs te steunen.
feature: Developing
role: Admin, Developer
exl-id: 2f487fa5-57a7-477a-ad68-590e6cc12f4e
source-git-commit: d938abce2b46786343b19113454da1738a824ed0
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# De universele editor uitbreiden {#extending}

Leer over de verschillende opties om de mogelijkheden van Universele Redacteur uit te breiden om de behoeften van uw inhoudsauteurs te steunen.

>[!TIP]
>
>De Universele Redacteur biedt ook verscheidene [&#x200B; aanpassingsopties aan, &#x200B;](/help/implementing/universal-editor/customizing.md) toestaand u om aan uw projectbehoeften beter te voldoen.

## Extensies {#extensions}

Als Adobe Experience Cloud-service kan de gebruikersinterface van de Universal Editor worden uitgebreid met de App Builder en Experience Manager. Adobe biedt vele kant-en-klare uitbreidingen beschikbaar door [&#x200B; Extension Manager &#x200B;](https://experience.adobe.com/aem/extension-manager) aan die u voor uw project kunt gebruiken.

* **[de multi-plaats-Beheer van AEM (MSM) Uitbreiding](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)**: Breek of herstelt overerving op het componentenniveau
* **[Uitbreiding van de Eigenschappen van de Pagina van AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties)**: Heb toegang tot het pagina tot eigenschappen venster van de pagina in de Universele Redacteur
* **[Uitbreiding van Admin van de Plaats van AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#sites-console)**: Open de Console van Plaatsen aan de plaats van de pagina in de Universele Redacteur
* **[Uitbreiding van het Slot van de Pagina van AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#locking-pages)**: Bekijk en verander de status van het paginaslot van de Universele Redacteur
* **[de Uitbreiding van de Werkschema&#39;s van AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#workflows)**: De werkschema&#39;s van het begin op de pagina en paginainhoud van de Universele Redacteur
* **[produceer Variaties](/help/generative-ai/generate-variations-integrated-editor.md)**: De generatieve kunstmatige intelligentie van het gebruik (AI) om variaties voor uw inhoud direct in het eigenschappenpaneel tot stand te brengen.
* **[de Plukker van het Product van AEM voor Universele Redacteur &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)**: Integreer de gegevens van Adobe Commerce door productgegevens te selecteren of te verwijderen uit de redacteur.
* **[Universele de Inhoudsconcepten van de Redacteur &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: Creeer, geef, en beheer veelvoudige concepten van inhoud uit.
* **[Configureerbare de Plukker van Activa &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)**: laat activaselectie van bewaarplaatsen buiten toe die door de uitgegeven pagina wordt gebruikt.
* **de Redacteur van de Regel van Forms**: Voeg dynamisch gedrag aan de gebieden van AEM Forms visueel toe, zonder codering.
* **[de Fragmenten van de Inhoud van de Uitvoer naar Adobe Target &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)**: De Fragmenten van de Inhoud van de uitvoer, die in Adobe Experience Manager as a Cloud Service aan Adobe Target worden gecreeerd om als aanbiedingen in de activiteiten van het Doel worden gebruikt, om ervaringen bij schaal te testen en te personaliseren.
* **[de Werkschema&#39;s van het Fragment van de Inhoud &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)**: Initieer een werkschema van AEM voor geselecteerde inhoudsfragmenten.

Voor informatie over hoe te om deze uitbreidingen toe te laten, [&#x200B; te zien gelieve de documentatie van Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## De gebruikersinterface uitbreiden {#extending-ui}

De UI-extensies van de Universal Editor zijn JavaScript-toepassingen die zijn gemaakt met Adobe App Builder. Met dezelfde gereedschappen kunt u ook uw eigen knoppen en handelingen toevoegen aan het koptekstmenu en het deelvenster Eigenschappen en kunt u uw eigen gebeurtenissen voor de Universal Editor maken.

Zie de volgende bronnen voor informatie over de mogelijkheden om uw eigen extensies te maken:

1. [&#x200B; Uitbreidbaarheid UI &#x200B;](https://developer.adobe.com/uix/docs/) - dit is de ontwikkelaardocumentatie voor uitbreiding UI.
1. [&#x200B; UI de Gidsen van de Rekbaarheid &#x200B;](https://developer.adobe.com/uix/docs/guides/) - geleidelijke instructies op hoe te om uw eigen uitbreiding te ontwikkelen
1. [&#x200B; de Universele Punten van de Uitbreiding UI van de Redacteur &#x200B;](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Universele redacteur-specifieke documentatie van het uitbreidingspunt

>[!TIP]
>
>Als u het leren door voorbeeld verkiest, te zien gelieve het [&#x200B; de rekbaarheidsleerprogramma van AEM UI &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Hoewel het zich concentreert op het uitbreiden van de console van het Fragment van de Inhoud, zijn de concepten voor het uitvoeren van een uitbreiding UI in de Universele Redacteur het zelfde.

[&#x200B; Gebruikend Extension Manager in AEM Sites &#x200B;](https://developer.adobe.com/uix/docs/extension-manager/), kunt u uw uitbreidingen op een per-instantiebasis toelaten of onbruikbaar maken, tot Adobe toegang hebben eerste-partijuitbreidingen met inbegrip van die voor de Universele Redacteur, en veel meer.

## Extensiepunten {#extension-points}

Naast UI-uitbreidbaarheid biedt de Universal Editor vele andere flexibele extensiepunten om een naadloze integratie van aangepaste bedrijfsvereisten mogelijk te maken.

* **[Blokken &#x200B;](https://www.aem.live/developer/block-collection)**: In eenvoudig formaat JSON, kunnen de projecten de blokken en de eigenschappen van de UE beschikbaar voor inhoudsverwezenlijking aanpassen.
* **[Aangepast Gebruikersinterface](#extending-ui)**: De uitbreidingen kunnen noodzakelijke UI in zij-panelen of modale dialogen tonen.
* **[Gebeurtenissen](/help/implementing/universal-editor/events.md)**: De uitbreidingen ontvangen gebeurtenissen over de acties en de selecties van de auteur op de pagina om geschikt te antwoorden.
