---
title: Bulkmetagegevens bewerken in Assets View
description: Leer hoe u een vooraf gedefinieerde set standaardmetagegevensvelden kunt bijwerken voor meerdere elementen die tegelijkertijd beschikbaar zijn in de Assets View.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Bulkmetagegevens bewerken in Assets View{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

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

De **Bulk Meta-gegevens geeft** eigenschap binnen de Mening van Assets uit staat gebruikers toe om een vooraf bepaalde reeks standaardmeta-gegevensgebieden voor veelvoudige activa gelijktijdig uit te geven dossiers. Selecteer meerdere elementen en bulksgewijs werk de vooraf gedefinieerde set standaardmetagegevens tegelijk bij in plaats van deze standaardmetagegevens voor elk element afzonderlijk bij te werken. Deze functie verbetert de efficiëntie, consistentie en nauwkeurigheid van standaardeigenschappen voor metagegevens in een grote set elementen, waardoor de zoekbaarheid en organisatie van middelen wordt verbeterd.

## Metagegevens van elementen in blokvorm bewerken {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Voer de volgende stappen uit om de metagegevens van meerdere elementen tegelijk in bulk te bewerken:

1. Voor de Mening van Assets, klik **Assets**.
1. Blader naar specifieke elementen of doorzoek deze met behulp van trefwoorden op de zoekbalk.
1. Selecteer de activa en klik **Bulk Meta-gegevens uitgeven** van het hoogste menu.
   ![ bulk-meta-gegeven-geef uit ](/help/assets/assets/bulk-metadata-edit1.png)
1. Op de Edit meta-gegevenspagina, geef de volgende gebieden in het **paneel van Eigenschappen** uit:
   * **Status:** selecteer een status voor de geselecteerde activa.
   * **Vervaldatum:** plaats een datum waarna de activa ongeldig of nodig zijn.
   * **Auteur:** specificeer de naam van de auteur.
   * **Sleutelwoorden:** voeg specifieke termijnen of tekstkoorden toe die een informatie op hoog niveau over de activa verstrekken om hun ontdekkingsbaarheid te verbeteren. Voeg een trefwoord toe en druk op Enter of Return om nog een trefwoord aan de lijst toe te voegen.
   * **Markeringen:** klik ![ etikettenpictogram ](/help/assets/assets/tags-icon.svg) om markeringen van de beschikbare opties te selecteren. Tags bieden specifiekere informatie over de elementen en verbeteren de ontdekkingsmogelijkheden ervan. De markeringen die reeds op de geselecteerde activa worden toegepast tonen in het **paneel van Eigenschappen**. Als u de relevante tags niet kunt vinden, maakt u deze en wijst u ze toe aan de geselecteerde elementen. Zie [ markeringen in de mening van Assets beheren ](/help/assets/tagging-management-assets-view.md) voor details bij het creëren van en het toewijzen van markeringen aan activa.
   * Klik **sparen** om de bovengenoemde meta-gegevensupdates op de geselecteerde activa toe te passen. Nadat trefwoorden en tags zijn opgeslagen, worden deze toegevoegd terwijl de bijgewerkte gegevens voor Status, Vervaldatum en Auteur de bestaande gegevens overschrijven.
     ![ sparen-bulk-meta-gegeven-geef-eigenschappen uit ](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >U kunt de metagegevens van 100 elementen tegelijk bewerken.

Om de toegepaste meta-gegevensupdates aan een activa te zien, navigeer aan de pagina van activadetails (uitgezochte activa, en klik **Details**) en klik ![](/help/assets/assets/info-icon-solid-black.svg) om de meta-gegevens van de activa in het **paneel van de Informatie** te zien.

>[!NOTE]
>
>**Status**, **Vervaldatum**, **Auteur**, **Trefwoorden** en **Markeringen** zijn standaardmeta-gegevenseigenschappen beschikbaar voor bulkmeta-gegevens het uitgeven, ongeacht omslag-specifieke meta-gegevens. Deze eigenschappen van metagegevens worden alleen weergegeven op de pagina met elementdetails als ze zijn opgenomen in het metagegevensformulier dat is toegepast op de map van het element. Als u deze standaardeigenschappen voor metagegevens niet kunt vinden op de pagina met elementdetails, bewerkt u het metagegevensformulier van de map met middelen om deze op te nemen. Zie [ Meta-gegevens in de Mening van Assets ](/help/assets/metadata-assets-view.md) leren om een meta-gegevensvorm tot stand te brengen of uit te geven en het op een omslag toe te passen.
