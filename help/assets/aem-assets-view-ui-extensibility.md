---
title: Uitbreidbaarheid gebruikersinterface AEM Assets View
description: Meer informatie over de UI-uitbreidingsmogelijkheden van AEM Assets View. Met de gebruikersinterface van de AEM Assets View kunt u aangepaste UI-componenten toevoegen om aan specifieke bedrijfsbehoeften te voldoen.
feature: App Builder
role: User, Developer
source-git-commit: c1446200898102881a20508031d4853c61f7c964
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Uitbreidbaarheid gebruikersinterface AEM Assets View{#AEM-Assets-View-UI-Extensibility}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

AEM Assets View heeft UI-uitbreidingsmogelijkheden. Met deze functie kunnen gebruikers aangepaste UI-componenten toevoegen aan de gebruikersinterface van de Assets View om tegemoet te komen aan specifieke bedrijfsbehoeften waaraan de functies van de AEM Assets View niet voldoen. Deze uitbreidbaarheidsfunctie verbetert de flexibiliteit van AEM Assets View die organisaties in staat stelt de interface voor specifieke workflows en vereisten aan te passen.
U kunt uw extensies toevoegen aan het niveau voor middelen, mappen en verzamelingen. De toegevoegde extensie wordt weergegeven in een speciaal deelvenster op de pagina Details van element, verzameling of map.

>[!IMPORTANT]
> De Uitbreidbaarheid UI van de Mening van AEM Assets is beschikbaar met [ Assets Ultimate ](/help/assets/assets-ultimate-overview.md).

## <a id="1"></a> Toegang tot Assets View

U kunt de Assets-weergave op de volgende manieren openen:
![ toegang-activa-mening-ui ](/help/assets/assets/access-assets-view.jpg)

## Waar wordt de gebruikersinterface weergegeven van de gebruikersinterface die is toegevoegd voor de gebruikersinterface van de Assets View? {#ui-extensibility-panel-assets-view}

Navigeer in de weergave Assets naar de pagina Details van een element, map of verzameling. Deze pagina Details bevat een speciaal deelvenster waarin de toegevoegde UI-extensie wordt weergegeven.
![ mijn werkruimte ](/help/assets/assets/my-workspace-assets-view3.png)

>[!NOTE]
>
> U hebt de mogelijkheid om de gebruikersinterface van de AEM Assets-weergave uit te breiden als Beta-release. U kunt feedback geven in de documentatie door de opties voor Gedetailleerde feedback uit te vouwen en op Een probleem melden te klikken.

## Vereisten voor het toevoegen van de component Uitbreidbaarheid

* [ Toegang tot de Mening van Assets ](#1).
* Toegang tot [ Adobe app builder ](https://developer.adobe.com/app-builder/docs/overview/), die in [ Assets Ultimate ](/help/assets/assets-ultimate-overview.md) door gebrek inbegrepen is.
* Toelating tot de Ontwikkelaar van de rol van Systeembeheerder binnen de Organisatie. Zie [ dit ](https://developer.adobe.com/uix/docs/guides/get-access/) voor meer informatie.
* Het hulpmiddel van de bevellijn van de Adobe IO (AIO CLI) moet op uw lokale machines worden geïnstalleerd. Dit hulpmiddel is essentieel voor het creëren van en het opstellen van uitbreidingsprojecten. Zie [ dit ](https://developer.adobe.com/app-builder/docs/getting_started/#local-environment-set-up) voor meer informatie.
* Goed inzicht in JavaScript, Node.js, en React technologieën.

## UI-uitbreidingscomponent toevoegen op gebruikersinterface van Assets View{#Adding-UI-Extensibility-Component-on-Assets-View}

1. Zie [ Begonnen het Worden ](https://developer.adobe.com/uix/docs/getting-started/) voor essentiële informatie over Uitbreidingen UI en het kader van Adobe App Builder. Leer hoe de Uitbreidbaarheid UI integratie van douanelogica en UI binnen de diensten van Adobe Experience Cloud toelaat en de architectuur en het werkschema voor het uitvoeren van Uitbreidingen UI begrijpt.
1. Zie [ Gidsen ](https://developer.adobe.com/uix/docs/guides/) voor algemene informatie betreffende Uitbreidbaarheid UI, met inbegrip van lokale milieu opstelling, lokale voorproef, het publiceren, en beheer.
1. Zie [ Gemeenschappelijke Concepten in het Creëren van Uitbreidingen ](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) om de grondbeginselen te begrijpen die worden vereist om een uitbreiding UI voor de Mening van AEM Assets te ontwikkelen.
1. Voeg aangepaste zijpanelen toe aan de interface van de Mening van Assets. De hosttoepassing (Assets View) beheert deze deelvensters om interacties in de gebruikersinterface, zoals schakelen en deep linking, af te handelen. Extensies gebruiken het extensiepunt `aem/assets/details/1` om aangepaste deelvensters te integreren die eigenschappen opgeven, zoals deelvenster-id, titel en inhoud-URL. Ontwikkelaars registreren aangepaste deelvensters met de methode `getPanels()` en bouwen routes om aangepaste inhoud weer te geven. Voor gedetailleerde implementatie, met inbegrip van API verwijzingen en codevoorbeelden, zie [ Mening van Details ](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Stel uw lokale omgeving in en ervaar het proces voor het ontwikkelen van UI-extensies in de Assets-weergave zelf door uw eerste UI-extensie te maken. Zie [ geleidelijke de Ontwikkeling van de Uitbreiding van de Uitbreiding van de Mening van AEM Assets ](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) voor meer details.
1. Stel uw app in met de AIO CLI om de basisextensiestructuur en de vereiste code te genereren. Zie [ de Generatie van de Code voor de Mening van AEM Assets ](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/) voor gedetailleerde informatie.
1. Test uw extensies lokaal om te controleren of ze werken zoals u had verwacht vóór de implementatie. Voer uw extensie uit in een volledig geïsoleerde omgeving of met een gedeeltelijke isolatie en sluit uw extensie aan op de productie-AEM Assets View voor tests. Zie [ het Oplossen van problemen - de Uitbreidbaarheid van de Mening van AEM Assets ](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) voor gedetailleerde informatie.


