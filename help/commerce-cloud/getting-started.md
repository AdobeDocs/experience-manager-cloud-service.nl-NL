---
title: Aan de slag met AEM as a Cloud Service Handel
description: Leer hoe te om een handel-toegelaten AEM project aan een lopende AEM als de dienstmilieu van de Wolk op te stellen. Gebruik functies van Adobe Cloud Manager en een CI/CD-pijplijn, zodat u de Venia-referentieopslag kunt bouwen naar een actieve omgeving.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# Aan de slag met AEM as a Cloud Service Handel {#start}

Om met AEM as a Cloud Service Handel te beginnen, moet uw Experience Manager Cloud Service met het Kader van de Integratie van de Handel (CIF) toe:voegen-on worden voorzien. De invoegtoepassing CIF is een extra module boven op [AEM Sites as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/home.html).

## Onboarding {#onboarding}

Het aan boord nemen voor AEM as a Cloud Service Handel is een proces in twee stappen:

1. Krijg AEM as a Cloud Service Handel toegelaten en toe:voegen-op CIF provisioned
2. Connect AEM Commerce as a Cloud Service met uw handelsoplossing

De eerste instapstap wordt uitgevoerd door Adobe. Voor meer informatie over prijzen en provisioning moet u contact opnemen met uw verkoper.

Nadat u de CIF-invoegtoepassing hebt ingericht, wordt deze toegepast op bestaande Cloud Manager-programma&#39;s. Als u geen Cloud Manager-programma hebt, moet u er een maken. Raadpleeg voor meer informatie [Uw programma instellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html).

De tweede stap is zelfbediening voor elke AEM as a Cloud Service omgeving. Er zijn sommige extra configuraties die u na de aanvankelijke levering van toe:voegen-op CIF moet doen.

## AEM verbinden met een Oplossing van de Handel {#solution}

De CIF-invoegtoepassing en de [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) met een handelsoplossing, moet u het eindpunt URL van GraphQL als milieuvariabele van de Manager van de Wolk verstrekken. De variabelenaam is `COMMERCE_ENDPOINT`. Er moet een beveiligde verbinding via HTTPS worden geconfigureerd.

Deze omgevingsvariabele wordt op twee plaatsen gebruikt:

- De vraag van GraphQL van AEM aan handelsafstand, als één of andere gemeenschappelijke cliënt GraphQl, die door de AEM componenten van de Kern van CIF en componenten van het klantenproject wordt gebruikt.
- Stel een GraphQL-proxy-URL in voor elke AEM omgeving waarin de variabele beschikbaar is `/api/graphql`. Deze URL wordt gebruikt door de AEM handels auteurshulpmiddelen (toe:voegen-aan CIF) en cliënt-zijcomponenten CIF.

Voor elke AEM as a Cloud Service omgeving kan een andere URL voor het eindpunt van GraphQL worden gebruikt. Zo kunnen projecten AEM het opvoeren milieu&#39;s met handel het opvoeren systemen en AEM productiemilieu met een handelsproductiesysteem verbinden. Dat het eindpunt van GraphQL openbaar moet zijn, privé VPN of lokale verbindingen worden niet gesteund. Naar keuze, kan een authentificatiekopbal worden verstrekt om extra eigenschappen te gebruiken CIF die authentificatie vereisen.

De CIF-invoegtoepassing (optioneel en alleen voor Adobe Commerce Enterprise/Cloud) ondersteunt het gebruik van gefaseerde catalogusgegevens voor AEM auteurs. Deze gegevens vereisen dat u een vergunningskopbal vormt. Deze koptekst is alleen beschikbaar en wordt uit veiligheidsoverwegingen gebruikt bij AEM auteur-instanties. AEM publicatie-instanties kunnen geen gefaseerde gegevens weergeven.

Er zijn twee opties om het eindpunt te vormen:

### Via de gebruikersinterface van Cloud Manager (standaard) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Deze configuratie kan worden gedaan gebruikend een dialoogdoos op de pagina van de Details van het Milieu. Wanneer het bekijken van deze pagina voor een handel-Toegelaten programma, wordt een knoop getoond als het eindpunt momenteel niet wordt gevormd:

![CM-omgevingsinformatie](/help/commerce-cloud/assets/commerce-cmui.png)

Als u op deze knop klikt, wordt een dialoogvenster geopend:

![Eindpunt van CM-handel](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nadat het eindpunt en naar keuze een vergunningskopbal voor gefaseerde catalogussteun wordt geplaatst, wordt het eindpunt getoond op de detailpagina. Klik op het pictogram Bewerken om hetzelfde dialoogvenster te openen waarin u indien nodig het eindpunt kunt bewerken.

![CM-omgevingsinformatie](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Als Adobe I/O CLI  {#adobe-cli}

Om AEM met een handelsoplossing door middel van Adobe I/O CLI te verbinden, volg deze stappen:

1. De Adobe I/O CLI ophalen met de plug-in Cloud Manager

   Controleer de [Adobe Cloud Manager-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html) over het downloaden, instellen en gebruiken van de [Adobe I/O CLI](https://github.com/adobe/aio-cli) met de [Cloud Manager CLI-insteekmodule](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Verifieer Adobe I/O CLI met het AEM as a Cloud Service programma

3. Stel de `COMMERCE_ENDPOINT` variabele in Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Zie [CLI-documenten](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor meer informatie.

   De handel GraphQL eindpunt URL moet aan de dienst van GraphQl van de handel richten en een veilige verbinding gebruiken HTTPS. Bijvoorbeeld: `https://<yourcommercesystem>/graphql`.

4. Catalogusfuncties met status inschakelen die verificatie vereisen (optioneel)

   >[!NOTE]
   >
   >Deze functie is alleen beschikbaar in Adobe Commerce Enterprise of Cloud Edition. Zie [Op token gebaseerde verificatie](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) voor meer informatie.

   Stel de `COMMERCE_AUTH_HEADER` geheime variabele in Cloud Manager:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>U kunt alle variabelen van de Manager van de Wolk een lijst maken gebruikend het volgende bevel om te controleren tweemaal: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

U bent klaar om AEM as a Cloud Service Handel te gebruiken en kunt uw project als Manager van de Wolk opstellen.

## Opslaan en catalogi configureren {#catalog}

De CIF-invoegtoepassing en de [CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) kan op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handels opslag (of opslagmeningen, etc.) worden verbonden. Standaard wordt de CIF-invoegtoepassing geïmplementeerd met een standaardconfiguratie die verbinding maakt met de standaardstore en -catalogus van Adobe Commerce.

Deze configuratie kan voor het project als CIF Cloud Service worden aangepast config die deze stappen volgt:

1. Ga in AEM naar Tools -> Cloud Services -> CIF Configuration.

2. Selecteer de handelsconfiguratie die u wilt veranderen.

3. Open de configuratie-eigenschappen via de actiebalk.

![Configuratie CIF-Cloud Services](/help/commerce-cloud/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- GraphQL Client - selecteer de geconfigureerde GraphQL-client voor commerciële back-endcommunicatie. Deze client moet standaard blijven.
- Winkelweergave - de weergave-id van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL Proxy Path - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt van GraphQL.
  >[!NOTE]
  >
  > In de meeste instellingen is de standaardwaarde `/api/graphql` mogen niet worden gewijzigd. Alleen geavanceerde instellingen die de opgegeven GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.
- Schakel ondersteuning voor UID-catalogus in - schakel ondersteuning voor UID in in plaats van voor ID in de commerciële back-end GraphQL-aanroepen.
  >[!NOTE]
  >
  > Ondersteuning voor UID&#39;s is geïntroduceerd in Adobe Commerce 2.4.2. Laat slechts UIDs toe als uw handels achterkant een schema van GraphQL van versie 2.4.2 of later steunt.
- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus
  >[!CAUTION]
  >
  > Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. Als uw project CIF Core Components versie 2.0.0 gebruikt moet u de Steun van UID van de Catalogus toelaten en een geldige categorieUID als &quot;Identifier van de Categorie van de Hoofdmap van de Catalogus gebruiken&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Voor complexere instellingen raadpleegt u het dialoogvenster [Multi-Store-installatie voor handel](configuring/multi-store-setup.md) zelfstudie.

## Aanvullende bronnen {#additional-resources}

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Multi-Store-installatie voor handel](configuring/multi-store-setup.md)
- [Meerdere instellingen voor handelssystemen](configuring/multiple-commerce-systems-setup.md)

