---
title: Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters
description: Leer hoe u de inhoudsfragmenten voor geoptimaliseerde GraphQL-filters in Adobe Experience Manager as a Cloud Service kunt bijwerken voor levering van inhoud zonder kop.
exl-id: 211f079e-d129-4905-a56a-4fddc11551cc
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 8d14936ad21dc5879c72383defc3db22ce9a24ef
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters {#updating-content-fragments-for-optimized-graphql-filtering}

Als u de prestaties van uw GraphQL-filters wilt optimaliseren, voert u een procedure uit om uw Content Fragments bij te werken.

>[!NOTE]
>
>Na het bijwerken van uw Fragmenten van de Inhoud, kunt u de aanbevelingen voor [ volgen het Optimaliseren van de Vragen van GraphQL ](/help/headless/graphql-api/graphql-optimization.md).


## Vereisten {#prerequisites}

Er zijn voorwaarden voor deze taak:

1. Zorg ervoor dat u minimaal over de 2023.1.0-release van AEM as a Cloud Service beschikt.

1. Zorg ervoor dat de gebruiker die de taak uitvoert de vereiste toestemmingen heeft:

   * minimaal is de `Deployment Manager` rol in Cloud Manager vereist.

## Inhoudsfragmenten bijwerken {#updating-content-fragments}

1. Schakel de update in door de volgende variabelen voor uw instantie in te stellen met behulp van de gebruikersinterface van Cloud Manager:

   ![ de Configuratie van het Milieu van Cloud Manager ](assets/cfm-graphql-update-01.png " de Configuratie van het Milieu van Cloud Manager ")

   De beschikbare variabelen zijn:

   | | Naam | Waarde | Standaardwaarde | Service | Toegepast | Type | Notities |
   |---|---|---|---|---|---|---|---|
   | 1 | `CF_MIGRATION_ENABLED` | `1` | `0` | Alles | | Variabele | Schakelt in(!=0) of schakelt (0) het activeren van de migratietaak voor inhoudsfragmenten uit. |
   | 2 | `CF_MIGRATION_ENFORCE` | `1` | `0` | Alles | | Variabele | Afdwingen (!=0) hermigratie van inhoudsfragmenten. Als u deze markering instelt op 0, wordt er een incrementele migratie van CF&#39;s uitgevoerd. Dit betekent dat als de taak om welke reden dan ook wordt beëindigd, de volgende uitvoering van de taak de migratie start vanaf het punt waar deze is beëindigd. De eerste migratie wordt aanbevolen voor handhaving (waarde=1). |
   | 3 | `CF_MIGRATION_BATCH` | `50` | `50` | Alles | | Variabele | Grootte van de batch voor het opslaan van het aantal inhoudsfragmenten na de migratie. Dit is relevant voor hoeveel CFs aan de bewaarplaats in één partij wordt bewaard, en kan worden gebruikt om het aantal te optimaliseren schrijft aan de bewaarplaats. |
   | 4 | `CF_MIGRATION_LIMIT` | `1000` | `1000` | Alles | | Variabele | Max. aantal te verwerken inhoudsfragmenten. Zie ook notities voor `CF_MIGRATION_INTERVAL` . |
   | 5 | `CF_MIGRATION_INTERVAL` | `60` | `600` | Alles | | Variabele | Interval (seconden) om de resterende inhoudsfragmenten tot de volgende limiet te verwerken. Dit interval wordt ook beschouwd als zowel een wachttijd alvorens de baan te beginnen, als een vertraging tussen verwerking van elk verdere aantal CF_MIGRATION_LIMIT van CFs. (*) |

   >[!NOTE]
   >
   >(*)
   >
   >De waarde van `CF_MIGRATION_INTERVAL` kan ook helpen om de totale uitvoeringstijd van de migratietaak te benaderen.
   >
   >Bijvoorbeeld:
   >
   >* Totaal aantal inhoudsfragmenten = 20.000
   >* CF_MIGRATION_LIMIT = 1000
   >* CF_MIGRATION_INTERNAL = 60 (sec)
   >* Geschatte tijd die nodig is om de migratie te voltooien = 60 + (20,000/1000 * 60) = 1260 sec = 21 minuten
   >  De extra &#39;60&#39; seconden die aan het begin worden toegevoegd, zijn het gevolg van de eerste vertraging bij het starten van de taak.
   >
   >Dit is slechts de *minimum* tijd die wordt vereist om de baan te voltooien, en omvat niet de I/O tijd. De werkelijke tijd zou meer kunnen zijn dan deze schatting.

1. De voortgang en voltooiing van de update volgen.

   Hiervoor volgt u de logboeken van auteur en golden-publish van:

   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

      * Auteurslogboeken, bijvoorbeeld:

        ```shell
        23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
        ...
        23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
        
        23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
        ```

      * Logboeken met gouden publicatie, bijvoorbeeld:

        ```shell
        23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
        
        23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
        ...
        23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
        ```

   De klanten, die toegang tot de milieulogboeken gebruikend Splunk toeliet, kunnen de voorbeeldvraag hieronder gebruiken om het verbeteringsproces te controleren. Voor details over het toelaten van het registreren van het Splunk, zie [ het Zuiveren Productie en Stadium ](/help/implementing/developing/introduction/logging.md#debugging-production-and-stage).

   ```splunk
   index=<indexName> sourcetype=aemerror aem_envId=<environmentId> msg="*com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished*" 
   (aem_tier=golden-publish OR aem_tier=author) | table _time aem_tier pod_name msg | sort -_time desc
   ```

   Waarbij:

   * `environmentId` - een id voor de omgeving van de klant, bijvoorbeeld `e1234`
   * `indexName` - een naam voor een index van een klant, waarin `aemerror` -gebeurtenissen worden verzameld

   Voorbeeld-uitvoer:

   <table style="table-layout:auto">
     <thead>
       <tr>
       <th>_time</th>
       <th>aem_tier</th>
       <th>pod_name</th>
       <th>msg</th>
       </tr>
     </thead> 
     <tbody>
       <tr>
         <td>2023-04-21 06 :00: 35.723</td>
         <td>auteur</td>
         <td>cm-p1234-e1234-aem-auteur-76d6dc4b79-8lsb5</td>
         <td>[sling-threadpool-bb5da4dd-6b05-4230-93ea-1d5cd242e24f-(apache-sling-baan-draad-pool)-1-Inhoud Config van de Rij van de Rij van de Verbetering van het Fragment (cfm/upgrader)] com.adobe.cq.dam.impl.upgrade.UpgradeJob Voltooide content fragments upgrade in 391m, slingJobId: 2023/4/20/23/16/db7963df-e267-489b-b69a-5930b0dadb37_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade aan versie '1' is uitgevoerd.', errors=[], successCount=36756, failedCount=0, skippedCount=0}</td>
       </tr>
       <tr>
         <td>2023-04-21 06 :05: 48.207</td>
         <td>gouden publicatie</td>
         <td>cm-p1234-e1234-aem-golden-publish-644487c9c5-lvkv2</td>
         <td>[sling-threadpool-284b9a-8454-461e-9bdb-44866c6ddfb1-(apache-sling-baan-draad-pool)-1-Inhoud Config van de Rij van de Rij van de Verbetering van het Fragment (cfm/upgrader)] com.adobe.cq.dam.cfm.impl.impl.impl upgrade.UpgradeJob Voltooide content fragments upgrade in 211m, slingJobId: 2023/4/20/23/15/66c1690a-cdb7-4e66-bc52-90f3394ddfc_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade aan versie '1' is uitgevoerd.', errors=[], successCount=19557, failedCount=0, skippedCount=0}</td>
       </tr>
     </tbody>
   <table>

1. Schakel de updateprocedure uit.

   >[!IMPORTANT]
   >
   >Deze stap is vereist om de verbetering te voltooien.

   Nadat de updateprocedure is uitgevoerd, stelt u de omgevingsvariabele voor de cloud `CF_MIGRATION_ENABLED` in op &#39;0&#39; om de recycling van alle pods te activeren.

   | | Naam | Waarde | Standaardwaarde | Service | Toegepast | Type | Notities |
   |---|---|---|---|---|---|---|---|
   | | `CF_MIGRATION_ENABLED` | `0` | `0` | Alles | | Variabele | Disables(0) (or Enables(!=0)) het activeren van de migratietaak voor inhoudsfragmenten. |

   >[!NOTE]
   >
   >Dit is belangrijk voor het publicatieniveau, aangezien de content-update alleen wordt uitgevoerd op gouden publicaties en bij het recyclen van pods alle normale publicatiepods zijn gebaseerd op de gouden publicatie.

1. Verifieer voltooiing van de updateprocedure.

   U kunt controleren of de update is voltooid met de browser van de repository in de Cloud Manager Developer Console om de fragmentgegevens van de inhoud te controleren.

   * Vóór de eerste volledige migratie bestaat de eigenschap `cfGlobalVersion` niet.
Daarom bevestigt de aanwezigheid van deze eigenschap, op het JCR-knooppunt `/content/dam` met de waarde `1` , de voltooiing van de migratie.

   * U kunt ook de volgende eigenschappen controleren op de afzonderlijke inhoudsfragmenten:

      * `_strucVersion` moet de waarde `1` hebben
      * `indexedData` -structuur moet bestaan

     >[!NOTE]
     >
     >De procedure werkt Inhoudsfragmenten op instanties van Auteur en van Publish bij.
     >
     >Daarom adviseert de Adobe dat u de controle als bewaargegevensbrowser voor *minstens* één Auteur *en* één instantie van Publish uitvoert.

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen:

* Optimalisatie van de prestaties van GraphQL-filters is alleen mogelijk na een volledige update van al uw Content Fragments (aangegeven door de eigenschap `cfGlobalVersion` voor het JCR-knooppunt `/content/dam` )

* Als Inhoudsfragmenten uit een inhoudspakket worden geïmporteerd (met `crx/de` ) nadat de updateprocedure is uitgevoerd, worden deze Inhoudsfragmenten pas in de resultaten van de GraphQL-query meegenomen als de updateprocedure opnieuw wordt uitgevoerd.
