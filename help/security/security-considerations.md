---
title: Overwegingen voor AEM as a Cloud Service-beveiliging
description: Meer informatie over belangrijke beveiligingsoverwegingen bij het gebruik van AEM as a Cloud Service.
hidefromtoc: true
hide: true
exl-id: d2dfde05-ce02-478e-8697-b939fb8740c3
feature: Security
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Overwegingen voor AEM as a Cloud Service-beveiliging {#security-considerations}

## AEM Trust Store {#aem-trust-store}

Om asymmetrische, cryptografische verrichtingen te steunen, AEM slaat certificaten binnen de inhoudsbewaarplaats, in een globaal vertrouwen-opslag op. De inhoud is openbaar en is standaard anoniem toegankelijk voor iedereen op uitgeversexemplaren.

### Kenmerken van de Trust Store {#truststore-characteristics}

* De vertrouwde opslag bevindt zich onder `/etc/truststore` en bestaat uit een Java™ sleutelarchiefbestand, het sleutelarchiefwachtwoord en de metagegevens van de opslagplaats. Zowel het wachtwoord als het sleutelarchief zijn om technische redenen gecodeerd, ook al zijn de ingesloten certificaten standaard voor iedereen toegankelijk via de API
* Buiten het vak worden de certificaten alleen gebruikt voor HTTPS- en SAML-ondersteuning en moet de winkel eerst handmatig worden gemaakt
* De klanten kunnen het in hun eigen code door [&#x200B; keystore API &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-) gebruiken
* De vertrouwen-opslag kan door UI in **Hulpmiddelen** worden geleid - **Veiligheid** - **opslag van het Vertrouwen** of door tot *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`* toegang te hebben, zoals hieronder getoond:

  ![&#x200B; Beheer van de Opslag van het Vertrouwen &#x200B;](/help/security/assets/global-trust-store-modified.png)

* De toegang tot de trust-opslag kan verder worden beperkt door de toegangscontrole van de bewaarplaats afhankelijk van het gebruik-geval.

>[!NOTE]
>
>De Adobe beveelt aan dat de standaardtoegangscontroles voor de Opslag van het Vertrouwen worden gebruikt, wat betekent dat het openbaar toegankelijk blijft. Voor de veiligste configuratie kunt u een beleid van ontkennen `jcr:all` voor iedereen gebruiken.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, see [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=nl-NL#anonymous-permission-hardening-package).
-->
