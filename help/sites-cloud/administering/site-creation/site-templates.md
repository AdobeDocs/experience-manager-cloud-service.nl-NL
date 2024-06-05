---
title: Sitesjablonen
description: Leer hoe AEM sitesjablonen kunnen worden gebruikt om de sitestructuur en de initiële inhoud vooraf te definiëren, zodat u snel sites kunt maken.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# Sitesjablonen {#site-templates}

Leer hoe AEM sitesjablonen kunnen worden gebruikt om de sitestructuur en de initiële inhoud vooraf te definiëren, zodat u snel sites kunt maken.

## Overzicht {#overview}

Het is handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket.

Sitesjablonen bevatten over het algemeen inhoud en structuur van de basissite en informatie over de siteopmaak, die bekend staat als de [site-thema;](site-themes.md) om snel aan de slag te gaan met een nieuwe site. Beheerders selecteren een sitesjabloon waarop ze de site willen baseren [tijdens het maken van de site.](create-site.md)

Sjablonen zijn krachtig omdat ze opnieuw kunnen worden gebruikt en aanpasbaar zijn. En aangezien u veelvoudige malplaatjes beschikbaar in uw AEM installatie kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!NOTE]
>
>AEM sitesjablonen mogen niet worden verward met [paginasjablonen](/help/sites-cloud/authoring/sites-console/templates.md). Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.
>
>AEM sitesjablonen mogen niet worden verward met [Sitethema&#39;s AEM](site-themes.md). AEM sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM site. Met AEM sitesjablonen definieert u de sitestructuur en de initiële inhoud. Sjablonen bevatten een AEM sitethema dat het mogelijk maakt [snel site maken](create-site.md).

## Een sitesjabloon toevoegen aan AEM {#adding}

U kunt meerdere sjablonen toevoegen aan AEM, die u vervolgens kunt gebruiken om [sites maken](create-site.md).

1. Onderteken in uw AEM ontwerpomgeving en navigeer naar de Sites-console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Selecteren **Maken** rechtsboven in het scherm en in het keuzemenu selecteert u **Site van sjabloon**.

   ![Een site maken op basis van een sjabloon](../assets/create-site-from-template.png)

1. Selecteer in de wizard Site maken de optie **Importeren** boven aan de linkerkolom.

   ![Wizard Site maken](../assets/site-creation-wizard.png)

1. Zoek in de bestandenbrowser de sjabloon die u wilt gebruiken en selecteer **Uploaden**.

1. Zodra het geüpload, verschijnt het in de lijst van beschikbare malplaatjes.

Uw sjabloon is geüpload en kan worden gebruikt om [nieuwe sites maken](create-site.md).

Als u een bestaande sjabloon selecteert, wordt informatie over de sjabloon in de rechterkolom weergegeven.

![Een sjabloon selecteren](../assets/select-site-template.png)

## Sjabloonstructuur van site {#structure}

Sitesjablonen zijn eenvoudig pakketten met een logische structuur die het doel van de pakketinhoud duidelijk weerspiegelt. Een sitesjabloon heeft de volgende structuur.

* `files`: Map met de UI-kit, XD bestand en mogelijk andere bestanden
* `previews`: Map met screenshots van de sitesjabloon
* `site`: Inhoudspakket van de inhoud die wordt gekopieerd voor elke site die met deze sjabloon wordt gemaakt, zoals paginasjablonen, pagina&#39;s enzovoort.
* `theme`: Bronnen van de [site-thema](site-themes.md) om de weergave van de site te wijzigen, zoals CSS, JavaScript, enzovoort.

## Standaardsitesjabloon {#standard-site-template}

Adobe biedt een referentiesjabloon voor best practices dat u kunt gebruiken als basis voor het maken van uw eigen sjablonen. [Het StandaardMalplaatje van de Plaats is beschikbaar op GitHub.](https://github.com/adobe/aem-site-template-standard)

[De meest recente versie van de standaardsitesjabloon](https://github.com/adobe/aem-site-template-standard/releases) kan worden gedownload en rechtstreeks worden gebruikt voor [nieuwe sites maken](create-site.md).

## Sitesjablonen ontwikkelen {#developing-templates}

De Adobe verstrekt en AEM de Bouwer van het Malplaatje van de Plaats als reeks manuscripten voor het creëren van nieuwe plaatsmalplaatjes.

[De Bouwer van het Malplaatje van de Plaats van de AEM is beschikbaar samen met gebruiksdocumentatie op GitHub](https://github.com/adobe/aem-site-template-builder). Voor het aanpassen van de [site-thema](site-themes.md) en AEM kennis van ontwikkelaars is vereist voor het aanpassen van de sitestructuur en -inhoud.
