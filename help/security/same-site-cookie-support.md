---
title: Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager as a Cloud Service
description: Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager as a Cloud Service.
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
feature: Security
role: Admin
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Ondersteuning voor zelfde site-cookie voor Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Sinds versie 80, Chrome, en later Safari, introduceerde een nieuw model voor koekjesveiligheid. Deze modus is ontworpen om beveiligingsinstellingen te introduceren voor de beschikbaarheid van cookies op sites van derden, via een instelling die `SameSite` wordt genoemd. Voor meer gedetailleerde informatie, zie [ web.dev - de koekjes SameSite verklaarden ](https://web.dev/articles/samesite-cookies-explained).

De standaardwaarde van dit plaatsen (`SameSite=Lax`) zou authentificatie tussen AEM instanties of de diensten kunnen veroorzaken om niet te werken. Dit komt doordat de domeinen of URL-structuren van deze services mogelijk niet onder de beperkingen van dit cookiebeleid vallen.

Als u dit wilt omzeilen, stelt u het Cookie-kenmerk SameSite in op `None` voor het aanmeldingstoken.

>[!CAUTION]
>
>De instelling `SameSite=None` wordt alleen toegepast als het protocol beveiligd is (HTTPS).
>
>Als het protocol niet veilig (HTTP) is, dan wordt het plaatsen genegeerd en de server toont dit waarschuwingsbericht:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

U kunt de instelling toevoegen door de volgende stappen uit te voeren:

1. Een versie van de AEM SDK QuickStart lokaal installeren
1. Ga naar de webconsole op `http://serveraddress:serverport/system/console/configMgr`
1. Onderzoek naar en klik de **Adobe granite Symbolische Handler van de Authentificatie**
1. Plaats het **SameSite attribuut voor het login-symbolische koekje** aan `None`, zoals aangetoond in het hieronder beeld
   ![ gelijk ](/help/security/assets/samesite1.png)
1. Klik op Opslaan
1. Produceer de JSON formaatconfiguraties voor dit bepaalde plaatsen door de stappen te volgen die in [ worden geschetst die Configuraties OSGi gebruikend de Snelle start van SDK van de AEM gebruiken ](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)
1. Pas de montages toe door de stappen in het [ Cloud Manager API Formaat voor het Plaatsen van Eigenschappen ](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) OSGi documentatie te volgen.

Nadat deze instelling is bijgewerkt en gebruikers zijn afgemeld en opnieuw zijn aangemeld, wordt voor `login-token` -cookies het kenmerk `None` ingesteld en opgenomen in intersite aanvragen.
