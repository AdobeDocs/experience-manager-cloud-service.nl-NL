---
title: Het gebruiken van GrahiQL winde in AEM
description: Leer hoe u de GraphiQL IDE in Adobe Experience Manager gebruikt.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 3%

---

# GraphiQL IDE gebruiken {#graphiql-ide}

Tenuitvoerlegging van de norm [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE is beschikbaar voor gebruik met AEM GraphQL. Dit kan [geïnstalleerd met AEM](#installing-graphiql-ide).

>[!NOTE]
>
>GraphiQL is gebonden het globale eindpunt (en werkt niet met andere eindpunten voor specifieke configuraties van Plaatsen).

Met het gereedschap GraphiQL kunt u query&#39;s rechtstreeks invoeren, testen en debuggen. GraphiQL biedt ook eenvoudige toegang tot de documentatie, waardoor u gemakkelijk kunt leren welke methoden beschikbaar zijn en begrijpen.

Bijvoorbeeld:

* `http://localhost:4502/content/graphiql.html`

Dit biedt functies zoals syntaxismarkering, automatisch aanvullen, automatisch voorstellen, samen met een geschiedenis en online documentatie:

![GraphiQL Interface](assets/cfm-graphiql-interface.png "GraphiQL Interface")

## De AEM GraphiQL IDE installeren {#installing-graphiql-ide}

GrahiQL winde is een ontwikkelingshulpmiddel en nodig slechts op laag-vlakke milieu&#39;s zoals een ontwikkeling of lokale instantie. Daarom is het niet opgenomen in het AEM-project, maar als een afzonderlijk pakket dat op ad-hocbasis kan worden geïnstalleerd.

1. Ga naar de **[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)** > **AEM as a Cloud Service**.
1. Zoek naar &quot;GraphiQL&quot; (zorg ervoor dat u de **i** in **GraphiQL**.
1. Download de nieuwste **GraphiQL Content Package v.x.x.x**
1. Van de **AEM starten** menu navigeren naar **Gereedschappen** > **Implementatie** > **Pakketten**.
1. Klikken **Pakket uploaden** en kiest u het pakket dat u in de vorige stap hebt gedownload. Klikken **Installeren** om het pakket te installeren.
