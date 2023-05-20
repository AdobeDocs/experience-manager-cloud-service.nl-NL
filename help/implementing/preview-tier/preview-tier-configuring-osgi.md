---
title: OSGi-instellingen configureren voor de voorbeeldreeks
description: Leer hoe u de AEM voorvertoningsservice configureert voor een voorvertoning van inhoud voordat u live gaat.
exl-id: 1200bb17-8a3c-4e41-85f4-ed2334b61f69
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# OSGi-instellingen configureren voor de voorbeeldreeks {#configure-osgi-preview-tier}

AEM biedt een Sites Preview-service waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van een reeks ervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving. Paginaovergangen, ervaringsfragmenten en andere alleen-inhoud aan de publiczijde.

De OSGi-eigenschapswaarden van de voorvertoningslaag worden overgenomen van de publicatielijst. De waarden van de voorvertoningslaag kunnen echter afwijken van die van de publicatielaag door het instellen van de optie `service` parameter voor de waarde `preview`.

>[!NOTE]
>
>Meer informatie over de voorvertoningsomgevingen vindt u in het document [Omgevingen beheren.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Het vormen van de Montages OSGi voor de Rij van de Voorproef {#configuring-osgi-settings-for-the-preview-tier}

Het volgende voorbeeld van een bezit OSGi bepaalt URL van een integratieeindpunt.

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
