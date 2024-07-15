---
title: Uw digitale middelen beheren
description: Verplaats, schrap, kopieer, hernoem, werk, en versie uw activa in  [!DNL Assets view] bij.
role: User, Leader
contentOwner: AG
exl-id: 2459d482-828b-4410-810c-ac55ef0a2119
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Elementen beheren {#manage-assets}

U kunt verschillende DAM-taken (Digital Asset Management) eenvoudig uitvoeren met de gebruikersvriendelijke interface van [!DNL Assets view] . Nadat u de elementen hebt toegevoegd, kunt u uw elementen zoeken, downloaden, verplaatsen, kopiëren, hernoemen, verwijderen, bijwerken en bewerken.

Gebruik [!DNL Assets view] om de volgende taken voor middelenbeheer uit te voeren. Wanneer u een element selecteert, worden de volgende opties bovenaan op de werkbalk weergegeven.

![ de opties van de Toolbar wanneer u activa ](assets/toolbar-image-selected.png) selecteert

*Cijfer: De opties beschikbaar in de toolbar voor een geselecteerd beeld.*

* ![ schrap pictogram ](assets/do-not-localize/close-icon.png) Deselecteer de selectie.

* ![ vind gelijkaardige pictogram ](assets/do-not-localize/find-similar.svg) vind gelijkaardige beeldactiva in Assets UI die op de meta-gegevens en slimme markeringen wordt gebaseerd.

* ![ detailspictogram ](assets/do-not-localize/edit-in-icon.png) klik om activa voor te vertonen en de gedetailleerde meta-gegevens te bekijken. Als u een voorvertoning weergeeft, kunt u de versies weergeven en een afbeelding bewerken.

* ![ downloadpictogram ](assets/do-not-localize/download-icon.png) Download de geselecteerde activa aan uw lokaal dossiersysteem.

* ![ voeg inzamelingspictogram ](assets/do-not-localize/add-collection.svg) toe voegt de geselecteerde activa aan een inzameling toe.

* ![ Vastzet activa pictogram ](assets/do-not-localize/pin-quick-access.svg) Vastzetten activa voor snellere toegang wanneer u het later nodig hebt. Alle vastgezette punten tonen in de **Snelle toegang** sectie van Mijn Workspace.

* ![ geef in uitdrukkelijke pictogram uit ](assets/do-not-localize/edit-e.svg) geef een beeld in de geïntegreerde Adobe Express binnen Adobe Experience Manager Assets uit.

* ![ geef activapictogram uit ](assets/do-not-localize/edit-e.svg) geef het beeld uit gebruikend Adobe Express.

* ![ het pictogram van de de verbindingsactiva van het aandeel ](assets/do-not-localize/share-link.svg) voor activa met andere gebruikers zodat zij tot het kunnen toegang hebben en het downloaden.

* ![ schrappingspictogram ](assets/do-not-localize/delete-icon.png) schrapt de geselecteerde activa of de omslag.

* ](assets/do-not-localize/copy-icon.png) Kopieer het pictogram van 0} exemplaar het geselecteerde dossier of de omslag.![

* ](assets/do-not-localize/move-icon.png) Beweeg het pictogram van de beweging 0} {het geselecteerde activa of de omslag naar een verschillende plaats in de bewaarplaatshiërarchie.![

* ![ anders noem pictogram ](assets/do-not-localize/rename-icon.png) noem het geselecteerde activa of de omslag anders. Gebruik een unieke naam anders ontbreekt het anders noemen met een waarschuwing. U kunt het opnieuw proberen met een nieuwe naam.
Bovendien kunt u op de titel van een element of map klikken om de naam ervan te wijzigen. Vermelding de nieuwe tekst in **anders noemt Activa** textbox en klikt **sparen**. Deze mogelijkheid is beschikbaar in de raster-, galerie-, waterval- en lijstweergaven.

* ![ pictogram van de watervalmening ](assets/do-not-localize/waterfall-view.png) [!UICONTROL Waterfall View].

* ![ pictogram van de exemplaarbibliotheek ](assets/do-not-localize/copy-icon.png) voeg een activa aan Bibliotheek toe.

* ![ wijs taakpictogram ](assets/do-not-localize/review-delegate-icon.png) toe wijst taken aan andere gebruikers om aan activa samen te werken.

* ![ wijs taakpictogram ](assets/do-not-localize/watch-asset.svg) toe Monitor de verrichtingen die op activa worden uitgevoerd.

U kunt dezelfde opties weergeven op de miniaturen van elementen.

![ Opties op activaduimnagel om activa ](assets/options-on-thumbnail.png) te beheren

In [!DNL Assets view] worden alleen de relevante opties op de werkbalk weergegeven die afhankelijk zijn van het type geselecteerd element.

![ de opties van de Toolbar wanneer u activa ](assets/toolbar-folder-selected.png) selecteert

*Cijfer: De opties beschikbaar in de toolbar voor een geselecteerde omslag.*

![ de opties van de Toolbar wanneer u activa ](assets/toolbar-pdf-selected.png) selecteert

*Cijfer: De opties beschikbaar in de toolbar voor een geselecteerd dossier van de PDF.*

## Elementen downloaden en distribueren {#download}

U kunt een of meer elementen of mappen of een combinatie van beide selecteren en de selectie naar uw lokale bestandssysteem downloaden. U kunt de elementen bewerken en opnieuw uploaden of de elementen buiten [!DNL Assets view] verspreiden. Ook, kunt u de vertoningen ](/help/assets/add-delete-assets-view.md#renditions) van een activa [ downloaden.

## Asset versioning {#versions-of-assets}

<!-- 
TBD: query for engineering: How many versions are maintained. What happens when we reach that limit? Are old versions automatically removed? -->

De elementen worden door [!DNL Assets view] bijgewerkt wanneer de elementen opnieuw worden geüpload of bewerkt. U kunt versiegeschiedenis, oudere versies bekijken, en een vroegere versie van activa als recentste versie herstellen, die aan een vorige versie indien nodig wordt teruggezet. In de volgende scenario&#39;s worden versies van middelen gemaakt:

* Upload een nieuw element met dezelfde bestandsnaam als een bestaand element en in dezelfde map als het bestaande element. [!DNL Assets view] vraagt om het vorige element te overschrijven of het nieuwe element op te slaan als een versie. Zie [ gedupliceerde activa ](/help/assets/add-delete-assets-view.md) uploaden.

  ![ creeer versies wanneer het uploaden ](assets/uploads-manage-duplicates.png)

  *Cijfer: Wanneer het uploaden van activa genoemd het zelfde als bestaand activa, kunt u een versie van de activa tot stand brengen.*

* Bewerk een afbeelding en klik op **[!UICONTROL Save as Version]** . Zie [ beelden ](/help/assets/edit-images-assets-view.md) uitgeven.

  ![ sparen uitgegeven beeld als versie ](assets/edit-image2.png)

  *Cijfer: sparen uitgegeven beeld als versie.*

* Open de versies van een bestaand element. Klik op **[!UICONTROL New Version]** en upload een nieuwere versie van het middel in de repository.

  ![ Optie om een nieuwe versie van een activa van de versiegeschiedenis te uploaden ](assets/view-asset-versions2.png)

### Versies van een element weergeven {#view-versions}

Wanneer u een gedupliceerde kopie of een gewijzigde kopie van een element uploadt, kunt u de versies ervan maken. Met Versioning kunt u historische elementen controleren en desgewenst terugkeren naar een vorige versie.

Om versies te bekijken, open de voorproef van activa en klik **[!UICONTROL Versions]** {het pictogram van Versies 1} ](assets/do-not-localize/versions-clock-icon.png) van de juiste zijbalk. ![ Als u een voorvertoning van een specifieke versie wilt weergeven, selecteert u deze. Klik op **[!UICONTROL Make Latest]** om terug te keren naar de hyperlink.

U kunt ook versies maken van de tijdlijn van de versie. Selecteer de meest recente versie, klik op **[!UICONTROL New Version]** en upload een nieuwe kopie van het element vanuit uw lokale bestandssysteem.

![ de versies van de Mening van activa ](assets/view-asset-versions1.png)

*Cijfer: De versies van de mening van activa, keren aan een vorige versie terug, of uploaden een andere nieuwe versie.*

## De elementstatus beheren {#manage-asset-status}

**Vereiste toestemmingen:** `Can Edit`, `Owner`, of beheerdertoestemmingen op een activa.

In de Assets-weergave kunt u de status instellen voor de middelen die in de opslagplaats beschikbaar zijn. Stel een elementstatus in om het downstreamgebruik van digitale elementen beter te beheren en te beheren.

U kunt de volgende status instellen voor elementen:

* Goedgekeurd

* Geweigerd

* Geen status

### Status van element instellen {#set-asset-status}

De elementstatus instellen:

1. Selecteer het element en klik op **[!UICONTROL Details]** op de werkbalk.

1. Selecteer op het tabblad **[!UICONTROL Basic]** de elementstatus in de vervolgkeuzelijst **[!UICONTROL Status]** . Mogelijke waarden zijn Goedgekeurd, Afgewezen en Geen status (standaardwaarde).

   >[!VIDEO](https://video.tv.adobe.com/v/342495)


### Vervaldatum van element instellen {#set-asset-expiration-date}

In de Assets-weergave kunt u ook een vervaldatum instellen voor de middelen die in de opslagplaats beschikbaar zijn. U kunt dan [ de onderzoeksresultaten ](search-assets-view.md#refine-search-results) filtreren die op een `Expired` activastatus worden gebaseerd. Daarnaast kunt u een datumbereik voor de vervaldatum voor elementen opgeven om de zoekresultaten verder te filteren.

De vervaldatum van het element instellen:

1. Selecteer het element en klik op **[!UICONTROL Details]** op de werkbalk.

1. Stel op het tabblad **[!UICONTROL Basic]** de vervaldatum voor het element in met behulp van het veld **[!UICONTROL Expiration date]** .

De indicator `Expired` voor de elementenkaart heeft voorrang op de indicator `Approved` of `Rejected` die voor een element is ingesteld.

U kunt activa ook filtreren die op een activastatus worden gebaseerd, voor meer informatie, zie [ activa van het Onderzoek in de mening van Assets ](search-assets-view.md).

## Metagegevensformulieren aanpassen om het statusveld voor elementen op te nemen {#customize-asset-status-metadata-form}

**Vereiste Toestemmingen:** Beheerder

De Assets-weergave biedt standaard vele standaardmetagegevensvelden. Organisaties hebben extra behoeften aan metagegevens en hebben meer metagegevensvelden nodig om bedrijfsspecifieke metagegevens toe te voegen. Met metagegevensformulieren kunnen bedrijven aangepaste metagegevensvelden toevoegen aan de pagina [!UICONTROL Details] van een element. De bedrijfsspecifieke metagegevens verbeteren het beheer en de ontdekking van de bedrijfsmiddelen.

Voor meer informatie over hoe te om extra meta-gegevensgebieden aan de meta-gegevensvorm toe te voegen, zie [ Meta-gegevens Forms ](metadata-assets-view.md#metadata-forms).

**voeg de meta-gegevensgebied van de Status van Activa aan de vorm** toe

Als u een metagegevensveld voor de status van element wilt toevoegen aan het formulier, sleept u de component **[!UICONTROL Asset Status]** van de linkerrail naar het formulier. De toewijzingseigenschap wordt automatisch vooraf ingevuld. Sla het formulier op om de wijzigingen te bevestigen.

**voeg de meta-gegevensgebied van de Datum van de Vervalsing aan de vorm toe**

Als u het metagegevensveld Vervaldatum aan het formulier wilt toevoegen, sleept u de component **[!UICONTROL Date]** van de linkerrails naar het formulier. Specificeer **Datum van de Vervalsing** als etiket en `pur:expirationDate` als kaartbezit. Sla het formulier op om de wijzigingen te bevestigen.

## Volgende stappen {#next-steps}

* [ bekijk een video om activa in de mening van Assets te beheren ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/managing.html)

* Feedback geven op het product met de optie [!UICONTROL Feedback] die beschikbaar is in de gebruikersinterface van de Assets-weergave

* Verstrek documentatie terugkoppelt gebruikend [!UICONTROL Edit this page] ![ uitgeeft de pagina ](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![ creeer een kwestie GitHub ](assets/do-not-localize/github-issue.png) beschikbaar op juiste sidebar

* De Zorg van de Klant van het contact ](https://experienceleague.adobe.com/?support-solution=General#support)[

