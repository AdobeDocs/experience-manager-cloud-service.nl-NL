---
title: Productiepijpleidingen configureren
description: Productiepijpleidingen configureren
index: true
source-git-commit: f25e26c84a87cf793f9c8a5ac53009034e6cd2e9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Een productiepijpleiding configureren {#configure-production-pipeline}

De Manager van de Plaatsing is verantwoordelijk voor het vormen van de Pijpleiding van de Productie.

>[!NOTE]
>Een productiepijpleiding kan pas worden ingesteld als het programma is gemaakt, de Git-opslagplaats ten minste één vertakking heeft en er een productie- en werkgebiedomgeving is ingesteld.

Alvorens u begint uw code op te stellen, moet u uw pijpleidingsmontages van vormen [!UICONTROL Cloud Manager].

>[!NOTE]
>U kunt de pijpleidingsmontages na aanvankelijke opstelling veranderen.

## Een nieuwe productiepijpleiding toevoegen {#adding-production-pipeline}

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


1. De **Productiepijpleiding toevoegen** bevat een tweede tabblad met het label **Broncode**. U kunt **[Volledige stapelcode](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** of **[Code frontend](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. U kunt de **Bewaarplaats** en de **Git Branch**. Selecteer de Implementatieopties voor productie, zoals hieronder wordt uitgelegd. Klikken op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prodpipeline-fullstack1.png)

   Als u **Code frontend**, moet u de optie **Bewaarplaats**, **Git Branch** en **Codelocatie**, zoals weergegeven in onderstaande afbeelding:
   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prodpipeline-fullstack1.png)

   Als u **Volledige stapelcode**, moet u de optie **Bewaarplaats**, **Git Branch** en **Implementatieopties voor productie**, zoals weergegeven in onderstaande afbeelding:
   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prodpipeline-fullstack2.png)

   **Implementatieopties voor productie:**

   * **Pauzeren vóór implementatie naar productie**: Met deze optie kan de implementatie vóór de productie worden gepauzeerd.
   * **Gepland**: Met deze optie kan de gebruiker de geplande productieimplementatie inschakelen.

   >[!IMPORTANT]
   >Als er al een pijplijn met volledige stapelcode bestaat voor de geselecteerde omgeving, wordt deze selectie uitgeschakeld.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/full-stack-disabled.png)

   >[!NOTE]
   >Voordat u begint met het configureren van de voorste-eindpijplijnen, raadpleegt u [Reis voor snel maken van site AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites-journey/quick-site/overview.html) voor een end-to-end workflow met het gebruiksvriendelijke AEM gereedschap Snel site maken. Met deze documentatiesite kunt u de front-end ontwikkeling van uw AEM Site stroomlijnen en uw site snel aanpassen zonder AEM kennis van de back-end.





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


