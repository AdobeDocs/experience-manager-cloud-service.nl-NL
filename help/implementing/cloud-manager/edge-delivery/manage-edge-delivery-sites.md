---
title: Edge Delivery-sites beheren in Cloud Manager
description: Leer hoe u een CDN-configuratie toevoegt aan een Edge Delivery-site of een Edge Delivery-site verwijdert.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: f8135fea6cb1e43ec27a250d4664b12fa577ed4b
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Edge Delivery-site beheren in Cloud Manager {#manage-edge-delivery-sites}

Leer hoe u Edge Delivery-sites in Cloud Manager beheert door een CDN-configuratie toe te voegen aan een bestaande site. Of verwijder een Edge Delivery-site.

## Een CDN-configuratie toevoegen aan een bestaande Edge Delivery-site {#add-cdn-to-edge-delivery-site}

Zie [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen.

## De naam van een Edge Delivery-site wijzigen (#rename-edge-delivery-site)

In Adobe Cloud Manager wilt u de naam van een Edge Delivery-site mogelijk wijzigen om verschillende redenen:

* **Duidelijkheid en organisatie**: Om het doel van de plaats of zijn bijbehorende milieu (bijvoorbeeld, productie, het opvoeren) beter te beschrijven.
* **vermijdend verwarring**: Als de veelvoudige plaatsen in gebruik zijn, kan het anders noemen helpen tussen hen gemakkelijk onderscheiden, die de kans verminderen om configuraties of updates op de verkeerde plaats toe te passen.
* **Normalisatie**: Om een verenigbare noemende overeenkomst te volgen die zich op de richtlijnen van uw organisatie voor gemakkelijker beheer en controle richt.

**om een plaats van Edge Delivery anders te noemen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de naam wilt wijzigen.
Klik **anders noemen**.
   * In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren. Onder de **rubriek van de Diensten**, klik ![ het pictogram van Web-pagina&#39;s ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **de Plaatsen van Edge Delivery**.
In de de plaatslijst van Edge Delivery, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan plaats wilt anders noemen. Klik **anders noemen**.

1. In **geef de dialoogdoos van de Plaats van Edge Delivery** uit, op het **3} tekstgebied van de Naam van de Plaats {, ga de nieuwe naam van de plaats in.**

1. Klik **uitgeven**.

## Een Edge Delivery-site verwijderen {#delete-edge-delivery-site}

Als u een Edge Delivery Services-site verwijdert, worden alle gekoppelde CDN-configuraties ook verwijderd. Met deze actie wordt de verbinding tussen aangepaste domeinen en de site verbroken. Zie CDN-configuraties voor meer informatie. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**om een plaats van Edge Delivery te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. In de de plaatslijst van Edge Delivery, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan plaats u wilt verwijderen.
Klik ![ het plaatspictogram van Edge Delivery van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Schrapping**, dan klik **Schrapping** opnieuw om de verwijdering van de plaats te bevestigen.

     ![ voeg de Plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren. Onder de **rubriek van de Diensten**, klik ![ Web-pagina voor het de plaatspictogram van Edge Delivery ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **de Plaatsen van Edge Delivery**.
In de de plaatslijst van Edge Delivery, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan plaats u wilt verwijderen. Klik ![ het plaatspictogram van Edge Delivery van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Schrapping**, dan klik **Schrapping** opnieuw om de verwijdering van de plaats te bevestigen.

     ![ voeg de Plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Een Edge Delivery-site beheren tussen Helix 4 en Helix 5

Gebruik het API-eindpunt van `/program/{programId}/site/{siteId}` om een Edge Delivery-site tussen Helix 4 en Helix 5 te migreren.

CDN-configuraties voor Helix 4-websites kunnen niet automatisch worden gemigreerd naar Helix 5. Deze beperking bestaat omdat de plaatsen van de klantenproductie op Helix 4 nog kunnen lopen, terwijl hun Helix 5 versies nog in ontwikkeling zijn.

**Eerste vereisten**

* De instructie `sitename` moet al bestaan.
* Weet de juiste waarden voor `branchName` , Helix `version` en `repo` .
* Migratie wijzigt alleen `branchName`, Helix `version` en `repo` . Het veld Eigenaar kan niet worden gewijzigd.

**API formaat**

```http
PUT /api/program/{programId}/site/{siteId}
```

**de lichaamsparameters van het Verzoek**
Maakt een overschrijving voor een Edge Delivery-site om de oorsprong af te dwingen die is opgegeven in de aanvraaginstantie.

```json
{
  "sitename": "<required site name>",
  "branchName": "<git branch>",
  "version": "v4" | "v5",
  "repo": "<git repository name>"
}
```

### Voorbeeld 1: Migreren naar Helix 5

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix5",
  "branchName": "branch",
  "version": "v5",
  "repo": "my-website"
}
```

**Resultaat van Oorsprong URL**
Retourneert een Edge Delivery-site met de volgende oorspronkelijke URL:

`"origin": "branch--my-website–Teo48.aem.live"`


### Voorbeeld 2: Migreren naar Helix 4

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix4",
  "branchName": "branch",
  "version": "v4",
  "repo": "my-website"
}
```

**Resultaat van Oorsprong URL**
Retourneert een Edge Delivery-site met de volgende oorspronkelijke URL:

`"origin": "branch--my-website--Teo48.hlx.live"`

### Voorbeeld 3: Opnieuw te plaatsen site migreren naar Helix 5

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-reposless-website",
  "branchName": "main",
  "version": "v5",
  "repo": "my-reposless-website"
}
```

**Resultaat van Oorsprong URL**
Retourneert een Edge Delivery-site met de volgende oorspronkelijke URL:

`"origin": "main--my-repoless-website--Teo48.aem.live"`

## Een ondersteuningsticket vastleggen {#eds-support-ticket}

{{support-ticket}}
