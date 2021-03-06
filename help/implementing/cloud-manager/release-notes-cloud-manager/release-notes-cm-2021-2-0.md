---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.2.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.2.0
exl-id: 281f9523-dec2-44f1-9459-5a45d48489d9
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.2.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.2.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.2.0 is 11 februari 2021.

## Cloud Manager {#cloud-manager}

### Wat is er nieuw? {#what-is-new}

* Klanten van middelen kunnen nu kiezen wanneer en waar ze hun Brand Portal-exemplaar op een zelfbedieningsmanier implementeren via de interface van Cloud Manager. Voor een normaal (niet-sandbox) programma met middelenoplossing kan Brand Portal nu worden ingericht op de productieomgeving. De levering kan slechts eenmaal op het milieu van de Productie worden gedaan.

* Het AEM Project Archetype dat in Project en Sandbox creatie wordt gebruikt is bijgewerkt aan versie 25.

* De lijst met afgekeurde API&#39;s die tijdens het scannen van code zijn geïdentificeerd, is verfijnd en bevat nu extra klassen en methoden die zijn afgekeurd in de meest recente SDK-versies van de Cloud Service.

* SonarQube-profiel voor Cloud Manager bijgewerkt om Sonar rule squid:S2142 te verwijderen. Dit is niet langer in conflict met de controles van de Onderbreking van de thread.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk niet domeinnaam kan toevoegen/bijwerken omdat het bijbehorende milieu of een lopende pijpleiding in bijlage aan het of momenteel in het wachten op de goedkeuringsstap heeft.

* Eigenschappen ingesteld in klant `pom.xml` bestanden die vooraf met sonar zijn gemaakt , worden nu dynamisch verwijderd om fouten met het maken van opbouwen en het scannen van kwaliteit te voorkomen .

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein in gebruik is die momenteel wordt opgesteld.

* Er zijn aanvullende regels voor de kwaliteit van code toegevoegd om compatibiliteitsproblemen met Cloud Servicen te verhelpen.

### Opgeloste problemen  {#bug-fixes}

* Het vergelijken van SSL-certificaat met een domeinnaam is niet langer hoofdlettergevoelig.

* De gebruikersinterface van Cloud Manager stelt de gebruiker nu op de hoogte als de persoonlijke certificaatsleutels niet voldoen aan de limiet van 2048 bits met een geschikt foutbericht.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein wordt gebruikt die momenteel wordt opgesteld.

* In sommige gevallen kan een intern probleem ertoe leiden dat het verwijderen van het milieu vastloopt.

* Sommige pijpleidingsmislukkingen werden verkeerd gemeld als pijpleidingsfouten.
