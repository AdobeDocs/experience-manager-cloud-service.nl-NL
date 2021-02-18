---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: 6f48b5daa5b47ad19db8b3431350111364f962fc
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] als Cloud Service weergegeven.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2021.1.0 is 3 februari 2021.
De volgende release (2021.2.0) vindt plaats op 25 februari 2021.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

### Beheer van inhoud zonder hoofd {#headless}

* **[GraphQL API voor levering](/help/assets/content-fragments/graphql-api-content-fragments.md)** van inhoudsfragmenten: Mogelijkheid om inhoudsfragmenten op te vragen met de syntaxis GraphQL en schema&#39;s die zijn gebaseerd op modellen van inhoudsfragmenten, voor uitvoer in JSON-indeling.

* **[Verificatieondersteuning voor GraphQL API-verzoeken](/help/assets/content-fragments/graphql-authentication-content-fragments.md)**: Mogelijkheid om GraphQL API-aanvragen te verifiëren met toegangstokens voor server-side API&#39;s.

* **[De RemotePage-component](/help/implementing/developing/hybrid/remote-page.md)**: Extra ondersteuning voor het weergeven en bewerken van externe SPA in AEM.

* **[Een externe SPA bewerken in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)**: Mogelijkheid toegevoegd om een zelfstandige toepassing van één pagina naar een AEM instantie te uploaden, bewerkbare gedeelten van inhoud toe te voegen en het schrijven van inhoud in te schakelen.

* Verbeterde JSON-uitvoer van GraphQL API, inclusief de mogelijkheid om RTF-tekst uit te voeren in JSON-indeling en landinstellingen.

* Ondersteuning voor het nesten van modellen van inhoudsfragmenten om het maken van geneste structuren voor inhoudsfragmenten mogelijk te maken via specifieke gegevenstypen van Content Fragment Reference of verwijzingen van inhoudsfragmenten inline in tekstvelden met meerdere regels.

* Aanvullende validatieregels beschikbaar in de gegevenstypen van het inhoudsfragmentmodel, waaronder &quot;uniek&quot;, &quot;vereist&quot; en &quot;vertaalbaar&quot;.

* Mogelijkheid om Content Fragment-modellen van tags te voorzien en het maken van Content Fragment toe te staan in een map met beleid per tag of pad.

* Verbeteringen op gebied van bruikbaarheid in de Content Fragment-editor, inclusief publicatieactie en weergave van het model waarop een fragment is gebaseerd.

* Mogelijkheid om JSON-uitvoer direct voor te vertonen in de Content Fragment Editor.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] als een  [!DNL Cloud Service] uitbreiding van de functie Slimme tags ter ondersteuning van de identificatie van trefwoorden en entiteiten in op tekst gebaseerde elementen. De tekst wordt geïdentificeerd, geïndexeerd, en ter beschikking gesteld als meta-gegevens om de onderzoekservaring zonder de behoefte aan om het even welke configuratie te verbeteren. Zie [Slimme tags](/help/assets/smart-tags.md).

* MXF-bestandsindeling wordt nu ondersteund. Zie [ondersteunde bestandsindelingen](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Product Experience Management: Het nieuwe lusje van eigenschappen van de &quot;Handel&quot;voor Activa en de Fragmenten van de Ervaring. Op dit tabblad kunt u producten/categorieën koppelen aan Elementen en Fragmenten ervaren. Op het tabblad vindt u ook real-time gegevens voor gekoppelde producten/categorieën en een koppeling om details weer te geven in de productconsole.

* Uitgebrachte CIF Venia Reference Site - 2021.02.02 met de nieuwste versie van CIF Core Components v1.7.0. Raadpleeg [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02) voor meer informatie.

* Uitgebrachte CIF Core Components v1.7.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0) voor meer informatie.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.2.0 is 11 februari 2021.

### Nieuwe functies {#what-is-new-cloud-manager}


* Klanten van middelen kunnen nu kiezen wanneer en waar ze hun Brand Portal-instantie op een zelfbedieningsmanier implementeren via de interface van Cloud Manager. Voor een regelmatig (niet-sandbox) programma met middelenoplossing kan het Brand Portal nu worden ingericht op de productieomgeving. De levering kan slechts eenmaal op het milieu van de Productie worden gedaan.

* Het AEM Project Archetype dat in Project en Sandbox creatie wordt gebruikt is bijgewerkt aan versie 25.

* De lijst met afgekeurde API&#39;s die tijdens het scannen van code zijn geïdentificeerd, is verfijnd en bevat nu extra klassen en methoden die zijn afgekeurd in de meest recente Cloud Service SDK-releases.

* SonarQube-profiel voor Cloud Manager bijgewerkt om Sonar rule squid:S2142 te verwijderen. Dit is niet langer in conflict met de controles van de Onderbreking van de thread.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk niet domeinnaam kan toevoegen/bijwerken omdat het bijbehorende milieu of een lopende pijpleiding in bijlage aan het of momenteel in het wachten op de goedkeuringsstap heeft.

* Eigenschappen die zijn ingesteld in `pom.xml`-bestanden van de klant die vooraf zijn voorzien van sonar, worden nu dynamisch verwijderd om fouten met het scannen van build en kwaliteit te voorkomen.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein in gebruik is die momenteel wordt opgesteld.

* Er zijn aanvullende regels voor de kwaliteit van code toegevoegd om compatibiliteitsproblemen met Cloud Servicen te verhelpen.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Het vergelijken van SSL-certificaat met een domeinnaam is niet langer hoofdlettergevoelig.

* De gebruikersinterface van Cloud Manager stelt de gebruiker nu op de hoogte als de persoonlijke certificaatsleutels niet voldoen aan de limiet van 2048 bits met een geschikt foutbericht.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein wordt gebruikt die momenteel wordt opgesteld.

* In sommige gevallen kan een intern probleem ertoe leiden dat het verwijderen van het milieu vastloopt.

* Sommige pijpleidingsmislukkingen werden verkeerd gemeld als pijpleidingsfouten.

## AEM als Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### Nieuwe functies {#what-is-new-foundation}

* Server-aan-server voor authentiek verklaarde API vraag - produceer de aangewezen toegangstokens om voor authentiek verklaarde server-aan-server API vraag tussen uw externe toepassingen en AEM als milieu&#39;s van de Cloud Service te maken. Lees meer door [de documentatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) te lezen of door de [zelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) te raadplegen.

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM als Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren.

Voor deze afgifte zijn twee nieuwe analysatoren toegevoegd:

* herpuntanalyse
* bundle-nativecode

Raadpleeg de documentatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) voor meer informatie.

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.2.4 is 10 februari 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* Bij het toewijzen van meerdere gebruikers werden IMS-id&#39;s van sommige gebruikers onjuist toegewezen. Dit is opgelost.

### Releasedatum {#release-date-ctt-feb}

De releasedatum voor Content Transfer Tool v1.2.2 is 1 februari 2021.

### Nieuw in gereedschap voor inhoudsoverdracht {#what-is-new-ctt}

* Nieuwe mogelijkheid en interface toegevoegd aan het gereedschap voor inhoudsoverdracht - Toewijzing van gebruikers. Deze functie wijst automatisch bestaande gebruikers en groepen toe aan hun Adobe Identity Management System-id&#39;s als onderdeel van de migratie van inhoud.
Raadpleeg [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) voor meer informatie.
* Met het gereedschap Inhoud overbrengen worden nu alle groepen en gebruikers gemigreerd waarnaar in de migratieset wordt verwezen, inclusief kinderen.
* Gebruikers mogen bepaalde paden onder `/etc` selecteren bij het maken van migratiesets.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.2 is 18 februari 2021.

### Nieuw in Analyzer van Beste praktijken {#what-is-new-bpa}

* Mogelijkheid om het gebruik van de implementatie van AEM Forms en AEM Forms te detecteren en gebieden aan te geven die van belang zijn voor de migratie naar AEM Forms als Cloud Service.
* Mogelijkheid om het gebruik en het aantal aangepaste componenten en sjablonen te detecteren en te rapporteren.
* Capaciteit om het type van knoopopslag en gebruikte gegevensopslag te ontdekken.
* Mogelijkheid om het gebruik van Dynamic Media te detecteren.
* Mogelijkheid om de gebruikte Java-versie te detecteren.

## Tools voor herstructurering van code {#code-refactoring-tools}

### Nieuw in de Hulpmiddelen {#what-is-new-crt} van de Refactoring van de Code

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat verschillende foutoplossingen voor de Repository Modernizer.
Raadpleeg [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) voor meer informatie over deze plug-in.

### Opgeloste problemen {#bug-fixes-crt}

* Verschillende opgeloste problemen zijn opgelost in de Repository Modernizer.
Verwijs naar [Middel GitHub: aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer informatie.








