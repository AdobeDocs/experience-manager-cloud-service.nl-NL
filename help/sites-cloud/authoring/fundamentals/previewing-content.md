---
title: Inhoud voorvertonen
description: Leer hoe u de AEM voorvertoningsservice gebruikt om inhoud voor te vertonen voordat u live gaat.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: a9a2362903e8eec25393e2ceb307814e1a21f142
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


# Inhoud voorvertonen {#previewing-content}

AEM biedt een Sites Preview-service, waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van paginaervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving, zoals paginaovergangen en andere alleen inhoud aan de publiczijde.

>[!NOTE]
>
>Aangezien de inhoud ** aan het voorproefmilieu wordt gepubliceerd is het toegankelijk door URL (zo vereist geen toegang tot AEM).

Voor meer details over de voorproefmilieu&#39;s, zie [ Milieu&#39;s ](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) beheren.

## Inhoud publiceren voor voorvertoning {#publishing-content-to-preview}

U kunt inhoud aan de voorproefdienst publiceren door **Beheerde Publicatie** UI te gebruiken.

1. In de console van Plaatsen, selecteer de pagina of de pagina&#39;s u aan voorproef wilt verzenden en **klikken leidt Publicatie** knoop.
1. In de volgende tovenaar, uitgezochte **Voorproef** als bestemming.

   ![ beheerde publicatie ](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klik **daarna**, en dan **Publish** om te bevestigen.

1. In een dialoogvenster worden de URL&#39;s weergegeven voor toegang tot de inhoud in de voorvertoningsomgeving.

   >[!NOTE]
   >
   >Aangezien de inhoud ** aan het voorproefmilieu wordt gepubliceerd is het toegankelijk door URL (zo vereist geen toegang tot AEM).

Als u de URL&#39;s in de wizard wilt gebruiken om de inhoud van de voorvertoning weer te geven, kunt u `preview-` ook aan de publicatie-URL van de productieinstantie toevoegen.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Zie het document [ Leiden Milieu ](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over hoe terugwinning URLs voor uw milieu&#39;s.

De inhoud kan ook aan voorproef worden gepubliceerd door a [ te gebruiken publiceer inhoudsboomwerkschema ](/help/operations/replication.md#publish-content-tree-workflow) met de `agentId` parameter die aan `preview` wordt geplaatst of door [ replicatie API ](/help/operations/replication.md#replication-api) met `AgentFilter` te gebruiken voor voorproef wordt gevormd.

## Publicatie van inhoud in voorvertoning ongedaan maken {#unpublishing-content-from-preview}

Het ongedaan maken van inhoud van uw **milieu van de Voorproef** is fundamenteel het zelfde proces zoals [ unpublishing pagina&#39;s ](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages) van het **Publish** milieu.

Het enige verschil is dat u de **Bestemming** kunt selecteren om **Voorproef** te zijn.
