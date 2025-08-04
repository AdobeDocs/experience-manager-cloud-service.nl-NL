---
title: Edge Delivery Services integreren met door Adobe beheerde CDN in Cloud Manager
description: null
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 2d2a206fea14d7e786a98e848bc2f2592ac65429
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Edge Delivery Services integreren met door Adobe beheerde CDN in Cloud Manager {#integrate-adbe-cdn-with-edservices-in-cm}

Adobe Managed CDN (AMC-D) kan op een native manier worden geïntegreerd met Edge Delivery Services, zodat u beschikt over uitstekende, wereldwijd verspreide ervaringen voor Adobe Experience Manager (AEM)-sites.

Samen bieden ze u de volgende voordelen:

* Een kant-en-klare CDN die door Adobe wordt beheerd.
* Een moderne rand-levering laag die verzoeken versnelt, caching optimaliseert, en tegen gemeenschappelijke aanvallen beschermt.
* Een verenigde Cloud Manager-workflow voor domeinbeheer, SSL-certificaten en door pijpleidingen gestuurde implementaties.

<!--
Adobe's Edge Delivery Services (EDS) can take advantage of an Adobe managed CDN. EDS is a framework that optimizes website delivery for speed, simplicity, and scalability by pushing content closer to the user through edge nodes. It is not a replacement for a CDN, but rather a way to enhance content delivery, especially when you use the Adobe managed CDN. It offers you the following benefits:

* Adobe-Managed CDN: EDS can use an Adobe-managed CDN, offering features like self-service CDN management and automatic certificate renewal. 
* EDS and AEM: EDS is a feature of AEM as a Cloud Service and works alongside the AEM authoring environment. 
* Performance enhancement: EDS, in conjunction with an Adobe Managed CDN, improves website performance by caching content at edge locations closer to users, reducing latency. 
* Flexibility: EDS provides flexibility in content delivery, allowing your organization to choose between the Adobe-managed CDN or their own CDN setup, based on their needs and existing infrastructure. 
Self-Service CDN Management:
Adobe-managed CDN within EDS enables self-service configuration and management tasks like SSL certificate setup. 
 
Use Cases:
EDS with CDN integration is beneficial for various scenarios, including e-commerce storefronts and websites requiring high performance and scalability. -->

## Edge Delivery Services-implementatieopties in door Adobe beheerde CDN in Cloud Manager {#deployment-options}

Dit onderwerp verklaart de twee manieren u Edge Delivery Services op Adobe Geleide CDN in Cloud Manager kunt opstellen en, enkel even belangrijk, helpt u beslissen welke optie voor uw gebruiksgeval het best is.

Edge Delivery Services kan worden ingesteld op basis van een van de volgende twee opties. Elk heeft verschillende mogelijkheden.

|  | Implementatieoptie | Toetsdocument | Capaciteit | Best voor |
| --- | --- | --- | --- | --- |
| Optie 1 | *met* een bestaand milieu van AEM as a Cloud Service (AEMaaCS) | [ opstelling een volmacht van een bestaand milieu ](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment) | Config Pipeline is doorgaans beschikbaar voor AEMaaCS-omgevingen | Teams die al Sites uitvoeren in Cloud Manager en die een snelle prestatieverhoging met lage risico&#39;s willen. |
| Optie 2 | *zonder* een bestaand milieu AEMaaCS; gekend als standalone &quot;milieu van Edge.&quot; | [ Opstelling een plaats van Edge Delivery zonder een bestaand milieu ](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment) | Config Pipeline is momenteel alleen beschikbaar voor Edge-omgevingen via het beperkte Beta-programma.<br> zie [ toevoegen de Pijpleiding van Edge Delivery Config ](help/implementing/cloud-manager/release-notes/current.md##add-eds-pipeline). | Nieuwe builds of migraties die de volledige Edge Delivery architectuur en granulaire routering willen omarmen. |

<!-- Ultimately this URL above will need to be updated on GA -->

| Optie | Samenvatting | Best voor | Belangrijke documenten |
| --- | --- | --- | --- |
| Door Adobe beheerde CDN-proxy | Met Adobe Managed CDN wordt een bestaande AEM Sites-omgeving voorafgegaan. Uw huidige pijpleiding van Plaatsen blijft de &quot;oorsprong,&quot;terwijl AMC-D randcaching en de beëindiging van TLS behandelt. | Teams die al Sites uitvoeren in Cloud Manager en die een snelle prestatieverhoging met lage risico&#39;s willen. | Een AMC-D-proxy instellen |
| Config Pipeline met originSelectors | Een speciale Edge Delivery Config Pipeline publiceert statische en dynamische inhoud rechtstreeks aan de rand. `originSelectors` routeverkeer tussen AMC-D en uw AEM-auteur-/publicatielagen. | Nieuwe builds of migraties die de volledige Edge Delivery architectuur en granulaire routering willen omarmen. | De Edge Delivery-pijplijn configureren |

>[!TIP]
>
>Onzeker welk pad moet worden gekozen? Zie [ kiezen een plaatsingsmodel ](#choose-deployment-model) hieronder voor besluitvormingsrichtlijnen.

## Kies een implementatiemodel {#choose-deployment-model}

Beide modellen kunnen naast elkaar bestaan binnen hetzelfde Cloud Manager-programma, waardoor gefaseerde migratie mogelijk is.

| Als u... | Gebruik vervolgens... |
| :--- | :--- |
| Hebt u een snelle, minimale implementatie nodig en host Sites al in Cloud Manager | AMC-D-proxy |
| Plan om inhoud voor Edge Delivery te herstructureren, of wil het fijnkorrelige verpletteren tussen veelvoudige oorsprong | Edge Deliver Pipeline + `originSelectors` configureren |

## Vereisten {#prerequisites}

1. Aan boord van uw site in Cloud Manager
&#x200B;- Vereist voor beide modellen. Volg een AEM-site aan boord.

2. Kies voor uw eigen git (BYOG) (optioneel)
&#x200B;- Als u sitecode buiten Adobe Git opslaat, moet u BYOG inboarding voltooien.

3. Edge Delivery-licentie
&#x200B;- Controleer of er een licentie voor uw programma is voor Edge Delivery Services.


