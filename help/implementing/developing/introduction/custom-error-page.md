---
title: Aangepaste foutpagina's
description: AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten, die kan worden aangepast.
exl-id: b74c65d1-8ef5-4ad4-8255-8187f3b1d84c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Foutpagina&#39;s aanpassen {#customizing-error-pages}

AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten, bijvoorbeeld door het volgende weer te geven:

![Standaardfoutbericht](assets/error-message-standard.png)

Als u op fouten wilt reageren, biedt AEM een `404.jsp` script onder `/libs/sling/servlet/errorhandler`.

>[!TIP]
>
>Omdat AEM gebaseerd is op Apache Sling, is meer informatie beschikbaar [in de Apache-documentatie voor foutafhandeling.](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>Op een instantie van de auteur [CQ WCM-foutopsporingsfilter](/help/implementing/deploying/configuring-osgi.md) is standaard ingeschakeld. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een publicatie-instantie is CQ WCM Debug Filter **altijd** uitgeschakeld (zelfs als geconfigureerd als ingeschakeld).

## Hoe te om Pagina&#39;s aan te passen die door de Handler van de Fout worden getoond {#how-to-customize-pages-shown-by-the-error-handler}

U kunt uw eigen scripts ontwikkelen om de pagina&#39;s aan te passen die door de fouthandler worden weergegeven wanneer een fout optreedt. Om dit te doen gebruikt u [AEM standaardbedekkingsmechanisme](/help/implementing/developing/introduction/overlays.md) zodat uw aangepaste pagina&#39;s onder `/apps` en bedekken de standaardpagina&#39;s die onder zijn `/libs`.

1. Kopieer het standaardscript of de standaardscripts in de gegevensopslagruimte:

   * Van `/libs/sling/servlet/errorhandler/`
   * tot `/apps/sling/servlet/errorhandler/`

   Het doelpad bestaat niet standaard. U moet het dus maken wanneer u dit voor het eerst doet.

1. Navigeren naar `/apps/sling/servlet/errorhandler`. Hier kunt u:

   * bewerk het juiste bestaande script om de vereiste informatie op te geven. of
   * Maak en bewerk een nieuw script voor de vereiste code.

1. Sla de wijzigingen op en test u deze.

>[!CAUTION]
>
>De `404.jsp` het script is specifiek ontworpen om rekening te houden met AEM verificatie, met name om systeemaanmelding mogelijk te maken in het geval van deze fouten.
>
>Daarom zou de vervanging van dit manuscript met grote voorzichtigheid moeten worden gedaan.

### De reactie op HTTP 500-fouten aanpassen {#customizing-the-response-to-http-errors}

De HTTP [500 Interne serverfout](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) Hiermee wordt een serverfout aangegeven, zoals de server die een onverwachte voorwaarde tegenkomt waardoor deze de aanvraag niet heeft kunnen uitvoeren.

Wanneer de verzoekverwerking in een uitzondering resulteert, het kader Apache Sling (dat AEM wordt voortgebouwd op):

* Hiermee wordt de uitzondering geregistreerd
* En retourneert in de hoofdtekst van de respons:
   * De HTTP-responscode 500
   * De uitzonderingsstapeltracering

Door [aanpassen van de pagina&#39;s die worden weergegeven door de fouthandler](#how-to-customize-pages-shown-by-the-error-handler) a `500.jsp` kan worden gemaakt. Het wordt echter alleen gebruikt als `HttpServletResponse.sendError(500)` wordt uitgevoerd uitdrukkelijk; namelijk van een uitzonderingsvanger.

Anders is de antwoordcode ingesteld op 500, maar wordt de `500.jsp` script niet uitgevoerd.

Als u 500 fouten wilt afhandelen, moet de bestandsnaam van het script van de fouthandler gelijk zijn aan de uitzonderingsklasse (of superklasse). Om al dergelijke uitzonderingen te behandelen kunt u een manuscript tot stand brengen `/apps/sling/servlet/errorhandler/Throwable.jsp` of `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!NOTE]
>
>In AEM als Cloud Service, dient CDN een generische foutenpagina wanneer een 5XX fout van het achtereind wordt ontvangen. Als u de werkelijke reactie van de backend wilt laten doorgeven, moet u de volgende koptekst toevoegen aan de reactie: `x-aem-error-pass: true`.
>Dit werkt alleen voor reacties die afkomstig zijn van AEM of de laag Apache/Dispatcher. Andere onverwachte fouten die uit tussenliggende infrastructuurlagen komen zullen nog de generische foutenpagina tonen.

>[!CAUTION]
>
>Op een instantie van de auteur [CQ WCM-foutopsporingsfilter](/help/implementing/deploying/configuring-osgi.md) is standaard ingeschakeld. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een aangepaste fout-handler zijn reacties met code 500 nodig - dus de [CQ WCM-foutopsporingsfilter moet worden uitgeschakeld](/help/implementing/deploying/configuring-osgi.md). Dit zorgt ervoor dat reactiecode 500 is teruggekeerd, die beurtelings de correcte fout-manager van het Sling teweegbrengt.
>
>Voor een publicatie-instantie is CQ WCM Debug Filter **altijd** uitgeschakeld (zelfs als geconfigureerd als ingeschakeld).
