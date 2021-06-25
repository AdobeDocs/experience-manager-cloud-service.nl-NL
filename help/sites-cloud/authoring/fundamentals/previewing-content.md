---
title: Inhoud voorvertonen
description: Leer hoe u de AEM Preview Service kunt gebruiken om inhoud voor te vertonen voordat u live gaat.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 53a3fb91dcf093d55e80c7dfcdef3a7855731841
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Inhoud voorvertonen {#previewing-content}

>[!NOTE]
>
>De functie Voorvertoning maakt deel uit van de release 2021.5.0 en wordt in de komende weken geleidelijk uitgevoerd.

AEM biedt een Sites Preview-service waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en die openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van paginaervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving, zoals paginaovergangen en andere alleen inhoud aan de publiczijde.

## Inhoud publiceren voor voorvertoning {#publishing-content-to-preview}

U kunt inhoud aan de Dienst van de Voorproef publiceren door Beheerde Publicatie UI als volgt te gebruiken:

1. Selecteer de pagina of pagina&#39;s die u wilt verzenden voor voorvertoning in de siteconsole en klik op de knop **Publicatie beheren**
1. Selecteer **Voorvertoning** als doel in de volgende wizard

   ![beheerde publicatie](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klik **Volgende**, en dan **Publish** om te bevestigen.

Zie de voorproefinhoud, voeg **voorproef** aan toe publiceren URL van uw productie instantie. De URL moet als volgt worden samengesteld:

```
https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
```

Zie [Uw omgevingen beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) voor meer informatie over het ophalen van de URL&#39;s voor uw omgevingen.

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
Zie [Uw omgevingen beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) voor meer informatie over het ophalen van de URL&#39;s voor uw omgevingen.
