---
title: Integreren met Adobe Target
description: Integreren met Adobe Target
exl-id: 2b4cf35e-2b75-4303-8d09-f6644ad99274
source-git-commit: 0af1f7dcc330a2ee5300088f274150a3ea79efe8
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

Als deel van Adobe Experience Cloud, [ Adobe Target ](https://business.adobe.com/products/target/adobe-target.html) laat u inhoudsrelevantie door het richten en het meten over alle kanalen verhogen. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM as a Cloud Service heeft de workflow voor het opgeven van doelen overgenomen die wordt gebruikt in Adobe Target Standard. Als u Target gebruikt, bent u vertrouwd met de het richten het uitgeven milieu in AEM as a Cloud Service.

Integreer uw AEM-sites met Adobe Target, zodat u de inhoud van uw pagina&#39;s kunt aanpassen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

>[!NOTE]
>
>Klanten die geen bestaande rekening van het Doel hebben kunnen om toegang tot het Pak van de Stichting van het Doel voor Experience Cloud verzoeken. Het Pak van de Stichting verstrekt volume beperkt gebruik van Doel.

Voer de volgende taken uit om met Doel te integreren:

* [ voer in eerste instantie vereiste taken ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html) uit: Register met Adobe Target en vorm bepaalde aspecten van de de auteursinstantie van AEM. Uw rekening van Adobe Target moet **het niveautoestemmingen van de goedkeuraar {op een minimum hebben.** Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

* Launch by Adobe is de facto tool voor het van instrumenten voorzien van een AEM-site met doelmogelijkheden (JS-bibliotheken). Daarom gaat de integratie van AEM as a Cloud Service met Launch en Adobe Target hand in hand (zie de koppelingen hieronder).

   * [ integreer Lancering door Adobe ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html)
   * [ integreer AEM met de Lancering van Adobe als Adobe I/O ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html)
   * [ Begrijpend de Integratie van AEM met Lancering door Adobe, Analytics en Doel ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html)

>[!NOTE]
>
>De IMS-configuratie (technische accounts) voor Starten door Adobe is vooraf geconfigureerd in AEM as a Cloud Service. Gebruikers hoeven deze configuratie niet te maken.

1. [ vorm Activiteiten ](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html): Verdeel uw Activiteiten met de de wolkenconfiguratie van het Doel.

>[!CAUTION]
>
>In AEM as a Cloud Service is de replicatieagent voor het synchroniseren van aanbiedingen en activiteiten van AEM naar Adobe Target standaard uitgeschakeld. Contacteer het [ team van de Steun van Adobe ](https://experienceleague.adobe.com/?support-solution=General#support) als u de replicatieagent moet opnieuw toelaten.

>[!NOTE]
>
>Als u Target gebruikt met een aangepaste proxyconfiguratie, moet u zowel de proxyconfiguraties van de HTTP-client configureren, aangezien sommige functies van AEM de 3.x-API&#39;s en sommige andere de 4.x-API&#39;s gebruiken:
>
>* 3.x wordt gevormd met [ http://localhost :4502 /system/console/configMgr/com.day.commons.httpclient ](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt gevormd met [ http://localhost :4502 /system/console/configMgr/org.apache.http.proxyconfigurator ](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>

>[!CAUTION]
>
>Beveilig de knoop van activiteitenmontages **cq:ActivitySettings** op publiceer instantie zodat het voor normale gebruikers ontoegankelijk is. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [ Vereisten voor het Integreren met Adobe Target ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node) voor gedetailleerde informatie.

Wanneer de integratie volledig is, kunt u [ auteur gerichte inhoud ](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/content-targeting-touch.html) die bezoekersgegevens naar Adobe Target verzendt. Voor paginacomponenten is specifieke code vereist om het aanwijzen van inhoud mogelijk te maken. (Zie [ het Ontwikkelen voor Gerichte Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/target.html).

>[!NOTE]
>
>Wanneer u een component in de auteur van AEM richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (als gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM as a Cloud Service met Adobe Target is kennis van Adobe Target, AEM Activity Management en AEM Audiences Management vereist. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (zie de [ documentatie van Adobe Target ](https://experienceleague.adobe.com/docs/target/using/target-home.html)).
* De console van de Activiteiten van AEM (zie [ het Leiden Activiteiten ](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html)).
* Het publiek van AEM (zie [ het Leiden Soorten publiek ](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/managing-audiences.html)).

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 cijfers
>* 50 rapporteringssegmenten
