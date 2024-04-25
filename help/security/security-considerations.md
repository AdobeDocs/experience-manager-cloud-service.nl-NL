---
title: Overwegingen bij as a Cloud Service beveiliging AEM
description: Lees meer over belangrijke beveiligingsoverwegingen wanneer u AEM as a Cloud Service gebruikt.
hidefromtoc: true
hide: true
exl-id: d2dfde05-ce02-478e-8697-b939fb8740c3
source-git-commit: 678e81eb22cc1d7c239ac7a2594b39a3a60c51e2
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Overwegingen bij as a Cloud Service beveiliging AEM {#security-considerations}

## AEM Trust Store {#aem-trust-store}

Om asymmetrische, cryptografische verrichtingen te steunen, AEM slaat certificaten binnen de inhoudsbewaarplaats, in een globaal vertrouwen-opslag op. De inhoud is openbaar en is standaard anoniem toegankelijk voor iedereen op uitgeversexemplaren.

### Kenmerken van de Trust Store {#truststore-characteristics}

* De vertrouwde-opslag bevindt zich hieronder `/etc/truststore` en bestaat uit een Java™ sleutelarchiefbestand, het sleutelarchiefwachtwoord en de gegevensopslaggegevens. Zowel het wachtwoord als het sleutelarchief zijn om technische redenen gecodeerd, ook al zijn de ingesloten certificaten standaard voor iedereen toegankelijk via de API
* Buiten het vak worden de certificaten alleen gebruikt voor HTTPS- en SAML-ondersteuning en moet de winkel eerst handmatig worden gemaakt
* Klanten kunnen het in hun eigen code gebruiken door [sleutelarchief-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)
* De trust-opslag kan door UI bij worden beheerd **Gereedschappen** - **Beveiliging** - **Trust Store** of door toegang *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*, zoals hieronder weergegeven:

  ![Betrouwbaarheidswinkelbeheer](/help/security/assets/global-trust-store-modified.png)

* De toegang tot de trust-opslag kan verder worden beperkt door de toegangscontrole van de bewaarplaats afhankelijk van het gebruik-geval.

>[!NOTE]
>
>De Adobe beveelt aan dat de standaardtoegangscontroles voor de Opslag van het Vertrouwen worden gebruikt, wat betekent dat het openbaar toegankelijk blijft. Voor de veiligste configuratie, kunt u een beleid van ontkennen gebruiken `jcr:all` voor iedereen.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, see [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
