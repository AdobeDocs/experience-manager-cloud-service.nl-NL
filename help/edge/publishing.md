---
title: Inhoud voor Edge Delivery Services publiceren
description: Leer hoe het publiceren van inhoud met Edge Delivery Services werkt en hoe te om AEM inhoud met Edge Delivery Services te publiceren.
feature: Edge Delivery Services
exl-id: 32fbb144-9175-47a9-bb5a-ca15f3fcd2d8
source-git-commit: 58d85886ef04b548c09e3ef9308fe596dd3eda38
workflow-type: tm+mt
source-wordcount: '228'
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
>Per dag zijn maximaal 5000 paden toegestaan die zijn gepubliceerd vanuit de ontwerpinterface of via workflows. Integraties die werklasten voor bulkpublicaties maken, worden niet ondersteund.

![De stroom van informatie wanneer het publiceren van AEM aan Edge Delivery Services](assets/publishing-flow.png)

1. De auteur van de inhoud publiceert AEM inhoud in de Universal Editor.
1. Een publicatiegebeurtenis wordt geduwd aan de Rij van de Pijpleiding van de Adobe.
1. De Edge Delivery Publish Service stuurt de relevante gebeurtenissen door naar de Edge Delivery Admin API.
1. De Levering van de rand trekt en neemt semantische HTML van AEM Auteur op.
1. AEM wordt bijgewerkt met publicatiestatus.

## Aan de slag {#how-to-get-started}

Neem contact op met uw Adobe voor toegang tot deze functie.
