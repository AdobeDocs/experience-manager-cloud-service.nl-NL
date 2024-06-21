---
title: Inhoudsfragmenten - Overwegingen verwijderen
description: Herzie deze belangrijke overwegingen alvorens uw beleid van de schrapping van de Fragmenten van de Inhoud in AEM te bepalen. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de implicaties van het verwijderen ervan moeten zorgvuldig worden overwogen.
feature: Content Fragments
role: User, Developer, Architect
exl-id: d1726bff-3aa8-4758-bee7-0cacea1f660a
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Overwegingen voor inhoudsfragmenten verwijderen {#delete-considerations-content-fragments}

Herzie deze belangrijke overwegingen alvorens uw schrappingsbeleid voor de Fragmenten van de Inhoud in AEM te bepalen. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de implicaties van het verwijderen ervan moeten zorgvuldig worden overwogen.

## Machtigingen - Verwijderen of Niet verwijderen {#permissions-delete-or-not-delete}

De capaciteit om inhoud te schrappen is krachtig, maar potentieel gevoelig, met vele industrieën die moeten beperken en controleren hoe deze voorrechten worden verdeeld.

Met betrekking tot schrappingstoestemmingen, moeten de Fragmenten van de Inhoud op twee niveaus worden overwogen:

1. **Het inhoudsfragment als één entiteit.**

   * **Hoofdletters gebruiken**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken - **en verwijder een volledig fragment**.
   * **Machtigingen**: De machtiging Verwijderen kan worden toegewezen via gebruikers- en/of groepsbeheer.

2. **De meerdere subentiteiten waaruit een inhoudsfragment bestaat, bijvoorbeeld variaties en subknooppunten.**

   Voor de basisbewerking van de editor voor inhoudsfragmenten moeten dergelijke tijdelijke subelementen kunnen worden verwijderd. Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

   * **Hoofdletters gebruiken**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken - **zonder dat een volledig fragment mag worden verwijderd**.
   * **Machtigingen**: Zie [Machtigingen alleen vereist voor Editor-functionaliteit](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Zie ook hoe te de Verrichtingen van het Beheer van de Gebruiker in AEM controleren.

## Machtigingen alleen vereist voor Editor-functionaliteit {#permissions-required-for-editor-functionality-only}

Voor gebruikers die een inhoudsfragment moeten bewerken/bijwerken, **zonder dat ze een volledig fragment mogen verwijderen**, moeten specifieke machtigingen worden toegewezen, aangezien voor de basisbewerking van de Content Fragment-editor is vereist dat tijdelijke subelementen kunnen worden verwijderd.

Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

>[!NOTE]
>
>De machtigingen voor verwijderen die vereist zijn om een inhoudsfragment te bewerken/bij te werken, worden opgenomen in de machtiging Verwijderen die is toegewezen via Gebruiker en/of Groepsbeheer.

De machtigingen die nodig zijn om een fragment te bewerken/bij te werken, moeten worden toegepast op het knooppunt met het inhoudsfragment of op een geschikt bovenliggend knooppunt (op elk niveau onder `/content/dam`). Wanneer de machtigingen aan een dergelijk bovenliggend knooppunt worden toegewezen, worden deze toegepast op alle knooppunten binnen dat vertakking.

Bijvoorbeeld een map waarin alle inhoudsfragmenten staan, zoals:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Machtigingen instellen op `/content/dam` is ook mogelijk, omdat alle inhoudsfragmenten hier worden opgeslagen.
>
>Deze handeling past echter dezelfde verwijdermachtigingen toe op *alles* ook andere soorten activa.

De voorwaarde voor machtigingen om een bepaalde gebruiker en/of groep toe te staan een inhoudsfragment te bewerken/bijwerken is:

>[!NOTE]
>
>In deze lijst worden alle vereiste rechten weergegeven, niet alleen de verwijderingsrechten.

* Voor knooppunten of mappen van inhoudsfragment:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Voor de `jcr:content`knooppunt van alle inhoudsfragmenten:

   * `jcr:addChildNodes`, `jcr:modifyProperties`, en `jcr:removeChildNodes`

* Voor alle onderstaande knooppunten `jcr:content` van alle inhoudsfragmenten:

   * `jcr:addChildNodes`, `jcr:modifyProperties`, en `jcr:removeChildNodes`, `jcr:removeNode`
