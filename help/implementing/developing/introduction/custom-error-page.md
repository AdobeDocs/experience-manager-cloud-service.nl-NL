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

![ Standaard foutenmelding ](assets/error-message-standard.png)

AEM biedt een `404.jsp` -script onder `/libs/sling/servlet/errorhandler` om op fouten te reageren.

>[!TIP]
>
>Omdat AEM op Apache Sling gebaseerd is, is de verdere informatie beschikbaar [ in de Apache fout behandelende documentatie.](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>Op een auteursinstantie, ](/help/implementing/deploying/configuring-osgi.md) wordt de Debug Filter van 0} CQ WCM toegelaten door gebrek. [ Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Op publiceer instantie, is CQ WCM zuivert Filter **altijd** gehandicapt (zelfs als gevormd zoals toegelaten).

## Hoe te om Pagina&#39;s aan te passen die door de Handler van de Fout worden getoond {#how-to-customize-pages-shown-by-the-error-handler}

U kunt uw eigen scripts ontwikkelen om de pagina&#39;s aan te passen die door de fouthandler worden weergegeven wanneer een fout optreedt. Om dit te doen gebruikt u [ AEM standaard bedekkingsmechanisme ](/help/implementing/developing/introduction/overlays.md) zodat uw aangepaste pagina&#39;s onder `/apps` worden gecreeerd en de standaardpagina&#39;s bedekken die onder `/libs` zijn.

1. Kopieer het standaardscript of de standaardscripts in de gegevensopslagruimte:

   * Van `/libs/sling/servlet/errorhandler/`
   * tot `/apps/sling/servlet/errorhandler/`

   Het doelpad bestaat niet standaard. U moet het dus maken wanneer u dit voor het eerst doet.

1. Navigeer naar `/apps/sling/servlet/errorhandler` . Hier kunt u:

   * bewerk het juiste bestaande script om de vereiste informatie op te geven. of
   * Maak en bewerk een nieuw script voor de vereiste code.

1. Sla de wijzigingen op en test u deze.

>[!CAUTION]
>
>Het script van `404.jsp` is specifiek ontworpen om te kunnen voldoen aan AEM verificatie, met name om systeemaanmelding mogelijk te maken in het geval van deze fouten.
>
>Daarom zou de vervanging van dit manuscript met grote voorzichtigheid moeten worden gedaan.

### De reactie op HTTP 500-fouten aanpassen {#customizing-the-response-to-http-errors}

De interne Fout van de Server van HTTP [ 500 ](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) wijst op een server-zijfout zoals de server die een onverwachte voorwaarde ontmoet die het verhinderde het verzoek te vervullen.

Wanneer de verzoekverwerking in een uitzondering resulteert, het kader Apache Sling (dat AEM wordt voortgebouwd op):

* Hiermee wordt de uitzondering geregistreerd
* En retourneert in de hoofdtekst van de respons:
   * De HTTP-responscode 500
   * De uitzonderingsstapeltracering

Door [ aan te passen kunnen de pagina&#39;s die door de foutenmanager ](#how-to-customize-pages-shown-by-the-error-handler) worden getoond a `500.jsp` manuscript worden gecreeerd. Deze wordt echter alleen gebruikt als `HttpServletResponse.sendError(500)` expliciet wordt uitgevoerd, dat wil zeggen van een uitzonderingscatcher.

Anders is de antwoordcode ingesteld op 500, maar wordt het script `500.jsp` niet uitgevoerd.

Als u 500 fouten wilt afhandelen, moet de bestandsnaam van het script van de fouthandler gelijk zijn aan de uitzonderingsklasse (of superklasse). U kunt dergelijke uitzonderingen afhandelen door een script `/apps/sling/servlet/errorhandler/Throwable.jsp` of `/apps/sling/servlet/errorhandler/Exception.jsp` te maken.

>[!NOTE]
>
>In AEM als Cloud Service, dient CDN een generische foutenpagina wanneer een 5XX fout van het achtereind wordt ontvangen. Als u wilt toestaan dat de werkelijke reactie van de backend wordt doorgegeven, moet u de volgende koptekst toevoegen aan de reactie: `x-aem-error-pass: true` .
>Dit werkt alleen voor reacties die afkomstig zijn van AEM of de laag Apache/Dispatcher. Andere onverwachte fouten die uit tussenliggende infrastructuurlagen komen zullen nog de generische foutenpagina tonen.

>[!CAUTION]
>
>Op een auteursinstantie, ](/help/implementing/deploying/configuring-osgi.md) wordt de Debug Filter van 0} CQ WCM toegelaten door gebrek. [ Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een douane fout-manager, zijn de reacties met code 500 nodig - zodat moet de [ CQ WCM zuivert Filter ](/help/implementing/deploying/configuring-osgi.md) worden onbruikbaar gemaakt. Dit zorgt ervoor dat reactiecode 500 is teruggekeerd, die beurtelings de correcte fout-manager van het Sling teweegbrengt.
>
>Op publiceer instantie, is CQ WCM zuivert Filter **altijd** gehandicapt (zelfs als gevormd zoals toegelaten).
