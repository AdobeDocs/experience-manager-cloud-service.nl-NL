---
title: Sitesjablonen
description: Leer hoe u met AEM-sitesjablonen de sitestructuur en initiële inhoud vooraf definieert, zodat u snel sites kunt maken.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
solution: Experience Manager Sites
source-git-commit: 4d45e7ef626ad0b46f5323263cca791b14f9732f
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# Sitesjablonen {#site-templates}

Leer hoe u met AEM-sitesjablonen de sitestructuur en initiële inhoud vooraf definieert, zodat u snel sites kunt maken.

## Overzicht {#overview}

Het is handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket.

De malplaatjes van de plaats bevatten over het algemeen inhoud en structuur van de basisplaats en plaats het stileren informatie, die als het [&#x200B; plaatsthema wordt bekend, &#x200B;](site-themes.md) om een nieuwe begonnen plaats snel te krijgen. De beheerders selecteren een plaatsmalplaatje waarop om de plaats [&#x200B; tijdens het proces van de plaatsverwezenlijking te baseren.](create-site.md)

Sjablonen zijn krachtig omdat ze opnieuw kunnen worden gebruikt en aanpasbaar zijn. En aangezien u veelvoudige malplaatjes beschikbaar in uw installatie van AEM kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!NOTE]
>
>De plaatssjablonen van AEM zouden niet met [&#x200B; paginasjablonen &#x200B;](/help/sites-cloud/authoring/page-editor/templates.md) moeten worden verward. Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.
>
>De plaatssjablonen van AEM zouden niet met [&#x200B; de plaatsthema&#39;s van AEM moeten worden verward.](site-themes.md) AEM-sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM-site. De plaatsmalplaatjes van AEM bepalen plaatsstructuur en aanvankelijke inhoud, en bevatten een de plaatsthema van AEM om voor [&#x200B; snelle plaatsverwezenlijking toe te staan.](create-site.md)

### Door Adobe verschafte sitesjablonen {#adobe-templates}

{{adobe-templates}}

## Sjabloon site toevoegen aan AEM {#adding}

U kunt veelvoudige malplaatjes aan AEM toevoegen, die dan kunnen worden gebruikt om plaatsen tot stand te brengen [.](create-site.md)

1. Aanmelden bij uw AEM-ontwerpomgeving en naar de Sites-console navigeren

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Selecteer **creeer** bij het hoogste recht van het scherm en van het drop-down menu uitgezocht **Plaats van malplaatje**.

   ![&#x200B; Creërend een plaats van een malplaatje &#x200B;](../assets/create-site-from-template.png)

1. In de Create tovenaar van de Plaats, uitgezochte **Invoer** bij de bovenkant van de linkerkolom.

   ![&#x200B; tovenaar van de creatie van de Plaats &#x200B;](../assets/site-creation-wizard.png)

1. In dossierbrowser, bepaal de plaats van het malplaatje u **gebruiken en wilt selecteren uploadt**.

1. Zodra het geüpload, verschijnt het in de lijst van beschikbare malplaatjes.

Uw malplaatje wordt geupload en kan worden gebruikt om [&#x200B; nieuwe plaatsen tot stand te brengen.](create-site.md)

Als u een bestaande sjabloon selecteert, wordt informatie over de sjabloon in de rechterkolom weergegeven.

![&#x200B; selecteer een malplaatje &#x200B;](../assets/select-site-template.png)

## Sjabloonstructuur van site {#structure}

Sitesjablonen zijn eenvoudig pakketten met een logische structuur die het doel van de pakketinhoud duidelijk weerspiegelt. Een sitesjabloon heeft de volgende structuur.

* `files`: map met de UI-kit, het XD-bestand en mogelijk andere bestanden
* `previews`: map met screenshots van de sitesjabloon
* `site`: Inhoudspakket met de inhoud die wordt gekopieerd voor elke site die met deze sjabloon wordt gemaakt, zoals paginasjablonen, pagina&#39;s enzovoort.
* `theme`: Bronnen van het [&#x200B; plaatsthema &#x200B;](site-themes.md) om te wijzigen hoe de plaats met inbegrip van CSS, JavaScript, etc. kijkt.

## Sitesjablonen ontwikkelen {#developing-templates}

Adobe biedt en AEM Site Template Builder als een set scripts voor het maken van nieuwe sitesjablonen. [&#x200B; de Bouwer van het Malplaatje van de Plaats van AEM is beschikbaar samen met gebruiksdocumentatie op GitHub.](https://github.com/adobe/aem-site-template-builder)
