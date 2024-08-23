---
title: Sitesjablonen
description: Leer hoe AEM sitesjablonen kunnen worden gebruikt om de sitestructuur en de initiële inhoud vooraf te definiëren, zodat u snel sites kunt maken.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
solution: Experience Manager Sites
source-git-commit: 7adfe0ca7fbab1f8a5bd488e524a48be62584966
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# Sitesjablonen {#site-templates}

Leer hoe AEM sitesjablonen kunnen worden gebruikt om de sitestructuur en de initiële inhoud vooraf te definiëren, zodat u snel sites kunt maken.

## Overzicht {#overview}

Het is handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket.

De malplaatjes van de plaats bevatten over het algemeen inhoud en structuur van de basisplaats en plaats het stileren informatie, die als het [ plaatsthema wordt bekend, ](site-themes.md) om een nieuwe begonnen plaats snel te krijgen. De beheerders selecteren een plaatsmalplaatje waarop om de plaats [ tijdens het proces van de plaatsverwezenlijking te baseren.](create-site.md)

Sjablonen zijn krachtig omdat ze opnieuw kunnen worden gebruikt en aanpasbaar zijn. En aangezien u veelvoudige malplaatjes beschikbaar in uw AEM installatie kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!NOTE]
>
>AEM plaatssjablonen zouden niet met [ paginasjablonen ](/help/sites-cloud/authoring/page-editor/templates.md) moeten worden verward. Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.
>
>AEM plaatssjablonen zouden niet met [ AEM plaatsthema&#39;s ](site-themes.md) moeten worden verward. AEM sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM site. AEM plaatssjablonen bepalen plaatsstructuur en aanvankelijke inhoud, en bevatten een AEM plaatsthema om voor [ snelle plaatsverwezenlijking ](create-site.md) toe te staan.

## Een sitesjabloon toevoegen aan AEM {#adding}

U kunt veelvoudige malplaatjes aan AEM toevoegen, die dan kunnen worden gebruikt om plaatsen [ tot stand te brengen ](create-site.md).

1. Onderteken in uw AEM ontwerpomgeving en navigeer naar de Sites-console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Selecteer **creeer** bij het hoogste recht van het scherm en van het drop-down menu uitgezocht **Plaats van malplaatje**.

   ![ Creërend een plaats van een malplaatje ](../assets/create-site-from-template.png)

1. In de Create tovenaar van de Plaats, uitgezochte **Invoer** bij de bovenkant van de linkerkolom.

   ![ tovenaar van de creatie van de Plaats ](../assets/site-creation-wizard.png)

1. In dossierbrowser, bepaal de plaats van het malplaatje u **gebruiken en wilt selecteren uploadt**.

1. Zodra het geüpload, verschijnt het in de lijst van beschikbare malplaatjes.

Uw malplaatje wordt geupload en kan worden gebruikt [ tot nieuwe plaatsen ](create-site.md) leiden.

Als u een bestaande sjabloon selecteert, wordt informatie over de sjabloon in de rechterkolom weergegeven.

![ selecteer een malplaatje ](../assets/select-site-template.png)

## Sjabloonstructuur van site {#structure}

Sitesjablonen zijn eenvoudig pakketten met een logische structuur die het doel van de pakketinhoud duidelijk weerspiegelt. Een sitesjabloon heeft de volgende structuur.

* `files`: Map met de UI-kit, XD bestand en mogelijk andere bestanden
* `previews`: map met screenshots van de sitesjabloon
* `site`: Inhoudspakket met de inhoud die wordt gekopieerd voor elke site die met deze sjabloon wordt gemaakt, zoals paginasjablonen, pagina&#39;s enzovoort.
* `theme`: Bronnen van het [ plaatsthema ](site-themes.md) om te wijzigen hoe de plaats met inbegrip van CSS, JavaScript, etc. kijkt.

## Standaardsitesjabloon {#standard-site-template}

Adobe biedt een referentiesjabloon voor best practices dat u kunt gebruiken als basis voor het maken van uw eigen sjablonen. [ het StandaardMalplaatje van de Plaats is beschikbaar op GitHub.](https://github.com/adobe/aem-site-template-standard)

[ De recentste versie van het StandaardMalplaatje van de Plaats ](https://github.com/adobe/aem-site-template-standard/releases) kan worden gedownload en direct voor [ worden gebruikt creërend nieuwe plaatsen ](create-site.md).

## Sitesjablonen ontwikkelen {#developing-templates}

De Adobe verstrekt en AEM de Bouwer van het Malplaatje van de Plaats als reeks manuscripten voor het creëren van nieuwe plaatsmalplaatjes.

[ de Bouwer van het Malplaatje van de Plaats van de AEM is beschikbaar samen met gebruiksdocumentatie op GitHub ](https://github.com/adobe/aem-site-template-builder). De voorste-eindontwikkelaarervaring wordt vereist voor het aanpassen van het [ plaatsthema ](site-themes.md) en AEM ontwikkelaarskennis wordt vereist voor het aanpassen van de plaatsstructuur en de inhoud.
