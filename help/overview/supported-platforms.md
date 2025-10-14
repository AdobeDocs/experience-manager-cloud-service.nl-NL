---
title: Ondersteunde clientplatforms
description: Leer welke browsers worden ondersteund voor het ontwerpen van inhoud met Adobe Experience Manager as a Cloud Service en het openen van sites die met AEM worden gepubliceerd.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 7ddd0a75-621a-4499-91d1-7b3408a68269
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Ondersteunde clientplatforms {#supported-platforms}

Leer welke browsers worden ondersteund voor het ontwerpen van inhoud met Adobe Experience Manager as a Cloud Service en het openen van sites die met AEM worden gepubliceerd.

>[!TIP]
>
>Dit document is van toepassing op clientplatforms die door AEM as a Cloud Service worden ondersteund. Voor details op het bouwstijlmilieu voor het ontwikkelen van uw project van AEM, te zien gelieve het document [&#x200B; Milieu bouwen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)

## Ondersteuningsniveaus {#support-levels}

Adobe definieert de volgende ondersteuningsniveaus voor AEM-clientplatforms.

| Ondersteuningsniveau | Beschrijving |
|---|---|
| A: Ondersteund | Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie. Deze configuratie valt onder het kwaliteitsborgingsproces van Adobe. |
| R: Beperkte ondersteuning | De steun vereist een formeel verzoek aan Adobe om de configuratie in een project te gebruiken. Zodra Adobe door Adobe is bevestigd, verleent het volledige steun binnen het beperkte steunprogramma. Neem voor meer informatie contact op met de klantenservice van Adobe. |
| Z: Niet ondersteund | De configuratie wordt niet ondersteund. Adobe legt geen verklaringen over of de configuratie werkt, en steunt het niet. |

## Ondersteunde browsers voor ontwerpen van inhoud {#authoring}

De AEM-gebruikersinterface is geoptimaliseerd voor grotere schermen in laptops, desktopcomputers en tablets (zoals Apple iPad of Microsoft Surface). De telefoonvormfactor wordt niet gesteund voor om het even welk auteursgeval.

Het gebruikersinterface van Adobe Experience Manager werkt met de volgende cliëntplatforms afhankelijk van [&#x200B; auteursmethode.](/help/edge/overview.md#authoring-method)

* [Universele editor](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [Pagina-editor](/help/sites-cloud/authoring/page-editor/introduction.md)
* [&#x200B; op document-Gebaseerde creatie &#x200B;](https://www.aem.live/docs/aem-authoring) gebruikend [&#x200B; Sidekick &#x200B;](https://www.aem.live/docs/sidekick)

Alle browsers worden getest met de standaardset plug-ins en invoegtoepassingen.

| Browser | Ondersteuning voor Universal Editor | Ondersteuningsniveau pagina-editor | Sidekick-ondersteuningsniveau |
|---|---|---|---|
| Google Chrome (groen) | A: Ondersteund | A: Ondersteund | A: Ondersteund |
| Microsoft Edge (groen) | A: Ondersteund | A: Ondersteund | Z: Niet ondersteund |
| Mozilla Firefox (evergroen) | A: Ondersteund | A: Ondersteund | Z: Niet ondersteund |
| Mozilla Firefox recentste ESR [ 1 ] | A: Ondersteund | A: Ondersteund | Z: Niet ondersteund |
| Safari op macOS (evergreen) | A: Ondersteund | A: Ondersteund | Z: Niet ondersteund |
| Safari op iPadOS (groen) | Z: Niet ondersteund | A: Ondersteund | Z: Niet ondersteund |

1. Uitgebreide Versie van de Steun van Firefox ([&#x200B; leert meer op mozilla.org &#x200B;](https://www.mozilla.org/en-US/firefox/enterprise/))

>[!NOTE]
>
>**Steun voor browsers met snelle versiecycli:**
>
>De release van Firefox, Chrome en Edge wordt regelmatig bijgewerkt. Adobe streeft ernaar het supportniveau dat hierboven voor toekomstige versies van deze browsers wordt vermeld, te handhaven.

## Ondersteunde browsers voor websites {#websites}

Browserondersteuning voor websites die door AEM worden weergegeven, is afhankelijk van de implementatie van AEM-paginasjablonen, -blokken, -ontwerpen en -componentuitvoer. Daarom hebben uw ontwikkelaars die uw project implementeren uiteindelijk controle over de compatibiliteit van uw site.

AEM [&#x200B; projectbouwsteen, &#x200B;](https://www.aem.live/developer/ue-tutorial#create-github-project) [&#x200B; Componenten van de Kern, &#x200B;](/help/implementing/developing/components/overview.md#aem-core-components) en [&#x200B; WKND steekproefplaats &#x200B;](/help/implementing/developing/introduction/develop-wknd-tutorial.md) zijn allen compatibel met alle moderne browsers.
