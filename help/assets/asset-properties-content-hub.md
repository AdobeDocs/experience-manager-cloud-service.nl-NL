---
title: Elementen en eigenschappen voorvertonen in  [!DNL the Content Hub]
description: Leer hoe u elementen en eigenschappen voorvertoont in  [!DNL Content Hub]
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="van toepassing op AEM Assets)."
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '978'
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

## Veelgestelde vragen {#faqs-asset-properties-content-hub}

### Waarom bekijkt u een voorvertoning van de elementen en hun eigenschappen in AEM Assets Content Hub?

Door een voorvertoning van de activa en hun eigendommen in AEM Assets Content Hub te bekijken, kunnen gebruikers de gegevens van de bedrijfsmiddelen nauwkeurig bekijken. Deze gegevens zijn van essentieel belang voor een efficiënte distributie en beheer van bedrijfsmiddelen. Naarmate de digitale informatie toeneemt, wordt het eenvoudig om bestandsnamen en miniaturen te gebruiken, niet meer schaalbaar. Door gedetailleerde eigenschappen weer te geven kunt u elementen categoriseren, ze toegankelijker, eenvoudiger te gebruiken en zorgt u ervoor dat de informatie volledig is voor alle gebruikers.

### Hoe kan ik de eigenschappen van een actief in AEM Assets Content Hub bekijken en ermee communiceren?

Als u de eigenschappen van een element wilt weergeven in AEM Assets Content Hub, navigeert u naar het element of zoekt u het. Klik vervolgens op het element om de eigenschappenpagina te openen. Hier kunt u in- of uitzoomen op de voorvertoning, zoomen ongedaan maken, naar vorige of volgende elementen gaan, het element downloaden, het bewerken met Adobe Express, het toevoegen aan een verzameling of de voorvertoning sluiten. Op de eigenschappenpagina wordt gedetailleerde informatie weergegeven, zoals titel, opmaak, grootte, resolutie, tags, kleurtags en slimme tags.

### Wat zijn afgeleide eigenschappen in AEM Assets Content Hub, en hoe worden zij geproduceerd?

Afgeleide eigenschappen in AEM Assets Content Hub worden automatisch gegenereerd wanneer elementen worden geüpload en goedgekeurd. Voorbeelden zijn de grootte van het element, slimme tags en kleurcodes. Slimme tags maken gebruik van Adobe AI Smart Content Services om relevante tags automatisch te herkennen en toe te passen, waardoor de herkenbaarheid van bedrijfsmiddelen wordt vergroot. Kleurlabels worden ook automatisch herkend met AI, zodat gebruikers elementen herkennen aan hun prominente kleuren.

### Kunnen beheerders aanpassen welke activa eigenschappen in AEM Assets Content Hub zichtbaar zijn?

Ja, beheerders kunnen configureren welke eigenschappen worden weergegeven voor elk element in de AEM Assets Content Hub. Dit kan zowel voor de gebruikersinterface van de activavoorproef als activakaarten in onderzoeksresultaten of inzamelingen worden gedaan, die ervoor zorgen dat de gebruikers de meest relevante informatie zien die op de vereisten wordt gebaseerd.

### Wat zijn de ondersteunde bestandsindelingen voor de voorvertoning van elementen in AEM Assets Content Hub?

De ondersteunde bestandsindelingen in AEM Assets Content Hub zijn onder andere JPEG en PNG voor afbeeldingen, QuickTime, MP4 en MPEG voor video&#39;s, TXT, DOC/DOCX en XML voor documenten en PDF voor afdrukmedia.


