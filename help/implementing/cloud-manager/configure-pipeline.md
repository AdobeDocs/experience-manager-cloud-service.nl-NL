---
title: CI/CD-pijpleiding configureren - Cloud Services
description: CI/CD-pijpleiding configureren - Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: bcbb0cc739c3be8e39585dd752af1b1da801a434
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 0%

---

# De CI/CD-pipeline configureren {#configure-ci-cd-pipeline}

In Cloud Manager zijn er twee typen pijplijn:

* **Productiepijpleiding**:

   Een productiepijpleiding kan alleen worden toegevoegd als een productie- en werkgebiedomgeving is ingesteld.

   Raadpleeg [Productiepijplijn instellen](configure-pipeline.md#setting-up-the-pipeline) voor meer informatie.

* **Niet-productiepijpleiding**:

   Een niet-productiepijpleiding kan van **Overzicht** pagina van het gebruikersinterface van de Manager van de Wolk worden toegevoegd.

   Raadpleeg [Uitsluitend pijplijnen ](configure-pipeline.md#non-production-pipelines) Niet-productie en alleen codekwaliteit voor meer informatie.

>[!NOTE]
>Om uw pijpleiding te vormen, moet u:
> * bepaal de trekker die de pijpleiding zal beginnen.
> * de parameters voor de implementatie van de productie te definiëren.
> * de testparameters voor de prestaties configureren.


## Productiepijpleiding instellen {#setting-up-production-pipeline}

De Manager van de Plaatsing is verantwoordelijk voor vestiging de Pijpleiding van de Productie.

>[!NOTE]
>Een productiepijpleiding kan pas worden ingesteld als het programma is gemaakt, de Git-opslagplaats ten minste één vertakking heeft en er een productie- en werkgebiedomgeving is ingesteld.

Alvorens u begint om uw code op te stellen, moet u uw pijpleidingsmontages van [!UICONTROL Cloud Manager] vormen.

>[!NOTE]
>
>U kunt de pijpleidingsmontages na aanvankelijke opstelling veranderen.

## Het vormen van de Montages van de Pijpleiding van [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Zodra u opstelling uw programma hebt en minstens één milieu gebruikend [!UICONTROL Cloud Manager] UI heeft, bent u klaar om uw plaatsingspijpleiding te installeren.

Voer de volgende stappen uit om het gedrag en de voorkeuren voor uw pijplijn te configureren:

1. Klik **De Pijpleiding van de Opstelling** om uw pijpleiding te installeren en te vormen.

   ![](assets/set-up-pipeline1.png)

1. De **Setup Pipeline** schermvertoningen. Selecteer de vertakking en klik **Next**.

   ![](assets/setup-1.png)

1. Configureer uw implementatieopties.

   ![](assets/setup-pipeline.png)

   U kunt de trekker bepalen om de pijpleiding te beginnen:

   * **Handmatig**  - de UI gebruikt manueel begint de pijpleiding.
   * **Bij de Veranderingen**  van het Git - begint de pijpleiding CI/CD wanneer er toezeggingen aan de gevormde git tak worden toegevoegd. Zelfs als u deze optie selecteert, kunt u de pijpleiding altijd manueel beginnen.

   Tijdens pijpleidingsopstelling of geef uit, heeft de Manager van de Plaatsing de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitshates wordt ontmoet.

   Dit is handig voor klanten die meer geautomatiseerde processen willen. De beschikbare opties zijn:

   * **Telkens**  vragen - Dit is de standaardinstelling en u moet handmatig ingrijpen bij elke belangrijke fout.
   * **Onmiddellijk**  annuleren - Als u deze optie selecteert, wordt de pijplijn geannuleerd wanneer een belangrijke fout optreedt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Direct**  goedkeuren - Als geselecteerd, zal de pijpleiding automatisch te werk gaan wanneer een Belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.


1. De montages van de productiepijpleiding omvatten een derde lusje geëtiketteerd als **ErvingsAudit**. Deze optie verstrekt een lijst voor de wegen URL die altijd in de Controle van de Ervaring moeten worden omvat.

   >[!NOTE]
   >U moet op **toevoegen Nieuwe Pagina** klikken om uw eigen douaneverbinding te bepalen.

   ![](assets/setup-3.png)

   Klik **Nieuwe pagina toevoegen** om een weg URL te verstrekken die in de Controle van de Ervaring moet worden omvat.

   Als u bijvoorbeeld `https://wknd.site/us/en/about-us.html` wilt opnemen in de Experience Audit, voert u het pad `us/en/about-us.html` in dit veld in en klikt u op **Opslaan**.

   ![](assets/exp-audit4.png)

   De URL die in de tabel wordt weergegeven, is:

   `https://publish-p14253-e43686.adobeaemcloud.com/us/en/about-us.html`

   ![](assets/exp-audit5.png)

   U kunt maximaal 25 rijen opnemen. Als de gebruiker in deze sectie geen pagina&#39;s heeft verzonden, wordt de homepage van de site standaard opgenomen in de Experience Audit.

   Raadpleeg [Understanding Experience Audit Results](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie.

   >[!NOTE]
   > De pagina&#39;s die worden gevormd zullen aan de dienst worden voorgelegd en volgens prestaties, toegankelijkheid, SEO (de Optimalisering van de Motor van het Onderzoek), beste praktijken, en PWA (Progressieve App van het Web) tests geëvalueerd.

1. Klik **Save** van **Edit Pijpleiding** scherm. Op de pagina **Overzicht** wordt nu **Program**-kaart implementeren weergegeven. Klik **Implementeer** knoop om uw programma op te stellen.

   ![](assets/configure-pipeline5.png)

### Een productiepijpleiding bewerken {#editing-prod-pipeline}

U kunt de pijpleidingsconfiguraties van de **pagina van het Overzicht van het Programma** uitgeven.

Volg de stappen hieronder om de gevormde pijpleiding uit te geven:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Klik op **Edit** van **Pipelines** kaart.

   ![](assets/configure-pipeline/edit-pipeline-1.png)

1. Met het tabblad **Broncode** kunt u de opslagplaats bijwerken. Klik op **Toegang tot repo-info** om de gegevensopslagruimte bij te werken.

   >[!NOTE]
   >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/cloud-manager-repositories.md#add-manage-repos) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

   ![](assets/configure-pipeline/edit-pipeline-2.png)


1. Met het tabblad **Omgevingen** kunt u het werkgebied en de productieopties bijwerken.

   ![](assets/configure-pipeline/edit-pipeline-3.png)

1. Met de optie **Experience Audit** kunt u nieuwe pagina&#39;s bijwerken of toevoegen.

   ![](assets/configure-pipeline/edit-pipeline-4.png)

1. Klik op **Save** zodra u klaar bent met het bewerken van de pijplijn.

## Uitsluitend pijplijnen zonder productie en codekwaliteit {#non-production-pipelines}

Naast de hoofdpijpleiding die zich naar het stadium en de productie ontwikkelt, kunnen klanten extra pijpleidingen opzetten, die als **Niet-productiepijpleidingen** worden bedoeld. Deze pijpleidingen voeren altijd de bouw en de stappen van de codekwaliteit uit. Zij kunnen naar keuze ook opstellen aan AEM als milieu van de Cloud Service.

Op het thuisscherm worden deze pijpleidingen op een nieuwe kaart vermeld:

1. Open de tegel **Niet-productiepijpleidingen** vanuit het startscherm van Cloud Manager.

   ![](/help/implementing/cloud-manager/assets/non-prod-add.png)

1. Klik op **Add** knoop, om de Naam van de Pijpleiding, het Type van Pijpleiding, en de Tak van het Git te specificeren.

   Bovendien, kunt u de Trigger van de Plaatsing van de opstelling en Belangrijk Gedrag van de Mislukking van de Opties van de Pijpleiding ook plaatsen.

   ![](assets/non-prod-pipe1.png)

1. Klik **sparen** en de pijpleiding wordt getoond op de kaart op het huisscherm met vijf acties, zoals hieronder getoond:

   ![](/help/implementing/cloud-manager/assets/prod-one.png)

   * **Bewerken**  - staat het uitgeven van de pijpleidingsmontages toe
   * **Details**  - verstrekt details van de pijpleidingsuitvoering
   * **Build**  - navigeert aan de uitvoeringspagina, waarvan de pijpleiding kan worden uitgevoerd
   * **Toegang tot repo-informatie** : hiermee kan de gebruiker de informatie ophalen die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager
   * **Leer meer**  - navigeert aan het begrip van de CI/CD bron van de pijpleidingsdocumentatie.

### Een niet-productiepijplijn bewerken {#editing-nonprod-pipeline}

U kunt de pijpleidingsconfiguraties van de **pagina van het Overzicht van het Programma** uitgeven.

Voer de onderstaande stappen uit om de geconfigureerde niet-productiepijplijn te bewerken:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Selecteer het tabblad **Niet-productie** en klik op **Bewerken** nadat u de gewenste pijpleidingen hebt geselecteerd.

   ![](assets/configure-pipeline/non-prod-edit-1.png)

1. Selecteer de gewenste opslagplaats en klik op **Opslaan**.

   ![](assets/configure-pipeline/non-prod-edit2.png)

## De volgende stappen {#the-next-steps}

Zodra u de pijpleiding hebt gevormd, moet u uw code opstellen.

Zie [Uw code implementeren](deploy-code.md) voor meer informatie.
