---
title: Opmerkingen bij de release 2020.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2020.7.0."
exl-id: 75d354a3-6987-4de0-aec8-24043461c516
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.7.0 beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.7.0 is 30 juli 2020.

## Adobe Experience Manager Sites as a Cloud Service {#cloud-services-sites}

### Wat is er nieuw? {#what-is-new-sites}

[!DNL Experience Manager] as a Cloud Service connectors voor [!DNL Adobe Target] en [!DNL Adobe Analytics] worden op de volgende manieren verbeterd:

* Een nieuwe die implementatie van het gebruikersinterface vervangt de implementatie op Klassieke UI wordt gebaseerd.

* Vereenvoudigde gebruikersinterfacedialoogvensters, waarbij het maken van een framework voor variabele toewijzing en andere configuraties overblijft [!DNL Adobe Launch]. Zie [Adobe Analytics integreren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html) en [Adobe Target integreren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html).

* Configuraties worden nu opgeslagen in `/conf` eerder dan `/etc/cloudsettings` in de opslagplaats van de Experience Manager.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* [!DNL Asset Compute Service] is de scalable en verlengbare dienst om activa te verwerken. Beheerders kunnen [!DNL Experience Manager] om aangepaste toepassingen aan te roepen die zijn gemaakt met de [!DNL Asset Compute Service]. De ontwikkelaars kunnen de dienst gebruiken om gespecialiseerde douanetoepassingen tot stand te brengen die aan complexe gebruiksgevallen behandelen. Met deze webservice kunt u miniaturen genereren voor verschillende bestandstypen, afbeeldingen van hoge kwaliteit renderen in de bestandsindelingen voor Adoben, video&#39;s coderen (in de toekomst), metagegevens extraheren, volledige tekst uitnemen als voorloper voor indexering en een element uitvoeren via alle beschikbare opties [!DNL Sensei] diensten. zie [gebruik microservices en verwerkingsprofielen voor bedrijfsmiddelen](/help/assets/asset-microservices-configure-and-use.md).

* De eerste configuratie van [!DNL Dynamic Media] in [!DNL Experience Manager] as a Cloud Service is verbeterd om robuuster te zijn. Het verstrekt nu vooruitgang van de processen aan de beheerders.

* Publiceren van activa naar [!DNL Dynamic Media] wordt vereenvoudigd en robuuster gemaakt door van deze pijpleiding een integrerend deel uit te maken van de algemene assetverwerkingpijplijn met behulp van asset microservices en de back-end voor het publiceren van batches te verbeteren.

* Workflowstappen die niet compatibel zijn met een Cloud Service-implementatie worden nu gemarkeerd met een waarschuwing in het gedeelte [!UICONTROL workflow model] editor. Bij het uitvoeren van de bestaande workflows in de omgeving van de Cloud Service worden ook de incompatibele workflowstappen overgeslagen.

* De modellen van het werkschema die door klanten worden gecreeerd die aan worden opgesteld `/conf/global` in het Git-project dat verband houdt met het milieu in [!DNL Cloud Manager] worden automatisch geïmplementeerd op `/var` en dus beschikbaar in [!DNL Experience Manager]. Productworkflowmodellen onder `/libs` die door de klant zijn gewijzigd, niet automatisch worden geïmplementeerd op `/var`.

### Buizen gecorrigeerd {#assets-bugs-fixed}

* De wizard Element verplaatsen wordt niet naar behoren geladen voor de elementen die in Verzamelingen zijn opgenomen. (CQ-4296756)
* De waarden van `dam:size` en `dam:sha1` zijn uitgesloten van XMP terugschrijven. (CQ-4237355)
* Bij het bulksgewijs ongedaan maken van de publicatie van activa [!DNL Brand Portal] genereert een fout die aangeeft dat de aanvraag-URI te lang is. (CQ-4299474)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Wat is er nieuw? {#what-is-new-commerce}

AEM Commerce is nu beschikbaar op de Cloud Service.

Zie [Aan de slag met AEM as a Cloud Service Commerce](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/commerce/getting-started.html) voor meer informatie .

## Kernonderdelen {#core-components}

### Wat is er nieuw? {#what-is-new-core-components}

Release 2.11.0 van de [AEM kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) is nu beschikbaar als onderdeel van AEM Sites, waaronder:

* Invoering van een nieuwe [PDF Viewer-component](https://www.aemcomponents.dev/content/core-components-examples/library/core-content/pdf-viewer.html).

* Ondersteuning voor versnelde mobiele pagina&#39;s (AMP) van kerncomponenten is nu beschikbaar. Het helpt klanten sneller ervaringen op te doen door de paginaovergang onmiddellijk te maken wanneer ze de site betreden vanuit een mobiel zoekresultaat van Google, wat de betrokkenheid van gebruikers en SEO verbetert.
Zie [AMP-ondersteuning voor de kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) voor meer informatie .

* Compatibiliteit met versie 1.0.2 van de [Gegevenslaag client-Adobe](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html).

* Bugfixes en verbeteringen van de codekwaliteit.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] Versie 202.7.0 is 9 juli 2020.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* De pagina met omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De pijpleidingen van de Manager van de wolk steunen nu klant-vastgestelde variabelen en geheimen.

  Zie Variabelen voor pijplijn voor meer informatie.

* Verificatie-gebonden Private Maven Repositories worden nu ondersteund.

* De buildcontainer van Cloud Manager ondersteunt nu zowel Java 8 als Java 11.
Zie Java 11-ondersteuning gebruiken voor meer informatie.

### Opgeloste problemen {#bug-fixes-cm}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De **Annuleren** en **Opslaan** op de pagina Bewerken van niet-productiepijpleiding zijn niet altijd opties weergegeven.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.

### Bekende problemen {#known-issues}

* Als gevolg van een wijziging in de manier waarop de codedekking wordt berekend, wordt de *minimum* De versie van de Jacoco-plug-in is nu 0.7.5.201505241946 (uitgebracht in mei 2015). Klanten die expliciet verwijzen naar een oudere versie ontvangen een foutbericht in het proces voor codekwaliteit.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### Wat is er nieuw? {#what-is-new-foundations}

* [Logboeken kunnen naar Splunk-accounts worden doorgestuurd](/help/implementing/developing/introduction/logging.md#splunk-logs), waardoor organisaties hun Splunk-investering kunnen gebruiken.

* [Een statisch, toegewijd IP adres van het uitgang](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) kan voor uitgaand verkeer worden toegewezen dat in code van Java wordt geprogrammeerd, die voor sommige integratie nuttig kan zijn.

* GePorted AEM Analytics Cloud Service UI van Klassieke UI naar nieuwe AEM UI. Ook de locatie van de Analytics-cloudservice in AEM opslagplaats verplaatst van `/etc` tot `/conf`, om deze uit te lijnen met andere AEM cloudservices.

* GePorted AEM Target cloud service UI van klassieke UI naar nieuwe AEM UI. Ook de locatie van de doelcloudservice in AEM opslagplaats verplaatst van `/etc` tot `/conf`, om deze uit te lijnen met andere AEM cloudservices.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Readiness Analyzer Release v1.0.2.

### Opgeloste problemen {#cra-bug-fixes}

* Eerdere versie van de CRA kan niet worden uitgevoerd op Adobe Experience Manager (AEM) 6.1. Er is expliciete ondersteuning toegevoegd om gebruikers in de beheerdersgroep toe te staan.

  Zie [CRA installeren op AEM 6.1](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) voor meer informatie .

* De tijdstempel voor verlopen die in het samenvattingsrapport wordt weergegeven, is onjuist.

* CRA detecteerde dubbele aangepaste componenten.

* Op AEM 6.1 was de inhoudsinspectie afgesloten voordat de volledige inspectie werd voltooid. Uitzonderingsafhandeling is toegevoegd, zodat de controle kan overslaan en doorgaan totdat de volledige inspectie is voltooid.
