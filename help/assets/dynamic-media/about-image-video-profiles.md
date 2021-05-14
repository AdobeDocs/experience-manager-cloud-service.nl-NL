---
title: Informatie over Dynamic Media-afbeeldingsprofielen en videoprofielen
description: Een afbeeldingsprofiel of videoprofiel is een recept voor de opties die u kunt toepassen op elementen die u uploadt naar een map. U kunt bijvoorbeeld opgeven welke videocodering moet worden toegepast op Dynamic Media-video-elementen die u uploadt. Of welk afbeeldingsprofiel moet worden toegepast op Dynamic Media-afbeeldingselementen om deze op de juiste wijze te kunnen bijsnijden.
feature: Middelenbeheer, afbeeldingsprofielen, videoprofielen
role: Administrator,Business Practitioner
exl-id: 8c8f0a57-13f5-4903-8d76-bfb6ee83323c
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 2%

---

# Informatie over Dynamic Media-afbeeldingsprofielen en videoprofielen{#about-dm-image-video-profiles}

Een afbeeldingsprofiel of videoprofiel is een recept voor de opties die u kunt toepassen op elementen die u uploadt naar een map. U kunt bijvoorbeeld opgeven welke videocodering moet worden toegepast op Dynamic Media-video-elementen die u uploadt. Of welk afbeeldingsprofiel moet worden toegepast op Dynamic Media-afbeeldingselementen om deze op de juiste wijze te kunnen bijsnijden.

In Dynamic Media kunt u twee typen profielen maken, die in detail worden besproken op de volgende koppelingen:

* [Dynamic Media-afbeeldingsprofielen](/help/assets/dynamic-media/image-profiles.md)
* [Dynamic Media-videoprofielen](/help/assets/dynamic-media/video-profiles.md)

Zie ook [Metagegevensprofielen](/help/assets/metadata-profiles.md).

U moet beheerdersrechten hebben om Dynamic Media Image Profiles of Dynamic Media Video Profiles te maken, te bewerken en te verwijderen.

Nadat u een afbeeldingsprofiel of videoprofiel hebt gemaakt, wijst u dit toe aan een of meer mappen die u gebruikt voor nieuw geüploade Dynamic Media-elementen.

Zie ook [Aanbevolen procedures voor het ordenen van uw digitale elementen voor het gebruik van afbeeldingsprofielen of videoprofielen](/help/assets/dynamic-media/best-practices-for-file-management.md).

>[!NOTE]
>
>Elementen die u van de ene map naar de andere verplaatst, worden niet opnieuw verwerkt. Stel dat u Map 1 hebt waaraan profiel A is toegewezen en Map 2 waaraan profiel B is toegewezen. Als u elementen verplaatst van map 1 naar map 2, behouden de verplaatste elementen hun oorspronkelijke verwerking van map 1.
>
>Hetzelfde geldt ook wanneer u elementen verplaatst tussen twee mappen waaraan hetzelfde profiel is toegewezen.

## Dynamic Media-elementen in een map {#reprocessing-assets} opnieuw verwerken

U kunt elementen opnieuw verwerken in een map die al een bestaand Dynamic Media-afbeeldingsprofiel heeft of een Dynamic Media-videoprofiel dat u later hebt gewijzigd.

Stel dat u een Dynamic Media-afbeeldingsprofiel hebt gemaakt en dit aan een map hebt toegewezen. Op alle afbeeldingselementen die u naar de map hebt geüpload, wordt het afbeeldingsprofiel automatisch toegepast op de elementen. Later besluit u echter een nieuwe verhouding voor slimme uitsnijden toe te voegen aan het afbeeldingsprofiel. Nu hoeft u de elementen niet meer opnieuw naar de map te selecteren en te uploaden, maar gewoon de *Scene7 uit te voeren: Elementen opnieuw verwerken* workflow.

U kunt de herverwerkingsworkflow uitvoeren op een element waarvoor de verwerking de eerste keer is mislukt. Zelfs als u geen afbeeldingsprofiel of videoprofiel hebt bewerkt of als u al een afbeeldingsprofiel of videoprofiel hebt toegepast, kunt u de workflow voor het opnieuw verwerken van een map met elementen altijd uitvoeren.

U kunt optioneel de batchgrootte van de workflow voor het opnieuw verwerken aanpassen van een standaard van 50 elementen tot 1000 elementen. Wanneer u _Scene7 in werking stelt: Elementen opnieuw verwerken_ in een map, middelen worden gegroepeerd in batches en vervolgens naar de Dynamic Media-server verzonden voor verwerking. Na de verwerking worden de metagegevens van elk element in de volledige batchset bijgewerkt in Adobe Experience Manager. Als de partij groot is, kunt u een vertraging in verwerking ervaren. Als de batch te klein is, kan dit ook leiden tot te veel retourvluchten naar de Dynamic Media-server.

Zie [De batchgrootte van de workflow voor opnieuw verwerken aanpassen](#adjusting-load).

>[!NOTE]
>
>Als u een massale migratie van middelen van Dynamic Media Classic naar Experience Manager uitvoert, laat de de replicatieagent van de Migratie op de server van Dynamic Media toe. Wanneer de migratie volledig is, zorg ervoor u de agent onbruikbaar maakt.
>
>De Migratie-publicatieagent moet zijn uitgeschakeld op de Dynamic Media-server, zodat de workflow voor opnieuw verwerken naar behoren functioneert.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**Dynamic Media-elementen in een map opnieuw verwerken:**
1. Navigeer in Experience Manager vanaf de middelenpagina naar een map met elementen waaraan een afbeeldingsprofiel of een videoprofiel is toegewezen en waarvoor u de **Scene7 wilt toepassen: Workflow Asset** opnieuw verwerken.

   Mappen waaraan een afbeeldingsprofiel of videoprofiel is toegewezen, krijgen de naam van het profiel direct onder de mapnaam in de Kaartweergave.

1. Selecteer een map.

   * In de workflow worden alle bestanden in de geselecteerde map recursief bekeken.
   * Als er een of meer submappen met elementen in de geselecteerde hoofdmap staan, worden alle elementen in de maphiërarchie opnieuw verwerkt.
   * U kunt deze workflow het beste niet uitvoeren in een mappenhiërarchie met meer dan 1000 elementen.

1. Klik in de linkerbovenhoek van de pagina in de vervolgkeuzelijst op **[!UICONTROL Timeline]**.
1. Tik in de linkerbenedenhoek van de pagina, rechts van het veld [!UICONTROL Comment], op het karatpictogram ( **^** ).

   ![Workflow 1 voor opnieuw verwerken van middelen](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Klik op **[!UICONTROL Start Workflow]**.
1. Kies **[!UICONTROL Scene7: Reprocess Assets]** in de vervolgkeuzelijst **[!UICONTROL Start Workflow]**.
1. (Optioneel) Voer in het tekstveld **Voer een titel van de workflow in** een naam voor de workflow in. U kunt de naam gebruiken om naar de werkstroominstantie te verwijzen, indien nodig.

   ![Activa opnieuw verwerken 2](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. Klik **[!UICONTROL Start]**, dan klik **[!UICONTROL Confirm]**.

   Om het werkschema te controleren of zijn vooruitgang te controleren, van de Experience Manager belangrijkste consolepagina, klik **[!UICONTROL Tools > Workflow]**. Selecteer een workflow op de pagina Workflowinstanties. Klik op **[!UICONTROL Open History]** op de menubalk. U kunt een geselecteerde workflow ook beëindigen, onderbreken of hernoemen op dezelfde pagina Workflowinstanties.

### De batchgrootte van de workflow voor opnieuw verwerken aanpassen {#adjusting-load}

(Optioneel) De standaardbatch-grootte in de opwerkingsworkflow is 50 elementen per taak. Deze optimale omvang van de partij wordt bepaald door de gemiddelde omvang van de activa en de MIME-typen van activa waarop het herproces wordt uitgevoerd. Een hogere waarde betekent dat u veel bestanden in één opwerkingstaak hebt. De verwerkingsbanner blijft dus langer op Experience Manager-elementen. Als de gemiddelde bestandsgrootte echter klein-1 MB of kleiner-Adobe is, wordt u aangeraden de waarde te verhogen tot enkele 100, maar nooit meer dan 1000. Als de gemiddelde bestandsgrootte honderden megabytes is, raadt Adobe u aan de batch tot 10 te verkleinen.

**U kunt de batchgrootte van de workflow voor opnieuw verwerken desgewenst aanpassen:**

1. Tik in Experience Manager op **[!UICONTROL Adobe Experience Manager]** om naar de globale navigatieconsole te gaan en tik vervolgens op het pictogram **[!UICONTROL Tools]** (hamer) > **[!UICONTROL Workflow > Models]**.
1. Voor de pagina van de Modellen van het Werkschema, in de Mening van de Kaart of de Mening van de Lijst, selecteer **[!UICONTROL Scene7: Reprocess Assets]**.

   ![Pagina Workflowmodellen met Scene7: Workflow voor opnieuw verwerken van middelen die zijn geselecteerd in Kaartweergave](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. Klik op **[!UICONTROL Edit]** op de werkbalk. Met een nieuw browsertabblad wordt de Scene7 geopend: Modelpagina voor middelenwerkstroom opnieuw verwerken.
1. Op de Scene7: Tik in de rechterbovenhoek op **[!UICONTROL Edit]** om de workflow te &quot;ontgrendelen&quot;.
1. Selecteer in de workflow de Scene7-component Batch uploaden om de werkbalk te openen en tik vervolgens op **[!UICONTROL Configure]** in de werkbalk.

   ![Scene7-component Batch uploaden](/help/assets/dynamic-media/assets/reprocess-assets8.png)

1. Stel in het dialoogvenster **[!UICONTROL Batch Upload to Scene7—Step Properties]** het volgende in:
   * Typ desgewenst een nieuwe titel en beschrijving voor de taak in de tekstvelden **[!UICONTROL Title]** en **[!UICONTROL Description]**.
   * Selecteer **[!UICONTROL Handler Advance]** als uw manager aan de volgende stap zal verdergaan.
   * Voer in het veld **[!UICONTROL Timeout]** de time-out van het externe proces (seconden) in.
   * Voer in het veld **[!UICONTROL Period]** een pollinginterval (seconden) in om te testen of het externe proces is voltooid.
   * Voer in **[!UICONTROL Batch field]** het maximumaantal elementen (50-1000) in dat u wilt verwerken in een uploadtaak voor batchverwerking van een Dynamic Media-server.
   * Selecteer **[!UICONTROL Advance on timeout]** als u wilt vooruitgaan wanneer de onderbreking wordt bereikt. Schakel deze optie uit als u wilt doorgaan naar het Postvak IN wanneer de time-out is bereikt.

   ![Eigenschappen, dialoogvenster](/help/assets/dynamic-media/assets/reprocess-assets3.png)

1. Tik in de rechterbovenhoek van het dialoogvenster **[!UICONTROL Batch Upload to Scene7 – Step Properties]** op **[!UICONTROL Done]**.

1. In de rechterbovenhoek van de Scene7: Tik op **[!UICONTROL Sync]** om de modelpagina Elementen opnieuw te verwerken. Wanneer u **[!UICONTROL Synced]** ziet, wordt het model van de werkschemaruntime met succes gesynchroniseerd en klaar om activa in een omslag opnieuw te verwerken.

   ![Het workflowmodel synchroniseren](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Sluit het browsertabblad waarin de Scene7 wordt weergegeven: Workflowmodel voor opnieuw verwerken van middelen.

<!-- MAY BE NEEDED IN THE FUTURE

1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/security/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/security/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.

-->
