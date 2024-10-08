---
title: Uw code implementeren
description: Leer hoe u uw code implementeert met Cloud Manager-pijpleidingen in AEM as a Cloud Service.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cfaa3be31195929b80310610120a779a20537c61
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 0%

---


# Uw code implementeren {#deploy-your-code}

Leer hoe u uw code kunt implementeren in Production met Cloud Manager-pijpleidingen in AEM as a Cloud Service.

![ het pijpleidingsdiagram van de Productie ](./assets/configure-pipeline/production-pipeline-diagram.png)

Het naadloos opstellen van code aan Stadium en dan door aan Productie wordt gedaan via een pijpleiding van de Productie. De uitvoering van de productiepijplijn wordt opgedeeld in twee logische fasen.

1. Implementatie in de Stage-omgeving
   * De code wordt gebouwd en opgesteld aan het milieu van het Stadium voor geautomatiseerde functionele tests, het testen UI, ervaringscontrole, en het testen van de gebruikersaanvaarding (UAT).
1. Implementatie in productieomgeving
   * Zodra de bouw op Stadium wordt bevestigd, en voor bevordering aan Productie goedgekeurd, wordt het zelfde bouwstijlfeit opgesteld aan het milieu van de Productie.

_slechts steunt het Volledige pijpleidingstype van de Code van de Stapel coderingsaftasten, functie het testen, UI het testen, en ervaringscontrole._

## Je code implementeren met Cloud Manager in AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Zodra u [ uw productiePijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) met inbegrip van bewaarplaats, milieu, en het testen milieu hebt gevormd, bent u bereid om uw code op te stellen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, ontvang of klik het programma waarvoor u code wilt opstellen.

1. Klik **opstellen** van vraag-aan-actie op het **scherm van het Overzicht** om het plaatsingsproces te beginnen.

   ![ CTA ](assets/deploy-code1.png)

1. De **het schermvertoningen van de Uitvoering van de Pijpleiding**. Klik **bouwen** om het proces te beginnen.

   ![ het scherm van de Uitvoering van de Pijpleiding ](assets/deploy-code2.png)

Het bouwstijlproces stelt uw code door drie fasen op.

1. [Werkgebiedimplementatie](#stage-deployment)
1. [Werkgebiedtests](#stage-testing)
1. [Implementatie van productie](#production-deployment)

>[!TIP]
>
>U kunt de stappen van diverse plaatsingsprocessen herzien door logboeken, of het herzien van resultaten, voor de testende criteria te bekijken.

## Implementatiefase werkgebied {#stage-deployment}

De **fase van de Plaatsing van het Stadium**. Deze stappen worden uitgevoerd.

* **Bevestiging** - Deze stap zorgt ervoor dat de pijpleiding wordt gevormd om de momenteel beschikbare middelen te gebruiken. bijvoorbeeld, het testen dat de gevormde tak bestaat en dat de milieu&#39;s beschikbaar zijn.
* **Bouwstijl &amp; het Testen van de Eenheid** - Deze stap stelt een inperkt bouwstijlproces in werking.
   * Zie [ de Details van het Milieu van de Bouwstijl ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) voor details op het bouwstijlmilieu.
* **Scannen van de Code** - Deze stap evalueert de kwaliteit van uw toepassingscode.
   * Zie [ het Testen van de Kwaliteit van de Code ](/help/implementing/cloud-manager/code-quality-testing.md) voor details op het het testen proces.
* **bouwt Beelden** - Dit proces is verantwoordelijk voor het transformeren van de inhoud en de dispatcherpakketten die door de bouwstijlstap in de beelden van het Docker en configuraties Kubernetes worden geproduceerd.
* **stelt aan Stadium** op - het beeld wordt opgesteld aan het het opvoeren milieu in voorbereiding op het [ Stadium testende stadium ](#stage-testing).

![ Plaatsing van het Stadium ](assets/stage-deployment.png)

## Testfase werkgebied {#stage-testing}

De **testende 1} fase van het Stadium {impliceert deze stappen.**

* **Functionele het Testen van het Product** - de pijpleiding van Cloud Manager voert tests uit die tegen het werkgebiedmilieu lopen.
   * Zie [ Functionele het Testen van het Product ](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) voor meer details.

* **het Functionele Testen van de Douane** - Deze stap in de pijpleiding wordt altijd uitgevoerd en kan niet worden overgeslagen. Als er geen test-JAR wordt geproduceerd door de constructie, slaagt de test standaard.
   * Zie [ het Functionele Testen van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) voor meer details.

* **het Testen van de Douane UI** - Deze stap is een facultatieve eigenschap die de tests van UI automatisch in werking stellen die voor douanetoepassingen worden gecreeerd.
   * De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd).
   * Zie [ het Testen van UI van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) voor meer details.

* **Controle van de Ervaring** - Deze stap in de pijpleiding wordt altijd uitgevoerd en kan niet worden overgeslagen. Aangezien een productiepijplijn wordt uitgevoerd, is een stap van de ervaringscontrole inbegrepen na douane functionele het testen die de controles zal in werking stellen.
   * De pagina&#39;s die worden gevormd worden voorgelegd aan de dienst en geëvalueerd.
   * De resultaten zijn informatief en tonen de scores en de verandering tussen de huidige en vorige scores.
   * Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing wordt geïntroduceerd.
   * Zie [ Begrijpend de resultaten van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md) voor meer details.

![ het Testen van het Stadium ](assets/stage-testing.png)

## Implementatiefase productie {#production-deployment}

Het proces voor het opstellen aan productietopologieën verschilt lichtjes om impactbezoekers aan een AEM plaats te minimaliseren.

Productieimplementaties volgen doorgaans dezelfde stappen als eerder beschreven, maar op een voortschrijdende manier.

1. Implementeer AEM pakketten naar de auteur.
1. Dispatcher1 loskoppelen van het taakverdelingsmechanisme.
1. Implementeer AEM pakketten om te publiceren1 en het verzenderpakket om de verzendingscache van Dispatcher1 leeg te maken.
1. Plaats dispatcher1 terug in het taakverdelingsmechanisme.
1. Als dispatcher1 weer in bedrijf is, koppelt u dispatcher2 af van het taakverdelingsmechanisme.
1. Implementeer AEM pakketten om te publiceren2 en het verzenderpakket om de verzendingscache van Dispatcher2 leeg te maken.
1. Plaats dispatcher2 terug in het taakverdelingsmechanisme.

Dit proces gaat verder tot de plaatsing alle uitgevers en verzenders in de topologie heeft bereikt.

![ De fase van de Plaatsing van de Productie ](assets/production-deployment.png)

## Tijdstippen {#timeouts}

Er wordt een time-out toegepast in de volgende stappen als er op feedback van gebruikers wordt gewacht:

| Stap | Time-out |
|--- |--- |
| Testen van de codekwaliteit | 14 dagen |
| Beveiligingstests | 14 dagen |
| Prestatietesten | 14 dagen |
| Goedkeuringsaanvraag | 14 dagen |
| Implementatie van planningsproductie | 14 dagen |
| CSE-ondersteuning | 14 dagen |

## Implementatieproces {#deployment-process}

Alle plaatsingen van de Cloud Service volgen een het rollen proces om nul onderbreking te verzekeren. Zie [ hoe het Rollen het Werk van Plaatsingen ](/help/implementing/deploying/overview.md#how-rolling-deployments-work) om meer te leren.

>[!NOTE]
>
>De Dispatcher-cache wordt bij elke implementatie gewist. Het wordt dan opgewarmd alvorens de nieuwe publicatieknooppunten verkeer goedkeuren.

## Het opnieuw uitvoeren van een Plaatsing van de Productie {#reexecute-deployment}

In zeldzame gevallen kunnen de stappen van de productielocatie om voorbijgaande redenen ontbreken. In dergelijke gevallen wordt heruitvoering van de productieleidingsstap ondersteund zolang de productieleidingsstap is voltooid, ongeacht het type voltooiing (bijvoorbeeld geannuleerd of mislukt). De heruitvoering leidt tot een nieuwe uitvoering gebruikend de zelfde pijpleiding die uit drie stappen bestaat.

1. Bevestig stap - dit is hoofdzakelijk de zelfde bevestiging die tijdens een normale pijpleidingsuitvoering voorkomt.
1. De bouwstijlstap - in de context van een heruitvoering, kopieert de bouwstijlstap artefacten en voert eigenlijk geen nieuw bouwstijlproces uit.
1. De stap van de productieleiding - dit gebruikt de zelfde configuratie en de opties zoals de stap van de productieleiding in een normale pijpleidingsuitvoering.

In dergelijke omstandigheden waar een heruitvoering mogelijk is, verstrekt de pagina van de de statuspagina van de productiepijpleiding **re-execute** optie naast de gebruikelijke **Download bouwt logboek** optie.

![ re-execute optie in het venster van het pijpleidingsoverzicht ](assets/re-execute.png)

>[!NOTE]
>
>In een heruitvoering, wordt de bouwstijlstap geëtiketteerd in UI om erop te wijzen dat het artefacten kopieert, niet re-bouwt.

### Beperkingen {#limitations}

* Het opnieuw uitvoeren van de stap van de productieplaatsing zal slechts voor de laatste uitvoering beschikbaar zijn.
* Heruitvoering is niet beschikbaar voor het uitvoeren van push-updates.
   * Als de laatste uitvoering een uitvoering van een push-update is, is het niet mogelijk deze opnieuw uit te voeren.
* Als de laatste uitvoering is mislukt op een willekeurig punt vóór de stap voor de implementatie van de productie, is het niet mogelijk de productie opnieuw uit te voeren.

### API opnieuw uitvoeren {#reexecute-API}

Naast het zijn beschikbaar in UI, kunt u [ Cloud Manager API ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) gebruiken om wederuitvoeringen teweeg te brengen en uitvoeringen te identificeren die als re-uitvoeringen werden teweeggebracht.

#### Een nieuwe uitvoering activeren {#reexecute-deployment-api}

Om een re-uitvoering teweeg te brengen, doe een verzoek van de PUT aan de Verbinding van de HAL `https://ns.adobe.com/adobecloud/rel/pipeline/reExecute` op de productie opstelt stapstaat.

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

Het voorleggen van een verzoek van de PUT aan dit eindpunt resulteert in een 201 reactie als succesvol, en het antwoordlichaam is de vertegenwoordiging van de nieuwe uitvoering. Dit is vergelijkbaar met het starten van een normale uitvoering via de API.

#### Een opnieuw uitgevoerde uitvoering identificeren {#identify-reexecution}

Herhaalde uitvoeringen kunnen worden geïdentificeerd door de waarde `RE_EXECUTE` in het veld `trigger` .
