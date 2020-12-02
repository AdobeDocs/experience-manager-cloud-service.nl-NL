---
title: Aan de slag met AEM Commerce als Cloud Service
description: Leer hoe te om een handel-toegelaten AEM project aan een lopende AEM als de dienstmilieu van de Wolk op te stellen. Gebruik functies van Adobe Cloud Manager en een CI/CD-pijplijn om de Venia-naslaggids te maken naar een actieve omgeving.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: 7a26596b00f276404934e467490ff79d08b0e1d0
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 2%

---


# Aan de slag met AEM Handel als Cloud Service {#start}

Om met AEM Handel als Cloud Service te beginnen, moet uw Experience Manager Cloud Service worden voorzien van het Kader van de Integratie van de Handel (CIF) toe:voegen-on. De invoegtoepassing CIF is een extra module boven op [AEM Sites als een Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/home.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Onboarding {#onboarding}

Het instappen voor AEM Handel als Cloud Service is een proces in twee stappen:

1. Krijg AEMHandel als toegelaten Cloud Service en CIF toe:voegen-on provisioned
2. Sluit AEM Handel als Cloud Service met uw Magento milieu aan

De eerste stap wordt gedaan door Adobe. U zult informatie zoals de organisatie IMS, het eindpunt URL GraphQL eindpunt van uw milieu van Magento, enz. moeten verstrekken. als onderdeel van het inrichtingsproces. Voor meer informatie over prijzen en provisioning moet u contact opnemen met uw verkoper.

Nadat u de CIF-invoegtoepassing hebt ingericht, wordt deze toegepast op alle bestaande Cloud Manager-programma&#39;s. Als u geen Cloud Manager-programma hebt, moet u een nieuw programma maken. Voor meer details, verwijs naar [Opstelling uw Programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

De tweede stap is zelfbediening voor elke AEM als omgeving van een Cloud Service. Er zijn sommige extra configuraties u na de aanvankelijke levering van toe:voegen-op CIF zult moeten doen.

## Verbinding maken AEM Handel met Magento {#magento}

Om CIF toe:voegen-op &amp; [AEM de milieu van de Kern van CIF ](https://github.com/adobe/aem-core-cif-components) met u Magento te verbinden moet u het eindpunt URL van Magento GraphQL via een de omgevingsvariabele van de Manager van de Wolk verstrekken. De variabelenaam is `COMMERCE_ENDPOINT`. Er moet een beveiligde verbinding via HTTPS worden geconfigureerd.
Een verschillend eindpunt URL van Magento GraphQL eindpunt kan voor elke AEM als milieu van de Cloud Service worden gebruikt. Zo kunnen projecten AEM het opvoeren milieu&#39;s met Magento opvoeren systemen en AEM productiemilieu met een Magento productiesysteem verbinden. Dat eindpunt van Magento GraphQL openbaar moet zijn, privé VPN of lokale verbindingen worden niet gesteund.

Ga als volgt te werk om AEM Handel met Magento te verbinden:

1. De Adobe I/O CLI ophalen met de plug-in Cloud Manager

   Raadpleeg de [Adobe Cloud Manager-documentatie](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) voor informatie over het downloaden, instellen en gebruiken van de [Adobe I/O CLI](https://github.com/adobe/aio-cli) met de [Cloud Manager CLI-plug-in](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Verifieer CLI met de AEM als programma van de Cloud Service

3. De variabele `COMMERCE_ENDPOINT` instellen in Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Zie [CLI docs](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor meer informatie.

   De Magento GraphQL eindpunt URL moet aan de dienst richten GraphQl en een veilige verbinding gebruiken HTTPS. Bijvoorbeeld: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>U kunt alle variabelen van de Manager van de Wolk een lijst maken gebruikend het volgende bevel om te controleren tweemaal: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>U kunt ook de [Cloud Manager-API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) gebruiken om de Cloud Manager-variabelen ook te configureren.

Met dit, bent u klaar om AEM Handel als Cloud Service te gebruiken en uw project via de Manager van de Wolk te opstellen.

## Niet-actieve catalogusfuncties inschakelen (optioneel) {#staging}

>[!NOTE]
>
>Deze functie is alleen beschikbaar bij Magento Enterprise Edition of Magento Cloud.

1. Meld u aan bij Magento en maak een integratietoken. Zie [Op token gebaseerde verificatie](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) voor meer informatie. Zorg ervoor dat het integratietoken *only* toegang tot `Content -> Staging` middelen heeft. Kopieer de waarde `Access Token`.

1. Stel de geheime variabele `COMMERCE_AUTH_HEADER` in Cloud Manager in:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization Bearer: <Access Token>"
   ```

   Zie [AEM Commerce verbinden met Magento](#magento) voor het configureren van de Adobe I/O CLI voor Cloud Manager.

## Integratie van andere bedrijven {#integrations}

Voor de integratie van de derdehandel, is een [API mappinglayer](architecture/third-party.md) nodig om AEM Handel als Cloud Service en de Componenten van de Kern van CIF met uw handelsysteem te verbinden. Deze API-toewijzingslaag wordt doorgaans geïmplementeerd op Adobe I/O Runtime. Neem contact op met uw verkoper voor de beschikbare integratie en toegang tot Adobe I/O Runtime.
