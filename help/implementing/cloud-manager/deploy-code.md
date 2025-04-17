---
title: Uw code implementeren
description: Leer hoe u uw code implementeert met Cloud Manager-pijpleidingen in AEM as a Cloud Service.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0712ba8918696f4300089be24cad3e4125416c02
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 0%

---


# Uw code implementeren {#deploy-your-code}

Leer hoe u uw code kunt implementeren in Production met Cloud Manager-pijpleidingen in AEM as a Cloud Service.

![ het pijpleidingsdiagram van de Productie ](./assets/configure-pipeline/production-pipeline-diagram.png)

Het opstellen van code foutloos aan Stadium en dan door aan Productie wordt gedaan door een pijpleiding van de Productie. De uitvoering van de productiepijplijn wordt opgesplitst in de volgende twee logische fasen:

1. **Plaatsing aan het milieu van het Stadium** - de code wordt gebouwd en aan het milieu van het Stadium voor geautomatiseerde functionele het testen, UI het testen, ervaringscontrole, en het Testen van de Erkenning van de Gebruiker (UAT) opgesteld.
1. **Plaatsing aan het milieu van de Productie** - Zodra de bouwstijl op Stadium wordt bevestigd, en voor bevordering aan Productie goedgekeurd, wordt het zelfde bouwstijlartefact opgesteld aan het milieu van de Productie.

_slechts steunt het Volledige pijpleidingstype van de Code van de Stapel coderingsaftasten, functie het testen, UI het testen, en ervaringscontrole._

## Implementatieproces {#deployment-process}

Alle Cloud Service-implementaties volgen een schuifproces om ervoor te zorgen dat er geen downtime optreedt. Zie [ hoe het Rollen het Werk van Plaatsingen ](/help/implementing/deploying/overview.md#how-rolling-deployments-work) om meer te leren.

>[!NOTE]
>
>De Dispatcher-cache wordt bij elke implementatie gewist. Het wordt dan &quot;opgewarmd&quot;alvorens de nieuwe publicatieknooppunten verkeer goedkeuren.

## Uw code distribueren met Cloud Manager in AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Zodra u [ uw productiePijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) met inbegrip van bewaarplaats, milieu, en het testen milieu hebt gevormd, bent u bereid om uw code op te stellen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, klik het programma waarvoor u code wilt opstellen.

1. Op de **pagina van het Overzicht**, in het gebied van call-to-action, klik **opstellen**.

   ![ CTA ](assets/deploy-code1.png)

1. Op **opstellen aan productie** pagina, klik **bouwt**.

   ![ het scherm van de Uitvoering van de Pijpleiding ](assets/deploy-code2.png)

Het bouwstijlproces stelt uw code door de volgende drie bevolen fasen op:

1. [Implementatiefase van fase](#stage-deployment)
1. [Fase van de testfase](#stage-testing)
1. [Implementatiefase productie](#production-deployment)

>[!TIP]
>
>U kunt de stappen van diverse plaatsingsprocessen herzien door logboeken te bekijken, of resultaten voor de testende criteria te herzien.

### Implementatiefase van fase {#stage-deployment}

De **fase van de Plaatsing van het 0} Stadium impliceert de volgende stappen:**

| Implementatiestap van werkgebied | Beschrijving |
| --- | --- |
| Validatie | Zorgt ervoor dat de pijpleiding wordt gevormd om de momenteel beschikbare middelen te gebruiken. bijvoorbeeld, het testen dat de gevormde tak bestaat en dat de milieu&#39;s beschikbaar zijn. |
| Testen van build en eenheid | Voert een in containers gedrukt bouwstijlproces in werking.<br> zie [ de Details van het Milieu van de Bouwstijl ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) voor details op het bouwstijlmilieu. |
| Codescannen | Evalueert de kwaliteit van uw toepassingscode.<br> zie [ het Testen van de Kwaliteit van de Code ](/help/implementing/cloud-manager/code-quality-testing.md) voor details op het het testen proces. |
| Afbeeldingen samenstellen | Dit proces zet inhoud en de pakketten van Dispatcher van de stap van de Bouwstijl in de beelden van de Docker om. Het produceert ook configuraties Kubernetes die op die pakketten worden gebaseerd. |
| Distribueren naar werkgebied | Het beeld wordt opgesteld aan het opvoeren milieu in voorbereiding op het [ het testen stadium van het Stadium ](#stage-testing). |

![ Plaatsing van het Stadium ](assets/stage-deployment.png)

### Fase van de testfase {#stage-testing}

De **testende 1} fase van het Stadium {impliceert de volgende stappen:**

| Teststap werkgebied | Beschrijving |
| --- | --- |
| Functioneel testen van producten | De pijpleiding van Cloud Manager voert tests uit die tegen het werkgebiedmilieu lopen.<br> zie ook [ Functionele het Testen van het Product ](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing). |
| Aangepaste functionele tests | Deze stap in de pijplijn wordt altijd uitgevoerd en kan niet worden overgeslagen. Als de build geen test JAR produceert, slaagt de test automatisch.<br> zie ook [ het Functionele Testen van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing). |
| Aangepaste UI-tests | Een optionele functie waarmee automatisch UI-tests worden uitgevoerd die voor aangepaste toepassingen zijn gemaakt.<br> de tests UI zijn op selenium-Gebaseerd en verpakt in een beeld van het Docker om flexibiliteit in taal en kaders aan te bieden. Met deze methode kunt u Java en Maven, Node en WebDriver.io of een op Selenium gebaseerd framework of technologie gebruiken.<br> zie ook [ het Testen UI van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing). |
| Experience Audit | Deze stap in de pijplijn wordt altijd uitgevoerd en kan niet worden overgeslagen. Aangezien een productiepijplijn wordt uitgevoerd, is een stap van de ervaringscontrole inbegrepen na douane functionele het testen die de controles in werking stelt.<ul><li>De pagina&#39;s die worden gevormd worden voorgelegd aan de dienst en geëvalueerd.</li><li>De resultaten zijn informatief en tonen de scores en de verandering tussen de huidige en vorige scores.</li><li>Deze insight is nuttig om te bepalen of er een regressie is die met de huidige plaatsing wordt geïntroduceerd.</li></ul>Zie [ Begrijpend de resultaten van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md).</li></ul> |

![ het Testen van het Stadium ](assets/stage-testing.png)

### Implementatiefase productie {#production-deployment}

Het implementatieproces voor productietopologieën verschilt enigszins om de impact op bezoekers van een AEM-site tot een minimum te beperken.

Productieimplementaties volgen doorgaans dezelfde stappen als eerder beschreven, maar op een voortschrijdende manier. Deze stappen omvatten het volgende:

1. Implementeer AEM-pakketten naar auteur.
1. Koppel `dispatcher1` los van het taakverdelingsmechanisme.
1. Gebruik AEM-pakketten in `publish1` en Dispatcher-pakketten in `dispatcher1` om de Dispatcher-cache te leegmaken.
1. Plaats `dispatcher1` weer in het taakverdelingsmechanisme.
1. Koppel `dispatcher2` los van het taakverdelingsmechanisme wanneer `dispatcher1` weer in service is.
1. Gebruik AEM-pakketten in `publish2` en Dispatcher-pakketten in `dispatcher2` om de Dispatcher-cache te leegmaken.
1. Plaats `dispatcher2` weer in het taakverdelingsmechanisme.

Dit proces gaat verder tot de plaatsing alle uitgevers en Dispatchers in de topologie heeft bereikt.

![ De fase van de Plaatsing van de Productie ](assets/production-deployment.png)

## Tijdslimieten tijdens een implementatie {#timeouts}

De volgende stappen time-out als ze wachten op feedback van gebruikers tijdens een implementatie:

| Stap | Time-out |
|--- |--- |
| Testen van de codekwaliteit | 14 dagen |
| Beveiligingstests | 14 dagen |
| Prestatietesten | 14 dagen |
| Goedkeuringsaanvraag | 14 dagen |
| Implementatie van planningsproductie | 14 dagen |
| CSE-ondersteuning | 14 dagen |

## Een productieimplementatie opnieuw uitvoeren {#reexecute-deployment}

In zeldzame gevallen kunnen de stappen van de productielocatie om voorbijgaande redenen ontbreken. In dergelijke gevallen wordt heruitvoering van de productieleidingsstap ondersteund zolang de productieleidingsstap is voltooid, ongeacht het type voltooiing (bijvoorbeeld geannuleerd of mislukt). De heruitvoering leidt tot een nieuwe uitvoering gebruikend de zelfde pijpleiding die uit de volgende drie stappen bestaat:

1. **Bevestiging** - de zelfde bevestiging die tijdens een normale pijpleidingsuitvoering voorkomt.
1. **bouwt** - in de context van een heruitvoering, kopieert de bouwstijlstap artefacten en voert eigenlijk geen nieuw bouwstijlproces uit.
1. **plaatsing van de Productie** - gebruikt de zelfde configuratie en de opties zoals de stap van de productieplaatsing in een normale pijpleidingsuitvoering.

In dergelijke omstandigheden waar een heruitvoering mogelijk is, verstrekt de pagina van de de statuspagina van de productiepijpleiding **re-execute** optie naast de gebruikelijke **Download bouwt logboek** optie.

![ re-execute optie in het venster van het pijpleidingsoverzicht ](assets/re-execute.png)

>[!NOTE]
>
>In een heruitvoering, wordt de bouwstijlstap geëtiketteerd in UI om erop te wijzen dat het artefacten kopieert, niet re-bouwt.

### Gebruiksnotities {#usage-notes}

* Het opnieuw uitvoeren van de stap van de productieplaatsing is slechts beschikbaar voor de laatste uitvoering.
* Heruitvoering is niet beschikbaar voor het uitvoeren van push-updates. Als de laatste uitvoering een uitvoering van een push-update is, is het niet mogelijk deze opnieuw uit te voeren.
* Als de laatste uitvoering is mislukt op een willekeurig punt vóór de stap voor de implementatie van de productie, is het niet mogelijk de productie opnieuw uit te voeren.

### API opnieuw uitvoeren {#reexecute-API}

Naast het zijn beschikbaar in UI, kunt u [ Cloud Manager API ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) gebruiken om wederuitvoeringen teweeg te brengen en uitvoeringen te identificeren die als re-uitvoeringen werden teweeggebracht.

#### Een nieuwe uitvoering activeren {#reexecute-deployment-api}

Om een re-uitvoering teweeg te brengen, doe een verzoek van PUT aan de Verbinding van de HAL `https://ns.adobe.com/adobecloud/rel/pipeline/reExecute` op de productie stapstaat opstelt.

* Als deze koppeling aanwezig is, kan de uitvoering vanaf die stap opnieuw worden gestart.
* Als dit niet het geval is, kan de uitvoering niet vanaf die stap opnieuw worden gestart.

Deze verbinding is slechts beschikbaar voor de productie stelt stap op.

```JavaScript
 {
  "_links": {
    "https://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

De syntaxis van de href-waarde van de HAL-koppeling is slechts een voorbeeld. De werkelijke waarde moet altijd worden gelezen van de HAL-koppeling en niet worden gegenereerd.

Het voorleggen van een verzoek van PUT aan dit eindpunt resulteert in een 201 reactie als succesvol, en het antwoordlichaam is de vertegenwoordiging van de nieuwe uitvoering. Deze workflow lijkt op het starten van een normale uitvoering via de API.

#### Identificeer een wederuitvoeringsuitvoering {#identify-reexecution}

Het systeem heruitvoeringen identificeert door het veld `trigger` in te stellen op de waarde `RE_EXECUTE` .
