---
title: Nota's van de versie voor versie 2020.7.0 van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: '[!DNL Adobe Experience Manager] Opmerkingen bij de release van as a Cloud Service voor 2020.7.0.'
exl-id: 75d354a3-6987-4de0-aec8-24043461c516
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Opmerkingen bij de release van [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.7.0 beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.7.0 is 30 juli 2020.

## Adobe Experience Manager Sites as a Cloud Service {#cloud-services-sites}

### Wat is er nieuw? {#what-is-new-sites}

[!DNL Experience Manager] as a Cloud Service-connectors voor [!DNL Adobe Target] en [!DNL Adobe Analytics] worden op de volgende manieren verbeterd:

* Een nieuwe die implementatie van het gebruikersinterface vervangt de implementatie op Klassieke UI wordt gebaseerd.

* Vereenvoudigde dialoogvensters voor gebruikersinterfaces, waarbij het maken van frameworks voor variabele mapping en andere configuraties overblijven op [!DNL Adobe Launch] . Zie [&#x200B; Integrerend Adobe Analytics &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html?lang=nl-NL) en [&#x200B; Integrerend Adobe Target &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html?lang=nl-NL).

* Configuraties worden nu opgeslagen in `/conf` in plaats van `/etc/cloudsettings` in de Experience Manager-opslagplaats.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* [!DNL Asset Compute Service] is een schaalbare en uitbreidbare service voor het verwerken van elementen. Beheerders kunnen [!DNL Experience Manager] zo configureren dat aangepaste toepassingen worden aangeroepen die met [!DNL Asset Compute Service] zijn gemaakt. De ontwikkelaars kunnen de dienst gebruiken om gespecialiseerde douanetoepassingen tot stand te brengen die aan complexe gebruiksgevallen behandelen. Deze webservice kan miniaturen genereren voor verschillende bestandstypen, afbeeldingen van hoge kwaliteit renderen in Adobe-bestandsindelingen, video&#39;s coderen (in de toekomst), metagegevens extraheren, volledige tekst uitnemen als voorloper voor indexering en een element uitvoeren via alle beschikbare [!DNL AI] -services. zie [&#x200B; gebruik activa microservices en verwerkingsprofielen &#x200B;](/help/assets/asset-microservices-configure-and-use.md).

* De initiële configuratie van [!DNL Dynamic Media] in [!DNL Experience Manager] as a Cloud Service is verbeterd en nu robuuster. Het verstrekt nu vooruitgang van de processen aan de beheerders.

* Het publiceren van elementen naar [!DNL Dynamic Media] wordt vereenvoudigd en robuuster gemaakt door deze tot een integraal onderdeel te maken van de algehele assetverwerkingspijplijn met behulp van asset microservices en de back-end voor het publiceren van batches te verbeteren.

* Workflowstappen die niet compatibel zijn met een Cloud Service-implementatie, worden nu gemarkeerd met een waarschuwing in de [!UICONTROL workflow model] -editor. Bij het uitvoeren van de bestaande workflows in de Cloud Service-omgeving worden ook de incompatibele workflowstappen overgeslagen.

* Workflowmodellen die zijn gemaakt door klanten die zijn geïmplementeerd in `/conf/global` het Git-project dat is gekoppeld aan de omgeving in [!DNL Cloud Manager] , worden automatisch geïmplementeerd in `/var` en zijn dus beschikbaar in [!DNL Experience Manager] . De workflowmodellen voor producten onder `/libs` die door de klant zijn gewijzigd, worden niet automatisch geïmplementeerd in `/var` .

### Buizen gecorrigeerd {#assets-bugs-fixed}

* De wizard Element verplaatsen wordt niet naar behoren geladen voor de elementen die in Verzamelingen zijn opgenomen. (CQ-4296756)
* De waarden van `dam:size` en `dam:sha1` worden niet opgenomen in XMP-schrijfback. (CQ-4237355)
* Wanneer [!DNL Brand Portal] de publicatie van elementen bulksgewijs ongedaan maakt, wordt een fout gegenereerd die aangeeft dat de aanvraag-URI te lang is. (CQ-4299474)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Wat is er nieuw? {#what-is-new-commerce}

AEM Commerce is nu beschikbaar op Cloud Service.

Zie [&#x200B; Begonnen het worden met AEM Commerce as a Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/commerce/getting-started.html?lang=nl-NL) voor meer details.

## Kernonderdelen {#core-components}

### Wat is er nieuw? {#what-is-new-core-components}

Versie 2.11.0 van de [&#x200B; Componenten van de Kern van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) is nu beschikbaar als deel van AEM Sites met inbegrip van:

* Inleiding van een nieuwe [&#x200B; Component van de Kijker van PDF &#x200B;](https://www.aemcomponents.dev/content/core-components-examples/library/core-content/pdf-viewer.html).

* Ondersteuning voor versnelde mobiele pagina&#39;s (AMP) van kerncomponenten is nu beschikbaar. Het helpt klanten sneller ervaringen op te doen door de paginaovergang onmiddellijk te maken wanneer ze de site betreden vanuit een mobiel zoekresultaat van Google, wat de betrokkenheid van gebruikers en SEO verbetert.
Zie [&#x200B; Steun van AMP voor de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=nl-NL) voor meer details.

* Verenigbaarheid met versie 1.0.2 van de [&#x200B; Laag van Gegevens van de Cliënt van Adobe &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=nl-NL).

* Bugfixes en verbeteringen van de codekwaliteit.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.7.0 is 9 juli 2020.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* De pagina met omgevingen is opnieuw ontworpen.

* Gesamberde omgevingen hebben nu een aparte status in Cloud Manager wanneer ze gehiberneerd zijn.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* Cloud Manager-pijpleidingen ondersteunen nu klantspecifieke variabelen en geheimen.

  Zie Variabelen voor pijplijn voor meer informatie.

* Verificatie-gebonden Private Maven Repositories worden nu ondersteund.

* De Cloud Manager build-container ondersteunt nu zowel Java 8 als Java 11.
Zie Java 11-ondersteuning gebruiken voor meer informatie.

### Opgeloste problemen {#bug-fixes-cm}

* De link van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de Developer Console rechtstreeks vanuit Cloud Manager gaf niet de optie weer om de omgeving van een Sandbox-programma te dehiberneren of te hiberneren.

* **annuleert** en **sparen** opties op de niet-Productiepijpleiding uitgeeft pagina waren niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.

### Bekende problemen {#known-issues}

* Als gevolg van een verandering in hoe de codedekking wordt berekend, is de *minimum* versie van de jakobstop nu 0.7.5.201505241946 (vrijgegeven Mei 2015). Klanten die expliciet verwijzen naar een oudere versie ontvangen een foutbericht in het proces voor codekwaliteit.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### Wat is er nieuw? {#what-is-new-foundations}

* [&#x200B; Logs kan aan de rekeningen van de Splunk &#x200B;](/help/implementing/developing/introduction/logging.md#splunk-logs) door:sturen, die organisaties toestaat om hun investering van de Splunk te gebruiken.

* [&#x200B; statisch, specifiek uitgangIP adres &#x200B;](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) kan voor uitgaand verkeer worden toegewezen dat in code van Java wordt geprogrammeerd, die voor sommige integratie nuttig kan zijn.

* GePorted AEM Analytics-cloudservice-interface van de klassieke gebruikersinterface naar de nieuwe interface van AEM. Ook de locatie van de Analytics-cloudservice in de AEM-opslagplaats verplaatst van `/etc` naar `/conf` , zodat deze overeenkomt met andere AEM-cloudservices.

* GePorted AEM Target cloudservice-interface van klassieke gebruikersinterface naar nieuwe interface van AEM. Ook de locatie van de Target-cloudservice in de AEM-opslagplaats verplaatst van `/etc` naar `/conf` om deze uit te lijnen met andere AEM-cloudservices.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Readiness Analyzer Release v1.0.2.

### Opgeloste problemen {#cra-bug-fixes}

* Eerdere versie van de CRA kan niet worden uitgevoerd op Adobe Experience Manager (AEM) 6.1. Er is expliciete ondersteuning toegevoegd om gebruikers in de beheerdersgroep toe te staan.

  Zie [&#x200B; Installerend CRA op AEM 6.1 &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html?lang=nl-NL#installing-on-aem61) voor meer details.

* De tijdstempel voor verlopen die in het samenvattingsrapport wordt weergegeven, is onjuist.

* CRA detecteerde dubbele aangepaste componenten.

* In AEM 6.1 was de inhoudscontrole afgesloten voordat de volledige inspectie werd voltooid. Uitzonderingsafhandeling is toegevoegd, zodat de controle kan overslaan en doorgaan totdat de volledige inspectie is voltooid.
