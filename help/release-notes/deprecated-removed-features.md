---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release die specifiek zijn voor vervangen en verwijderde functies in Adobe Experience Manager als Cloud Service.
translation-type: tm+mt
source-git-commit: 0a9a462f1b92a0dcb712163574bbf57582f8145c
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 12%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies. Bovendien, aangezien Adobe Experience Manager als Cloud Service een cloud-native implementatiemodel biedt, zijn bepaalde mogelijkheden en functies vervangen door in de cloud geïntegreerde tegenhangers.

Om de aanstaande verwijdering/vervanging van AEM mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Verouderde mogelijkheden blijven beschikbaar, maar worden niet verder uitgebreid.
1. Capabilities waarvan is aangekondigd dat ze zullen worden afgekeurd, worden ten vroegste in de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Deprecated features {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als afgekeurd in Experience Manager als Cloud Service zijn gemerkt. Typisch, worden de eigenschappen die om in een toekomstige versie worden gepland worden verwijderd geplaatst aan eerst afgekeurd, met een verstrekt alternatief.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken.

| Mogelijkheden | Verouderde functie | Vervanging |
| ------------ | ------------------ | ----------- |
| Assets | `DAM Asset Update` werkwijze voor het verwerken van opgenomen afbeeldingen. | Asset-opname maakt nu gebruik van [asset-microservices](/help/assets/asset-microservices-overview.md) . |
| Assets | Elementen rechtstreeks uploaden naar AEM. Zie API&#39;s voor het uploaden van [afgekeurde elementen](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Gebruik [Direct binair uploaden](/help/assets/add-assets.md). Zie API&#39;s voor [directe upload voor meer informatie](/help/assets/developer-reference-material-apis.md#upload-binary). |
| Assets | [Bepaalde workflowstappen](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) in de `DAM Asset Update` workflow worden niet ondersteund, zoals het aanroepen van opdrachtregelprogramma&#39;s zoals ImageMagick. | [Asset microservices](/help/assets/asset-microservices-overview.md) bieden een vervanging voor veel workflows. Gebruik voor aangepaste verwerking [naverwerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| Assets | MPEG-transcodering van video&#39;s. | Gebruik [Asset microservices](/help/assets/asset-microservices-overview.md)voor het genereren van miniaturen in MPEG. Gebruik [Dynamische media](/help/assets/manage-video-assets.md)voor MPEG-transcodering. |

## Verwijderde functies {#removed-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die uit AEM met Experience Manager als Cloud Service zijn verwijderd.

| Gebied | Functie | Vervanging |
| ------------ | ------------------ | ----------- |
| UI | Terwijl sommige Klassieke dialogen UI voorlopig voor een paar uitgezochte mogelijkheden, zoals de Controleur van de Verbinding, het Leegmaken van de Versie en sommige configuraties van de Cloud Service blijven, is de toegang tot Klassieke UI in het algemeen verwijderd in de AEM productinterface. | Standaardinterface |
|  Dynamic Media  | Previous integrations with [Dynamic Media Classic (Scene7)](https://helpx.adobe.com/nl/experience-manager/6-5/sites/administering/using/scene7.html) and [Dynamic Media Hybrid mode](https://helpx.adobe.com/nl/experience-manager/6-5/assets/using/config-dynamic.html) are not available in AEM as a Cloud Service. | Gebruik [Dynamische media](/help/assets/dynamic-media/dynamic-media.md) die bij Experience Manager worden geleverd als een cloudservice. |
| Sites | Portal Director en Portlet-component | Deze mogelijkheden zijn verouderd in AEM 6.4 en zijn nu verwijderd uit AEM. |
| Sites | Design Importer | Deze mogelijkheid is verwijderd omdat onveranderlijke gedeelten van de AEM niet toegankelijk zijn tijdens runtime. |
| Assets | [AEM Assets delen met Marketing Cloud Assets Core Service en Creative Cloud services](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) is niet beschikbaar. | Voor integratie met Creative Cloud, gebruik de Verbinding van de Activa van [Adobe](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). |
