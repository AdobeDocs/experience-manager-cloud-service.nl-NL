---
title: Replicatie
description: Distributie en replicatie van probleemoplossing.
translation-type: tm+mt
source-git-commit: abb45225e880f3d08b9d26c29e243037564acef0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# Replicatie {#replication}

Adobe Experience Manager als Cloud Service gebruikt het [Verkopen vermogen van de Distributie](https://sling.apache.org/documentation/bundles/content-distribution.html) van de Inhoud om de inhoud te bewegen om aan een pijpleidingsdienst te herhalen die op Adobe I/O wordt uitgevoerd die buiten AEM runtime is.

>[!NOTE]
>
>Lees [Distributie](/help/core-concepts/architecture.md#content-distribution) voor meer informatie.

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

### Snel publiceren/publiceren - Gepland ongedaan maken/publiceren {#publish-unpublish}

Deze standaard AEM functies voor de auteurs veranderen niet met AEM Cloud Service.

### Aan- en uittijden - Configuratie activeren {#on-and-off-times-trigger-configuration}

De extra mogelijkheden van **Aan Tijd** en **Uit Tijd** zijn beschikbaar bij het [Basislusje van de Eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)van de Pagina.

Om de automatische replicatie voor dit te realiseren moet u **AutoReplicatie** in de configuratie [](/help/implementing/deploying/configuring-osgi.md) OSGi **bij de Configuratie** van de Trekker toelaten:

![Configuratie van OSGi bij activering](/help/operations/assets/replication-on-off-trigger.png)

### Boomactivering {#tree-activation}

Een boomactivering uitvoeren:

1. Navigeer in het menu AEM naar **Gereedschappen > Implementatie > Distributie**
2. De kaart **forwardPublisher selecteren**
3. Eenmaal in de UI van de forwardPublisher-webconsole **selecteert u Distribueren**

   ![](assets/distribute.png "DistributeDistribute")
4. Selecteer het pad in de padbrowser en kies een knooppunt, structuur of verwijder het gewenste pad en selecteer **Verzenden.**

## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de Auteur AEM:

1. Navigeer in het menu AEM naar **Gereedschappen > Implementatie > Distributie**
2. De kaart **forwardPublisher selecteren**
   ![](assets/status.png "StatusStatus")
3. Controleer de wachtrijstatus die groen moet zijn
4. U kunt de verbinding met de replicatieservice testen
5. Selecteer het tabblad **Logs** waarin de geschiedenis van publicaties met inhoud wordt weergegeven

![](assets/logs.png "LogsLogs")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM-publicatieservice.
In dat geval moeten de rijen worden herzien om te bepalen welke punten de annulering van de publicatie hebben veroorzaakt. Door op een rij te klikken die een rode status toont, zou de rij met hangende punten verschijnen, waarvan enige of alle punten kunnen worden ontruimd indien nodig.
