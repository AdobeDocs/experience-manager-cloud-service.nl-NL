---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4ddca61044d7923db9fd08b96cb18cedfd71cf70
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 0%

---


# Pijpleidingen beheren {#managing-pipelines}

Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.

## Pipetkaart {#pipeline-card}

De **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** in Cloud Manager geeft u een overzicht van al uw pijpleidingen en hun huidige status.

![ de kaart van Pijpleidingen in Cloud Manager ](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

Door ![ Ellipse te klikken - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast elke pijpleiding, kunt u de volgende acties nemen:

* [Een pijplijn uitvoeren](#running-pipelines)
* [Een pijplijn annuleren](#cancel)
* [Een pijplijn bewerken](#editing-pipelines)
* [Een pijplijn verwijderen](#deleting-pipelines)
* [Bekijk laatste looppas details van een pijpleiding](#view-details)

Onder aan de lijst met pijpleidingen staan de volgende algemene opties:

* **voeg** toe - [ om een nieuwe productiepijpleiding ](configuring-production-pipelines.md) toe of [ voeg een nieuwe niet-productiepijpleiding ](configuring-non-production-pipelines.md) toe toe te voegen
* **toon allen** - neemt de gebruiker aan het scherm van Pijpleidingen om alle pijpleidingen in een meer gedetailleerde lijst te bekijken.
* **Info van de Reactie van de Toegang** - Toont de informatie noodzakelijk om tot de git van Cloud Manager toegang te hebben bewaarplaats
* **leer Meer** - navigeert aan CI/CD de middelen van de pijpleidingsdocumentatie.

## Pagina met pijplijnen {#pipelines}

De **pagina van Pijpleidingen** toont een volledige lijst van alle pijpleidingen voor het geselecteerde programma. Deze informatie is nuttig omdat het uitvoerigere informatie dan voorstelt wat in de [ kaart van de Pijpleiding ](#pipeline-card) beschikbaar is.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht van het 0&rbrace; Programma, klik ![ het lusje van de Pijpleiding - het pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg)** Pijpleidingen **tabel.**

1. Op de **pagina van Pijpleidingen**, kunt u een lijst van alle pijpleidingen voor het programma zien en pijpleiding beginnen en ophouden uitvoeren zoals u in de **Kaart van Pijpleidingen** zou doen.

Als een pijpleiding uitvoert, klik ![ Info - middelgroot pictogram ](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) in de **3&rbrace; kolom van de Status &lbrace;om een pop-up met details over de uitvoering te tonen.** Binnen pop-up, klik **details van de Mening** om de [ details van de pijpleidingsuitvoering ](#view-details) te zien.

![ de uitvoeringsdetails van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)


U kunt ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding ook klikken om extra acties aangewezen aan de pijpleidingsstaat te nemen zoals [ het uitgeven ](#editing-pipelines) of [ annulerend uitvoering ](#cancel).

![ Acties van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

### Markeer favorieten voor pijpleidingen{#pipeline-favorites}

U kunt specifieke pijpleidingen als favorieten merken zodat verschijnen zij bij de bovenkant van de lijst op de **pagina van Pijpleidingen**. Hierdoor zijn vaak geopende pijpleidingen gemakkelijker te vinden en uit te voeren.

**om pijpleidingsfavorieten te merken:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. Van de **pagina van het Overzicht van het 0&rbrace; Programma, klik ![ het lusje van de Pijpleiding - het pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg)** Pijpleidingen **tabel.**
1. Voor de pagina van Pijpleidingen, links van een pijpleidingsnaam en type, klik ![ het overzichtspictogram van de Ster voor ongunstige pijpleiding ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_StarOutline_18_N.svg) om het aan uw favoriete lijst toe te voegen.
Alternatief, klik ![ pictogram van de Ster voor een favoriete pijpleiding ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Star_18_N.svg) om de pijpleiding uit uw favorieten lijst te verwijderen.


## Activiteitenpagina {#activity}

De **pagina van de Activiteit** toont een volledige lijst van alle pijpleidingen uitvoeringen voor het geselecteerde programma en andere belangrijke programmagebeurtenissen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, in het zijmenu, klik ![ het pictogram van de Bell ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) **Activiteit**.

1. In de **pagina van de Activiteit**, kunt u een lijst van alle pijpleidingsuitvoeringen voor het programma, met inbegrip van huidige en historische uitvoeringen zien.

Als een pijpleiding uitvoert, kunt u ![ Info - middelgroot pictogram ](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) in de **3&rbrace; kolom van de Status &lbrace;klikken om een pop-up te tonen die u informatie over de uitvoering toont.**

![ de uitvoeringsdetails van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Klik de rij die de pijpleidingsuitvoering vertegenwoordigen om de [ details van de pijpleidingsuitvoering ](#view-details) te bekijken.

U kunt ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) ook klikken om extra actie op de pijpleidingsuitvoering, zoals mening zijn details of download het logboek, dat u aan de [ pagina van de pijpleidingsdetails ](#view-details) neemt.

![ de uitvoeringshandelingen van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## Een pijplijn uitvoeren {#running-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.

1. Klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u in werking stelt.

1. Van het drop-down menu, klik ![ Looppas - het pictogram van het Spel ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PlayCircle_18_N.svg) **Looppas**.

   De pijpleidingslooppas begint, en de **Status** kolom toont zijn vooruitgang.

U kunt de details van de looppas zien door ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) opnieuw te klikken en **[details van de Mening](#view-details)** te klikken.

Afhankelijk van het type van pijpleiding, kunt u de looppas kunnen annuleren door ![ Ellipse te klikken - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) opnieuw en **te klikken annuleert**.

## Meerdere pijpleidingen uitvoeren {#run-multiple-pipelines}

Met Cloud Manager kunt u meerdere pijpleidingen tegelijk uitvoeren, waardoor de implementatie efficiënter wordt voor AEM as a Cloud Service-klanten. De **Looppas geselecteerde** eigenschap laat u veelvoudige pijpleidingen selecteren en hen teweegbrengen om meteen te lopen. Het vermindert de handmatige inspanning van het moeten pijpleidingen individueel in werking stellen en optimaliseert bouw en plaatsingswerkschema&#39;s.

**om veelvoudige pijpleidingen in werking te stellen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Van het linkerzijmenu, klik ![ pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pijpleidingen**.
1. In de lijst op de **pagina van de Pijpleiding**, selecteer checkboxes naast de pijpleidingen u wilt lopen.
Indien noodzakelijk, klik ![ pictogram van de Filter, trechter ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg) **Filters** aan soortpijpleidingen door naam, of milieu, of opgesteld codetype, of een combinatie van alle drie.
1. Dichtbij de hoger-juiste hoek van de pagina, klik **Geselecteerde Looppas (x)**.
1. In de **Looppas geselecteerde pijpleidingen (x)** dialoogdoos, klik **Looppas (x)**.

   De **looppas** knoop wijst op het aantal pijpleidingen die kunnen te werk gaan. U hebt bijvoorbeeld vier pijpleidingen geselecteerd, maar er is al een pijpleiding actief. Of een omgeving die is gekoppeld aan een geselecteerde pijpleiding bestaat niet meer. In dergelijke gevallen wordt het systeem dienovereenkomstig aangepast. De knop wordt bijgewerkt naar &quot;Uitvoeren (3)&quot; om aan te geven dat drie pijpleidingen kunnen doorgaan.

1. De pijpleidingen beginnen lopend, en hun status wordt bijgewerkt in de **lijst van Pijpleidingen**.

## Een pijplijn bewerken {#editing-pipelines}

U kunt een pijpleiding uitgeven als het niet loopt.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.

1. Klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u wilt uitgeven.

1. Van het drop-down menu, geeft de klik **&#x200B;**&#x200B;uit.

1. In **geef de Pijpleiding van de Productie uit** of **geeft niet-Productie pijplijn** dialoogdoos uit, geef de zelfde details uit die u toen het creëren van de pijpleiding inging.

   Zie de volgende pagina&#39;s voor details over de gebieden en configuratieopties beschikbaar voor pijpleidingen.
   * [Een productiepijpleiding configureren](configuring-production-pipelines.md)
   * [Een niet-productiepijplijn configureren](configuring-non-production-pipelines.md)

1. Wanneer u wordt gedaan, klik **Update**.

>[!NOTE]
>
>De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen. Zie [ een Privé Bewaarplaats GitHub in Cloud Manager ](/help/implementing/cloud-manager/managing-code/private-repositories.md) voor details en de volledige lijst van beperkingen toevoegen.

## Een pijplijn verwijderen {#deleting-pipelines}

U kunt een pijpleiding schrappen als het niet loopt.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.

1. Klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u in werking stelt.

1. Van het drop-down menu, klik **Schrapping**.


## Bekijk laatste looppas details van een pijpleiding {#view-details}

U kunt de details van een pijpleiding controleren om de status en de logboeken van zijn meest recente looppas te bekijken. Nochtans, kunt u tot de details slechts toegang hebben als de pijpleiding momenteel loopt of minstens eens uitgevoerd is.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.

1. Van het drop-down menu, klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u in werking stelt.

1. Van het drop-down menu, klik **Mening laatste uitvoering**.

   U wordt genomen aan de detailspagina van de lopende pijpleiding.

   ![ details van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

   Van hier, kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie [ Uw Code ](/help/implementing/cloud-manager/deploy-code.md) voor meer informatie over codeplaatsing en tests opstellen.

   Alle stappen in een pijpleidingsuitvoering worden getoond met degenen die nog niet uit grijs begonnen. De voltooide stappen tonen hun duur.

   Nadat een pijpleidingsstap volledig is, wordt een samenvatting voorgesteld.

   ![ Overzicht van de Stap ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

1. Klik **details van de Mening** om de **sectie van de Duur** uit te breiden, waar u de gemiddelde duur van de pijpleiding kunt zien die op de historische tendensen van het programma wordt gebaseerd.

   ![ Duur ](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

1. Als uw pijpleiding a **Code Scanning** stap omvatte die kwesties markeerde, klik **Details van de Download** om tot een lijst van [ tests van de codekwaliteit ](/help/implementing/cloud-manager/code-quality-testing.md) toegang te hebben die ontbrak om over te gaan.

   ![ de kwaliteitskwesties van de Code ](assets/managing-pipelines-code-quality-issues.png)

   Het CSV- dossier omvat de kolom van de Plaats van het Dossier van het a **&#x200B;**, die de weg aan de problematische code met betrekking tot het project toont. In tegenstelling, wijst de **kolom van de Plaats van het 0&rbrace; Dossier op de Gegenereerde weg.**

   ![ van het de aftasten van de code van het Project details ](assets/managing-pipelines-code-quality-details.png)

## Een pijplijn annuleren {#cancel}

U kunt de pijpleidingslooppas veilig annuleren als het in de bevestiging of bouwt beeldfase is.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de pagina van het programmaoverzicht, klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van de pijpleiding u op de **Pijpleidingen** kaart wilt annuleren.

   ![ het Kantelen van een pijpleiding ](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Klik **annuleren**.

Alternatief, kunt u een pijpleiding van de pagina van pijpleidingsdetails annuleren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het ![ lusje van Pijpleidingen - het pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pijpleidingen** lusje van het **Overzicht van het Programma** pagina en selecteer de pijpleiding u wilt annuleren.

   U wordt genomen aan de detailspagina van de lopende pijpleiding.

   ![ annuleert de details van de Pijpleiding ](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Klik **annuleren**.

