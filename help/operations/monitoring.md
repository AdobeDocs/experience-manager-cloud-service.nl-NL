---
title: Infrastructuur- en servicecontrole in AEM as a Cloud Service
description: Infrastructuur- en servicecontrole in AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
source-git-commit: a95c914502fbb279bd44abd6d5d4d141707e9a59
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Infrastructuur- en servicecontrole in AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service biedt waarneming en controle van: infrastructuur, services en gebruikerservaring. Aangezien verschillende oplossingen worden gebruikt en er verscheidene lagen van controle zijn, wordt deze pagina georganiseerd in drie secties:

* [Externe beschikbaarheid](#external-availability)
* [Interne module bewaking](#module-monitoring)
* [Waarmerking van de klant](#customer-observability)

AEM as a Cloud Service gebruikt honderden native monitoren in de cloud om de status van elke omgeving (24/7) gedurende 365 dagen per jaar voortdurend te rapporteren. De monitordefinities zijn niet statisch, zij worden voortdurend herzien om het vroege opsporingsvermogen te verbeteren. Bovendien heeft Adobe oproepprocedures ingesteld om op waarschuwingen te reageren.

Als u informatie nodig hebt over andere typen controle, zoals registratie of bewaking via Cloud Manager, raadpleegt u [Aanvullende bronnen](#resources).

## Externe beschikbaarheid {#external-availability}

De externe beschikbaarheid bestaat uit twee delen: Service Edge en Aangepaste bewaking.

### Service Edge {#service-edge}

Al uw milieu&#39;s van AEM as a Cloud Service worden gecontroleerd op beschikbaarheid. De Service Edge Monitoring is echter alleen ingesteld voor productieomgevingen en de meetgegevens worden gebruikt om de SLA van de klant te berekenen. Hierbij wordt rekening gehouden met de milieu-runtime en de AEM as a Cloud Service CDN. De Controle van de Rand van de dienst gebruikt vijf verschillende plaatsen dicht bij uw gekozen gebied en controleert periodiek voor beschikbaarheid. De onbeschikbaarheid van een site activeert een waarschuwing en activeert Adobe-call supportteams en processen.

### Aangepaste controle {#custom-monitoring}

Met Aangepaste controle kunnen klanten optioneel maximaal vijf verschillende URL&#39;s voor westeigenschappen leveren [live gaan](/help/journey-migration/go-live.md). Deze URL&#39;s moeten geldig zijn en een HTTP 200-antwoordcode retourneren. Deze monitoren ondersteunen klanten die [hun eigen CDN plaatsen](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) voor de Adobe DN en om het even welk extern verkeer dat binnen dienst voor AEM werkt die niet onder Adobe controle CDN is as a Cloud Service. Het alarm resulterend uit de controles van de Controle van de Controle van de Controle van de Douane neemt steunteams en processen van de Adobe in dienst.

>[!NOTE]
>
> Deze functionaliteit wordt alleen aangeboden voor klanten met [Geavanceerde cloudondersteuning.](https://experienceleague.adobe.com/docs/support-resources/data-sheets/overview.html#support-add-ons) Neem contact op met het Adobe-accountteam als u vragen hebt.

## Interne modulemonitoring {#module-monitoring}

Terwijl de externe beschikbaarheid op eindgebruikercontrole wordt geconcentreerd, merkt de interne module controle op of de architecturale subsystemen nominaal zonder eigenschap of prestatiesdegradatie werken. Als er een probleem is, worden de alarm teweeggebracht zodat kunnen de reparaties of automatisch of door de betrokkenheid van het verrichtingenteam, met het doel worden gedaan om gecompromitteerde beschikbaarheid te verhinderen. Er zijn verschillende categorieën monitoren, die hieronder worden weergegeven, zijn enkele voorbeelden van controles:

* Het CPU-wachttijdpercentage overschrijdt een bepaalde drempel niet.
* Instantieherplaatsingen overschrijden een bepaalde frequentie niet.
* Schijfgebruik is onder een bepaalde drempel.
* De grootte van de opslagplaats van de auteur is binnen bepaalde grenzen.
* Back-upbewerkingen zijn voltooid.
* De gezondheid en de prestaties van het gegevensbestand worden gecontroleerd.
* AEM Cloud-services gedragen zich zoals verwacht, inclusief geen geblokkeerde replicatiestijlen, consistente gegevens en query&#39;s voor prestaties.

Extra controles worden toegevoegd aan omgevingen die zijn ingericht voor Forms. Controledefinities zijn niet statisch en kunnen worden gewijzigd en bijgewerkt.

## Waarmerking van de klant {#customer-observability}

Klanten kunnen de [New Relic Application Performance Monitoring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html) -suite met prestatiegegevens in real-time die worden verzameld en in kaart gebracht voor analyse en probleemoplossing. Met behulp van de monitorsuite kunnen klanten rechtstreeks verschillende meetgegevens observeren, zoals: De prestatiesmetriek van JVM, transactietijd voor Java™, achtergrond externe vraag, en gegevensbestandvraag.

## Aanvullende bronnen {#resources}

* [New Relic Application Performance Monitoring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html)
* [Aanmelden voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html)
* [Monitoringomgevingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html)
