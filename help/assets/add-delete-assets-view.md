---
title: Elementen uploaden naar de opslagplaats
description: Elementen uploaden naar [!DNL Assets view], uploadstatussen weergeven en uploadproblemen oplossen.
role: User
exl-id: 01af3b66-dba8-4b09-aadf-ba4ae09b824f
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Elementen uploaden {#add-assets}

Als u nieuwe elementen wilt toevoegen om mee te werken, uploadt u een aantal elementen van uw lokale bestandssysteem. <!-- TBD: Many of the [common file formats are supported](/help/assets/supported-file-formats-assets-view.md). -->

U kunt de volgende methoden gebruiken om een of meer elementen of een map met elementen te uploaden:

* Sleep elementen of mappen naar de gebruikersinterface en volg de aanwijzingen op het scherm.
* Klikken **[!UICONTROL Add Assets]** op de werkbalk en voegt u enkele bestanden toe aan het dialoogvenster voor uploaden.

<!-- TBD: Update this GIF
![Asset and nested folder upload demo](assets/do-not-localize/upload-assets.gif) -->

U kunt al deze methoden gebruiken om elementen te uploaden nadat u een map hebt gemaakt. Als u een lege map wilt maken, klikt u **[!UICONTROL Create Folder]** op de werkbalk. while [!DNL Assets view] biedt een krachtige zoekfunctie met volledige tekst, zodat u uw elementen beter kunt ordenen met mappen.

Nadat u de bestanden hebt geselecteerd, wordt een bevestigingsvenster weergegeven waarin u meer bestanden kunt toevoegen of reeds geselecteerde bestanden kunt verwijderen. Als u meer bestanden aan een selectie wilt toevoegen, klikt u op **[!UICONTROL Browse]** en selecteert u **[!UICONTROL Browse files]** of **[!UICONTROL Browse folders]**. Voeg meer bestanden of mappen toe vanuit dezelfde map of vanuit een andere map.

Als alle bestanden in de wachtrij zijn geplaatst, klikt u op **[!UICONTROL Upload]**.

![Bestanden en mappen uploaden](assets/upload-browse-files-folders.png)

*Afbeelding: Voordat u de geselecteerde elementen uploadt, kunt u elementen aan de wachtrij toevoegen of eruit verwijderen.*

>[!TIP]
>
>Als u een mapstructuur uploadt naar de weergave Middelen, hoeft u geen .ZIP-bestand met de mapstructuur te maken, kunt u mapstructuren rechtstreeks uploaden. Een ZIP-bestand dat naar de weergave Elementen is geüpload, wordt opgeslagen als één ZIP-element en wordt niet automatisch uitgepakt na het uploaden.

## Voortgang van uploaden en status weergeven {#upload-progress}

Wanneer u veel elementen of geneste mappen uploadt naar [!DNL Assets view]Sommige elementen kunnen niet worden geüpload om verschillende redenen, zoals dubbele middelen en netwerkproblemen.

Als u de voortgang van het uploaden wilt bijhouden, klikt u op **[!UICONTROL Upload Progress]** op de werkbalk. In een deelvenster wordt de voortgang van het uploaden van alle elementen weergegeven.

Als u een subset met elementen wilt weergeven op basis van de voortgang of status van het uploaden, gebruikt u het filter in het dialoogvenster **[!UICONTROL Upload Progress]** zijbalk. De verschillende filters moeten alle elementen weergeven, voltooide uploads, uploads die bezig zijn, elementen in de wachtrij die moeten worden geüpload, gepauzeerde uploads, dubbele elementen en elementen die niet zijn geüpload.

![De uploadvoortgang filteren op basis van de status van de upload](assets/filter-upload-progress.png)

*Figuur: Filter de elementen die u probeerde te uploaden op basis van hun status van uploaden of voortgang van uploaden.*

Onmiddellijk nadat de elementen zijn geüpload [!DNL Assets view] verwerkt de elementen om miniaturen te genereren en metagegevens te verwerken. Voor veel elementen duurt het enige tijd. Als er geen miniatuur wordt weergegeven en er een verwerkingsbericht wordt weergegeven bij de plaatsaanduidingsminiatuur, controleert u de map na een paar minuten opnieuw. Tijdens de verwerking [!DNL Assets view] Hiermee genereert u de uitvoeringen, voegt u slimme tags toe en indexeert u de elementdetails voor de zoekopdracht.

![Elementen zijn processen tijdens het uploaden en de verwerking van de tegels](assets/upload-processing.png)

*Afbeelding: Bij geüploade elementen wordt de verwerking weergegeven op het element dat wordt verwerkt.*

## Elementuitvoeringen {#renditions}

[!DNL Assets view] verwerkt de geüploade elementen in bijna realtime en voor veel ondersteunde bestandstypen worden uitvoeringen gegenereerd. De uitvoeringen zijn gemaakt voor afbeeldingen en de grootte van versies van de geüploade afbeelding wordt gewijzigd. U kunt niet alleen het element downloaden, maar ook de uitvoeringen om een geschikte versie te gebruiken. U kunt alle uitvoeringen van een element weergeven wanneer u [een voorvertoning van een element weergeven](/help/assets/navigate-assets-view.md#preview-assets).

![Uitvoeringen](assets/renditions-view-download.png)

*Afbeelding: de uitvoeringen weergeven en downloaden.*

## Onderbroken uploads beheren {#resolve-upload-fails}

Als het uploaden van een ondersteund element om een of andere reden mislukt, klikt u op **[!UICONTROL Retry]** van de [!UICONTROL Upload Progress] venster.

![Uploaden mislukt opnieuw proberen](assets/upload-retry.png)

*Afbeelding: probeer het opnieuw als het uploaden van een ondersteund bestand om een of andere reden mislukt.*

Als u probeert dubbele elementen te uploaden, worden de elementen pas geüpload wanneer u de upload expliciet bevestigt. Eerst worden de dubbele elementen gemarkeerd als geüploade bestanden. U lost dit probleem op door gewoon een versie te maken, de bestaande elementen te verwijderen en te vervangen of een kopie te maken door de naam van het element te wijzigen. U kunt dergelijke fouten één middel tegelijk oplossen of het bulksgewijs doen voor alle ontbroken duplicaten in één keer.

![Dubbele elementen een voor een beheren](assets/uploads-manage-duplicates.png)

*Afbeelding: voor dubbele elementen die standaard niet kunnen worden geüpload, moet u de uitgave van één element tegelijk oplossen.*

![Alle mislukte uploads bulksgewijs beheren](assets/upload-progress-manage-failed-uploads.png)

*Afbeelding: voor dubbele elementen die standaard niet kunnen worden geüpload, kunt u problemen met alle elementen tegelijk oplossen.*

>[!TIP]
>
>U kunt elementen rechtstreeks vanuit uw systeem uploaden naar de DAM-opslagplaats [!DNL Creative Cloud] bureaubladtoepassingen.
<!--TBD
See how [[!DNL Assets view] integrates with [!DNL Adobe Asset Link]](/help/assets/integration-assets-view.md).
-->

## Elementen of mappen verwijderen {#delete-assets}

Gebruikers kunnen afzonderlijke elementen of mappen verwijderen die niet meer vereist zijn. Voer een van de volgende handelingen uit om een middel of map te verwijderen:

* Gebruik de optie die beschikbaar is op de miniatuur van een element of map.

  ![Opties op elementminiatuur voor het beheren van elementen](assets/options-on-thumbnail.png)

  *Afbeelding: Handelingen voor bestanden en mappen zijn beschikbaar in het element met middelen of mappen.*

* Selecteer een middel of een omslag en klik **[!UICONTROL Delete]** ![verwijderpictogram](assets/do-not-localize/delete-icon.png) in de werkbalk.

## Volgende stappen {#next-steps}

* [Een video bekijken om elementen te uploaden in de weergave Middelen](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/creating.html)

* Feedback geven op het product met de [!UICONTROL Feedback] optie beschikbaar in de gebruikersinterface van de weergave Elementen

* Documentfeedback geven met [!UICONTROL Edit this page] ![de pagina bewerken](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![een GitHub-probleem maken](assets/do-not-localize/github-issue.png) beschikbaar op de rechterzijbalk

* Contact [Klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)
