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

* Op documenten gebaseerde inhoud - Zie [Sectie Publiceren](/help/edge/docs/authoring.md) van de documentatie bij Edge Delivery Services.
* AEM inhoud - Zie de onderstaande details.

## Stroom publiceren vanuit AEM {#publishing-flow}

Wanneer u de Universal Editor gebruikt om AEM inhoud te schrijven, kunt u alleen publiceren als u op de knop **Publiceren** in de Universal Editor. Zie het document [Inhoud publiceren met de Universal Editor.](/help/sites-cloud/authoring/universal-editor/publishing.md)

De informatiestroom bij publicatie ziet er als volgt uit. Zodra de auteur begint met de publicatie, is deze stroom automatisch en wordt deze hier ter informatie weergegeven.

>[!NOTE]
>
>Per dag zijn maximaal 5000 paden toegestaan die zijn gepubliceerd vanuit de ontwerpinterface of via workflows. Integraties die werklasten voor bulkpublicaties maken, worden niet ondersteund. Als uw project meer capaciteit vereist, gelieve voor te stellen het voor [VIP](https://www.aem.live/vip/intake).

![De stroom van informatie wanneer het publiceren van AEM aan Edge Delivery Services](assets/publishing-flow.png)

1. De auteur van de inhoud publiceert AEM inhoud in de Universal Editor.
1. Een publicatiegebeurtenis wordt geduwd aan de pijpleidingsrij van de Adobe.
1. De Edge Delivery Services publiceren de dienst door:sturen de relevante gebeurtenissen aan Edge Delivery Services admin API.
1. De Levering van de rand trekt en neemt semantische HTML van AEM auteur op.
1. AEM wordt bijgewerkt met publicatiestatus.

>[!NOTE]
>
>Standaard is de API voor beheer van Edge Delivery Services niet beveiligd en kan deze worden gebruikt om documenten zonder verificatie te publiceren of de publicatie ervan ongedaan te maken. Voor het configureren van verificatie voor de API voor beheer, zoals beschreven in [Verificatie voor auteurs configureren](https://www.aem.live/docs/authentication-setup-authoring)moet uw project voorzien zijn van een API_KEY, die toegang tot de publicatieservice verleent. [Neem contact op met het team Adobe voor Slack](/help/edge/docs/slack.md) ter begeleiding.

