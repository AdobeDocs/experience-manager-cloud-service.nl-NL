---
title: Integreren met Adobe Target
description: Integreren met Adobe Target
exl-id: 2b4cf35e-2b75-4303-8d09-f6644ad99274
source-git-commit: 421ad8506435e8538be9c83df0b78ad8f222df0c
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 1%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

In het kader van de Adobe Marketing Cloud [Adobe Target](https://www.adobe.com/solutions/testing-targeting/testandtarget.html) Hiermee kunt u de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM as a Cloud Service heeft de doelworkflow overgenomen die wordt gebruikt in Adobe Target Standard. Als u Doel gebruikt, zult u met het richten het uitgeven milieu in AEM as a Cloud Service vertrouwd zijn.

Integreer uw AEM met Adobe Target om inhoud op uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

>[!NOTE]
>
>De klanten van Adobe Experience Manager as a Cloud Service die geen bestaand rekening van het Doel hebben, kunnen om toegang tot het Pak van de Stichting van het Doel voor Experience Cloud verzoeken.  Het Pak van de Stichting verstrekt volume beperkt gebruik van Doel.


Voer de volgende taken uit om met Doel te integreren:

* [Voorwaardelijke taken uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html): Registreer u bij Adobe Target en configureer bepaalde aspecten van de AEM auteur. Je Adobe Target-account moet **fiatteur** minimaal niveau aan machtigingen. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

* Launch by Adobe is het defacto hulpmiddel om een AEM plaats met de mogelijkheden van het Doel (bibliotheken JS) van instrumenten te voorzien. De integratie van AEM as a Cloud Service met Launch en Adobe Target gaat daarom hand in hand (zie de koppelingen hieronder).

   * [Integratie met Adobe Target met Adobe I/O](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-target-ims-adobe-io.html)
   * [Launch by Adobe integreren](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)
   * [AEM integreren met Adobe starten via Adobe I/O](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)
   * [Inzicht in AEM integratie met Launch by Adobe, Analyses en Doel](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)

>[!NOTE]
>
>De configuratie IMS (technische rekeningen) voor Launch by Adobe wordt preconfigured in AEM as a Cloud Service. Gebruikers hoeven deze configuratie niet te maken.

1. [Activiteiten configureren](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html): Koppel uw activiteiten aan de doelwolkenconfiguratie.

>[!CAUTION]
>
>In AEM as a Cloud Service, wordt de replicatieagent die Aanbiedingen en Activiteiten van AEM aan Adobe Target synchroniseert onbruikbaar gemaakt door gebrek. Neem contact op met de [Adobe-ondersteuning](https://experienceleague.adobe.com/?support-solution=General#support) team als u de replicatieagent opnieuw moet toelaten.

>[!NOTE]
>
>Als u Doel met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM de 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


>[!CAUTION]
>
>U moet het knooppunt met activiteiteninstellingen beveiligen **cq:ActivitySettings** op de publicatie-instantie zodat deze niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [Vereisten voor integratie met Adobe Target](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node) voor nadere informatie.

Wanneer de integratie is voltooid, kunt u [doelinhoud auteur](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/content-targeting-touch.html) die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [Ontwikkelen voor gerichte inhoud](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/target.html).

>[!NOTE]
>
>Wanneer u een component in AEM auteur richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (indien gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM as a Cloud Service met Adobe Target is kennis van Adobe Target, AEM Activiteitenbeheer en AEM beheer van doelgroepen vereist. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (Zie de [Adobe Target-documentatie](https://experienceleague.adobe.com/docs/target/using/target-home.html)).
* AEM Activiteitenconsole (zie [Beheersactiviteiten](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html).
* AEM publiek (zie [Soorten publiek beheren](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/managing-audiences.html).

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 metriek
>* 50 rapporteringssegmenten

