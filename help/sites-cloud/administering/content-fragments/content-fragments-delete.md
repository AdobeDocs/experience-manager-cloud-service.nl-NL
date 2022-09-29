---
title: Contentfragmenten - Overwegingen verwijderen
description: Herzie deze belangrijke overwegingen alvorens uw beleid van de schrapping van de Fragmenten van de Inhoud in AEM te bepalen. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de gevolgen van het verwijderen ervan moeten zorgvuldig worden overwogen.
feature: Content Fragments
role: User
exl-id: f6698dd8-3e2a-44ac-b00f-df578aa85ffe
source-git-commit: 944665bc7cac1f00811187a508a18800c3d73f2a
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 9%

---

# Contentfragmenten - Overwegingen verwijderen {#content-fragments-delete-considerations}

Herzie deze belangrijke overwegingen alvorens uw beleid van de schrapping van de Fragmenten van de Inhoud in AEM te bepalen. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de gevolgen van het verwijderen ervan moeten zorgvuldig worden overwogen.

## Machtigingen - Verwijderen of Niet verwijderen {#permissions-delete-or-not-delete}

De capaciteit om inhoud te schrappen is krachtig, maar potentieel gevoelig, met vele industrieën die moeten beperken en controleren hoe deze voorrechten worden verdeeld.

Met betrekking tot schrappingstoestemmingen, moeten de Fragmenten van de Inhoud op twee niveaus worden overwogen:

1. **Het inhoudsfragment als één entiteit.**

   * **Hoofdletters gebruiken**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken - **en verwijder een volledig fragment**.
   * **Machtigingen**: De machtiging Verwijderen kan worden toegewezen via gebruikers- en/of groepsbeheer. <!-- The [Delete](/help/sites-administering/security.md#actions) permission can be [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). -->

2. **De meerdere subentiteiten waaruit een inhoudsfragment bestaat; bijvoorbeeld variaties, subknooppunten.**

   De basiswerking van de inhoudfragment-editor vereist dat dergelijke tijdelijke subelementen kunnen worden verwijderd. Bijvoorbeeld bij het manipuleren van variaties; ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

   * **Hoofdletters gebruiken**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken - **zonder dat het is toegestaan een volledig fragment te verwijderen**.
   * **Machtigingen**: Zie [Machtigingen alleen vereist voor Editor-functionaliteit](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Wanneer een gebruiker geen machtiging Verwijderen heeft, wordt de editor voor inhoudsfragmenten uitgevoerd in *alleen-lezen* in. <!-- When a user does not have any [Delete](/help/sites-administering/security.md#actions) permissions, the Content Fragment editor operates in *read-only* mode. -->

>[!NOTE]
>
>Zie ook hoe te de Verrichtingen van het Beheer van de Gebruiker in AEM controleren. <!-- See also [How to Audit User Management Operations in AEM](/help/sites-administering/audit-user-management-operations.md). -->

## Machtigingen alleen vereist voor Editor-functionaliteit {#permissions-required-for-editor-functionality-only}

Voor gebruikers die een contentfragment moeten bewerken of bijwerken, **zonder hun toe te staan om een volledig fragment te verwijderen**, moeten specifieke machtigingen worden toegewezen, aangezien de basisbewerking van de contentfragmenteditor vereist dat tijdelijke subelementen kunnen worden verwijderd.

Bijvoorbeeld bij het manipuleren van variaties; ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

>[!NOTE]
>
>De machtigingen voor verwijderen die vereist zijn om een inhoudsfragment te bewerken/bij te werken, worden opgenomen in de machtiging Verwijderen die is toegewezen via Gebruiker en/of Groepsbeheer. <!-- The delete permissions, required to edit/update a Content Fragment, are included in the Delete permission [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). -->

De machtigingen die nodig zijn om een fragment te bewerken/bij te werken, moeten worden toegepast op het knooppunt met het inhoudsfragment of op een geschikt bovenliggend knooppunt (op elk niveau onder `/content/dam`). Wanneer toegewezen aan een dergelijk bovenliggend knooppunt, worden de machtigingen toegepast op alle knooppunten in die vertakking.

Bijvoorbeeld een map die alle inhoudsfragmenten bevat, zoals:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Machtigingen instellen op `/content/dam` is ook mogelijk, omdat alle inhoudsfragmenten hier worden opgeslagen.
>
>Deze handeling past echter dezelfde verwijdermachtigingen toe op *alles* ook andere soorten activa.

U kunt een inhoudsfragment alleen bewerken/bijwerken als een specifieke gebruiker en/of groep de volgende machtigingen heeft:

>[!NOTE]
>
>In deze lijst worden alle vereiste rechten weergegeven, niet alleen de verwijderingsrechten.

* Voor de knooppunten of mappen van het inhoudsfragment:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Voor de `jcr:content`knooppunt van alle inhoudsfragmenten:

   * `jcr:addChildNodes`, `jcr:modifyProperties` en `jcr:removeChildNodes`

* Voor alle onderstaande knooppunten `jcr:content` van alle inhoudsfragmenten:

   * `jcr:addChildNodes`, `jcr:modifyProperties` en `jcr:removeChildNodes`, `jcr:removeNode`

<!-- There is no CRXDE Lite -->

<!--
These `remove` privileges must be [administered using Access Control Lists, within CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management). 

The `add` and `modify` privileges can also be administered in CRXDE Lite, or using the User Management console.

For example, the definition of the `remove` privileges for a group `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
-->
