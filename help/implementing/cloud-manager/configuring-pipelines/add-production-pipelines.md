---
title: Productiepijpleidingen toevoegen
description: Productiepijpleidingen toevoegen
index: false
source-git-commit: 16e3280d7eaf53d8f944a60ec93b21c6676f0133
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Een productiepijpleiding maken {#create-production-pipeline}

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

