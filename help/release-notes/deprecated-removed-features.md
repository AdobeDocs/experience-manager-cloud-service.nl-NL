---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release die specifiek betrekking hebben op vervangen en verwijderde functies in Adobe Experience Manager als cloudservice.
translation-type: tm+mt
source-git-commit: b31ae32285080075d2531edd2c4976cf801d1c89

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de productmogelijkheden, zodat oudere functies na verloop van tijd opnieuw kunnen worden uitgevonden of vervangen door modernere alternatieven om de algehele waarde van de klant te verbeteren, waarbij altijd zorgvuldig moet worden gekeken naar compatibiliteit met oudere versies. Aangezien Adobe Experience Manager als Cloud Service een implementatiemodel in de cloud biedt, zijn bovendien bepaalde mogelijkheden en functies vervangen door in de cloud geïntegreerde tegenhangers.

Om de dreigende verwijdering/vervanging van de mogelijkheden van AEM mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Verouderde mogelijkheden blijven beschikbaar, maar worden niet verder uitgebreid.
1. Capabilities waarvan is aangekondigd dat ze zullen worden afgekeurd, worden ten vroegste in de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die in Experience Manager zijn gemarkeerd als een Cloud Service. Typisch, worden de eigenschappen die om in een toekomstige versie worden gepland worden verwijderd geplaatst aan eerst afgekeurd, met een verstrekt alternatief.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken.

| Gebied | Functie | Vervanging |
| ------------ | ------------------ | ----------- |
| Activa | Inname en verwerking van bedrijfsmiddelen maakt niet langer gebruik van `DAM Asset Update` workflow | Asset-opname maakt nu gebruik van [asset-microservices](/help/assets/asset-microservices-overview.md) . |
| Activa | Elementen rechtstreeks uploaden naar AEM - zie API&#39;s voor het uploaden van [afgekeurde elementen](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api) | [Directe binaire upload](/help/assets/add-assets.md) wordt gebruikt in de Manager van de Ervaring als Dienst van de Wolk. Zie API&#39;s voor [directe upload voor meer informatie](/help/assets/developer-reference-material-apis.md#overview-binary-upload). |
| Activa | [Bepaalde workflowstappen](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) in de `DAM Asset Update` workflow worden niet ondersteund, zoals het aanroepen van opdrachtregelprogramma&#39;s zoals ImageMagick | [Asset microservices](/help/assets/asset-microservices-overview.md) bieden een vervanging voor veel workflows. Gebruik voor aangepaste verwerking [naverwerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die uit AEM zijn verwijderd met Experience Manager als Cloud Service.

| Gebied | Functie | Vervanging |
| ------------ | ------------------ | ----------- |
| UI | Terwijl sommige Klassieke dialogen UI voorlopig voor een paar uitgezochte mogelijkheden, zoals de Controleur van de Verbinding, het Leegmaken van de Versie en sommige configuraties van de Dienst van de Wolk blijven, is de toegang tot Klassieke UI in het algemeen verwijderd in het product van AEM UI. | Standaardinterface |
| Dynamische media | Eerdere integraties met de [Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/scene7.html) en de [Dynamic Media Hybrid-modus](https://helpx.adobe.com/experience-manager/6-5/assets/using/config-dynamic.html) zijn niet beschikbaar in AEM als Cloud Service. | Gebruik [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) die met Experience Manager worden geleverd als cloudservice. |
| Sites | Portal Director en Portlet-component | Deze mogelijkheden zijn verouderd in AEM 6.4 en zijn nu verwijderd uit AEM. |
| Sites | Design Importer | Deze mogelijkheid is verwijderd omdat onveranderlijke gedeelten van de AEM-opslagplaats niet toegankelijk zijn tijdens runtime. |
| Activa | [Delen van AEM-middelen via de Marketing Cloud Assets Core Service en Creative Cloud-services](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) is niet beschikbaar. | Voor integratie met Creative Cloud gebruikt u [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). |
