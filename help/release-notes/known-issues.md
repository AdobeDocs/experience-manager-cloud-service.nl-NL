---
title: Bekende problemen
description: Bekende problemen met Adobe Experience Manager as a Cloud Service
exl-id: 897b944a-d320-4d21-91f4-2cd3da6179b1
source-git-commit: 755c0072148ad73486df2ccfed69248b9d73ec2a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Bekende problemen {#known-issues}

In dit artikel worden de bekende problemen van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] aanbieden. De lijst wordt herzien en bijgewerkt bij elke ononderbroken release van [!DNL Experience Manager].

[Contact opnemen met ondersteuning](https://experienceleague.adobe.com/?lang=en&amp;support-solution=Experience+Manager#support) voor meer informatie over de bekende problemen.

<!-- 
## Platform {#platform}
-->

## Sites {#sites}

Sommige bekende problemen in [!DNL Sites] zijn:

* In GrafiekQL winde kunt u [beheer het geheime voorgeheugen voor uw voortgezette vragen](/help/headless/graphql-api/graphiql-ide.md##managing-cache).
   * Bij de eerste keer sparen de waarden voor de kopballen worden bewaard geplaatst aan `0` (in plaats van de standaardwaarden) - als de gebruiker deze waarden in het dialoogvenster niet heeft gewijzigd.
   * Bij het opslaan worden de waarden correct opgeslagen.
   * Daarom moet de gebruiker de kopballen tweemaal bewaren.

## [!DNL Assets] {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Sommige bekende problemen in [!DNL Assets] zijn:

* **Downloaden**: Als u een lege map downloadt, [!DNL Experience Manager] geeft een succesbericht weer over het maken van een ZIP-archief, maar het archief wordt niet gemaakt.

* **Metagegevensschema**: Widget voor assetclassificatie die wordt gebruikt om een JSP-compilatiefout te veroorzaken. Deze is verwijderd uit het metagegevensschema. <!-- CQ-4282865, CQ-4284633 -->

Zie ook [opmerkelijke wijzigingen in [!DNL Experience Manager Assets]](/help/assets/assets-cloud-changes.md).

<!-- This content was added at GA. Not sure if we should continue to have this commitment about upcoming features/enh. in the docs. Commenting it for now.

### Upcoming Assets capabilities {#upcoming-assets-capabilities}

A few capabilities of Adobe Experience Manager Assets that depend on foundation capabilities, which are not yet available in the Experience Manager as a Cloud Service deployment architecture, are expected to be enabled at a later stage:

* Capabilities not enabled at this stage due to dependency on Commerce Integration Framework APIs:
  * Photoshoot workflow models.
  * Product information tab in the asset properties user interface is not populated.

* Capabilities not enabled at this stage due to dependency on InDesign Server integration:
  * Asset Templates and Asset Catalogs.
  * Multi-page preview of Adobe InDesign files.
-->

>[!MORELIKETHIS]
>
>* [Belangrijke wijzigingen in [!DNL Experience Manager]](aem-cloud-changes.md)
>* [Verouderde en verwijderde functies](deprecated-removed-features.md)
>* [Opmerkingen bij de release](home.md)

