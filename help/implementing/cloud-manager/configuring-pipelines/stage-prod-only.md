---
title: Splitsen van alleen-werkgebied- en alleen-productie-pijplijnen
description: Leer hoe u het opvoeren en productielokaties kunt verdelen gebruikend specifieke pijpleidingen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#staging-production-only-pipelines"
hide: true
hidefromtoc: true
index: false
exl-id: 7d76a87c-122c-4c4d-8071-957bef4c9cf1
source-git-commit: 51318172b826eb81dff86b3e8dfb6f2ded648c4c
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# Pijpleidingen die alleen bestemd zijn voor de productie en die alleen voor de productie worden gesplitst {#stage-prod-only}

U kunt het opvoeren en productieplaatsingen verdelen gebruikend specifieke pijpleidingen.

## Overzicht {#overview}

Staging- en productieomgevingen zijn nauw aan elkaar gekoppeld. Door gebrek, worden de plaatsingen aan hen verbonden aan één enkele pijpleiding. Dat wil zeggen, een plaatsingspijpleiding aan zowel de het opvoeren als productiemilieu&#39;s in dat programma opstelt. Hoewel deze koppeling normaal gesproken geschikt is, zijn er bepaalde gevallen waarin er nadelen zijn:

* Als u aan stadium-slechts wilt opstellen, verwerpt u **bevorderen aan Prod** stap in de pijpleiding. De uitvoering wordt echter gemarkeerd als geannuleerd.
* Als u de recentste code in een het opvoeren milieu aan productie wilt opstellen, moet u de volledige pijpleiding met inbegrip van de het opvoeren plaatsing opnieuw opstellen alhoewel geen code daar werd veranderd.
* De milieu&#39;s kunnen niet tijdens plaatsingen worden bijgewerkt. Als u de testomgeving enkele dagen lang pauzeert voordat u de productie promoot, blijft de productieomgeving vergrendeld en kan deze niet worden bijgewerkt. Dit scenario maakt niet-afhankelijke taken zoals het bijwerken van [ milieuvariabelen ](/help/implementing/cloud-manager/environment-variables.md) onmogelijk.

De fase-slechts en prod-slechts pijpleidingen bieden oplossingen aan deze gebruiksgevallen door specifieke plaatsingsopties te verstrekken.

* **stadium-slechts de Pijpleidingen van de Plaatsing:** stelt slechts aan een het opvoeren milieu met de uitvoering op die eindigt zodra de plaatsing en de tests worden gedaan. Een alleen-fase pijpleiding gedraagt zich identiek aan de standaard gekoppelde volledige pijpleiding van de stapelprod maar zonder de stappen van de productieleiding (goedkeuring, programma, opstelling).
* **Prod-Enige Pijpleidingen van de Plaatsing:** stelt slechts aan productie op door de meest recente succesvolle werkgebieduitvoering te selecteren. Dan het opstellen van zijn artefacten aan productie. Prod-enige pijpleidingen hergebruiken de artefacten van de werkgebiedplaatsing, die de bouwingsfase mijden.

De fase-slechts en prod-enige pijpleidingen worden niet uitgevoerd terwijl een volledig-stapelproductiepijplijn lopend is, en vice versa. Als zowel het stadium-slechts als de full-stack productiepijplijn de **gevormde trekker van de Veranderingen van het Git** hebben en aan de zelfde tak en de bewaarplaats richten, slechts wordt de stadium-enige pijpleiding automatisch begonnen. Pijpleidingen met alleen proxy&#39;s starten niet **`On Git Changes`** omdat deze niet rechtstreeks aan een opslagplaats zijn gekoppeld.

Prod-slechts pijpleidingen worden teweeggebracht manueel, aangezien zij niet direct met een bewaarplaats voor **op de Veranderingen van het Git** verbonden zijn.

Deze speciale pijpleidingen bieden meer flexibiliteit, maar u zou de volgende details van verrichting en aanbevelingen moeten noteren.

>[!NOTE]
>
>Pijpleidingen met alleen profielen maken altijd gebruik van artefacten uit de pijpleiding met alleen het werkgebied. Dit proces is nog steeds van toepassing, ook al heeft de standaard gekoppelde productiepijpleiding intussen iets anders ingezet.
>
>* Bijvoorbeeld scenario&#39;s kunnen leiden tot ongewenste terugdraaiversies van code.
>* Adobe raadt aan om de standaard gekoppelde productiepijpleiding niet meer te gebruiken zodra u begint met het gebruik van de pijpleidingen met alleen maar profielen en alleen met trapsgewijs.
>* Als u nog steeds besluit om zowel de standaard gekoppelde pijpleidingen als de pijpleidingen met alleen fase/fase uit te voeren, dient u rekening te houden met het hergebruik van artefacten om terugdraaiversies van code te voorkomen.

## Pipetontwerp {#pipeline-creation}

Prod-slechts en stadium-enige pijpleidingen worden gecreeerd op een gelijkaardige manier aan de standaard gekoppelde [ productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) en [ niet productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Zie deze documenten voor meer informatie.

1. In het **venster van Pijpleidingen**, klik **toevoegen Pijpleiding**.

   * Selecteer **toevoegen de niet-Productiepijpleiding** aan [ een stadium-slechts pijpleiding ](#stage-only) creëren.
   * Selecteer **Voeg slechts de Pijpleiding van de Productie** toe om [ tot een pro-enige pijpleiding ](#prod-only) te leiden.

![ Creërend een prod/stadium-enige pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-stage-pipeline.png)

>[!NOTE]
>
>Bepaalde opties kunnen grijs worden weergegeven als de desbetreffende pijpleidingen al bestaan.
>
>* **voeg slechts de Pijpleiding van de Productie** toe is niet beschikbaar als een stadium-enige pijpleiding nog niet bestaat.
>* **voeg de Pijpleiding van de Productie** toe is niet beschikbaar als een standaard gekoppelde pijpleiding reeds bestaat.
>* Per programma zijn slechts één pijpleiding met alleen maar een fase en één pijpleiding toegestaan.

### Een alleen-werkgebiedpijpleiding maken {#stage-only}

1. In **voeg niet-Productie pijplijn** dialoogdoos, op het **3} lusje van de Configuratie toe, selecteer het** gebied van de Pijpleiding van de Plaatsing **voor uw pijpleiding.**
1. Voer in het veld Naam niet-productiepijplijn een naam in voor vrije tekst.
1. Selecteer de gewenste plaatsingsopties, dan klik **verdergaan**.

   ![ het lusje van de Configuratie in Add niet-Productie de dialoogdoos van de Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-1.png)

1. Op het **lusje van de Code van Source**, uitgezochte **Volledige Code van de Stapel**. Met deze optie wordt de volledige AEM-toepassing (back-end, Dispatcher/web tier config en alle front-end modules in de repo) samengesteld en geïmplementeerd.

1. In de **In aanmerking komende drop-down lijst van de Milieu&#39;s van de Plaatsing**, selecteer het **stadium** milieu als plaatsingsmilieu voor uw pijpleiding. Het selecteren van het stadium leidt tot een pijpleiding die aan het werkgebiedmilieu wordt gewijd (productiebevordering gebeurt door middel van een afzonderlijke pijpleiding).

1. Selecteer uw **Bewaarplaats** en **Tak van het Git** in de respectieve drop-down lijsten, dan klik **verdergaan**.

   ![ het lusje van de Code van Source in Add niet-Productie de dialoogdoos van de Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-2.png)

1. Op het **lusje van de Controle van de Ervaring**, is de gespecificeerde Plaats URL gepubliceerde URL die Cloud Manager voor paginakwaliteit controleert.

1. Op het **gebied van de Weg van de Pagina 0} {, specificeer welke pagina&#39;s u wilt controleren, dan klikken** pictogram **![toevoegen Pagina ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg).**

   In de Experience Audit wordt elk pad geanalyseerd dat u toevoegt voor prestaties, toegankelijkheid, progressieve webapps, aanbevolen werkwijzen, SEO en andere kwaliteitscontroles. U kunt veelvoudige wegen toevoegen en om het even welk verwijderen door ![ Grootte 400 te klikken pictogram ](https://spectrum.adobe.com/static/icons/ui_18/CrossSize400.svg).

   ![ het lusje van de Controle van de Ervaring in Add niet-Productie de dialoogdoos van de Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-3.png)

1. Klik **sparen**.


### Een pijplijn maken die alleen in de vorm van een proxy kan worden weergegeven {#prod-only}

1. In de dialoogdoos **voeg slechts de Pijpleiding van de Productie**, op het **de tekstgebied van de Naam van de Pijpleiding** toe, ga de vrije-tekstnaam van de pijpleiding in.
1. Op het **gebied van de Naam van de Pijpleiding**, typ de naam u wilt.
1. Onder **de Opties van de Plaatsing van de Productie**, uitgezochte **Pauze alvorens aan Productie** op te stellen.

   Met deze optie voegt u een handmatige goedkeuringspoort in vlak voor de productiefase. De pijpleiding houdt op en wacht op een fiatteur (zoals een Manager van de Plaatsing, of een BedrijfsEigenaar) om de productie goed te keuren of te annuleren opstellen.

   Wordt gebruikt voor wijzigingsbeheer of voor controles op het laatste moment.

1. Klik **sparen** om de productie-enige pijpleiding met deze opties tot stand te brengen.

   ![ Creërend een productie-enige pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-production-only-pipeline.png)

## Pijpleidingen met alleen het werkgebied en met alleen het profiel uitvoeren {#running}

U kunt de nieuwe pijpleidingen [ als een andere pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) beginnen. U kunt een productie-enige pijpleiding rechtstreeks van de uitvoeringsdetails van een stadium-enige pijpleiding teweegbrengen.

<!-- * Stage-only and prod-only pipelines offer a new [emergency mode](#emergency-mode) to skip testing.
Prod-only pipeline run can be triggered directly from the execution details of a [stage-only pipeline](#stage-only-run).


### Emergency Mode {#emergency-mode}

When starting production-only and staging-online pipelines, you are prompted to confirm the start and how it starts.

* **Normal Mode** is a standard run and includes stage testing steps.
* **Emergency Mode** skips stage testing steps.

![Emergency Mode](/help/assets/configure-pipelines/emergency-mode.png) -->

### Uitvoeren van pijpleidingen met alleen trapsgewijze uitloop {#stage-only-run}

In de uitvoeringsdetails, a **bevorderen bouwt** knoop na de het testen stappen. Klik het om een productie-enige pijpleiding teweeg te brengen die de het werkgebiedartefacten van deze looppas aan productie opstelt. De knop wordt alleen weergegeven bij de laatste geslaagde uitvoering van het werkgebied.

![ werkgebied-enige pijpleiding loopt ](/help/implementing/cloud-manager/configuring-pipelines/assets/stage-only-pipelines-run.png)

Wanneer u **bevordert bouw** klikt, opent een dialoogdoos voor u om de looppas van de verwante productie-enige pijpleiding te bevestigen. Klik **Looppas** om het te beginnen.

![ bevordert bouw - de dialoogdoos van de Pijpleiding van de Looppas ](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-run.png)

Als er geen installatieprogramma is, wordt u gevraagd om er een te maken.

![ Bevorderen bouwt - Geen geldig vakje van de pijpleidingsdialoog ](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-no-valid-pipeline.png)


### Pijpleidingen met alleen profielen uitvoeren {#prod-only-run}

Voor a **productie-enige** pijpleiding, toont Cloud Manager de bronartefacten die aan productie worden opgesteld. Controleer de **stap van de Voorbereiding van het 0} Artefact voor de bronuitvoering, dan open het om details en logboeken te bekijken.**


![ details Artefact ](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-only-pipelines-run.png)
