---
title: Workflowinstanties beheren
description: Leer hoe u workflowinstanties beheert met de workflowconsole
feature: Administering
role: Admin
exl-id: d2adb5e8-3f0e-4a3b-b7d0-dbbc5450e45f
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 0%

---

# Workflowinstanties beheren {#administering-workflow-instances}

De workflowconsole biedt verschillende gereedschappen voor het beheer van workflowinstanties om ervoor te zorgen dat deze naar behoren worden uitgevoerd.

Er zijn verschillende consoles beschikbaar voor het beheer van uw workflows. Gebruik de [ globale navigatie ](/help/sites-cloud/authoring/basic-handling.md#global-navigation) om de **ruit van Hulpmiddelen** te openen, dan uitgezocht **Werkschema**:

* **Modellen**: Beheer werkschemadefinities
* **Instanties**: De mening en beheert het runnen werkschemainstanties
* **Lanceerprogramma&#39;s**: Beheer hoe de werkschema&#39;s moeten worden gelanceerd
* **Archief**: De geschiedenis van de mening van werkschema&#39;s die met succes voltooiden
* **Mislukt**: De geschiedenis van de mening van werkschema&#39;s die met fouten voltooiden
* **auto-wijst** toe: Vorm auto-Wijs werkschema&#39;s aan malplaatjes toe

## Controle van de status van workflowinstanties {#monitoring-the-status-of-workflow-instances}

1. Gebruikend de uitgezochte Navigatie **Hulpmiddelen**, toen **Werkschema**.
1. Selecteer **Instanties** om de lijst van lopende werkschemainstanties momenteel te tonen.
1. Op het hoogste spoor, in de juiste hoek, tonen de werkschemainstanties **Lopende werkschema&#39;s**, **Status**, en **Details**.
1. **Lopende werkschema&#39;s** toont het aantal lopende werkschema&#39;s, en hun status. bijvoorbeeld, in de bepaalde getoonde beelden, zijn het aantal **Lopende werkschema&#39;s** en de **Status** van AEM instantie:

   * **Status: Gezonde**
     ![ status-gezond ](/help/sites-cloud/administering/assets/status-healthy.png)

   * **Status: Ongezond**
     ![ status-ongezond ](/help/sites-cloud/administering/assets/status-unhealthy.png)

1. Voor **de details van de Status** van werkschemainstanties, klik **Details**, om het **aantal lopende werkstroominstanties**, **voltooide werkschemainstanties**, **geaborteerde werkschemainstanties**, **ontbroken werkschemainstanties** te tonen, etc. bijvoorbeeld, hieronder zijn de bepaalde beelden die **details van de Status** met tonen:

   * **de details van de Status: Gezonde**
     ![ status-details-gezond ](/help/sites-cloud/administering/assets/status-details-healthy.png)

   * **de details van de Status: Ongezond**
     ![ status-details-ongezond ](/help/sites-cloud/administering/assets/status-details-unhealthy.png)

   >[!NOTE]
   >
   > Om werkschemainstantie gezond te handhaven, volg beste praktijken bij [ regelmatig het zuiveren van werkschemainstanties ](#regular-purging-of-workflow-instances) of [ werkschemabeste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-best-practices.html).

## Workflowinstanties zoeken {#search-workflow-instances}

1. Gebruikend de uitgezochte Navigatie **Hulpmiddelen**, toen **Werkschema**.
1. Selecteer **Instanties** om de lijst van werkschemainstanties te tonen momenteel lopend. Op het hoogste spoor, in de linkerhoek, uitgezochte **Filters**. U kunt ook de toetsaanslagen alt+1 gebruiken. Het volgende dialoogvenster wordt weergegeven:

   ![ wf-99-1 ](/help/sites-cloud/administering/assets/wf-99-1.png)

1. Selecteer de zoekcriteria voor de workflow in het dialoogvenster Filter. U kunt zoeken op basis van de volgende gegevens:

   * Payloadpad: een specifiek pad selecteren
   * Workflowmodel: een workflowmodel selecteren
   * Aangewezen persoon: Selecteer een werkstroomontvanger
   * Type: taak, workflowitem of workflowfout
   * Taakstatus: actief, voltooid of beëindigd
   * Waar ik ben: Eigenaar en ontvanger, alleen eigenaar, alleen gevolmachtigde
   * Begindatum: Begindatum voor of na een opgegeven datum
   * Einddatum: Einddatum vóór of na een opgegeven datum
   * Vervaldatum: Vervaldatum voor of na een bepaalde datum
   * Bijgewerkte datum: Bijgewerkte datum voor of na een opgegeven datum

## Het onderbreken, Hervatten, en het Eindigen van een Instantie van het Werkschema {#suspending-resuming-and-terminating-a-workflow-instance}

1. Gebruikend de uitgezochte Navigatie **Hulpmiddelen**, toen **Werkschema**.
1. Selecteer **Instanties** om de lijst van werkschemainstanties te tonen momenteel lopend.

   ![ wf-96-1 ](/help/sites-cloud/administering/assets/wf-96-1.png)

1. Selecteer een specifiek punt, dan gebruik **beëindigt**, **Schorsing**, of **hervat**, zoals aangewezen; bevestiging, en/of verdere details worden vereist:

   ![ wf-97-1 ](/help/sites-cloud/administering/assets/wf-97-1.png)

   >[!NOTE]
   >
   >
   >Als u een workflow wilt beëindigen of afbreken, moet deze in een toestand verkeren waarin wordt gewacht op tussenkomst van de gebruiker, zoals in een stap Deelnemer. Als u probeert een workflow af te breken die momenteel taken uitvoert (actieve threads die worden uitgevoerd), krijgt u mogelijk niet de verwachte resultaten.


## Gearchiveerde workflows weergeven {#viewing-archived-workflows}

1. Gebruikend de uitgezochte Navigatie **Hulpmiddelen**, toen **Werkschema**.

1. Selecteer **Archief** om de lijst van werkschemainstanties te tonen die met succes voltooiden.

   ![ archived-instances ](/help/sites-cloud/administering/assets/archived-instances.png)

   >[!NOTE]
   >
   >
   >De afbreekstatus wordt beschouwd als een succesvolle beëindiging aangezien het als resultaat van gebruikersactie voorkomt; bijvoorbeeld:
   >
   >* gebruik van **beëindigt** actie
   >* als een pagina die aan een workflow is onderworpen (geforceerd) wordt verwijderd, wordt de workflow beëindigd.

1. Selecteer een specifiek punt, dan **Open Geschiedenis** om meer details te zien:

   ![ wf-99 ](/help/sites-cloud/administering/assets/wf-99.png)

## Fouten in werkstroominstantie herstellen {#fixing-workflow-instance-failures}

Wanneer een werkschema ontbreekt, AEM verstrekt de **console van Mislukt** om u toe te staan om aangewezen actie te onderzoeken en te nemen zodra de originele oorzaak is behandeld:

* **Details van de Mislukking**
Opent een venster om het **Bericht van de Mislukking**, **Stap, en **Stapel van de Mislukking** te tonen.

* **Open Geschiedenis**
Geeft details van de workflowgeschiedenis weer.

* **herprobeer Stap** voert opnieuw de de componenteninstantie van de Stap van het Manuscript uit. Gebruik de opdracht Stap opnieuw proberen nadat u de oorzaak van de oorspronkelijke fout hebt opgelost. U kunt bijvoorbeeld de stap opnieuw uitvoeren nadat u een fout in het script hebt opgelost dat door de processtap wordt uitgevoerd.
* **eindigt** het werkschema als de fout een onherstelbare situatie voor het werkschema heeft veroorzaakt. De workflow kan bijvoorbeeld afhankelijk zijn van omgevingsfactoren, zoals informatie in de opslagplaats die niet langer geldig is voor de werkstroominstantie.
* **beëindigt en probeert opnieuw** gelijkend op **eindigt** behalve dat is een nieuwe werkschemainstantie begonnen gebruikend de originele nuttige lading, de titel, en de beschrijving.

Om mislukkingen te onderzoeken, dan hervat of beëindigt het werkschema daarna, gebruik de volgende stappen:

1. Gebruikend de uitgezochte Navigatie **Hulpmiddelen**, toen **Werkschema**.

1. Selecteer **Mislukt** om de lijst van werkschemainstanties te tonen die niet met succes voltooiden.
1. Selecteer een specifiek item en voer de gewenste actie uit:

![ werkschema-mislukking ](/help/sites-cloud/administering/assets/workflow-failure.png)

## Regelmatig leegmaken van workflowinstanties {#regular-purging-of-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen.

Vorm **de Configuratie van de Wrijving van het Werkschema van 0} Adobe granite om werkschemainstanties volgens hun leeftijd en status te zuiveren.** U kunt ook werkstroominstanties van alle modellen of van een specifiek model wissen.

U kunt ook meerdere configuraties van de service maken om workflowinstanties die aan verschillende criteria voldoen, leeg te maken. Maak bijvoorbeeld een configuratie die de instanties van een bepaald workflowmodel zuivert wanneer deze veel langer dan de verwachte tijd worden uitgevoerd. Maak een andere configuratie die alle voltooide workflows na enkele dagen leegmaakt om de grootte van de opslagplaats te minimaliseren.

Om de dienst te vormen, kunt u de OSGi- Dossiers van de Configuratie vormen zie [ OSGi configuratiedossiers ](/help/implementing/deploying/configuring-osgi.md). In de volgende tabel worden de eigenschappen beschreven die u voor een van beide methoden nodig hebt.

>[!NOTE]
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>`com.adobe.granite.workflow.purge.Scheduler`
>Omdat de service een fabrieksservice is, vereist de naam van het knooppunt `sling:OsgiConfig` een achtervoegsel met id, bijvoorbeeld:
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table>
 <tbody>
  <tr>
   <th>Naam eigenschap (webconsole)</th>
   <th>OSGi Eigenschapnaam</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Taaknaam</td>
   <td>scheduledpurge.name</td>
   <td>Een beschrijvende naam voor de geplande leegloop.</td>
  </tr>
  <tr>
   <td>Workflowstatus</td>
   <td>scheduledpurge.workflowStatus</td>
   <td><p>De status van de te wissen werkstroominstanties. De volgende waarden zijn geldig:</p>
    <ul>
     <li>VOLTOOID: instanties van voltooide werkstromen worden gewist.</li>
     <li>UITVOEREN: instanties van actieve werkstromen worden gewist.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Te wissen modellen</td>
   <td>scheduledpurge.modelIds</td>
   <td><p>De id van de workflowmodellen die moeten worden gewist. Identiteitskaart is de weg aan de modelknoop, bijvoorbeeld:<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model <br /> specificeer geen waarde om instanties van alle werkschemamodellen te zuiveren.</p> <p>Als u meerdere modellen wilt opgeven, klikt u op + in de webconsole. </p> </td>
  </tr>
  <tr>
   <td>Werkstroomleeftijd</td>
   <td>scheduledpurge.daysold</td>
   <td>De leeftijd van de werkstroominstanties die moeten worden gewist, in dagen.</td>
  </tr>
 </tbody>
</table>

## De maximale grootte van het Postvak IN instellen {#setting-the-maximum-size-of-the-inbox}

U kunt de maximumgrootte van inbox plaatsen door de **Dienst van het Werkschema van de Adobe te vormen Granite**, zie [ een configuratie OSGi aan de bewaarplaats ](/help/implementing/deploying/configuring-osgi.md) toevoegen. De volgende lijst beschrijft het bezit dat u vormt.

>[!NOTE]
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Naam eigenschap (webconsole) | OSGi Eigenschapnaam |
|---|---|
| Max. grootte van invoerquery | granite.workflow.inboxQuerySize |

## Workflowvariabelen gebruiken voor datastores die eigendom zijn van klanten {#using-workflow-variables-customer-datastore}

Gegevens die door workflows worden verwerkt, worden opgeslagen in de Adobe opgegeven opslagruimte (JCR). Deze gegevens kunnen van nature gevoelig zijn. U kunt alle door de gebruiker gedefinieerde metagegevens of gegevens in uw eigen beheerde opslagruimte opslaan in plaats van de door de Adobe verschafte opslagruimte. In deze secties wordt beschreven hoe u deze variabelen instelt voor externe opslag.

### Het model instellen voor externe opslag van metagegevens {#set-model-for-external-storage}

Op het niveau van het workflowmodel wordt een markering opgegeven die aangeeft dat het model (en de runtimeinstanties) externe opslag van metagegevens heeft. Workflowvariabelen blijven niet behouden in JCR voor de workflowinstanties van de modellen die zijn gemarkeerd voor externe opslag.

Het bezit *userMetadataPersistenceEnabled* wordt opgeslagen op *jcr:inhoudsknoop* van het werkschemamodel. Deze vlag wordt voortgeduurd in werkschemagegevens als *cq:userMetaDataCustomPersistenceEnabled*.

In de onderstaande afbeelding ziet u hoe u de markering op een workflow instelt.

![ werkschema-externalize-config ](/help/sites-cloud/administering/assets/workflow-externalize-config.png)

### API&#39;s voor metagegevens in externe opslag {#apis-for-metadata-external-storage}

Als u de variabelen extern wilt opslaan, moet u de API&#39;s implementeren die in de workflow beschikbaar worden gesteld.

UserMetaDataPersistenceContext

In de volgende voorbeelden ziet u hoe u de API gebruikt.

```
@ProviderType
public interface UserMetaDataPersistenceContext {
 
    /**
     * Gets the workflow for persistence
     * @return workflow
     */
    Workflow getWorkflow();
 
    /**
     * Gets the workflow id for persistence
     * @return workflowId
     */
    String getWorkflowId();
 
    /**
     * Gets the user metadata persistence id
     * @return userDataId
     */
    String getUserDataId();
}
```

UserMetaDataPersistenceProvider

```
/**
 * This provider can be implemented to store the user defined workflow-data metadata in a custom storage location
 */
@ConsumerType
public interface UserMetaDataPersistenceProvider {
 
   /**
    * Retrieves the metadata using a unique identifier
    * @param userMetaDataPersistenceContext
    * @param metaDataMap of user defined workflow data metaData
    * @throws WorkflowException
    */
   void get(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
   /**
    * Stores the given metadata to the custom storage location
    * @param userMetaDataPersistenceContext
    * @param metaDataMap metadata map
    * @return the unique identifier that can be used to retrieve metadata. If null is returned, then workflowId is used.
    * @throws WorkflowException
    */
   String put(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
} 
```
