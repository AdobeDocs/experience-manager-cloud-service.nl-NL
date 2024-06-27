---
title: Eigenschappen van elementen in [!DNL the Content Hub]
description: Leer hoe u elementen kunt weergeven en beheren in [!DNL Content Hub]
role: User
source-git-commit: e590c34c177e6b45b6a52370caa88da54b61ebc0
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---


# Elementeigenschappen beheren in Content Hub {#asset-properties}

![Afbeelding van metagegevensbanner](assets/metadata-banner-image.png)

[!DNL The Content Hub] Hiermee kunt u informatie over het element weergeven die essentieel is voor een efficiënte distributie van elementen. Het is de verzameling van alle gegevens die beschikbaar zijn voor een element.

Door de eigenschappen van elementen weer te geven, kunt u elementen verder indelen. Dit is handig als de hoeveelheid digitale informatie toeneemt. U kunt een paar honderd bestanden beheren op basis van alleen de bestandsnamen, miniaturen en het geheugen. Nochtans, is deze benadering niet scalable wanneer het aantal betrokken personen, en het aantal beheerde activa stijgen. Bovendien neemt de waarde van een digitaal element toe naarmate het element wordt:

* Toegankelijker - systemen en gebruikers kunnen het gemakkelijk vinden.
* Eenvoudiger te beheren - u kunt gemakkelijk middelen met de zelfde reeks eigenschappen vinden en veranderingen op hen toepassen.
* Complete - asset bevat meer informatie en context.

## Eigenschappen van een element weergeven {#properties-ui}

Voordat u middelen gebruikt, deelt of downloadt, kunt u deze nauwkeuriger bekijken. Met de voorvertoningsfunctie kunt u niet alleen de afbeeldingen bekijken, maar ook een paar andere ondersteunde elementtypen. U kunt niet alleen het element weergeven, maar ook de gedetailleerde informatie ervan bekijken en andere handelingen uitvoeren. Navigeer naar het element of de [zoeken](search-assets.md) het element en klik vervolgens op het element om de eigenschappen ervan te openen. In de volgende afbeelding ziet u de velden die beschikbaar zijn op een pagina met eigenschappen van elementen:

![Eigenschappen van de interface van een element](assets/properties-ui.png)

* **A:** Benaming van een actief
* **B:** Percentage van zoomen of voorvertoning van element nauwkeuriger door in of uit te zoomen
* **C:** Ongedaan maken Zoomen naar het vorige geselecteerde percentage
* **D:** Naar vorig of volgend element gaan
* **E:** Aantal Assets
* **F:** Het element downloaden
* **G:** Middel bewerken met [!DNL Adobe Express]
* **H:** Informatie over een element samenvouwen of voorvertonen
* **I:** Het element delen
* **J:** Middel toevoegen aan [!DNL Collection]
* **K:** Voorvertoningsscherm sluiten
* **L:** Informatie over een element, zoals titel, opmaak, grootte, resolutie, tags, kleurcodes en slimme tags.

## Ondersteunde indelingen {#supported-formats}

In de volgende tabel worden de ondersteunde bestandsindelingen weergegeven in [!DNL the Content Hub]:

<table> 
    <tbody>
     <tr>
      <th><strong>Bestandstype</strong></th>
      <th><strong>Ondersteunde indelingen</strong></th>
     </tr>
     <tr>
      <td>Afbeelding</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL SVG]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Video</td>
      <td>
        <ul>
            <li>[!UICONTROL Quicktime]</li>  
            <li>[!UICONTROL MP4]</li> 
        </ul>
      </td>
     </tr>
      <tr>
      <td>Document</td>
      <td>
        <ul>
            <li>[!UICONTROL txt] (Normaal)</li>  
            <li>[!UICONTROL Doc/Docx]</li> 
            <li>[!UICONTROL XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Media afdrukken</td>
      <td>
        <ul>
            <li>[!UICONTROL PDF]</li>  
        </ul>
      </td>
     </tr>  
    </tbody>
   </table>

### Afgeleide eigenschappen na het uploaden van een element {#derived-properties}

Nadat u een element hebt geüpload, leidt de Content Hub een aantal eigenschappen af die automatisch worden gegenereerd. Hieronder volgt een lijst van enkele voorbeelden:

* **Grootte:** De grootte demonstreert de logische waarde van een element op basis van de afmetingen. Het verduidelijkt de ruimte die een activa in een bewaarplaats neemt. [!DNL The Content Hub] ondersteunt middelen tot 2 GB.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Slimme tags:** [!DNL The Content Hub] gebruikt Adobe Sensei Smart Content Services om elementen te trainen met behulp van herkenningsalgoritme op de op tags gebaseerde structuur. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. Met slimme tags verhoogt u de snelheid van de inhoud van uw projecten doordat u snel relevante middelen kunt vinden. De slimme tags zijn een voorbeeld van informatie over elementen die niet in de afbeelding voorkomen. [!DNL The Content Hub] past automatisch slimme tags toe op elementen.

* **Kleurlabels:** [Kleurlabels](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) Help u een element te herkennen met kleuren die automatisch in een element worden geïdentificeerd met behulp van de Sensei AI-mogelijkheden van de Adobe.

* Uploaddatum

* Geüpload door

* Laatst gewijzigd

* Laatst gewijzigd door

Er zijn ook eigenschappen die worden opgegeven wanneer elementen aan Content Hub worden toegevoegd. Zie voor meer informatie [Door een merk goedgekeurde middelen toevoegen aan Content Hub](upload-brand-approved-assets.md). Deze eigenschappen worden ook weergegeven op de pagina met eigenschappen van elementen.

Beheerders kunnen ook de eigenschappen configureren die voor elk element worden weergegeven. Zie voor meer informatie [Content Hub-gebruikersinterface configureren](configure-content-hub-ui-options.md#configure-asset-details-content-hub).

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->

