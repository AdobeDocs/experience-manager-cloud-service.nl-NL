---
title: Metagegevens van elementen in bulk importeren en exporteren
description: In dit artikel wordt beschreven hoe u metagegevens bulksgewijs kunt importeren en exporteren.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: fb70a068-3ba3-4459-952d-79155d286c42
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 4%

---

# Metagegevens van elementen in bulk importeren en exporteren {#import-and-export-asset-metadata-in-bulk}

Met Adobe Experience Manager Assets kunt u metagegevens van elementen in bulk importeren met behulp van een CSV-bestand. U kunt bulkupdates uitvoeren voor de onlangs geüploade elementen of de bestaande elementen door een CSV-bestand te importeren. U kunt ook metagegevens van elementen bulksgewijs invoeren vanuit een systeem van derden in de CSV-indeling.

## Metagegevens importeren {#import-metadata}

De import van metagegevens is asynchroon en belemmert de systeemprestaties niet. Gelijktijdige update van de metagegevens voor meerdere elementen kan bronintensief zijn vanwege de activiteit voor het terugschrijven van metagegevens met behulp van de asset microservices. Adobe raadt u aan om bulkbewerkingen tijdens het gebruik van een slanke server te plannen, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

>[!NOTE]
>
>Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.

1. Navigeer naar de gebruikersinterface van [!DNL Assets] , selecteer **[!UICONTROL Create]** op de werkbalk en kies **[!UICONTROL Metadata]** in het menu.
1. Klik op **[!UICONTROL Select File]** op de pagina **[!UICONTROL Metadata Import]** . Selecteer het CSV-bestand met de metadata.
1. Geef de volgende parameters op:

   | Parameter | Beschrijving |
   | ---------------------- | ------- |
   | Batchgrootte | Aantal elementen in een batch waarvoor metagegevens moeten worden geïmporteerd. De standaardwaarde is 50. Maximumwaarde is 100. |
   | Veldscheider | De standaardwaarde is `,` (een komma). U kunt elk ander teken opgeven. |
   | Scheidingsteken voor meerdere waarden | Scheidingsteken voor metagegevenswaarden. De standaardwaarde is `|` . |
   | Workflows starten | Standaard false. Wanneer deze eigenschap is ingesteld op `true` en de standaardinstellingen zijn van kracht voor de DAM Metadata WriteBack-workflow (die metagegevens naar de binaire XMP-gegevens schrijft). Als u de workflows inschakelt, wordt het systeem trager. |
   | Kolomnaam elementpad | Hiermee definieert u de kolomnaam voor het CSV-bestand met elementen. |

1. Selecteer **[!UICONTROL Import]** op de werkbalk. Nadat de metagegevens zijn geïmporteerd, wordt een melding verzonden naar het Postvak Melding. Navigeer naar de eigenschappenpagina voor elementen en controleer of de metagegevenswaarden correct zijn geïmporteerd voor elementen.

1. Als u datum en tijdstempel wilt toevoegen om de metagegevens te importeren, gebruikt u de `YYYY-MM-DDThh:mm:ss.fff-00:00` -indeling voor datum en tijd. Datum en tijd worden door `T` van elkaar gescheiden, `hh` is uren in 24-uursnotatie, `fff` is nanoseconden en `-00:00` is tijdzone-verschuiving. Bijvoorbeeld, `2020-03-26T11:26:00.000-07:00` is 26 Maart, 2020 bij 11 :26: 00.000 AM PST.

   * De datumnotatie is afhankelijk van de kolomkop en de notatie waarin deze staat. Als de datum bijvoorbeeld een klacht is met de indeling `yyyy-MM-dd'T'HH:mm:ssXXX` , moet de desbetreffende kolomkop `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` zijn.
   * De standaarddatumnotatie is `yyyy-MM-dd'T'HH:mm:ss.SSSXXX` .

<!-- Hidden via cqdoc-17869>

>[!CAUTION]
>
>If the date format does not match `YYYY-MM-DDThh:mm:ss.fff-00:00`, the date values are not set. The date formats of exported metadata CSV file is in the format `YYYY-MM-DDThh:mm:ss-00:00`. If you want to import it, convert it to the acceptable format by adding the nanoseconds value denoted by `fff`.
-->

## Metagegevens exporteren {#export-metadata}

U kunt metagegevens voor meerdere elementen in CSV-indeling exporteren. De metagegevens worden asynchroon geëxporteerd en hebben geen invloed op de prestaties van het systeem. Als u metagegevens wilt exporteren, doorloopt Experience Manager de eigenschappen van het knooppunt asset `jcr:content/metadata` en de onderliggende knooppunten en exporteert het de eigenschappen van metagegevens in een CSV-bestand.

Hier volgen enkele voorbeelden van het gebruik van metagegevens voor bulksgewijs exporteren:

* Importeer de metagegevens in een systeem van derden wanneer u elementen migreert.
* Metagegevens over elementen delen met een groter projectteam.
* Test of controleer de metagegevens op conformiteit.
* De metagegevens extern maken voor afzonderlijke lokalisatie.

>[!NOTE]
>
>Metagegevens worden beperkt tot 1.048.575 Assets, wat overeenkomt met de maximale werkbladgrootte in Microsoft Excel. Als een geëxporteerde hiërarchie meer dan dit aantal Assets bevat, worden alleen de metagegevens van de eerste 1.048.575 Assets opgenomen in het CSV-bestand.

1. Selecteer de elementenmap die elementen bevat waarvoor u metagegevens wilt exporteren. Selecteer **[!UICONTROL Export metadata]** in de werkbalk.
1. Geef in het dialoogvenster Metagegevens exporteren een naam op voor het CSV-bestand. Selecteer **[!UICONTROL Include assets in subfolders]** als u metagegevens voor elementen in submappen wilt exporteren.

   ![&#x200B; Interface en opties om meta-gegevens van alle activa in een omslag &#x200B;](assets/export_metadata_page.png " Interface en opties uit te voeren om meta-gegevens van alle activa in een omslag ") uit te voeren

1. Selecteer de gewenste opties. Geef een bestandsnaam en zo nodig een datum op.

1. Geef in het veld **[!UICONTROL Properties to be exported]** op of u alle of specifieke eigenschappen wilt exporteren. Als u Selectieve eigenschappen kiest die u wilt exporteren, voegt u de gewenste eigenschappen toe.

1. Selecteer **[!UICONTROL Export]** in de werkbalk. Een bericht bevestigt dat de metagegevens worden geëxporteerd. Sluit het bericht.
1. Open het bericht in het Postvak IN voor de exporttaak. Selecteer de taak en klik op **[!UICONTROL Open]** op de werkbalk. Als u het CSV-bestand met de metagegevens wilt downloaden, selecteert u **[!UICONTROL CSV Download]** op de werkbalk. Klik op **[!UICONTROL Close]**.

   ![&#x200B; Dialoog om het Csv- dossier te downloaden dat meta-gegevens bevat die in bulk worden uitgevoerd &#x200B;](assets/csv_download.png)

   *Cijfer: Dialoog om het Csv- dossier te downloaden dat meta-gegevens bevat die in bulk worden uitgevoerd.*

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [&#x200B; de meta-gegevens van de Invoer wanneer het invoeren van activa in bulk &#x200B;](/help/assets/add-assets.md#asset-bulk-ingestor)
