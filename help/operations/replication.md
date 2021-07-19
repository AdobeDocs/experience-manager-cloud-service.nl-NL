---
title: Replicatie
description: Distributie en replicatie van probleemoplossing.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 00bea8b6a32bab358dae6a8c30aa807cf4586d84
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 1%

---

# Replicatie {#replication}

Adobe Experience Manager als Cloud Service gebruikt de [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) mogelijkheid om de inhoud te verplaatsen naar een pijplijnservice die wordt uitgevoerd op een Adobe I/O die zich buiten de AEM runtime bevindt.

>[!NOTE]
>
>Lees [Distribution](/help/core-concepts/architecture.md#content-distribution) voor meer informatie.

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

### Snel publiceren/publiceren - Gepland ongedaan maken/publiceren {#publish-unpublish}

Hierdoor kunt u de geselecteerde pagina(&#39;s) direct publiceren, zonder de extra opties die mogelijk zijn via de methode Publicatie beheren.

Zie [Publicatie beheren](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication) voor meer informatie.

### Aan- en uittijden - Configuratie activeren {#on-and-off-times-trigger-configuration}

De extra mogelijkheden van **On Tijd** en **Uit Tijd** zijn beschikbaar bij [Basislusje van Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Om de automatische replicatie voor dit te realiseren moet u **Auto Replicate** in [OSGi configuratie](/help/implementing/deploying/configuring-osgi.md) **On Off Configuratie** toelaten:

![Configuratie van OSGi bij activering](/help/operations/assets/replication-on-off-trigger.png)

### Publicatie beheren {#manage-publication}

Publicatie beheren biedt meer opties dan Snel publiceren, waardoor onderliggende pagina&#39;s kunnen worden opgenomen, de referenties kunnen worden aangepast en toepasselijke workflows kunnen worden gestart en de optie kan worden geboden om op een latere datum te publiceren.

Als de onderliggende items van een map worden opgenomen voor de optie &quot;Later publiceren&quot;, wordt de workflow van de structuur met publicatie-inhoud geactiveerd, zoals in dit artikel wordt beschreven.

Meer informatie over Publicatie beheren vindt u in de [documentatie van Grondbeginselen publiceren](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Boomactivering {#tree-activation}

>[!NOTE]
>
>Deze benadering moet als afgekeurd worden beschouwd, aangezien zij geen status aanhoudt en minder schaalbaar is dan andere benaderingen. Aanbevolen wordt in plaats daarvan publicatiemethoden te gebruiken

Een boomactivering uitvoeren:

1. Navigeer in het menu AEM Start naar **Extra > Implementatie > Distributie**
2. Selecteer de kaart **publish**
3. Eenmaal in de gebruikersinterface van de webconsole voor publiceren, **selecteer Distribueren**

   ![](assets/publish-distribute.png "DistributeDistribute")
4. Selecteer het pad in de padbrowser en kies een knooppunt, structuur of verwijder het pad naar wens en selecteer **Verzenden**

### Workflow van inhoudsstructuur publiceren {#publish-content-tree-workflow}

U kunt een boomreplicatie teweegbrengen door **Hulpmiddelen - Werkschema - Modellen** te kiezen en het **Publish Inhoudsboom** uit-van-de-doos werkschemamodel te kopiëren, zoals hieronder getoond:

![](/help/operations/assets/publishcontenttreeworkflow.png)

Wijzig het originele model niet of activeer het niet. In plaats daarvan, zorg ervoor om het model eerst te kopiëren en dan die exemplaar te wijzigen of aan te halen.

Net als bij alle workflows kan de functie ook via de API worden aangeroepen. Voor meer informatie, zie [Interacting with Workflows Programatically](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

Alternatief, kunt u dit ook bereiken door een Model van het Werkschema te creëren dat de `Publish Content Tree` processtap gebruikt:

1. Van de AEM als homepage van de Cloud Service, ga naar **Hulpmiddelen - Werkschema - Modellen**
1. Druk in de pagina Workflowmodellen op **Create** in de rechterbovenhoek van het scherm
1. Voeg een titel en een naam toe aan uw model. Voor meer informatie, zie [Creating Workflow Models](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)
1. Selecteer het nieuwe model in de lijst en druk op **Bewerken**
1. Sleep in het volgende venster de processtap naar de huidige modelstroom:

   ![Processtap](/help/operations/assets/processstep.png)

1. Klik de stap van het Proces in de stroom en selecteer **vorm** door het moersleutelpictogram te drukken
1. Klik op de tab **Proces** en selecteer `Publish Content Tree` in de vervolgkeuzelijst

   ![Treeactivation](/help/operations/assets/newstep.png)

1. Stel aanvullende parameters in het veld **Argumenten** in. Meerdere door komma&#39;s gescheiden argumenten kunnen met elkaar worden verbonden. Bijvoorbeeld:

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >Zie de sectie **Parameters** hieronder voor de lijst met parameters.

1. Druk op **Done** om het workflowmodel op te slaan.

**Parameters**

* `replicateAsParticipant` (booleaanse waarde, standaardwaarde):  `false`). Indien gevormd als `true`, gebruikt de replicatie `userid` van het hoofd dat de deelnemersstap uitvoerde.
* `enableVersion` (booleaanse waarde, standaardwaarde):  `true`). Deze parameter bepaalt als een nieuwe versie op replicatie wordt gecreeerd.
* `agentId` (tekenreekswaarde; de standaardwaarde betekent dat alleen agents voor publicatie worden gebruikt). Men adviseert om over agentId uitdrukkelijk te zijn; Stel bijvoorbeeld de waarde in: publiceren. Als de agent wordt ingesteld op `preview`, wordt de voorvertoningsservice gepubliceerd
* `filters` (tekenreekswaarde, standaard betekent dat alle paden zijn geactiveerd). Beschikbare waarden zijn:
   * `onlyActivated` - alleen paden die niet zijn gemarkeerd als geactiveerd, worden geactiveerd.
   * `onlyModified` - activeer alleen paden die al zijn geactiveerd en een wijzigingsdatum na de activeringsdatum hebben.
   * Het bovenstaande kan ORed zijn met een pijp &quot;|&quot;. Bijvoorbeeld, `onlyActivated|onlyModified`.

**Logboekregistratie**

Wanneer de stap van de workflow voor activering van de structuur begint, worden de configuratieparameters op het INFO-logniveau vastgelegd. Wanneer de wegen worden geactiveerd, wordt een verklaring INFO ook geregistreerd.

Een definitieve verklaring van INFO zal dan worden geregistreerd nadat de werkschemastap alle wegen heeft herhaald.

Bovendien kunt u het logniveau van de loggers onder `com.day.cq.wcm.workflow.process.impl` aan DEBUG/TRACE verhogen om nog meer logboekinformatie te krijgen.

In het geval van fouten, eindigt de werkschemastap met `WorkflowException`, die de onderliggende Uitzondering verpakt.

Hieronder vindt u voorbeelden van logboeken die worden gegenereerd tijdens een voorbeeldworkflow voor de publicatiestructuur van inhoud:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Ondersteuning hervatten**

De workflow verwerkt inhoud in blokken, die elk een subset vormen van de volledige inhoud die moet worden gepubliceerd. Als om het even welke reden de werkschema door het systeem wordt tegengehouden, zal het het brok opnieuw beginnen en verwerken dat nog niet werd verwerkt. In een loginstructie wordt aangegeven dat de inhoud is hervat vanaf een specifiek pad.

### Replicatie-API {#replication-api}

U kunt inhoud publiceren gebruikend Replacement API die in AEM als Cloud Service wordt vermeld.

Zie de [API-documentatie](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html) voor meer informatie.

**Basisgebruik van de API**

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

**Replicatie met specifieke agents**

Wanneer het repliceren van middelen zoals in het bovenstaande voorbeeld, slechts de agenten die door gebrek actief zijn zullen worden gebruikt. In AEM als Cloud Service, zal dit slechts de agent genoemd &quot;publiceren&quot;zijn, die de auteur met publicatielaag verbindt.

Ter ondersteuning van de voorvertoningsfunctionaliteit is een nieuwe agent met de naam &quot;preview&quot; toegevoegd, die niet standaard actief is. Deze agent wordt gebruikt om de auteur met de voorproefrij te verbinden. Als u slechts via de voorproefagent wilt herhalen, moet u deze voorproefagent via `AgentFilter` uitdrukkelijk selecteren.

Zie het onderstaande voorbeeld over hoe u dit kunt doen:

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

Het algemene `ReplicationStatus` van een middel wordt slechts gewijzigd als de replicatieactie minstens één agent omvat die door gebrek actief is. In het bovenstaande voorbeeld is dit niet het geval, aangezien de replicatie enkel de &quot;voorproef&quot;agent gebruikt. Daarom moet u de nieuwe `getStatusForAgent()` methode gebruiken, die het vragen van de status voor een specifieke agent toestaat. Deze methode werkt ook voor de &quot;publiceer&quot;agent. Het keert een niet-krachteloze waarde terug als er om het even welke replicatieactie die gebruikend de verstrekte agent is gedaan geweest.

## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de Auteur AEM:

1. Navigeer in het menu AEM Start naar **Extra > Implementatie > Distributie**
2. Selecteer de kaart **publish**
   ![](assets/publish-status.png "StatusStatus")
3. Controleer de wachtrijstatus die groen moet zijn
4. U kunt de verbinding met de replicatieservice testen
5. Selecteer het tabblad **Logs** waarmee de geschiedenis van inhoudspublicaties wordt weergegeven

![](assets/publish-logs.png "LogsLogs")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM-publicatieservice.
In dat geval wordt in de hoofdbewerkbare wachtrij een rode status weergegeven en moet deze worden herzien om te bepalen welke items de annulering van de publicatie hebben veroorzaakt. Door op die wachtrij te klikken, worden de items in behandeling weergegeven, waaruit één item of alle items indien nodig kunnen worden gewist.
