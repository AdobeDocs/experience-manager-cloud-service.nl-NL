---
title: Integreren met Adobe Analytics
description: 'Integreren met Adobe Analytics '
translation-type: tm+mt
source-git-commit: 6754693da488b0bc44a71aa9f0402fc1308b703a
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 13%

---


# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM als Cloud Service te integreren, kunt u de activiteiten van uw webpagina volgen:

* Met een configuratie voor Adobe Analytics kan AEM verificatie uitvoeren met Adobe Analytics.
* Een framework geeft de gegevens aan die naar uw Adobe Analytics-rapportsuite worden verzonden.

De gegevens bevatten bijvoorbeeld pagina- en gebruikersgegevens:

* gegevens die door AEM-componenten worden verzameld
* koppelingsklikken
* videogebruiksinformatie
* het aantal pagina-bezoeken van Adobe Analytics

De pagina&#39;s hieronder kunnen u helpen de integratie vormen. Opgemerkt moet worden dat het lanceren door Adobe het facto hulpmiddel voor het van instrumenten voorzien van een plaats AEM met de mogelijkheden van Analytics (bibliotheken JS) is. Daarom gaat de integratie van AEM als Cloud Service met Launch en Adobe Analytics hand in hand.

* [Verbinding maken met Adobe Analytics en Frameworks](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-connect.html) maken - Onthoud dat &#39;Analytics frameworks&#39; verouderd zijn in AEM en dat het maken ervan niet werkt in AEM als Cloud Service omdat hiervoor de klassieke gebruikersinterface is vereist. Start door Adobe moet worden gebruikt voor het toewijzen van variabelen en voor het implementeren van JS-bibliotheken op pagina&#39;s.
* [Starten door Adobe integreren](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [AEM integreren met Adobe Launch via Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [AEM-integratie begrijpen met Starten door Adobe, Analytics en Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Koppelingen bijhouden configureren voor Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Componentgegevens toewijzen met de eigenschappen van Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Video bijhouden configureren voor Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe-classificaties](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Adobe Experience Manager als klanten van de Cloud Service die geen bestaand Analytics-account hebben, kunnen toegang aanvragen tot het Analytics Foundation Pack voor Experience Cloud.  This Foundation Pack provided volume limited use of Analytics.

>[!NOTE]
>
>De IMS-configuratie (technische accounts) voor Starten door Adobe is vooraf geconfigureerd in AEM als een Cloud Service. Gebruikers hoeven deze configuratie niet te maken.

## Aanvullende informatie {#further-information}

Zie:

* [De Adobe Analytics Integration](https://docs.adobe.com/content/help/en/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) uitbreiden voor informatie over het ontwikkelen van componenten die gebruikersgegevens verzamelen en het Adobe Analytics-framework aanpassen. U moet weten dat &quot;Analytics frameworks&quot; verouderd zijn in AEM en dat het maken ervan niet werkt in AEM als Cloud Service omdat hiervoor de klassieke gebruikersinterface is vereist. Start door Adobe moet worden gebruikt voor het toewijzen van variabelen en voor het implementeren van JS-bibliotheken op pagina&#39;s.
* Het kennisbankartikel, [Adobe Analytics-integratie - Problemen](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)oplossen, voor informatie over het oplossen van problemen met de integratie van Adobe Analytics.

>[!NOTE]
>
>Als u Adobe Analytics gebruikt met een aangepaste proxyconfiguratie, moet u [twee OSGi-bundels configureren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/configuring-osgi.html) (bijvoorbeeld met de webconsole) die voor de **Apache HTTP Client**-proxyconfiguraties vereist zijn. Beide zijn vereist omdat sommige functies van AEM de 3.x-API&#39;s gebruiken, terwijl andere de 4.x-API&#39;s gebruiken. Configureren:
>
>* **Day Commons HTTP Client 3.1** om de 3.x API te configureren;
   >  bijvoorbeeld [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Apache HTTP Components Proxy Configuration** om de 4.x API te configureren;
   >  bijvoorbeeld [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


