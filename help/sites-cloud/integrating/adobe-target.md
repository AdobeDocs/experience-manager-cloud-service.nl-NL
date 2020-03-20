---
title: Integreren met Adobe Target
description: 'Integreren met Adobe Target '
translation-type: tm+mt
source-git-commit: ed8cfc564e198552ae4efabee1ff48950470790a

---


# Integreren met Adobe Target{#integrating-with-adobe-target}

Als onderdeel van de Adobe Marketing Cloud kunt u met [Adobe Target](http://www.adobe.com/solutions/testing-targeting/testandtarget.html) de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (op basis van gedrag) en het automatiseren van het kiezen voor inhoud en online ervaringen. AEM als Cloud Service heeft de doelworkflow overgenomen die wordt gebruikt in Adobe Target Standard. Als u Target gebruikt, zult u vertrouwd met het richten het uitgeven milieu in AEM als Dienst van de Wolk zijn.

Integreer uw AEM-sites met Adobe Target om de inhoud van uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

>[!NOTE]
>
>Adobe Experience Manager als klanten van de Cloud Service die geen bestaand Target-account hebben, kunnen toegang aanvragen tot het Target Foundation Pack voor Experience Cloud.  Het Pak van de Stichting verstrekt volume beperkt gebruik van Doel.


Voer de volgende taken uit om met Doel te integreren:

* [Voorwaardelijke taken](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html)uitvoeren: Meld u aan bij Adobe Target en configureer bepaalde aspecten van de AEM-auteur. Uw Adobe Target-account moet minimaal **toegangsrechten op het niveau van de fiatteur** hebben. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

* Launch by Adobe is de facto tool voor het van instrumenten voorzien van een AEM-site met doelmogelijkheden (JS-bibliotheken). Daarom gaat de integratie van AEM als Cloud Service met Launch en Adobe Target hand in hand (zie de koppelingen hieronder).

   * [Integratie met Adobe Target met Adobe I/O](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html)
   * [Starten door Adobe integreren](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
   * [AEM integreren met Adobe Launch via Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
   * [AEM-integratie begrijpen met Starten door Adobe, Analytics en Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)

>[!NOTE]
>
>De IMS-configuratie (technische accounts) voor Starten door Adobe is vooraf geconfigureerd in AEM als een Cloud Service. Gebruikers hoeven deze configuratie niet te maken.

1. [Activiteiten](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html)configureren: Koppel uw activiteiten aan de doelwolkenconfiguratie.

>[!CAUTION]
>
>In AEM als Cloud Service is de replicatieagent die aanbiedingen en activiteiten van AEM synchroniseert met Adobe Target standaard uitgeschakeld. Neem contact op met het ondersteuningsteam van [Adobe](https://helpx.adobe.com/contact/enterprise-support.ec.html#experience-manager) als u de replicatieagent opnieuw moet inschakelen.

>[!NOTE]
>
>Als u Doel met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



>[!CAUTION]
>
>U moet het knooppunt activity settings (activity settings) **cq:ActivitySettings** op de publicatie-instantie beveiligen, zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt met activiteiteninstellingen mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt naar Adobe Target.
>
>Zie [Vereisten voor Integratie met Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node) voor meer informatie.

Wanneer de integratie is voltooid, kunt u specifieke inhoud [](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/content-targeting-touch.html) ontwerpen die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [Ontwikkelen voor gerichte inhoud](https://docs.adobe.com/content/help/en/experience-manager-65/developing/personlization/target.html).

>[!NOTE]
>
>Wanneer u een component aanwijst in de auteur van AEM, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, aanbiedingen op te zetten, en de segmenten van het Doel van Adobe terug te winnen (als gevormd). Er worden geen serveraanroepen vanuit AEM-publicatie naar Adobe Target uitgevoerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM als Cloud Service met Adobe Target is kennis vereist van Adobe Target, AEM Activity Management en AEM Audiences Management. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (Zie de documentatie [van](https://marketing.adobe.com/resources/help/en_US/target/)Adobe Target).
* AEM Activity Console (zie [Managing Activity](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html).
* AEM-publiek (zie [Soorten publiek](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/managing-audiences.html)beheren).

>[!NOTE]
>
>Wanneer u werkt met Adobe Target, is het volgende het maximumaantal artefacten dat binnen een campagne is toegestaan:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 metriek
>* 50 rapporteringssegmenten
>


