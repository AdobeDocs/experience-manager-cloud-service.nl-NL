---
title: Aan de slag met AEM Commerce as a Cloud Service
description: Leer hoe te om een Adobe Experience Manager (AEM) handelproject op te stellen, gebruikend Adobe Cloud Manager, een CI/CD pijpleiding, en de verwijzingswinkel van Venia.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# Aan de slag met AEM Commerce as a Cloud Service {#start}

Om aan de slag te gaan met Adobe Experience Manager (AEM) Commerce as a Cloud Service, moet uw Experience Manager Cloud Service voorzien zijn van de Commerce integration framework (CIF) add-on. CIF toe:voegen-op is een extra module bovenop [ as a Cloud Service van AEM Sites ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/home.html).

## Onboarding {#onboarding}

Het instappen voor AEM Commerce as a Cloud Service is een proces in twee stappen:

1. AEM Commerce as a Cloud Service en de CIF add-on ingericht krijgen
2. Verbind AEM Commerce as a Cloud Service met uw handelsoplossing

De eerste instapstap wordt uitgevoerd door Adobe. Voor meer informatie over prijzen en provisioning moet u contact opnemen met uw verkoper.

Nadat u de CIF hebt ingericht, wordt deze toegepast op alle bestaande Cloud Manager-programma&#39;s. Als u geen Cloud Manager-programma hebt, moet u er een maken. Voor meer details, zie [ Opstelling uw Programma ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html).

De tweede stap is zelfbediening voor elke AEM as a Cloud Service-omgeving. Er zijn sommige extra configuraties die u na de aanvankelijke levering van CIF toe:voegen-op moet doen.

## Verbinding maken AEM met een Commerce-oplossing {#solution}

Om CIF toe:voegen-op &amp; [ AEM de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components) met een handelsoplossing te verbinden, moet u het eindpunt URL van GraphQL als milieuvariabele van Cloud Manager verstrekken. De variabelenaam is `COMMERCE_ENDPOINT` . Er moet een beveiligde verbinding via HTTPS worden geconfigureerd.

Deze omgevingsvariabele wordt op twee plaatsen gebruikt:

- De vraag van GraphQL van AEM aan handelsafstand, als één of andere gemeenschappelijke cliënt GraphQl, die door de AEM wordt gebruikt van de Componenten van de Kern van de CIF en componenten van het klantenproject.
- Stel een GraphQL-proxy-URL in voor elke AEM omgeving waarin de variabele beschikbaar is op `/api/graphql` . Deze URL wordt gebruikt door de AEM handels auteurshulpmiddelen (CIF toe:voegen-aan) en CIF cliënt-zijcomponenten.

Voor elke AEM as a Cloud Service-omgeving kan een andere URL voor het eindpunt van GraphQL worden gebruikt. Zo kunnen projecten AEM het opvoeren milieu&#39;s met handel het opvoeren systemen en AEM productiemilieu met een handelsproductiesysteem verbinden. Dat het eindpunt van GraphQL openbaar moet zijn, privé VPN of lokale verbindingen worden niet gesteund. Naar keuze, kan een authentificatiekopbal worden verstrekt om extra CIF eigenschappen te gebruiken die authentificatie vereisen.

De CIF add-on (optioneel en alleen voor Adobe Commerce Enterprise/Cloud) ondersteunt het gebruik van gefaseerde catalogusgegevens voor AEM auteurs. Deze gegevens vereisen dat u een vergunningskopbal vormt. Deze koptekst is alleen beschikbaar en wordt uit veiligheidsoverwegingen gebruikt bij AEM instanties Auteur. AEM Publish-instanties kunnen geen gefaseerde gegevens weergeven.

Er zijn twee opties om het eindpunt te vormen:

### Als gebruikersinterface van Cloud Manager (standaard) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Deze configuratie kan worden gedaan gebruikend een dialoogdoos op de pagina van de Details van het Milieu. Wanneer het bekijken van deze pagina voor een Commerce-Toegelaten programma, wordt een knoop getoond als het eindpunt momenteel niet wordt gevormd:

![ Informatie van het Milieu van CM ](/help/commerce-cloud/assets/commerce-cmui.png)

Als u op deze knop klikt, wordt een dialoogvenster geopend:

![ Commerce Eindpunt van CM ](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nadat het eindpunt en naar keuze een vergunningskopbal voor gefaseerde catalogussteun wordt geplaatst, wordt het eindpunt getoond op de detailpagina. Klik op het pictogram Bewerken om hetzelfde dialoogvenster te openen waarin u indien nodig het eindpunt kunt bewerken.

![ Informatie van het Milieu van CM ](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Als Adobe I/O CLI  {#adobe-cli}

Om AEM met een handelsoplossing door middel van Adobe I/O CLI te verbinden, volg deze stappen:

1. De Adobe I/O CLI met de Cloud Manager-insteekmodule

   Controleer de [ documentatie van Cloud Manager van de Adobe ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html) op hoe te om, opstelling te downloaden, en de [ Adobe I/O CLI ](https://github.com/adobe/aio-cli) met de [ stop van Cloud Manager CLI ](https://github.com/adobe/aio-cli-plugin-cloudmanager) te gebruiken.

2. Verifieer Adobe I/O CLI met het programma van AEM as a Cloud Service

3. De variabele `COMMERCE_ENDPOINT` instellen in Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Zie [ CLI documenten ](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor details.

   De handel GraphQL eindpunt URL moet aan de dienst van GraphQl van de handel richten en een veilige verbinding gebruiken HTTPS. Bijvoorbeeld: `https://<yourcommercesystem>/graphql` .

4. Catalogusfuncties met status inschakelen die verificatie vereisen (optioneel)

   >[!NOTE]
   >
   >Deze functie is alleen beschikbaar in Adobe Commerce Enterprise of Cloud Edition. Zie [ op token-gebaseerde authentificatie ](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) voor details.

   Stel de geheim variabele `COMMERCE_AUTH_HEADER` in Cloud Manager in:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>U kunt alle Cloud Manager-variabelen weergeven met de volgende opdracht voor dubbele controle: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

U kunt AEM Commerce as a Cloud Service gebruiken en uw project implementeren via Cloud Manager.

## Opslaan en catalogi configureren {#catalog}

De CIF toe:voegen-op en [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components) kunnen op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handels (of opslagmeningen, etc. worden verbonden). Standaard wordt de CIF add-on geïmplementeerd met een standaardconfiguratie die verbinding maakt met de standaardstore en -catalogus van Adobe Commerce.

Deze configuratie kan voor het project als CIF Cloud Service worden aangepast config die deze stappen volgt:

1. Ga in AEM naar Gereedschappen > Cloud Servicen > Configuratie CIF.

2. Selecteer de handelsconfiguratie die u wilt veranderen.

3. Open de configuratie-eigenschappen via de actiebalk.

![ CIF de Configuratie van Cloud Servicen ](/help/commerce-cloud/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- GraphQL Client - selecteer de geconfigureerde GraphQL-client voor commerciële back-endcommunicatie. Deze client moet standaard blijven.
- Winkelweergave - de weergave-id van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL Proxy Path - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt van GraphQL.
  >[!NOTE]
  >
  > In de meeste instellingen mag de standaardwaarde `/api/graphql` niet worden gewijzigd. Alleen geavanceerde instellingen die de opgegeven GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.
- Schakel ondersteuning voor UID-catalogus in - schakel ondersteuning voor UID in in plaats van voor ID in de commerciële back-end GraphQL-aanroepen.
  >[!NOTE]
  >
  > Ondersteuning voor UID&#39;s is geïntroduceerd in Adobe Commerce 2.4.2. Laat slechts UIDs toe als uw handels achterkant een schema van GraphQL van versie 2.4.2 of later steunt.
- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus
  >[!CAUTION]
  >
  > Vanaf CIF Core Components versie 2.0.0 is de ondersteuning voor `id` verwijderd en vervangen door `uid` . Als uw project CIF versie 2.0.0 van de Componenten van de Kern gebruikt moet u de Steun van UID van de Catalogus toelaten en een geldige categorieUID als &quot;Identifier van de Categorie van de Hoofdstad van de Catalogus gebruiken&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Voor complexere montages, die veelvoudige AEM plaatsstructuren gebruiken die met verschillende handelscatalogi worden gecombineerd zien het ](configuring/multi-store-setup.md) leerprogramma van de Opstelling van de multi-Opslag van Commerce 0} {.[

## Aanvullende bronnen {#additional-resources}

- [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store ](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce Multi-Store Setup](configuring/multi-store-setup.md)
- [Meerdere Commerce Systems-instellingen](configuring/multiple-commerce-systems-setup.md)

