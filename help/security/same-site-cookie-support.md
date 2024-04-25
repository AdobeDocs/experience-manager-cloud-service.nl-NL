---
title: Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager as a Cloud Service
description: Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager as a Cloud Service.
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
source-git-commit: 678e81eb22cc1d7c239ac7a2594b39a3a60c51e2
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Sinds versie 80, introduceerde Chrome, en recentere Safari, een nieuw model voor koekjesveiligheid. Deze wijze wordt ontworpen om veiligheidscontroles rond beschikbaarheid van koekjes aan derdeplaatsen, door het plaatsen te introduceren genoemd `SameSite`. Zie deze voor meer informatie [artikel](https://web.dev/articles/samesite-cookies-explained).

De standaardwaarde van deze instelling (`SameSite=Lax`) kan ervoor zorgen dat verificatie tussen AEM instanties of services niet werkt. Dit komt doordat de domeinen of URL-structuren van deze services mogelijk niet onder de beperkingen van dit cookiebeleid vallen.

Als u dit wilt omzeilen, stelt u het Cookie-kenmerk SameSite in op `None` voor het aanmeldingstoken.

>[!CAUTION]
>
>De `SameSite=None` instelling wordt alleen toegepast als het protocol beveiligd is (HTTPS).
>
>Als het protocol niet veilig (HTTP) is, dan wordt het plaatsen genegeerd en de server toont dit waarschuwingsbericht:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

U kunt de instelling toevoegen door de volgende stappen uit te voeren:

1. Een versie van de AEM SDK QuickStart lokaal installeren
1. Ga naar de webconsole op `http://serveraddress:serverport/system/console/configMgr`
1. Zoeken naar en klikken op de knop **Adobe Granite Token Authentication Handler**
1. Stel de **Het attribuut SameSite voor het cookie met het token login** tot `None`, zoals wordt weergegeven in de onderstaande afbeelding
   ![samesite](/help/security/assets/samesite1.png)
1. Klik op Opslaan
1. Genereer de JSON-opmaakconfiguraties voor deze specifieke instelling door de stappen uit te voeren die worden beschreven in [OSGi-configuraties genereren met de AEM SDK QuickStart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)
1. Pas de instellingen toe door de stappen in het dialoogvenster [Cloud Manager API-indeling voor het instellen van eigenschappen](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) OSGi-documentatie.

Nadat deze instelling is bijgewerkt en de gebruikers zijn afgemeld en opnieuw zijn aangemeld, `login-token` cookies hebben de `None` kenmerk ingesteld en wordt opgenomen in aanvragen voor andere sites.
