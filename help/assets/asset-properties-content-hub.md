---
title: Elementen en eigenschappen voorvertonen in  [!DNL the Content Hub]
description: Leer hoe u elementen en eigenschappen voorvertoont in  [!DNL Content Hub]
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Middelen voorvertonen en de eigenschappen ervan in Content Hub {#asset-properties}

![ Bannerbeeld van de metagegevensbanner ](assets/metadata-banner-image.png)

Met [!DNL The Content Hub] kunt u informatie over het element weergeven die essentieel is voor een efficiënte distributie van elementen. Het is de verzameling van alle gegevens die beschikbaar zijn voor een element.

Door de voorvertoning van elementen en de bijbehorende eigenschappen weer te geven, kunt u elementen verder indelen. Dit is handig als de hoeveelheid digitale informatie toeneemt. U kunt een paar honderd bestanden beheren op basis van alleen de bestandsnamen, miniaturen en het geheugen. Nochtans, is deze benadering niet scalable wanneer het aantal betrokken personen, en het aantal beheerde activa stijgen. Bovendien neemt de waarde van een digitaal element toe naarmate het element wordt:

* Toegankelijker - systemen en gebruikers kunnen het gemakkelijk vinden.
* Gemakkelijker om op te treden - u hebt volledige informatie over de visuals en de verwante informatie van activa, om op hen sneller en met meer vertrouwen te kunnen handelen.
* Complete - asset bevat meer informatie en context.

## Vereisten {#prerequisites}

[ de gebruikers van Content Hub ](deploy-content-hub.md#onboard-content-hub-users) kunnen acties uitvoeren die in dit artikel worden vermeld.

## Middelen voorvertonen en de eigenschappen ervan {#properties-ui}

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

## Ondersteunde elementindelingen {#supported-formats}

[!DNL Content Hub] ondersteunt alle typen elementen en indelingen die door de onderliggende [!DNL Assets] -opslagplaats worden ondersteund. In de volgende tabel vindt u een overzicht van de belangrijkste bestandsindelingen in [!DNL the Content Hub] , die extra ondersteuning bieden voor het visueel voorvertonen van elementen:

<table> 
    <tbody>
     <tr>
      <th><strong>Bestandstype</strong></th>
      <th><strong>Ondersteunde indelingen</strong></th>
     </tr>
     <tr>
        <td rowspan="3"> Afbeelding </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
    </tr>
    <tr>
        <td rowspan="4"> Video </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL Quicktime]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MPEG]</td>
    </tr>
    <tr>
        <td rowspan="4"> Document </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL txt] (Normaal)</td>
    </tr>
    <tr>
        <td>[!UICONTROL Doc/Docx]</td>
    </tr>
    <tr>
        <td>[!UICONTROL XML]</td>
    </tr>
    <tr>
        <td rowspan="2"> Media afdrukken </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL PDF]</td>
    </tr>
    </tbody>
</table>

### Afgeleide eigenschappen {#derived-properties}

Sommige eigenschappen voor elementen die worden weergegeven in [!DNL Content Hub] , worden afgeleid of automatisch gegenereerd wanneer elementen worden geüpload naar [!DNL Assets] en vervolgens worden goedgekeurd voor beschikbaarheid op [!DNL Content Hub] . Hieronder volgt een lijst van enkele voorbeelden:

* **Grootte:** de Grootte vertegenwoordigt de grootte van de activa binair die in de onderliggende bewaarplaats wordt opgeslagen.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Slimme Markeringen:** [!DNL The Content Hub] gebruikt de slimme inhoudsdiensten van Adobe AI om activa te trainen gebruikend herkenningsalgoritme op de op markeringen-gebaseerde structuur. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. Met slimme tags verhoogt u de snelheid van de inhoud van uw projecten doordat u snel relevante middelen kunt vinden. De slimme tags zijn een voorbeeld van informatie over elementen die niet in de afbeelding voorkomen. [!DNL Experience Manager Assets] past standaard automatisch slimme tags toe op elementen.

* **de Markeringen van de Kleur:** [ de markeringen van de Kleur ](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) helpen u activa herkennen gebruikend kleuren die automatisch in activa gebruikend Adobe AI mogelijkheden worden geïdentificeerd.

* Uploaddatum

* Geüpload door

* Laatst gewijzigd

* Laatst gewijzigd door

Er zijn ook eigenschappen die worden opgegeven wanneer elementen aan Content Hub worden toegevoegd. Voor meer informatie, zie [ merk goedgekeurde activa aan Content Hub ](upload-brand-approved-assets.md) toevoegen. Deze eigenschappen worden ook weergegeven op de pagina met eigenschappen van elementen.

Beheerders kunnen ook de eigenschappen configureren, die voor elk element worden weergegeven:

* In de activavoorproef UI: zie [ Content Hub gebruikersinterface ](configure-content-hub-ui-options.md#configure-asset-details-content-hub) vormen.
* Op activakaarten in onderzoeksresultaten of inzamelingen: zie [ Content Hub gebruikersinterface ](configure-content-hub-ui-options.md#asset-card) vormen.

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
