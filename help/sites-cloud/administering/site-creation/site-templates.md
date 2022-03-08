---
title: Sitesjablonen
description: Leer hoe AEM sitesjablonen kunnen worden gebruikt om de sitestructuur en de initiële inhoud vooraf te definiëren, zodat u snel sites kunt maken.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# Sitesjablonen {#site-templates}

Leer hoe AEM sitesjablonen kunnen worden gebruikt om de sitestructuur en de initiële inhoud vooraf te definiëren, zodat u snel sites kunt maken.

## Overzicht {#overview}

Het is handig om vooraf gedefinieerde structuren beschikbaar te hebben om snel een nieuwe site te implementeren op basis van een set bestaande standaarden. Sitesjablonen zijn een manier om basissite-inhoud te combineren tot een handig en herbruikbaar pakket.

Sitesjablonen bevatten over het algemeen inhoud en structuur van de basissite en informatie over de sitestijl, ook wel de [site-thema;](site-themes.md) om snel een nieuwe site te starten. Beheerders selecteren een sitesjabloon waarop ze de site willen baseren [tijdens het maken van de site.](create-site.md)

Sjablonen zijn krachtig omdat ze herbruikbaar en aanpasbaar zijn. En aangezien u veelvoudige malplaatjes beschikbaar in uw AEM installatie kunt hebben, hebt u de flexibiliteit om verschillende plaatsen tot stand te brengen om aan diverse bedrijfsbehoeften te voldoen.

>[!NOTE]
>
>AEM sitesjablonen mogen niet worden verward met [paginasjablonen.](/help/sites-cloud/authoring/features/templates.md) Sitesjablonen definiëren de algehele structuur van een site. Een paginasjabloon definieert de structuur en initiële inhoud van een afzonderlijke pagina.
>
>AEM sitesjablonen mogen niet worden verward met [AEM sitethema&#39;s.](site-themes.md) AEM sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM site. Met AEM sitesjablonen kunt u de sitestructuur en de initiële inhoud definiëren en een AEM sitethema bevatten om het mogelijk te maken [snel websites maken.](create-site.md)

## Een sitesjabloon toevoegen aan AEM {#adding}

U kunt meerdere sjablonen toevoegen aan AEM, die u vervolgens kunt gebruiken om [sites maken.](create-site.md)

1. Onderteken in uw AEM ontwerpomgeving en navigeer naar de Sites-console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tik of klik op **Maken** rechtsboven in het scherm en in het keuzemenu selecteert u **Site van sjabloon**.

   ![Een site maken op basis van een sjabloon](../assets/create-site-from-template.png)

1. Tik of klik in de wizard Site maken op **Importeren** boven aan de linkerkolom.

   ![Wizard Site maken](../assets/site-creation-wizard.png)

1. Zoek in de bestandsbrowser de sjabloon die u wilt gebruiken en tik of klik op **Uploaden**.

1. Nadat de sjabloon is geüpload, wordt deze weergegeven in de lijst met beschikbare sjablonen.

Uw sjabloon is geüpload en kan worden gebruikt om [nieuwe sites maken.](create-site.md)

Als u een bestaande sjabloon selecteert, wordt informatie over de sjabloon in de rechterkolom weergegeven.

![Een sjabloon selecteren](../assets/select-site-template.png)

## Sjabloonstructuur van site {#structure}

Sitesjablonen zijn eenvoudig pakketten met een logische structuur die het doel van de pakketinhoud duidelijk weerspiegelt. Een sitesjabloon heeft de volgende structuur.

* `files`: Map met de UI-kit, XD bestand en mogelijk andere bestanden
* `previews`: Map met screenshots van de sitesjabloon
* `site`: Inhoudspakket van de inhoud die wordt gekopieerd voor elke site die met deze sjabloon wordt gemaakt, zoals paginasjablonen, pagina&#39;s, enzovoort.
* `theme`: Bronnen van de [site-thema](site-themes.md) om de weergave van de site te wijzigen, zoals CSS, JavaScript, enz.

## Standaardsitesjabloon {#standard-site-template}

Adobe biedt een referentiesjabloon voor best practices dat u kunt gebruiken als basis voor het maken van uw eigen sjablonen. [Het StandaardMalplaatje van de Plaats is beschikbaar op GitHub.](https://github.com/adobe/aem-site-template-standard)

[De meest recente versie van de standaardsitesjabloon](https://github.com/adobe/aem-site-template-standard/releases) kan worden gedownload en rechtstreeks worden gebruikt voor [nieuwe sites maken.](create-site.md)

## Sitesjablonen ontwikkelen {#developing-templates}

Adobe verstrekt en AEM de Bouwer van het Malplaatje van de Plaats als reeks manuscripten voor het creëren van nieuwe plaatssjablonen.

[De AEM Bouwer van het Malplaatje van de Plaats is beschikbaar samen met gebruiksdocumentatie op GitHub.](https://github.com/adobe/aem-site-template-builder) Voor het aanpassen van de [site-thema](site-themes.md) en AEM kennis van ontwikkelaars is vereist voor het aanpassen van de sitestructuur en -inhoud.
