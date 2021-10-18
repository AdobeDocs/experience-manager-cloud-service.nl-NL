---
title: CI/CD-pijpleiding configureren - Cloud Services
description: CI/CD-pijpleiding configureren - Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: 01cd4efc920515996c928a8cb455bb44d4f722f2
workflow-type: tm+mt
source-wordcount: '1403'
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

### Een nieuwe productiepijpleiding toevoegen {#adding-production-pipeline}

Zodra u opstelling uw programma hebt en minstens één milieu gebruikend [!UICONTROL Cloud Manager] UI heeft, bent u bereid om een productiepijplijn toe te voegen.

Voer de volgende stappen uit om het gedrag en de voorkeuren voor uw productiepijplijn te configureren:

1. Navigeer naar de **Pipelines**-kaart van de pagina **Program Overview**.
Klik op **+Add** en selecteer **Productiepijplijn toevoegen**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **De vertoningen van de** de dialoogdoos van de Pijl van de Productie toevoegen. Ga de pijpleidingsnaam in.

   Daarnaast kunt u **Implementatietrigger** en **Belangrijk gedrag voor metrische fouten** instellen vanuit **Implementatieopties**. Klik op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   U kunt de plaatsingstrekkers bepalen om de pijpleiding te beginnen.

   * **Handmatig**  - de UI gebruikt manueel begint de pijpleiding.
   * **Bij de Veranderingen**  van het Git - begint de pijpleiding CI/CD wanneer er toezeggingen aan de gevormde git tak worden toegevoegd. Zelfs als u deze optie selecteert, kunt u de pijpleiding altijd manueel beginnen.

      Tijdens pijpleidingsopstelling of geef uit, heeft de Manager van de Plaatsing de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitshates wordt ontmoet.

      Dit is handig voor klanten die meer geautomatiseerde processen willen. De beschikbare opties zijn:
   U kunt het belangrijke gedrag van mislukkingsmetriek bepalen om de pijpleiding te beginnen.

   * **Telkens**  vragen - Dit is de standaardinstelling en u moet handmatig ingrijpen bij elke belangrijke fout.
   * **Direct**  mislukt - Als deze optie is geselecteerd, wordt de pijplijn geannuleerd wanneer een belangrijke fout optreedt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Ga onmiddellijk**  door - als geselecteerd, zal de pijpleiding automatisch te werk wanneer een Belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.


1. Het dialoogvenster **Productiepijplijn toevoegen** bevat een tweede tabblad met het label **Broncode**. **Volledige** stapelcodes geselecteerd. U kunt de **Repository** en **Git Branch** kiezen. Selecteer de Implementatieopties voor productie, zoals hieronder wordt uitgelegd. Klik op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-fullstack1.png)

   Implementatieopties voor productie:

   * **Pauzeren vóór implementatie naar productie**: Met deze optie kan de implementatie vóór de productie worden gepauzeerd.
   * **Gepland**: Met deze optie kan de gebruiker de geplande productieimplementatie inschakelen.

1. Het dialoogvenster **Productiepijplijn toevoegen** bevat een derde tabblad met het label **Experience Audit**. Deze optie verstrekt een lijst voor de wegen URL die altijd in de Controle van de Ervaring moeten worden omvat.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   >[!IMPORTANT]
   >U moet op **Add Pagina** klikken om uw eigen douaneverbinding te bepalen. Paginapad moet beginnen met `/`.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit2.png)


   Klik **Nieuwe pagina toevoegen** om een weg URL te verstrekken die in de Controle van de Ervaring moet worden omvat.

   Als u bijvoorbeeld `https://wknd.site/us/en/about-us.html` wilt opnemen in de Experience Audit, voert u het pad `/us/en/about-us.html` in dit veld in en klikt u op **Opslaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

   De URL die in de tabel wordt weergegeven, is:

   `https://publish-p12361-e112003.adobeaemcloud.com/us/en/about-us.html`

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

   U kunt maximaal 25 rijen opnemen. Als de gebruiker in deze sectie geen pagina&#39;s heeft verzonden, wordt de homepage van de site standaard opgenomen in de Experience Audit.

   Raadpleeg [Understanding Experience Audit Results](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie.

   >[!NOTE]
   > De pagina&#39;s die worden gevormd zullen aan de dienst worden voorgelegd en volgens prestaties, toegankelijkheid, SEO (de Optimalisering van de Motor van het Onderzoek), beste praktijken, en PWA (Progressieve App van het Web) tests geëvalueerd.

1. Klik op **Opslaan**. De nieuwe productiepijplijn wordt nu weergegeven in de **Pipelines**-kaart.

   De pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   * **Voeg toe**  - staat het toevoegen van een nieuwe pijpleiding toe.
   * **Toegang tot repo-informatie** : hiermee kan de gebruiker de informatie ophalen die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager Git.
   * **Leer meer**  - navigeert aan het begrip van de CI/CD bron van de pijpleidingsdocumentatie.

### Een productiepijpleiding bewerken {#editing-prod-pipeline}

U kunt de pijpleidingsconfiguraties van de **pagina van het Overzicht van het Programma** uitgeven.

Volg de stappen hieronder om de gevormde pijpleiding uit te geven:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Klik op **..** van **Pipelines** kaart en klik op **Edit**, zoals aangetoond in hieronder figuur.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. Het dialoogvenster **Productiepijplijn bewerken** wordt weergegeven.

   1. Met de tab **Configuration** kunt u de **Pipeline Name**, **Deployment Trigger** en **Important Metrics Failed Behavior** bijwerken.

      >[!NOTE]
      >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. Het **tabblad Bron** biedt u een optie om **Pauzeren te controleren of uit te schakelen voordat u de installatie uitvoert naar Productie** en **Geplande** opties van **Implementatieopties voor productie**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. Met de optie **Experience Audit** kunt u nieuwe pagina&#39;s bijwerken of toevoegen.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Klik op **Update** zodra u klaar bent met het uitgeven van de pijpleiding.

### Aanvullende acties voor productiepijpleiding {#additional-prod-actions}

#### Een productiepijpleiding uitvoeren {#run-prod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen in werking stellen:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Klik op **..** van **Pipelines** kaart en klik op **Run**, zoals aangetoond in hieronder figuur.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

#### Een productiepijpleiding verwijderen {#delete-prod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen schrappen:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Klik op **..** van **Pipelines** kaart en klik op **Delete**, zoals aangetoond in hieronder figuur.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via **Schrapping** optie van de kaart van de Pijpleiding nu schrappen.


## Uitsluitend pijplijnen zonder productie en codekwaliteit {#non-production-pipelines}

Naast de hoofdpijpleiding die zich naar het stadium en de productie ontwikkelt, kunnen klanten extra pijpleidingen opzetten, die als **Niet-productiepijpleidingen** worden bedoeld. Deze pijpleidingen voeren altijd de bouw en de stappen van de codekwaliteit uit. Ze kunnen optioneel ook worden geïmplementeerd in AEM as a Cloud Service omgeving.

### Een nieuwe niet-productiepijplijn toevoegen {#adding-non-production-pipeline}

Op het thuisscherm worden deze pijpleidingen op een nieuwe kaart vermeld:

1. Open de **Pipelines**-kaart vanuit het startscherm van Cloud Manager. Klik op **+Add** en selecteer **Niet-productiepijplijn toevoegen**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **De vertoningen van de**  de dialoogdoos van de Pijl van de Niet-Productie toevoegen. Selecteer het type pijplijn dat u wilt maken, **Code Quality Pipeline** of **Deployment Pipeline**.

   Daarnaast kunt u **Implementatietrigger** en **Belangrijk gedrag voor metrische fouten** instellen vanuit **Implementatieopties**. Klik op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. **Volledige** stapelcodes geselecteerd. U kunt de **Repository** en **Git Branch** kiezen. Klik op **Opslaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

1. De nieuwe niet-productiepijplijn wordt nu weergegeven in de **Pipelines**-kaart.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   De pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   * **Voeg toe**  - staat het toevoegen van een nieuwe pijpleiding toe.
   * **Toegang tot repo-informatie** : hiermee kan de gebruiker de informatie ophalen die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager Git.
   * **Leer meer**  - navigeert aan het begrip van de CI/CD bron van de pijpleidingsdocumentatie.

### Een niet-productiepijplijn bewerken {#editing-nonprod-pipeline}

U kunt de pijpleidingsconfiguraties van **Pipelines kaart** van **Overzicht van het Programma** pagina uitgeven.

Voer de onderstaande stappen uit om de geconfigureerde niet-productiepijplijn te bewerken:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Selecteer de niet-productiepijplijn en klik op **..**. Klik op **Edit**, zoals aangetoond in het hieronder cijfer.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. Het dialoogvenster **Productiepijplijn bewerken** wordt weergegeven.

   1. Met de tab **Configuration** kunt u het **Pipeline Name**, **Implementatietrigger** en **Belangrijke metrische foutgedragingen** bijwerken.

      >[!NOTE]
      >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. Op het tabblad **Broncode** kunt u de **opslagplaats** en de **Git Branch** bijwerken.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Klik op **Update** zodra u klaar bent met het uitgeven van de niet-productiepijplijn.

### Aanvullende niet-productie pijplijnhandelingen {#additional-nonprod-actions}

#### Een niet-productiepijpleiding uitvoeren {#run-nonprod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen in werking stellen:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Klik op **..** van **Pipelines** kaart en klik op **Run**, zoals aangetoond in hieronder figuur.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

#### Schrapping van een niet-productiepijpleiding {#delete-nonprod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen schrappen:

1. Navigeer naar **Pipelines**-kaart van de pagina **Program Overview**.

1. Klik op **..** van **Pipelines** kaart en klik op **Delete**, zoals aangetoond in hieronder figuur.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)


## De volgende stappen {#the-next-steps}

Zodra u de pijpleiding hebt gevormd, moet u uw code opstellen.

Zie [Uw code implementeren](deploy-code.md) voor meer informatie.
