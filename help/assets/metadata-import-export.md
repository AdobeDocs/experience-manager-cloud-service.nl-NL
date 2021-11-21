---
title: Importeer/exporteer metadata van assets bulksgewijs
description: In dit artikel wordt beschreven hoe u metagegevens bulksgewijs kunt importeren en exporteren.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: fb70a068-3ba3-4459-952d-79155d286c42
source-git-commit: e7028272a32c2f53c3438cb918caaf04445442af
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 11%

---

# Importeer/exporteer metadata van assets bulksgewijs {#import-and-export-asset-metadata-in-bulk}

Met Adobe Experience Manager Assets kunt u metagegevens van elementen in bulk importeren met behulp van een CSV-bestand. U kunt bulkupdates uitvoeren voor de onlangs geüploade elementen of de bestaande elementen door een CSV-bestand te importeren. U kunt ook metagegevens van elementen bulksgewijs invoeren vanuit een systeem van derden in de CSV-indeling.

## Metagegevens importeren {#import-metadata}

De import van metagegevens is asynchroon en belemmert de systeemprestaties niet. Gelijktijdige update van de metagegevens voor meerdere elementen kan bronintensief zijn vanwege de activiteit voor het terugschrijven van metagegevens met behulp van de asset microservices. Adobe raadt u aan om bulkbewerkingen tijdens het gebruik van een slanke server te plannen, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

>[!NOTE]
>
>Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.

1. Navigeer naar de gebruikersinterface Middelen en tik/klik **[!UICONTROL Create]** op de werkbalk.
1. Selecteer **[!UICONTROL Metadata]** in het menu.
1. Tik of klik op de pagina **[!UICONTROL Metadata Import]** op **[!UICONTROL Select File]**. Selecteer het CSV-bestand met de metadata.
1. Geef de volgende parameters op:

   | Parameter | Beschrijving |
   | ---------------------- | ------- |
   | Batchgrootte | Aantal elementen in een batch waarvoor metagegevens moeten worden geïmporteerd. De standaardwaarde is 50. Maximumwaarde is 100. |
   | Veldscheidingsteken | Standaardwaarde is `,` (een komma). U kunt elk ander teken opgeven. |
   | Scheidingsteken voor meerdere waarden | Scheidingsteken voor metagegevenswaarden. De standaardwaarde is `|`. |
   | Workflows starten | Standaard false. Wanneer ingesteld op `true` en de standaardinstellingen zijn van kracht voor de DAM Metadata WriteBack-workflow (die metagegevens naar de binaire XMP schrijft). Als u de workflows inschakelt, wordt het systeem trager. |
   | Kolomnaam elementpad | Hiermee definieert u de kolomnaam voor het CSV-bestand met elementen. |

1. Klik op **[!UICONTROL Import]** op de werkbalk. Nadat de metagegevens zijn geïmporteerd, wordt een melding verzonden naar het Postvak Melding. Navigeer naar de eigenschappenpagina voor elementen en controleer of de metagegevenswaarden correct zijn geïmporteerd voor elementen.

Als u datum en tijdstempel wilt toevoegen tijdens het importeren van metagegevens, gebruikt u `YYYY-MM-DDThh:mm:ss.fff-00:00` notatie voor datum en tijd. Datum en tijd worden gescheiden door `T`, `hh` is uren in 24-uursnotatie, `fff` nanoseconden is, en `-00:00` is de verschuiving van de tijdzone. Bijvoorbeeld: `2020-03-26T11:26:00.000-07:00` is 26 maart 2020 om 11:26:00.000 AM PST-tijd.

>[!CAUTION]
>
>Als de datumnotatie niet overeenkomt `YYYY-MM-DDThh:mm:ss.fff-00:00`, worden de datumwaarden niet ingesteld. De datumnotaties van het geëxporteerde CSV-bestand met metagegevens hebben de indeling `YYYY-MM-DDThh:mm:ss-00:00`. Als u het wilt invoeren, zet het in het aanvaardbare formaat door de nanosecondenwaarde toe te voegen die door wordt aangegeven `fff`.

## Metagegevens exporteren {#export-metadata}

U kunt metagegevens voor meerdere elementen in CSV-indeling exporteren. De metagegevens worden asynchroon geëxporteerd en hebben geen invloed op de prestaties van het systeem. Als u metagegevens wilt exporteren, doorloopt Experience Manager de eigenschappen van het knooppunt Asset `jcr:content/metadata` en de onderliggende knooppunten en exporteert de eigenschappen van de metagegevens in een CSV-bestand.

Hier volgen enkele voorbeelden van het gebruik van metagegevens voor bulksgewijs exporteren:

* Importeer de metagegevens in een systeem van derden wanneer u elementen migreert.
* Metagegevens over elementen delen met een groter projectteam.
* Test of controleer de metagegevens op conformiteit.
* De metagegevens extern maken voor afzonderlijke lokalisatie.

1. Selecteer de elementenmap die elementen bevat waarvoor u metagegevens wilt exporteren. Selecteer **[!UICONTROL Export metadata]** in de werkbalk.
1. Geef in het dialoogvenster Metagegevens exporteren een naam op voor het CSV-bestand. Selecteer **[!UICONTROL Include assets in subfolders]**.

   ![Interface en opties voor het exporteren van metagegevens van alle elementen in een map](assets/export_metadata_page.png "Interface en opties voor het exporteren van metagegevens van alle elementen in een map")

1. Selecteer de gewenste opties. Geef een bestandsnaam en zo nodig een datum op.

1. In de **[!UICONTROL Properties to be exported]** -veld, geeft u op of u alle of specifieke eigenschappen wilt exporteren. Als u Selectieve eigenschappen kiest die u wilt exporteren, voegt u de gewenste eigenschappen toe.

1. Tik/klik op de werkbalk **[!UICONTROL Export]**. Een bericht bevestigt dat de metagegevens worden geëxporteerd. Sluit het bericht.
1. Open het bericht in het Postvak IN voor de exporttaak. Selecteer de taak en klik op **[!UICONTROL Open]** op de werkbalk. Tik of klik op **[!UICONTROL CSV Download]** op de werkbalk om het CSV-bestand met de metadata te downloaden. Klik op **[!UICONTROL Close]**.

   ![Dialoogvenster voor het downloaden van het CSV-bestand met metagegevens die bulksgewijs zijn geëxporteerd](assets/csv_download.png)

   *Afbeelding: Dialoogvenster voor het downloaden van het CSV-bestand met metagegevens die bulksgewijs zijn geëxporteerd.*

>[!MORELIKETHIS]
>
>* [Metagegevens importeren bij het importeren van elementen in bulk](/help/assets/add-assets.md#asset-bulk-ingestor)

