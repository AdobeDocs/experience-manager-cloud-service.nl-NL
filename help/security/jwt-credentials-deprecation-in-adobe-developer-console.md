---
title: JWT Credentials Deprection in Adobe Developer Console
description: Meer informatie over de impact van de afschrijving van JWT-referenties in Adobe Developer Console op AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
source-git-commit: b52da0a604d2c320d046136f5e526e2b244fa6cb
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# JWT Credentials Deprection in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>AEM 6.5 [dit artikel](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) voor meer informatie .

Adobe die klanten gebruiken [Adobe Developer Console](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de geloofsbrieven van Server-aan-Server OAuth. De nieuwe geloofsbrieven van de Rekening van de Dienst (JWT) kunnen niet op of na 3 juni 2024 worden gecreeerd, en de bestaande geloofsbrieven van JWT zullen niet aan of na 27 jan. 2025 werken. U kunt [lezen over de afgekeurde tekst](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dit artikel biedt een extra context voor de manier waarop AEM as a Cloud Service de afleiding moet verwerken.

Momenteel, is de belangrijkste overname dat AEM eigenschappen nog niet de nieuwe geloofsbrieven van Server-aan-Server steunen OAuth. De steun komt snel-tegen medio april 2024 door een AEM versie voor AEM as a Cloud Service. U kunt een e-mail met instructies hebben ontvangen om uw geloofsbrieven van JWT te migreren, maar rust verzekerd dat u op de geloofsbrieven migratie kunt en zou moeten blokkeren tot AEM het nieuwe server-aan-server credentiële type van OAuth steunt.

In de volgende secties worden de scenario&#39;s weergegeven waarin klanten hun JWT-referenties (Service Account) moeten (of soms niet) vervangen door OAuth Server-to-Server-referenties, zodra AEM ze halverwege april ondersteunt. [Lees hoe](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) om de geloofsbrieven in de toekomst te vervangen.

>[!NOTE]
>
>De [**AEM** Ontwerpconsole](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (noteer de **AEM** in de naam, die deze onderscheidt van de **Adobe** Developer Console) biedt een hulpprogramma om te genereren [JWT-tokens](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) gebruikt voor server-aan-server APIs. Deze gegevens zijn niet afgekeurd en kunnen ook in de toekomst worden gebruikt.


## AEM integreren met andere oplossingen voor Adobe {#integrating-aem-with-other-adobe-solutions}

**Handeling**: Wacht op migratie tot eind april 2024, wanneer AEM het ondersteunt (dit artikel wordt dan bijgewerkt)

**Relevante AEM versies**: AEM AS A CLOUD SERVICE

AEM klanten gebruiken AEM Auteur UI om integratie met alle andere oplossingen van de Adobe te vormen. Bijvoorbeeld Adobe Target, Adobe Analytics, Adobe Launch, AFCS en nog veel meer.

![AEM integreren met andere oplossingen](/help/security/assets/jwt-deprecation.png)

Hier ziet u bijvoorbeeld [de instructies](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=en) voor het configureren van de integratie met Adobe Target. De API-sleutel in het dialoogvenster [De IMS-configuratie voltooien in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html#completing-the-ims-configuration-in-aem) de sectie zou aan het server-aan-server referentie type van OAuth moeten worden gemigreerd, zodra AEM die geloofsbrieven halverwege april steunt. Die instructies zullen half april worden bijgewerkt om u te helpen de nieuwe geloofsbrieven van Server-aan-Server toepassen OAuth.

## Cloud Manager-API&#39;s {#cloud-manager-apis}

**Handeling**: Wacht op migratie tot eind april 2024, wanneer AEM het ondersteunt (dit artikel wordt op dat moment bijgewerkt).

**Relevante AEM versies**: AEM AS A CLOUD SERVICE

Klanten maken Adobe Developer Console-projecten zodat ze deze kunnen aanroepen [Cloud Manager-API&#39;s](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). De geloofsbrieven in het project van Adobe Developer zouden aan het OAuth server-aan-Server credentietype moeten worden gemigreerd, zodra AEM en de Manager van de Wolk het steunen.

## Automatisch gegenereerde projecten {#autogen-projects}

**Handeling**: Niet migreren omdat Adobe voor u gaat migreren.

**Relevante AEM versies**: AEM as a Cloud Service.

Wanneer de bepalingen van de Manager van de Wolk AEM as a Cloud Service milieu, het auto-produceert een project van de Console van Adobe Developer met geloofsbrieven JWT. Dit project is gemarkeerd als alleen-lezen, zoals in de onderstaande schermafbeelding wordt geïllustreerd. De klanten kunnen en zouden niet moeten proberen om deze projecten aan geloofsbrieven te migreren OAuth Server-aan-Server; in plaats daarvan, gaat de Adobe deze projecten op zijn eigen migreren, alvorens de geloofsbrieven niet meer bruikbaar zijn.

![Automatisch gegenereerde projecten](/help/security/assets/jwt-deprecation-autogen-projects.png)
