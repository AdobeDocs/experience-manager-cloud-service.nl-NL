---
title: Elementen uploaden naar de opslagplaats
description: Upload activa aan  [!DNL Assets view], bekijk uploadstatussen, en los uploadkwesties op.
role: User
exl-id: 01af3b66-dba8-4b09-aadf-ba4ae09b824f
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Elementen uploaden {#add-assets}

Als u nieuwe elementen wilt toevoegen om mee te werken, uploadt u een aantal elementen van uw lokale bestandssysteem. <!-- TBD: Many of the [common file formats are supported](/help/assets/supported-file-formats-assets-view.md). -->

U kunt de volgende methoden gebruiken om een of meer elementen of een map met elementen te uploaden:

* Sleep elementen of mappen naar de gebruikersinterface en volg de aanwijzingen op het scherm.
* Klik op de optie **[!UICONTROL Add Assets]** op de werkbalk en voeg enkele bestanden toe aan het dialoogvenster voor uploaden.

<!-- TBD: Update this GIF
![Asset and nested folder upload demo](assets/do-not-localize/upload-assets.gif) -->

U kunt al deze methoden gebruiken om elementen te uploaden nadat u een map hebt gemaakt. Als u een lege map wilt maken, klikt u op **[!UICONTROL Create Folder]** op de werkbalk. Hoewel [!DNL Assets view] een krachtige zoekfunctie met volledige tekst biedt, kunt u ook mappen gebruiken om uw elementen beter te ordenen.

Nadat u de bestanden hebt geselecteerd, wordt een bevestigingsvenster weergegeven waarin u meer bestanden kunt toevoegen of reeds geselecteerde bestanden kunt verwijderen. Als u meer bestanden aan een selectie wilt toevoegen, klikt u op **[!UICONTROL Browse]** en selecteert u **[!UICONTROL Browse files]** of **[!UICONTROL Browse folders]** . Voeg meer bestanden of mappen toe vanuit dezelfde map of vanuit een andere map.

Klik op **[!UICONTROL Upload]** als alle bestanden in de wachtrij zijn geplaatst.

![ uploadt dossiers en omslagen ](assets/upload-browse-files-folders.png)

*Figuur: Alvorens u de geselecteerde activa uploadt, kunt u activa toevoegen of verwijderen uit de rij.*

>[!TIP]
>
>Als u een mapstructuur uploadt naar de Assets-weergave, hoeft u geen .ZIP-bestand met de mappenstructuur te maken. U kunt mapstructuren rechtstreeks uploaden. Een ZIP-bestand dat naar de Assets-weergave is geüpload, wordt opgeslagen als één ZIP-element en wordt niet automatisch uitgepakt na het uploaden.

## Voortgang van uploaden en status weergeven {#upload-progress}

Wanneer u veel elementen of geneste mappen uploadt naar [!DNL Assets view] , kunnen sommige elementen niet worden geüpload om verschillende redenen, zoals dubbele elementen en netwerkproblemen.

Klik op de werkbalk op de optie **[!UICONTROL Upload Progress]** om de voortgang van het uploaden te volgen. In een deelvenster wordt de voortgang van het uploaden van alle elementen weergegeven.

Als u een subset met elementen wilt weergeven op basis van de voortgang of status van het uploaden, gebruikt u het filter in de zijbalk van **[!UICONTROL Upload Progress]** . De verschillende filters moeten alle elementen weergeven, voltooide uploads, uploads die bezig zijn, elementen in de wachtrij die moeten worden geüpload, gepauzeerde uploads, dubbele elementen en elementen die niet zijn geüpload.

![ Filter de uploadvoortgang die op status van wordt gebaseerd uploadt ](assets/filter-upload-progress.png)

*Cijfer: Filter de activa die u probeerde te uploaden gebaseerd op hun uploadstatus of uploadt vooruitgang.*

Direct nadat de elementen zijn geüpload, verwerkt [!DNL Assets view] de elementen om miniaturen te genereren en metagegevens te verwerken. Voor veel elementen duurt het enige tijd. Als er geen miniatuur wordt weergegeven en er een verwerkingsbericht wordt weergegeven bij de plaatsaanduidingsminiatuur, controleert u de map na een paar minuten opnieuw. Tijdens de verwerking genereert [!DNL Assets view] onder andere de uitvoeringen, voegt slimme tags toe en indexeert de elementdetails voor de zoekopdracht.

![ Assets zijn processen op upload en de tegelvertoningen verwerking ](assets/upload-processing.png)

*Cijfer: Geüploade activa tonen verwerking op de tegel deze wordt verwerkt.*

## Elementuitvoeringen {#renditions}

[!DNL Assets view] verwerkt de geüploade elementen in bijna realtime en voor veel ondersteunde bestandstypen worden uitvoeringen gegenereerd. De uitvoeringen zijn gemaakt voor afbeeldingen en de grootte van versies van de geüploade afbeelding wordt gewijzigd. U kunt niet alleen het element downloaden, maar ook de uitvoeringen om een geschikte versie te gebruiken. U kunt alle vertoningen van een activa bekijken wanneer u [ voorproef een activa ](/help/assets/navigate-assets-view.md#preview-assets).

![ Vertoningen ](assets/renditions-view-download.png)

*Cijfer: Bekijk en download de vertoningen.*

## Onderbroken uploads beheren {#resolve-upload-fails}

Als het uploaden van een ondersteund element om een of andere reden mislukt, klikt u op **[!UICONTROL Retry]** in het deelvenster [!UICONTROL Upload Progress] .

![ probeer opnieuw ontbroken upload ](assets/upload-retry.png)

*Cijfer: probeer opnieuw als een gesteund dossier om één of andere reden niet kan uploaden.*

Als u probeert dubbele elementen te uploaden, worden de elementen pas geüpload wanneer u de upload expliciet bevestigt. Eerst worden de dubbele elementen gemarkeerd als geüploade bestanden. U lost dit probleem op door gewoon een versie te maken, de bestaande elementen te verwijderen en te vervangen of een kopie te maken door de naam van het element te wijzigen. U kunt dergelijke fouten één middel tegelijk oplossen of het bulksgewijs doen voor alle ontbroken duplicaten in één keer.

![ beheert dubbele activa één tegelijkertijd ](assets/uploads-manage-duplicates.png)

*Cijfer: Voor dubbele activa die er niet in slagen om door gebrek te uploaden, los de kwestie één activa tegelijkertijd op.*

![ beheer alle ontbroken uploads in bulk ](assets/upload-progress-manage-failed-uploads.png)

*Cijfer: Voor dubbele activa die er niet in slagen om door gebrek te uploaden, los kwesties voor alle activa in één keer op.*

>[!TIP]
>
>U kunt elementen rechtstreeks vanuit uw [!DNL Creative Cloud] -bureaubladtoepassingen uploaden naar de DAM-opslagplaats.
<!--TBD
See how [[!DNL Assets view] integrates with [!DNL Adobe Asset Link]](/help/assets/integration-assets-view.md).
-->

## Elementen of mappen verwijderen {#delete-assets}

Gebruikers kunnen afzonderlijke elementen of mappen verwijderen die niet meer vereist zijn. Voer een van de volgende handelingen uit om een middel of map te verwijderen:

* Gebruik de optie die beschikbaar is op de miniatuur van een element of map.

  ![ Opties op activaduimnagel om activa ](assets/options-on-thumbnail.png) te beheren

  *Cijfer: De acties voor dossiers en omslagen zijn beschikbaar op de activa of de omslagtegel.*

* Selecteer activa of een omslag en klik **[!UICONTROL Delete]** ![ schrappingspictogram ](assets/do-not-localize/delete-icon.png) in de toolbar.

## Volgende stappen {#next-steps}

* [ bekijk een video om activa in de mening van Assets te uploaden ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/creating.html)

* Feedback geven op het product met de optie [!UICONTROL Feedback] die beschikbaar is in de gebruikersinterface van de Assets-weergave

* Verstrek documentatie terugkoppelt gebruikend [!UICONTROL Edit this page] ![ uitgeeft de pagina ](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![ creeer een kwestie GitHub ](assets/do-not-localize/github-issue.png) beschikbaar op juiste sidebar

* De Zorg van de Klant van het contact ](https://experienceleague.adobe.com/?support-solution=General#support)[
