---
title: Rapporten over gebruik en delen
description: Rapporten over uw elementen in [!DNL Adobe Experience Manager Assets] waarmee u inzicht krijgt in het gebruik, de activiteiten en het delen van uw digitale middelen.
contentOwner: AG
feature: Asset Reports, Asset Management
role: Admin, User
exl-id: ef617b01-0019-4379-8d58-c03215d7e28f
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 3%

---

# Elementen rapporteren {#asset-reports}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/asset-reports.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Met Asset Reporting kunt u het nut van uw [!DNL Adobe Experience Manager Assets] implementatie. Met [!DNL Assets]kunt u verschillende rapporten genereren voor uw digitale middelen. De rapporten bevatten nuttige informatie over het gebruik van uw systeem, over de manier waarop gebruikers met elementen werken en over de elementen die u gebruikt <!-- downloaded and --> gedeeld.

Gebruik de informatie in de rapporten om belangrijke succesmetriek af te leiden om de goedkeuring te meten [!DNL Assets] binnen uw onderneming en door klanten.

De [!DNL Assets] rapportagekader gebruikt [!DNL Sling] banen aan asynchroon verwerken rapportverzoeken op ordelijke wijze. Het is schaalbaar voor grote opslagruimten. De asynchrone rapportverwerking verhoogt de efficiency en de snelheid waarmee de rapporten worden geproduceerd.

De interface van het rapportbeheer is intuïtief en omvat fijnkorrelige opties en controles om tot gearchiveerde rapporten toegang te hebben en de loopstatussen van het meningsrapport (succes, ontbroken, en een rij gevormd) in werking te stellen.

Wanneer een rapport wordt gegenereerd, ontvangt u een melding via <!-- through an email (optional) and --> een inbox-melding. U kunt een rapport weergeven, downloaden of verwijderen van de pagina met rapportlijsten waarop alle eerder gegenereerde rapporten worden weergegeven.

## Rapporten genereren {#generate-reports}

[!DNL Experience Manager Assets] Hiermee genereert u de volgende standaardrapporten:

* Uploaden
* Downloaden
* Verlopen
* Wijziging
* Publiceren
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

1. In [!DNL Experience Manager] interface, klik **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.

   ![Pagina Gereedschappen om te navigeren in middelenrapport](assets/navigation.png)

1. Op de [!UICONTROL Asset Reports] pagina, klikt u **[!UICONTROL Create]** op de werkbalk.
1. Van de **[!UICONTROL Create Report]** pagina, kiest u het rapport dat u wilt maken en klikt u op **[!UICONTROL Next]**.

   ![Rapporttype selecteren](assets/choose_report.png)

1. Configureer rapportdetails zoals titel, beschrijving, miniatuur en mappad. Standaard is het mappad `/content/dam`. U kunt een andere weg specificeren om het rapport over een specifieke omslag uit te voeren.

   ![Pagina om rapportdetails toe te voegen](assets/report_configuration.png)

   Kies het datumbereik voor uw rapport. U kunt ervoor kiezen het rapport nu of op een toekomstige datum en tijd te genereren.

   >[!NOTE]
   >
   >Als u ervoor kiest om het rapport later te plannen, zorg ervoor dat u de datum en de tijd in de gebieden van de Datum en van de Tijd specificeert. Als u geen waarde specificeert, behandelt de rapportmotor het als een rapport dat onmiddellijk moet worden geproduceerd.

   De gebieden van de configuratie kunnen verschillen gebaseerd op het type van rapport u creeert. Bijvoorbeeld de **[!UICONTROL Disk Usage]** rapport biedt opties voor het opnemen van elementen bij het berekenen van de schijfruimte die door elementen wordt gebruikt. U kunt ervoor kiezen om elementen in submappen op te nemen of uit te sluiten voor het berekenen van het schijfgebruik.

   >[!NOTE]
   >
   >Het rapport **[!UICONTROL Disk Usage]** bevat geen datumbereikvelden omdat het alleen het huidige gebruik van schijfruimte aangeeft.

   ![Pagina met details van rapport Schijfgebruik](assets/disk_usage_configuration.png)

   Wanneer u de opdracht **[!UICONTROL Files]** rapport, kunt u submappen opnemen/uitsluiten. U kunt echter geen elementuitvoeringen opnemen voor dit rapport.

   ![Pagina met details van rapport Bestanden](assets/files_report.png)

   De **[!UICONTROL Link Share]** rapport geeft URL&#39;s weer aan elementen die vanuit de toepassing worden gedeeld met externe gebruikers [!DNL Assets]. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> De kolommen kunnen niet worden aangepast.

   De **[!UICONTROL Link Share]** rapport, bevat geen opties voor submappen en uitvoeringen omdat alleen de gedeelde URL&#39;s worden gepubliceerd die onder `/var/dam/share`.

   ![De pagina van details van het rapport van het Aandeel van de Verbinding](assets/link_share.png)

1. Klik op **[!UICONTROL Next]** op de werkbalk.

1. In de **[!UICONTROL Configure Columns]** pagina, worden sommige kolommen geselecteerd om in het rapport door gebrek te verschijnen. U kunt meer kolommen selecteren. Annuleer de selectie van een kolom om deze uit te sluiten in het rapport.

   ![Selectie van rapportkolommen selecteren of annuleren](assets/configure_columns.png)

   Als u een aangepaste kolomnaam of een aangepast eigenschappenpad wilt weergeven, configureert u de eigenschappen voor het element binair onder het dialoogvenster `jcr:content` in CRX. U kunt dit ook toevoegen via de padkiezer voor eigenschappen.

   ![Selectie van rapportkolommen selecteren of annuleren](assets/custom_columns.png)

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht meldt dat de rapportgeneratie is in werking gesteld.
1. Op de [!UICONTROL Asset Reports] pagina, is de status van de rapportgeneratie gebaseerd op de huidige staat van de rapportbaan, bijvoorbeeld [!UICONTROL Success], [!UICONTROL Failed], [!UICONTROL Queued], of [!UICONTROL Scheduled]. Dezelfde status wordt weergegeven in het vak met meldingen. Klik op de rapportkoppeling om de rapportpagina weer te geven. U kunt ook het rapport selecteren en op **[!UICONTROL View]** op de werkbalk.

   <!--![A generated report](assets/report_page.png)-->
   ![gegenereerde rapportstatus](assets/report-status.JPG)

   Klikken **[!UICONTROL Download]** van de toolbar om het rapport in CSV formaat te downloaden.

   >[!NOTE]
   >
   >U kunt rapporten genereren op basis van de gebeurtenissen die in de afgelopen 360 dagen zijn gegenereerd. Experience Manager bewaart de gegevens van de gebruikers-id 30 dagen.

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
* Verlopen
* Wijziging
* Publiceren
* [!DNL Brand Portal] publish
* Bestanden

Ga als volgt te werk om aangepaste kolommen aan deze rapporten toe te voegen:

1. In de [!DNL Manager interface], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. Op de [!UICONTROL Asset Reports] pagina, klikt u **[!UICONTROL Create]** op de werkbalk.

1. Van de **[!UICONTROL Create Report]** pagina, kiest u een rapport dat u wilt maken. Klik op **[!UICONTROL Next]**.

1. Configureer de rapportdetails, zoals titel, beschrijving, miniatuur, mappad en datumbereik. Klik op **[!UICONTROL Next]**.

1. Selecteer de toepasselijke informatie in de lijst met **[!UICONTROL Default Columns]**. Als u een aangepaste kolom wilt weergeven, geeft u de naam op van de kolom onder **[!UICONTROL Custom Columns]**.

   ![Geef een naam op voor de aangepaste rapportkolom](assets/custom_columns-1.png)

1. Het pad naar de eigenschap toevoegen onder het dialoogvenster `jcr:content` knoop in CRXDE gebruikend de plukker van de bezitspad. U kunt ook het pad typen in het veld Pad eigenschap.

   ![Eigenschappenpad toewijzen vanuit paden in jcr:content](assets/property_picker.png)

   Klik op **[!UICONTROL Add]** en herhaal de bovenstaande stappen.

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht deelt mee dat de rapportgeneratie in werking wordt gesteld.

<!-- TBD: How to configure purge now? Is it using OSGi configurations?

## Configure purging service {#configure-purging-service}

To remove reports that you no longer require, configure the DAM Report Purge service from the web console to purge existing reports based on their quantity and age.

1. Access the web console (configuration manager) from `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL DAM Report Purge Service]** configuration.
1. Specify the frequency (time interval) for the purging service in the `scheduler.expression.name` field. You can also configure the age and the quantity threshold for reports.
1. Save the changes.
-->

## Problemen oplossen {#tips-troubleshoot}

* Als de [!UICONTROL Disk Usage Report] genereert niet en als u gebruikt [!DNL Dynamic Media], zorgt u ervoor dat alle elementen correct worden verwerkt. U lost de problemen op door de elementen opnieuw te verwerken en het rapport opnieuw te genereren.

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

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
