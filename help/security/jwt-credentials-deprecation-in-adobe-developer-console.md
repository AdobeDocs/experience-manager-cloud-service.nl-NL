---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de impact van de afschrijving van JWT-referenties in Adobe Developer Console op AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
source-git-commit: f183e1999e29ee7f25f2d427d0b2273d244e4632
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5 [dit artikel](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) voor meer informatie .

Adobe die klanten gebruiken [Adobe Developer Console](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 3 juni 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 27 jan. 2025 werken. U kunt [lezen over de afgekeurde tekst](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dit artikel biedt een extra context voor de manier waarop AEM as a Cloud Service de afleiding moet verwerken.

Het belangrijkste wegnemen is dat AEM nu de nieuwe geloofsbrieven van Server-aan-Server OAuth voor AEM as a Cloud Service steunt. Mogelijk hebt u een e-mail ontvangen met instructies voor het migreren van uw JWT-gegevens. Deze migratie kan nu worden uitgevoerd.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-referenties (Service Account) moeten vervangen door OAuth Server-to-Server-referenties, nu AEM hen ondersteunt. [Lees hoe](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) om de gegevens te migreren.

>[!NOTE]
>
>De [**AEM** Ontwerpconsole](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (noteer de **AEM** in de naam, die deze onderscheidt van de **Adobe** Developer Console) biedt een hulpprogramma om te genereren [JWT-tokens](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) gebruikt voor server-aan-server APIs. Deze gegevens zijn niet afgekeurd en kunnen ook in de toekomst worden gebruikt.

## AEM integreren met andere oplossingen voor Adobe {#integrating-aem-with-other-adobe-solutions}

**Handeling**: Migreer uw configuratie aangezien AEM nu geloofsbrieven OAuth steunt.

**Relevante AEM versies**: AEM AS A CLOUD SERVICE

AEM klanten gebruiken AEM om integratie met vele andere oplossingen van de Adobe te vormen. Bijvoorbeeld Adobe Target, Adobe Analytics en andere.

Zie [IMS-integratie instellen voor AEM as a Cloud Service](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) voor meer informatie over hoe:

* configuraties maken met OAuth-gebruikersgegevens
* migreer configuraties, die met geloofsbrieven JWT werden gecreeerd, om geloofsbrieven te gebruiken OAuth

## Cloud Manager-API&#39;s {#cloud-manager-apis}

**Handeling**: Migreer uw JWT-gegevens naar OAuth-gegevens, die nu door Cloud Manager worden ondersteund.

**Relevante AEM versies**: AEM AS A CLOUD SERVICE

Klanten maken Adobe Developer Console-projecten zodat ze deze kunnen aanroepen [Cloud Manager-API&#39;s](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). De geloofsbrieven in het project van Adobe Developer zouden aan het server-aan-Server referentie type OAuth moeten worden gemigreerd alvorens de afgekeurde geloofsbrieven JWT in Januari 2025 verlopen.

## Automatisch gegenereerde projecten {#autogen-projects}

**Handeling**: Niet migreren omdat Adobe voor u gaat migreren.

**Relevante AEM versies**: AEM as a Cloud Service.

Wanneer de bepalingen van de Manager van de Wolk AEM as a Cloud Service milieu&#39;s, het automatisch een project van de Console van Adobe Developer met geloofsbrieven JWT produceert. Dit project is gemarkeerd als alleen-lezen, zoals in de onderstaande schermafbeelding wordt geïllustreerd. De klanten kunnen en zouden niet moeten proberen om deze projecten aan OAuth server-aan-Server geloofsbrieven te migreren. In plaats daarvan, zal de Adobe deze projecten op zich migreren, alvorens de geloofsbrieven niet meer bruikbaar zijn.

![Automatisch gegenereerde projecten](/help/security/assets/jwt-deprecation-autogen-projects.png)
