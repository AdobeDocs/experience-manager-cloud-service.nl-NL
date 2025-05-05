---
title: Elementen in mappen en verzamelingen controleren
description: Stel revisieworkflows in voor elementen in een map of verzameling en deel deze met revisoren of creatieve partners om feedback te zoeken.
contentOwner: AG
feature: Collections, Collaboration
role: User
exl-id: 1e5bdd66-2707-4584-87ed-a0ff1bde3718
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 3%

---

# Elementen in mappen en verzamelingen controleren {#review-folder-assets-and-collections}

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

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/bulk-approval.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Met Adobe Experience Manager Assets kunt u werkstromen voor ad-hocrevisies instellen voor elementen in een map of een verzameling. U kunt deze delen met revisoren of creatieve partners om hun feedback te vragen. U kunt een revisiewerkstroom aan een project koppelen of een onafhankelijke revisietaak maken.

Nadat u de middelen hebt gedeeld, kunnen revisoren deze goedkeuren of afwijzen. Meldingen worden in verschillende fasen van de workflow verzonden om beoogde ontvangers op de hoogte te stellen van de voltooiing van verschillende taken. Als u bijvoorbeeld een map of verzameling deelt, ontvangt de controleur een melding dat een map of verzameling is gedeeld voor revisie.

Nadat de controleur de revisie heeft voltooid (activa goedkeurt of verwerpt), ontvangt u een bericht dat de revisie is voltooid.

## Een revisietaak voor mappen maken {#creating-a-review-task-for-folders}

1. Selecteer in de gebruikersinterface van Assets de map waarvoor u een revisietaak wilt maken.
1. Selecteer op de werkbalk het pictogram **[!UICONTROL Create Review Task]** om de pagina van **[!UICONTROL Review Task]** te openen. Als het pictogram niet op de werkbalk wordt weergegeven, selecteert u **[!UICONTROL More]** en vervolgens het pictogram.

   ![ chlimage_1-403 ](assets/chlimage_1-403.png)

1. (Optioneel) Selecteer in de lijst **[!UICONTROL Project]** het project waaraan u de revisietaak wilt koppelen. Standaard is de optie **[!UICONTROL None]** geselecteerd. Als u geen project aan de overzichtstaak wilt associëren, behoud deze selectie.

   >[!NOTE]
   >
   >Alleen de projecten waarvoor u de machtiging op Editor (of hoger) hebt, zijn zichtbaar in de lijst **[!UICONTROL Projects]** .

1. Voer een naam in voor de revisietaak en selecteer een fiatteur in de lijst **[!UICONTROL Assign To]** .

   >[!NOTE]
   >
   >De leden/groepen van het geselecteerde project zijn beschikbaar als fiatteurs in de **[!UICONTROL Assign To]** lijst.

1. Voer een beschrijving, de prioriteit van de taak en de vervaldatum voor de controletaak in.

   ![ task_details ](assets/task_details.png)

1. Voer op het tabblad Geavanceerd een label in dat u wilt gebruiken om de URI te maken.

   ![ review_name ](assets/review_name.png)

1. Selecteer **[!UICONTROL Submit]** en selecteer vervolgens **[!UICONTROL Done]** om het bevestigingsbericht te sluiten. Er wordt een bericht voor de nieuwe taak naar de goedkeurder verzonden.
1. Meld u aan bij [!DNL Experience Manager Assets] als fiatteur en navigeer naar de gebruikersinterface van Assets. Als u elementen wilt goedkeuren, selecteert u het pictogram **[!UICONTROL Notifications]** en selecteert u vervolgens de revisietaak in de lijst.

   ![ bericht ](assets/notification.png)

1. Controleer op de pagina **[!UICONTROL Review Task]** de details van de revisietaak en selecteer vervolgens **[!UICONTROL Review]** .
1. Selecteer op de pagina **[!UICONTROL Review Task]** elementen en selecteer het pictogram **[!UICONTROL Approve/Reject]** dat u wilt goedkeuren of afwijzen.

   ![ review_task ](assets/review_task.png)

1. Selecteer het pictogram **[!UICONTROL Complete]** op de werkbalk. Voer in het dialoogvenster een opmerking in en selecteer **[!UICONTROL Complete]** om te bevestigen.
1. Navigeer naar de gebruikersinterface van Assets en open de map. De pictogrammen voor de goedkeuringsstatus van de elementen worden weergegeven in zowel de Kaart- als lijstweergave.

   **mening van de Kaart**

   ![ chlimage_1-404 ](assets/chlimage_1-404.png)

   **mening van de Lijst**

   ![ review_status_listview ](assets/review_status_listview.png)

## Een revisietaak voor verzamelingen maken {#creating-a-review-task-for-collections}

1. Selecteer op de pagina Verzamelingen de verzameling waarvoor u een revisietaak wilt maken.
1. Selecteer op de werkbalk het pictogram **[!UICONTROL Create Review Task]** om de pagina van **[!UICONTROL Review Task]** te openen. Als het pictogram niet op de werkbalk wordt weergegeven, selecteert u **[!UICONTROL More]** en vervolgens het pictogram.

   ![ chlimage_1-405 ](assets/chlimage_1-405.png)

1. (Optioneel) Selecteer in de lijst **[!UICONTROL Project]** het project waaraan u de revisietaak wilt koppelen. Standaard is de optie **[!UICONTROL None]** geselecteerd. Als u geen project aan de overzichtstaak wilt associëren, behoud deze selectie.

   >[!NOTE]
   >
   >Alleen de projecten waarvoor u de machtiging op Editor (of hoger) hebt, zijn zichtbaar in de lijst **[!UICONTROL Projects]** .

1. Voer een naam in voor de revisietaak en selecteer een fiatteur in de lijst **[!UICONTROL Assign To]** .

   >[!NOTE]
   >
   >De leden/groepen van het geselecteerde project zijn beschikbaar als fiatteurs in de **[!UICONTROL Assign To]** lijst.

1. Voer een beschrijving, de prioriteit van de taak en de vervaldatum voor de controletaak in.

   ![ task_details-collection ](assets/task_details-collection.png)

1. Selecteer **[!UICONTROL Submit]** en selecteer vervolgens **[!UICONTROL Done]** om het bevestigingsbericht te sluiten. Er wordt een bericht voor de nieuwe taak naar de goedkeurder verzonden.
1. Meld u aan bij [!DNL Experience Manager Assets] als fiatteur en navigeer naar de Assets-console. Als u elementen wilt goedkeuren, selecteert u het pictogram **[!UICONTROL Notifications]** en selecteert u vervolgens de revisietaak in de lijst.
1. Controleer op de pagina **[!UICONTROL Review Task]** de details van de revisietaak en selecteer vervolgens **[!UICONTROL Review]** .
1. Alle elementen in de verzameling zijn zichtbaar op de controlepagina. Selecteer de elementen en selecteer het pictogram **[!UICONTROL Approve/Reject]** om elementen goed te keuren of af te wijzen.

   ![ review_task_collection ](assets/review_task_collection.png)

1. Selecteer het pictogram **[!UICONTROL Complete]** op de werkbalk. Voer in het dialoogvenster een opmerking in en selecteer **[!UICONTROL Complete]** om te bevestigen.
1. Navigeer naar de verzamelingsconsole en open de verzameling. De pictogrammen voor de goedkeuringsstatus van de elementen worden weergegeven in zowel de Kaart- als lijstweergave.

   **mening van de Kaart**

   ![ collection_reviewstatuscardview ](assets/collection_reviewstatuscardview.png)

   **mening van de Lijst**

   ![ collection_reviewstatuslistview ](assets/collection_reviewstatuslistview.png)

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
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
