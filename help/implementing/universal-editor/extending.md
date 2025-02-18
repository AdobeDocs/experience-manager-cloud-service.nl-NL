---
title: De universele editor uitbreiden
description: Leer over de verschillende opties om de mogelijkheden van Universele Redacteur uit te breiden om de behoeften van uw inhoudsauteurs te steunen.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0cab4a807be4aa402667feddb6a948f0d2db371f
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# De universele editor uitbreiden {#extending}

Leer over de verschillende opties om de mogelijkheden van Universele Redacteur uit te breiden om de behoeften van uw inhoudsauteurs te steunen.

>[!TIP]
>
>De Universele Redacteur biedt ook verscheidene [ aanpassingsopties aan, ](/help/implementing/universal-editor/customizing.md) toestaand u om aan uw projectbehoeften beter te voldoen.

## Extensies {#extensions}

Als Adobe Experience Cloud-service kan de gebruikersinterface van de Universal Editor worden uitgebreid met de App Builder en Experience Manager. Adobe biedt veel kant-en-klare extensies die u voor uw project kunt gebruiken.

* **[de Plukker van het Product van AEM voor Universele Redacteur ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)**: Integreer de gegevens van Adobe Commerce door productgegevens te selecteren of te verwijderen uit de redacteur.
* **[Universele de Inhoudsconcepten van de Redacteur ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: Creeer, geef, en beheer veelvoudige concepten van inhoud uit.
* **[Configureerbare de Plukker van Activa ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)**: laat activaselectie van bewaarplaatsen buiten toe die door de uitgegeven pagina wordt gebruikt.
* **de Redacteur van de Regel van Forms**: Voeg dynamisch gedrag aan de gebieden van AEM Forms visueel toe, zonder codering.
* **[de Fragmenten van de Inhoud van de Uitvoer naar Adobe Target ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)**: De Fragmenten van de Inhoud van de uitvoer, die in Adobe Experience Manager as a Cloud Service aan Adobe Target worden gecreeerd om als aanbiedingen in de activiteiten van het Doel worden gebruikt, om ervaringen bij schaal te testen en te personaliseren.
* **[de Werkschema&#39;s van het Fragment van de Inhoud ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)**: Initieer een werkschema van AEM voor geselecteerde inhoudsfragmenten.

## De gebruikersinterface uitbreiden {#extending-ui}

De UI-extensies van de Universal Editor zijn JavaScript-toepassingen die zijn gemaakt met Adobe App Builder. Met dezelfde gereedschappen kunt u ook uw eigen knoppen en handelingen toevoegen aan het koptekstmenu en het deelvenster Eigenschappen en kunt u uw eigen gebeurtenissen voor de Universal Editor maken.

Zie de volgende bronnen voor informatie over de mogelijkheden om uw eigen extensies te maken:

1. [ Uitbreidbaarheid UI ](https://developer.adobe.com/uix/docs/) - dit is de ontwikkelaardocumentatie voor uitbreiding UI.
1. [ UI de Gidsen van de Rekbaarheid ](https://developer.adobe.com/uix/docs/guides/) - geleidelijke instructies op hoe te om uw eigen uitbreiding te ontwikkelen
1. [ de Universele Punten van de Uitbreiding UI van de Redacteur ](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Universele redacteur-specifieke documentatie van het uitbreidingspunt

>[!TIP]
>
>Als u het leren door voorbeeld verkiest, te zien gelieve het [ de rekbaarheidsleerprogramma van AEM UI ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Hoewel het zich concentreert op het uitbreiden van de console van het Fragment van de Inhoud, zijn de concepten voor het uitvoeren van een uitbreiding UI in de Universele Redacteur het zelfde.

[ Gebruikend Extension Manager in AEM Sites ](https://developer.adobe.com/uix/docs/extension-manager/), kunt u uw uitbreidingen op een per-instantiebasis toelaten of onbruikbaar maken, tot Adobe toegang hebben eerste-partijuitbreidingen met inbegrip van die voor de Universele Redacteur, en veel meer.

## Extensiepunten {#extension-points}

Naast UI-uitbreidbaarheid biedt de Universal Editor vele andere flexibele extensiepunten om een naadloze integratie van aangepaste bedrijfsvereisten mogelijk te maken.

* **[Blokken](/help/edge/developer/block-collection.md)**: In eenvoudig formaat JSON, kunnen de projecten de blokken en de eigenschappen van de UE beschikbaar voor inhoudsverwezenlijking aanpassen.
* **[Aangepast Gebruikersinterface](#extending-ui)**: De uitbreidingen kunnen noodzakelijke UI in zij-panelen of modale dialogen tonen.
* **[Gebeurtenissen](/help/implementing/universal-editor/events.md)**: De uitbreidingen ontvangen gebeurtenissen over de acties en de selecties van de auteur op de pagina om geschikt te antwoorden.
