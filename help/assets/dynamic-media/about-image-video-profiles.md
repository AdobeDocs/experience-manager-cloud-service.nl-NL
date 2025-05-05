---
title: Dynamische profielen van Media-afbeeldingen en videoprofielen
description: Een afbeeldingsprofiel of videoprofiel is een recept voor de opties die u kunt toepassen op elementen die u uploadt naar een map. U kunt bijvoorbeeld opgeven welke videocodering moet worden toegepast op dynamische media-videoelementen die u uploadt. Of welk afbeeldingsprofiel moet worden toegepast op dynamische media-afbeeldingselementen om deze op de juiste wijze te kunnen bijsnijden.
contentOwner: Rick Brough
feature: Asset Management,Image Profiles,Video Profiles
role: Admin,User
exl-id: 8c8f0a57-13f5-4903-8d76-bfb6ee83323c
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%

---

# Dynamische profielen van Media-afbeeldingen en videoprofielen{#about-dm-image-video-profiles}

Een afbeeldingsprofiel of videoprofiel is een recept voor de opties die u kunt toepassen op elementen die u uploadt naar een map. U kunt bijvoorbeeld opgeven welke videocodering moet worden toegepast op dynamische media-videoelementen die u uploadt. Of welk afbeeldingsprofiel moet worden toegepast op dynamische media-afbeeldingselementen om deze op de juiste wijze te kunnen bijsnijden.

In Dynamische media kunt u twee typen profielen maken, die in detail worden besproken op de volgende koppelingen:

* [Dynamische afbeeldingsprofielen van media](/help/assets/dynamic-media/image-profiles.md)
* [Dynamische mediavideoprofielen](/help/assets/dynamic-media/video-profiles.md)

Zie ook {de profielen van 0} Meta-gegevens [&#128279;](/help/assets/metadata-profiles.md).

U moet beheerdersrechten hebben om dynamische profielen voor mediageluurafbeeldingen of dynamische profielen voor mediagelocaties te maken, bewerken en verwijderen.

Nadat u een afbeeldingsprofiel of videoprofiel hebt gemaakt, wijst u dit toe aan een of meer mappen die u gebruikt voor nieuw geüploade dynamische media-elementen.

Zie ook [ Beste praktijken voor het Organiseren van uw Digitale Assets voor het gebruiken van Profielen van de Verwerking ](/help/assets/organize-assets.md).


>[!NOTE]
>
>Assets die u van de ene map naar de andere verplaatst, wordt niet opnieuw verwerkt. Stel dat u Map 1 hebt waaraan profiel A is toegewezen en Map 2 waaraan profiel B is toegewezen. Als u elementen verplaatst van map 1 naar map 2, behouden de verplaatste elementen hun oorspronkelijke verwerking van map 1.
>
>Hetzelfde geldt ook wanneer u elementen verplaatst tussen twee mappen waaraan hetzelfde profiel is toegewezen.

## Dynamische media-elementen in een map opnieuw verwerken {#reprocessing-assets}

U kunt middelen in een omslag opnieuw verwerken die reeds een bestaand Dynamisch Profiel van het Beeld van Media of een Dynamisch Profiel van Media Video heeft dat u later veranderde.

Stel dat u een dynamisch mediaafbeeldingsprofiel hebt gemaakt en dit aan een map hebt toegewezen. Op alle afbeeldingselementen die u naar de map hebt geüpload, wordt het afbeeldingsprofiel automatisch toegepast op de elementen. Later besluit u echter een nieuwe verhouding voor slimme uitsnijden toe te voegen aan het afbeeldingsprofiel. Nu, in plaats van het moeten de activa aan de omslag selecteren en opnieuw uploaden over, stelt u eenvoudig het *Dynamische 1&rbrace; werkschema van Media in werking opnieuw verwerken.*

U kunt de herverwerkingsworkflow uitvoeren op een element waarvoor de verwerking de eerste keer is mislukt. Zelfs als u geen afbeeldingsprofiel of videoprofiel hebt bewerkt of als u al een afbeeldingsprofiel of videoprofiel hebt toegepast, kunt u de workflow voor het opnieuw verwerken van een map met elementen altijd uitvoeren.

U kunt optioneel de batchgrootte van de workflow voor het opnieuw verwerken aanpassen van een standaard van 50 elementen tot 1000 elementen. Wanneer u het _Dynamische 1&rbrace; werkschema van Media van het Herverwerken &lbrace;op een omslag in werking stelt, worden de activa gegroepeerd in partijen, dan verzonden naar de Dynamische server van Media voor verwerking._ Na de verwerking worden de metagegevens van elk element in de volledige batchset bijgewerkt op [!DNL Adobe Experience Manager] . Als de partij groot is, kunt u een vertraging in verwerking ervaren. Als de batch te klein is, kan dit ook leiden tot te veel roundtrips op de Dynamic Media-server.

Zie [ aanpassen de partijgrootte van het herproceswerkschema ](#adjusting-load).

>[!NOTE]
>
>Als u een grote migratie van middelen van Dynamic Media Classic naar [!DNL Experience Manager] uitvoert, laat de de replicatieagent van de Migratie op de Dynamische server van Media toe. Wanneer de migratie volledig is, zorg ervoor u de agent onbruikbaar maakt.
>
>De migratiepublicatieagent moet zijn uitgeschakeld op de Dynamic Media-server, zodat de workflow voor opnieuw verwerken naar behoren werkt.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media's Image Production System) job. When you run the Dynamic Media Reprocess workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**om Dynamische activa van Media in een omslag opnieuw te verwerken:**

1. In [!DNL Experience Manager], van de pagina van Assets, navigeer aan een activa omslag die een Profiel van het Beeld of een VideoProfiel heeft dat aan het wordt toegewezen en waarvoor u het **Dynamische 2&rbrace; werkschema van Media wilt toepassen Reprocess &lbrace;.**

   Mappen waaraan een afbeeldingsprofiel of videoprofiel is toegewezen, krijgen de naam van het profiel direct onder de mapnaam in de Kaartweergave.

1. Selecteer een map.

   * In de workflow worden alle bestanden in de geselecteerde map recursief bekeken.
   * Als er een of meer submappen met elementen in de geselecteerde hoofdmap staan, worden alle elementen in de maphiërarchie opnieuw verwerkt.
   * U kunt deze workflow het beste niet uitvoeren in een mappenhiërarchie met meer dan 1000 elementen.

1. Selecteer in de vervolgkeuzelijst in de linkerbovenhoek van de pagina de optie **[!UICONTROL Timeline]** .
1. Selecteer rechts naast de linkerbenedenhoek van de pagina, rechts van het veld [!UICONTROL Comment] , het karatpictogram ( **^** ).

   ![ Schermafbeelding van Assets in Experience Manager die een geselecteerde omslag van activa toont, benadrukte de drop-down lijst van de Chronologie, de benadrukte knoop van het Werkschema van het Begin, en het karatpictogram rechts van het gebied van de Commentaar ook ](/help/assets/dynamic-media/assets/reprocess-assets1.png) benadrukte.

1. Selecteer **[!UICONTROL Start Workflow]** .
1. Kies **[!UICONTROL Dynamic Media Reprocess]** in de vervolgkeuzelijst **[!UICONTROL Start Workflow]** .
1. (Facultatief) op **ga titel van werkschemagebied** in, ga een naam voor het werkschema in. U kunt de naam gebruiken om naar de werkstroominstantie te verwijzen, indien nodig.

   ![ Screenshot van het gebruikersinterface van de Chronologie met &quot;Dynamische Media die&quot;van de drop-down lijst van het Werkschema van het Begin wordt geselecteerd, en de knoop van het Begin benadrukte ](/help/assets/dynamic-media/assets/reprocess-assets2.png).

1. Selecteer **[!UICONTROL Start]** en selecteer vervolgens **[!UICONTROL Confirm]** .

   Als u de workflow wilt controleren of de voortgang wilt controleren, selecteert u **[!UICONTROL Tools > Workflow]** op de hoofdconsolepagina van [!DNL Experience Manager] . Selecteer een workflow op de pagina Workflowinstanties. Selecteer **[!UICONTROL Open History]** op de menubalk. U kunt een geselecteerde workflow ook beëindigen, opschorten of de naam ervan wijzigen vanuit dezelfde pagina Workflowinstanties.

### De batchgrootte van de workflow voor opnieuw verwerken aanpassen (optioneel) {#adjusting-load}

(Optioneel) De standaardbatch-grootte in de opwerkingsworkflow is 50 elementen per taak. Deze optimale omvang van de partij wordt bepaald door de gemiddelde omvang van de activa en de MIME-typen van activa waarop het herproces wordt uitgevoerd. Een hogere waarde betekent dat u veel bestanden in één opwerkingstaak hebt. De verwerkingsbanner blijft dus langer op [!DNL Experience Manager] -elementen staan. Als de gemiddelde bestandsgrootte echter klein-1 MB of kleiner is, raadt Adobe u aan de waarde te verhogen tot enkele 100, maar nooit meer dan 1000. Als de gemiddelde bestandsgrootte honderden megabytes is, wordt u aangeraden de batch tot 10 te verkleinen.

**om naar keuze de partijgrootte van het herproceswerkschema aan te passen:**

1. Selecteer in [!DNL Experience Manager] **[!UICONTROL Adobe Experience Manager]** om toegang te krijgen tot de algemene navigatieconsole en selecteer vervolgens het pictogram **[!UICONTROL Tools]** (hamer) > **[!UICONTROL Workflow > Models]** .
1. Selecteer **[!UICONTROL Dynamic Media Reprocess]** op de pagina Workflowmodellen in Kaartweergave of Lijstweergave.

   ![ Schermafbeelding van de pagina van de Modellen van het Werkschema met het &quot;Dynamische Werkschema van Media die&quot;werkschema in de mening van de Kaart van Experience Manager ](/help/assets/dynamic-media/assets/reprocess-assets7.png) wordt geselecteerd.

1. Selecteer **[!UICONTROL Edit]** in de werkbalk. Met een nieuw browsertabblad wordt de modelpagina Dynamisch opnieuw verwerken van media geopend.
1. Selecteer in de rechterbovenhoek van de pagina Dynamische media herverwerken workflow **[!UICONTROL Edit]** om de workflow te &quot;ontgrendelen&quot;.
1. In het werkschema, selecteer de Partij Scene7 uploadt component om de toolbar te openen, dan uitgezocht **[!UICONTROL Configure]** in de toolbar.

   ![ Screenshot van de &quot;Plaats Scene7&quot;component op de &quot;Dynamische pagina van Media Reprocess&quot;met de muiswijzer die over het &quot;Configure&quot;pictogram ](/help/assets/dynamic-media/assets/reprocess-assets8.png) beweegt.

1. Stel in het dialoogvenster **[!UICONTROL Batch Upload to Scene7—Step Properties]** het volgende in:
   * Voer in de tekstvelden **[!UICONTROL Title]** en **[!UICONTROL Description]** desgewenst een nieuwe titel en beschrijving in voor de taak.
   * Selecteer **[!UICONTROL Handler Advance]** als de handler de volgende stap uitvoert.
   * Voer in het veld **[!UICONTROL Timeout]** de time-out van het externe proces (seconden) in.
   * Voer in het veld **[!UICONTROL Period]** een pollinginterval (seconden) in om te testen of het externe proces is voltooid.
   * Voer in de **[!UICONTROL Batch field]** het maximumaantal elementen (50-1000) in dat u wilt verwerken in een uploadtaak voor de batchverwerking van een Dynamic Media-server.
   * Selecteer **[!UICONTROL Advance on timeout]** als u wilt doorgaan wanneer de time-out is bereikt. Schakel deze optie uit als u wilt doorgaan naar het Postvak IN wanneer de time-out is bereikt.

   ![ Schermafbeelding van de &quot;Partij uploadt aan Scene7 - de pagina van de Eigenschappen van de Stap&quot;](/help/assets/dynamic-media/assets/reprocess-assets3.png).

1. Selecteer **[!UICONTROL Done]** in de rechterbovenhoek van het dialoogvenster **[!UICONTROL Batch Upload to Scene7 – Step Properties]** .

1. Selecteer **[!UICONTROL Sync]** in de rechterbovenhoek van de modelpagina Dynamische media opnieuw verwerken. Wanneer u **[!UICONTROL Synced]** ziet, wordt het runtimemodel van de workflow gesynchroniseerd en kunt u elementen in een map opnieuw verwerken.

   ![ Schermafbeelding van Assets in Experience Manager die een geselecteerde omslag van activa toont, benadrukte de drop-down lijst van de Chronologie, de benadrukte knoop van het Werkschema van het Begin, en het karatpictogram rechts van het gebied van de Commentaar ook ](/help/assets/dynamic-media/assets/reprocess-assets1.png) benadrukte.

1. Sluit het browsertabblad waarin het workflowmodel Dynamische media opnieuw verwerken wordt weergegeven.

<!-- MAY BE NEEDED IN THE FUTURE

1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, select **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then select the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/security/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, select **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/security/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, select **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, select **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Dynamic Media Reprocess workflow model.

-->
