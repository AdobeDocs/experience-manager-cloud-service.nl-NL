---
title: Inhoud voorvertonen
description: Leer hoe u de AEM voorvertoningsservice gebruikt om inhoud voor te vertonen voordat u live gaat.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: dc55bd43641c03dd022a891c8b85569d9be28ebe
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---


# Inhoud voorvertonen {#previewing-content}

AEM biedt een Sites Preview-service, waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van paginaervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving, zoals paginaovergangen en andere alleen inhoud aan de publiczijde.

Meer informatie over de voorvertoningsomgevingen vindt u in het document [Omgevingen beheren.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>Het publiceren van een Fragment van de Ervaring aan Voorproef volgt eigenlijk de zelfde procedure zoals voor een pagina, hoewel van de console of de redacteur van de Fragmenten van de Ervaring.

## Inhoud publiceren voor voorvertoning {#publishing-content-to-preview}

U kunt inhoud naar de voorvertoningsservice publiceren met de opdracht **Beheerde publicatie** UI.

1. Selecteer in de Sites-console de pagina of pagina&#39;s die u wilt verzenden voor de voorvertoning en klik op de knop **Publicatie beheren** knop
1. Selecteer in de volgende wizard de optie **Voorvertoning** als bestemming

   ![beheerde publicatie](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klikken **Volgende** en vervolgens **Publiceren** ter bevestiging.

1. In een dialoogvenster worden de URL&#39;s weergegeven voor toegang tot de inhoud in de voorvertoningsomgeving.


Als u de in de wizard weergegeven URL&#39;s wilt gebruiken om de inhoud van de voorvertoning weer te geven, kunt u ook een voorvoegsel toevoegen `preview-` naar de publicatie-URL van uw productieexemplaar.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Zie het document [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over het ophalen van de URL&#39;s voor uw omgevingen.

Inhoud kan ook voor voorvertoning worden gepubliceerd met behulp van een [workflow voor publicatiestructuur](/help/operations/replication.md#publish-content-tree-workflow) met de `agentId` parameter ingesteld op `preview` of door [replicatie-API](/help/operations/replication.md#replication-api) met een `AgentFilter` geconfigureerd voor voorvertoning.

## Publicatie van inhoud in voorvertoning ongedaan maken {#unpublishing-content-from-preview}

Publiceren van inhoud vanuit uw **Voorvertoning** milieu is in wezen hetzelfde proces als [publicatie van pagina&#39;s ongedaan maken](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages) van de **Publiceren** milieu.

Het enige verschil is dat u de **Doel** te worden **Voorvertoning**.

## OSGi-instellingen configureren voor de voorbeeldreeks {#configuring-osgi-settings-for-the-preview-tier}

De OSGi-eigenschapswaarden van de voorvertoningslaag worden overgenomen van de publicatielijst. De waarden van de voorvertoningslaag kunnen echter afwijken van die van de publicatielaag door het instellen van de optie `service` parameter voor de waarde `preview`. Het volgende voorbeeld van een bezit OSGi bepaalt URL van een integratieeindpunt.

```
[
{
"name":"INTEGRATION_URL",
"type":"string",
"value":"http://s2.integrationvendor.com",
"service": "preview"
}
]
```

Zie voor meer informatie [deze sectie](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) van de OSGi-configuratiedocumentatie.

## Foutopsporingsvoorbeeld met de ontwikkelaarsconsole {#debugging-preview-using-the-developer-console}

Voer de volgende stappen uit om fouten op te sporen in de voorvertoningslaag met de Developer Console:

* In de [Ontwerpconsole](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools)Selecteer een van de **— Alle voorvertoningen —** of een productieomgeving die **prev** in zijn naam
* De relevante informatie voor de voorbeeldinstantie genereren Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over hoe u de URL&#39;s voor uw omgevingen kunt ophalen.
