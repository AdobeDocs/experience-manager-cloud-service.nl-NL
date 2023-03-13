---
title: Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters
description: Leer hoe u de inhoudsfragmenten voor geoptimaliseerde GraphQL-filters in Adobe Experience Manager as a Cloud Service kunt bijwerken voor levering van inhoud zonder kop.
source-git-commit: 44f39df675ff7b3bd40d76e1ebb0e0f17f1e128b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 5%

---


# Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters {#updating-content-fragments-for-optimized-graphql-filtering}

Om de prestaties van uw GraphQL-filters te optimaliseren, moet u een procedure uitvoeren om uw Content Fragments bij te werken.

>[!NOTE]
>
>Nadat u de inhoudsfragmenten hebt bijgewerkt, kunt u de aanbevelingen voor [GraphQL-query&#39;s optimaliseren](/help/headless/graphql-api/graphql-optimization.md).


## Vereisten {#prerequisites}

Zorg ervoor dat u minimaal over de 2023.1.0-release van AEM as a Cloud Service beschikt.

## Inhoudsfragmenten bijwerken {#updating-content-fragments}

Voer de volgende stappen uit om de procedure uit te voeren:

1. Schakel de update in door de volgende variabelen voor uw instantie in te stellen met behulp van de interface van Cloud Manager:

   ![Configuratie van Cloud Manager-omgeving](assets/cfm-graphql-update-01.png "Configuratie van Cloud Manager-omgeving")

   De beschikbare variabelen zijn:

   <table style="table-layout:auto">
    <tbody>
     <tr>
      <th> </th>
      <th>Naam</th>
      <th>Waarde</th>
      <th>Standaardwaarde</th>
      <th>Service</th>
      <th>Toegepast</th>
      <th>Type</th>
      <th>Opmerkingen</th>
     </tr>
     <tr>
      <td>1</td>
      <td>` AEM_RELEASE_CHANNEL` </td>
      <td>"prerelease" </td>
      <td> </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Vereist om de functie in te schakelen. </td>
     </tr>
     <tr>
      <td>2</td>
      <td>"CF_MIGRATION_ENABLED" </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Schakelt in(!=0) of schakelt (0) het activeren van de migratietaak voor inhoudsfragmenten uit. </td>
     </tr>
     <tr>
      <td>3</td>
      <td>"CF_MIGRATION_ENFORCE" </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Afdwingen (!=0) hermigratie van inhoudsfragmenten.<br>Het plaatsen van deze vlag aan 0 zal een stijgende migratie van CFs doen. Dit betekent dat als de taak om welke reden dan ook wordt beëindigd, de volgende taak de migratie start vanaf het punt waar deze is beëindigd. De allereerste migratie wordt aanbevolen (waarde=1). </td>
     </tr>
     <tr>
      <td>4</td>
      <td>"CF_MIGRATION_BATCH" </td>
      <td>`50` </td>
      <td>`50` </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Grootte van de batch voor het opslaan van het aantal inhoudsfragmenten na de migratie.<br>Dit is relevant voor hoeveel CFs aan bewaarplaats in één partij zal worden bewaard, en kan worden gebruikt om aantal te optimaliseren schrijft aan bewaarplaats. </td>
     </tr>
     <tr>
      <td>5</td>
      <td>"CF_MIGRATION_LIMIT" </td>
      <td>`1000` </td>
      <td>`1000` </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Max. aantal te verwerken inhoudsfragmenten.<br>Zie ook nota's voor "CF_MIGRATION_INTERVAL". </td>
     </tr>
     <tr>
      <td>6</td>
      <td>"CF_MIGRATION_INTERVAL" </td>
      <td>`60` </td>
      <td>`600` </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Interval (seconden) om resterende inhoudsfragmenten tot de volgende limiet te verwerken<br>Dit interval wordt ook beschouwd als een wachttijd alvorens de baan, evenals een vertraging tussen verwerking van elk verdere aantal CF_MIGRATION_LIMIT van CFs te beginnen.<br>(*)</td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >(*)
   >
   >De waarde van `CF_MIGRATION_INTERVAL` kan ook helpen de totale uitvoeringstijd van de migratietaak te benaderen.
   >
   >Bijvoorbeeld:
   >
   >* Totaal aantal inhoudsfragmenten = 20.000
   >* CF_MIGRATION_LIMIT = 1000
   >* CF_MIGRATION_INTERNAL = 60 (sec)
   >* Geschatte tijd die nodig is om de migratie te voltooien = 60 + (20,000/1000 * 60) = 1260 sec = 21 minuten
      >  De extra &#39;60&#39; seconden die aan het begin worden toegevoegd, zijn het gevolg van de eerste vertraging bij het starten van de taak.

   >
   >U moet zich er ook van bewust zijn dat dit alleen de *minimum* de tijd die nodig is om de taak uit te voeren, zonder de I/O-tijd. De werkelijke tijd zou aanzienlijk meer kunnen zijn dan deze schatting.

1. De voortgang en voltooiing van de update volgen.

   Hiervoor volgt u de logboeken van auteur en golden-publish van:

   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

      * Auteurslogboeken; bijvoorbeeld:

         ```shell
         23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
         ...
         23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
         
         23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
         ```
   * stammen van stamhout; bijvoorbeeld:

      ```shell
      23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
      
      23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
      ...
      23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
      ```


1. Schakel de updateprocedure uit.

   >[!IMPORTANT]
   >
   >Deze stap wordt vereist om de verbetering te voltooien.

   Nadat de updateprocedure is uitgevoerd, stelt u de omgevingsvariabele van de cloud opnieuw in `CF_MIGRATION_ENABLED` tot &#39;0&#39;, om de recycling van alle pods te starten.

   <table style="table-layout:auto">
    <tbody>
     <tr>
      <th> </th>
      <th>Naam</th>
      <th>Waarde</th>
      <th>Standaardwaarde</th>
      <th>Service</th>
      <th>Toegepast</th>
      <th>Type</th>
      <th>Opmerkingen</th>
     </tr>
     <tr>
      <td></td>
      <td>"CF_MIGRATION_ENABLED" </td>
      <td>`0` </td>
      <td>`0` </td>
      <td>Alles </td>
      <td> </td>
      <td>Variabele </td>
      <td>Disables(0) (or Enables(!=0)) het activeren van de migratietaak voor inhoudsfragmenten. </td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >Dit is met name van belang voor de publicatielijst, aangezien de content-update alleen wordt uitgevoerd op gouden publicaties en bij het recyclen van pods alle normale publicatiepods zijn gebaseerd op de gouden publicatie.

1. Verifieer voltooiing van de updateprocedure.

   U kunt controleren of de update is voltooid met de browser van de gegevensopslagruimte in de ontwikkelingsconsole van Cloud Manager om de fragmentgegevens van de inhoud te controleren.

   * Voor de eerste volledige migratie `cfGlobalVersion` eigenschap bestaat niet.
De aanwezigheid van deze eigenschap op het JCR-knooppunt `/content/dam` met een waarde van `1`bevestigt de voltooiing van de migratie.

   * U kunt ook de volgende eigenschappen controleren op de afzonderlijke inhoudsfragmenten:

      * `_strucVersion` moet de waarde hebben van `1`
      * `indexedData` structuur moet bestaan

      >[!NOTE]
      >
      >De procedure werkt inhoudsfragmenten bij op auteur- en publicatieinstanties.
      >
      >Daarom wordt aanbevolen de verificatie via de browser van de repository uit te voeren voor *ten minste* één auteur *en* één publicatieexemplaar.


## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen:

* Optimalisatie van de prestaties van GraphQL-filters is alleen mogelijk na een volledige update van al uw Content Fragments (aangegeven door de aanwezigheid van de `cfGlobalVersion` eigenschap voor de JCR-node `/content/dam`)

* Als inhoudsfragmenten worden geïmporteerd uit een inhoudspakket (met `crx/de`) nadat de updateprocedure is uitgevoerd, worden die inhoudsfragmenten niet in de resultaten van de GraphQL-query meegenomen totdat de updateprocedure opnieuw wordt uitgevoerd.