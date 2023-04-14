---
title: Overwegingen bij as a Cloud Service beveiliging AEM
description: Belangrijke beveiligingsoverwegingen bij het gebruik van AEM as a Cloud Service
hidefromtoc: true
hide: true
source-git-commit: 39ffd826f5d1e9cea2e6a03a74f39c16647b45fa
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Overwegingen bij as a Cloud Service beveiliging AEM {#security-considerations}

## AEM Trust Store {#aem-trust-store}

Om asymmetrische, cryptografische verrichtingen te steunen, AEM certificaten binnen de inhoudsbewaarplaats, in een globaal vertrouwen-opslag op. De inhoud is openbaar en is standaard anoniem toegankelijk voor iedereen op uitgeversexemplaren.

### Kenmerken van de Trust Store {#truststore-characteristics}

* De vertrouwde-opslag bevindt zich hieronder `/etc/truststore` en bestaat uit een Java-sleutelarchiefbestand, het sleutelarchiefwachtwoord en de gegevensopslaggegevens. Merk op dat zowel het wachtwoord als keystore zelf om technische redenen worden gecodeerd, ook al zijn de ingesloten certificaten standaard toegankelijk voor iedereen via de API
* Buiten het vak worden de certificaten alleen gebruikt voor HTTPS- en SAML-ondersteuning en moet de winkel eerst handmatig worden gemaakt
* Klanten kunnen het in hun eigen code gebruiken door [sleutelarchief-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)
* De trust-opslag kan door UI bij worden beheerd **Gereedschappen** - **Beveiliging** - **Trust Store** of door toegang *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*, zoals hieronder weergegeven:

   ![Betrouwbaarheidswinkelbeheer](/help/security/assets/global-trust-store-modified.png)

* De toegang tot de trust-opslag kan verder worden beperkt door de toegangscontrole van de bewaarplaats afhankelijk van het gebruik-geval.

>[!NOTE]
>
>Adobe raadt aan de standaardtoegangscontroles te gebruiken voor de Opslag van het Vertrouwen, wat betekent dat het openbaar toegankelijk blijft. Voor de veiligste configuratie, kunt u een beleid gebruiken van ontkennen jcr:allen voor iedereen.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, please see the [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
