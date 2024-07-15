---
title: Configuratie voor het delen van bronnen van verschillende oorsprong (CORS) met AEM headless
description: Met CORS (Cross-Origin Resource Sharing) van Adobe Experience Manager kunnen webtoepassingen zonder kop aanroepen naar AEM uitvoeren. Een configuratie CORS is nodig om toegang tot het eindpunt van GraphQL toe te laten.
feature: Headless, GraphQL API
exl-id: 426be9f9-f44a-4744-ac08-e64bb97308a0
solution: Experience Manager
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Configuratie voor het delen van bronnen tussen verschillende bronnen (CORS)

>[!CAUTION]
>
>Als [ caching in Dispatcher ](/help/headless/deployment/dispatcher-caching.md) dan is toegelaten is het filter CORS niet nodig, en zo kan deze sectie worden genegeerd.

>[!NOTE]
>
>Voor een gedetailleerd overzicht van het CORS middel delend beleid in AEM zie [ het Delen van het Middel van de Cross-Origin begrijpen (CORS) ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html#understand-cross-origin-resource-sharing-(cors)).

Om tot het eindpunt van GraphQL toegang te hebben, moet een beleid CORS worden gevormd en aan een AEM Project worden toegevoegd dat [ aan AEM via Cloud Manager ](/help/implementing/cloud-manager/deploy-code.md) wordt opgesteld. Dit wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor het gewenste eindpunt (s) toe te voegen. U kunt meerdere CORS-configuraties maken en implementeren in verschillende omgevingen. De voorbeelden kunnen in de [ plaats van de Verwijzing WKND ](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig) worden gevonden

In de CORS-configuratie moet een vertrouwde website-oorsprong `alloworigin` of `alloworiginregexp` worden opgegeven waarvoor toegang moet worden verleend.

Het configuratiebestand moet de volgende naam hebben: `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` waarbij `appname` de naam van de toepassing weergeeft.

Als u bijvoorbeeld toegang wilt verlenen tot het eindpunt `/content/cq:graphql/wknd/endpoint` van GraphQL en het eindpunt van aanhoudende query&#39;s voor `https://my.domain` , kunt u het volgende gebruiken:

```json
{
  "supportscredentials":false,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/cq:graphql/wknd/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Als u een ijkpad voor het eindpunt hebt geconfigureerd, kunt u dit ook gebruiken in `allowedpaths` .
