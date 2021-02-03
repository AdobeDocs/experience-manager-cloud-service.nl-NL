---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: cd392473d4e8ebee20b41c6c979121fe81819a40
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] als Cloud Service weergegeven.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2021.1.0 is 3 februari 2021.
De volgende release (2021.2.0) vindt plaats op 25 februari 2021.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

* **[HTTP-API voor](/help/assets/content-fragments/assets-api-content-fragments.md)** inhoudsfragment: Voeg de mogelijkheid toe om variaties van inhoudsfragmenten toe te voegen/bij te werken en te verwijderen met de HTTP-API.

* **[GraphQL API voor levering](/help/assets/content-fragments/graphql-api-content-fragments.md)** van inhoudsfragmenten: Mogelijkheid om inhoudsfragmenten op te vragen met de syntaxis GraphQL en schema&#39;s die zijn gebaseerd op modellen van inhoudsfragmenten, voor uitvoer in JSON-indeling.

* **[Verificatieondersteuning voor GraphQL API-verzoeken](/help/assets/content-fragments/graphql-authentication-content-fragments.md)**: Mogelijkheid om GraphQL API-aanvragen te verifiëren met toegangstokens voor server-side API&#39;s.

* Verbeterde JSON-uitvoer van GraphQL API, inclusief de mogelijkheid om RTF-tekst uit te voeren in JSON-indeling en landinstellingen.

* Ondersteuning voor het nesten van modellen van inhoudsfragmenten om het maken van geneste structuren voor inhoudsfragmenten mogelijk te maken via specifieke gegevenstypen van Content Fragment Reference of verwijzingen van inhoudsfragmenten inline in tekstvelden met meerdere regels.

* Aanvullende validatieregels beschikbaar in de gegevenstypen van het inhoudsfragmentmodel, waaronder &quot;uniek&quot;, &quot;vereist&quot; en &quot;vertaalbaar&quot;.

* Mogelijkheid om Content Fragment-modellen van tags te voorzien en het maken van Content Fragment toe te staan in een map met beleid per tag of pad.

* Verbeteringen op gebied van bruikbaarheid in de Content Fragment-editor, inclusief publicatieactie en weergave van het model waarop een fragment is gebaseerd.

* Mogelijkheid om JSON-uitvoer direct voor te vertonen in de Content Fragment Editor.


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

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.1.0 is 14 januari 2021.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* De instantie van de Productie van activa kan de merkportstatus op **Milieu** detailpagina als *In behandeling* tonen zonder de gebruiker toe te staan om het even welke actie te ondernemen.

* Bij het activeren van een dehibernate vanuit Cloud Manager werd soms een foutbericht weergegeven, zelfs wanneer de dehibernatie met succes werd gestart.

* Zeldzame gevallen van fouten die zijn aangetroffen bij het creëren of verwijderen van een omgeving, zijn opgelost.

## Tools voor herstructurering van code {#code-refactoring-tools}

### Nieuw in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat foutoplossingen voor de AEM Dispatcher Converter en de Repository Modernizer en ondersteunt ook een nieuw hulpprogramma - Index Converter. Raadpleeg [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) voor meer informatie over deze plug-in.

* De Omzetter van de index is een nut dat kan worden gebruikt om de Definities van de Index van de Douane van een klant om te zetten in AEM als Cloud Service compatibele Definities van de Index OAK. Raadpleeg [Indexconverter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) voor meer informatie.

* Nieuwe functie toegevoegd aan [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) die een afzonderlijk pakket `ui.config` maakt om alle OSGi-configuraties te bevatten.

### Opgeloste problemen {#crt-bug-fixes}

* Verscheidene insectenmoeilijke situaties die op de AEM Convertor van de Verzender en de Modernizer van de Bewaarplaats worden gedaan hulpmiddelen. Raadpleeg [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) en [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## AEM als Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### Nieuwe functies {#what-is-new-foundation}

* Server-aan-server voor authentiek verklaarde API vraag - produceer de aangewezen toegangstokens om voor authentiek verklaarde server-aan-server API vraag tussen uw externe toepassingen en AEM als milieu&#39;s van de Cloud Service te maken. Lees meer door [de documentatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) te lezen of door de [zelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) te raadplegen.

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM als Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren.

Voor deze afgifte zijn twee nieuwe analysatoren toegevoegd:

* herpuntanalyse
* bundle-nativecode

Raadpleeg de documentatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) voor meer informatie.

## Tools voor de overgang naar Cloud Service {#code-transition-tools}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.2.2 is 1 februari 2021.

### Nieuw in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Nieuwe mogelijkheid en interface toegevoegd aan het gereedschap voor inhoudsoverdracht - Toewijzing van gebruikers. Deze functie wijst automatisch bestaande gebruikers en groepen toe aan hun Adobe Identity Management System-id&#39;s als onderdeel van de migratie van inhoud. Raadpleeg [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) voor meer informatie.
* Met het gereedschap Inhoud overbrengen worden nu alle groepen en gebruikers gemigreerd waarnaar in de migratieset wordt verwezen, inclusief kinderen.
* Gebruikers mogen bepaalde paden onder `/etc` selecteren bij het maken van migratiesets.
