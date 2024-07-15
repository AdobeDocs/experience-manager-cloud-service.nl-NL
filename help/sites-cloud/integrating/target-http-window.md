---
title: Adobe AEM HTTP-doelvenster
description: Adobe AEM HTTP-doelvenster
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---


# Inleiding {#introduction}

Deze pagina beschrijft de configureerbare parameters huidig in de Adobe AEM het Venster van HTTP van het Doel.

## Parameters {#parameters}

![ het Venster van HTTP van het Doel ](assets/httpwindow.png " Venster van HTTP van het Doel ")

Het venster bevat de volgende configureerbare parameters:

| Parameter | Beschrijving |
|---|---|
| Adobe Target API-URL | De URL van de Adobe Target API. |
| Absolute URL inschakelen | Hiermee wordt bepaald of het hostgedeelte van de URL of de volledige URL wordt gebruikt. Schakel het selectievakje in als u de volledige (niet-verkorte) URL wilt gebruiken. Het selectievakje is standaard uitgeschakeld. |
| Time-out verbinding | De time-out (in milliseconden) totdat een verbinding tot stand is gebracht. De standaardwaarde is 60000 milliseconden. Een waarde 0 wordt geïnterpreteerd als een oneindige time-out. |
| Time-out socket | De time-out (in milliseconden) die moet worden gewacht op gegevens of een maximale periode van inactiviteit tussen twee opeenvolgende gegevenspakketten. De standaardwaarde is 30000 milliseconden. |
| Adobe Target Recommendations URL Regex Token vervangen | Bepaalt het token in de URL van het eindpunt van Adobe Target dat moet worden vervangen om naar de URL van de API voor aanbevelingen van het doel te wijzen. |
| Adobe Target Recommendations URL Replace with Token | Vervanging voor de regex die in de bovenstaande parameter wordt beschreven, zodat zal resulterende URL naar het doel beveelt API richten. |
