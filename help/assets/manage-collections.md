---
title: Verzamelingen digitale middelen beheren
description: Begrijp het concept van inzameling in Adobe Experience Manager Assets. Leer hoe u verzamelingen kunt beheren, bewerken en verzamelen met andere gebruikers.
contentOwner: AG
mini-toc-levels: 1
feature: Collections, Asset Management
role: User
exl-id: b0798adc-56a4-4577-b4ee-8d1fca3bff09
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '2263'
ht-degree: 13%

---

# Verzamelingen beheren {#manage-collections}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-collections.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Een verzameling is een set elementen binnen Adobe Experience Manager Assets. Gebruik verzamelingen om elementen tussen gebruikers te delen. De set kan een statische verzameling of een dynamische verzameling zijn die is gebaseerd op zoekresultaten.

In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt verzamelingen delen met verschillende gebruikers waaraan verschillende niveaus van bevoegdheden zijn toegewezen, zoals weergeven, bewerken, enzovoort.

U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

De inzamelingen zijn van de volgende types, die op de manier worden gebaseerd zij activa sorteren:

* Een verzameling die een statische referentielijst met elementen, mappen en andere verzamelingen bevat.

* Een slimme verzameling die dynamisch elementen bevat op basis van zoekcriteria.

## Toegang tot de verzamelingsconsole {#navigate-the-collections-console}

U opent als volgt de **[!UICONTROL Collections]** -console:

Selecteer het logo van de Experience Manager om **[!UICONTROL Collections]** te openen. Ga vanaf de navigatiepagina naar **[!UICONTROL Assets]** > **[!UICONTROL Collections]** .

## Een verzameling maken {#create-a-collection}

U kunt een inzameling of met [ statische verwijzingen ](#create-a-collection-with-static-references) tot stand brengen of op a [ onderzoek op criteria-gebaseerde filter ](#create-a-smart-collection) worden gebaseerd. U kunt ook een verzameling maken van een lichtbak.

### Een verzameling met statische verwijzingen maken {#create-a-collection-with-static-references}

U kunt een verzameling maken met statische verwijzingen, bijvoorbeeld een verzameling met verwijzingen naar elementen, mappen, verzamelingen, centrifuges en afbeeldingssets.

1. Navigeer naar de **[!UICONTROL Collections]** -console.
1. Selecteer **[!UICONTROL Create]** in de werkbalk.
1. Voer op de pagina **[!UICONTROL Create Collection]** een titel en een optionele beschrijving in voor de verzameling.
1. Voeg leden toe aan de verzameling en wijs de juiste machtigingen toe. U kunt ook **[!UICONTROL Public Collection]** selecteren om alle gebruikers toegang te geven tot de verzameling.

   >[!NOTE]
   >
   >Als u wilt dat leden verzamelingen kunnen delen met andere gebruikers, geeft u de `dam-users` groep leesmachtigingen op het pad `home/users` . Geef gebruikers toestemming op de locatie `/content/dam/collections` om de verzamelingen in pop-uplijsten weer te geven. U kunt de gebruiker ook deel laten uitmaken van een `dam-users` -groep.

1. (Optioneel) Voeg een miniatuurafbeelding toe voor de verzameling.
1. Selecteer **[!UICONTROL Create]** en selecteer vervolgens **[!UICONTROL OK]** om het dialoogvenster te sluiten. Een verzameling met de opgegeven titel en eigenschappen wordt geopend in de console voor verzamelingen.

   >[!NOTE]
   >
   >Met Experience Manager Assets kunt u controletaken voor een verzameling maken, vergelijkbaar met de manier waarop u overzichtstaken voor een map met middelen maakt.

   Navigeer naar de gebruikersinterface van Assets om elementen aan de verzameling toe te voegen. Voor details, zie [ activa aan een inzameling ](#add-assets-to-a-collection) toevoegen.

### Verzamelingen maken met dropzone {#create-collections-using-dropzone}

U kunt elementen van de gebruikersinterface van Assets naar een verzameling slepen. U kunt ook een kopie van een verzameling maken en de elementen daar slepen.

1. Selecteer in de gebruikersinterface van Assets de elementen die u aan een verzameling wilt toevoegen.
1. Sleep de elementen naar de **[!UICONTROL Drop in Collection]** -zone. U kunt ook het pictogram **[!UICONTROL To Collection]** op de werkbalk selecteren.
1. Selecteer op de pagina **[!UICONTROL Add To Collection]** het pictogram **[!UICONTROL Create Collection]** op de werkbalk. Als u de elementen aan een bestaande verzameling wilt toevoegen, selecteert u deze op de pagina en selecteert u **[!UICONTROL Add]** . Standaard wordt de laatst bijgewerkte verzameling geselecteerd.
1. Geef in het dialoogvenster **[!UICONTROL Create New Collection]** een naam op voor de verzameling. Selecteer **[!UICONTROL Public Collection]** als u de verzameling toegankelijk wilt maken voor alle gebruikers.
1. Selecteer **[!UICONTROL Continue]** om de verzameling te maken.

### Een slimme verzameling maken {#create-a-smart-collection}

Een slimme verzameling gebruikt zoekcriteria om elementen dynamisch te vullen. U kunt een slimme verzameling alleen maken met behulp van bestanden, niet met mappen of bestanden en mappen.

1. Navigeer naar de gebruikersinterface van Assets en selecteer het pictogram **[!UICONTROL Search]** .
1. Voer het trefwoord in het vak Universeel zoeken in en selecteer `Enter` . Selecteer het GlobalNav-pictogram om het deelvenster Filters weer te geven en een zoekfilter toe te passen in het deelvenster Zoeken.
1. Selecteer in de lijst **[!UICONTROL Files & Folders]** de optie **[!UICONTROL Files]** .
1. Selecteer **[!UICONTROL Save Smart Collection]** .
1. Geef een naam op voor de verzameling. Selecteer **[!UICONTROL Public]** om de groep DAM-gebruikers met de Viewer-rol toe te voegen aan de slimme verzameling.

   >[!NOTE]
   >
   >Als u **[!UICONTROL Public]** selecteert, wordt de slimme verzameling beschikbaar voor iedereen met de rol Eigenaar nadat u deze hebt gemaakt. Als u de optie **[!UICONTROL Public]** annuleert, wordt de DAM-gebruikersgroep niet meer gekoppeld aan de slimme verzameling.

1. Selecteer **[!UICONTROL Save]** om de slimme verzameling te maken en sluit vervolgens het berichtvenster om het proces te voltooien. De nieuwe slimme verzameling wordt ook toegevoegd aan de lijst **[!UICONTROL Saved Searches]** .
Het label van de knop **[!UICONTROL Create Smart Selection]** verandert in **[!UICONTROL Edit Smart Selection]**. Als u de instellingen van de slimme verzameling wilt bewerken, selecteert u **[!UICONTROL Files]** in de lijst **[!UICONTROL Files & Folders]**. Selecteer vervolgens de knop **[!UICONTROL Edit Smart Selection]** .

## Elementen toevoegen aan een verzameling {#add-assets-to-a-collection}

U kunt elementen toevoegen aan een verzameling die een lijst met bestanden of mappen waarnaar wordt verwezen, bevat.

>[!NOTE]
>
>Slimme verzamelingen gebruiken een zoekquery om elementen te vullen. Daarom zijn statische verwijzingen naar elementen en mappen niet op hen van toepassing.

1. In Assets UI, navigeer aan de plaats van de activa die u aan een inzameling wilt toevoegen.
1. Selecteer het element en selecteer het pictogram **[!UICONTROL To Collection]** op de werkbalk. U kunt het element ook naar de **[!UICONTROL Drop in Collection]** -zone slepen. Laat de muisknop los wanneer de neerzetzone actief wordt en het label wordt gewijzigd in **[!UICONTROL Drop to Add]** .
1. Selecteer op de pagina **[!UICONTROL Add To Collection]** de verzameling waaraan u het element wilt toevoegen.
1. Selecteer **[!UICONTROL Add]** en sluit het bevestigingsbericht. Het element wordt toegevoegd aan de collectie.

## Een slimme verzameling bewerken {#edit-a-smart-collection}

De slimme inzamelingen worden gebouwd door een onderzoek te bewaren zodat kunt u hun inhoud veranderen door de onderzoeksparameters van het [ bewaarde onderzoek ](#saved-searches) te wijzigen.

1. Selecteer in de Assets-gebruikersinterface het pictogram **[!UICONTROL Search]** op de werkbalk.
1. Selecteer de `Enter` -toets terwijl de cursor in het vak Onderzoek staat.
1. Selecteer het GlobalNav-pictogram om het deelvenster Filters weer te geven.
1. Selecteer in de lijst met **[!UICONTROL Saved Searches]** de slimme verzameling die u wilt wijzigen. In het deelvenster Zoeken worden de filters weergegeven die zijn geconfigureerd voor de opgeslagen zoekopdracht.
1. Selecteer in de lijst **[!UICONTROL Files & Folders]** de optie **[!UICONTROL Files]** .
1. Wijzig desgewenst een of meer filters. Selecteer **[!UICONTROL Edit Smart Collection]**. U kunt ook de naam van de slimme verzameling bewerken.
1. Selecteer **[!UICONTROL Save]**. Het dialoogvenster **[!UICONTROL Edit Smart Collection]** wordt weergegeven.
1. Selecteer **[!UICONTROL Overwrite]** om de originele slimme verzameling te vervangen door de bewerkte verzameling. U kunt ook **[!UICONTROL Save As]** selecteren om de bewerkte verzameling afzonderlijk op te slaan.
1. Selecteer **[!UICONTROL Save]** in het bevestigingsvenster om het proces te voltooien.

## Metagegevens van verzamelingen weergeven en bewerken {#view-and-edit-collection-metadata}

De meta-gegevens van de inzameling omvat gegevens over de inzameling, met inbegrip van om het even welke markeringen die worden toegevoegd.

1. Selecteer een verzameling in de console Verzamelingen en selecteer het pictogram **[!UICONTROL Properties]** op de werkbalk.
1. Bekijk op de pagina **[!UICONTROL Collection Metadata]** de verzamelingsmetadata van de tabbladen **[!UICONTROL Basic]** en **Geavanceerd**.
1. Wijzig desgewenst de metagegevens en selecteer **[!UICONTROL Save & Close]** op de werkbalk om de wijzigingen op te slaan.

### Metagegevens van verzamelingen bulksgewijs bewerken {#edit-collection-metadata-in-bulk}

U kunt de metagegevens van meerdere verzamelingen tegelijk bewerken. Deze functionaliteit helpt u snel gemeenschappelijke meta-gegevens in veelvoudige inzamelingen te herhalen.

1. Selecteer twee of meer verzamelingen waarvoor u metagegevens wilt bewerken in de console Verzamelingen.
1. Selecteer in de werkbalk het pictogram **[!UICONTROL Properties]** .
1. Bewerk desgewenst de metadata op de pagina **[!UICONTROL Collection Metadata]** onder de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]**.
1. Selecteer **[!UICONTROL Save & Close]** op de werkbalk en sluit het bevestigingsvenster om het proces te voltooien.
1. Selecteer **[!UICONTROL Apend mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Selecteer **[!UICONTROL Submit]** .

   >[!NOTE]
   >
   >De modus Toevoegen werkt alleen voor velden die meerdere waarden kunnen bevatten. Voor velden die slechts één waarde kunnen bevatten worden de nieuwe metadata niet toegevoegd aan de bestaande waarde in het veld, zelfs niet als u **[!UICONTROL Append mode]** selecteert.

## Zoeken {#searching}

De eigenschap van het Onderzoek binnen Inzamelingen steunt zowel [ Onderzoek naar inzamelingen ](#search-collections) als [ Onderzoek naar activa binnen een Inzameling ](#search-within-collections).

### Verzamelingen zoeken {#search-collections}

U kunt inzamelingen van de console van Inzamelingen zoeken. Wanneer u met trefwoorden in het vak Zoeken zoekt, zoekt [!DNL Experience Manager Assets] naar namen van verzamelingen, metagegevens en de tags die aan de verzamelingen zijn toegevoegd.

Als u zoekt naar verzamelingen op het hoogste niveau, worden alleen afzonderlijke verzamelingen geretourneerd in zoekresultaten. Assets of mappen in de verzamelingen zijn uitgesloten. In alle andere gevallen (bijvoorbeeld in een afzonderlijke verzameling of in een mappenhiërarchie) worden alle relevante elementen, mappen en verzamelingen geretourneerd.

### Zoeken in verzamelingen {#search-within-collections}

Selecteer in de console Verzamelingen een verzameling om deze te openen.

In een verzameling is het zoeken in [!DNL Experience Manager] beperkt tot elementen (en de bijbehorende tags en metagegevens) in de verzameling die u bekijkt. Wanneer u in een map zoekt, worden alle overeenkomende elementen en onderliggende mappen in de huidige map geretourneerd. Wanneer u in een verzameling zoekt, worden alleen overeenkomende elementen, mappen en andere verzamelingen geretourneerd die directe leden van de verzameling zijn.

## Verzamelingsinstellingen bewerken {#edit-collection-settings}

U kunt verzamelingsinstellingen bewerken, zoals titel en beschrijving, of leden toevoegen aan een verzameling.

1. Selecteer een verzameling en selecteer het pictogram **[!UICONTROL Settings]** op de werkbalk. U kunt ook de handeling **[!UICONTROL Settings]** quick uit de verzamelingsminiatuur gebruiken.
1. Wijzig de verzamelingsinstellingen op de pagina **[!UICONTROL Collection Settings]**. Wijzig bijvoorbeeld de verzamelingstitel, beschrijvingen, leden, en machtigingen zoals die in [Verzamelingen toevoegen](#create-a-collection) worden besproken.
1. Selecteer **[!UICONTROL Save]** om de wijzigingen op te slaan.

## Een verzameling verwijderen {#delete-a-collection}

1. Selecteer een of meer verzamelingen in de console Verzamelingen en selecteer het verwijderpictogram op de werkbalk.
1. Selecteer **[!UICONTROL Delete]** in het dialoogvenster om de verwijderactie te bevestigen.

   >[!NOTE]
   >
   >U kunt Slimme inzamelingen ook schrappen door [ bewaarde onderzoeken ](#saved-searches) te schrappen.

## Een verzameling downloaden {#download-a-collection}

Wanneer u een verzameling downloadt, wordt de volledige hiërarchie van elementen in de verzameling gedownload, inclusief mappen en onderliggende verzamelingen.

1. Selecteer een of meer verzamelingen die u wilt downloaden in de console Verzamelingen.
1. Selecteer het downloadpictogram op de werkbalk.
1. Selecteer **[!UICONTROL Download]** in het dialoogvenster **[!UICONTROL Download]** . Selecteer **[!UICONTROL Renditions]** als u de uitvoeringen van de elementen in de verzameling wilt downloaden. <!-- Select the **[!UICONTROL Email]** option to send an email notification to the owner of the collection. -->

   Wanneer u een verzameling selecteert die u wilt downloaden, wordt de volledige maphiërarchie onder de verzameling gedownload. Selecteer **[!UICONTROL Create separate folder for each asset]** als u elke verzameling die u downloadt, wilt opnemen (inclusief elementen in onderliggende verzamelingen die onder de bovenliggende verzameling zijn genest) in een afzonderlijke map.

## Eigenschappen van metagegevens van meerdere verzamelingen bewerken {#editing-metadata-properties-of-multiple-collections}

Met Adobe Enterprise Manager Assets kunt u de metagegevens van vele verzamelingen bulksgewijs bewerken. Gebruik de pagina [!UICONTROL Properties] om wijzigingen in metagegevens uit te voeren voor meerdere verzamelingen. Wijzig bijvoorbeeld de eigenschappen van metagegevens in een algemene waarde of voeg tags toe of wijzig deze.

Gebruik de Schema-editor om de pagina met metagegevens [!UICONTROL Properties] aan te passen, zoals eigenschappen van metagegevens toevoegen, wijzigen of verwijderen.

>[!NOTE]
>
>De bulkbewerkingsmethoden werken voor elementen die beschikbaar zijn in een verzameling. Voor de activa die over omslagen beschikbaar zijn of een gemeenschappelijke criteria aanpassen, is het mogelijk aan [ bulkupdate de meta-gegevens na het zoeken ](/help/assets/search-assets.md#metadata-updates).

1. Selecteer in de verzamelingsconsole de verzamelingen die u wilt bewerken.
1. Selecteer op de werkbalk **[!UICONTROL Properties]** om de pagina [!UICONTROL Properties] voor de geselecteerde verzamelingen te openen.
1. Wijzig de eigenschappen van metagegevens voor geselecteerde verzamelingen onder de verschillende tabbladen.

   >[!NOTE]
   >
   >De metagegevens die u voor de geselecteerde verzamelingen toevoegt, overschrijven de vorige metagegevens voor deze verzamelingen, met uitzondering van codes. Alle tags die u toevoegt in het veld **[!UICONTROL Tags]** , worden toegevoegd aan de bestaande lijst met tags in de metagegevens.

1. Als u de eigenschappen van metagegevens voor een specifieke verzameling wilt weergeven, annuleert u de selectie van de resterende verzamelingen in de lijst met verzamelingen. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor de bepaalde inzameling.

   >[!NOTE]
   >
   >* Op de pagina met eigenschappen van verzamelingen kunt u verzamelingen verwijderen uit de lijst met verzamelingen door de selectie te annuleren. Alle verzamelingen zijn standaard geselecteerd in de lijst met verzamelingen. De metagegevens voor verzamelingen die u verwijdert, worden niet bijgewerkt.
   >* Selecteer boven aan de lijst het selectievakje bij **[!UICONTROL Title]** om te schakelen tussen het selecteren van de verzamelingen en het wissen van de lijst.

1. Sla de wijzigingen op.

## Geneste verzamelingen maken {#create-nested-collections}

U kunt een verzameling toevoegen aan een andere verzameling en zo een geneste verzameling maken.

1. Selecteer in de verzamelingsconsole de gewenste verzameling of groep verzamelingen en selecteer **[!UICONTROL To Collection]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Add To Collection]** de verzameling waarin u de verzameling wilt toevoegen.

   >[!NOTE]
   >
   >De verzameling die het laatst is bijgewerkt, is standaard geselecteerd op de pagina **[!UICONTROL Add To Collection]** .

1. Selecteer **[!UICONTROL Add]**. Een bericht bevestigt dat de verzameling wordt toegevoegd aan de doelverzameling op de pagina **[!UICONTROL Select Destination]** . Sluit het bericht om het proces te voltooien.

>[!NOTE]
>
>Slimme verzamelingen kunnen niet worden genest. Met andere woorden, slimme verzamelingen kunnen geen andere verzameling bevatten.

## Opgeslagen zoekopdrachten {#saved-searches}

In de gebruikersinterface Assets kunt u op basis van bepaalde regels, zoekcriteria of aangepaste zoekfacetten zoeken of filteren. Als u deze opslaat als **[!UICONTROL Saved Searches]**, kunt u ze later openen vanuit de lijst **[!UICONTROL Saved Searches]** in het deelvenster Filteren. Als u een opgeslagen zoekopdracht maakt, wordt ook een slimme verzameling gemaakt.

Opgeslagen zoekopdrachten worden gemaakt wanneer u een slimme verzameling maakt. Slimme verzamelingen worden automatisch toegevoegd aan de lijst met **[!UICONTROL Saved Searches]**. De query Opgeslagen zoekopdrachten voor de verzameling wordt opgeslagen in de eigenschap `dam:query` in CRXDE op de relatieve locatie `/content/dam/collections/` . Er gelden geen limieten voor de zoekopdrachten die u kunt opslaan en voor de opgeslagen zoekopdrachten die in de lijst worden weergegeven.

>[!NOTE]
>
>U kunt slimme verzamelingen op dezelfde manier delen als statische verzamelingen.

Opgeslagen zoekopdrachten bewerken is hetzelfde als slimme verzamelingen bewerken. Voor details, zie [ een slimme inzameling ](#edit-a-smart-collection) uitgeven.

Voer de volgende stappen uit om opgeslagen zoekopdrachten te verwijderen:

1. Selecteer in de gebruikersinterface van Assets het zoekpictogram op de werkbalk.

1. Selecteer de `Enter` -toets terwijl de cursor zich in het veld Onderzoek bevindt.
1. Selecteer het GlobalNav-pictogram om het deelvenster Filters weer te geven.
1. Selecteer in de lijst **[!UICONTROL Saved Searches]** de optie **[!UICONTROL Delete]** naast de slimme verzameling die u wilt verwijderen.
1. Selecteer **[!UICONTROL Delete]** in het dialoogvenster om de opgeslagen zoekopdracht te verwijderen.

## Een workflow op een verzameling uitvoeren {#run-a-workflow-on-a-collection}

U kunt een workflow voor de elementen in een verzameling uitvoeren. Als de verzameling geneste verzamelingen bevat, wordt de workflow ook uitgevoerd op de elementen in de geneste verzamelingen. Als de verzameling en de geneste verzameling echter dubbele elementen bevatten, wordt de workflow slechts eenmaal uitgevoerd voor dergelijke elementen.

1. Selecteer in de console Verzamelingen een verzameling waarop u een workflow wilt uitvoeren.
1. Selecteer het GlobalNav-pictogram en kies **[!UICONTROL Timeline]** in de lijst.
1. Selecteer in de tijdlijn het pictogram Caret onderaan en selecteer vervolgens **[!UICONTROL Start Workflow]** .
1. Selecteer in de sectie **[!UICONTROL Start Workflow]** een workflowmodel in de lijst. Selecteer bijvoorbeeld het model **[!UICONTROL DAM Update Asset]** .
1. Voer een titel in voor de workflow en selecteer **[!UICONTROL Start]** .
1. Selecteer **[!UICONTROL Proceed]** in het dialoogvenster. De workflow wordt uitgevoerd op alle elementen in de verzameling.

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
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ creeer een overzichtstaak voor Inzamelingen ](/help/assets/bulk-approval.md)
