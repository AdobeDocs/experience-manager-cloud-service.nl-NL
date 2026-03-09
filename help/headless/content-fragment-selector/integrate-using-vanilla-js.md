---
title: Inhoudsfragmentkiezer integreren met Vanilla JS
description: Integreer de kiezer voor inhoudsfragmenten met verschillende Adobe-, niet-Adobe- en externe toepassingen.
role: Admin, User, Developer
source-git-commit: 592e443928f2c9c18ac281027026132b1c877ce3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Inhoudsfragmentkiezer integreren met Vanilla JS {#integrate-content-fragment-selector-using-vanilla-js}

U kunt elke Adobe- of niet-Adobe-toepassing integreren met Adobe Experience Manager (AEM) als een Cloud-opslagplaats en Content Fragments selecteren vanuit die toepassing.

De integratie wordt uitgevoerd door het pakket Content Fragment Selector te importeren en verbinding te maken met de AEM as a Cloud Service via de Vanilla JavaScript-bibliotheek. Bewerk een `index.html` of een ander geschikt bestand in uw toepassing om:

* De verificatiedetails definiëren
* Toegang krijgen tot de AEM as a Cloud Service-opslagplaats
* De weergave-eigenschappen van de Content Fragment Selector configureren

U kunt verificatie uitvoeren zonder enkele IMS-eigenschappen te definiëren, als u:

* integreren een toepassing van Adobe op [ Verenigde Shell ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell)
* Er is al een IMS-token gegenereerd voor verificatie
