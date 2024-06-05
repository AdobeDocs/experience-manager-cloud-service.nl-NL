---
title: Hoe multisite beheer voor gerichte inhoud is gestructureerd
description: Een diagram toont hoe multisite steun voor gerichte inhoud gestructureerd is
exl-id: c6b05c2a-0897-4514-8937-e23bfcf757d5
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Hoe multisite beheer voor gerichte inhoud is gestructureerd {#how-multisite-management-for-targeted-content-is-structured}

Het volgende diagram toont hoe multisite steun voor gerichte inhoud gestructureerd is.

Onder de gebieden verschijnen **/content/campagnes/&lt;brand>** en elk merk heeft standaard een hoofdgebied dat automatisch wordt gemaakt. Elk gebied bevat zijn eigen reeks activiteiten, ervaringen en aanbiedingen.

![Multisite structuur](/help/sites-cloud/authoring/assets/multisite-structure.png)

Om gerichte inhoud op te zoeken, kunnen de pagina&#39;s of de plaatsen aan een gebied in kaart brengen. Als er geen gebied is geconfigureerd, AEM terugvalt naar het hoofdgebied voor dit specifieke merk.

Het volgende diagram is een voorbeeld van hoe de logica voor drie plaatsen, genoemd site1, site2, en site3 werkt.

![Multisite structuur over sites](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* site1 zoekt myarea1 op merk1 en other area2 op merk2 op basis van gebiedstoewijzing.
* site2 zoekt myarea1 op voor merk1 en hoofdgebied voor merk2 omdat alleen de gebiedstoewijzing voor merk1 is gedefinieerd.
* site3 zoekt het hoofdgebied voor merk1 en merk2 op omdat er helemaal geen andere gebiedstoewijzing voor deze site is gedefinieerd.
