---
title: Replicatie
description: Distributie en replicatie van probleemoplossing.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 1a42cfaa1010686279bc11ca92f50afc75d89e9d
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 1%

---

# Replicatie {#replication}

Adobe Experience Manager as a Cloud Service gebruikt de [Distributie van inhoud verkopen](https://sling.apache.org/documentation/bundles/content-distribution.html) capaciteit om de inhoud te bewegen aan een pijpleidingsdienst te herhalen die op Adobe I/O wordt uitgevoerd die buiten AEM runtime is.

>[!NOTE]
>
>Lezen [Distributie](/help/overview/architecture.md#content-distribution) voor meer informatie .

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

>[!NOTE]
>
>Als u interesse hebt in content voor bulkpublicaties, gebruikt u de [Workflow van inhoudsstructuur publiceren](#publish-content-tree-workflow).
>Deze workflowstap is speciaal voor Cloud Service gemaakt en kan grote ladingen efficiënt verwerken.
>Het wordt niet aanbevolen om uw eigen aangepaste code voor bulkpublicaties te maken.
>Als u om welke reden dan ook moet aanpassen, kunt u deze workflow/workflow-stap activeren door bestaande workflow-API&#39;s te gebruiken.
>Hoewel het altijd een goede gewoonte is om alleen inhoud te publiceren die gepubliceerd moet worden en om voorzichtig te zijn met het niet publiceren van een groot aantal inhoud als dit niet nodig is, gelden er geen beperkingen voor de hoeveelheid inhoud die u via de workflow van de inhoudsstructuur publiceren kunt verzenden.

### Snel publiceren/publiceren - Gepland ongedaan maken/publiceren {#publish-unpublish}

Hierdoor kunt u de geselecteerde pagina(&#39;s) direct publiceren, zonder de extra opties die mogelijk zijn via de methode Publicatie beheren.

Zie voor meer informatie [Publicatie beheren](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Aan- en uittijden - Configuratie activeren {#on-and-off-times-trigger-configuration}

De extra mogelijkheden van **Op tijd** en **Uit-tijd** zijn beschikbaar op [Het tabblad Standaard van Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Om de automatische replicatie voor dit te realiseren moet u toelaten **Automatisch repliceren** in de [OSGi-configuratie](/help/implementing/deploying/configuring-osgi.md) **Configuratie van activering uit**:

![Configuratie van OSGi bij activering](/help/operations/assets/replication-on-off-trigger.png)

### Publicatie beheren {#manage-publication}

Publicatie beheren biedt meer opties dan Snel publiceren, waardoor onderliggende pagina&#39;s kunnen worden opgenomen, de referenties kunnen worden aangepast en toepasselijke workflows kunnen worden gestart en de optie kan worden geboden om op een latere datum te publiceren.

Als de onderliggende items van een map worden opgenomen voor de optie &quot;Later publiceren&quot;, wordt de workflow van de structuur met publicatie-inhoud geactiveerd, zoals in dit artikel wordt beschreven.

U vindt meer gedetailleerde informatie over Publicatie beheren op het tabblad [Publicatie van documentatie over grondbeginselen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Workflow van inhoudsstructuur publiceren {#publish-content-tree-workflow}

U kunt een boomreplicatie teweegbrengen door te kiezen **Tools - Workflow - Modellen** en het kopiëren van de **Inhoudsstructuur publiceren** out-of-the-box workflowmodel, zoals hieronder getoond:

![](/help/operations/assets/publishcontenttreeworkflow.png)

Wijzig het originele model niet of activeer het niet. In plaats daarvan, zorg ervoor om het model eerst te kopiëren en dan die exemplaar te wijzigen of aan te halen.

Net als bij alle workflows kan de functie ook via de API worden aangeroepen. Zie voor meer informatie [Programmatische interactie met Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

U kunt dit ook bereiken door een workflowmodel te maken dat gebruikmaakt van de `Publish Content Tree` processtap:

1. Ga vanaf de AEM as a Cloud Service startpagina naar **Tools - Workflow - Modellen**
1. Druk op de pagina Workflowmodellen op **Maken** in de rechterbovenhoek van het scherm
1. Voeg een titel en een naam toe aan uw model. Zie voor meer informatie [Workflowmodellen maken](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)
1. Selecteer het nieuwe model in de lijst en druk op **Bewerken**
1. Sleep in het volgende venster de processtap naar de huidige modelstroom:

   ![Processtap](/help/operations/assets/processstep.png)

1. Klik op de stap Proces in de flow en selecteer **Configureren** door op het moersleutelpictogram te drukken
1. Klik op de knop **Proces** en selecteert u `Publish Content Tree` in de vervolgkeuzelijst

   ![Treeactivation](/help/operations/assets/newstep.png)

1. Stel eventuele aanvullende parameters in het dialoogvenster **Argumenten** veld. Meerdere door komma&#39;s gescheiden argumenten kunnen met elkaar worden verbonden. Bijvoorbeeld:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Voor de lijst met parameters raadpleegt u de **Parameters** hieronder.

1. Druk **Gereed** om het workflowmodel op te slaan.

**Parameters**

* `includeChildren` (booleaanse waarde, standaardwaarde): `false`). false betekent dat alleen het pad wordt gepubliceerd. true betekent dat ook kinderen worden gepubliceerd .
* `replicateAsParticipant` (booleaanse waarde, standaardwaarde): `false`). Indien geconfigureerd als `true`, gebruikt de replicatie de `userid` van de opdrachtgever die de deelnemersstap heeft uitgevoerd.
* `enableVersion` (booleaanse waarde, standaardwaarde): `true`). Deze parameter bepaalt als een nieuwe versie op replicatie wordt gecreeerd.
* `agentId` (tekenreekswaarde; de standaardwaarde betekent dat alleen agents voor publicatie worden gebruikt). Men adviseert om over agentId uitdrukkelijk te zijn; Stel bijvoorbeeld de waarde in: publiceren. De agent instellen op `preview` publiceert naar de voorbeeldservice
* `filters` (tekenreekswaarde, standaard betekent dat alle paden zijn geactiveerd). Beschikbare waarden zijn:
   * `onlyActivated` - alleen pagina&#39;s activeren die (al) zijn geactiveerd. Werkt als een vorm van reactivering.
   * `onlyModified` - activeer alleen paden die al zijn geactiveerd en een wijzigingsdatum na de activeringsdatum hebben.
   * Het bovenstaande kan ORed zijn met een pijp &quot;|&quot;. Bijvoorbeeld, `onlyActivated|onlyModified`.

**Logboekregistratie**

Wanneer de stap van de workflow voor activering van de structuur begint, worden de configuratieparameters op het INFO-logniveau vastgelegd. Wanneer de wegen worden geactiveerd, wordt een verklaring INFO ook geregistreerd.

Een definitieve verklaring van INFO zal dan worden geregistreerd nadat de werkschemastap alle wegen heeft herhaald.

Daarnaast kunt u het logniveau van de onderstaande loggers verhogen `com.day.cq.wcm.workflow.process.impl` aan DEBUG/TRACE om nog meer logboekinformatie te krijgen.

In het geval van fouten, eindigt de werkschemastap met een `WorkflowException`, die de onderliggende uitzondering omsluit.

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

U kunt inhoud publiceren gebruikend de Replicatie API die in AEM as a Cloud Service wordt getoond.

Zie voor meer informatie de [API-documentatie](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

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

Wanneer het repliceren van middelen zoals in het bovenstaande voorbeeld, slechts de agenten die door gebrek actief zijn zullen worden gebruikt. In AEM as a Cloud Service, zal dit slechts de agent genoemd &quot;publiceren&quot;zijn, die de auteur met publicatielaag verbindt.

Ter ondersteuning van de voorvertoningsfunctionaliteit is een nieuwe agent met de naam &quot;preview&quot; toegevoegd, die niet standaard actief is. Deze agent wordt gebruikt om de auteur met de voorproefrij te verbinden. Als u slechts via de voorproefagent wilt herhalen, moet u deze voorproefagent uitdrukkelijk selecteren via `AgentFilter`.

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

De `ReplicationStatus` van een middel wordt slechts gewijzigd als de replicatieactie minstens één agent omvat die door gebrek actief is. In het bovenstaande voorbeeld is dit niet het geval, aangezien de replicatie enkel de &quot;voorproef&quot;agent gebruikt. Daarom moet u het nieuwe `getStatusForAgent()` methode, die het vragen van de status voor een specifieke agent toestaat. Deze methode werkt ook voor de &quot;publiceer&quot;agent. Het keert een niet-krachteloze waarde terug als er om het even welke replicatieactie die gebruikend de verstrekte agent is gedaan geweest.

### Methoden voor het ongeldig maken van inhoud {#invalidating-content}

U kunt inhoud direct ongeldig maken door of het Verdelen van de Invalidatie van de Inhoud (SCD) van auteur (de aangewezen methode) te gebruiken of door de Replicatie API te gebruiken om de publicatieverzender te roepen flush replicatieagent. Zie de [Caching](/help/implementing/dispatcher/caching.md) voor meer informatie.

**Limieten voor replicatie-API**

Het wordt aanbevolen minder dan 100 paden tegelijk te repliceren, waarbij 500 paden de harde limiet zijn. Boven de harde limiet geldt een `ReplicationException` wordt gegenereerd.
Als voor uw toepassingslogica geen atoomreplicatie is vereist, kunt u deze limiet overwinnen door het instellen van de optie `ReplicationOptions.setUseAtomicCalls` naar false, dat een willekeurig aantal paden accepteert, maar intern emmers maakt om onder deze limiet te blijven.

De grootte van de inhoud die per replicatievraag wordt overgebracht moet niet overschrijden `10 MB`. Dit omvat de knooppunten en de eigenschappen, maar geen binaire bestanden (workflowpakketten en inhoudspakketten worden als binaire bestanden beschouwd).


## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de Auteur AEM:

1. Ga in het menu AEM Start naar **Extra > Implementatie > Distributie**
2. Selecteer de kaart **publish**
   ![Status](assets/publish-status.png "Status")
3. Controleer de wachtrijstatus die groen moet zijn
4. U kunt de verbinding met de replicatieservice testen
5. Selecteer **Logboeken** tabblad waarin de geschiedenis van publicaties met inhoud wordt weergegeven

![Logboeken](assets/publish-logs.png "Logboeken")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM-publicatieservice.
In dat geval wordt in de hoofdbewerkbare wachtrij een rode status weergegeven en moet deze worden herzien om te bepalen welke items de annulering van de publicatie hebben veroorzaakt. Door op die wachtrij te klikken, worden de items in behandeling weergegeven, waaruit één item of alle items indien nodig kunnen worden gewist.
