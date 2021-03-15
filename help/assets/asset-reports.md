---
title: Rapporten over gebruik en delen
description: Meldt over uw middelen in [!DNL Adobe Experience Manager Assets] die u helpen gebruik, activiteit, en het delen van uw digitale activa begrijpen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dc6823d9a0dabcc4fe1537073d90ca53da205556
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 5%

---


# Rapporten over assets {#asset-reports}

Met Asset Reporting kunt u het nut van uw [!DNL Adobe Experience Manager Assets]-implementatie beoordelen. Met [!DNL Assets] kunt u verschillende rapporten genereren voor uw digitale middelen. De rapporten bevatten nuttige informatie over het gebruik van uw systeem, over de manier waarop gebruikers met elementen werken en over de elementen die <!-- downloaded and --> worden gedeeld.

Gebruik de informatie in de rapporten om zeer belangrijke succesmetriek af te leiden om de goedkeuring van [!DNL Assets] binnen uw onderneming en door klanten te meten.

Het [!DNL Assets] rapporteringskader gebruikt [!DNL Sling] banen om rapportverzoeken op geordende wijze asynchroon te verwerken. Het is schaalbaar voor grote opslagruimten. De asynchrone rapportverwerking verhoogt de efficiency en de snelheid waarmee de rapporten worden geproduceerd.

De interface van het rapportbeheer is intuïtief en omvat fijnkorrelige opties en controles om tot gearchiveerde rapporten toegang te hebben en de loopstatussen van het meningsrapport (succes, ontbroken, en een rij gevormd) in werking te stellen.

Wanneer een rapport wordt geproduceerd, wordt u via <!-- through an email (optional) and --> een inbox bericht op de hoogte gebracht. U kunt een rapport weergeven, downloaden of verwijderen van de pagina met rapportlijsten waarop alle eerder gegenereerde rapporten worden weergegeven.

## Rapporten genereren {#generate-reports}

[!DNL Experience Manager Assets] Hiermee genereert u de volgende standaardrapporten:

* Uploaden
* Verlopen
* Wijziging
* Publicatie
* [!DNL Brand Portal] publish
* Schijfgebruik
* Bestanden
* Delen van koppeling

<!-- Removed download report.
* Upload
* Download
* Expiration
* Modification
* Publish
* [!DNL Brand Portal] publish
* Disk Usage
* Files
* Link Share
-->

[!DNL Adobe Experience Manager] beheerders kunnen deze rapporten gemakkelijk produceren en aanpassen voor uw implementatie. Een beheerder kan deze stappen volgen om een rapport te produceren:

1. Klik in [!DNL Experience Manager] interface op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.

   ![Pagina Gereedschappen om te navigeren in middelenrapport](assets/navigation.png)

1. Klik op [!UICONTROL Asset Reports] op de werkbalk.**[!UICONTROL Create]**
1. Kies op de pagina **[!UICONTROL Create Report]** het rapport dat u wilt maken en klik op **[!UICONTROL Next]**.

   ![Rapporttype selecteren](assets/choose_report.png)

1. Configureer rapportdetails zoals titel, beschrijving, miniatuur en mappad in de CRX-opslagplaats waar het rapport wordt opgeslagen. Standaard is het mappad `/content/dam`. U kunt een ander pad opgeven.

   ![Pagina om rapportdetails toe te voegen](assets/report_configuration.png)

   Kies het datumbereik voor uw rapport. U kunt ervoor kiezen het rapport nu of op een toekomstige datum en tijd te genereren.

   >[!NOTE]
   >
   >Als u ervoor kiest om het rapport later te plannen, zorg ervoor dat u de datum en de tijd in de gebieden van de Datum en van de Tijd specificeert. Als u geen waarde specificeert, behandelt de rapportmotor het als een rapport dat onmiddellijk moet worden geproduceerd.

   De gebieden van de configuratie kunnen verschillen gebaseerd op het type van rapport u creeert. Het **[!UICONTROL Disk Usage]**-rapport bevat bijvoorbeeld opties voor het opnemen van elementen bij het berekenen van de schijfruimte die door elementen wordt gebruikt. U kunt ervoor kiezen om elementen in submappen op te nemen of uit te sluiten voor het berekenen van het schijfgebruik.

   >[!NOTE]
   >
   >Het rapport **[!UICONTROL Disk Usage]** bevat geen datumbereikvelden omdat het alleen het huidige gebruik van schijfruimte aangeeft.

   ![Detailpagina van rapport Schijfgebruik](assets/disk_usage_configuration.png)

   Wanneer u het **[!UICONTROL Files]** rapport creeert, kunt u subfolders omvatten/uitsluiten. U kunt echter geen elementuitvoeringen opnemen voor dit rapport.

   ![Pagina met details van rapport Bestanden](assets/files_report.png)

   Het **[!UICONTROL Link Share]** rapport toont URLs aan activa die met externe gebruikers van binnen [!DNL Assets] worden gedeeld. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> De kolommen kunnen niet worden aangepast.

   Het **[!UICONTROL Link Share]**-rapport bevat geen opties voor submappen en uitvoeringen omdat het alleen de gedeelde URL&#39;s publiceert die onder `/var/dam/share` worden weergegeven.

   ![De pagina van details van het rapport van het Aandeel van de Verbinding](assets/link_share.png)

1. Klik op **[!UICONTROL Next]** op de werkbalk.

1. Op de pagina **[!UICONTROL Configure Columns]** worden sommige kolommen geselecteerd om standaard in het rapport te verschijnen. U kunt meer kolommen selecteren. Annuleer de selectie van een kolom om deze uit te sluiten in het rapport.

   ![Selectie van rapportkolommen selecteren of annuleren](assets/configure_columns.png)

   Om een de naam of bezitspad van de douanekolom te tonen, vorm de eigenschappen voor de activa binair onder de `jcr:content` knoop in CRX. U kunt dit ook toevoegen via de padkiezer voor eigenschappen.

   ![Selectie van rapportkolommen selecteren of annuleren](assets/custom_columns.png)

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht meldt dat de rapportgeneratie is in werking gesteld.
1. Op de [!UICONTROL Asset Reports] pagina, is de status van de rapportgeneratie gebaseerd op de huidige staat van de rapportbaan, bijvoorbeeld [!UICONTROL Success], [!UICONTROL Failed], [!UICONTROL Queued], of [!UICONTROL Scheduled]. Dezelfde status wordt weergegeven in het vak met meldingen. Klik op de rapportkoppeling om de rapportpagina weer te geven. U kunt ook het rapport selecteren en op **[!UICONTROL View]** op de werkbalk klikken.

   ![Een gegenereerd rapport](assets/report_page.png)

   Klik **[!UICONTROL Download]** van de toolbar om het rapport in formaat te downloaden CSV.

## Aangepaste kolommen toevoegen aan rapporten {#add-custom-columns}

U kunt douanekolommen aan de volgende rapporten toevoegen om meer gegevens voor uw douanevereisten te tonen:

<!-- Remove download report.
* Upload
* Download
* Expiration
* Modification
* Publish
* [!DNL Brand Portal] publish
* Files
-->

* Uploaden
* Downloaden
* Verlopen
* Wijziging
* Publicatie
* [!DNL Brand Portal] publish
* Bestanden

Ga als volgt te werk om aangepaste kolommen aan deze rapporten toe te voegen:

1. Klik in [!DNL Manager interface] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. Klik op [!UICONTROL Asset Reports] op de werkbalk.**[!UICONTROL Create]**

1. Kies op de pagina **[!UICONTROL Create Report]** een rapport dat u wilt maken. Klik op **[!UICONTROL Next]**.

1. Configureer de rapportdetails, zoals titel, beschrijving, miniatuur, mappad en datumbereik. Klik op **[!UICONTROL Next]**.

1. Selecteer de toepasselijke informatie in de lijst van **[!UICONTROL Default Columns]**. Als u een aangepaste kolom wilt weergeven, geeft u de naam van de kolom op onder **[!UICONTROL Custom Columns]**.

   ![Geef een naam op voor de aangepaste rapportkolom](assets/custom_columns-1.png)

1. Voeg het bezitspad onder de `jcr:content` knoop in CRXDE toe gebruikend de plukker van de bezitspad. U kunt ook het pad typen in het veld Pad eigenschap.

   ![Eigenschappenpad toewijzen vanuit paden in jcr:content](assets/property_picker.png)

   Als u meer aangepaste kolommen wilt toevoegen, klikt u op **[!UICONTROL Add]** en herhaalt u de bovenstaande stappen.

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht deelt mee dat de rapportgeneratie in werking wordt gesteld.

<!-- TBD: How to configure purge now? Is it using OSGi configurations?

## Configure purging service {#configure-purging-service}

To remove reports that you no longer require, configure the DAM Report Purge service from the web console to purge existing reports based on their quantity and age.

1. Access the web console (configuration manager) from `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL DAM Report Purge Service]** configuration.
1. Specify the frequency (time interval) for the purging service in the `scheduler.expression.name` field. You can also configure the age and the quantity threshold for reports.
1. Save the changes.
-->

## Informatie over probleemoplossing {#tips-troubleshoot}

* Als [!UICONTROL Disk Usage Report] niet produceert en als u [!DNL Dynamic Media] gebruikt, zorg ervoor dat alle activa correct te werk gaan. U lost de problemen op door de elementen opnieuw te verwerken en het rapport opnieuw te genereren.

<!-- These notes were present in generate report section above. Removing commented text from in between the instructions to preserve the numbering of the ordered list.

TBD: How do enable this in CS now? Is it done using some OSGi config now?
   >[!NOTE]
   >
   >Before you can generate an **[!UICONTROL Asset Downloaded]** report, ensure that the Asset Download service is enabled. From the web console (`https://[aem_server]:[port]/system/console/configMgr`), open the **[!UICONTROL Day CQ DAM Event Recorder]** configuration, and select the **[!UICONTROL Asset Downloaded (DOWNLOADED)]** option in Event Types if not already selected.
-->

<!-- Removed download report.
   >[!NOTE]
   >
   >By default, the Content Fragments and link shares are included in the asset [!UICONTROL Download] report. Select the appropriate option to create a report of link shares or to exclude Content Fragments from the download report.

   >[!NOTE]
   >
   >The [!UICONTROL Download] report displays details of only those assets which are downloaded after selecting individually or are downloaded using Quick Action. However, it does not include the details of the assets that are inside a downloaded folder.
-->
