---
title: Modellen voor inhoudsfragmenten maken, headless Quick Start Guide
description: Met Content Fragment Models wordt de structuur gedefinieerd van de inhoud die u maakt en gebruikt AEM mogelijkheden zonder kop.
translation-type: tm+mt
source-git-commit: d37342feb794b9f1385bb5edd38b2d9bb6e7dff9
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Creërend de Modellen van het fragmenten van het InhoudFragment de Draadloze Snelle Gids van het Begin {#creating-content-fragment-models}

Met Content Fragment Models wordt de structuur gedefinieerd van de inhoud die u maakt en gebruikt AEM mogelijkheden zonder kop.

## Wat zijn modellen van inhoudsfragmenten? {#what-are-content-fragment-models}

[Nu u een configuratie hebt gemaakt, kunt ](create-configuration.md) u deze gebruiken om modellen van inhoudsfragmenten te maken.

Met Content Fragment Models wordt de structuur gedefinieerd van de gegevens en inhoud die u in AEM maakt en beheert. Ze dienen als een soort basisstructuur voor je inhoud. Wanneer u ervoor kiest inhoud te maken, selecteren de auteurs een model voor inhoudsfragmenten dat u definieert en dat hen bij het maken van inhoud begeleidt.

## Een inhoudsfragmentmodel maken {#how-to-create-a-content-fragment-model}

Een informatiearchitect zou deze taken slechts sporadisch uitvoeren aangezien de nieuwe modellen worden vereist. Om aan de slag te kunnen gaan, hoeven we maar één model te maken.

1. Meld u aan bij AEM als Cloud Service en selecteer **Gereedschappen -> Middelen -> Modellen van inhoudsfragment** in het hoofdmenu.
1. Tik of klik op de map die u hebt gemaakt door uw configuratie te maken.

   ![De map Modellen](../assets/models-folder.png)
1. Tik of klik op **Maken**.
1. Geef een **modeltitel**, **Codes** en **Beschrijving** op. U kunt ook **Model inschakelen** selecteren/deselecteren om te bepalen of het model onmiddellijk na verwezenlijking wordt toegelaten.

   ![Een model maken](../assets/models-create.png)
1. Tik in het bevestigingsvenster op **Open** om uw model te configureren.

   ![Bevestigingsvenster](../assets/models-confirmation.png)
1. Gebruikend **de ModelRedacteur van het Model van het Fragment van de Inhoud**, bouw uw Model van het Fragment van de Inhoud door gebieden van **de kolom van Types van Gegevens te slepen**.

   ![Velden slepen en neerzetten](../assets/models-drag-and-drop.png)

1. Nadat u een veld hebt geplaatst, moet u de eigenschappen ervan configureren. De redacteur zal automatisch op **Eigenschappen** lusje voor het toegevoegde gebied schakelen waar u de verplichte gebieden kunt verstrekken.

   ![Eigenschappen configureren](../assets/models-configure-properties.png)
1. Tik of klik op **Opslaan** als u klaar bent met het samenstellen van uw model. Het nieuwe model wordt opgeslagen in de modus **Concept**.

   ![Model in conceptmodus](../assets/models-draft.png)
1. Het model moet zijn ingeschakeld om het te kunnen gebruiken (als dit nog niet is ingeschakeld). Selecteer het model dat u net hebt gemaakt en tik of klik op **Inschakelen**.

   ![Het model inschakelen](../assets/models-enable.png)
1. Bevestig het toelaten van het model door **Enable** in de bevestigingsdialoog te tikken of te klikken.

   ![Bevestigingsvenster inschakelen](../assets/models-enabling.png)
1. Het model is nu ingeschakeld en klaar voor gebruik.

   ![Model ingeschakeld](../assets/models-enabled.png)

De **Inhoudsfragmentmodeleditor** ondersteunt vele verschillende gegevenstypen, zoals eenvoudige tekstvelden, elementverwijzingen, verwijzingen naar andere modellen en JSON-gegevens.

U kunt meerdere modellen maken. Modellen kunnen verwijzen naar andere inhoudsfragmenten. Gebruik [configuraties](create-configuration.md) om uw modellen te organiseren.

## Volgende stappen {#next-steps}

Nu u de structuren van uw Inhoudsfragmenten hebt gedefinieerd door modellen te maken, kunt u verdergaan naar het derde deel van de gids Aan de slag en [mappen maken waarin u de fragmenten zelf opslaat.](create-assets-folder.md)

>[!TIP]
>
>Raadpleeg de [documentatie bij Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md) voor volledige informatie over Content Fragment Models
