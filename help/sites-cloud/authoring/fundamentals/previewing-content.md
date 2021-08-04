---
title: Inhoud voorvertonen
description: Leer hoe u de AEM Preview Service kunt gebruiken om inhoud voor te vertonen voordat u live gaat.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 78c5649c6b9c04cb459f5730161affeb452c916c
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Inhoud voorvertonen {#previewing-content}

>[!NOTE]
>
>Om de voorproefeigenschap op milieu&#39;s toe te laten die vóór 3 Augustus, 2021 worden gecreeerd, zorg ervoor het milieu bij AEM versie 2021.05.5368.20210529T101701Z of hoger is en dan een klant-in werking gestelde pijpleiding.

AEM biedt een Sites Preview-service waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en die openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van paginaervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving, zoals paginaovergangen en andere alleen inhoud aan de publiczijde.

Lees ook [toegang tot de voorvertoningsservice](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Inhoud publiceren voor voorvertoning {#publishing-content-to-preview}

U kunt inhoud aan de Dienst van de Voorproef publiceren door Beheerde Publicatie UI als volgt te gebruiken:

1. Selecteer de pagina of pagina&#39;s die u wilt verzenden voor voorvertoning in de siteconsole en klik op de knop **Publicatie beheren**
1. Selecteer **Voorvertoning** als doel in de volgende wizard

   ![beheerde publicatie](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klik **Volgende**, en dan **Publish** om te bevestigen.

1. In een dialoogvenster worden de URL&#39;s weergegeven voor toegang tot de inhoud in de voorbeeldomgeving.

   Als u de inhoud van de voorvertoning wilt zien, kunt u **preview** ook toevoegen aan de publicatie-URL van uw productieexemplaar.

   De URL moet als volgt worden samengesteld:

   ```
   https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
   ```

Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over hoe u de URL&#39;s voor uw omgevingen kunt ophalen.

De inhoud kan ook worden gepubliceerd aan voorproef door een [Publish Inhoudsboom Werkschema](/help/operations/replication.md#publish-content-tree-workflow) met de agentId parameter te gebruiken die aan voorproef wordt geplaatst of door [replicatie API](/help/operations/replication.md#replication-api) met een AgentFilter te gebruiken voor voorproef wordt gevormd.

## OSGi-instellingen configureren voor de voorbeeldreeks {#configuring-osgi-settings-for-the-preview-tier}

De waarden van de OSGI-eigenschap van de voorvertoningslaag worden overgenomen van de publicatielijst, maar de waarden van de voorvertoningslaag kunnen worden onderscheiden van de publicatielijst met behulp van omgevingsspecifieke waarden die de parameter service instellen met de waarde &#39;preview&#39;. Neem het voorbeeld hieronder van een bezit OSGI dat URL van een integratieeindpunt bepaalt:

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

Voor meer informatie, zie [deze sectie](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) van de OSGi configuratiedocumentatie.

## Foutopsporingsvoorbeeld met de ontwikkelaarsconsole {#debugging-preview-using-the-developer-console}

Voer de volgende stappen uit om fouten op te sporen in de voorvertoningslaag met de Developer Console:

* Selecteer **— All Preview —** in de [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) of een productieomgeving die **prev** in zijn naam bevat
* De relevante informatie voor de voorvertoning genereren
Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over hoe u de URL&#39;s voor uw omgevingen kunt ophalen.
