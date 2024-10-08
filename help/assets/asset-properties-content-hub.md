---
title: Eigenschappen van element in  [!DNL the Content Hub]
description: Leer hoe u elementen kunt weergeven en beheren in  [!DNL Content Hub]
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# Elementeigenschappen beheren in Content Hub {#asset-properties}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![ Bannerbeeld van de metagegevensbanner ](assets/metadata-banner-image.png)

Met [!DNL The Content Hub] kunt u informatie over het element weergeven die essentieel is voor een efficiënte distributie van elementen. Het is de verzameling van alle gegevens die beschikbaar zijn voor een element.

Door de eigenschappen van elementen weer te geven, kunt u elementen verder indelen. Dit is handig als de hoeveelheid digitale informatie toeneemt. U kunt een paar honderd bestanden beheren op basis van alleen de bestandsnamen, miniaturen en het geheugen. Nochtans, is deze benadering niet scalable wanneer het aantal betrokken personen, en het aantal beheerde activa stijgen. Bovendien neemt de waarde van een digitaal element toe naarmate het element wordt:

* Toegankelijker - systemen en gebruikers kunnen het gemakkelijk vinden.
* Eenvoudiger te beheren - u kunt gemakkelijk middelen met de zelfde reeks eigenschappen vinden en veranderingen op hen toepassen.
* Complete - asset bevat meer informatie en context.

## Vereisten {#prerequisites}

[ de gebruikers van Content Hub ](deploy-content-hub.md#onboard-content-hub-users) kunnen acties uitvoeren die in dit artikel worden vermeld.

## Eigenschappen van een element weergeven {#properties-ui}

Voordat u middelen gebruikt, deelt of downloadt, kunt u deze nauwkeuriger bekijken. Met de voorvertoningsfunctie kunt u niet alleen de afbeeldingen bekijken, maar ook een paar andere ondersteunde elementtypen. U kunt niet alleen het element weergeven, maar ook de gedetailleerde informatie ervan bekijken en andere handelingen uitvoeren. Om informatie van een activa te bekijken, navigeer aan de activa of [ onderzoek ](search-assets.md) de activa en klik dan de activa om zijn eigenschappen te openen. In de volgende afbeelding ziet u de velden die beschikbaar zijn op een pagina met eigenschappen van elementen:

![ Eigenschappen van een activa UI ](assets/properties-ui.png)

* **A:** Titel van een activa
* **B:** percentage van gezoem of voorproefactiva door binnen of uit te zoomen
* **C:** maakt gezoem aan het eerder geselecteerde percentage ongedaan
* **D:** ga aan vorige of volgende activa te werk
* **E:** aantal Assets
* **F:** Download de activa
* **G:** geef activa uit gebruikend [!DNL Adobe Express]
* **H:** Vouw of voorproefinformatie van activa samen
* **I:** deel de activa
* **J:** voeg activa aan [!DNL Collection] toe
* **K:** Dichte voorproefscherm
* **L:** Informatie van activa die titel, formaat, grootte, resolutie, markeringen, kleurenmarkeringen, en slimme markeringen omvat.

## Ondersteunde indelingen {#supported-formats}

In de volgende tabel worden de ondersteunde bestandsindelingen weergegeven in [!DNL the Content Hub] :

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

* **Grootte:** de Grootte toont de logische waarde van een activa volgens zijn afmetingen aan. Het verduidelijkt de ruimte die een activa in een bewaarplaats neemt. [!DNL The Content Hub] ondersteunt elementen tot 2 GB.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Slimme Markeringen:** [!DNL The Content Hub] gebruikt de slimme inhoudsdiensten van Adobe Sensei om activa te trainen gebruikend herkenningsalgoritme op de op markeringen-gebaseerde structuur. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. Met slimme tags verhoogt u de snelheid van de inhoud van uw projecten doordat u snel relevante middelen kunt vinden. De slimme tags zijn een voorbeeld van informatie over elementen die niet in de afbeelding voorkomen. [!DNL The Content Hub] past standaard automatisch slimme tags toe op elementen.

* **de Markeringen van de Kleur:** [ markeringen van de Kleur ](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) helpen u activa herkennen gebruikend kleuren die automatisch in een activa gebruikend de mogelijkheden van Sensei van de Adobe worden geïdentificeerd AI.

* Uploaddatum

* Geüpload door

* Laatst gewijzigd

* Laatst gewijzigd door

Er zijn ook eigenschappen die worden opgegeven wanneer elementen aan Content Hub worden toegevoegd. Voor meer informatie, zie [ merk goedgekeurde activa aan Content Hub ](upload-brand-approved-assets.md) toevoegen. Deze eigenschappen worden ook weergegeven op de pagina met eigenschappen van elementen.

Beheerders kunnen ook de eigenschappen configureren die voor elk element worden weergegeven. Voor meer informatie, zie [ Content Hub gebruikersinterface ](configure-content-hub-ui-options.md#configure-asset-details-content-hub) vormen.

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
