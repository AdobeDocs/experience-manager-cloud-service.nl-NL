---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: dc66eca7b789cf3be1aeae3d63935362ab6f918a
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als een Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2021.5.0 is 27 mei 2021.
De volgende release (2021.6.0) vindt plaats op 24 juni 2021.

## AEM als Stichting van de Cloud Service {#foundation}

### Wat in AEM als Stichting van de Cloud Service {#what-is-new-foundation} Nieuw is

* [Prereleaskanaal](/help/release-notes/prerelease.md): Bekijk de volgende functies een volledige maand voordat u live gaat met de productie.

* [API-afdrukking](/help/release-notes/deprecated-apis.md): er is een lijst beschikbaar met de meest recente verouderde API&#39;s die als Cloud Service AEM worden gebruikt.

* [AEM als Cloud Service SDK Build Analyzer Maven Plugin](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): Werk uw gemaakte projecten bij naar de nieuwste versie, die een verouderde Java API-controle en andere verbeteringen bevat.

## [!DNL Adobe Experience Manager Sites] als  [!DNL Cloud Service] {#sites}

### Nieuw in [!DNL Sites] {#what-is-new-sites}

* U kunt binnenkort de inhoud op een nieuwe [Voorvertoningslaag](/help/sites-cloud/authoring/fundamentals/previewing-content.md) controleren om de weergave van de uiteindelijke ervaring te simuleren zoals u dat zou doen op de laag Publiceren. Dit wordt ingeschakeld door de AEM Sites Managed Publication-wizard, waarmee u nu een publicatiebestemming kunt kiezen tussen Publiceren of Voorvertoning. Ervaring met Voorvertoning is dan toegankelijk via een specifieke URL. Na validatie bij Voorvertoning kan inhoud op de gebruikelijke manier van Auteur worden gepubliceerd om te publiceren. Het inschakelen van de voorvertoningsservice in AEM als een Cloud Service-omgeving zal in de komende weken geleidelijk worden geïmplementeerd.

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuwe functies beschikbaar in het prereleasekanaal {#what-is-new-assets-prerelease}

* Metagegevensschema&#39;s kunnen rechtstreeks op de mapeigenschappen worden toegepast.

   ![Metagegevensschema toevoegen uit mapeigenschappen](/help/assets/assets/metadata-schema-folder-properties.png)

* Met het gereedschap Asset Bulk Ingestor kunt u metagegevens toevoegen tijdens een grote opname.

* Dankzij de verbeteringen in de gebruikerservaring wordt het aantal elementen in een map weergegeven. [!DNL Assets] geeft 1000+ weer voor meer dan 1000 elementen in een map.

   ![Het aantal elementen in een map wordt weergegeven op de interface](/help/assets/assets/browse-folder-number-of-assets.png)

### Buizen gecorrigeerd in [!DNL Assets] {#assets-bugs-fixed}

* Tijdens het uploaden van zeer grote bestanden loopt [!DNL Experience Manager desktop app] vast. (CQ-4320942)
* De werkbalkopties verschillen wanneer dezelfde verzameling in een map is geselecteerd en wanneer deze is geselecteerd uit een zoekresultaat. (CQ-4321406)

#### Nieuw in [!DNL Dynamic Media] {#what-is-new-dm}

* Dankzij de Pixelverhouding van Smart Imaging Device (DPR) en de optimalisatie van de netwerkbandbreedte kunt u beelden van de beste kwaliteit efficiënt leveren op apparaten met beeldschermen met hoge resolutie en beperkte netwerkbandbreedte. Zie [Veelgestelde vragen over slimme beeldverwerking](/help/assets/dynamic-media/imaging-faq.md).

   >[!NOTE]
   >
   >De releasetijdlijn voor de bovenstaande verbeteringen voor Smart Imaging is:
   >
   >* Noord-Amerika 24 mei 2021 in NA,
      >
      >
   * Europa, het Midden-Oosten en Afrika 25 juni 2021,
      >
      >
   * Azië-Stille Oceaan 19 juli 2021.


* Introductie van ondersteuning voor AVIF-afbeeldingsindeling van volgende generatie in levering [!DNL Dynamic Media] (fmt URL-modifier).

   >[!NOTE]
   >
   >De releasetijdlijn voor AVIF-ondersteuning is:
   >
   >* Noord-Amerika 10 mei 2021,
      >
      >
   * Europa, het Midden-Oosten en Afrika 24 mei 2021,
      >
      >
   * Azië-Stille Oceaan 24 juni 2021.


## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.5.0.

### Releasedatum {#release-date-cm-may}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.5.0 is 6 mei 2021.
De volgende release is gepland voor 10 juni 2021.

### Wat is er nieuw?{#what-is-new-may}

* De PackageOverlaps kwaliteitsregel ontdekt nu gevallen waar het zelfde pakket veelvoudige tijden, d.w.z. in veelvoudige ingebedde plaatsen, in de zelfde opgestelde pakketreeks werd opgesteld.

* Het eindpunt van de repository in de Public API bevat nu de Git URL.

* Het implementatielogboek dat door een gebruiker van Cloud Manager wordt gedownload, is begrijpelijker en bevat nu details over fouten en successcenario&#39;s.

* Intermitterende fouten die werden aangetroffen tijdens het doorvoeren van code naar Adobe-it, zijn nu opgelost.

* Invoegtoepassing voor handel kan nu worden toegepast op Sandbox-programma&#39;s tijdens de workflow van het bewerkingsprogramma.

* De ervaring met het bewerkingsprogramma is vernieuwd.

* De lijst van de Namen van het Domein in de pagina van Details van het Milieu zal tot 250 namen van Domein via paginering tonen.

* Het lusje van Oplossingen in Add Programma en geef de werkschema&#39;s van het Programma uit zal de oplossing tonen, zelfs als slechts één oplossing voor het Programma beschikbaar is.

* Het foutenbericht in het bouwstijlstaplogboek toen de bouwstijl geen opgestelde inhoudspakketten produceerde was onduidelijk.

### Opgeloste problemen {#bug-fixes-cm-may}

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* In plaats van &#39;verwijderde&#39; variabelen te verwijderen, markeert de API voor pijpleidingvariabelen deze alleen met status **DELETED**.

* Sommige kwaliteitskwesties van het type Code Smell hadden een onjuiste invloed op de beoordeling Betrouwbaarheid.

* Omdat jokertekendomeinen niet worden ondersteund, staat de gebruikersinterface de gebruiker niet toe een jokertekendomein in te dienen.

* Wanneer een pijpleidingsuitvoering tussen middernacht en 1am UTC werd begonnen, werd de artefactversie die door de Manager van de Wolk werd geproduceerd niet gewaarborgd om groter te zijn dan een versie die de vorige dag werd gecreeerd.

* Tijdens de opstelling van het programma Sandbox, zodra het project met steekproefcode met succes is gecreeerd, zal Manage Git als verbinding van de heldenkaart in de pagina van het Overzicht verschijnen.

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.4.0 is 11 mei 2021.

### Wat is er nieuw?{#what-is-new-ctt-may}

* Met deze versie van het gereedschap Inhoud overbrengen maakt u tekstuitvoeringen voor elementen die naar de Cloud Service worden gemigreerd. Tekstuitvoeringen zijn vereist voor ondersteuning van het zoeken naar volledige tekst op ingesloten elementen.
* Het maximumaantal migratiesets van Content Transfer Tool dat een gebruiker kan maken, is verhoogd van 4 naar 10.

### Opgeloste problemen {#bug-fixes-ctt-may}

* De veelvoudige insectenmoeilijke situaties verwant met auto-verfrissen eigenschap in het Hulpmiddel van de Overdracht van de Inhoud UI.
* Het hulpmiddel van de Overdracht van de inhoud met `wipe=true` resulteerde in onjuiste tellerindex op het doel. Dit is opgelost.

## Commerce Add-on {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Pagineringsondersteuning voor gekoppelde inhoud in eigenschappen van productconsole

### Opgeloste problemen {#bug-fixes-commerce}

* Miniaturen van middelen worden niet weergegeven op het tabblad Middelen van de producteigenschappen

* Breadcrumb herstelt voorvertoningsgegevens in productconsole
