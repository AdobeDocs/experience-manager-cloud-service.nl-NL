---
title: Bulkmetagegevens bewerken in  [!DNL Assets View]
description: Leer hoe u een vooraf gedefinieerde set standaardmetagegevensvelden kunt bijwerken voor meerdere middelen die beschikbaar zijn op de [DNL!] Assets View] tegelijkertijd.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 19c5155363ef3f5083d36af880727a33c7224e84
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Bulkmetagegevens bewerken in [!DNL Assets View]{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

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

Met de **[!DNL Bulk Metadata Edit]** mogelijkheid van [!DNL Assets View] kunt u een vooraf gedefinieerde set standaardmetagegevensvelden voor meerdere elementbestanden tegelijk bewerken. Selecteer meerdere elementen en bulksgewijs werk de vooraf gedefinieerde set standaardmetagegevens tegelijk bij in plaats van deze standaardmetagegevens voor elk element afzonderlijk bij te werken. Met deze functie blijven de efficiëntie, consistentie en nauwkeurigheid van de set standaardeigenschappen voor metagegevens in de grote sets elementen behouden, waardoor de doorzoekbaarheid en organisatie van deze elementen worden verbeterd.

## Metagegevens van elementen in blokvorm bewerken {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Voer de volgende stappen uit om de metagegevens van meerdere elementen tegelijk in bulk te bewerken:

1. Ga naar **[!DNL Assets View]** en klik op **[!UICONTROL Assets]** .
1. Blader naar specifieke elementen of doorzoek deze met behulp van trefwoorden op de zoekbalk.
1. Selecteer de elementen en klik op **[!UICONTROL Bulk Metadata Edit]** in het bovenste menu.
   ![ bulk-meta-gegeven-geef uit ](/help/assets/assets/bulk-metadata-edit1.png)
1. Bewerk in het [!UICONTROL Edit metadata page] de volgende velden in het deelvenster **[!UICONTROL Properties]** :
   * **[!UICONTROL Status]:** selecteer een status voor de geselecteerde elementen.
   * **[!UICONTROL Expiration date]:** Stel een datum in waarna de elementen niet meer geldig of nodig zijn.
   * **[!UICONTROL Author]:** specificeer de naam van de auteur.
   * **[!UICONTROL Keywords]:** voeg specifieke termijnen of tekstkoorden toe die een informatie op hoog niveau over de activa verstrekken om hun ontdekkingsbaarheid te verbeteren. Voeg een sleutelwoord toe en druk **ga** of **terugkeer** in om een ander sleutelwoord aan de lijst toe te voegen.
   * **[!UICONTROL Tags]:** klik ![ bulkmeta-gegevens uitgeven ](/help/assets/assets/tags-icon.svg) om markeringen van de beschikbare opties te selecteren. Tags bieden specifiekere informatie over de elementen en verbeteren de ontdekkingsmogelijkheden ervan. Labels die al zijn toegepast op de geselecteerde elementen, worden weergegeven in het deelvenster **[!UICONTROL Properties]** . Als u de relevante tags niet kunt vinden, maakt u deze en wijst u deze toe aan de geselecteerde elementen. Zie [ markeringen binnen beheren  [!DNL Assets view]](/help/assets/tagging-management-assets-view.md) voor details bij het creëren van en het toewijzen van markeringen aan activa.
   * Klik op **[!UICONTROL Save]** om de bovenstaande updates van metagegevens toe te passen op de geselecteerde elementen. Als de gegevens voor **[!UICONTROL Status]** , **[!UICONTROL Expiration date]** en **[!UICONTROL Author]** eenmaal zijn opgeslagen, worden **[!UICONTROL Keywords]** en **[!UICONTROL Tags]** toegevoegd en worden de bestaande gegevens door de bijgewerkte details voor  ,  en  genegeerd.
     ![ sparen-bulk-meta-gegeven-geef-eigenschappen uit ](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >U kunt de metagegevens van 100 elementen tegelijk bewerken.

Om de toegepaste meta-gegevensupdates aan een activa te zien, navigeer aan [!DNL asset details page] (uitgezochte activa, en klik **[!UICONTROL Details]**) en klik ![ bulkmeta-gegevens uitgeven ](/help/assets/assets/info-icon-solid-black.svg) om de meta-gegevens van de activa in het **[!UICONTROL Information]** paneel te zien.

>[!NOTE]
>
>**[!UICONTROL Status]** , **[!UICONTROL Expiration date]** , **[!UICONTROL Author]** , **[!UICONTROL Keywords]** en **[!UICONTROL Tags]** zijn standaardeigenschappen voor metagegevens die in bulk kunnen worden bewerkt, ongeacht de mapspecifieke metagegevens. Deze eigenschappen van metagegevens worden alleen weergegeven op de [!UICONTROL asset details page] als ze zijn opgenomen in het metagegevensformulier dat is toegepast op de map van het element. Als u deze standaardeigenschappen voor metagegevens niet kunt vinden op de [!UICONTROL asset details page] , bewerkt u het metagegevensformulier van de elementmap om deze op te nemen. Zie [ Meta-gegevens in  [!DNL Assets View]](/help/assets/metadata-assets-view.md) leren om een meta-gegevensvorm tot stand te brengen of uit te geven en het op een omslag toe te passen.
