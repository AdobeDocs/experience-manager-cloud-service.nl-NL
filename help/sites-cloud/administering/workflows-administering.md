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

Er zijn verschillende consoles beschikbaar voor het beheer van uw workflows. Gebruik de [globale navigatie](/help/sites-cloud/authoring/basic-handling.md#global-navigation) om de **Gereedschappen** selecteert u vervolgens **Workflow**:

* **Modellen**: Workflowdefinities beheren
* **Instanties**: Doorlopende workflowinstanties weergeven en beheren
* **Launchers**: De manier beheren waarop workflows worden gestart
* **Archief**: De geschiedenis van workflows weergeven die zijn voltooid
* **Mislukt**: De geschiedenis weergeven van workflows die zijn voltooid met fouten
* **Automatisch toewijzen**: Workflows automatisch toewijzen aan sjablonen configureren

## Controle van de status van workflowinstanties {#monitoring-the-status-of-workflow-instances}

1. Navigatie selecteren **Gereedschappen** vervolgens **Workflow**.
1. Selecteren **Instanties** om een lijst weer te geven met actieve workflowinstanties die momenteel worden uitgevoerd.
1. Op de bovenste rail, in de rechterhoek, tonen de werkschemainstanties **Workflows uitvoeren**, **Status**, en **Details**.
1. **Workflows uitvoeren** toont het aantal actieve workflows, en hun status. in de gegeven afbeeldingen is de getoonde waarde bijvoorbeeld het aantal **Workflows uitvoeren** en de **Status** van AEM instantie:

   * **Status: gezond**
     ![status-gezond](/help/sites-cloud/administering/assets/status-healthy.png)

   * **Status: Ongezond**
     ![status-ongezond](/help/sites-cloud/administering/assets/status-unhealthy.png)

1. Voor **Statusdetails** van workflowinstanties klikt u op **Details** om de **aantal actieve workflows**, **voltooide workflowinstanties**, **afgebroken workflowinstanties**, **mislukte werkstroominstanties**, enzovoort. hieronder ziet u bijvoorbeeld de afbeeldingen die u ziet **Statusdetails** met:

   * **Statusdetails: gezond**
     ![status-details-gezond](/help/sites-cloud/administering/assets/status-details-healthy.png)

   * **Statusdetails: Ongezond**
     ![status-details-ongezond](/help/sites-cloud/administering/assets/status-details-unhealthy.png)

   >[!NOTE]
   >
   > Om werkstroominstantie gezond te houden, volgt u de aanbevolen procedures op [regelmatige zuivering van workflowinstanties](#regular-purging-of-workflow-instances) of [best practices voor workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-best-practices.html).

## Workflowinstanties zoeken {#search-workflow-instances}

1. Navigatie selecteren **Gereedschappen** vervolgens **Workflow**.
1. Selecteren **Instanties** om een lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd. Selecteer in de bovenste rail in de linkerhoek de optie **Filters**. U kunt ook de toetsaanslagen alt+1 gebruiken. Het volgende dialoogvenster wordt weergegeven:

   ![wf-99-1](/help/sites-cloud/administering/assets/wf-99-1.png)

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

1. Navigatie selecteren **Gereedschappen** vervolgens **Workflow**.
1. Selecteren **Instanties** om een lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd.

   ![wf-96-1](/help/sites-cloud/administering/assets/wf-96-1.png)

1. Selecteer een specifiek item en gebruik **Beëindigen**, **Onderbreken**, of **Hervatten** in voorkomend geval; bevestiging en/of nadere bijzonderheden zijn vereist:

   ![wf-97-1](/help/sites-cloud/administering/assets/wf-97-1.png)

   >[!NOTE]
   >
   >
   >Als u een workflow wilt beëindigen of afbreken, moet deze in een toestand verkeren waarin wordt gewacht op tussenkomst van de gebruiker, zoals in een stap Deelnemer. Als u probeert een workflow af te breken die momenteel taken uitvoert (actieve threads die worden uitgevoerd), krijgt u mogelijk niet de verwachte resultaten.


## Gearchiveerde workflows weergeven {#viewing-archived-workflows}

1. Navigatie selecteren **Gereedschappen** vervolgens **Workflow**.

1. Selecteren **Archief** om een lijst weer te geven met workflowinstanties die met succes zijn voltooid.

   ![archived-instances](/help/sites-cloud/administering/assets/archived-instances.png)

   >[!NOTE]
   >
   >
   >De afbreekstatus wordt beschouwd als een succesvolle beëindiging aangezien het als resultaat van gebruikersactie voorkomt; bijvoorbeeld:
   >
   >* gebruik van de **Beëindigen** action
   >* als een pagina die aan een workflow is onderworpen (geforceerd) wordt verwijderd, wordt de workflow beëindigd.

1. Selecteer vervolgens een specifiek item **Historie openen** voor meer informatie :

   ![wf-99](/help/sites-cloud/administering/assets/wf-99.png)

## Fouten in werkstroominstantie herstellen {#fixing-workflow-instance-failures}

Wanneer een werkstroom mislukt, biedt AEM de **Mislukt** console om u toe te staan om aangewezen actie te onderzoeken en te nemen zodra de originele oorzaak is behandeld:

* **Foutgegevens**
Hiermee opent u een venster waarin de **Foutbericht**, **Stap, en **Stapel mislukt**.

* **Historie openen**
Geeft details van de workflowgeschiedenis weer.

* **Stap opnieuw proberen** Hiermee wordt de componentinstantie Scriptstap opnieuw uitgevoerd. Gebruik de opdracht Stap opnieuw proberen nadat u de oorzaak van de oorspronkelijke fout hebt opgelost. U kunt bijvoorbeeld de stap opnieuw uitvoeren nadat u een fout in het script hebt opgelost dat door de processtap wordt uitgevoerd.
* **Beëindigen** Beëindig de werkstroom als de fout een onherstelbare situatie voor het werkschema heeft veroorzaakt. De workflow kan bijvoorbeeld afhankelijk zijn van omgevingsfactoren, zoals informatie in de opslagplaats die niet langer geldig is voor de werkstroominstantie.
* **Beëindigen en opnieuw proberen** vergelijkbaar met **Beëindigen** behalve dat een nieuwe werkschemainstantie gebruikend de originele lading, de titel, en de beschrijving is begonnen.

Om mislukkingen te onderzoeken, dan hervat of beëindigt het werkschema daarna, gebruik de volgende stappen:

1. Navigatie selecteren **Gereedschappen** vervolgens **Workflow**.

1. Selecteren **Mislukt** om een lijst weer te geven met werkstroominstanties die niet zijn voltooid.
1. Selecteer een specifiek item en voer de gewenste actie uit:

![workflowfout](/help/sites-cloud/administering/assets/workflow-failure.png)

## Regelmatig leegmaken van workflowinstanties {#regular-purging-of-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen.

Configureren **Configuratie van opschonen van de Adobe van Granite-workflow** om werkstroominstanties te wissen op basis van hun leeftijd en status. U kunt ook werkstroominstanties van alle modellen of van een specifiek model wissen.

U kunt ook meerdere configuraties van de service maken om workflowinstanties die aan verschillende criteria voldoen, leeg te maken. Maak bijvoorbeeld een configuratie die de instanties van een bepaald workflowmodel zuivert wanneer deze veel langer dan de verwachte tijd worden uitgevoerd. Maak een andere configuratie die alle voltooide workflows na enkele dagen leegmaakt om de grootte van de opslagplaats te minimaliseren.

Om de dienst te vormen, kunt u de Dossiers van de Configuratie vormen OSGi zie [OSGi-configuratiebestanden](/help/implementing/deploying/configuring-osgi.md). In de volgende tabel worden de eigenschappen beschreven die u voor een van beide methoden nodig hebt.

>[!NOTE]
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>`com.adobe.granite.workflow.purge.Scheduler`
>Omdat de dienst een fabrieksdienst is, de naam van `sling:OsgiConfig` knooppunt vereist een achtervoegsel voor id, bijvoorbeeld:
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
   <td><p>De id van de workflowmodellen die moeten worden gewist. De id is het pad naar het modelknooppunt, bijvoorbeeld:<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Geef geen waarde op om instanties van alle workflowmodellen leeg te maken.</p> <p>Als u meerdere modellen wilt opgeven, klikt u op + in de webconsole. </p> </td>
  </tr>
  <tr>
   <td>Werkstroomleeftijd</td>
   <td>scheduledpurge.daysold</td>
   <td>De leeftijd van de werkstroominstanties die moeten worden gewist, in dagen.</td>
  </tr>
 </tbody>
</table>

## De maximale grootte van het Postvak IN instellen {#setting-the-maximum-size-of-the-inbox}

U kunt de maximumgrootte van inbox plaatsen door te vormen **Adobe Granite Workflow Service**, zie [Voeg een configuratie OSGi aan de bewaarplaats toe](/help/implementing/deploying/configuring-osgi.md). De volgende lijst beschrijft het bezit dat u vormt.

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

De eigenschap *userMetadataPersistenceEnabled* wordt opgeslagen op de *jcr:inhoudsknooppunt* van het workflowmodel. Deze markering wordt in metagegevens van de workflow als *cq:userMetaDataCustomPersistenceEnabled*.

In de onderstaande afbeelding ziet u hoe u de markering op een workflow instelt.

![workflow-externalize-config](/help/sites-cloud/administering/assets/workflow-externalize-config.png)

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
