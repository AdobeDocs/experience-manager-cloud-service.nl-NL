---
title: CI/CD-pijpleiding configureren - Cloud Services
description: CI/CD-pijpleiding configureren - Cloud Services
translation-type: tm+mt
source-git-commit: 4d5ad99e44446ac40d9798df1c7fabb862065495
workflow-type: tm+mt
source-wordcount: '764'
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


## Productiepijpleiding {#setting-up-production-pipeline} instellen

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

   ![](assets/setup-2.png)

   U kunt de trekker bepalen om de pijpleiding te beginnen:

   * **Handmatig**  - de UI gebruikt manueel begint de pijpleiding.
   * **Bij de Veranderingen**  van het Git - begint de pijpleiding CI/CD wanneer er toezeggingen aan de gevormde git tak worden toegevoegd. Zelfs als u deze optie selecteert, kunt u de pijpleiding altijd manueel beginnen.

   Tijdens pijpleidingsopstelling of geef uit, heeft de Manager van de Plaatsing de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitshates wordt ontmoet.

   Dit is handig voor klanten die meer geautomatiseerde processen willen. De beschikbare opties zijn:

   * **Telkens**  vragen - Dit is de standaardinstelling en u moet handmatig ingrijpen bij elke belangrijke fout.
   * **Onmiddellijk**  afbreken - Als deze optie is geselecteerd, wordt de pijplijn geannuleerd wanneer een belangrijke fout optreedt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Ga onmiddellijk**  verder - als geselecteerd, zal de pijpleiding automatisch te werk wanneer een Belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.


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


## Uitsluitend pijplijnen {#non-production-pipelines}

Naast de hoofdpijpleiding die zich naar het stadium en de productie ontwikkelt, kunnen klanten extra pijpleidingen opzetten, die als **Niet-productiepijpleidingen** worden bedoeld. Deze pijpleidingen voeren altijd de bouw en de stappen van de codekwaliteit uit. Ze kunnen optioneel ook worden geïmplementeerd in de omgeving van Adobe Managed Services.

Op het thuisscherm worden deze pijpleidingen op een nieuwe kaart vermeld:

1. Open de tegel **Niet-productiepijpleidingen** vanuit het startscherm van Cloud Manager.

   ![](assets/configure-pipeline6.png)

1. Klik op **Add** knoop, om de Naam van de Pijpleiding, het Type van Pijpleiding, en de Tak van het Git te specificeren.

   Bovendien, kunt u de Trigger van de Plaatsing van de opstelling en Belangrijk Gedrag van de Mislukking van de Opties van de Pijpleiding ook plaatsen.

   ![](assets/non-prod-pipe1.png)

1. Klik **sparen** en de pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   ![](assets/configure-pipeline8.png)

   * **Bewerken**  - staat het uitgeven van de pijpleidingsmontages toe
   * **Build**  - navigeert aan de uitvoeringspagina, waarvan de pijpleiding kan worden uitgevoerd
   * **Git**  beheren: hiermee kan de gebruiker de informatie ophalen die nodig is voor toegang tot de Git-opslagplaats van Cloud Manager

## De volgende stappen {#the-next-steps}

Zodra u de pijpleiding hebt gevormd, moet u uw code opstellen.

Zie [Uw code implementeren](deploy-code.md) voor meer informatie.
