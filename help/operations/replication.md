---
title: Replicatie
description: Meer informatie over distributie en probleemoplossing voor replicatie in AEM as a Cloud Service.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 0%

---

# Replicatie {#replication}

Adobe Experience Manager as a Cloud Service gebruikt het [ Verschuivende vermogen van de Distributie van de Inhoud ](https://sling.apache.org/documentation/bundles/content-distribution.html) om de inhoud te bewegen om aan een pijpleidingsdienst te herhalen die op Adobe Developer wordt uitgevoerd die buiten AEM runtime is.

>[!NOTE]
>
>Lees [ Distributie ](/help/overview/architecture.md#content-distribution) voor meer informatie.

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

>[!NOTE]
>
>Als u in bulk het publiceren inhoud geinteresseerd bent, gebruik het [ Werkschema van de Boom van de Inhoud van Publish ](#publish-content-tree-workflow).
>Deze workflowstap is speciaal voor Cloud Service gemaakt en kan grote ladingen efficiënt verwerken.
>Het wordt niet aangeraden om uw eigen aangepaste code voor bulkpublicaties te maken.
>Als u om welke reden dan ook moet aanpassen, kunt u deze workflow/workflowstap activeren met behulp van bestaande workflow-API&#39;s.
>Het is altijd een goede gewoonte om alleen inhoud te publiceren die moet worden gepubliceerd. En wees voorzichtig als u geen grote aantallen content probeert te publiceren, als dat niet nodig is. Er gelden echter geen beperkingen voor de hoeveelheid inhoud die u via de Publish Content Tree Workflow kunt verzenden.

### Quick Un/Publish - Gepland VN/Publish {#publish-unpublish}

Met deze functie kunt u de geselecteerde pagina&#39;s direct publiceren, zonder de extra opties die mogelijk zijn via de methode Publicatie beheren.

Voor meer informatie, zie [ Publicatie ](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication) leiden.

### Aan- en uittijden - Configuratie activeren {#on-and-off-times-trigger-configuration}

De extra mogelijkheden van **op Tijd** en **van Tijd** zijn beschikbaar bij het [ Basis lusje van de Eigenschappen van de Pagina ](/help/sites-cloud/authoring/sites-console/page-properties.md#basic).

Om de automatische replicatie voor deze eigenschap te realiseren, laat **AutoReplicatie** in de [ configuratie OSGi ](/help/implementing/deploying/configuring-osgi.md) **op van de Configuratie van de Trekker** toe:

![ OSGi op de Configuratie van de Trekker ](/help/operations/assets/replication-on-off-trigger.png)

### Publicatie beheren {#manage-publication}

Publicatie beheren biedt meer opties dan Quick Publish, waardoor onderliggende pagina&#39;s kunnen worden opgenomen, de referenties kunnen worden aangepast en toepasselijke workflows kunnen worden gestart en de optie kan worden geboden om later te publiceren.

Als onderliggende items van een map worden opgenomen voor de optie &quot;Later publiceren&quot;, wordt de workflow van de Publish-inhoudsstructuur geactiveerd, zoals in dit artikel wordt beschreven.

U kunt meer gedetailleerde informatie over Manage Publication over de [ het Publiceren documentatie van Grondbeginselen ](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication) vinden.

### Publish Content Tree Workflow {#publish-content-tree-workflow}

U kunt een boomreplicatie teweegbrengen door **Hulpmiddelen te kiezen - Werkschema - Modellen** en het kopiëren van het **de Inhoudsboom van Publish** uit-van-de-doos werkschemamodel, zoals hieronder getoond:

![ de Kaart van het Werkschema van de Inhoudsboom van Publish ](/help/operations/assets/publishcontenttreeworkflow.png)

Roep het oorspronkelijke model niet aan. Let er in plaats daarvan op dat u het model eerst kopieert en dat exemplaar aanroept.

Net als bij alle workflows kan de functie ook via de API worden aangeroepen. Voor meer informatie, zie [ Interacting met Workflows programmatically ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html#extending-aem).

U kunt ook een workflowmodel maken dat de processtap `Publish Content Tree` gebruikt:

1. Van de homepage van AEM as a Cloud Service, ga naar **Hulpmiddelen - Werkschema - Modellen**.
1. In de pagina Modellen van het Werkschema, druk **creeer** in de hogere juiste hoek van het scherm.
1. Voeg een titel en een naam toe aan uw model. Voor meer informatie, zie [ Creërend de Modellen van het Werkschema ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html).
1. Selecteer het gecreeerde model van de lijst, en druk **uitgeven**
1. Sleep in het volgende venster de processtap naar de huidige modelstroom:

   ![ Stap van het Proces ](/help/operations/assets/processstep.png)

1. Selecteer de stap van het Proces in de stroom en selecteer **vormen** door het moersleutelpictogram te drukken.
1. Selecteer het **lusje van het Proces** {en selecteer `Publish Content Tree` van de drop-down lijst, dan controleer het **Geniet van de Handler {** controlevakje

   ![ Treeactivation ](/help/operations/assets/newstep.png)

1. Plaats om het even welke extra parameters op het **gebied van Argumenten**. U kunt meerdere door komma&#39;s gescheiden argumenten samenvoegen. Bijvoorbeeld:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Voor de lijst van parameters, zie de **hieronder sectie van Parameters**.

1. Pers **Gedaan** om het model van het Werkschema te bewaren.

**Parameters**

* `includeChildren` (booleaanse waarde, standaardwaarde: `false` ). De waarde `false` betekent dat alleen het pad wordt gepubliceerd; `true` betekent dat ook onderliggende objecten worden gepubliceerd.
* `replicateAsParticipant` (booleaanse waarde, standaardwaarde: `false` ). Indien geconfigureerd als `true`, gebruikt de replicatie de `userid` van de principal die de deelnemersstap heeft uitgevoerd.
* `enableVersion` (booleaanse waarde, standaardwaarde: `false` ). Deze parameter bepaalt als een nieuwe versie op replicatie wordt gecreeerd.
* `agentId` (tekenreekswaarde, standaardwaarde betekent dat alleen de publicatieagents worden gebruikt). Men adviseert om over agentId uitdrukkelijk te zijn; bijvoorbeeld, plaatsend het de waarde: publiceer. Als u de agent instelt op `preview` , wordt deze naar de service preview gepubliceerd.
* `filters` (standaardwaarde betekent dat alle paden zijn geactiveerd). Beschikbare waarden zijn:
   * `onlyActivated` - alleen pagina&#39;s activeren die (al) zijn geactiveerd. Werkt als een vorm van reactivering.
   * `onlyModified` - activeer alleen paden die al zijn geactiveerd en een wijzigingsdatum na de activeringsdatum hebben.
   * Het bovenstaande kan ORed zijn met een pijp &quot;|&quot;. Bijvoorbeeld `onlyActivated|onlyModified` .

**het Registreren**

Wanneer de stap van het werkschema van de boomactivering begint, registreert het zijn configuratieparameters op het INFO loglevel. Wanneer de wegen worden geactiveerd, wordt een verklaring INFO ook geregistreerd.

Een laatste INFO-instructie wordt vastgelegd nadat alle paden door de workflowstap zijn gerepliceerd.

U kunt ook het logniveau van de loggers onder `com.day.cq.wcm.workflow.process.impl` verhogen tot DEBUG/TRACE voor nog meer loginformatie.

Als er fouten zijn, eindigt de werkschemastap met a `WorkflowException`, die de onderliggende Uitzondering verpakt.

Hieronder volgen voorbeelden van logboeken die worden gegenereerd tijdens een workflow in een voorbeeld van een publicatiestructuur voor inhoud:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Steun van het hervatten**

De workflow verwerkt inhoud in blokken, die elk een subset vormen van de volledige inhoud die moet worden gepubliceerd. Als de workflow door het systeem wordt gestopt, wordt het segment dat nog niet is verwerkt opnieuw gestart en verwerkt. Een logboekverklaring verklaart dat de inhoud van een specifieke weg werd hervat.

### Replicatie-API {#replication-api}

U kunt inhoud publiceren met behulp van de Replicatie-API die in AEM as a Cloud Service is geïnstalleerd.

Voor meer informatie, zie de [ API Documentatie ](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

**Basis Gebruik van API**

```
@Reference
Replicator replicator;
@Reference
ReplicationStatusProvider replicationStatusProvider;

....
Session session = ...
// Activate a single page to all agents, which are active by default
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en");
// Activate multiple pages (but try to limit it to approx 100 at max)
replicator.replicate(session,ReplicationActionType.ACTIVATE, new String[]{"/content/we-retail/en","/content/we-retail/de"});

// ways to get the replication status
Resource enResource = resourceResolver.getResource("/content/we-retail/en");
Resource deResource = resourceResolver.getResource("/content/we-retail/de");
ReplicationStatus enStatus = enResource.adaptTo(ReplicationStatus.class);
// if you need to get the status for more more than 1 resource at once, this approach is more performant
Map<String,ReplicationStatus> allStatus = replicationStatusProvider.getBatchReplicationStatus(enResource,deResource);
```

**Replicatie met Specifieke Agenten**

Bij het repliceren van middelen, zoals in het bovenstaande voorbeeld, slechts worden de agenten gebruikt die door gebrek actief zijn. In AEM as a Cloud Service betekent dit alleen de agent met de naam &quot;publish&quot;, die de auteur verbindt met de publicatielijst.

Ter ondersteuning van de voorvertoningsfunctionaliteit is een nieuwe agent met de naam &quot;preview&quot; toegevoegd, die niet standaard actief is. Deze agent wordt gebruikt om de auteur met de voorproefrij te verbinden. Als u alleen via de voorvertoningsagent wilt repliceren, moet u deze voorvertoningsagent expliciet selecteren via een `AgentFilter` .

Zie het volgende voorbeeld:

```
private static final String PREVIEW_AGENT = "preview";

ReplicationStatus beforeStatus = enResource.adaptTo(ReplicationStatus.class); // beforeStatus.isActivated == false

ReplicationOptions options = new ReplicationOptions();
options.setFilter(new AgentFilter() {
  @Override
  public boolean isIncluded (Agent agent) {
    return agent.getId().equals(PREVIEW_AGENT);
  }
});
// will replicate only to preview
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en", options);

ReplicationStatus afterStatus = enResource.adaptTo(ReplicationStatus.class); // afterStatus.isActivated == false
ReplicationStatus previewStatus = afterStatus.getStatusForAgent(PREVIEW_AGENT); // previewStatus.isActivated == true
```

Als u een dergelijk filter niet aanbiedt en alleen de &quot;publish&quot;-agent gebruikt, wordt de &quot;preview&quot;-agent niet gebruikt en heeft de replicatiehandeling geen invloed op de voorvertoningslaag.

De algemene `ReplicationStatus` van een bron wordt alleen gewijzigd als de replicatiehandeling ten minste één agent bevat die standaard actief is. In het bovenstaande voorbeeld was deze stroom niet het geval. De replicatie gebruikte gewoon de &#39;preview&#39;-agent. Daarom moet u de nieuwe `getStatusForAgent()` methode gebruiken, die het vragen van de status voor een specifieke agent toestaat. Deze methode werkt ook voor de &quot;publiceer&quot;agent. Het keert een niet-krachteloze waarde terug als er om het even welke replicatieactie is gedaan gebruikend de verstrekte agent.

### Methoden voor het ongeldig maken van inhoud {#invalidating-content}

U kunt inhoud direct ongeldig maken door of het Verdelen van de Invalidatie van de Inhoud (SCD) van auteur (de aangewezen methode) te gebruiken of door de Replicatie API te gebruiken om publiceer Dispatcher te roepen flush replicatieagent. Zie [ Caching ](/help/implementing/dispatcher/caching.md) pagina voor verdere details.

**de capaciteitsgrenzen van de Replicatie API**

Repliceer minder dan 100 paden tegelijk, waarbij 500 paden de limiet zijn. Boven de limiet wordt een `ReplicationException` gegenereerd.
Als voor uw toepassingslogica geen atomische replicatie is vereist, kan deze limiet worden overbrugd door de waarde `ReplicationOptions.setUseAtomicCalls` in te stellen op false, die een willekeurig aantal paden accepteert, maar intern emmers maakt om onder deze limiet te blijven.

De grootte van de inhoud die per replicatieaanroep wordt verzonden, mag niet groter zijn dan `10 MB` . Deze regel bevat de knooppunten en eigenschappen, maar geen binaire bestanden (workflowpakketten en inhoudspakketten worden als binaire bestanden beschouwd).


## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de AEM Auteur:

1. Van het Menu van het Begin van het AEM, navigeer aan **Hulpmiddelen** > **Plaatsing** > **Distributie**
1. Selecteer kaart **publiceren**

   ![ Status ](assets/publish-status.png " Status ")

1. Controleer de wachtrijstatus die groen moet zijn
1. U kunt de verbinding met de replicatieservice testen
1. Selecteer het **Logs** lusje dat de geschiedenis van inhoudspublicaties toont

![ Logs ](assets/publish-logs.png " Logs ")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM Publish Service.

In dat geval geeft de hoofdwachtrij een rode status weer en moet deze worden gecontroleerd om te bepalen welke items de annulering van de publicatie hebben veroorzaakt. Door op die wachtrij te klikken, worden de items in behandeling weergegeven, waaruit één item of alle items indien nodig kunnen worden gewist.
