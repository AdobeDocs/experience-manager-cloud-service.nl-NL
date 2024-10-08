---
title: Elementen in mappen en verzamelingen controleren
description: Stel revisieworkflows in voor elementen in een map of verzameling en deel deze met revisoren of creatieve partners om feedback te zoeken.
contentOwner: AG
feature: Collections, Collaboration
role: User
exl-id: 1e5bdd66-2707-4584-87ed-a0ff1bde3718
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 3%

---

# Elementen in mappen en verzamelingen controleren {#review-folder-assets-and-collections}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/bulk-approval.html?lang=en) |
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
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
