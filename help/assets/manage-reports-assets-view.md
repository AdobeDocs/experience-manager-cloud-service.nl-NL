---
title: Rapporten beheren in de middelenweergave
description: Open de gegevens in de sectie Rapporten van de mening van Activa om product en eigenschapgebruik te beoordelen en inzichten van zeer belangrijke succesmetriek af te leiden.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
source-git-commit: 6dc6b3e4ec9d6a816d92152cb535cd9a5d56a3b0
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 1%

---

# Rapporten beheren {#manage-reports}

Asset Reporting geeft beheerders inzicht in de activiteiten van de Adobe Experience Manager Assets View-omgeving. Deze gegevens bevatten nuttige informatie over de manier waarop gebruikers met inhoud en het product werken. Alle gebruikers kunnen tot het dashboard van Inzichten toegang hebben en degenen die aan het het productprofiel van Beheerders worden toegewezen kunnen user-defined rapporten tot stand brengen.

## Toegangsrapporten {#access-reports}

Alle gebruikers die zijn toegewezen aan het productprofiel voor middelenweergavebeheerders hebben toegang tot het dashboard Inzichten of kunnen door de gebruiker gedefinieerde rapporten maken in de weergave Elementen.

Ga naar om rapporten te openen **[!UICONTROL Reports]** krachtens **[!UICONTROL Settings]**.

![Rapporten](assets/reports.png)
<!--
In the **[!UICONTROL Reports]** screen, various components are shown in the tabular format which includes the following:

* **Title**: Title of the report
* **Type**: Determines whether the report is uploaded or downloaded to the repository
* **Description**: Provide details of the report that was given during uploading/downloading the report
* **Status**: Determines whether the report is completed, under progress, or deleted.
* **Author**: Provides email of the author who has uploaded/downloaded the report.
* **Created**: Gives information of the date when the report was generated.
-->

## Inzichten weergeven {#view-live-statistics}

In de weergave Elementen kunt u realtime gegevens voor de weergave Elementen weergeven met het dashboard Inzichten. U kunt real-time gebeurtenismetriek tijdens de laatste 30 dagen of voor de laatste 12 maanden bekijken.

<!--![Toolbar options when you select an asset](assets/assets-essentials-live-statistics.png)-->

Klikken **[!UICONTROL Insights]** U kunt de volgende automatisch gegenereerde grafieken weergeven in het linkernavigatiegebied:

* **Downloads**: Het aantal elementen dat in de afgelopen 30 dagen of 12 maanden is gedownload van de weergaveomgeving Elementen dat met een lijngrafiek wordt weergegeven.
  ![inzichten downloaden](/help/assets/assets/insights-downloads2341.svg)

* **Uploads**: Het aantal elementen dat in de weergaveomgeving van Elementen is geüpload in de laatste 30 dagen of twaalf maanden die met een lijngrafiek worden weergegeven.
  ![inzichten uploaden](/help/assets/assets/insights-uplods2.svg)
  <!--* **Asset Count by Size**: The division of count of assets based on their range of various sizes from 0 MB to 100 GB.-->

* **Opslaggebruik**: Het opslaggebruik, in bytes, voor de de meningsmilieu van Activa die gebruikend een bar grafiek wordt vertegenwoordigd.
  ![inzichten uploaden](/help/assets/assets/insights-storage-usage1.svg)
  <!--* **Delivery**: The graph depicts the count of assets as the delivery dates.-->

<!--* **Asset Count by Asset Type**: Represents count of various MIME types of the available assets. For example, application/zip, image/png, video/mp4, application/postscripte.-->

* **Meest gebruikte zoekopdrachten**: Bekijk de belangrijkste gezochte termen samen met het aantal keren dat deze termen in de weergaveomgeving van de Middelen zijn doorzocht in de laatste 30 dagen of 12 maanden, weergegeven in een tabelindeling.
  ![inzichten uploaden](/help/assets/assets/insights-top-search.svg)
  <!--
   ![Insights](assets/insights1.png)
   ![Insights](assets/insights2.png)
   -->

* **Aantal elementen op grootte:** Hiermee segmenteert u het totale aantal elementen in uw omgeving van de middelenweergave in verschillende groottebereiken, waarbij het aantal en het percentage elementen in elk groottebereik worden gemarkeerd met behulp van een donutgrafiek.
  ![inzichten-activa-telling-door grootte](/help/assets/assets/insights-assets-count-by-size.svg)
* **Aantal elementen per type element:** Hiermee segmenteert u het totale aantal elementen in de omgeving van de middelenweergave, waarbij het aantal en het percentage van de elementen wordt gemarkeerd op basis van hun bestandstypen, weergegeven in het donutdiagram.
  ![inzichten-activa-telling-door grootte](/help/assets/assets/insights-assest-count-by-asset-type1.svg)

## Een downloadrapport maken {#create-download-report}

Een downloadrapport maken:

1. Navigeren naar **[!UICONTROL Settings]** > **[!UICONTROL Reports]** en klik op **[!UICONTROL Create Report]**.

1. In de [!UICONTROL Configuration] tab, specificeer het rapporttype als **[!UICONTROL Download]**.

1. Geef een titel en een optionele beschrijving voor het rapport op.

1. Selecteer het mappad, waarin de elementen staan waarmee het rapport moet worden uitgevoerd. Gebruik hiervoor de optie **[!UICONTROL Select Folder Path]** veld.

1. Selecteer het datuminterval voor het rapport.

   >[!NOTE]
   >
   > In de weergave Elementen worden alle lokale tijdzones omgezet in UTC (Coordinated Universal Time).

1. In de [!UICONTROL Columns] selecteert u de kolomnamen die u in het rapport wilt weergeven.

1. Klik op **[!UICONTROL Create]**.

   ![Rapport downloaden](assets/download-reports-config.png)

De volgende lijst verklaart het gebruik van alle kolommen die u aan het rapport kunt toevoegen:

<table>
    <tbody>
     <tr>
      <th><strong>Kolomnaam</strong></th>
      <th><strong>Beschrijving</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>De titel van het element.</td>
     </tr>
     <tr>
      <td>Pad</td>
      <td>Het mappad waar het element beschikbaar is in de middelenweergave.</td>
     </tr>
     <tr>
      <td>MIME-type</td>
      <td>Het MIME-type voor het element.</td>
     </tr>
     <tr>
      <td>Grootte</td>
      <td>De grootte van het element in bytes.</td>
     </tr>
     <tr>
      <td>Gedownload door</td>
      <td>De e-mailid van de gebruiker die het element heeft gedownload.</td>
     </tr>
     <tr>
      <td>Downloaddatum</td>
      <td>De datum waarop de handeling voor het downloaden van middelen wordt uitgevoerd.</td>
     </tr>
     <tr>
      <td>Auteur</td>
      <td>De auteur voor het element.</td>
     </tr>
     <tr>
      <td>Aanmaakdatum</td>
      <td>De datum waarop het element is geüpload naar de middelenweergave.</td>
     </tr>
     <tr>
      <td>Wijzigingsdatum</td>
      <td>De datum waarop het element voor het laatst is gewijzigd.</td>
     </tr>
     <tr>
      <td>Verlopen</td>
      <td>De vervalstatus van het actief.</td>
     </tr>
     <tr>
      <td>Gedownload op gebruikersnaam</td>
      <td>De naam van de gebruiker die het element heeft gedownload.</td>
     </tr>           
    </tbody>
   </table>

## Een rapport voor uploaden maken {#create-upload-report}

Een rapport voor uploaden maken:

1. Navigeren naar **[!UICONTROL Settings]** > **[!UICONTROL Reports]** en klik op **[!UICONTROL Create Report]**.

1. In de [!UICONTROL Configuration] tab, specificeer het rapporttype als **[!UICONTROL Upload]**.

1. Geef een titel en een optionele beschrijving voor het rapport op.

1. Selecteer het mappad, waarin de elementen staan waarmee het rapport moet worden uitgevoerd. Gebruik hiervoor de optie **[!UICONTROL Select Folder Path]** veld.

1. Selecteer het datuminterval voor het rapport.

1. In de [!UICONTROL Columns] selecteert u de kolomnamen die u in het rapport wilt weergeven.

1. Klik op **[!UICONTROL Create]**.

   ![Rapport uploaden](assets/upload-reports-config.png)

De volgende lijst verklaart het gebruik van alle kolommen die u aan het rapport kunt toevoegen:

<table>
    <tbody>
     <tr>
      <th><strong>Kolomnaam</strong></th>
      <th><strong>Beschrijving</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>De titel van het element.</td>
     </tr>
     <tr>
      <td>Pad</td>
      <td>Het mappad waar het element beschikbaar is in de middelenweergave.</td>
     </tr>
     <tr>
      <td>MIME-type</td>
      <td>Het MIME-type voor het element.</td>
     </tr>
     <tr>
      <td>Grootte</td>
      <td>De grootte van het element.</td>
     </tr>
     <tr>
      <td>Auteur</td>
      <td>De auteur voor het element.</td>
     </tr>
     <tr>
      <td>Aanmaakdatum</td>
      <td>De datum waarop het element is geüpload naar de middelenweergave.</td>
     </tr>
     <tr>
      <td>Wijzigingsdatum</td>
      <td>De datum waarop het element voor het laatst is gewijzigd.</td>
     </tr>
     <tr>
      <td>Verlopen</td>
      <td>De vervalstatus van het actief.</td>
     </tr>              
    </tbody>
   </table>

## Bestaande rapporten weergeven {#view-report-list}

Na [opstellen van het rapport](#create-download-report)kunt u de lijst met bestaande rapporten weergeven en deze downloaden in CSV-indeling of verwijderen.

Als u de lijst met rapporten wilt weergeven, navigeert u naar **[!UICONTROL Settings]** > **[!UICONTROL Reports]**.

Voor elk rapport, kunt u rapporttitel, het type van het rapport, gespecificeerde beschrijving bekijken terwijl het creëren van het rapport, status van het rapport, e-mailidentiteitskaart van de auteur die het rapport creeerde, en de datum van de rapportverwezenlijking.

`Completed ` de status van het rapport geeft aan dat het rapport klaar is om te worden gedownload .

![Lijst van verslagen](assets/list-of-reports.png)


## Een CSV-rapport downloaden {#download-csv-report}

Een rapport in CSV-indeling downloaden:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL Reports]**.

1. Selecteer een rapport en klik op **[!UICONTROL Download CSV]**.

Het geselecteerde rapport wordt gedownload in CSV-indeling. De kolommen die in het CSV-rapport worden weergegeven, zijn afhankelijk van de kolommen die u selecteert terwijl [opstellen van het rapport](#create-download-report).

## Een rapport verwijderen {#delete-report}

Een rapport verwijderen:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL Reports]**.

1. Selecteer een rapport en klik op **[!UICONTROL Delete]**.

1. Klikken **[!UICONTROL Delete]** nogmaals ter bevestiging.
