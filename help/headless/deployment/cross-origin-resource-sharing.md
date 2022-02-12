---
title: Configuratie voor het delen van bronnen van verschillende oorsprong (CORS) met AEM headless
description: Met CORS (Cross-Origin Resource Sharing) van Adobe Experience Manager kunnen webtoepassingen zonder kop aanroepen naar AEM uitvoeren. Een configuratie CORS is nodig om toegang tot het eindpunt toe te laten GraphQL.
feature: GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Configuratie voor het delen van bronnen tussen verschillende bronnen (CORS)

>[!NOTE]
>
>Voor een gedetailleerd overzicht van het beleid voor het delen van bronnen in AEM zie [Werken met het delen van bronnen tussen verschillende bronnen (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html#understand-cross-origin-resource-sharing-(cors)).

Om tot het eindpunt toegang te hebben GraphQL, moet een beleid CORS worden gevormd en aan een AEM Project worden toegevoegd dat is [geïmplementeerd op AEM via Cloud Manager](/help/implementing/cloud-manager/deploy-code.md). Dit wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor het gewenste eindpunt (s) toe te voegen. Meerdere CORS-configuraties kunnen worden gemaakt en geïmplementeerd in verschillende omgevingen. Voorbeelden vindt u in het dialoogvenster [WKND-naslagsite](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)

De CORS-configuratie moet een vertrouwde website-oorsprong opgeven `alloworigin` of `alloworiginregexp` waarvoor toegang moet worden verleend.

Het configuratiebestand moet de volgende naam hebben: `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` waar `appname` geeft de naam van uw toepassing weer.

Bijvoorbeeld, om toegang tot het eindpunt te verlenen GraphQL `/content/cq:graphql/wknd/endpoint` en voortgeduurde vragen eindpunt voor `https://my.domain` u kunt gebruiken:

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

Als u een ijdelingspad voor het eindpunt hebt gevormd, kunt u het binnen ook gebruiken `allowedpaths`.


