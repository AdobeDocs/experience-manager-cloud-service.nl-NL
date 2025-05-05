---
title: Verzamelingen beheren in Content Hub
description: Leer hoe u verzamelingen beheert in Content Hub
role: User
exl-id: ea74456c-f980-4a02-b26b-d7c46dac6aee
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Verzamelingen beheren in [!DNL Content Hub] {#manage-collections}

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

<!-- ![Manage collections](assets/manage-collections.jpg) -->
![Verzamelingen beheren](assets/manage-collection.png)

>[!AVAILABILITY]
>
>Content Hub-gids is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE &#x200B; de Gids PDF van Content Hub &#x200B;]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Een verzameling verwijst naar een set elementen die onder gebruikers kunnen worden gedeeld. Een verzameling kan elementen van verschillende locaties bevatten, terwijl de referentiële integriteit ervan behouden blijft.

Met [!DNL Content Hub] kunt u openbare verzamelingen maken. Deze verzamelingen zijn toegankelijk voor alle gemachtigde gebruikers, zodat een gedeelde ruimte ontstaat waar meerdere gebruikers op efficiënte wijze toegang hebben tot inhoud en deze kunnen gebruiken. Verzamelingen bevorderen gezamenlijk gebruik van bronnen voor meer efficiëntie en gemak. Binnen de inzameling doorbladert pagina, kunt u:

* **creeer**: Creeer één of meerdere inzamelingen.
* **Mening**: Bekijk de activa en hun eigenschappen.
* **Aandeel**: De activa van het aandeel als verbinding met anderen.
* **Download**: Download de activa.
* **verwijder**: Verwijder specifieke activa uit een inzameling.
* **Schrapping**: Schrap de volledige inzameling.

Hiermee kunnen gebruikers eenvoudig toegang krijgen tot de verschillende middelen die beschikbaar zijn in [!DNL Content Hub] en deze beheren.

## Vereisten {#prerequisites}

[ de gebruikers van Content Hub ](deploy-content-hub.md#onboard-content-hub-users) kunnen acties uitvoeren die in dit artikel worden vermeld.

## Verzamelingen maken{#create-collections}

U kunt verkiezen om [ tot een nieuwe inzameling ](#create-new-collection) te leiden of [ activa aan een bestaande inzameling ](#add-assets-to-existing-collection) toe te voegen.

### Een nieuwe verzameling maken{#create-new-collection}

Selecteer de elementen die u aan een verzameling wilt toevoegen en klik op **[!UICONTROL Add To collection]** .

![ creeer inzameling ](assets/add-assets-collection.jpg)

Als u een nieuwe verzameling wilt maken, navigeert u naar de tab **[!UICONTROL Collections]** en klikt u op **[!UICONTROL Create new collection]** . Voer de **[!UICONTROL Title]** in en geef een optioneel **[!UICONTROL Description]** voor de elementen op. Klik op **[!UICONTROL Create]**.

### Elementen toevoegen aan een bestaande verzameling{#add-assets-to-existing-collection}

Als u elementen aan een bestaande verzameling wilt toevoegen, selecteert u de elementen die u aan de verzameling wilt toevoegen. Klik op **[!UICONTROL Add to collection]**. U wordt gevraagd de verzameling te selecteren.

![ creeer een nieuwe inzameling ](assets/create-add-collection.jpg)

Kies de verzameling waar u het element wilt toevoegen. U kunt de bestaande verzameling ook doorzoeken met de zoekbalk. <br> selecteer de inzameling (s) waaraan u de activa moet toevoegen en **[!UICONTROL Add to collection]** klikken.

## Verzamelingen weergeven{#view-collections}

Navigeer naar het tabblad **[!UICONTROL Collections]** en zoek naar de naam van de verzameling. Klik op de naam van de verzameling als u de lijst met elementen die beschikbaar zijn in een verzameling wilt weergeven. U kunt filters ook toepassen binnen een verzameling om de resultaten van de elementen te beperken.

Klik op het element dat u wilt weergeven in een verzameling. [!DNL Content Hub] geeft de gedetailleerde weergave van het element weer. [ zie activa details ](asset-properties-content-hub.md).

<!--
![Asset details](assets/view-collection.jpg)

* **A**: Details and metadata of the asset 
* **B**: Zoom In or Zoom Out the asset 
* **C**: Reset Zoom view 
* **D**: View the previous or next asset 
* **E**: Download the asset 
* **F**: Open the asset in Adobe Express 
* **G**: Hide the metadata of the asset 
* **H**: Share the asset as a link 
-->

## Elementen downloaden die beschikbaar zijn in een verzameling{#download-assets-within-collection}

Navigeer naar het tabblad **[!UICONTROL Collections]** als u elementen die beschikbaar zijn in een verzameling wilt downloaden.\
Klik ![ pictogram van de downloaddownload ](assets/download-icon.svg) pictogram op de inzamelingskaart.

![ lusje van de Inzameling ](assets/download-collection.jpg)

Alle elementen in de verzameling worden gedownload.

U kunt de verzameling ook openen om de elementen afzonderlijk te downloaden. Klik op de verzameling met de elementen die u wilt downloaden. Selecteer de elementen en klik op **[!UICONTROL Download]** .

Leer hoe te om [ activa van  [!DNL Content Hub]](download-assets-content-hub.md) te downloaden.

## Elementen delen die beschikbaar zijn in een verzameling {#share-assets-available-within-collection}

U kunt ook de elementen delen die beschikbaar zijn in een verzameling. Navigeer naar de tab **[!UICONTROL Collections]** . Selecteer het ![ pictogram van het aandeel ](assets/share.svg) pictogram op de inzamelingskaart. De koppeling voor delen wordt gekopieerd. U kunt de gekopieerde koppeling delen met de ontvanger. Leer meer over [ delend activa in  [!DNL Content Hub]](share-assets-content-hub.md).

## Details van een verzameling bewerken {#edit-details-of-collection}

Om **[!UICONTROL Title]** en **[!UICONTROL Description]** van een inzameling uit te geven, klik de inzamelingsnaam en klik dan het ![ infopictogram ](assets/info-icon.svg) pictogram. [!UICONTROL Collection Details] wordt weergegeven, zodat u de **[!UICONTROL Title]** en **[!UICONTROL Description]** van een verzameling kunt bewerken. Klik op **[!UICONTROL Save Changes]** om de wijzigingen te bevestigen.

![ inzamelingsdetails ](assets/collection-details.png)

## Elementen uit een verzameling verwijderen{#remove-assets-from-a-collection}

U kunt een of meer elementen uit een verzameling verwijderen. Als u elementen uit een verzameling wilt verwijderen, klikt u op de verzameling waaruit u elementen wilt verwijderen, selecteert u de elementen en klikt u op **[!UICONTROL Remove from collection]** .

![ verwijder inzameling ](assets/remove-collection-new.jpg)

U wordt gevraagd de verwijdering van het element te bevestigen. Klik op **[!UICONTROL Remove]**.\
De geselecteerde elementen worden uit de verzameling verwijderd.

## Een verzameling verwijderen{#delete-collection}

Als u een verzameling wilt verwijderen, navigeert u naar het tabblad **[!UICONTROL Collections]** en klikt u op de verzameling die u wilt verwijderen. Klik ![ verwijderen pictogram ](assets/remove-icon.svg) pictogram om de inzameling te schrappen.
