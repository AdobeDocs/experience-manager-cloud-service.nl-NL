---
title: Replicatie
description: Distributie en replicatie van probleemoplossing.
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 3%

---


# Replicatie {#replication}

Adobe Experience Manager als Cloud Service gebruikt de [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) mogelijkheid om de inhoud te verplaatsen naar een pijplijnservice die wordt uitgevoerd op een Adobe I/O die buiten de AEM-runtime valt.

>[!NOTE]
>
> Lees [Distributie](/help/core-concepts/architecture.md#content-distribution) voor meer informatie.

## Methoden voor het publiceren van inhoud {#methods-of-publishing-content}

### Snel publiceren/publiceren - Gepland ongedaan maken/publiceren {#publish-unpublish}

Deze standaard AEM-functies voor de auteurs veranderen niet met AEM Cloud Service.

### Boomactivering {#tree-activation}

Een boomactivering uitvoeren:

1. Navigeer in het menu Start van AEM naar **Extra > Implementatie > Distributie**
2. De kaart **forwardPublisher selecteren**
3. Eenmaal in de UI van de forwardPublisher-webconsole **selecteert u Distribueren**
   ![](assets/distribute.png "DistributeDistribute")
4. Selecteer het pad in de padbrowser en kies een knooppunt, structuur of verwijder het gewenste pad en selecteer **Verzenden.**

## Problemen oplossen {#troubleshooting}

Om replicatie problemen op te lossen, navigeer aan de Queuws van de Replicatie in het Web UI van de Dienst van de Auteur AEM:

1. Navigeer in het menu Start van AEM naar **Extra > Implementatie > Distributie**
2. De kaart **forwardPublisher selecteren**
   ![](assets/status.png "StatusStatus")
3. Controleer de wachtrijstatus die groen moet zijn
4. U kunt de verbinding met de replicatieservice testen
5. Selecteer het tabblad **Logs** waarin de geschiedenis van publicaties met inhoud wordt weergegeven

![](assets/logs.png "LogsLogs")

Als de inhoud niet kon worden gepubliceerd, wordt de volledige publicatie teruggezet van de AEM-publicatieservice.
In dat geval moeten de rijen worden herzien om te bepalen welke punten de annulering van de publicatie hebben veroorzaakt. Door op een rij te klikken die een rode status toont, zou de rij met hangende punten verschijnen, waarvan enige of alle punten kunnen worden ontruimd indien nodig.
