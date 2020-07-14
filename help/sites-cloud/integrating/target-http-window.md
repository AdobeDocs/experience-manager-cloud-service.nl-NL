---
title: Adobe AEM Target HTTP-venster
description: 'Adobe AEM Target HTTP-venster '
translation-type: tm+mt
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---


# Inleiding {#introduction}

Op deze pagina vindt u een beschrijving van de configureerbare parameters in het HTTP-venster van Adobe AEM Target.

## Parameters {#parameters}

![Target HTTP](assets/httpwindow.png "WindowTarget HTTP Window")

Het venster bevat de volgende configureerbare parameters:

| Parameter | Beschrijving |
|---|---|
| Adobe Target API-URL | De URL van de Adobe Target API. |
| Absolute URL inschakelen | Hiermee wordt bepaald of het hostgedeelte van de URL of de volledige URL wordt gebruikt. Schakel het selectievakje in als u de volledige (niet-verkorte) URL wilt gebruiken. Het selectievakje is standaard uitgeschakeld. |
| Time-out verbinding | De time-out (in milliseconden) totdat een verbinding tot stand is gebracht. De standaardwaarde is 60000 milliseconden. Een waarde 0 wordt geïnterpreteerd als een oneindige time-out. |
| Time-out socket | De time-out (in milliseconden) die moet worden gewacht op gegevens of een maximale periode van inactiviteit tussen twee opeenvolgende gegevenspakketten. De standaardwaarde is 30000 milliseconden. |
| Adobe Target Recommendations URL Regex Token vervangen | Bepaalt het token in de URL van het Adobe Target-eindpunt dat moet worden vervangen om naar de URL van de Target-API voor aanbevelingen te verwijzen. |
| Adobe Target Recommendations URL Replace with Token | Vervanging voor de regex die in de bovenstaande parameter wordt beschreven, zodat de resulterende URL naar de API voor aanbevelingen van Target verwijst. |
