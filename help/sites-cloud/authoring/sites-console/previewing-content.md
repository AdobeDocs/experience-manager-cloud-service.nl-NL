---
title: Inhoud voorvertonen
description: Leer hoe u de AEM voorvertoningsservice gebruikt om inhoud voor te vertonen voordat u live gaat.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


# Inhoud voorvertonen {#previewing-content}

AEM biedt een Sites Preview-service, waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van paginaervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving, zoals paginaovergangen en andere alleen inhoud aan de publiczijde.

>[!NOTE]
>
>Als de inhoud *gepubliceerd* In de voorvertoningsomgeving is de URL toegankelijk (dus hebt u geen toegang tot AEM nodig).

Zie voor meer informatie over de voorvertoningsomgevingen [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Inhoud publiceren voor voorvertoning {#publishing-content-to-preview}

U kunt inhoud naar de voorvertoningsservice publiceren met de opdracht **Beheerde publicatie** UI.

1. Selecteer in de Sites-console de pagina of pagina&#39;s die u wilt verzenden voor de voorvertoning en klik op de knop **Publicatie beheren** knop.
1. Selecteer in de volgende wizard de optie **Voorvertoning** als de bestemming.

   ![beheerde publicatie](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klikken **Volgende** en vervolgens **Publiceren** ter bevestiging.

1. In een dialoogvenster worden de URL&#39;s weergegeven voor toegang tot de inhoud in de voorvertoningsomgeving.

   >[!NOTE]
   >
   >Als de inhoud *gepubliceerd* In de voorvertoningsomgeving is de URL toegankelijk (dus hebt u geen toegang tot AEM nodig).

Als u de in de wizard weergegeven URL&#39;s wilt gebruiken om de inhoud van de voorvertoning weer te geven, kunt u ook een voorvoegsel toevoegen `preview-` naar de publicatie-URL van uw productieexemplaar.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Zie het document [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over het ophalen van de URL&#39;s voor uw omgevingen.

Inhoud kan ook voor voorvertoning worden gepubliceerd met een [workflow voor publicatiestructuur](/help/operations/replication.md#publish-content-tree-workflow) met de `agentId` parameter ingesteld op `preview` of door [replicAPI](/help/operations/replication.md#replication-api) met een `AgentFilter` geconfigureerd voor voorvertoning.

## Publicatie van inhoud in voorvertoning ongedaan maken {#unpublishing-content-from-preview}

Publiceren van inhoud vanuit uw **Voorvertoning** milieu is in wezen hetzelfde proces als [publicatie van pagina&#39;s ongedaan maken](/help/sites-cloud/authoring/sites-console/publishing-pages.md#unpublishing-pages) van de **Publiceren** milieu.

Het enige verschil is dat u de **Doel** te worden **Voorvertoning**.
