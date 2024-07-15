---
title: Inhoud voor Edge Delivery Services publiceren
description: Leer hoe het publiceren van inhoud met Edge Delivery Services werkt en hoe te om AEM inhoud met Edge Delivery Services te publiceren.
feature: Edge Delivery Services
exl-id: 32fbb144-9175-47a9-bb5a-ca15f3fcd2d8
role: User
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Inhoud voor Edge Delivery Services publiceren {#publishing-edge}

Met Edge Delivery Services verloopt het publiceren van inhoud naadloos, ongeacht de inhoudsbron:

* Op document-gebaseerde inhoud - gelieve te zien {de sectie van 0} Publish ](/help/edge/docs/authoring.md) van de documentatie van Edge Delivery Services.[
* AEM inhoud - Zie de onderstaande details.

## Stroom publiceren vanuit AEM {#publishing-flow}

Wanneer het gebruiken van de Universele Redacteur aan auteur AEM inhoud, is het publiceren zo eenvoudig zoals het klikken van de **Publish** knoop in de Universele Redacteur. Gelieve te zien het document [ het Publiceren Inhoud met de Universele Redacteur.](/help/sites-cloud/authoring/universal-editor/publishing.md)

De informatiestroom bij publicatie ziet er als volgt uit. Zodra de auteur begint met de publicatie, is deze stroom automatisch en wordt deze hier ter informatie weergegeven.

>[!NOTE]
>
>Per dag zijn maximaal 5000 paden toegestaan die zijn gepubliceerd vanuit de ontwerpinterface of via workflows. Integraties die werklasten voor bulkpublicaties maken, worden niet ondersteund. Als u project hogere capaciteit vereist, gelieve het voor het [ VIP Programma ](https://www.aem.live/vip/intake) voor te stellen.

![ de stroom van informatie wanneer het publiceren van AEM aan Edge Delivery Services ](assets/publishing-flow.png)

1. De auteur van de inhoud publiceert AEM inhoud in de Universal Editor.
1. Een publicatiegebeurtenis wordt geduwd aan de pijpleidingsrij van de Adobe.
1. De Edge Delivery Services publiceren de dienst door:sturen de relevante gebeurtenissen aan Edge Delivery Services admin API.
1. Edge Delivery trekt semantische HTML in van AEM auteur.
1. AEM wordt bijgewerkt met publicatiestatus.

>[!NOTE]
>
>Standaard is de API voor beheer van Edge Delivery Services niet beveiligd en kan deze worden gebruikt om documenten zonder verificatie te publiceren of de publicatie ervan ongedaan te maken. Om authentificatie voor admin API zoals die in [ wordt gedocumenteerd Vormende Authentificatie voor Auteurs ](https://www.aem.live/docs/authentication-setup-authoring) te vormen, moet uw project voorzien zijn van API_KEY, die toegang tot de publicatiedienst verleent. [ te bereiken gelieve uit aan het team van de Adobe op Slack ](/help/edge/docs/slack.md) voor begeleiding.

