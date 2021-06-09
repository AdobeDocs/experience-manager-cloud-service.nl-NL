---
title: Aan de slag met AEM Commerce als Cloud Service
description: Leer hoe te om een handel-toegelaten AEM project aan een lopende AEM als de dienstmilieu van de Wolk op te stellen. Gebruik functies van Adobe Cloud Manager en een CI/CD-pijplijn om de Venia-naslaggids te maken naar een actieve omgeving.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: de756a469f2be7b4f93d647b500cd4e8dc046342
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---

# Aan de slag met AEM Commerce als Cloud Service {#start}

Om met AEM Handel als Cloud Service te beginnen, moet uw Experience Manager Cloud Service worden voorzien van het Kader van de Integratie van de Handel (CIF) toe:voegen-on. De invoegtoepassing CIF is een extra module boven op [AEM Sites als een Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/home.html).

## Onboarding {#onboarding}

Het instappen voor AEM Handel als Cloud Service is een proces in twee stappen:

1. Krijg AEMHandel als toegelaten Cloud Service en CIF toe:voegen-on provisioned
2. Verbind AEM Handel als Cloud Service met uw handelsoplossing

De eerste instapstap wordt uitgevoerd door Adobe. Voor meer informatie over prijzen en provisioning moet u contact opnemen met uw verkoper.

Nadat u de CIF-invoegtoepassing hebt ingericht, wordt deze toegepast op alle bestaande Cloud Manager-programma&#39;s. Als u geen Cloud Manager-programma hebt, moet u een nieuw programma maken. Voor meer details, verwijs naar [Opstelling uw Programma](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

De tweede stap is zelfbediening voor elke AEM als omgeving van een Cloud Service. Er zijn sommige extra configuraties u na de aanvankelijke levering van toe:voegen-op CIF zult moeten doen.

## AEM verbinden met een Oplossing van de Handel {#magento}

Om toe:voegen-op CIF &amp; [AEM de Componenten van de Kern van CIF](https://github.com/adobe/aem-core-cif-components) met een handelsoplossing te verbinden, moet u het eindpunt GraphQL URL via een de milieuvariabele van de Manager van de Wolk verstrekken. De variabelenaam is `COMMERCE_ENDPOINT`. Er moet een beveiligde verbinding via HTTPS worden geconfigureerd.

Deze omgevingsvariabele wordt op twee plaatsen gebruikt:

- GraphQL roept van AEM aan handels achterste deel, via één of andere gemeenschappelijke cliënt GraphQl, die door de AEM componenten van de Kern van CIF en componenten van het klantenproject wordt gebruikt.
- Opstelling een proxyURL GraphQL op elke AEM milieu de variabele beschikbaar bij `/api/graphql` wordt geplaatst. Dit wordt gebruikt door de AEM handels auteurshulpmiddelen (toe:voegen-aan CIF) en cliënt-zijcomponenten CIF.

Een verschillend eindpuntURL GraphQL kan voor elke AEM als milieu van de Cloud Service worden gebruikt. Zo kunnen projecten AEM het opvoeren milieu&#39;s met handel het opvoeren systemen en AEM productiemilieu met een handelsproductiesysteem verbinden. Dat eindpunt GraphQL openbaar moet zijn, privé VPN of lokale verbindingen worden niet gesteund. Naar keuze, kan een authentificatiekopbal worden verstrekt om extra eigenschappen te gebruiken CIF die authentificatie vereisen.

De CIF-invoegtoepassing is optioneel en alleen voor Adobe Commerce Enterprise/Cloud en ondersteunt het gebruik van gefaseerde catalogusgegevens voor AEM auteurs. Dit vereist om een toestemmingstoken te vormen. Het gevormde toestemmingstoken is slechts beschikbaar en gebruikt op AEM auteursinstanties om veiligheidsredenen. AEM publicatie-instanties kunnen geen gefaseerde gegevens weergeven.

Er zijn twee opties om het eindpunt te vormen:

### Via Cloud Manager-gebruikersinterface (standaard) {#cm-ui}

Dit kan worden gedaan via een dialoogvenster op de pagina Milieu-details. Wanneer het bekijken van deze pagina voor een handel-Toegelaten programma, zal een knoop worden getoond als het eindpunt momenteel niet wordt gevormd:

![CM-omgevingsinformatie](/help/commerce-cloud/assets/commerce-cmui.png)

Als u op deze knop klikt, wordt een dialoogvenster geopend:

![Eindpunt van CM-handel](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nadat het eindpunt (naar keuze een authentificatietoken voor gefaseerde catalogussteun) wordt geplaatst, zal het eindpunt op de detailpagina worden getoond. Als u op het pictogram Bewerken klikt, wordt hetzelfde dialoogvenster geopend waarin het eindpunt indien nodig kan worden gewijzigd.

![CM-omgevingsinformatie](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Via Adobe I/O CLI {#adobe-cli}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Om AEM met een handelsoplossing via Adobe I/O CLI te verbinden, volg deze stappen:

1. De Adobe I/O CLI ophalen met de plug-in Cloud Manager

   Raadpleeg de [Adobe Cloud Manager-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) voor informatie over het downloaden, instellen en gebruiken van de [Adobe I/O CLI](https://github.com/adobe/aio-cli) met de [Cloud Manager CLI-plug-in](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Verifieer Adobe I/O CLI met de AEM als programma van de Cloud Service

3. De variabele `COMMERCE_ENDPOINT` instellen in Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Zie [CLI docs](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor meer informatie.

   De het eindpunt URL van GraphQL van de handel eindpunt moet aan de dienst van GraphQl van de handel richten en een veilige verbinding gebruiken HTTPS. Bijvoorbeeld: `https://<yourmagentosystem>/graphql`.

4. Catalogusfuncties met status inschakelen die verificatie vereisen (optioneel)

   >[!NOTE]
   >
   >Deze functie is alleen beschikbaar bij Adobe Commerce Enterprise of Cloud Edition. Zie [Op token gebaseerde verificatie](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) voor meer informatie.

   Stel de geheime variabele `COMMERCE_AUTH_HEADER` in Cloud Manager in:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>U kunt alle variabelen van de Manager van de Wolk een lijst maken gebruikend het volgende bevel om te controleren tweemaal: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Met dit, bent u klaar om AEM Handel als Cloud Service te gebruiken en uw project via de Manager van de Wolk te opstellen.

## Opslaan en catalogi configureren {#catalog}

De toe:voegen-op CIF en [CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components) kunnen op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handels (of opslagmeningen, enz.) worden verbonden.Door gebrek, wordt toe:voegen-op CIF opgesteld met een gebrek config die met de standaardopslag en de catalogus van de Handel van Adobe verbindt (Magento).

Deze configuratie kan voor het project via CIF Cloud Service config worden aangepast die deze stappen volgt:

1. Ga in AEM naar Extra -> Cloud Services -> CIF-configuratie

2. Selecteer de handelsconfiguratie u wilt veranderen

3. De configuratie-eigenschappen openen via de actiebalk

![Configuratie CIF-Cloud Services](/help/commerce-cloud/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- Cliënt GraphQL - selecteer de gevormde cliënt GraphQL voor handel achterste mededeling. Dit zou typisch bij gebrek moeten blijven.
- Winkelweergave - de weergave-id (Magento) van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL de Weg van de Volmacht - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt GraphQL.
   >[!NOTE]
   >
   > In de meeste instellingen mag de standaardwaarde `/api/graphql` niet worden gewijzigd. Alleen geavanceerde instellingen die de geleverde GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.
- De Steun van UID van de Catalogus van de inschakelen - laat steun voor UID in plaats van identiteitskaart in de handel achterste vraag GraphQL toe.
   >[!NOTE]
   >
   > Steun voor UIDs werd geïntroduceerd in de Handel van de Adobe (Magento) 2.4.2. Laat slechts dit toe als uw handels achterkant een schema GraphQL van versie 2.4.2 of later steunt.
- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus

De configuratie hierboven wordt getoond is voor verwijzing. De projecten moeten hun eigen configuraties bieden.

Zie de zelfstudie [Commerce Multi-Store Setup](configuring/multi-store-setup.md) voor meer complexe instellingen die gebruikmaken van meerdere AEM sitestructuren die zijn gecombineerd met verschillende handelscatalogi.

## Aanvullende bronnen {#additional-resources}

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Multi-Store-installatie voor handel](configuring/multi-store-setup.md)
