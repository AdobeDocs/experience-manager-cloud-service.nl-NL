---
title: Indexeren na migreren van inhoud
description: Leer hoe het migratieproces de opgenomen inhoud op de Cloud Service-instantie van de bestemming zal indexeren.
exl-id: a13d5df4-b351-410a-9336-1b34a8af21b6
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Indexeren na migreren van inhoud {#Indexing-content}

## Indexeren {#aem-indexing-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_indexing"
>title="Indexering van inhoud"
>abstract="AEM Indexering verwijst naar het indexeren van de inhoud op de instantie Cloud Service na het migreren van inhoud naar de instantie. Indexering is vereist om het zoeken naar inhoud voor die instantie te ondersteunen."

Zodra de Cloud Acceleration Manager de inhoud in uw Cloud Service-instantie heeft opgenomen, is deze klaar om te worden gebruikt. In eerste instantie wordt de inhoud niet geïndexeerd, wat waarschijnlijk resulteert in een instabiele omgeving waarin problemen zoals ondoorzoekbare inhoud en verminderde prestaties kunnen worden verwacht. Voor optimale prestaties op de instantie wordt de inhoud automatisch geïndexeerd tijdens het migratieproces. Er hoeft niets te worden gedaan, behalve om de voortgang van de indexering te volgen.

> Voor informatie over hoe te om een opname te beginnen, zie [ Ingesterend Inhoud in Cloud Service ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

De volgende stappen tonen de algemene stroom u in UI tijdens het indexeren kunt verwachten te zien. Sommige labels bieden handige context in knopinfo. Houd de muisaanwijzer boven items om meer te weten te komen over de huidige indexstatus.

Ga eerst naar Cloud Acceleration Manager. Klik op de projectkaart en klik vervolgens op de kaart voor inhoudsoverdracht. Navigeer aan **IngestieBanen** en zie de vermelde banen.

>[!NOTE]
>U kunt de indexerende logboeken bekijken of downloaden door de acties van de innametaak te gebruiken, gebruikend.. drop-down lijst. De logbestanden zijn beschikbaar in het
> &#39;Indexering logbestand&#39;-actiesectie, nadat de indexeertaak is voltooid

### In behandeling

Dit is hoe de rij van de opnametaak zal verschijnen wanneer de opname loopt, alvorens de indexerende baan is begonnen. Er is geen actie vereist van de gebruiker. Als de opname om welke reden dan ook mislukt, wordt het in de wachtrij plaatsen van de indextaak geannuleerd en niet gestart.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-indexing/pending.png)

### Wordt uitgevoerd

Wanneer de opname slaagt, wordt de indexerende baan in werking gesteld automatisch. De rij van de innametaak zal een vooruitgangspictogram voor de AEM indexerende status tonen. U kunt het dialoogvenster Duur openen om de voortgang van de taak te bekijken.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-indexing/running.png)

### Voltooid

Wanneer de indexeertaak succesvol is, is de instantie gereed om te worden gebruikt voor optimale prestaties. Op dit punt zijn de indexerende baanlogboeken beschikbaar om hen te bekijken of te downloaden te inspecteren.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-indexing/complete.png)

### Fouten

Het indexeren van de instantie van de bestemmings Cloud Service zal zeer waarschijnlijk slagen. In sommige gevallen kan dit mislukken en wordt de rij met ingevulde taken als volgt weergegeven. In alle gevallen, kunt u sommige details van de mislukking ontdekken door over de mislukkingsstatus te hangen, en het kan meer informatie verstrekken om u te helpen volgende stappen bepalen. Op dit punt, zijn de indexerende baanlogboeken beschikbaar aan mening of download helpen de bron van de mislukking ontdekken. Als de volgende stap niet duidelijk is, contacteer de Steun van de Adobe met details van de opname en het indexerende logboek.

>[!TIP]
>
> Als de het indexeren baan te lang schijnt te lopen, zorg ervoor dat een [ IP Lijst van gewenste personen niet ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) door Cloud Manager is toegepast aangezien het Cloud Acceleration Manager van het bereiken van de migratiedienst verhindert.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-indexing/failed.png)

## Volgende functies {#whats-next}

Zodra de de dienstinstantie van de bestemmingswolk is geïndexeerd, kunt u logboeken van de indexerende banen bekijken en details en fouten zoeken.

De migratie is voltooid. Het testen en valideren van de bestemmingscloudservice-instantie kan beginnen.
