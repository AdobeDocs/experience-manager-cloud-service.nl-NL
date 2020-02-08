---
title: Watermerk toevoegen aan uw digitale elementen
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Watermerken {#watermarking}

Met de functie Watermerken in Adobe Experience Manager (AEM) kunt u een digitaal watermerk toevoegen aan elementen, waarmee gebruikers de authenticiteit en het auteursrecht van de elementen kunnen controleren. AEM-elementen ondersteunen tekst die als watermerk moet worden gebruikt in PNG- en JPEG-bestanden.

Als u een watermerk op elementen wilt toepassen, voegt u de stap Watermerk toe in de DAM-werkstroom Element bijwerken.

1. Tik/klik op het AEM-logo en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modellen]**.
1. Selecteer op de pagina Workflowmodellen de workflow **[!UICONTROL DAM Update Asset]** en klik op **[!UICONTROL Bewerken]**.

1. Sleep vanuit het zijpaneel de stap Watermerk **** toevoegen naar de DAM-workflow Element bijwerken.

<!--  ![Darg add watermark step in the DAM update asset workflow](assets/add_watermark_step_aem_assets.png) -->

>[!NOTE]
>
>Plaats de stap Watermerk toevoegen ergens vóór de stap Miniatuur verwerken.

1. Open de stap Watermerk **** toevoegen om de eigenschappen ervan weer te geven.
1. Geef op het tabblad **[!UICONTROL Argumenten]** geldige waarden op in de verschillende velden, zoals tekst, lettertype, grootte, kleur, positie, oriëntatie, enzovoort. Tik op het pictogram Gereed om de wijzigingen te bevestigen.

<!--   ![Provide the arguments in the add watermark step in Assets](assets/arguments_add_watermark_aem_assets.png) -->

1. Sla de workflow **[!UICONTROL DAM Update Asset]** op met de stap Watermerk.
1. Upload een voorbeeldelement vanuit de gebruikersinterface Elementen. Het watermerk wordt weergegeven met de tekengrootte, de kleur enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.
