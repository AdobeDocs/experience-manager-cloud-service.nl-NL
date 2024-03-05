---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de gevolgen van de afschrijving van JWT-gebruikersgegevens in Adobe Developer Console voor AEM
source-git-commit: a354786f1ddfe50b01def85d3c83da09c6a35d2f
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---


# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM als Cloud Service dienen klanten te verwijzen naar [dit artikel](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html) voor meer informatie .

Adobe die klanten gebruiken [Adobe Developer Console](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 1 Mei, 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 1 Jan, 2025 werken. U kunt [lezen over de afgekeurde tekst](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dit artikel biedt een extra context voor de manier waarop AEM as a Cloud Service de afleiding moet verwerken.

Het belangrijkste op dit ogenblik weghalen is dat AEM eigenschappen nog niet de nieuwe geloofsbrieven van Server-aan-Server steunen OAuth. De steun zal binnenkort — medio april 2024 door een AEM release voor AEM as a Cloud Service komen. U kunt een e-mail met instructies hebben ontvangen om uw geloofsbrieven van JWT te migreren, maar rust verzekerd dat u op de geloofsbrieven migratie kunt en zou moeten blokkeren tot AEM het nieuwe server-aan-server credentiële type van OAuth steunt.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-gegevens (Service Account) moeten vervangen door OAuth Server-to-Server-referenties, zodra AEM deze gegevens medio april ondersteunt. [Lees hoe](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) om de geloofsbrieven in de toekomst te vervangen.

>[!NOTE]
>
>De [**AEM** Ontwerpconsole](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (noteer de **AEM** in de naam, die deze onderscheidt van de **Adobe** Developer Console) biedt een hulpprogramma om te genereren [JWT-tokens](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) gebruikt voor server-aan-server APIs. Deze gegevens zijn niet afgekeurd en kunnen ook in de toekomst worden gebruikt.


## AEM integreren met andere oplossingen voor Adobe {#integrating-aem-with-other-adobe-solutions}

**Handeling**: Wacht op migratie tot medio april 2024, wanneer AEM het ondersteunt.

**Relevante AEM versies**: AEM AS A CLOUD SERVICE

AEM klanten gebruiken AEM Auteur UI om integratie met alle andere oplossingen van de Adobe te vormen. Bijvoorbeeld Adobe Target, Adobe Analytics, Adobe Launch, AFCS en nog veel meer.

![AEM integreren met andere oplossingen](/help/security/assets/jwt-deprecation.png)

Hier ziet u bijvoorbeeld [de instructies](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=en) voor het configureren van de integratie met Adobe Target. De API-sleutel in het dialoogvenster [De IMS-configuratie voltooien in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html#completing-the-ims-configuration-in-aem) de sectie zou aan het server-aan-server referentie type van OAuth moeten worden gemigreerd, zodra AEM die geloofsbrieven halverwege april steunt. Die instructies zullen half april worden herzien om u te helpen de nieuwe geloofsbrieven van Server-aan-Server toepassen OAuth.

## Cloud Manager-API&#39;s {#cloud-manager-apis}

**Handeling**: Wacht op migratie tot medio april 2024, wanneer AEM het ondersteunt.

**Relevante AEM versies**: AEM AS A CLOUD SERVICE

Klanten maken Adobe Developer Console-projecten zodat ze deze kunnen aanroepen [Cloud Manager-API&#39;s](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). De geloofsbrieven in het project van Adobe Developer zouden aan het OAuth server-aan-Server credentietype moeten worden gemigreerd, zodra AEM en de Manager van de Wolk het steunen.

## Automatisch gegenereerde projecten {#autogen-projects}

**Handeling**: Niet migreren omdat de Adobe voor u zal migreren.

**Relevante AEM versies**: AEM as a Cloud Service.

Wanneer de bepalingen van de Manager van de Wolk AEM as a Cloud Service milieu&#39;s, het automatisch een project van de Console van Adobe Developer met geloofsbrieven JWT produceert. Dit project is gemarkeerd als alleen-lezen, zoals in de onderstaande schermafbeelding wordt geïllustreerd. De klanten kunnen en zouden niet moeten proberen om deze projecten aan geloofsbrieven van Server-aan-Server te migreren OAuth; in plaats daarvan, zal de Adobe deze projecten op zijn eigen migreren, alvorens de geloofsbrieven niet meer bruikbaar zijn.

![Automatisch gegenereerde projecten](/help/security/assets/jwt-deprecation-autogen-projects.png)

