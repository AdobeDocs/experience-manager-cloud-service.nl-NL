---
title: Aangepaste foutpagina's
description: AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten, die kan worden aangepast.
translation-type: tm+mt
source-git-commit: d7e9bdee83f1b85436185ca57420ee178268cb33
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Foutpagina&#39;s aanpassen {#customizing-error-pages}

AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten; bijvoorbeeld door het volgende weer te geven:

![Standaardfoutbericht](assets/error-message-standard.png)

Als u op fouten wilt reageren, AEM een `404.jsp`-script onder `/libs/sling/servlet/errorhandler`.

>[!TIP]
>
>Omdat AEM is gebaseerd op Apache Sling, is meer informatie [beschikbaar in de documentatie van de Apache foutenbehandeling.](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>Voor een auteurinstantie, [CQ WCM zuivert Filter ](/help/implementing/deploying/configuring-osgi.md) wordt toegelaten door gebrek. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een publicatie-instantie is CQ WCM Debug Filter **always** uitgeschakeld (zelfs als dit is geconfigureerd als ingeschakeld).

## Hoe te om Pagina&#39;s aan te passen die door de Handler van de Fout {#how-to-customize-pages-shown-by-the-error-handler} worden getoond

U kunt uw eigen scripts ontwikkelen om de pagina&#39;s aan te passen die door de fouthandler worden weergegeven wanneer een fout optreedt. Hiervoor gebruikt u [AEM standaardbedekkingsmechanisme](/help/implementing/developing/introduction/overlays.md), zodat uw aangepaste pagina&#39;s onder `/apps` worden gemaakt en de standaardpagina&#39;s onder `/libs` worden bedekt.

1. Kopieer het standaardscript of de standaardscripts in de gegevensopslagruimte:

   * Van `/libs/sling/servlet/errorhandler/`
   * tot `/apps/sling/servlet/errorhandler/`

   Het doelpad bestaat niet standaard, dus moet u het voor het eerst maken.

1. Ga naar `/apps/sling/servlet/errorhandler`. Hier kunt u:

   * bewerk het juiste bestaande script om de vereiste informatie op te geven. of
   * Maak en bewerk een nieuw script voor de vereiste code.

1. Sla de wijzigingen op en test u deze.

>[!CAUTION]
>
>Het `404.jsp` manuscript is specifiek ontworpen om aan AEM authentificatie te behandelen; met name om systeemaanmelding mogelijk te maken in het geval van deze fouten.
>
>Daarom zou de vervanging van dit manuscript met grote voorzichtigheid moeten worden gedaan.

### De reactie op HTTP 500-fouten aanpassen {#customizing-the-response-to-http-errors}

De HTTP [500 Interne serverfout](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) geeft een serverfout aan, zoals de server die een onverwachte voorwaarde tegenkomt die het onmogelijk maakte aan de aanvraag te voldoen.

Wanneer de verzoekverwerking in een uitzondering resulteert, het kader Apache Sling (dat AEM wordt voortgebouwd op):

* Hiermee wordt de uitzondering geregistreerd
* En retourneert in de hoofdtekst van de respons:
   * De HTTP-responscode 500
   * De trace van de uitzonderingsstapel

Door [het aanpassen van de pagina&#39;s die door foutenmanager](#how-to-customize-pages-shown-by-the-error-handler) worden getoond kan een `500.jsp` manuscript worden gecreeerd. Deze wordt echter alleen gebruikt als `HttpServletResponse.sendError(500)` expliciet wordt uitgevoerd; d.w.z. van een uitzonderingscatcher.

Anders is de antwoordcode ingesteld op 500, maar wordt het script `500.jsp` niet uitgevoerd.

Als u 500 fouten wilt afhandelen, moet de bestandsnaam van het script van de fouthandler gelijk zijn aan de uitzonderingsklasse (of superklasse). Om al dergelijke uitzonderingen te behandelen kunt u een manuscript `/apps/sling/servlet/errorhandler/Throwable.jsp` of `/apps/sling/servlet/errorhandler/Exception.jsp` tot stand brengen.

>[!CAUTION]
>
>Voor een auteurinstantie, [CQ WCM zuivert Filter ](/help/implementing/deploying/configuring-osgi.md) wordt toegelaten door gebrek. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een aangepaste fout-manager, zijn de reacties met code 500 nodig - zodat moet [CQ WCM zuivert Filter worden onbruikbaar gemaakt.](/help/implementing/deploying/configuring-osgi.md) Dit zorgt ervoor dat reactiecode 500 is teruggekeerd, die beurtelings de correcte fout-manager van het Sling teweegbrengt.
>
>Voor een publicatie-instantie is CQ WCM Debug Filter **always** uitgeschakeld (zelfs als dit is geconfigureerd als ingeschakeld).
