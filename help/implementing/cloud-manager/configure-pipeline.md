---
title: CI/CD-pijpleiding configureren - Cloud Services
description: CI/CD-pijpleiding configureren - Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: f3743451f7aeadae26e8a6814cfbed9667c4a242
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# De CI/CD-pipeline configureren {#configure-ci-cd-pipeline}

In Cloud Manager zijn er twee typen pijplijn:

* **Productiepijpleiding**:

   Een productiepijpleiding kan alleen worden toegevoegd als een productie- en werkgebiedomgeving is ingesteld.

   Zie [Productiepijpleiding instellen](configure-pipeline.md#setting-up-the-pipeline) voor meer informatie .

* **Niet-productiepijpleiding**:

   Er kan een niet-productiepijpleiding worden toegevoegd vanuit de **Overzicht** in de gebruikersinterface van Cloud Manager.

   Zie [Uitsluitend pijplijnen zonder productie en codekwaliteit](configure-pipeline.md#non-production-pipelines) voor meer informatie .

   >[!NOTE]
   >Om uw pijpleiding te vormen, moet u:
   > * bepaal de trekker die de pijpleiding zal beginnen.
   > * de parameters voor de implementatie van de productie te definiëren.
   > * de testparameters voor de prestaties configureren.


## Productiepijpleiding instellen {#setting-up-production-pipeline}

De Manager van de Plaatsing is verantwoordelijk voor vestiging de Pijpleiding van de Productie.

>[!NOTE]
>Een productiepijpleiding kan pas worden ingesteld als het programma is gemaakt, de Git-opslagplaats ten minste één vertakking heeft en er een productie- en werkgebiedomgeving is ingesteld.

Alvorens u begint uw code op te stellen, moet u uw pijpleidingsmontages van vormen [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt de pijpleidingsmontages na aanvankelijke opstelling veranderen.

### Een nieuwe productiepijpleiding toevoegen {#adding-production-pipeline}

Als u uw programma hebt ingesteld en minstens één omgeving hebt die [!UICONTROL Cloud Manager] UI, bent u bereid om een productiepijplijn toe te voegen.

Voer de volgende stappen uit om het gedrag en de voorkeuren voor uw productiepijplijn te configureren:

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina.
Klikken op **+Toevoegen** en selecteert u **Productiepijpleiding toevoegen**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **Productiepijpleiding toevoegen** wordt weergegeven. Ga de pijpleidingsnaam in.

   Bovendien kunt u ook instellen **Implementatieactivering** en **Belangrijk gedrag metrische fouten** van **Implementatieopties**. Klikken op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   U kunt de plaatsingstrekkers bepalen om de pijpleiding te beginnen.

   * **Handmatig** - het gebruiken van UI begint manueel de pijpleiding.
   * **Wijzigingen in Git** - start de CI/CD-pijplijn wanneer er verplichtingen aan de gevormde it-tak worden toegevoegd. Zelfs als u deze optie selecteert, kunt u de pijpleiding altijd manueel beginnen.

      Tijdens pijpleidingsopstelling of geef uit, heeft de Manager van de Plaatsing de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitshates wordt ontmoet.

      Dit is handig voor klanten die meer geautomatiseerde processen willen. De beschikbare opties zijn:
   U kunt het belangrijke gedrag van mislukkingsmetriek bepalen om de pijpleiding te beginnen.

   * **Telkens vragen** - Dit is de standaardinstelling en u moet handmatig ingrijpen bij elke belangrijke fout.
   * **Direct mislukken** - Indien geselecteerd, zal de pijpleiding worden geannuleerd wanneer een Belangrijke mislukking voorkomt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Direct doorgaan** - Indien geselecteerd, zal de pijpleiding automatisch te werk gaan wanneer een Belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.


1. De **Productiepijpleiding toevoegen** bevat een tweede tabblad met het label **Broncode**. **Volledige stapelcode** is geselecteerd. U kunt de **Bewaarplaats** en de **Git Branch**. Selecteer de Implementatieopties voor productie, zoals hieronder wordt uitgelegd. Klikken op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-fullstack1.png)

   Implementatieopties voor productie:

   * **Pauzeren vóór implementatie naar productie**: Met deze optie kan de implementatie vóór de productie worden gepauzeerd.
   * **Gepland**: Met deze optie kan de gebruiker de geplande productieimplementatie inschakelen.

1. De **Productiepijpleiding toevoegen** bevat een derde tabblad met het label **Experience Audit**. Deze optie verstrekt een lijst voor de wegen URL die altijd in de Controle van de Ervaring moeten worden omvat.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   >[!IMPORTANT]
   >U moet op **Pagina toevoegen** om uw eigen aangepaste koppeling te definiëren. Paginapad moet beginnen met `/`.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit2.png)


   Klikken **Nieuwe pagina toevoegen** om een URL-pad op te geven dat moet worden opgenomen in de Experience Audit.

   Als u bijvoorbeeld `https://wknd.site/us/en/about-us.html` in de Controle van de Ervaring, ga de weg in `/us/en/about-us.html` in dit veld en klik op **Opslaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

   De URL die in de tabel wordt weergegeven, is:

   `https://publish-p12361-e112003.adobeaemcloud.com/us/en/about-us.html`

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

   U kunt maximaal 25 rijen opnemen. Als de gebruiker in deze sectie geen pagina&#39;s heeft verzonden, wordt de homepage van de site standaard opgenomen in de Experience Audit.

   Zie [Werken met de resultaten van Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie .

   >[!NOTE]
   > De pagina&#39;s die worden gevormd zullen aan de dienst worden voorgelegd en volgens prestaties, toegankelijkheid, SEO (de Optimalisering van de Motor van het Onderzoek), beste praktijken, en PWA (Progressieve App van het Web) tests geëvalueerd.

1. Klikken op **Opslaan**. De nieuwe productiepijplijn wordt nu weergegeven in de **Pijpleidingen** kaart.

   De pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   * **Toevoegen** - staat toe dat een nieuwe pijpleiding wordt toegevoegd.
   * **Repo-info openen** - stelt de gebruiker in staat de informatie op te halen die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager Git.
   * **Meer informatie** - navigeert naar inzicht in de bron van de Documentatie van de CI/CD-pijpleiding.

### Een productiepijpleiding bewerken {#editing-prod-pipeline}

U kunt de pijpleidingsconfiguraties van de **Programmaoverzicht** pagina.

Volg de stappen hieronder om de gevormde pijpleiding uit te geven:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Bewerken**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. De **Productiepijpleiding bewerken** wordt weergegeven.

   1. De **Configuratie** kunt u de **Naam pijpleiding**, **Implementatieactivering**, en **Gedrag belangrijke metrische fout**.

      >[!NOTE]
      >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. De **Bron** biedt u een optie voor het in- of uitschakelen **Pauzeren vóór implementatie naar productie** en **Gepland** opties van **Implementatieopties voor productie**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. De **Experience Audit** kunt u nieuwe pagina&#39;s bijwerken of toevoegen.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Klikken op **Bijwerken** zodra u klaar bent met het bewerken van de pijplijn.

### Aanvullende acties voor productiepijpleiding {#additional-prod-actions}

#### Een productiepijpleiding uitvoeren {#run-prod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen in werking stellen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Uitvoeren**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

#### Een productiepijpleiding verwijderen {#delete-prod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen schrappen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Verwijderen**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via **Verwijderen** optie van de kaart van de Pijpleiding.


## Uitsluitend pijplijnen zonder productie en codekwaliteit {#non-production-pipelines}

Naast de hoofdpijpleiding die zich naar het stadium en de productie ontwikkelt, kunnen klanten extra pijpleidingen opzetten, die niet-productiepijpleidingen worden genoemd.
Er zijn twee soorten niet-productiepijpleidingen:

1. Codekwaliteit: Hiermee wordt de codekwaliteit gescand op de code in de git-vertakking. Deze pijpleiding voert de bouw en de stappen van de codekwaliteit uit.
1. Implementatie: Naast het uitvoeren van de bouw en de stappen van de codekwaliteit, stelt deze pijpleiding de code aan geselecteerde niet-productie aan AEM as a Cloud Service milieu op.

### Een nieuwe niet-productiepijplijn toevoegen {#adding-non-production-pipeline}

Op het thuisscherm worden deze pijpleidingen op een nieuwe kaart vermeld:

1. Toegang krijgen tot **Pijpleidingen** kaart van het startscherm van Cloud Manager. Klikken op **+Toevoegen** en selecteert u **Niet-productiepijpleiding toevoegen**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Niet-productiepijpleiding toevoegen**  wordt weergegeven. Selecteer het type pijpleiding u wilt creëren, of **Codekwaliteit, pijplijn** of **Implementatiepijp**.

   >[!NOTE]
   >Voor de pijpleidingen van de Plaatsing, moet u het plaatsingsmilieu selecteren.

   Bovendien kunt u ook instellen **Implementatieactivering** en **Belangrijk gedrag metrische fouten** van **Implementatieopties**. Klikken op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. **Volledige stapelcode** is geselecteerd. U kunt de **Bewaarplaats** en de **Git Branch**. Klikken op **Opslaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

1. De nieuwe niet-productiepijplijn wordt nu weergegeven in de **Pijpleidingen** kaart.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   De pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   * **Toevoegen** - staat toe dat een nieuwe pijpleiding wordt toegevoegd.
   * **Repo-info openen** - stelt de gebruiker in staat de informatie op te halen die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager Git.
   * **Meer informatie** - navigeert naar inzicht in de bron van de Documentatie van de CI/CD-pijpleiding.

### Een niet-productiepijplijn bewerken {#editing-nonprod-pipeline}

U kunt de pijpleidingsconfiguraties van de **Pipelkaart** van **Programmaoverzicht** pagina.

Voer de onderstaande stappen uit om de geconfigureerde niet-productiepijplijn te bewerken:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Selecteer de niet-productiepijplijn en klik op **...**. Klikken op **Bewerken**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. De **Productiepijpleiding bewerken** wordt weergegeven.

   1. De **Configuratie** kunt u de **Naam pijpleiding**, **Implementatieactivering**, en **Belangrijk gedrag metrische fouten**.

      >[!NOTE]
      >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. De **Broncode** tabblad geeft u de **Bewaarplaats** en de **Git Branch**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Klikken op **Bijwerken** als u klaar bent met het bewerken van de niet-productiepijplijn.

### Aanvullende niet-productie pijplijnhandelingen {#additional-nonprod-actions}

#### Een niet-productiepijpleiding uitvoeren {#run-nonprod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen in werking stellen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Uitvoeren**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

#### Schrapping van een niet-productiepijpleiding {#delete-nonprod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen schrappen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Verwijderen**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)


## De volgende stappen {#the-next-steps}

Zodra u de pijpleiding hebt gevormd, moet u uw code opstellen.

Zie [Uw code implementeren](deploy-code.md) voor meer informatie .
