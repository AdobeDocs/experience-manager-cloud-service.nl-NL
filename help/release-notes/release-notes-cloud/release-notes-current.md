---
title: Opmerkingen bij de release voor 2020.7.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als de Nota''s van de Versie van de Cloud Service voor 2020.7.0.'
translation-type: tm+mt
source-git-commit: 459843adff623395bcf7afb41f427d6ea0fb825c
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 2%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.7.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager beschreven als Cloud Service 2020.7.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als Cloud Service 2020.7.0 is 30 juli 2020.

## Adobe Experience Manager Sites als Cloud Service {#cloud-services-sites}

### What&#39;s New {#what-is-new-sites}

[!DNL Experience Manager] als connectors voor Cloud Servicen voor [!DNL Adobe Target] en [!DNL Adobe Analytics] worden op de volgende manieren verbeterd:

* Een nieuwe die implementatie van het gebruikersinterface vervangt de implementatie op Klassieke UI wordt gebaseerd.

* Vereenvoudigde dialoogvensters voor gebruikersinterfaces, waarbij het maken van een framework voor variabele toewijzing en andere configuraties overblijft [!DNL Adobe Launch]. Zie [Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html) integreren en [Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html)integreren.

* Configuraties worden nu opgeslagen in `/conf` plaats `/etc/cloudsettings` in de opslagplaats van de Experience Manager.

## Adobe Experience Manager Assets as a Cloud Service {#assets}

### What&#39;s New {#what-is-new-assets}

* [!DNL Asset Compute Service] is de scalable en verlengbare dienst om activa te verwerken. Beheerders kunnen Experience Manager configureren om een aangepaste worker aan te roepen die is gemaakt met de [!DNL Asset Compute Service]code. De ontwikkelaars kunnen de dienst gebruiken om gespecialiseerde douanearbeiders tot stand te brengen die aan complexe gebruiksgevallen behandelen. Deze webservice kan miniaturen genereren voor verschillende bestandstypen, afbeeldingen van hoge kwaliteit in de bestandsindelingen Adobe, video&#39;s coderen (in de toekomst), metagegevens extraheren, volledige tekst uitnemen als voorloper voor indexering en een element uitvoeren via alle beschikbare Sensei-services. Zie [Elementmicroservices en verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md)gebruiken.

* De aanvankelijke configuratie van [!DNL Dynamic Media] binnen [!DNL Experience Manager] als Cloud Service wordt verbeterd om robuuster te zijn. Het verstrekt nu vooruitgang van de processen aan de beheerders.

* Het publiceren van activa die moeten worden gepubliceerd, [!DNL Dynamic Media] wordt vereenvoudigd en robuuster gemaakt door deze tot een integraal onderdeel te maken van de algehele assetverwerkingspijplijn met behulp van asset microservices en de back-end voor het publiceren van batches te verbeteren.

* De stappen van het werkschema die niet compatibel met een plaatsing van de Cloud Service zijn nu duidelijk met een waarschuwing in de [!UICONTROL workflow model] redacteur. Bovendien, wanneer het uitvoeren van de bestaande werkschema&#39;s op het milieu van de Cloud Service, worden de incompatibele werkschemasstappen overgeslagen.

* De modellen van het werkschema die door klanten worden gecreeerd die aan `/conf/global` in het project van Git verbonden aan het milieu in de Manager van de Wolk worden opgesteld worden automatisch opgesteld aan `/var` en zo beschikbaar in Experience Manager. De modellen van het productwerkschema onder `/libs` die door klant werden veranderd worden niet automatisch opgesteld aan `/var`.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### What&#39;s New {#what-is-new-commerce}

* AEM Commerce is nu beschikbaar op Cloud Service. Raadpleeg [Aan de slag](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/commerce/getting-started.html)voor meer informatie.

## Kernonderdelen {#core-components}

### What&#39;s New {#what-is-new-core-components}

Release 2.11.0 van de [AEM Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) is nu beschikbaar als onderdeel van AEM Sites zoals:

* Introductie van een nieuwe [PDF Viewer-component](https://aemcomponents.dev/content/core-components-examples/library/page-authoring/pdf-viewer.html).

* Ondersteuning voor versnelde mobiele pagina&#39;s (AMP) van kerncomponenten is nu beschikbaar. Het helpt klanten sneller ervaringen op te doen door de paginaovergang onmiddellijk te maken wanneer ze de site betreden vanuit een mobiel zoekresultaat van Google, wat de betrokkenheid van gebruikers en SEO verbetert.
Raadpleeg [AMP Support for the Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/amp.html) voor meer informatie.

* Compatibiliteit met versie 1.0.2 van de gegevenslaag [van de Cliënt van](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/data-layer/overview.html)Adobe.

* Bugfixes en verbeteringen van de codekwaliteit.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.7.0 is 9 juli 2020.

### What&#39;s New {#what-is-new-cloud-manager}

* De pagina met omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De pijpleidingen van de Manager van de wolk steunen nu klant-vastgestelde variabelen en geheimen.

   Raadpleeg [Pipetvariabelen](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#pipeline-variables) voor meer informatie.

### Bug Fixes {#bug-fixes-cm}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De opties **Annuleren** en **Opslaan** op de bewerkingspagina Niet-productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.

### Bekende problemen {#known-issues}

* Als gevolg van een wijziging in de manier waarop de codedekking wordt berekend, is de *minimale* versie van de Jacoco-plug-in nu 0.7.5.201505241946 (uitgebracht in mei 2015). Klanten die expliciet verwijzen naar een oudere versie ontvangen een foutbericht in het proces voor de kwaliteit van de code.


## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### What&#39;s New {#what-is-new-foundations}

* [Logs kan aan Splunk accounts](/help/implementing/developing/introduction/logging.md#splunk-logs)worden doorgestuurd, waardoor organisaties hun Splunk-investering kunnen benutten.

* [Een statisch, specifiek uitgangIP adres](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) kan voor uitgaand verkeer worden toegewezen geprogrammeerd in code Java, die voor sommige integratie nuttig kan zijn.

* Ported AEM Analytics cloud service UI from Classic UI to new AEM UI. Ook de locatie van de Analytics-cloudservice in AEM opslagplaats verplaatst van `/etc` naar `/conf`, om deze uit te lijnen met andere AEM cloud services.

* Ported AEM Target cloud service UI from Classic UI to new AEM UI. Ook de locatie van de Target-cloudservice in AEM opslagplaats verplaatst van `/etc` naar `/conf`, om deze uit te lijnen met andere AEM cloud services.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Readiness Analyzer Release v1.0.2.

### Bug Fixes {#cra-bug-fixes}

* Eerdere versie van de CRA kon niet worden uitgevoerd op Adobe Experience Manager (AEM) 6.1. Er is expliciete ondersteuning toegevoegd om gebruikers in de beheerdersgroep toe te staan.

   Raadpleeg [CRA installeren op AEM 6.1](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) voor meer informatie.

* De tijdstempel voor verlopen die in het samenvattingsrapport wordt weergegeven, is onjuist.

* CRA detecteerde dubbele aangepaste componenten.

* Op AEM 6.1 was de inhoudsinspectie afgesloten voordat de volledige inspectie werd voltooid. Uitzonderingsafhandeling is toegevoegd, zodat de controle kan overslaan en doorgaan totdat de volledige inspectie is voltooid.
