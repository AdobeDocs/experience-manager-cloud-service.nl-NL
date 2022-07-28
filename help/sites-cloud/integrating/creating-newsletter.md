---
title: Adobe Experience Manager-nieuwsbrief maken
description: 'Adobe Experience Manager-nieuwsbrief maken '
feature: Administering
role: Admin
source-git-commit: f68f5a457bbbcd76681cccabe5a3f4c92b6f8770
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Adobe Experience Manager-nieuwsbrief maken {#creating-newsletter}

Voordat u de onderstaande stappen kunt uitvoeren, moet u eerst [integreren](/help/sites-cloud/integrating/integrating-campaign-classic.md) Adobe Campaign Classic en AEM as a Cloud Service. Nu u zowel Adobe Campaign Classic als AEM as a Cloud Service hebt geconfigureerd, leert u hoe u een Adobe Experience Manager-nieuwsbrief kunt maken.

1. Klik in de AEM auteur op het Adobe Experience Manager-logo linksboven op de pagina en selecteer **Sites**.
1. Campagne selecteren, klik **Logische pagina maken**.
   ![merk maken](assets/create.png)
1. Merk selecteren en klikken **Volgende**.
1. Voer een titel in en klik op **Maken** en **Gereed**.
1. Ga naar **Campagnes Reflectie AdobeDemo Master** en klik op **Logische pagina maken**.
   ![campagnepagina](assets/campaignpage.png)
1. Selecteer de sjabloon Campagne en klik op **Volgende** en **Gereed**.
1. Voer een titel in en klik op **Maken** en **Gereed**.
1. Ga naar **Campagne om AdobeDemo opnieuw te draaien Master** en selecteert u het selectievakje CampaignPage. Klikken **Eigenschappen** links boven.
   ![campagneeigenschappen](assets/propertiesedit.png)
1. Ga naar de **Cloud Service** tab:
   * Selecteer Adobe Campaign in de vervolgkeuzelijst Cloud Service Configurations.
   * Selecteer de gewenste naam voor de Adobe Campaign-configuratie.
   * **Opslaan** en **Sluiten**.
1. Ga naar **Campagne om AdobeDemo te herstellen Master effen CampagnePage** en klik op **Logische pagina maken**.
1. Selecteer de Adobe Campaign-sjabloon voor e-mail (bijvoorbeeld AC 6.1) en klik op **Volgende**.
1. Voer op de pagina Maken de titel voor de nieuwsbrief in en klik op **Maken** en **Gereed**.
1. Ga naar **Campagne om AdobeDemo te herstellen Master effen CampagnePage**, selecteert u het selectievakje Campaign Classic en klikt u op **Bewerken** bovenaan links om de e-mailpagina te openen.
1. Bewerk de Adobe Campaign Classic-pagina voor nieuwsbrieven naar wens.
1. Klik op de knop **Pagina-informatie** knop linksboven en klik op **Pagina publiceren**.
1. Selecteer de configuratie waarop de pagina moet worden gepubliceerd. Klikken **Publiceren**.
   ![publicatiepagina](assets/publish.png)
1. De pagina met nieuwsbrieven is gepubliceerd op het publicatieexemplaar en ook op de configuratie van AEM Adobe Campaign Classic.
   * De nieuwsbrief wordt nu weergegeven in Adobe Campaign Classic
1. Klik op de knop Pagina-informatie en klik op **Workflow starten**.
1. Selecteren **Goedkeuren voor Adobe Campaign** als het workflowmodel en klik op de knop **Workflow starten** knop.
1. Boven aan de pagina wordt een disclaimer weergegeven. Klikken **Voltooid** om de revisie te bevestigen en klik nogmaals op **OK**.
1. Klikken **Voltooid** en selecteert u **Goedkeuring van nieuwsbrief** in de vervolgkeuzelijst Volgende stap en klik op de knop **OK** knop.

## Een ontvanger maken {#creating-recipient}

1. Open de Adobe Campaign Classic-server met de Adobe Campaign Classic-clientconsole.
1. Ga naar de weergave Verkenner.
1. Ga in de structuurweergave aan de linkerkant naar Profielen en doelen en selecteer **Ontvangers**.
   ![ontvangers](assets/recipients.png)
1. Vul de details van de ontvanger in.
   * Voer de voornaam in.
   * Voer de achternaam in.
   * Voer het e-mailadres in.
   * Klikken **Opslaan**.

## Een e-maillevering maken in Adobe Campaign Classic {#create-delivery}

1. Open de Adobe Campaign Classic-server met de Adobe Campaign Classic-clientconsole.
1. Ga naar de weergave Verkenner.
1. Selecteer in de structuurweergave aan de linkerkant de optie **Campaign Management** en selecteert u **Leveringen**.
1. Klik in de rechterbovenhoek op **Nieuw**.
1. Selecteren **E-maillevering met AEM inhoud** van de drop-down lijst van het malplaatje van de Levering en klik **Doorgaan**.
1. Klik op de koppeling Van onder E-mailparameters.
   * Voer het adres van de afzender in.
   * Voer het veld Van in.
   * Klikken **OK**.
1. Klikken **Naar** koppeling en klik vervolgens op **Toevoegen** op het uitgezochte doelscherm.
1. Selecteren **Een ontvanger** en klik op **Volgende**.
   ![doeltype](assets/publish.png)
1. Selecteer de gemaakte ontvanger [voorheen](#creating-recipient) en klik op **Voltooien**.
1. De ontvanger is geselecteerd. Klikken **OK**.
1. Klikken **Synchroniseren**.
1. Selecteer de e-mailpagina in de lijst en klik op **OK**.
1. De e-mailsjabloon is gesynchroniseerd. Klikken **Inhoud vernieuwen** als het niet is geladen.
1. Klikken **Verzenden** om de e-mail te verzenden.
1. Selecteer in het volgende scherm **Aflevering zo snel mogelijk** en klik vervolgens op **Analyseren**.
   ![leveringsdoel](assets/deliverytarget.png)
1. Nu de levering is gemaakt, klikt u op **Levering bevestigen** om het e-mailbericht te verzenden. Klikken **Ja** ter bevestiging.
   ![bevestig levering](assets/confirmdelivery.png)
1. De levering is gestart. Klikken **Sluiten**.
1. Klikken **Opslaan** om de levering op te slaan.
