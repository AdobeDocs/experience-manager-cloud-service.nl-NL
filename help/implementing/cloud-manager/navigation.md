---
title: Navigeren door de gebruikersinterface van Cloud Manager
description: Leer hoe de gebruikersinterface van Cloud Manager is georganiseerd en hoe u kunt navigeren om uw programma's en omgevingen te beheren.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1595'
ht-degree: 0%

---


# Navigeren door de gebruikersinterface van Cloud Manager {#navigation}

Leer hoe de gebruikersinterface van Cloud Manager is georganiseerd en hoe u kunt navigeren om uw programma&#39;s en omgevingen te beheren.


De interface voor cloud-beheer bestaat voornamelijk uit twee grafische interfaces:

* [ de Mijn console van Programma&#39;s ](#my-programs-console) is waar u al uw programma&#39;s kunt bekijken en beheren.
* [ het venster van het Overzicht van het Programma ](#program-overview) is waar u het detail van kunt zien en een individueel programma beheren.

>[!TIP]
>
>Ook controleer de [ onboarding documentatiereis ](/help/journey-onboarding/overview.md) voor een volledig overzicht van hoe te met AEM as a Cloud Service het gebruiken van Cloud Manager in werking te stellen.


## AI Assistant in AEM

Voor klanten die [ voltooide noodzakelijke criteria ](/help/implementing/cloud-manager/ai-assistant-in-aem.md#get-access) hebben, is de Medewerker van AI in AEM beschikbaar aan gebruikers van hun organisatie. Zie [ Medewerker AI in AEM ](/help/implementing/cloud-manager/ai-assistant-in-aem.md).


## Mijn programmaconsole {#my-programs-console}

Wanneer u login in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en de aangewezen organisatie selecteert, komt u bij de **Mijn console van Programma&#39;s** aan.

![ Mijn console van Programma&#39;s ](assets/my-programs-console.png)

De console Mijn Programma&#39;s biedt een overzicht van alle programma&#39;s waartoe u toegang hebt in de geselecteerde organisatie. Het bestaat uit verschillende delen.

1. [ Toolbars ](#toolbars-my-programs-toolbars) voor organisatieselectie, alarm, en rekeningsmontages
1. Tabs waarmee u de huidige weergave van uw programma&#39;s kunt schakelen.
   * **Begin** mening (gebrek) die **Mijn mening van Programma&#39;s** met een overzicht van alle programma&#39;s selecteert
   * **Vergunning** die tot het [ dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md) toegang heeft.
   * Merk op dat het gebrek van lusjes aan gesloten en kan worden onthuld gebruikend ![ het menupictogram van de Show ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) in de [ kopbal van Cloud Manager ](#cloud-manager-header).
1. [ Statistieken en call-to-action ](#statistics) voor een overzicht van uw recente activiteit
1. [**Mijn Programma&#39;s** sectie ](#my-programs-section) met een overzicht van al uw programma&#39;s
1. [ Snelle verbindingen ](#quick-links-section) om tot verwante middelen gemakkelijk toegang te hebben.

>[!TIP]
>
>Zie [ Programma&#39;s en de Types van Programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) voor details op programma&#39;s.

### Werkbalken {#my-programs-toolbars}

Er staan twee werkbalken boven op elkaar.

#### Experience Platform top navigation bar {#cloud-manager-header}

De eerste is de bovenste navigatiebalk van Experience Platform, die blijvend is terwijl u door Cloud Manager navigeert. Het is een anker dat u toegang geeft tot instellingen en informatie die van toepassing zijn op alle Cloud Manager-programma&#39;s.

![ de hoogste navigatiebar van Experience Platform ](assets/experience-cloud-header.png)

* Het ![ menupictogram van de Show ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) (toon of verberg zijmenu) geeft u toegang tot een verscheidenheid van lusjes die u aan specifieke delen van een individueel programma kunnen nemen. Of, kunt u tussen het [ dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md) en de **[Mijn console van Programma&#39;s](#my-programs-console)** afhankelijk van de context schakelen.
* Het ![ pictogram van de Bell ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) ([ Meldingen ](/help/implementing/cloud-manager/notifications.md)) geeft u toegang tot berichten en aankondigingen, onder andere.

Voor verdere details op de hoogste navigatiebar van Experience Platform, gelieve te zien de [ gids UI van Adobe Experience Platform.](https://experienceleague.adobe.com/en/docs/experience-platform/landing/platform-ui/ui-guide#top-navigation-bar)

#### Programmawerkbalk {#program-toolbar}

Op de werkbalk van het programma vindt u koppelingen naar de verschillende Cloud Manager-programma&#39;s en naar acties die binnen de context passen.

![ de toolbar van het Programma ](assets/program-toolbar.png)

1. De **Mijn selecteur van Programma&#39;s** opent een drop-down waar u andere programma&#39;s kunt selecteren of context-aangewezen acties zoals het creëren van een nieuw programma nemen
1. De **Begonnen** verbinding geeft u toegang tot [ op het instappen documentatiereis ](/help/journey-onboarding/overview.md) om u met Cloud Manager in werking te stellen.
1. Met de knop Handeling kunt u contextgerichte acties uitvoeren, zoals het toevoegen van een programma.

### Statistieken en oproep tot actie {#statistics}

De sectie Statistieken en call-to-action bevat geaggregeerde gegevens voor uw organisatie. Als u bijvoorbeeld uw programma&#39;s hebt ingesteld, kunnen statistieken van uw activiteiten in de afgelopen 90 dagen worden weergegeven, zoals:

* Aantal [ plaatsingen ](/help/implementing/cloud-manager/deploy-code.md)
* Aantal [ geïdentificeerde kwesties van de 0} codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)
* Aantal builds

Of als u net de opstelling van uw org begint, zou er uiteinden op volgende stappen of documentatiemiddelen kunnen zijn.

### Sectie Mijn programma&#39;s {#my-programs-section}

De belangrijkste inhoud van de **Mijn console van Programma&#39;s** is de lijst van programma&#39;s in de **Mijn 3} sectie van Programma&#39;s.**

De **Mijn van Programma&#39;s** sectie maakt een lijst van kaarten die elk programma vertegenwoordigen. Klik een kaart om tot de **pagina van het Overzicht van het Programma** van het programma voor details over het programma toegang te hebben.

>[!NOTE]
>
>Afhankelijk van uw rechten kunt u bepaalde programma&#39;s mogelijk niet selecteren.


Gebruik de sorteeropties om het gewenste programma gemakkelijker te vinden.

![ het Sorteren opties ](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Sorteren op:
   * **Gemaakte Datum** (gebrek)
   * **Naam van het Programma**
   * **Status**
* ![ de orde van de Sortering neer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) Ascending (gebrek) / ![ de orde van de Sortering omhoog pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Aflopend
* ![ het Klassieke pictogram van de netmening ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) Mening van het Net (gebrek)
* ![ het lijstpictogram van de Mening van de Mening ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ViewList_18_N.svg)

#### Programmakaarten {#program-cards}

Een kaart (of rij in een tabel) vertegenwoordigt elk programma en biedt een overzicht van het programma en snelle koppelingen om actie te ondernemen.

![ kaart van het Programma ](assets/program-card.png)

* Beeld verbonden aan het Programma, indien gevormd. De bovenstaande afbeelding is &quot;WKND&quot;.
* Naam die aan het Programma wordt toegewezen. In de bovenstaande afbeelding ziet u &quot;SecurBank Sample&quot; als de naam van het programma.
* Servicetype:
   * **Experience Manager Cloud** — voor de programma&#39;s van AEM as a Cloud Service
   * **Experience Manager** — voor [ AMS (Adobe Managed Services) programma&#39;s ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction)
* [ Type van Programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md):
   * Sandbox
   * Productie
* Status. In de bovenstaande afbeelding is de status Gereed met een vinkje.
* Gevormde oplossingen. In de bovenstaande afbeelding zijn Sites en Assets de geconfigureerde oplossingen.
* Aanmaakdatum.

Een productieprogramma kan zijn voorzien van een badged om extra eigenschappen te tonen u op het tijdstip koos u het, zoals het volgende toevoegde:

* ![ HIPAA badge ](assets/hipaa.png) [ HIPAA ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* ![ WAF-DDOS badge ](assets/waf-ddos-protection.png) [ bescherming WAF-DDOS ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* [99,99% SLA (Service level agreement)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

Met het informatiepictogram hebt u ook snel toegang tot aanvullende informatie over het programma (nuttig in de lijstweergave).

![ Informatie ](assets/information-list-view.png)

Het ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_22/Smock_More_22_N.svg) pictogram geeft u toegang tot extra acties u het programma kunt nemen.

![ knoop van de Ellipsis voor programma&#39;s ](assets/program-ellipsis.png)

* Navigeer aan een bepaald ![ pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_22/Smock_Data_22_N.svg) [ Milieu ](/help/implementing/cloud-manager/manage-environments.md) van het programma
* Open het ![ pictogram van het Overzicht van het Programma ](/help/implementing/cloud-manager/assets/program-overview.svg) [ Overzicht van het Programma ](#program-overview)
* ![ geef pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) uit [ geef het programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing) uit
* ![ het pictogram van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) [ schrap een zandbakprogramma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>Raadpleeg de volgende secties voor meer informatie over programma&#39;s en het toevoegen en beheren van programma&#39;s:
>
>* [ Programma&#39;s en de Types van Programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [ creeer productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
>* [ creeer zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)


### Sectie Snelle koppelingen {#quick-links-section}

De snelle sectie van verbindingen geeft u toegang tot algemeen gebruikte middelen die verwant zijn.

## Pagina met overzicht van programma&#39;s {#program-overview}

Wanneer een programma in de **[Mijn console van Programma&#39;s](#my-programs-console)** wordt geselecteerd, wordt u genomen aan de **pagina van het Overzicht van het Programma**.

![ Overzicht van het Programma ](assets/program-overview.png)

In het programmaoverzicht hebt u toegang tot alle details van een Cloud Manager-programma. Als **Mijn console van Programma&#39;s**, wordt het gemaakt van verscheidene delen.

1. [ Toolbars ](#program-overview-toolbar) om terug naar de Mijn console van Programma&#39;s snel te springen, en het programma te navigeren
1. [ Lusjes ](#program-tabs) om tussen verschillende aspecten van het programma te schakelen
1. A [ call-to-action ](#cta) die op de laatste acties van het programma wordt gebaseerd
1. Een [ overzicht van de milieu&#39;s ](#environments) van het programma
1. Een [ overzicht van de pijpleidingen ](#pipelines) van het programma
1. Een [ overzicht van de prestaties ](#performance) van het programma
1. Verbindingen met [ nuttige middelen ](#useful-resources)

### Werkbalken {#program-overview-toolbar}

De toolbars voor het programmaoverzicht zijn gelijkaardig aan die toolbars van de [ Mijn console van Programma&#39;s ](#my-programs-toolbars). Alleen de verschillen worden hier geïllustreerd.

#### Cloud Manager header {#cloud-manager-header-2}

In de linkerbovenhoek van de pagina bevindt zich de Adobe Cloud Manager-header. U kunt ![ het menupictogram van de Zijde ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) klikken om het zijmenu van lusjes aan andere gebieden van de software te tonen of te verbergen.

![ Cloud Manager zijmenu ](assets/cloud-manager-hamburger.png)

Klik op Adobe Cloud Manager om terug te keren naar Home.

#### Programmawerkbalk {#program-toolbar-2}

Op de werkbalk van het programma hebt u nog steeds toegang om snel over te schakelen naar andere programma&#39;s, maar hebt u ook toegang tot contextgerichte acties, zoals het toevoegen en bewerken van het programma.

![ de toolbar van het Programma ](assets/cloud-manager-program-toolbar.png)

De toolbar toont altijd het lusje dat u momenteel bent, zelfs als u de lusjes gebruikend ![ toont menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) hebt verborgen.

### Tabbladen van programma {#program-tabs}

Elk programma heeft talrijke opties en gegevens verbonden aan het. Deze opties en gegevens worden in tabbladen verzameld om het navigeren door het programma eenvoudiger te maken. Met de tabbladen hebt u toegang tot:

**Programma**

* ![ Modern pictogram van de netmening ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ModernGridView_18_N.svg) Overzicht - het programmaoverzicht zoals die in het huidige document wordt beschreven
* ![ het pictogram van de Bell ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) [ Activiteit ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) - de geschiedenis van pijpleidingslooppas van het programma
* ![ pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) [ Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) - Alle pijpleidingen die voor het programma worden gevormd
* ![ het pictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) [ Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) - Alle bewaarplaatsen die voor het programma worden gevormd
* ![ het schijfpictogram van de Grafiek ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_GraphPie_18_N.svg) [ Rapporten ](/help/implementing/cloud-manager/reports/report-sla.md) - Metriek zoals de gegevens van SLA

**de Diensten**

* ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) [ Milieu&#39;s ](/help/implementing/cloud-manager/manage-environments.md) - Alle milieu&#39;s die voor het programma worden gevormd
* ![ het pictogram van de Web-pagina&#39;s ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) [ Plaatsen van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md) - beheert de plaatsen van Edge Delivery
* ![ pictogram van Montages ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) [ Montages van het Domein ](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - beheer de namen van het douanedomein voor het programma
* ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) [ SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) - beheer SSL certificaten voor het programma
* ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) Toewijzingen van het Domein 1} Sociale netwerkpictogram [ - beheer de Toewijzingen van het Domein](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
* ![ het lijstpictogram van de Taak ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) [`IP Allow Lists`](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) - bepaalt lijsten van gewenste personen voor bepaalde IP adressen
* ![ het pictogram van de Doos ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) [ Reeksen van de Inhoud ](/help/implementing/developing/tools/content-copy.md) - Reeksen inhoud die voor exemplaardoeleinden wordt gecreeerd
* ![ pictogram van de Geschiedenis ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) [ de Activiteit van de Inhoud van het Exemplaar ](/help/implementing/developing/tools/content-copy.md) - de activiteiten van het Inhoudsexemplaar
* ![ pictogram van het Kanaal ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Channel_18_N.svg) [ de Infrastructuur van het Netwerk ](/help/security/configuring-advanced-networking.md) - beheer geavanceerde voorzien van een netwerkopties voor het programma

**Middelen**

* ![ pictogram van het Boek ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Book_18_N.svg) het Leren Wegen - de Extra het leren middelen over Cloud Manager

Door gebrek, wanneer u een programma opent u op het **Overzicht** tabel aankomt. Het huidige tabblad wordt gemarkeerd. Selecteer een ander tabblad om de details ervan weer te geven.

In de upper-left hoek van de [ kopbal van Cloud Manager ](#cloud-manager-header-2), klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu van lusjes te tonen of te verbergen.

### Call-to-action {#cta}

In de sectie call-to-action vindt u nuttige informatie, afhankelijk van de status van uw programma. Voor een nieuw programma, kunt u volgende stappen zien gegeven en een herinnering van een go-live datum, [ die tijdens programmaverwezenlijking ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) wordt geplaatst.

![ Call-to-action voor een nieuw programma ](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Voor een levend programma, de status van uw laatste plaatsing met verbindingen voor details en het beginnen van een nieuwe plaatsing.

![ Call-to-action ](/help/implementing/cloud-manager/assets/info-banner.png)

### Milieukaart {#environments}

De **kaart van Milieu** geeft u een overzicht van uw milieu&#39;s en verbindingen voor snelle acties.

De **kaart van Milieu** maakt een lijst van slechts drie milieu&#39;s. Klik {het pictogram van het 0} Werkschema ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) tonen allen **om alle milieu&#39;s van het programma te zien.**

Zie ook [ Milieu ](/help/implementing/cloud-manager/manage-environments.md) beheren.

### Pipelkaart {#pipelines}

De **Pijpleidingen** kaart geeft u een overzicht van uw pijpleidingen en verbindingen voor snelle acties.

De **Pijpleidingen** kaart maakt slechts van drie pijpleidingen een lijst. Klik {het pictogram van het 0} Werkschema ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) tonen allen **om alle pijpleidingen van het programma te zien.**

Zie ook [ leiden Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) voor details op hoe te om uw pijpleidingen te beheren.

### Prestatiekaart {#performance}

De **kaart van Prestaties** geeft een overzicht van het **[CDN Dashboard](/help/implementing/cloud-manager/cdn-performance.md)**.

![ kaart van Prestaties ](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

### Nuttige bronnen {#useful-resources}

De **Nuttige 1} sectie van Middelen {verstrekt verbindingen aan extra het leren middelen voor Cloud Manager.**
