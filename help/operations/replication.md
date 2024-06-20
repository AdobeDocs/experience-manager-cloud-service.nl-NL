---
title: Replicatie
description: Leer over distributie en het oplossen van problemenreplicatie in AEM as a Cloud Service.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 0%

---

# Replicatie {#replication}

Adobe Experience Manager as a Cloud Service gebruikt de [Distributie van inhoud verkopen](https://sling.apache.org/documentation/bundles/content-distribution.html) mogelijkheid om de inhoud te verplaatsen naar een pijplijnservice die op Adobe Developer wordt uitgevoerd en die zich buiten de AEM runtime bevindt.

>[!NOTE]
>
>Lezen [Distributie](/help/overview/architecture.md#content-distribution) voor meer informatie .

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

>[!NOTE]
>
>Als u geïnteresseerd bent in het bulksgewijs publiceren van inhoud, gebruikt u de [Workflow van inhoudsstructuur publiceren](#publish-content-tree-workflow).
>Deze workflowstap is speciaal voor Cloud Service gemaakt en kan grote ladingen efficiënt verwerken.
>Het wordt niet aangeraden om uw eigen aangepaste code voor bulkpublicaties te maken.
>Als u om welke reden dan ook moet aanpassen, kunt u deze workflow/workflowstap activeren met behulp van bestaande workflow-API&#39;s.
>Het is altijd een goede gewoonte om alleen inhoud te publiceren die moet worden gepubliceerd. En wees voorzichtig als u geen grote aantallen content probeert te publiceren, als dat niet nodig is. Er gelden echter geen beperkingen voor de hoeveelheid inhoud die u via de workflow van de inhoudsstructuur voor publiceren kunt verzenden.

### Snel publiceren/publiceren - Gepland ongedaan maken/publiceren {#publish-unpublish}

Met deze functie kunt u de geselecteerde pagina&#39;s direct publiceren, zonder de extra opties die mogelijk zijn via de methode Publicatie beheren.

Zie voor meer informatie [Publicatie beheren](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

### Aan- en uittijden - Configuratie activeren {#on-and-off-times-trigger-configuration}

De extra mogelijkheden van **Op tijd** en **Uit-tijd** zijn beschikbaar op [Het tabblad Standaard van Pagina-eigenschappen](/help/sites-cloud/authoring/sites-console/page-properties.md#basic).

Om de automatische replicatie voor deze eigenschap te realiseren, laat toe **Automatisch repliceren** in de [OSGi-configuratie](/help/implementing/deploying/configuring-osgi.md) **Configuratie van activering uit**:

![Configuratie van OSGi bij activering](/help/operations/assets/replication-on-off-trigger.png)

### Publicatie beheren {#manage-publication}

Publicatie beheren biedt meer opties dan Snel publiceren, waardoor onderliggende pagina&#39;s kunnen worden opgenomen, de referenties kunnen worden aangepast en toepasselijke workflows kunnen worden gestart en de optie kan worden geboden om later te publiceren.

Als de onderliggende items van een map worden opgenomen voor de optie &quot;Later publiceren&quot;, wordt de workflow van de inhoudsstructuur publiceren geactiveerd, zoals in dit artikel wordt beschreven.

U vindt meer gedetailleerde informatie over Publicatie beheren op het tabblad [Publicatie van documentatie over grondbeginselen](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

### Workflow van inhoudsstructuur publiceren {#publish-content-tree-workflow}

U kunt een boomreplicatie teweegbrengen door te kiezen **Tools - Workflow - Modellen** en kopiëren **Inhoudsstructuur publiceren** out-of-the-box workflowmodel, zoals hieronder getoond:

![De werkstroomkaart van de inhoudsstructuur publiceren](/help/operations/assets/publishcontenttreeworkflow.png)

Roep het oorspronkelijke model niet aan. Let er in plaats daarvan op dat u het model eerst kopieert en dat exemplaar aanroept.

Net als bij alle workflows kan de functie ook via de API worden aangeroepen. Zie voor meer informatie [Programmatische interactie met Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html#extending-aem).

U kunt ook een workflowmodel maken waarin de `Publish Content Tree` processtap:

1. Ga vanaf de AEM as a Cloud Service startpagina naar **Tools - Workflow - Modellen**.
1. Druk op de pagina Workflowmodellen op **Maken** rechtsboven in het scherm.
1. Voeg een titel en een naam toe aan uw model. Zie voor meer informatie [Workflowmodellen maken](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html).
1. Selecteer het gemaakte model in de lijst en druk op **Bewerken**
1. Sleep in het volgende venster de processtap naar de huidige modelstroom:

   ![Processtap](/help/operations/assets/processstep.png)

1. Selecteer de processtap in de flow en selecteer **Configureren** door op het moersleutelpictogram te drukken.
1. Selecteer de **Proces** en selecteert u `Publish Content Tree` in de vervolgkeuzelijst, controleert u vervolgens de **Handler Advance** selectievakje

   ![Treeactivation](/help/operations/assets/newstep.png)

1. Stel eventuele aanvullende parameters in het dialoogvenster **Argumenten** veld. U kunt meerdere door komma&#39;s gescheiden argumenten samenvoegen. Bijvoorbeeld:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Voor de lijst met parameters raadpleegt u de **Parameters** hieronder.

1. Druk **Gereed** om het workflowmodel op te slaan.

**Parameters**

* `includeChildren` (booleaanse waarde, standaardwaarde): `false`). De waarde `false` betekent dat alleen het pad wordt gepubliceerd; `true` betekent dat ook kinderen worden gepubliceerd.
* `replicateAsParticipant` (booleaanse waarde, standaardwaarde): `false`). Indien geconfigureerd als `true`, gebruikt de replicatie de `userid` van de opdrachtgever die de deelnemersstap heeft uitgevoerd.
* `enableVersion` (booleaanse waarde, standaardwaarde): `false`). Deze parameter bepaalt als een nieuwe versie op replicatie wordt gecreeerd.
* `agentId` (tekenreekswaarde; de standaardwaarde betekent dat alleen agents voor publicatie worden gebruikt). Men adviseert om over agentId uitdrukkelijk te zijn; bijvoorbeeld, plaatsend het de waarde: publiceer. De agent instellen op `preview` publiceert naar de voorbeeldservice.
* `filters` (standaardwaarde betekent dat alle paden zijn geactiveerd). Beschikbare waarden zijn:
   * `onlyActivated` - alleen pagina&#39;s activeren die (al) zijn geactiveerd. Werkt als een vorm van reactivering.
   * `onlyModified` - activeer alleen paden die al zijn geactiveerd en een wijzigingsdatum na de activeringsdatum hebben.
   * Het bovenstaande kan ORed zijn met een pijp &quot;|&quot;. Bijvoorbeeld: `onlyActivated|onlyModified`.

**Logboekregistratie**

Wanneer de stap van het werkschema van de boomactivering begint, registreert het zijn configuratieparameters op het INFO loglevel. Wanneer de wegen worden geactiveerd, wordt een verklaring INFO ook geregistreerd.

Een laatste INFO-instructie wordt vastgelegd nadat alle paden door de workflowstap zijn gerepliceerd.

U kunt ook het logniveau van de onderstaande loggers verhogen `com.day.cq.wcm.workflow.process.impl` aan DEBUG/TRACE om nog meer logboekinformatie te krijgen.

Als er fouten optreden, wordt de workflowstap beëindigd met een `WorkflowException`, die de onderliggende uitzondering omsluit.

Hieronder volgen voorbeelden van logboeken die worden gegenereerd tijdens een workflow in een voorbeeld van een publicatiestructuur voor inhoud:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Ondersteuning hervatten**

De workflow verwerkt inhoud in blokken, die elk een subset vormen van de volledige inhoud die moet worden gepubliceerd. Als de workflow door het systeem wordt gestopt, wordt het segment dat nog niet is verwerkt opnieuw gestart en verwerkt. Een logboekverklaring verklaart dat de inhoud van een specifieke weg werd hervat.

### Replicatie-API {#replication-api}

U kunt inhoud publiceren gebruikend de Replicatie API die in AEM as a Cloud Service wordt getoond.

Zie de klasse [API-documentatie](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

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

Bij het repliceren van middelen, zoals in het bovenstaande voorbeeld, slechts worden de agenten gebruikt die door gebrek actief zijn. In AEM as a Cloud Service, betekent het slechts de agent genoemd &quot;publiceert&quot;, die de auteur met publicatielaag verbindt.

Ter ondersteuning van de voorvertoningsfunctionaliteit is een nieuwe agent met de naam &quot;preview&quot; toegevoegd, die niet standaard actief is. Deze agent wordt gebruikt om de auteur met de voorproefrij te verbinden. Als u slechts door de voorproefagent wilt herhalen, moet u deze voorproefagent uitdrukkelijk selecteren als `AgentFilter`.

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

Het geheel `ReplicationStatus` van een middel wordt slechts gewijzigd als de replicatieactie minstens één agent omvat die door gebrek actief is. In het bovenstaande voorbeeld was deze stroom niet het geval. De replicatie gebruikte gewoon de &#39;preview&#39;-agent. Daarom moet u het nieuwe `getStatusForAgent()` methode, die het vragen van de status voor een specifieke agent toestaat. Deze methode werkt ook voor de &quot;publiceer&quot;agent. Het keert een niet-krachteloze waarde terug als er om het even welke replicatieactie is gedaan gebruikend de verstrekte agent.

### Methoden voor het ongeldig maken van inhoud {#invalidating-content}

U kunt inhoud direct ongeldig maken door of de Verschuivende Invalidatie van de Inhoud (SCD) van auteur (de aangewezen methode) te gebruiken of door de Replicatie API te gebruiken om te roepen publiceert Dispatcher leegmaken replicatieagent. Zie [Caching](/help/implementing/dispatcher/caching.md) voor meer informatie.

**Limieten voor replicatie-API**

Repliceer minder dan 100 paden tegelijk, waarbij 500 paden de limiet zijn. Boven de limiet `ReplicationException` wordt gegenereerd.
Als voor uw toepassingslogica geen atoomreplicatie is vereist, kunt u deze limiet overwinnen door het instellen van de optie `ReplicationOptions.setUseAtomicCalls` naar false, dat een willekeurig aantal paden accepteert, maar intern emmers maakt om onder deze limiet te blijven.

De grootte van de inhoud die per replicatievraag wordt overgebracht moet niet overschrijden `10 MB`. Deze regel bevat de knooppunten en eigenschappen, maar geen binaire bestanden (workflowpakketten en inhoudspakketten worden als binaire bestanden beschouwd).


## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de AEM Auteur:

1. Navigeer in het menu AEM Start naar **Gereedschappen** > **Implementatie** > **Distributie**
1. Selecteer de kaart **publish**

   ![Status](assets/publish-status.png "Status")

1. Controleer de wachtrijstatus die groen moet zijn
1. U kunt de verbinding met de replicatieservice testen
1. Selecteer de **Logboeken** tabblad waarin de geschiedenis van publicaties met inhoud wordt weergegeven

![Logboeken](assets/publish-logs.png "Logboeken")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM publicatieservice.

In dat geval geeft de hoofdwachtrij een rode status weer en moet deze worden gecontroleerd om te bepalen welke items de annulering van de publicatie hebben veroorzaakt. Door op die wachtrij te klikken, worden de items in behandeling weergegeven, waaruit één item of alle items indien nodig kunnen worden gewist.
