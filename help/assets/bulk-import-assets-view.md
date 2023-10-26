---
title: Bulkimportelementen met middelenweergave
description: Leer hoe u importmiddelen in bulk importeert met de gebruikersinterface voor nieuwe elementen (weergave Middelen). Hiermee kunnen beheerders een groot aantal elementen uit een gegevensbron importeren in AEM Assets.
exl-id: 10f9d679-7579-4650-9379-bc8287cb2ff1
source-git-commit: 88198e9333a7f706fc99e487d8cde84647fa111f
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# Bulkimportelementen met middelenweergave  {#bulk-import-assets-view}

Bulkimport in de weergave AEM Assets biedt beheerders de mogelijkheid om een groot aantal elementen uit een gegevensbron te importeren in AEM Assets. De beheerders hoeven geen afzonderlijke elementen of mappen meer te uploaden naar AEM Assets.

>[!NOTE]
>
>In de overzichtsweergave van de middelenweergave wordt dezelfde achtergrond gebruikt als in de bulkimportmodule van de Admin-weergave. Het biedt echter meer gegevensbronnen om uit te importeren en een gestroomlijnde gebruikerservaring.

U kunt elementen importeren uit de volgende gegevensbronnen:

* Azure
* AWS
* Google Cloud
* Dropbox
* OneDrive

## Vereisten {#prerequisites}

| Gegevensbron | Vereisten |
|-----|------|
| Azure | <ul> <li>Azure Storage Account </li> <li> Azure Blob Container <li> Azure Access Key of SAS Token op basis van de verificatiemodus </li></ul> |
| AWS | <ul> <li>AWS Region </li> <li> AWS Bucket <li> AWS Access Key </li><li> AWS Access-geheim </li></ul> |
| Google Cloud | <ul> <li>GCP-emmertje </li> <li> GCP-serviceaccount-e-mail <li> persoonlijke sleutel GCP-serviceaccount</li></ul> |
| Dropbox | <ul> <li>Client-id voor Dropbox (toepassingssleutel) </li> <li> Dropbox Client Secret (App-geheim)</li></ul> |
| OneDrive | <ul> <li>OneDrive-TENant-id  </li> <li> OneDrive-client-id</li><li> OneDrive-clientgeheim</li></ul> |

Naast deze vereisten op basis van de gegevensbron, moet u zich bewust zijn van de naam van de bronmap in uw gegevensbron die alle elementen bevat die naar AEM Assets moeten worden geïmporteerd.

## De toepassing voor ontwikkelaars van Dropboxxen configureren {#dropbox-developer-application}

Voordat u elementen van uw Dropbox-account naar AEM Assets importeert, moet u de ontwikkelaarstoepassing voor Dropboxxen maken en configureren.

Voer de volgende stappen uit:

1. Aanmelden bij uw [Dropbox account](https://www.dropbox.com/developers) en klik op **[!UICONTROL Create apps]**.

1. In de **[!UICONTROL Choose an API]** selecteert u het enige beschikbare keuzerondje.

1. In de **[!UICONTROL Choose the type of access you need]** selecteert u een van de volgende opties:

   * Selecteren **[!UICONTROL App folder]**, als u toegang nodig hebt tot één map die in uw toepassing is gemaakt in uw account voor Dropboxxen.

   * Selecteren **[!UICONTROL Full Dropbox]**, als u toegang tot alle bestanden en mappen in uw account voor Dropboxxen nodig hebt.

1. Geef een naam voor de toepassing op en klik op **[!UICONTROL Create app]**.

1. In de **[!UICONTROL Settings]** van uw toepassing, voeg het volgende aan toe **[!UICONTROL Redirect URIs]** sectie:

   * https://exc-unifiedcontent.experience.adobe.net

   * https://exc-unifiedcontent.experience-stage.adobe.net (alleen geldig voor Stage-omgevingen)

1. Kopieer de waarden voor de **[!UICONTROL App key]** en **[!UICONTROL App secret]** velden. De waarden zijn vereist tijdens het configureren van het bulkimportprogramma in AEM Assets.

1. Op de **[!UICONTROL Permissions]** -tabblad, voegt u de volgende machtigingen toe in het dialoogvenster **[!UICONTROL Individual scopes]** sectie.

   * account_info.read

   * files.metadata.read

   * files.content.read

   * files.content.write

1. Klikken **[!UICONTROL Submit]** om de wijzigingen op te slaan

## De OneDrive-ontwikkelaarstoepassing configureren {#onedrive-developer-application}

Voordat u middelen van uw OneDrive-account naar AEM Assets importeert, moet u eerst de OneDrive-ontwikkeltoepassing maken en configureren.

Voer de volgende stappen uit:

1. Aanmelden bij uw [OneDrive-account](https://portal.azure.com/#view/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) en klik op **[!UICONTROL New registration]**.

1. Geef een naam voor de toepassing op en selecteer **[!UICONTROL Accounts in this organizational directory only (Adobe only - Single tenant)]** van **[!UICONTROL Supported account types]** en klik op **[!UICONTROL Register]**. De toepassing is gemaakt.

1. Kopieer de waarden voor de velden van de client-id van de toepassing en de id van de gebruiker. De waarden zijn vereist tijdens het configureren van het bulkimportprogramma in AEM Assets.

1. Voer de volgende stappen uit om een certificaat toe te voegen:
   1. Klik op de overzichtspagina van de toepassing op **[!UICONTROL Add a certificate or secret]** en klik vervolgens op **[!UICONTROL New client secret]**.
   1. Geef een beschrijving en vervaldatum van het clientgeheim op en klik op **[!UICONTROL Add]**.
   1. Kopieer na het maken van het clientgeheim de **[!UICONTROL Value]** (Kopieer het veld Geheime-id niet). Dit is vereist tijdens het configureren van bulkimport in AEM Assets.

1. Voer de volgende stappen uit om omleidings URIs toe te voegen:
   1. Klik op de overzichtspagina van de toepassing op **[!UICONTROL Add a Redirect URI]** > **[!UICONTROL Add a platform]** > **[!UICONTROL Web]**.
   1. Voeg het volgende toe aan de **[!UICONTROL Redirect URIs]** sectie:

      * https://exc-unifiedcontent.experience.adobe.net

      * https://exc-unifiedcontent.experience-stage.adobe.net (alleen geldig voor Stage-omgevingen)

      Voeg de eerste URI toe en klik **[!UICONTROL Configure]** toevoegen. U kunt meer toevoegen door op **[!UICONTROL Add URI]** beschikbaar in het dialoogvenster **[!UICONTROL Web]** de **[!UICONTROL Authentication]** pagina.

1. Voer de volgende stappen uit om API-machtigingen voor de toepassing toe te voegen:
   1. Klikken **[!UICONTROL API permissions]** in linkerdeelvenster en klik op **[!UICONTROL Add a permission]**.
   1. Klik op **[!UICONTROL Microsoft Graph]** > **[!UICONTROL Delegated permissions]**. De **[!UICONTROL Select Permission]** geeft de beschikbare machtigingen weer.
   1. Selecteren `offline_access` machtiging van `OpenId permissions` en `Files.ReadWrite.All` machtiging van `Files`.
   1. Klikken **[!UICONTROL Add permissions]** om de updates op te slaan.




## Configuratie voor bulkimport maken {#create-bulk-import-configuration}

Voer de volgende stappen uit om een bulkimportconfiguratie tot stand te brengen:

1. Navigeren naar **[!UICONTROL Settings]** > **[!UICONTROL Bulk Import]** en klik op **[!UICONTROL Create Import]**.
1. Selecteer de gegevensbron. Tot de beschikbare opties behoren Azure, AWS, Google Cloud en Dropbox.
1. Geef een naam op voor de configuratie voor bulkimport in het dialoogvenster **[!UICONTROL Name]** veld.
1. Geef de specifieke gegevens voor de gegevensbron op, zoals vermeld in [Vereisten](#prerequisites).
1. Geef de naam op van de map die elementen bevat in de gegevensbron in het dialoogvenster **[!UICONTROL Source Folder]** veld.

   >[!NOTE]
   >
   >Als u Dropbox als gegevensbron gebruikt, specificeer de bronomslagweg die op de volgende regels wordt gebaseerd:
   >* Als u **Volledige Dropbox** tijdens het maken van de Dropbox-toepassing en de map met de elementen bestaat in `https://www.dropbox.com/home/bulkimport-assets`en vervolgens `bulkimport-assets` in de **[!UICONTROL Source Folder]** veld.
   >* Als u **App-map** tijdens het maken van de Dropbox-toepassing en de map met de elementen bestaat in `https://www.dropbox.com/home/Apps/BulkImportAppFolderScope/bulkimport-assets`en vervolgens `bulkimport-assets` in de **[!UICONTROL Source Folder]** veld, waarin `BulkImportAppFolderScope` verwijst naar de naam van de toepassing. `Apps` wordt automatisch toegevoegd na `home` in dit geval.

1. (Optioneel) Selecteer de optie **[!UICONTROL Delete source file after import]** als u de oorspronkelijke bestanden uit de opslagplaats van brongegevens wilt verwijderen nadat de bestanden in Experience Manager Assets zijn geïmporteerd.
1. Selecteer de **[!UICONTROL Import Mode]**. Selecteren **[!UICONTROL Skip]**, **[!UICONTROL Replace]**, of **[!UICONTROL Create Version]**. De modus Overslaan is de standaardinstelling en in deze modus slaat de functie Instantor over om een element te importeren als dit al bestaat.
   ![Brondetails importeren](/help/assets/assets/bulk-import-source-details.png)

1. (Optioneel) Geef het metagegevensbestand op dat u wilt importeren, in CSV-indeling, in het veld Metagegevensbestand en klik op **[!UICONTROL Next]** om te navigeren naar **[!UICONTROL Location & Filters]**.
1. Om een plaats in DAM te bepalen waar de activa moeten worden ingevoerd gebruikend **[!UICONTROL Assets Target Folder]** veld, geeft u een pad op. Bijvoorbeeld, `/content/dam/imported_assets`.
1. (Optioneel) In het dialoogvenster **[!UICONTROL Choose Filters]** de minimale bestandsgrootte van elementen opgeven in MB om deze op te nemen in het innameproces in het dialoogvenster **[!UICONTROL Filter by Min Size]** veld.
1. (Optioneel) Geef de maximale bestandsgrootte van elementen op in MB om ze op te nemen in het innameproces in het dialoogvenster **[!UICONTROL Filter by Max Size]** veld.
1. (Optioneel) Selecteer de MIME-typen die u in het innameproces wilt opnemen met behulp van het **[!UICONTROL Include MIME Type]** veld. U kunt meerdere MIME-typen selecteren in dit veld. Als u geen waarde definieert, worden alle MIME-typen opgenomen in het innameproces.

1. (Optioneel) Selecteer de MIME-typen die u wilt uitsluiten in het innameproces met behulp van het **[!UICONTROL Exclude MIME Type]** veld. U kunt meerdere MIME-typen selecteren in dit veld. Als u geen waarde definieert, worden alle MIME-typen opgenomen in het innameproces.

   ![Bulkimportfilters](assets/bulk-import-location.png)

1. Klik op **[!UICONTROL Next]**. Selecteren **[!UICONTROL Save & run import]** om de configuratie op te slaan en de bulkimport uit te voeren. Selecteren **[!UICONTROL Save import]** om de configuratie voor nu op te slaan zodat u het later kunt in werking stellen.

   ![bulkimport uitvoeren](assets/bulk-import-run.png)

1. Klikken **[!UICONTROL Save]** om de geselecteerde optie uit te voeren.

### Bestandsnamen verwerken tijdens bulkimport {#filename-handling-bulkimport-assets-view}

Wanneer u elementen of mappen in bulk importeert, [!DNL Experience Manager Assets] importeert de gehele structuur van wat er in de invoerbron bestaat. [!DNL Experience Manager] volgt de ingebouwde regels voor speciale tekens in de naam van het element en de map. Deze bestandsnamen moeten daarom worden ontsmet. Voor zowel de mapnaam als de elementnaam blijft de door de gebruiker gedefinieerde titel ongewijzigd en wordt deze opgeslagen in `jcr:title`.

Tijdens de bulkinvoer [!DNL Experience Manager] zoekt u naar de bestaande mappen om te voorkomen dat de elementen en mappen opnieuw worden geïmporteerd, en controleert u ook de ontsmettingsregels die zijn toegepast in de bovenliggende map waar het importeren plaatsvindt. Als de ontsmettingsregels worden toegepast in de bovenliggende map, worden dezelfde regels toegepast op de importbron. Voor nieuwe importbewerkingen worden de volgende ontsmettingsregels toegepast om de bestandsnamen van elementen en mappen te beheren.

Voor meer informatie over niet-toegestane namen, het verwerken van namen van elementen en het verwerken van mapnamen tijdens het importeren van grote hoeveelheden raadpleegt u [Bestandsnamen verwerken tijdens het bulkimporteren in de beheerweergave](add-assets.md##filename-handling-bulkimport).

## Bestaande configuraties voor bulkimport weergeven {#view-import-configuration}

Als u ervoor kiest om de configuratie op te slaan nadat u deze hebt gemaakt, wordt de configuratie weergegeven in het dialoogvenster **[!UICONTROL Saved Imports]** tab.

![Configuratie voor bulkimport opslaan](assets/bulk-import-save.png)

Als u het importeren opslaat en uitvoert, wordt de configuratie voor importeren weergegeven in het dialoogvenster **[!UICONTROL Executed Imports]** tab.

![Configuratie voor bulkimport opslaan](assets/bulk-import-executed.png)

Als u een importbewerking plant, wordt deze weergegeven in het dialoogvenster **[!UICONTROL Scheduled Imports]** tab.

## Configuratie voor bulkimport bewerken {#edit-import-configuration}

Als u de configuratiedetails wilt bewerken, klikt u op Meer opties (...) voor de configuratienaam en klikt u op **[!UICONTROL Edit]**. U kunt de titel van de configuratie en de gegevensbron van het voer niet uitgeven terwijl het uitvoeren van geeft verrichting uit. U kunt de configuratie bewerken met de tabbladen Uitgevoerde, Geplande of Opgeslagen importbestanden.

![Configuratie voor bulkimport bewerken](assets/bulk-import-edit.png)

## Eenmalige of herhaalde invoer plannen {#schedule-imports}

Voer de volgende stappen uit om een eenmalige of terugkerende bulkimport te plannen:

1. Klik op Meer opties (...) die overeenkomen met de configuratienaam die beschikbaar is in het dialoogvenster **[!UICONTROL Executed Imports]** of **[!UICONTROL Saved Imports]** en klik op **[!UICONTROL Schedule]**. U kunt een bestaande geplande import ook opnieuw plannen door naar **[!UICONTROL Scheduled Imports]** tabblad en klikken **[!UICONTROL Schedule]**.

1. Stel een eenmalige opname in of voer een uur-, dag- of wekelijks schema in. Klik op **[!UICONTROL Submit]**.

   ![Configuratie voor bulkimport plannen](assets/bulk-import-schedule.png)

## Een health check voor importeren uitvoeren {#import-health-check}

Als u de verbinding met de gegevensbron wilt valideren, klikt u op Meer opties (...) die overeenkomen met de configuratienaam en klikt u op **[!UICONTROL Check]**. Als de verbinding tot stand is gebracht, geeft Experience Manager Assets het volgende bericht weer:

![Health check van bulkinvoer](assets/bulk-import-health-check.png)

## Een droge run uitvoeren voordat het importeren wordt uitgevoerd {#dry-run-bulk-import}

Klik op Meer opties (...) voor de configuratienaam en klik op **[!UICONTROL Dry Run]** om een testlooppas voor de BulkTaak van de Invoer aan te halen. Experience Manager Assets geeft de volgende gegevens weer over de Bulk Import-taak:

![Health check van bulkinvoer](assets/bulk-import-dry-run.png)

## Een bulkimport uitvoeren {#run-bulk-import}

Als u het importeren hebt opgeslagen tijdens het maken van de configuratie, kunt u naar het tabblad Opgeslagen importbestanden navigeren, op Meer opties (...) voor de configuratie klikken en op **[!UICONTROL Run]**.

Op dezelfde manier als u een reeds uitgevoerde invoer moet uitvoeren, navigeer aan het Uitvoerde lusje van Invoer, klik Meer Opties (...) die aan de configuratienaam beantwoorden en klik **[!UICONTROL Run]**.

## Doorlopende import stoppen of plannen {#schedule-stop-ongoing-report}

U kunt een actieve bulkimport plannen of stoppen met behulp van het statusdialoogvenster voor bulkimport dat tijdens het importeren wordt weergegeven op de introductiepagina Bulk.

![Doorlopende import](assets/bulk-import-progress.png)

U kunt ook de elementen weergeven die in de doelmap zijn geïmporteerd door op **[!UICONTROL View Assets]**.


## Een configuratie voor bulkimport verwijderen {#delete-bulk-import-configuration}

Klik op Meer opties (...) die overeenkomen met de bestaande configuratienaam in **[!UICONTROL Executed Imports]**, **[!UICONTROL Scheduled Imports]**, of **[!UICONTROL Saved Imports]** tabs en klikken **[!UICONTROL Delete]** om de configuratie van de Invoer van het Bulk te schrappen.

## Navigeren naar elementen nadat bulkimport is uitgevoerd {#view-assets-after-bulk-import}

Klik op Meer opties (...) voor de configuratienaam om de doellocatie weer te geven waar de elementen worden geïmporteerd nadat de Bulkimporttaak is uitgevoerd. Klik vervolgens op **[!UICONTROL View Assets]**.
