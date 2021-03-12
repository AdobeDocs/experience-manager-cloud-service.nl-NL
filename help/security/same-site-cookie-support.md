---
title: Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager als Cloud Service
description: ISame Site Cookie-ondersteuning voor Adobe Experience Manager als Cloud Service
translation-type: tm+mt
source-git-commit: 24f26a5cc77158ea20a09b1f40cf3d849a70591f
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Ondersteuning voor zelfde sitecookie voor Adobe Experience Manager als een Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Sinds versie 80, introduceerde Chrome, en recentere Safari, een nieuw model voor koekjesveiligheid. Deze wijze wordt ontworpen om veiligheidscontroles rond beschikbaarheid van koekjes aan derdeplaatsen, door het plaatsen te introduceren genoemd `SameSite`. Voor meer gedetailleerde informatie, zie dit [artikel](https://web.dev/samesite-cookies-explained/).

De standaardwaarde van dit plaatsen (`SameSite=Lax`) zou authentificatie tussen AEM instanties of de diensten kunnen veroorzaken om niet te werken. Dit komt doordat de domeinen of URL-structuren van deze services mogelijk niet onder de beperkingen van dit cookiebeleid vallen.

Om rond dit te krijgen, moet u het koekjesattribuut SameSite aan `None` voor het login token plaatsen.

U kunt dit doen door de volgende stappen te volgen:

1. Een versie van de AEM SDK QuickStart lokaal installeren
1. Ga naar de webconsole op `http://serveraddress:serverport/system/console/configMgr`
1. Zoek naar en klik **Adobe granite Token Authentication Handler**
1. Stel het **SameSite-kenmerk voor het cookie** in op `None`, zoals in de onderstaande afbeelding wordt getoond
   ![samesite](/help/security/assets/samesite1.png)
1. Klik op Opslaan
1. Genereer de JSON-opmaakconfiguraties voor deze specifieke instelling door de stappen te volgen die worden beschreven in [OSGi-configuraties genereren met de AEM SDK QuickStart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)
1. Pas de instellingen toe door de stappen in de [Cloud Manager API-indeling voor het instellen van eigenschappen](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) OSGi-documentatie uit te voeren.
