---
title: Hoe te om meta-gegevens in de mening van Activa te beheren?
description: Leer hoe u metagegevens beheert in de weergave Middelen. Een beter beheer van metagegevens maakt een middel toegankelijker, eenvoudiger te beheren en compleet.
role: User, Leader, Admin, Architect, Developer
contentOwner: AG
exl-id: 7264e8d1-fc8f-4eb3-93a9-a6066ca3f851
feature: Metadata
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1723'
ht-degree: 0%

---

# Metagegevens in middelenweergave {#metadata}

Metagegevens zijn gegevens of een beschrijving van de gegevens. Uw afbeeldingen als een element kunnen bijvoorbeeld informatie bevatten over de camera waarop u hebt geklikt of over copyrightgegevens. Deze informatie is metagegevens van de afbeelding. Metagegevens zijn essentieel voor efficiënt middelenbeheer. Metagegevens zijn de verzameling van alle gegevens die voor een element beschikbaar zijn, maar hoeven niet noodzakelijkerwijs in dat element te zijn opgenomen.

Met metagegevens kunt u elementen verder indelen. Dit is handig wanneer de hoeveelheid digitale informatie toeneemt. U kunt een paar honderd bestanden beheren op basis van alleen de bestandsnamen, miniaturen en het geheugen. Deze aanpak is echter niet schaalbaar. Het is te kort wanneer het aantal betrokken personen en het aantal beheerde activa toenemen.

Met de toevoeging van metagegevens neemt de waarde van een digitaal element toe, omdat het element:

* Toegankelijker - systemen en gebruikers kunnen het gemakkelijk vinden.
* Gemakkelijker te beheren - u kunt gemakkelijker middelen met de zelfde reeks eigenschappen vinden en veranderingen op hen toepassen.
* Volledig - asset bevat meer informatie en context met meer metagegevens.

Om deze redenen beschikt u over de juiste middelen om metagegevens voor uw digitale elementen te maken, te beheren en uit te wisselen.

## De metagegevens weergeven {#view-metadata}

Als u de metagegevens van een element wilt weergeven, bladert u naar het element of doorzoekt u het element, selecteert u het element en klikt u op **[!UICONTROL Details]** in de werkbalk.

![Metagegevens van een element weergeven](assets/metadata-view.png)

*Afbeelding: Als u een element en de bijbehorende metagegevens wilt weergeven, klikt u op **[!UICONTROL Details]**op de werkbalk of dubbelklikt u op het element.*

De basismetagegevens, zoals titel, beschrijving en uploaddatum, zijn beschikbaar in het dialoogvenster [!UICONTROL Basic] tab. De [!UICONTROL Advanced] bevat geavanceerdere metagegevens, zoals cameramodel, lensdetails en geotags. De [!UICONTROL Tags] bevat automatisch toegepaste tags op basis van de inhoud van de afbeelding.

## Metagegevens bijwerken {#update-metadata}

Nadat het metagegevensformulier door Admin is geconfigureerd, kunnen andere velden handmatig worden bijgewerkt. U kunt dit wijzigen omdat het alleen leest op basis van het metagegevensformulier in het vak.

## Slimme tags {#smart-tags}

[!DNL Experience Manager Assets] maakt gebruik van kunstmatige intelligentie, verstrekt door [Adobe Sensei](https://www.adobe.com/sensei.html) om automatisch relevante tags toe te passen op alle geüploade elementen. Deze labels, met de juiste naam Slimme tags, verhogen de snelheid van de inhoud van uw projecten door u te helpen snel relevante elementen te vinden. De slimme tags zijn een voorbeeld van metagegevens die niet in de afbeelding voorkomen.

De slimme tags worden toegepast in de buurt van realtime en worden gegenereerd op basis van de inhoud van de afbeelding. Wanneer u een element uploadt, wordt de gebruikersinterface weergegeven [!UICONTROL Processing] gedurende enige tijd op de miniatuur van het element. Zodra de verwerking is voltooid, kunt u [de metagegevens weergeven](#view-metadata) en de slimme tags.

![Slimme tags van een element weergeven](assets/metadata-view-tags.png)

*Figuur: Om de Slimme Markeringen van een activa te bekijken, klik **[!UICONTROL Details]**op de werkbalk of dubbelklikt u op het element.*

Slimme tags bevatten ook een betrouwbaarheidsscore als percentage. Het geeft het vertrouwen aan dat aan de toegepaste tag is gekoppeld. U kunt de automatisch toegepaste slimme tags verkleinen.

## Trefwoorden toevoegen of bijwerken {#manually-tag}

U kunt meer tags toevoegen aan uw elementen, naast de slimme tags die automatisch worden toegevoegd met de opdracht [!DNL Adobe Sensei] intelligente service. Een element openen voor een voorvertoning, klikt u op [!UICONTROL Tags]en typ de gewenste trefwoorden in het veld [!UICONTROL Keywords] veld. Druk op Return om de tag toe te voegen. [!DNL Assets view] indexeert het sleutelwoord in dichtbij echt - tijd en uw team kan spoedig de bijgewerkte activa zoeken gebruikend de nieuwe sleutelwoorden.

U kunt ook tags verwijderen uit het dialoogvenster [!UICONTROL Smart Tags] sectie die automatisch wordt toegevoegd door [!DNL Assets view] naar alle geüploade elementen.

## Taxonomiebeheer {#taxonomy-management}

Tags kunnen ook in een hiërarchie worden genest ter ondersteuning van relaties zoals categorie en subcategorie. Als u hiërarchische tags moet invoegen, worden deze eenvoudig beheerd door de beheerder in het dialoogvenster [!UICONTROL Taxonomy Management] deel van [!UICONTROL Settings]. U kunt een beheerde set naamruimten en tags maken die alle gebruikers kunnen gebruiken tijdens het beschrijven van inhoud. Alleen de beheerders kunnen taghiërarchieën instellen in [!UICONTROL Taxonomy Manager] ervoor zorgen dat de waarden op consistente wijze worden gecontroleerd en gebruikt.

## Metagegevens Forms instellen {#metadata-forms}

>[!CONTEXTUALHELP]
>id="assets_metadata_forms"
>title="Metagegevens Forms"
>abstract="[!DNL Experience Manager Assets] biedt standaard veel standaardvelden voor metagegevens. Organisaties hebben extra behoeften aan metagegevens en hebben meer metagegevensvelden nodig om bedrijfsspecifieke metagegevens toe te voegen. Met metagegevensformulieren kunnen bedrijven aangepaste metagegevensvelden toevoegen aan de pagina Details van een element. De bedrijfsspecifieke metagegevens verbeteren het beheer en de ontdekking van de bedrijfsmiddelen."

De middelenweergave biedt standaard vele standaardmetagegevensvelden. Organisaties hebben extra behoeften aan metagegevens en hebben meer metagegevensvelden nodig om bedrijfsspecifieke metagegevens toe te voegen. Met metagegevensformulieren kunnen bedrijven aangepaste metagegevensvelden toevoegen aan het element [!UICONTROL Details] pagina. De bedrijfsspecifieke metagegevens verbeteren het beheer en de ontdekking van de bedrijfsmiddelen. U kunt geheel nieuwe formulieren maken of een bestaand formulier opnieuw gebruiken.

U kunt metagegevensformulieren configureren voor verschillende typen elementen (verschillende MIME-typen). Gebruik dezelfde formuliernaam als het MIME-type van het bestand. In de middelenweergave wordt het MIME-type voor geüploade elementen automatisch afgestemd op de naam van het formulier en worden de metagegevens voor de geüploade elementen bijgewerkt op basis van de formuliervelden.
<!--
For example, if a metadata form by the name `PDF` or `pdf` exists, then the uploaded PDF documents contain metadata fields as defined in the form.
-->
In de middelenweergave wordt de volgende reeks gebruikt om te zoeken naar bestaande formuliernamen voor metagegevens om de metagegevensvelden toe te passen op de geüploade elementen van een bepaald type:

MIME-subtype > MIME-type > `default` form > Out-of-the-box form

Als een metagegevensformulier bijvoorbeeld op naam staat `PDF` of `pdf` bestaat, bevat het geüploade PDF-document metagegevensvelden zoals gedefinieerd in het formulier. Als een metagegevensformulier met de naam `PDF` of `pdf` bestaat niet. De middelenweergave komt overeen als er een metagegevensformulier met de naam bestaat `application`. Als er een metagegevensformulier met de naam `application`De geüploade PDF-documenten bevatten metagegevensvelden zoals gedefinieerd in het formulier. Als in de weergave Middelen nog steeds geen overeenkomend metagegevensformulier wordt gevonden, wordt gezocht naar de `default` metagegevensformulier waarmee u in het formulier gedefinieerde metagegevensvelden kunt toepassen op de geüploade PDF-documenten. Als geen van deze stappen werkt, worden in de weergave Middelen metagegevensvelden toegepast die in het formulier buiten het vak zijn gedefinieerd, op alle geüploade PDF-documenten.
Maar als u een metagegevensformulier aan een map wilt toewijzen [zie](#assign-metadata-form-folder).

>[!IMPORTANT]
>
>Het nieuwe metagegevensformulier voor een specifiek bestandstype vervangt volledig het standaardformulier voor metagegevens dat [!DNL Assets view] verstrekt. Als u een metagegevensformulier verwijdert of de naam ervan wijzigt, zijn de standaardmetagegevensvelden weer beschikbaar voor nieuwe elementen.

Ga als volgt te werk om een metagegevensformulier te maken:

1. Klik in het linkerspoor op **[!UICONTROL Settings]** > **[!UICONTROL Metadata Forms]**.

   ![metagegevensformulieren, optie in linkerzijbalk](assets/metadata-forms-sidebar.png)

1. Klikken **[!UICONTROL Create]**, in de rechterbovenhoek van de gebruikersinterface.
1. Geef het formulier een naam en klik op **[!UICONTROL Create]**.
1. Geef een naam op voor de tab in **[!UICONTROL Settings]** in het rechterspoor.
1. Van de **[!UICONTROL Components]** Sleep de vereiste componenten naar een tabblad in het formulier. Sleep de componenten in de gewenste volgorde.

   ![metagegevensformulieren, optie in linkerzijbalk](assets/metadata-form-new.png)

   *Afbeelding: interface voor het maken van metagegevens met opties voor het toevoegen van componenten en de optie voor een voorbeeldweergave van het formulier.*

1. Geef voor elke component een naam op in het dialoogvenster **[!UICONTROL Settings]** in de rechterspoorstaaf een kaart van de ondersteunde eigenschappen leveren.
1. Selecteer optioneel voor een component **[!UICONTROL Required]** om het metagegevensveld verplicht te maken en selecteer **[!UICONTROL Read-Only]** om het veld in het element onbewerkbaar te maken [!UICONTROL Details] pagina.
1. Klik optioneel op **[!UICONTROL Preview]** om een voorbeeld te bekijken van het formulier dat u maakt.
1. Voeg desgewenst meer tabbladen en de vereiste componenten toe aan elk tabblad.
1. Klikken **[!UICONTROL Save]** wanneer het formulier volledig is.

Bekijk deze video om de reeks stappen weer te geven:

>[!VIDEO](https://video.tv.adobe.com/v/341275)

Nadat een formulier is gemaakt, wordt het automatisch toegepast wanneer gebruikers een element van het overeenkomende MIME-type uploaden.

Als u een bestaand formulier opnieuw wilt gebruiken om een nieuw formulier te maken, selecteert u een metagegevensformulier. Klik op **[!UICONTROL Copy]** Geef een naam op in de werkbalk en klik op **[!UICONTROL Confirm]**. U kunt een metagegevensformulier bewerken om het te wijzigen. Wanneer u een formulier wijzigt, wordt dit gebruikt voor elementen die na de wijziging worden geüpload. De bestaande activa blijven ongewijzigd.

### Eigenschapcomponenten {#property-components}

U kunt het metagegevensformulier aanpassen met een van de volgende eigenschapcomponenten. U sleept het componenttype gewoon naar het formulier op de gewenste locatie en wijzigt de componentinstellingen.
Hieronder ziet u een overzicht van elk type eigenschap en de manier waarop deze worden opgeslagen.

| Componentnaam | Beschrijving |
|---|---|
| Accordeoncontainer | Voeg een inklapbare rubriek voor een lijst van gemeenschappelijke componenten en eigenschappen toe. Deze kan standaard worden uitgevouwen of samengevouwen. |
| Tekst met één regel | Voeg een teksteigenschap voor één regel toe. |
| Tekst met meerdere regels | Voeg meerdere tekstregels of een alinea toe. Het wordt uitgebreid als gebruikerstypes om alle inhoud te bevatten. |
| Tekst met meerdere waarden | Voeg een teksteigenschap voor meerdere waarden toe. |
| Getal | Voeg een getalcomponent toe. |
| Selectievakje | Voeg een Booleaanse waarde toe. Opgeslagen als TRUE of FALSE zodra een waarde is opgeslagen. |
| Datum | Voeg een datumcomponent toe. |
| Vervolgkeuzelijst | Voeg een vervolgkeuzelijst toe. |
| Staat | De statuseigenschap voor de repository toevoegen (toegewezen aan repo:state) |
| Status van element | De standaardeigenschap Asset Status toevoegen (toegewezen aan dam:assetStatus) |
| Tags | Voeg een tag toe uit waarden die zijn opgeslagen in Taxonomy Management (toegewezen aan xcm:tags). |
| Trefwoorden | Vrije-vormtrefwoorden toevoegen (toegewezen aan dc:subject). |
| Slimme tags | U kunt zoekmogelijkheden uitbreiden door automatisch metagegevenstags toe te voegen. |

### Metagegevensformulier toewijzen aan een map {#assign-metadata-form-folder}

U kunt ook een metagegevensformulier toewijzen aan een map binnen de implementatie van de middelenweergave. Het metagegevensformulier dat volgens het MIME-type aan een map is toegewezen, wordt overschreven wanneer u handmatig een metagegevensformulier op een map toepast. Alle elementen in de map, inclusief de elementen in de submappen, geven vervolgens de eigenschappen weer die in het metagegevensformulier zijn gedefinieerd.

Een metagegevensformulier toewijzen aan een map:

1. Navigeren naar **[!UICONTROL Settings]** > **[!UICONTROL Metadata Forms]** en selecteert u een metagegevensformulier.

2. Klik op **[!UICONTROL Assign to Folder]**.

3. Selecteer de map en klik op **[!UICONTROL Assign]**. U kunt de mappen selecteren door op de mapnamen te klikken.

   ![metagegevensformulier toewijzen aan een map](assets/assign-to-folder.png)

   U kunt ook naar de pagina met mapdetails navigeren en een metagegevensformulier selecteren uit de makeigenschappen in het rechterdeelvenster om het metagegevensformulier aan de map toe te wijzen.

   ![Metagegevens uit mapeigenschappen](assets/metadata-from-folder-props.png)

### Metagegevens uit mappen verwijderen {#remove-metadata-form-folder}

Nadat u een metagegevensformulier aan een of meerdere mappen hebt toegewezen, kunt u met Experience Manager Assets ook het metagegevensformulier uit de geselecteerde mappen verwijderen.

Een metagegevensformulier verwijderen uit een map:

1. Navigeren naar **[!UICONTROL Settings]** > **[!UICONTROL Metadata Forms]** en selecteert u een metagegevensformulier.

1. Klik op **[!UICONTROL Remove from Folder(s)]**. De lijst met toegewezen mappen voor de weergave van het metagegevensformulier.

1. Selecteer de map en klik op **[!UICONTROL Remove]**. U kunt ook meerdere mappen in de lijst selecteren.

U kunt ook naar de pagina met mapdetails navigeren en **[!UICONTROL System mapped Metadata Form]** van de **[!UICONTROL Metadata Forms]** veld om het toegewezen metagegevensformulier uit een map te verwijderen.

## Volgende stappen {#next-steps}

* [Een video bekijken om metagegevensformulieren te beheren in de middelenweergave](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/configuring/metadata-forms.html)

* Feedback geven op het product met de [!UICONTROL Feedback] optie beschikbaar in de gebruikersinterface van de weergave Elementen

* Documentfeedback geven met [!UICONTROL Edit this page] ![de pagina bewerken](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![een GitHub-probleem maken](assets/do-not-localize/github-issue.png) beschikbaar op de rechterzijbalk

* Contact [Klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)

<!-- TBD: Cannot create a form using the second option. Documenting only the first option for now.
To reuse an existing form to create a form, do one of these:

* Select a metadata form and click **[!UICONTROL Copy]** from the toolbar, provide a name, and click **[!UICONTROL Confirm]**.

* Click **[!UICONTROL Create]**, select **[!UICONTROL Use existing form structure as template]** option, and select an existing form. 
-->

<!-- TBD: Queries for PM and engg.

Can we edit the existing metadata in any form?

How to moderate smart tags?

Allow or deny list for smart tags?

What about Tags displayed just above Smart Tags in the UI?

Is there a detailed metadata tab. Where do the other details of an asset go?

How can one search based strictly on the metadata. Similar to AEM Assets GQL queries.
-->

<!-- TBD: Link to related articles if any.

>[!MORELIKETHIS]
>
>* [Search assets](search.md).
-->
