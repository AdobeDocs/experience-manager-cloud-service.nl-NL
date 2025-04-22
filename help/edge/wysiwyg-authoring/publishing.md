---
title: Inhoud publiceren voor Edge Delivery Services
description: Leer hoe het publiceren van content werkt met Edge Delivery Services en hoe u AEM-inhoud publiceert met Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 32fbb144-9175-47a9-bb5a-ca15f3fcd2d8
role: User
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Inhoud publiceren voor Edge Delivery Services {#publishing-edge}

In Edge Delivery Services is het publiceren van inhoud naadloos, ongeacht uw inhoudsbron:

* Op document-gebaseerde inhoud - gelieve te zien [ publiceren sectie ](/help/edge/docs/authoring.md) van de documentatie van Edge Delivery Services.
* AEM-inhoud - Zie de onderstaande details.

## Stroom publiceren vanuit AEM {#publishing-flow}

Wanneer het gebruiken van de Universele Redacteur aan de inhoud van auteurAEM, is het publiceren zo eenvoudig zoals het klikken van de **publiceer** knoop in de Universele Redacteur. Gelieve te zien het document [ het Publiceren Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/publishing.md).

De informatiestroom bij publicatie ziet er als volgt uit. Zodra de auteur begint met de publicatie, is deze stroom automatisch en wordt deze hier ter informatie weergegeven.

>[!NOTE]
>
>Per dag zijn maximaal 5000 paden toegestaan die zijn gepubliceerd vanuit de ontwerpinterface of via workflows. Integraties die werklasten voor bulkpublicaties maken, worden niet ondersteund. Als u het project hogere capaciteit vereist, gelieve het voor het [ Programma van VIP ](https://www.aem.live/vip/intake) voor te stellen.

![ de stroom van informatie wanneer het publiceren van AEM aan Edge Delivery Services ](assets/publishing-flow.png)

1. De auteur van de inhoud publiceert AEM-inhoud in de Universal Editor.
1. Een publicatiegebeurtenis wordt geduwd aan de pijpleidingsrij van Adobe.
1. De Edge Delivery Services-publicatieservice stuurt de relevante gebeurtenissen door naar de Edge Delivery Services-API voor beheer.
1. Edge Delivery trekt semantische HTML aan en neemt deze in van de AEM-auteur.
1. AEM wordt bijgewerkt met publicatiestatus.

>[!NOTE]
>
>Standaard is de Edge Delivery Services-API voor beheer niet beveiligd en kan deze worden gebruikt om documenten zonder verificatie te publiceren of de publicatie ervan ongedaan te maken. Om authentificatie voor admin API zoals die in [ wordt gedocumenteerd Vormende Authentificatie voor Auteurs ](https://www.aem.live/docs/authentication-setup-authoring) te vormen, moet uw project voorzien zijn van API_KEY, die toegang tot de publicatiedienst verleent. [ te bereiken gelieve uit aan het team van Adobe op Slack ](/help/edge/docs/slack.md) voor begeleiding.

