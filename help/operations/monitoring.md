---
title: Infrastructuur- en servicecontrole in AEM as a Cloud Service
description: Infrastructuur- en servicecontrole in AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
source-git-commit: f55439552e253b8b71b40525454130c6f163e6d4
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Infrastructuur- en servicecontrole in AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service biedt waarneming en controle van: infrastructuur, diensten en gebruikerservaring. Aangezien verschillende oplossingen worden gebruikt en er verscheidene lagen van controle zijn, wordt deze pagina georganiseerd in drie secties:

* [Externe beschikbaarheid](#external-availability)
* [Interne module bewaking](#module-monitoring)
* [Waarmerking van de klant](#customer-observability)

AEM as a Cloud Service gebruikt honderden native monitoren in de cloud om de status van elke omgeving (24/7) gedurende 365 dagen per jaar voortdurend te rapporteren. De monitordefinities zijn niet statisch, zij worden voortdurend herzien om het vroege opsporingsvermogen te verbeteren. Bovendien, heeft Adobe opvraagprocedures opstelling om op alarm te antwoorden.

Als u informatie nodig hebt over andere typen bewaking, zoals loggen of controleren via Cloud Manager, raadpleegt u de [Aanvullende bronnen](#resources) sectie.

## Externe beschikbaarheid {#external-availability}

De externe beschikbaarheid bestaat uit twee delen: Service Edge en Aangepaste bewaking.

### Service Edge {#service-edge}

Alle AEM as a Cloud Service omgevingen worden gecontroleerd op beschikbaarheid. De Service Edge Monitoring is echter alleen ingesteld voor productieomgevingen en de meetgegevens worden gebruikt om de SLA van de klant te berekenen. Hierbij wordt rekening gehouden met de milieu-runtime en de AEM as a Cloud Service CDN. De Controle van de Rand van de dienst gebruikt vijf verschillende plaatsen dicht bij uw gekozen gebied en controleert periodiek voor beschikbaarheid. De onbeschikbaarheid van een site zal een waarschuwing teweegbrengen en zal Adobe-vraag steunteams en processen in dienst nemen.

### Aangepaste controle {#custom-monitoring}

Met Aangepaste controle kunnen klanten maximaal vijf verschillende URL&#39;s voor westeigenschappen opgeven voordat ze [live gaan](/help/journey-migration/go-live.md). Deze URL&#39;s moeten geldig zijn en een HTTP 200-antwoordcode retourneren. Deze monitoren ondersteunen klanten die [hun eigen CDN plaatsen](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) voor Adobe CDN en om het even welk extern verkeer dat vóór AEM as a Cloud Service verplettert die niet onder de controle van Adobe is. Het alarm resulterend de controles van de Controle van de Controle van de Controle van de Douane zal Adobe steunteams en processen in dienst nemen.

>[!NOTE]
>
> Deze functionaliteit wordt alleen aangeboden voor klanten met [Geavanceerde cloudondersteuning.](https://experienceleague.adobe.com/docs/support-resources/data-sheets/overview.html#support-add-ons) Als u vragen hebt, kunt u een ondersteuningskwestie aankaarten via de beheerconsole.

## Interne modulemonitoring {#module-monitoring}

Hoewel de externe beschikbaarheid is gericht op controle door de eindgebruiker, merkt de interne module controle op of de architecturale subsystemen nominaal werken zonder eigenschap of prestatievermindering. In het geval van een probleem, worden de alarm teweeggebracht zodat kunnen de reparaties of automatisch of door de betrokkenheid van het verrichtingsteam, met als doel om gecompromitteerde beschikbaarheid te verhinderen worden gedaan. Er zijn verschillende categorieën monitoren, die hieronder worden weergegeven, zijn enkele voorbeelden van controles:

* Het CPU-wachttijdpercentage overschrijdt een bepaalde drempel niet.
* Instantieherplaatsingen overschrijden een bepaalde frequentie niet.
* Schijfgebruik is onder een bepaalde drempel.
* De grootte van de opslagplaats van de auteur is binnen bepaalde grenzen.
* Back-upbewerkingen zijn voltooid.
* De gezondheid en de prestaties van het gegevensbestand worden gecontroleerd.
* AEM Cloud-services gedragen zich zoals verwacht, inclusief geen geblokkeerde replicatiestijlen, consistente gegevens en vragen over prestaties.

Extra controles worden toegevoegd aan omgevingen die zijn ingericht voor Forms. Houd er rekening mee dat controledefinities niet statisch zijn en kunnen worden gewijzigd en bijgewerkt.

## Waarmerking van de klant {#customer-observability}

Klanten kunnen de [New Relic Application Performance Monitoring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html) -suite met prestatiegegevens in real-time die worden verzameld en in kaart gebracht voor analyse en probleemoplossing. Met behulp van de monitorsuite kunnen klanten rechtstreeks verschillende meetgegevens observeren, zoals: De prestatiesmetriek van JVM, transactietijd voor Java, achtergrond externe vraag en gegevensbestandvraag.

## Aanvullende bronnen {#resources}

* [New Relic Application Performance Monitoring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html)
* [Aanmelden voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html)
* [Monitoringomgevingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html)
