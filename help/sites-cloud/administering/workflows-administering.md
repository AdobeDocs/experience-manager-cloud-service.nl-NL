---
title: Workflowinstanties beheren
description: Leer hoe u workflowinstanties beheert
translation-type: tm+mt
source-git-commit: c19079b1be36c4e87962491f263ddf97ab98f831
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 0%

---


# Workflowinstanties beheren {#administering-workflow-instances}

De workflowconsole biedt verschillende gereedschappen voor het beheer van workflowinstanties om ervoor te zorgen dat deze naar behoren worden uitgevoerd.

Er zijn verschillende consoles beschikbaar voor het beheer van uw workflows. Gebruik [globale navigatie](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) om **Hulpmiddelen** ruit te openen, dan uitgezocht **Workflow**:

* **Modellen**: Workflowdefinities beheren
* **Instanties**: Doorlopende workflowinstanties weergeven en beheren
* **Launchers**: De manier beheren waarop workflows worden gestart
* **Archief**: De geschiedenis weergeven van workflows die zijn voltooid
* **Mislukt**: De geschiedenis weergeven van workflows die zijn voltooid met fouten
* **Automatisch toewijzen**: Workflows automatisch toewijzen aan sjablonen configureren

## De status van workflowinstanties controleren {#monitoring-the-status-of-workflow-instances}

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Instanties** om de lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd.

   ![wf-97](/help/sites-cloud/administering/assets/wf-97.png)


## Workflowinstanties doorzoeken {#search-workflow-instances}

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Instanties** om de lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd. Selecteer **Filters** in de bovenste track in de linkerhoek. U kunt ook de toetsaanslagen alt+1 gebruiken. Het volgende dialoogvenster wordt weergegeven:

   ![wf-99-1](/help/sites-cloud/administering/assets/wf-99-1.png)

1. Selecteer de zoekcriteria voor de workflow in het dialoogvenster Filter. U kunt zoeken op basis van de volgende gegevens:

   * Payloadpad: Een specifiek pad selecteren
   * Workflowmodel: Een workflowmodel selecteren
   * Geadresseerde: Een werkstroomontvanger selecteren
   * Type: Taak, workflowitem of workflowfout
   * Taakstatus: Actief, volledig of beëindigd
   * Waar ik ben: Eigenaar EN gemachtigde, alleen eigenaar, alleen gevolmachtigde
   * Begindatum: Begindatum voor of na een opgegeven datum
   * Einddatum: Einddatum voor of na een opgegeven datum
   * Vervaldatum: Vervaldatum voor of na een bepaalde datum
   * Bijgewerkte datum: Bijgewerkte datum voor of na een opgegeven datum

## Het onderbreken, Hervatten, en het Eindigen van een Instantie van het Werkschema {#suspending-resuming-and-terminating-a-workflow-instance}

1. Selecteer **Tools** met Navigatie en **Workflow**.
1. Selecteer **Instanties** om de lijst weer te geven met werkstroominstanties die momenteel worden uitgevoerd.

   ![wf-96-1](/help/sites-cloud/administering/assets/wf-96-1.png)

1. Selecteer een specifiek punt, dan gebruik **Terminate**, **Suspend**, of **hervatten**, zoals aangewezen; bevestiging en/of nadere bijzonderheden zijn vereist:

   ![wf-97-1](/help/sites-cloud/administering/assets/wf-97-1.png)

## Gearchiveerde workflows weergeven {#viewing-archived-workflows}

1. Selecteer **Tools** met Navigatie en **Workflow**.

1. Selecteer **Archiveren** om de lijst met workflowinstanties weer te geven die met succes zijn voltooid.

   ![wf-98](/help/sites-cloud/administering/assets/wf-98.png)

   >[!NOTE]
   >De afbreekstatus wordt beschouwd als een succesvolle beëindiging aangezien het als resultaat van gebruikersactie voorkomt; bijvoorbeeld:
   >
   >* gebruik van de handeling **Terminate**
   >* als een pagina die onderworpen is aan een workflow (geforceerd) wordt verwijderd, wordt de workflow beëindigd


1. Selecteer een specifiek punt, dan **Open Geschiedenis** om meer details te zien:

   ![wf-99](/help/sites-cloud/administering/assets/wf-99.png)

## Problemen met werkstroominstanties oplossen {#fixing-workflow-instance-failures}

Wanneer een werkschema ontbreekt, verstrekt AEM **Failures** console om u toe te staan om aangewezen actie te onderzoeken en te nemen zodra de originele oorzaak is behandeld:

* **Geen**
detailsHiermee wordt een venster geopend waarin de 
**Mislukkingsbericht**,  **** Stapel  **Stapel**.

* **Open**
HistorieHiermee geeft u details weer over de workflowgeschiedenis.

* **Opnieuw** StepExecutes de de componenteninstantie van de Stap van het Manuscript opnieuw. Gebruik de opdracht Stap opnieuw proberen nadat u de oorzaak van de oorspronkelijke fout hebt opgelost. U kunt bijvoorbeeld de stap opnieuw uitvoeren nadat u een fout in het script hebt opgelost dat door de processtap wordt uitgevoerd.
* **Beëindig de werkstroom als de fout een onherstelbare situatie voor het werkschema heeft veroorzaakt.** De workflow kan bijvoorbeeld afhankelijk zijn van omgevingsfactoren, zoals informatie in de opslagplaats die niet langer geldig is voor de werkstroominstantie.
* **Beëindigen en** Opnieuw proberenGelijkaardig aan  **** Terminateeg behalve dat wordt een nieuwe werkschemainstantie begonnen gebruikend de originele nuttige lading, de titel, en de beschrijving.

Om mislukkingen te onderzoeken, dan hervat of beëindigt het werkschema daarna, gebruik de volgende stappen:

1. Selecteer **Tools** met Navigatie en **Workflow**.

1. Selecteer **Failures** om de lijst weer te geven met workflowinstanties die niet met succes zijn voltooid.
1. Selecteer een specifiek item en voer de gewenste actie uit:

   ![wf-47](/help/sites-cloud/administering/assets/wf-47.png)

## Regelmatig leegmaken van workflowinstanties {#regular-purging-of-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen.

Configureer **Adobe Granite Workflow Purge Configuration** om workflowinstanties te wissen volgens hun leeftijd en status. U kunt ook werkstroominstanties van alle modellen of van een specifiek model wissen.

U kunt ook meerdere configuraties van de service maken om workflowinstanties die aan verschillende criteria voldoen, leeg te maken. Maak bijvoorbeeld een configuratie die de instanties van een bepaald workflowmodel zuivert wanneer deze veel langer dan de verwachte tijd worden uitgevoerd. Maak een andere configuratie die alle voltooide workflows na een bepaald aantal dagen leegmaakt om de grootte van de opslagplaats te minimaliseren.

Om de dienst te vormen, kunt u de Dossiers van de Configuratie vormen OSGi zie [OSGi configuratiedossiers](/help/implementing/deploying/configuring-osgi.md). In de volgende tabel worden de eigenschappen beschreven die u voor een van beide methoden nodig hebt.

>[!NOTE]
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>`com.adobe.granite.workflow.purge.Scheduler`
>Omdat de service een fabrieksservice is, vereist de naam van de `sling:OsgiConfig`-node een achtervoegsel met id, bijvoorbeeld:
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
   <td><p>De status van de werkstroominstanties die moeten worden gewist. De volgende waarden zijn geldig:</p>
    <ul>
     <li>VOLTOOID: Voltooide workflowinstanties worden gewist.</li>
     <li>UITVOEREN: Doorlopende workflowinstanties worden gewist.</li>
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

U kunt de maximumgrootte van inbox plaatsen door **de Dienst van het Werkschema** van de Granite van de Adobe te vormen, zie [een configuratie OSGi aan bewaarplaats](/help/implementing/deploying/configuring-osgi.md) toevoegen. De volgende lijst beschrijft het bezit dat u vormt.

>[!NOTE]
>Voor het toevoegen van de configuratie aan de repository is de service-PID:
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Naam eigenschap (webconsole) | OSGi Eigenschapnaam |
|---|---|
| Max. grootte van invoerquery | granite.workflow.inboxQuerySize |

