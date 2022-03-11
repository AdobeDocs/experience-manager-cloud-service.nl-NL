---
title: Structurering van beheer voor meerdere sites voor getargete content
description: Een diagram toont hoe multisite steun voor gerichte inhoud gestructureerd is
exl-id: c6b05c2a-0897-4514-8937-e23bfcf757d5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 8%

---

# Structurering van beheer voor meerdere sites voor getargete content {#how-multisite-management-for-targeted-content-is-structured}

Het volgende diagram toont hoe multisite steun voor gerichte inhoud gestructureerd is.

Onder de gebieden verschijnen **/content/campagnes/&lt;brand>** elk merk heeft standaard een master gebied dat automatisch wordt gemaakt . Elk gebied bevat zijn eigen reeks activiteiten, ervaringen en aanbiedingen.

![Multisite structuur](/help/sites-cloud/authoring/assets/multisite-structure.png)

Om gerichte inhoud op te zoeken, kunnen de pagina&#39;s of de plaatsen aan een gebied in kaart brengen. Als er geen gebied gevormd is, AEM valt terug naar het master gebied voor dit specifieke merk.

Het volgende diagram is een voorbeeld van hoe de logica voor drie plaatsen, genoemd site1, site2, en site3 werkt.

![Multisite structuur over sites](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* site1 zoekt myarea1 op merk1 en other area2 op merk2 op basis van gebiedstoewijzing.
* site2 zoekt myarea1 op voor merk1 en master gebied voor merk2 omdat alleen de gebiedstoewijzing voor merk1 is gedefinieerd.
* site3 zoekt het master gebied voor merk1 en merk2 op omdat er helemaal geen andere gebiedstoewijzing voor deze site is gedefinieerd.
