---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release die specifiek zijn voor vervangen en verwijderde functies in Adobe Experience Manager als Cloud Service.
translation-type: tm+mt
source-git-commit: e31ac0c2d28f60d7b98036c16f154a09da51d6bf
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 9%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies. Bovendien, aangezien Adobe Experience Manager als Cloud Service een cloud-native implementatiemodel biedt, zijn bepaalde mogelijkheden en functies vervangen door in de cloud geïntegreerde tegenhangers.

Om de aanstaande verwijdering/vervanging van AEM mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Verouderde mogelijkheden blijven beschikbaar, maar worden niet verder uitgebreid.
1. Capabilities waarvan is aangekondigd dat ze zullen worden afgekeurd, worden ten vroegste in de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als afgekeurd in Experience Manager als Cloud Service zijn gemerkt. Typisch, worden de eigenschappen die om in een toekomstige versie worden gepland worden verwijderd geplaatst aan eerst afgekeurd, met een verstrekt alternatief.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken.

| Mogelijkheden | Verouderde functie | Vervanging |
| ------------ | ------------------ | ----------- |
| Assets | `DAM Asset Update` werkwijze voor het verwerken van opgenomen afbeeldingen. | Bij het opnemen van bedrijfsmiddelen worden nu [assetmicroservices](/help/assets/asset-microservices-overview.md) gebruikt. |
| Activa | Elementen rechtstreeks uploaden naar AEM. Zie [API&#39;s voor het uploaden van afgekeurde elementen](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Gebruik [Directe binaire upload](/help/assets/add-assets.md). Voor technische details, zie [directe upload APIs](/help/assets/developer-reference-material-apis.md#upload-binary). |
| Activa | [Bepaalde workflowstepsin-](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps)   `DAM Asset Update` workflowworkflows worden niet ondersteund, zoals het aanroepen van opdrachtregelprogramma&#39;s zoals ImageMagick. | [De ](/help/assets/asset-microservices-overview.md) microservices van bedrijfsmiddelen bieden een vervanging voor veel workflows. Voor aangepaste verwerking gebruikt u [nabewerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| Activa | MPEG-transcodering van video&#39;s. | Gebruik [Asset microservices](/help/assets/asset-microservices-overview.md) voor het genereren van miniaturen in MPEG. Gebruik [Dynamische media](/help/assets/manage-video-assets.md) voor MPEG-transcodering. |

## Verwijderde functies {#removed-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die uit AEM met Experience Manager als Cloud Service zijn verwijderd.

| Gebied | Functie | Vervanging |
| ------------ | ------------------ | ----------- |
| UI | Terwijl sommige Klassieke dialogen UI voorlopig voor een paar uitgezochte mogelijkheden, zoals de Controleur van de Verbinding, het Leegmaken van de Versie en sommige configuraties van de Cloud Service blijven, is de toegang tot Klassieke UI in het algemeen verwijderd in de AEM productinterface. | Standaardinterface |
|  Dynamic Media  | Eerdere integraties met [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) en [Dynamic Media Hybrid mode](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic) zijn niet beschikbaar in AEM als Cloud Service. | Gebruik [Dynamische media](/help/assets/dynamic-media/dynamic-media.md) die bij Experience Manager as a Cloud Service worden geleverd. |
| Sites | Portal Director en Portlet-component | Deze mogelijkheden zijn verouderd in AEM 6.4 en zijn nu verwijderd uit AEM. |
| Sites | Design Importer | Deze mogelijkheid is verwijderd omdat onveranderlijke gedeelten van de AEM niet toegankelijk zijn tijdens runtime. |
| Activa | [AEM Assets delen met Marketing Cloud Assets Core Service en Creative Cloud ](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) services is niet beschikbaar. | Gebruik [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) voor integratie met Creative Cloud. |
