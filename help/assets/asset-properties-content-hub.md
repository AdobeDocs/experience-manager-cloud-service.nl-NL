---
title: Elementen en eigenschappen voorvertonen in  [!DNL the Content Hub]
description: Leer hoe u elementen en eigenschappen voorvertoont in  [!DNL Content Hub]
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# Middelen voorvertonen en de eigenschappen ervan in Content Hub {#asset-properties}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

![ Bannerbeeld van de metagegevensbanner ](assets/metadata-banner-image.png)

>[!AVAILABILITY]
>
>Content Hub-gids is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE &#x200B; de Gids PDF van Content Hub &#x200B;]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

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

### Afgeleide eigenschappen {#derived-properties}

Sommige eigenschappen voor elementen die worden weergegeven in [!DNL Content Hub] , worden afgeleid of automatisch gegenereerd wanneer elementen worden geüpload naar [!DNL Assets] en vervolgens worden goedgekeurd voor beschikbaarheid op [!DNL Content Hub] . Hieronder volgt een lijst van enkele voorbeelden:

* **Grootte:** de Grootte vertegenwoordigt de grootte van de activa binair die in de onderliggende bewaarplaats wordt opgeslagen.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Slimme Markeringen:** [!DNL The Content Hub] gebruikt de slimme inhoudsdiensten van Adobe Sensei om activa te trainen gebruikend herkenningsalgoritme op de op markeringen-gebaseerde structuur. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. Met slimme tags verhoogt u de snelheid van de inhoud van uw projecten doordat u snel relevante middelen kunt vinden. De slimme tags zijn een voorbeeld van informatie over elementen die niet in de afbeelding voorkomen. [!DNL Experience Manager Assets] past standaard automatisch slimme tags toe op elementen.

* **de Markeringen van de Kleur:** [ de markeringen van de Kleur ](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) helpen u activa herkennen gebruikend kleuren die automatisch in een activa gebruikend de mogelijkheden van Adobe AIR AI worden geïdentificeerd.

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
