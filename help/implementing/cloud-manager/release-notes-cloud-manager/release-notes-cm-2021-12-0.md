---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.12.0
description: Dit zijn de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service release 2021.12.0.
feature: Release Information
source-git-commit: bd31dc0ca5b0f4cd84314dba67c8a611f490d377
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.12.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.12.0 is 16 december 2021. De volgende release is gepland voor 20 januari 2022.

## Wat is er nieuw? {#what-is-new}

* De commit hash, die al zichtbaar is in de UI, wordt nu ook verstrekt in API.
* De pagina van de Activiteit omvat nu een pop-over voor het runnen van pijpleidingen die een samenvatting van pijpleidingsdetails bij-a-blik verstrekt.
* Er zijn updates toegevoegd om aanvullende details op de pagina Activiteiten op te nemen.
* Het tabblad Leren in Cloud Manager bevat nu snelle toegang tot API-hulplijnen en bijbehorende bronnen.
* Een gebruiker met de rol van de Manager van de Plaatsing kan nu de project/de aanmaaktovenaar van de Tak voor een bewaarplaats zonder takken van het actiemenu op de pagina van bewaarplaatsen in werking stellen.
* De Manager van de Plaatsing, die in toevoegt of pijpleidingswerkschema uitgeeft, wordt nu geïnformeerd over hoe te om een tak of een project tot stand te brengen als de geselecteerde bewaarplaats geen takken heeft.
* Er is een nieuwe zelfbedieningsfunctie voor Cloud Manager toegevoegd om [het toevoegen van vrije-vormvariabelen en geheimen op milieuniveau.](/help/implementing/cloud-manager/environment-variables.md)
* Met de nieuwe [Invoegtoepassing demo&#39;s referentie](/help/journey-sites/demos-add-on/overview.md) (beschikbaar op 17 december 2021) kunnen de meest recente demo-codebases voor AEM producten worden geïnstalleerd en klaar zijn om te worden geïmplementeerd via de nieuwe [snel site maken](/help/journey-sites/quick-site/overview.md) in sites.
* De pijpleidingen aan de voorzijde steunen nu pijpleidingsvariabelen.
* Schermen kunnen nu voor alle sandboxen worden ingeschakeld in het dialoogvenster Program Edit.
* De begeleiding die door de vraag-aan-actie kaart in de overzichtspagina wordt verstrekt is verfrist om zijn vereniging met de productie volledige stapelpijpleiding nauwkeurig te weerspiegelen.
* De verhogingen aan de pagina van de Activiteit werden toegevoegd aan oppervlakte extra details van toepassing op pijpleidingen met inbegrip van broncode, verbind identiteitskaart, enz.
* Er is een kleine update uitgevoerd naar de gebruikersinterface tijdens het kopiëren van TXT-items (&quot;TXT-waarde&quot; in plaats van &quot;TXT-record&quot;) om mogelijke verwarring te voorkomen.
* [De documentatie met betrekking tot certificaatfouten](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-errors) is bijgewerkt om aanvullende voorbeelden samen met het oplossen van problemen te behandelen.
* Een optie is nu beschikbaar in de front-end pijpleiding uitvoering om vóór plaatsing aan productie te verwerpen of goed te keuren.
* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 32.


## Opgeloste problemen {#bug-fixes}

* De functionaliteit en UI testartefacten waren niet inbegrepen in het bouwstijlstaplogboek.
* De logbestanden voor de teststappen voor het product, de functie en de gebruikersinterface zijn niet toegankelijk via de openbare API.
* In zeldzame gevallen is de koppeling van de pagina met omgevingsdetails naar de service Publiceren of Voorvertonen niet functioneel.
* De volledige pijpleidingen van de stapelproductie blijven genoemd &quot;Productiepijpleiding&quot;zelfs wanneer de gebruiker een verschillende naam op het naamgebied ingaat.
