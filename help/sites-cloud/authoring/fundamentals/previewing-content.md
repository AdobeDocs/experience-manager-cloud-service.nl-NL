---
title: Inhoud voorvertonen
description: Leer hoe u de AEM Preview Service kunt gebruiken om inhoud voor te vertonen voordat u live gaat.
source-git-commit: 9b4ac173c55380cbc06de64677470818aa801df4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# Inhoud voorvertonen {#previewing-content}

>[!NOTE]
>
>De functie Voorvertoning maakt deel uit van de release 2021.5.0 en wordt in de komende weken geleidelijk uitgevoerd.

AEM biedt een Sites Preview-service waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en die openbaar beschikbaar is.

Het vergemakkelijkt het voorvertonen van paginaervaringen die anders niet zichtbaar zouden zijn vanuit de auteursomgeving, zoals paginaovergangen en andere alleen inhoud aan de publiczijde.

## Te voorvertonen inhoud publiceren {#publishing-content-to-preview}

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

