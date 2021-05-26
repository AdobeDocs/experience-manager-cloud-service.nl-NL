---
title: Replicatie
description: Distributie en replicatie van probleemoplossing.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 1ba960a930e180f4114f78607a3eb4bd5ec3edaf
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 1%

---

# Replicatie {#replication}

Adobe Experience Manager als Cloud Service gebruikt de [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) mogelijkheid om de inhoud te verplaatsen naar een pijplijnservice die wordt uitgevoerd op een Adobe I/O die zich buiten de AEM runtime bevindt.

>[!NOTE]
>
>Lees [Distribution](/help/core-concepts/architecture.md#content-distribution) voor meer informatie.

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

### Snel publiceren/publiceren - Gepland {#publish-unpublish} publiceren

Deze standaard AEM functies voor de auteurs veranderen niet met AEM Cloud Service.

### Aan en uit Tijd - de Configuratie van de trekker {#on-and-off-times-trigger-configuration}

De extra mogelijkheden van **On Tijd** en **Uit Tijd** zijn beschikbaar bij [Basislusje van Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Om de automatische replicatie voor dit te realiseren moet u **Auto Replicate** in [OSGi configuratie](/help/implementing/deploying/configuring-osgi.md) **On Off Configuratie** toelaten:

![Configuratie van OSGi bij activering](/help/operations/assets/replication-on-off-trigger.png)

### Boomactivering {#tree-activation}

Een boomactivering uitvoeren:

1. Navigeer in het menu AEM Start naar **Extra > Implementatie > Distributie**
2. Selecteer de kaart **forwardPublisher**
3. Eenmaal in de UI van de forwardPublisher-webconsole, **selecteer Distribute**

   ![](assets/distribute.png "DistributeDistribute")
4. Selecteer het pad in de padbrowser en kies een knooppunt, structuur of verwijder het pad naar wens en selecteer **Verzenden**

### Workflow {#publish-content-tree-workflow} publiceren in inhoudsstructuur

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
* `agentId` (tekenreekswaarde, standaardwaarde betekent dat alle ingeschakelde agents worden gebruikt). Men adviseert om over agentId uitdrukkelijk te zijn; Stel bijvoorbeeld de waarde in: publish
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

## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de Auteur AEM:

1. Navigeer in het menu AEM Start naar **Extra > Implementatie > Distributie**
2. Selecteer de kaart **forwardPublisher**
   ![](assets/status.png "StatusStatus")
3. Controleer de wachtrijstatus die groen moet zijn
4. U kunt de verbinding met de replicatieservice testen
5. Selecteer het tabblad **Logs** waarmee de geschiedenis van inhoudspublicaties wordt weergegeven

![](assets/logs.png "LogsLogs")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM-publicatieservice.
In dat geval moeten de rijen worden herzien om te bepalen welke punten de annulering van de publicatie hebben veroorzaakt. Door op een rij te klikken die een rode status toont, zou de rij met hangende punten verschijnen, waarvan enige of alle punten kunnen worden ontruimd indien nodig.
