---
title: Navigeren door de gebruikersinterface van Cloud Manager
description: Leer hoe de gebruikersinterface van Cloud Manager is georganiseerd en hoe u kunt navigeren om uw programma's en omgevingen te beheren.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5f9d53958076b77cd333a042003c83853594db87
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 0%

---


# Navigeren door de gebruikersinterface van Cloud Manager {#navigation}

Leer hoe de gebruikersinterface van Cloud Manager is georganiseerd en hoe u kunt navigeren om uw programma&#39;s en omgevingen te beheren.


De interface voor cloud-beheer bestaat voornamelijk uit twee grafische interfaces:

* [&#x200B; de Mijn console van Programma&#39;s &#x200B;](#my-programs-console) is waar u al uw programma&#39;s kunt bekijken en beheren.
* [&#x200B; het venster van het Overzicht van het Programma &#x200B;](#program-overview) is waar u het detail van kunt zien en een individueel programma beheren.

>[!TIP]
>
>Ook controleer de [&#x200B; onboarding documentatiereis &#x200B;](/help/journey-onboarding/overview.md) voor een volledig overzicht van hoe te met AEM as a Cloud Service het gebruiken van Cloud Manager in werking te stellen.


## AI Assistant in AEM

Voor klanten die [&#x200B; voltooide noodzakelijke criteria &#x200B;](/help/implementing/cloud-manager/ai-assistant-in-aem.md#get-access) hebben, is de Medewerker van AI in AEM beschikbaar aan gebruikers van hun organisatie. Zie [&#x200B; Medewerker AI in AEM &#x200B;](/help/implementing/cloud-manager/ai-assistant-in-aem.md).


## Mijn programmaconsole {#my-programs-console}

Wanneer u login in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en de aangewezen organisatie selecteert, komt u bij de **Mijn console van Programma&#39;s** aan.

![&#x200B; Mijn console van Programma&#39;s &#x200B;](assets/my-programs-console.png)

De console Mijn Programma&#39;s biedt een overzicht van alle programma&#39;s waartoe u toegang hebt in de geselecteerde organisatie. Het bestaat uit verschillende delen.

1. [&#x200B; Toolbars &#x200B;](#toolbars-my-programs-toolbars) voor organisatieselectie, alarm, en rekeningsmontages
1. Tabs waarmee u de huidige weergave van uw programma&#39;s kunt schakelen.
   * **Begin** mening (gebrek) die **Mijn mening van Programma&#39;s** met een overzicht van alle programma&#39;s selecteert
   * **Vergunning** die tot het [&#x200B; dashboard van de Vergunning &#x200B;](/help/implementing/cloud-manager/license-dashboard.md) toegang heeft.
   * Merk op dat het gebrek van lusjes aan gesloten en kan worden onthuld gebruikend ![&#x200B; het menupictogram van de Show &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) in de [&#x200B; kopbal van Cloud Manager &#x200B;](#cloud-manager-header).
1. [&#x200B; Statistieken en call-to-action &#x200B;](#statistics) voor een overzicht van uw recente activiteit
1. [**Mijn Programma&#39;s** sectie &#x200B;](#my-programs-section) met een overzicht van al uw programma&#39;s
1. [&#x200B; Snelle verbindingen &#x200B;](#quick-links-section) om tot verwante middelen gemakkelijk toegang te hebben.

>[!TIP]
>
>Zie [&#x200B; Programma&#39;s en de Types van Programma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) voor details op programma&#39;s.

### Werkbalken {#my-programs-toolbars}

Er staan twee werkbalken boven op elkaar.

#### Cloud Manager header {#cloud-manager-header}

De eerste is de Cloud Manager header, die blijvend is terwijl je door Cloud Manager navigeert. Het is een anker dat u toegang geeft tot instellingen en informatie die van toepassing zijn op alle Cloud Manager-programma&#39;s.

![&#x200B; de kopbal van Experience Cloud &#x200B;](assets/experience-cloud-header.png)

1. Klik ![&#x200B; tonen menupictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) (toon of verberg zijmenu) om u toegang tot een verscheidenheid van lusjes te geven die u aan specifieke delen van een individueel programma kunnen nemen. Of, kunt u tussen het [&#x200B; dashboard van de Vergunning &#x200B;](/help/implementing/cloud-manager/license-dashboard.md) en de **[Mijn console van Programma&#39;s](#my-programs-console)** afhankelijk van de context schakelen.
1. Klik op de knop Adobe Cloud Manager om terug te keren naar de My Programs console van Cloud Manager, waar u zich ook in Cloud Manager bevindt.
1. Klik **Terugkoppeling** om terugkoppelen aan Adobe over Cloud Manager te verstrekken.
1. Klik de organisatieselecteur toont de organisatie die u momenteel wordt ondertekend (in dit voorbeeld, de Interne Stichting van de Stichting). Klik om over te schakelen naar een andere organisatie als uw Adobe ID aan meerdere organisaties is gekoppeld.
1. Klik ![&#x200B; Apps pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) (de schakelaar van Oplossingen) om snel aan andere oplossingen van Experience Cloud te springen.
1. Klik ![&#x200B; pictogram van de Hulp &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Help_18_N.svg) om u snelle toegang tot het leren en steunmiddelen te geven.
1. Klik het pictogram van de Bell ![&#x200B; (](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) Meldingen [) om berichten en aankondigingen, onder andere te zien.](/help/implementing/cloud-manager/notifications.md)
1. Klik op het pictogram voor gebruikerstoegang tot uw gebruikersinstellingen. Als u geen gebruikersbeeld hebt gevormd, wordt een pictogram willekeurig toegewezen.

#### Programmawerkbalk {#program-toolbar}

Op de werkbalk van het programma vindt u koppelingen naar de verschillende Cloud Manager-programma&#39;s en naar acties die binnen de context passen.

![&#x200B; de toolbar van het Programma &#x200B;](assets/program-toolbar.png)

1. De **Mijn selecteur van Programma&#39;s** opent een drop-down waar u andere programma&#39;s kunt selecteren of context-aangewezen acties zoals het creëren van een nieuw programma nemen
1. De **Begonnen** verbinding geeft u toegang tot [&#x200B; op het instappen documentatiereis &#x200B;](/help/journey-onboarding/overview.md) om u met Cloud Manager in werking te stellen.
1. Met de knop Handeling kunt u contextgerichte acties uitvoeren, zoals het toevoegen van een programma.

### Statistieken en oproep tot actie {#statistics}

De sectie Statistieken en call-to-action bevat geaggregeerde gegevens voor uw organisatie. Als u bijvoorbeeld uw programma&#39;s hebt ingesteld, kunnen statistieken van uw activiteiten in de afgelopen 90 dagen worden weergegeven, zoals:

* Aantal [&#x200B; plaatsingen &#x200B;](/help/implementing/cloud-manager/deploy-code.md)
* Aantal [&#x200B; geïdentificeerde kwesties van de 0&rbrace; codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)
* Aantal builds

Of als u net de opstelling van uw org begint, zou er uiteinden op volgende stappen of documentatiemiddelen kunnen zijn.

### Sectie Mijn programma&#39;s {#my-programs-section}

De belangrijkste inhoud van de **Mijn console van Programma&#39;s** is de lijst van programma&#39;s in de **Mijn 3&rbrace; sectie van Programma&#39;s.**

De **Mijn van Programma&#39;s** sectie maakt een lijst van kaarten die elk programma vertegenwoordigen. Klik een kaart om tot de **pagina van het Overzicht van het Programma** van het programma voor details over het programma toegang te hebben.

>[!NOTE]
>
>Afhankelijk van uw rechten kunt u bepaalde programma&#39;s mogelijk niet selecteren.


Gebruik de sorteeropties om het gewenste programma gemakkelijker te vinden.

![&#x200B; het Sorteren opties &#x200B;](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Sorteren op:
   * **Gemaakte Datum** (gebrek)
   * **Naam van het Programma**
   * **Status**
* ![&#x200B; de orde van de Sortering neer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) Ascending (gebrek) / ![&#x200B; de orde van de Sortering omhoog pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Aflopend
* ![&#x200B; het Klassieke pictogram van de netmening &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) Mening van het Net (gebrek)
* ![&#x200B; het lijstpictogram van de Mening van de Mening &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ViewList_18_N.svg)

#### Programmakaarten {#program-cards}

Een kaart (of rij in een tabel) vertegenwoordigt elk programma en biedt een overzicht van het programma en snelle koppelingen om actie te ondernemen.

![&#x200B; kaart van het Programma &#x200B;](assets/program-card.png)

* Beeld verbonden aan het Programma, indien gevormd. De bovenstaande afbeelding is &quot;WKND&quot;.
* Naam die aan het Programma wordt toegewezen. In de bovenstaande afbeelding ziet u &quot;SecurBank Sample&quot; als de naam van het programma.
* Servicetype:
   * **Experience Manager Cloud** — voor de programma&#39;s van AEM as a Cloud Service
   * **Experience Manager** — voor [&#x200B; AMS (Adobe Managed Services) programma&#39;s &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction)
* [&#x200B; Type van Programma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md):
   * Sandbox
   * Productie
* Status. In de bovenstaande afbeelding is de status Gereed met een vinkje.
* Gevormde oplossingen. In de bovenstaande afbeelding zijn Sites en Assets de geconfigureerde oplossingen.
* Aanmaakdatum.

Een productieprogramma kan zijn voorzien van een badged om extra eigenschappen te tonen u op het tijdstip koos u het, zoals het volgende toevoegde:

* ![&#x200B; HIPAA badge &#x200B;](assets/hipaa.png) [&#x200B; HIPAA &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* ![&#x200B; WAF-DDOS badge &#x200B;](assets/waf-ddos-protection.png) [&#x200B; bescherming WAF-DDOS &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* [99,99% SLA (Service level agreement)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

Met het informatiepictogram hebt u ook snel toegang tot aanvullende informatie over het programma (nuttig in de lijstweergave).

![&#x200B; Informatie &#x200B;](assets/information-list-view.png)

Het ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_22/Smock_More_22_N.svg) pictogram geeft u toegang tot extra acties u het programma kunt nemen.

![&#x200B; knoop van de Ellipsis voor programma&#39;s &#x200B;](assets/program-ellipsis.png)

* Navigeer aan een bepaald ![&#x200B; pictogram van Gegevens &#x200B;](https://spectrum.adobe.com/static/icons/workflow_22/Smock_Data_22_N.svg) [&#x200B; Milieu &#x200B;](/help/implementing/cloud-manager/manage-environments.md) van het programma
* Open het ![&#x200B; pictogram van het Overzicht van het Programma &#x200B;](/help/implementing/cloud-manager/assets/program-overview.svg) [&#x200B; Overzicht van het Programma &#x200B;](#program-overview)
* ![&#x200B; geef pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) uit [&#x200B; geef het programma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing) uit
* ![&#x200B; het pictogram van de Schrapping &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) [&#x200B; schrap een zandbakprogramma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>Raadpleeg de volgende secties voor meer informatie over programma&#39;s en het toevoegen en beheren van programma&#39;s:
>
>* [&#x200B; Programma&#39;s en de Types van Programma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [&#x200B; creeer productieprogramma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
>* [&#x200B; creeer zandbakprogramma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)


### Sectie Snelle koppelingen {#quick-links-section}

De snelle sectie van verbindingen geeft u toegang tot algemeen gebruikte middelen die verwant zijn.

## Pagina met overzicht van programma&#39;s {#program-overview}

Wanneer een programma in de **[Mijn console van Programma&#39;s](#my-programs-console)** wordt geselecteerd, wordt u genomen aan de **pagina van het Overzicht van het Programma**.

![&#x200B; Overzicht van het Programma &#x200B;](assets/program-overview.png)

In het programmaoverzicht hebt u toegang tot alle details van een Cloud Manager-programma. Als **Mijn console van Programma&#39;s**, wordt het gemaakt van verscheidene delen.

1. [&#x200B; Toolbars &#x200B;](#program-overview-toolbar) om terug naar de Mijn console van Programma&#39;s snel te springen, en het programma te navigeren
1. [&#x200B; Lusjes &#x200B;](#program-tabs) om tussen verschillende aspecten van het programma te schakelen
1. A [&#x200B; call-to-action &#x200B;](#cta) die op de laatste acties van het programma wordt gebaseerd
1. Een [&#x200B; overzicht van de milieu&#39;s &#x200B;](#environments) van het programma
1. Een [&#x200B; overzicht van de pijpleidingen &#x200B;](#pipelines) van het programma
1. Een [&#x200B; overzicht van de prestaties &#x200B;](#performance) van het programma
1. Verbindingen met [&#x200B; nuttige middelen &#x200B;](#useful-resources)

### Werkbalken {#program-overview-toolbar}

De toolbars voor het programmaoverzicht zijn gelijkaardig aan die toolbars van de [&#x200B; Mijn console van Programma&#39;s &#x200B;](#my-programs-toolbars). Alleen de verschillen worden hier geïllustreerd.

#### Cloud Manager header {#cloud-manager-header-2}

In de linkerbovenhoek van de pagina bevindt zich de Adobe Cloud Manager-header. U kunt ![&#x200B; het menupictogram van de Zijde &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) klikken om het zijmenu van lusjes aan andere gebieden van de software te tonen of te verbergen.

![&#x200B; Cloud Manager zijmenu &#x200B;](assets/cloud-manager-hamburger.png)

Klik op Adobe Cloud Manager om terug te keren naar Home.

#### Programmawerkbalk {#program-toolbar-2}

Op de werkbalk van het programma hebt u nog steeds toegang om snel over te schakelen naar andere programma&#39;s, maar hebt u ook toegang tot contextgerichte acties, zoals het toevoegen en bewerken van het programma.

![&#x200B; de toolbar van het Programma &#x200B;](assets/cloud-manager-program-toolbar.png)

De toolbar toont altijd het lusje dat u momenteel bent, zelfs als u de lusjes gebruikend ![&#x200B; toont menupictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) hebt verborgen.

### Tabbladen van programma {#program-tabs}

Elk programma heeft talrijke opties en gegevens verbonden aan het. Deze opties en gegevens worden in tabbladen verzameld om het navigeren door het programma eenvoudiger te maken. Met de tabbladen hebt u toegang tot:

**Programma**

* ![&#x200B; Modern pictogram van de netmening &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ModernGridView_18_N.svg) Overzicht - het programmaoverzicht zoals die in het huidige document wordt beschreven
* ![&#x200B; het pictogram van de Bell &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) [&#x200B; Activiteit &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) - de geschiedenis van pijpleidingslooppas van het programma
* ![&#x200B; pictogram van het Werkschema &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) [&#x200B; Pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) - Alle pijpleidingen die voor het programma worden gevormd
* ![&#x200B; het pictogram van de Omslag &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) [&#x200B; Bewaarplaatsen &#x200B;](/help/implementing/cloud-manager/managing-code/managing-repositories.md) - Alle bewaarplaatsen die voor het programma worden gevormd
* ![&#x200B; het schijfpictogram van de Grafiek &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_GraphPie_18_N.svg) [&#x200B; Rapporten &#x200B;](/help/implementing/cloud-manager/reports/report-sla.md) - Metriek zoals de gegevens van SLA

**de Diensten**

* ![&#x200B; het pictogram van Gegevens &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) [&#x200B; Milieu&#39;s &#x200B;](/help/implementing/cloud-manager/manage-environments.md) - Alle milieu&#39;s die voor het programma worden gevormd
* ![&#x200B; het pictogram van de Web-pagina&#39;s &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) [&#x200B; Plaatsen van Edge Delivery &#x200B;](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md) - beheert de plaatsen van Edge Delivery
* ![&#x200B; pictogram van Montages &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) [&#x200B; Montages van het Domein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - beheer de namen van het douanedomein voor het programma
* ![&#x200B; Slot gesloten pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) [&#x200B; SSL Certificaten &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) - beheer SSL certificaten voor het programma
* ![&#x200B; &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) Toewijzingen van het Domein 1&rbrace; Sociale netwerkpictogram [&#x200B; - beheer de Toewijzingen van het Domein](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
* ![&#x200B; het lijstpictogram van de Taak &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) [`IP Allow Lists`](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) - bepaalt lijsten van gewenste personen voor bepaalde IP adressen
* ![&#x200B; het pictogram van de Doos &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) [&#x200B; Reeksen van de Inhoud &#x200B;](/help/implementing/developing/tools/content-copy.md) - Reeksen inhoud die voor exemplaardoeleinden wordt gecreeerd
* ![&#x200B; pictogram van de Geschiedenis &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) [&#x200B; de Activiteit van de Inhoud van het Exemplaar &#x200B;](/help/implementing/developing/tools/content-copy.md) - de activiteiten van het Inhoudsexemplaar
* ![&#x200B; pictogram van het Kanaal &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Channel_18_N.svg) [&#x200B; de Infrastructuur van het Netwerk &#x200B;](/help/security/configuring-advanced-networking.md) - beheer geavanceerde voorzien van een netwerkopties voor het programma

**Middelen**

* ![&#x200B; pictogram van het Boek &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Book_18_N.svg) het Leren Wegen - de Extra het leren middelen over Cloud Manager

Door gebrek, wanneer u een programma opent u op het **Overzicht** tabel aankomt. Het huidige tabblad wordt gemarkeerd. Selecteer een ander tabblad om de details ervan weer te geven.

In de upper-left hoek van de [&#x200B; kopbal van Cloud Manager &#x200B;](#cloud-manager-header-2), klik ![&#x200B; tonen menupictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu van lusjes te tonen of te verbergen.

### Call-to-action {#cta}

In de sectie call-to-action vindt u nuttige informatie, afhankelijk van de status van uw programma. Voor een nieuw programma, kunt u volgende stappen zien gegeven en een herinnering van een go-live datum, [&#x200B; die tijdens programmaverwezenlijking &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) wordt geplaatst.

![&#x200B; Call-to-action voor een nieuw programma &#x200B;](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Voor een levend programma, de status van uw laatste plaatsing met verbindingen voor details en het beginnen van een nieuwe plaatsing.

![&#x200B; Call-to-action &#x200B;](/help/implementing/cloud-manager/assets/info-banner.png)

### Milieukaart {#environments}

De **kaart van Milieu** geeft u een overzicht van uw milieu&#39;s en verbindingen voor snelle acties.

De **kaart van Milieu** maakt een lijst van slechts drie milieu&#39;s. Klik {het pictogram van het 0} Werkschema ![&#x200B; &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) tonen allen **om alle milieu&#39;s van het programma te zien.**

Zie ook [&#x200B; Milieu &#x200B;](/help/implementing/cloud-manager/manage-environments.md) beheren.

### Pipelkaart {#pipelines}

De **Pijpleidingen** kaart geeft u een overzicht van uw pijpleidingen en verbindingen voor snelle acties.

De **Pijpleidingen** kaart maakt slechts van drie pijpleidingen een lijst. Klik {het pictogram van het 0} Werkschema ![&#x200B; &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) tonen allen **om alle pijpleidingen van het programma te zien.**

Zie ook [&#x200B; leiden Pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) voor details op hoe te om uw pijpleidingen te beheren.

### Prestatiekaart {#performance}

De **kaart van Prestaties** geeft een overzicht van het **[CDN Dashboard](/help/implementing/cloud-manager/cdn-performance.md)**.

![&#x200B; kaart van Prestaties &#x200B;](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

### Nuttige bronnen {#useful-resources}

De **Nuttige 1&rbrace; sectie van Middelen &lbrace;verstrekt verbindingen aan extra het leren middelen voor Cloud Manager.**
