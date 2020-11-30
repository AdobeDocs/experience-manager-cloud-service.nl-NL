---
title: Integreren met Adobe Target
description: 'Integreren met Adobe Target '
translation-type: tm+mt
source-git-commit: bffc335fdafe6bf12a66bcd2f7aacf029fce567e
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 1%

---


# Integreren met Adobe Target{#integrating-with-adobe-target}

Als onderdeel van de Adobe Marketing Cloud kunt u met [Adobe Target](http://www.adobe.com/solutions/testing-targeting/testandtarget.html) de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM als Cloud Service heeft de doelworkflow overgenomen die wordt gebruikt in Adobe Target Standard. Als u Doel gebruikt, zult u met het richten het uitgeven milieu in AEM als Cloud Service vertrouwd zijn.

Integreer uw AEM met Adobe Target om inhoud op uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

>[!NOTE]
>
>Adobe Experience Manager als klanten van de Cloud Service die geen bestaande rekening van het Doel hebben, kan om toegang tot het Pak van de Stichting van het Doel voor Experience Cloud verzoeken.  Het Pak van de Stichting verstrekt volume beperkt gebruik van Doel.


Voer de volgende taken uit om met Doel te integreren:

* [Voorwaardelijke taken](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html)uitvoeren: Registreer u bij Adobe Target en configureer bepaalde aspecten van de AEM auteur. Uw Adobe Target-account moet minimaal **toegangsrechten op het niveau van de fiatteur** hebben. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

* Launch by Adobe is het defacto hulpmiddel om een AEM plaats met de mogelijkheden van het Doel (bibliotheken JS) van instrumenten te voorzien. Daarom gaat de integratie van AEM als Cloud Service met Launch en Adobe Target hand in hand (zie de koppelingen hieronder).

   * [Integratie met Adobe Target met Adobe I/O](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html)
   * [Launch by Adobe integreren](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
   * [AEM integreren met Adobe starten via Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
   * [Inzicht in AEM integratie met Launch by Adobe, Analyses en Doel](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)

>[!NOTE]
>
>De configuratie IMS (technische rekeningen) voor Launch by Adobe wordt preconfigured in AEM als Cloud Service. Gebruikers hoeven deze configuratie niet te maken.

1. [Activiteiten](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html)configureren: Koppel uw activiteiten aan de doelwolkenconfiguratie.

>[!CAUTION]
>
>In AEM als Cloud Service, wordt de replicatieagent die Aanbiedingen en Activiteiten van AEM aan Adobe Target synchroniseert door gebrek onbruikbaar gemaakt. Neem contact op met het [Adobe Support](https://helpx.adobe.com/contact/enterprise-support.ec.html#experience-manager) -team als u de replicatieagent opnieuw moet inschakelen.

>[!NOTE]
>
>Als u Doel met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM de 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



>[!CAUTION]
>
>U moet het knooppunt activity settings (activity settings) **cq:ActivitySettings** op de publicatie-instantie beveiligen, zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [Vereisten voor Integratie met Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node) voor meer informatie.

Wanneer de integratie is voltooid, kunt u specifieke inhoud [](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/content-targeting-touch.html) ontwerpen die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [Ontwikkelen voor gerichte inhoud](https://docs.adobe.com/content/help/en/experience-manager-65/developing/personlization/target.html).

>[!NOTE]
>
>Wanneer u een component in AEM auteur richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (indien gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM als Cloud Service met Adobe Target is kennis vereist van Adobe Target, AEM Activiteitenbeheer en AEM beheer van doelgroepen. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (Zie de documentatie [van](https://docs.adobe.com/content/help/en/target/using/target-home.html)Adobe Target).
* AEM Activiteiten console (zie [Managing Activity](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html).
* AEM publiek (Zie [Soorten publiek](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/managing-audiences.html)beheren.

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 metriek
>* 50 rapporteringssegmenten

>


