---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Integreer de selecteur van Activa met diverse Adobe, niet-Adobe, en derdetoepassingen.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Asset Selector integreren met Vanilla JS {#integration-using-vanilla-js}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

U kunt elke toepassing van het type [!DNL Adobe] of niet-Adobe integreren met de [!DNL Experience Manager Assets] -opslagplaats en elementen selecteren vanuit de toepassing. Zie [ de Integratie van de Selecteur van Activa met diverse toepassingen ](#asset-selector-integration-with-apps).

De integratie gebeurt door het pakket Asset Selector te importeren en verbinding te maken met de Assets-as a Cloud Service met behulp van de Vanilla JavaScript-bibliotheek. Bewerk een `index.html` of een ander geschikt bestand in uw toepassing om:

* De verificatiedetails definiëren
* Toegang krijgen tot de Assets as a Cloud Service dataopslag
* De weergave-eigenschappen voor de middelenkiezer configureren

U kunt verificatie uitvoeren zonder enkele IMS-eigenschappen te definiëren, als:

* U integreert een [!DNL Adobe] toepassing op [ Verenigde Shell ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=en).
* Er is al een IMS-token gegenereerd voor verificatie.

## Asset Selector integreren met verschillende toepassingen {#asset-selector-integration-with-apps}

U kunt Asset Selector integreren met verschillende toepassingen, zoals:

* [Integreer de Selecteur van Activa met een  [!DNL Adobe]  toepassing](/help/assets/integrate-asset-selector-adobe-app.md)
* [Asset Selector integreren met een toepassing zonder Adobe](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Integratie voor Dynamic Media met OpenAPI-mogelijkheden](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [ de aanpassingen van de Selecteur van Activa ](/help/assets/asset-selector-customization.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
>* [ integreer de Selector van Activa met Dynamic Media met mogelijkheden OpenAPI ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
