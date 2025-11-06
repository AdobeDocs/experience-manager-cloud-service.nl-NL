---
title: Inhoudsfragmenten - Overwegingen verwijderen
description: Bekijk deze belangrijke overwegingen voordat u uw beleid voor het verwijderen van inhoudsfragmenten in AEM definieert. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de implicaties van het verwijderen ervan moeten zorgvuldig worden overwogen.
feature: Content Fragments
role: User, Developer
exl-id: d1726bff-3aa8-4758-bee7-0cacea1f660a
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Overwegingen voor inhoudsfragmenten verwijderen {#delete-considerations-content-fragments}

Bekijk deze belangrijke overwegingen voordat u uw verwijderingsbeleid voor inhoudsfragmenten in AEM definieert. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de implicaties van het verwijderen ervan moeten zorgvuldig worden overwogen.

## Machtigingen - Verwijderen of Niet verwijderen {#permissions-delete-or-not-delete}

De capaciteit om inhoud te schrappen is krachtig, maar potentieel gevoelig, met vele industrieën die moeten beperken en controleren hoe deze voorrechten worden verdeeld.

Met betrekking tot schrappingstoestemmingen, moeten de Fragmenten van de Inhoud op twee niveaus worden overwogen:

1. **het Fragment van de Inhoud als één enkele entiteit.**

   * **Geval van het Gebruik**: Een gebruiker die/een Fragment van de Inhoud moet uitgeven bijwerken - **en een volledig fragment** schrappen.
   * **Toestemmingen**: De toestemming van de Schrapping kan door Gebruiker en/of het Beheer van de Groep worden toegewezen.

2. **de veelvoudige subentities die omhoog een Fragment van de Inhoud maken; bijvoorbeeld, variaties, subnodes.**

   Voor de basisbewerking van de editor voor inhoudsfragmenten moeten dergelijke tijdelijke subelementen kunnen worden verwijderd. Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

   * **Geval van het Gebruik**: Een gebruiker die een Fragment van de Inhoud moet uitgeven/bijwerken - **zonder het worden toegestaan om een volledig fragment** te schrappen.
   * **Toestemmingen**: Zie [ Toestemmingen die voor de Functionaliteit van de Redacteur slechts ](#permissions-required-for-editor-functionality-only) worden vereist.

>[!NOTE]
>
>Zie ook hoe te de Verrichtingen van het Beheer van de Gebruiker in AEM controleren.

## Machtigingen alleen vereist voor Editor-functionaliteit {#permissions-required-for-editor-functionality-only}

Voor gebruikers die een Fragment van de Inhoud uitgeven/moeten bijwerken, **zonder hen toe te staan om een volledig fragment** te schrappen, moeten de specifieke toestemmingen worden toegewezen, aangezien de basisverrichting van de redacteur van het Fragment van de Inhoud vereist dat de voorbijgaande subelementen kunnen worden geschrapt.

Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

>[!NOTE]
>
>De machtigingen voor verwijderen die vereist zijn om een inhoudsfragment te bewerken/bij te werken, worden opgenomen in de machtiging Verwijderen die is toegewezen via Gebruiker en/of Groepsbeheer.

De machtigingen die nodig zijn om een fragment te bewerken/bij te werken, moeten worden toegepast op het knooppunt met het inhoudsfragment of op een geschikt bovenliggend knooppunt (op elk niveau onder `/content/dam`). Wanneer de machtigingen aan een dergelijk bovenliggend knooppunt worden toegewezen, worden deze toegepast op alle knooppunten binnen dat vertakking.

Bijvoorbeeld een map waarin alle inhoudsfragmenten staan, zoals:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Het is ook mogelijk de machtigingen voor `/content/dam` in te stellen, aangezien alle inhoudsfragmenten hier worden opgeslagen.
>
>Nochtans past deze actie de zelfde schrappingstoestemmingen op *alle* andere activa types eveneens toe.

De voorwaarde voor machtigingen om een bepaalde gebruiker en/of groep toe te staan een inhoudsfragment te bewerken/bijwerken is:

>[!NOTE]
>
>In deze lijst worden alle vereiste rechten weergegeven, niet alleen de verwijderingsrechten.

* Voor knooppunten of mappen van inhoudsfragment:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Voor de `jcr:content` knoop van alle Fragmenten van de Inhoud:

   * `jcr:addChildNodes` , `jcr:modifyProperties` en `jcr:removeChildNodes`

* Voor alle knooppunten onder `jcr:content` van alle inhoudsfragmenten:

   * `jcr:addChildNodes` , `jcr:modifyProperties` en `jcr:removeChildNodes` , `jcr:removeNode`
