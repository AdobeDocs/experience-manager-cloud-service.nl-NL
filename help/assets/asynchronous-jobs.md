---
title: Asynchrone bewerkingen
description: AEM Assets optimaliseert prestaties door sommige middel-intensieve taken asynchroon te voltooien.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Asynchrone bewerkingen {#asynchronous-operations}

Om negatieve gevolgen voor de prestaties te beperken, verwerkt Adobe Experience Manager (AEM)-middelen bepaalde langlopende en hulpbronnenintensieve middelenbewerkingen asynchroon.

Deze bewerkingen omvatten:

* Veel elementen verwijderen
* Veel elementen of elementen met veel verwijzingen verplaatsen
* Metagegevens van elementen bulksgewijs exporteren/importeren.
* Het opvangen van activa, die boven de vastgestelde drempelgrens zijn, van een verre plaatsing AEM.

Asynchrone verwerking omvat het onderzoeken van veelvoudige banen en uiteindelijk het leiden van hen op een periodieke manier afhankelijk van de beschikbaarheid van systeemmiddelen.

U kunt de status van asynchrone taken weergeven op de pagina **[!UICONTROL Taakstatus]** synchroniseren.

>[!NOTE]
>
>Standaard worden taken in AEM Assets parallel uitgevoerd. Als N het aantal CPU-cores is, kunnen N/2-taken standaard parallel worden uitgevoerd. Als u aangepaste instellingen voor de taakwachtrij wilt gebruiken, wijzigt u de configuratie van de standaardwachtrij voor **Async-bewerkingen** in de webconsole. Voor meer informatie, zie de Configuraties van de [Rij](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## De status van asynchrone bewerkingen controleren {#monitoring-the-status-of-asynchronous-operations}

Wanneer AEM Assets een verrichting asynchroon verwerkt, ontvangt u een bericht bij uw inbox <!-- and through email -->.

Als u de status van de asynchrone bewerkingen in detail wilt weergeven, navigeert u naar de pagina **[!UICONTROL Taakstatus]** synchroniseren.

1. Tap/click the AEM logo, and go **[!UICONTROL Assets]** > **[!UICONTROL Jobs]**.
1. Controleer de details van de bewerkingen op de pagina Taakstatus **** synchroniseren.

   ![job_status](assets/job_status.png)

   Zie de waarde in de kolom **[!UICONTROL Status]** om de voortgang van een bepaalde bewerking te controleren. Afhankelijk van de voortgang wordt een van de volgende statussen weergegeven:

   **[!UICONTROL Actief]**: De bewerking wordt verwerkt

   **[!UICONTROL Geslaagd]**: De bewerking is voltooid

   **[!UICONTROL Mislukt]** of **[!UICONTROL fout]**: De bewerking kan niet worden verwerkt

   **[!UICONTROL Gepland]**: De bewerking is gepland voor verwerking op een later tijdstip

1. Als u een actieve bewerking wilt stoppen, selecteert u deze in de lijst en tikt u op het pictogram **[!UICONTROL Stoppen]** of klikt u op de werkbalk.

   ![stop_icon](assets/stop_icon.png)

1. Als u extra details wilt weergeven, bijvoorbeeld beschrijving en logbestanden, selecteert u de bewerking en tikt u op het pictogram **[!UICONTROL Openen]** op de werkbalk.

   ![open_icon](assets/open_icon.png)

   De pagina met taakdetails wordt weergegeven.

   ![job_details](assets/job_details.png)

1. Als u de bewerking uit de lijst wilt verwijderen, selecteert u **[!UICONTROL Verwijderen]** op de werkbalk. Tik op het pictogram **[!UICONTROL Downloaden]** om de details in een CSV-bestand te downloaden.

   >[!NOTE]
   >
   >U kunt een taak niet verwijderen als de status actief is of in de wachtrij staat.

## Voltooide taken leegmaken {#purging-completed-jobs}

AEM Assets stelt elke dag om 1:00 in werking om voltooide asynchrone banen te schrappen die meer dan een dag oud zijn.

U kunt het schema voor de zuiveringstaak en de duur wijzigen waarvoor de details van voltooide banen worden behouden alvorens zij worden geschrapt. U kunt ook het maximumaantal voltooide taken configureren waarvoor de details op elk gewenst moment behouden blijven.

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]** -taak.
1. Vermeld het drempelaantal dagen waarna voltooide taken worden verwijderd en het maximumaantal banen waarvoor gegevens in de geschiedenis worden bewaard.

   ![Configuratie om het leegmaken van asynchrone taken te plannen](assets/configmgr_purge_asyncjobs.png)
   *Afbeelding: Configuratie om het leegmaken van asynchrone taken te plannen*

1. Sla de wijzigingen op.

## Drempels configureren voor asynchrone verwerking {#configuring-thresholds-for-asynchronous-processing}

U kunt het drempelaantal elementen of verwijzingen voor AEM-elementen zodanig configureren dat een bepaalde bewerking asynchroon wordt verwerkt.

### Drempels configureren voor asynchrone verwijderingsbewerkingen {#configuring-thresholds-for-asynchronous-delete-operations}

Als het aantal te verwijderen elementen of mappen de drempelwaarde overschrijdt, wordt de verwijderbewerking asynchroon uitgevoerd.

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async-configuratie Taakverwerking]** verwijderen.
1. Geef in het vak **[!UICONTROL Drempelwaarde voor het aantal elementen]** het drempelaantal elementen/mappen voor asynchrone verwerking van verwijderingsbewerkingen op.

   ![delete_threshold](assets/delete_threshold.png)

1. Sla de wijzigingen op.

### Drempels voor asynchrone verplaatsingsbewerkingen configureren {#configuring-thresholds-for-asynchronous-move-operations}

Als het aantal te verplaatsen elementen/mappen of verwijzingen het drempelnummer overschrijdt, wordt de verplaatsingsbewerking asynchroon uitgevoerd.

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async-configuratie Taakverwerking]** verplaatsen.
1. Geef in het vak **[!UICONTROL Drempelwaarde aantal elementen/referenties]** het drempelaantal elementen/mappen of verwijzingen voor asynchrone verwerking van verplaatsingsbewerkingen op.

   ![move_threshold](assets/move_threshold.png)

1. Sla de wijzigingen op.
