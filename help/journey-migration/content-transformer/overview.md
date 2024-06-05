---
title: Overzicht tot Inhoud transformeren
description: Leer hoe u aan inhoud gerelateerde problemen kunt detecteren en verhelpen die door de BPA zijn gemeld met Content Transformer.
exl-id: aa3397ff-3dd6-4c67-9064-cb9b19bf1c73
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Overzicht {#overview-ct}

De Content Transformer (CT) is een hulpmiddel dat door de Adobe is ontwikkeld en dat kan worden gebruikt om problemen met betrekking tot inhoud die door de [Best Practices Analyzer (BPA)](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) voordat u inhoud migreert van uw huidige AEM-implementatie (On-premise of Managed Services) naar AEM as a Cloud Service.

De Content Transformer kan helpen problemen op te lossen die onder de volgende [BPA-patrooncategorieën](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html) (weergegeven in de onderstaande tabel) door gebruikers in staat te stellen bulkhandelingen uit te voeren, zoals verplaatsen of verwijderen. Dit kan de tijd aanzienlijk verminderen en de complexiteit van een migratieproject verminderen.

## Patrooncategorieën die worden gedekt door Content Transformer en oplossingen die worden voorgesteld {#pattern-categories-and-benefits}

| Patrooncode | Type suspensie / Subtype | Mogelijke oplossing voordat inhoud wordt gemigreerd naar AEM as a Cloud Service |
|--------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| ACV | missing.jcrcontent <br> missing.original.rendition <br> metadata.descendants.schending | Verplaats deze elementen naar een andere locatie of verwijder ze om ervoor te zorgen dat ze niet worden gemigreerd naar AEM as a Cloud Service. |
| CAV | content.area.violation | Paden tijdelijk verplaatsen naar `/etc/packages/content-transformation/paths` om ervoor te zorgen dat zij niet naar AEM as a Cloud Service worden gemigreerd. |
| DOPI | deprecated.ordered.index | Verwijder de vervangen indexen. |
| OAUI | non.migrated.oauth.users | Verwijder deze gebruikers om ervoor te zorgen dat ze niet naar AEM as a Cloud Service worden gemigreerd. |
| PCX | page.complex.medium <br> pagina.complex.high | Verwijder de pagina&#39;s/onderliggende items of verplaats deze naar een andere locatie om te voorkomen dat ze worden gemigreerd naar AEM as a Cloud Service. |
| REP | forward.replication <br> reverse.replication <br> standard.replication.agent.modification <br> custom.replication.agent.detection | Verwijder de gecreeerde replicatieagenten. <br> OF <br> Verwijder de gewijzigde/toegevoegde eigenschappen. |
| URS | clientlibs.location <br> file.location <br> node.location <br> workflow.location | Ga naar de juiste locatie om problemen tijdens de migratie te voorkomen. |
| URS | node.size | De knooppunten tijdelijk verplaatsen naar`/etc/packages/content-transformation/paths` om ervoor te zorgen dat zij niet naar AEM as a Cloud Service worden gemigreerd. |

## Voordelen die worden geboden door de Content Transformer {#benefits}

De Content Transformer biedt de volgende voordelen:

* Niet-veilig: een pakket wordt gemaakt door de Content Transformer telkens wanneer de opslagplaats wijzigingen aanbrengt om problemen op te lossen. Indien nodig kunt u terugkeren naar de vorige status door het pakket te installeren.
* Eenvoudig te gebruiken: de Inhoudstransformer is geïntegreerd met het gereedschap Inhoudsoverdracht en wordt geleverd met een eenvoudige, intuïtieve gebruikersinterface.
* Bespart tijd: wanneer u veel inhoudsproblemen hebt die onder één patrooncategorie vallen, kunt u deze allemaal oplossen door met meerdere klikken de Inhoudstransformer te gebruiken.
