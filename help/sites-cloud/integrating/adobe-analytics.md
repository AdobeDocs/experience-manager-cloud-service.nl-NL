---
title: 'Integreren met Adobe Analytics '
description: 'Integreren met Adobe Analytics '
translation-type: tm+mt
source-git-commit: ec747361935b94a729cdd5b6712aee6d3ce1b8a2
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 13%

---


# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM als Cloud Service te integreren, kunt u uw webpaginageactiviteit volgen:

* Met een Adobe Analytics-configuratie kunnen AEM verifiëren met Adobe Analytics.
* Een framework geeft de gegevens aan die naar uw Adobe Analytics-rapportenpakket worden verzonden.

De gegevens bevatten bijvoorbeeld pagina- en gebruikersgegevens:

* gegevens die AEM componenten verzamelen
* koppelingsklikken
* videogebruiksinformatie
* het aantal pagina-bezoeken van Adobe Analytics

De pagina&#39;s hieronder kunnen u helpen de integratie vormen. Opgemerkt moet worden dat Launch by Adobe het instrument is waarmee een AEM site met Analytics-mogelijkheden (JS-bibliotheken) van instrumenten kan worden voorzien. Daarom gaat het integreren van AEM als Cloud Service met Launch en Adobe Analytics hand in hand.

* [Verbinding maken met Adobe Analytics en Frameworks](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-connect.html) maken - Opmerking: &quot;Analytics-frameworks&quot; zijn verouderd in AEM en het maken ervan werkt niet in AEM als Cloud Service omdat hiervoor de klassieke gebruikersinterface is vereist. In plaats daarvan moet Launch by Adobe worden gebruikt voor het toewijzen van variabelen en voor het implementeren van JS-bibliotheken op pagina&#39;s.
* [Launch by Adobe integreren](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [AEM integreren met Adobe starten via Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [Inzicht in AEM integratie met Launch by Adobe, Analytics en Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Koppeling bijhouden configureren voor Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Componentgegevens toewijzen aan Adobe Analytics-eigenschappen](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Video bijhouden configureren voor Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe-classificaties](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Adobe Experience Manager als klanten van de Cloud Service die geen bestaande rekening van Analytics hebben, kan om toegang tot het Pak van de Stichting van Analytics voor Experience Cloud verzoeken.  This Foundation Pack provided volume limited use of Analytics.

>[!NOTE]
>
>De configuratie IMS (technische rekeningen) voor Launch by Adobe wordt preconfigured in AEM als Cloud Service. Gebruikers hoeven deze configuratie niet te maken.

## Aanvullende informatie {#further-information}

Zie:

* [De Adobe Analytics-integratie](https://docs.adobe.com/content/help/en/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) uitbreiden voor informatie over het ontwikkelen van componenten die gebruikersgegevens verzamelen en het Adobe Analytics-framework aanpassen. Opmerking: &quot;Analytics-frameworks&quot; zijn verouderd in AEM en het maken ervan werkt niet in AEM als Cloud Service omdat hiervoor de klassieke gebruikersinterface is vereist. In plaats daarvan moet Launch by Adobe worden gebruikt voor het toewijzen van variabelen en voor het implementeren van JS-bibliotheken op pagina&#39;s.
* Het kennisbankartikel, integratie van [Adobe Analytics - het oplossen van problemenkwesties](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), voor informatie over het oplossen van problemen uw integratie van Adobe Analytics.

>[!NOTE]
>
>Als u Adobe Analytics gebruikt met een aangepaste proxyconfiguratie, moet u [twee OSGi-bundels configureren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/configuring-osgi.html) (bijvoorbeeld met de webconsole) die voor de **Apache HTTP Client**-proxyconfiguraties vereist zijn. Beide zijn vereist omdat sommige functies van AEM de 3.x-API&#39;s gebruiken, terwijl andere de 4.x-API&#39;s gebruiken. Configureren:
>
>* **Day Commons HTTP Client 3.1** om de 3.x API te configureren;
>  bijvoorbeeld [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** om de 4.x API te configureren;
>  bijvoorbeeld [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


