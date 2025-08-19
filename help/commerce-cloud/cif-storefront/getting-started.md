---
title: Aan de slag met AEM Commerce as a Cloud Service
description: Leer hoe te om een de handelproject van Adobe Experience Manager (AEM) op te stellen, gebruikend Adobe Cloud Manager, een pijpleiding CI/CD, en de verwijzingswinkel van Venia.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Experience Manager as a Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
role: Admin
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---


# Aan de slag met AEM Commerce as a Cloud Service {#start}

Als u aan de slag wilt met Adobe Experience Manager (AEM) Commerce as a Cloud Service, moet uw Experience Manager Cloud Service zijn ingericht met de invoegtoepassing Commerce integration framework (CIF). CIF toe:voegen-op is een extra module bovenop [ AEM Sites as a Cloud Service.](/help/sites-cloud/sites-cloud-changes.md)

>[!TIP]
>
>**hebt u Edge Delivery Services overwogen?**
>
>Edge Delivery Services is de Adobe-voorkeursoplossing voor het maken van een winkel. Gelieve te zien het document [ Inleiding en overzicht ](/help/commerce-cloud/introduction.md) voor meer informatie.

## Onboarding {#onboarding}

De instapprocedure voor AEM Commerce as a Cloud Service bestaat uit twee stappen:

1. AEM Commerce as a Cloud Service ingeschakeld en de CIF add-on ingericht
1. Connect AEM Commerce as a Cloud Service met uw handelsoplossing

De eerste instapstap wordt uitgevoerd door Adobe. Voor meer informatie over prijzen en provisioning moet u contact opnemen met uw verkoper.

Nadat u de invoegtoepassing CIF hebt ingericht, wordt deze toegepast op alle bestaande Cloud Manager-programma&#39;s. Als u geen Cloud Manager-programma hebt, moet u er een maken. Voor meer details, zie [ Opstelling uw Programma.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html)

De tweede stap is zelfbediening voor elke AEM as a Cloud Service-omgeving. Er zijn enkele aanvullende configuraties die u moet uitvoeren na de eerste provisioning van de CIF-invoegtoepassing.

## AEM verbinden met een Commerce-oplossing {#solution}

Om CIF toe:voegen-op &amp; de [ componenten van de Kern van AEM CIF ](https://github.com/adobe/aem-core-cif-components) met een handelsoplossing te verbinden, moet u het eindpunt URL van GraphQL als milieuvariabele van Cloud Manager verstrekken. De variabelenaam is `COMMERCE_ENDPOINT` . Er moet een beveiligde verbinding via HTTPS worden geconfigureerd.

Deze omgevingsvariabele wordt op twee plaatsen gebruikt:

* GraphQL roept van AEM aan handel achterkant, als één of andere gemeenschappelijke cliënt GraphQl, die door de Componenten van de Kern van AEM CIF en de componenten van het klantenproject wordt gebruikt.
* Stel een GraphQL-proxy-URL in voor elke AEM-omgeving waarin de variabele beschikbaar is op `/api/graphql` . Deze URL wordt gebruikt door de AEM-gereedschappen voor het maken van handelsontwerpen (CIF add-on) en CIF-clientcomponenten.

Voor elke AEM as a Cloud Service-omgeving kan een andere URL voor het eindpunt van GraphQL worden gebruikt. Op die manier kunnen projecten AEM-testomgevingen verbinden met staging-systemen voor handel en AEM-productieomgeving met een handelsproductiesysteem. Dat het eindpunt van GraphQL openbaar moet zijn, privé VPN of lokale verbindingen worden niet gesteund. Naar keuze, kan een authentificatiekopbal worden verstrekt om extra eigenschappen van CIF te gebruiken die authentificatie vereisen.

De invoegtoepassing CIF ondersteunt optioneel en alleen voor Adobe Commerce Enterprise / Cloud het gebruik van gefaseerde catalogusgegevens voor AEM-auteurs. Deze gegevens vereisen dat u een vergunningskopbal vormt. Deze header is alleen beschikbaar en wordt uit veiligheidsoverwegingen gebruikt op AEM Author-instanties. In AEM-publicatie-instanties kunnen geen gefaseerde gegevens worden weergegeven.

Er zijn twee opties om het eindpunt te vormen:

### Als gebruikersinterface van Cloud Manager (standaard) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Deze configuratie kan worden gedaan gebruikend een dialoogdoos op de pagina van de Details van het Milieu. Wanneer het bekijken van deze pagina voor een Commerce-Toegelaten programma, wordt een knoop getoond als het eindpunt momenteel niet wordt gevormd:

![ Informatie van het Milieu van CM ](/help/commerce-cloud/cif-storefront/assets/commerce-cmui.png)

Als u op deze knop klikt, wordt een dialoogvenster geopend:

![ Commerce Eindpunt van CM ](/help/commerce-cloud/cif-storefront/assets/commerce-cm-endpoint.png)

Nadat het eindpunt en naar keuze een vergunningskopbal voor gefaseerde catalogussteun wordt geplaatst, wordt het eindpunt getoond op de detailpagina. Klik op het pictogram Bewerken om hetzelfde dialoogvenster te openen waarin u indien nodig het eindpunt kunt bewerken.

![ Informatie van het Milieu van CM ](/help/commerce-cloud/cif-storefront/assets/commerce-cmui-done.png)

### Als Adobe I/O CLI  {#adobe-cli}

Ga als volgt te werk als u AEM via Adobe I/O CLI wilt verbinden met een handelsoplossing:

1. Kies voor de Adobe I/O CLI met de Cloud Manager-insteekmodule.

   * Controleer de [ documentatie van Adobe Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html) op hoe te om, opstelling te downloaden, en [ Adobe I/O CLI ](https://github.com/adobe/aio-cli) met de [ stop van Cloud Manager CLI te gebruiken.](https://github.com/adobe/aio-cli-plugin-cloudmanager)

1. Verifieer Adobe I/O CLI met het programma van AEM as a Cloud Service.

1. Stel de variabele `COMMERCE_ENDPOINT` in Cloud Manager in.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   * Zie [ CLI documenten ](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) voor details.

   * De handel GraphQL eindpunt URL moet aan de dienst van GraphQl van de handel richten en een veilige verbinding gebruiken HTTPS. Bijvoorbeeld: `https://<yourcommercesystem>/graphql` .

1. Schakel nog niet actieve catalogusfuncties in waarvoor verificatie vereist is (optioneel).

   >[!NOTE]
   >
   >Deze functie is alleen beschikbaar in Adobe Commerce Enterprise of Cloud Edition. Zie [ op token-gebaseerde authentificatie ](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) voor details.

   * Stel de geheim variabele `COMMERCE_AUTH_HEADER` in Cloud Manager in:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>U kunt alle Cloud Manager-variabelen weergeven met de volgende opdracht voor dubbele controle: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

U kunt AEM Commerce as a Cloud Service gebruiken en uw project implementeren via Cloud Manager.

## Opslaan en catalogi configureren {#catalog}

CIF toe:voegen-op en de [ Componenten van de Kern van CIF ](https://github.com/adobe/aem-core-cif-components) kunnen op veelvoudige de plaatsstructuren worden gebruikt van AEM die met verschillende handelshoudingen (of opslagmeningen, etc. worden verbonden). Standaard wordt de invoegtoepassing CIF geïmplementeerd met een standaardconfiguratie die verbinding maakt met de standaardwinkel en catalogus van Adobe Commerce.

Deze configuratie kan voor het project door CIF Cloud Service worden aangepast config die deze stappen volgt:

1. Ga in AEM naar Extra > Cloud Services > CIF Configuration.

1. Selecteer de handelsconfiguratie die u wilt veranderen.

1. Open de configuratie-eigenschappen via de actiebalk.

![ Configuratie van de Diensten van de Wolk van CIF ](/help/commerce-cloud/cif-storefront/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

* GraphQL Client - selecteer de geconfigureerde GraphQL-client voor commerciële back-endcommunicatie. Deze client moet standaard blijven.
* Winkelweergave - de weergave-id van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
* GraphQL Proxy Path - de Volmacht van GraphQL van de weg URL in AEM gebruikt aan volmachtsverzoeken aan het commerciële achterste eindpunt van GraphQL.
  >[!NOTE]
  >
  > In de meeste instellingen mag de standaardwaarde `/api/graphql` niet worden gewijzigd. Alleen geavanceerde instellingen die de opgegeven GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.
* Ondersteuning voor Catalog UID inschakelen - ondersteuning voor UID inschakelen in plaats van ID in de commerciële back-end GraphQL-aanroepen.
  >[!NOTE]
  >
  > Ondersteuning voor UID&#39;s is geïntroduceerd in Adobe Commerce 2.4.2. Laat slechts UIDs toe als uw handels achterkant een schema van GraphQL van versie 2.4.2 of later steunt.
* Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus
  >[!CAUTION]
  >
  > Vanaf CIF Core Components versie 2.0.0 is de ondersteuning voor `id` verwijderd en vervangen door `uid` . Als uw project CIF Core Components versie 2.0.0 gebruikt, moet u de Steun van UID van de Catalogus toelaten en een geldige categorie UID gebruiken als &quot;Identifier van de Hoofdcategorie van de Catalogus&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Voor complexere montages, die veelvoudige de plaatsstructuren gebruiken van AEM die met verschillende handelscatalogi worden gecombineerd zien het [ leerprogramma van de Opstelling van de multi-Opslag van 0&rbrace; Commerce &lbrace;.](/help/commerce-cloud/cif-storefront/configuring/multi-store-setup.md)

## Aanvullende bronnen {#additional-resources}

* [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype)
* [ de Opslag van de Verwijzing van AEM Venia ](https://github.com/adobe/aem-cif-guides-venia)
* [Commerce Multi-Store Setup](/help/commerce-cloud/cif-storefront/configuring/multi-store-setup.md)
* [Meerdere Commerce Systems-instellingen](/help/commerce-cloud/cif-storefront/configuring/multiple-commerce-systems-setup.md)
