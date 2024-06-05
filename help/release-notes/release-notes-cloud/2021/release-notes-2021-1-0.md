---
title: Opmerkingen bij de release 2021.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2021.1.0."
exl-id: cd639736-6e3d-4b69-b8ae-11e4e6490535
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Experience Manager] as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.1.0 is 3 februari 2021.
De volgende release (2021.2.0) vindt plaats op 25 februari 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[HTTP-API voor inhoudsfragment](/help/assets/content-fragments/assets-api-content-fragments.md)**: Voeg de mogelijkheid toe om variaties van inhoudsfragmenten toe te voegen/bij te werken en te verwijderen met de HTTP-API.

* **[GraphQL API voor levering van inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)**: Mogelijkheid om inhoudfragmenten te controleren met gebruik van GraphQL-syntaxis en schema&#39;s die zijn gebaseerd op modellen van inhoudsfragmenten, voor uitvoer in JSON-indeling.

* **[Verificatieondersteuning voor GraphQL API-verzoeken](/help/headless/security/authentication.md)**: Mogelijkheid om GraphQL API-aanvragen te verifiëren met toegangstokens voor server-side API&#39;s.

* Verbeterde JSON-uitvoer van de GraphQL API, inclusief de mogelijkheid om RTF-tekst uit te voeren in JSON-indeling en landinstellingen.

* Ondersteuning voor het nesten van modellen van inhoudsfragmenten om het maken van geneste structuren voor inhoudsfragmenten mogelijk te maken, via specifieke gegevenstypen van Content Fragment Reference of inline verwijzingen van inhoudsfragmenten in tekstvelden met meerdere regels.

* Aanvullende validatieregels beschikbaar in de gegevenstypen van het inhoudsfragmentmodel, waaronder &quot;uniek&quot;, &quot;vereist&quot; en &quot;vertaalbaar&quot;.

* Mogelijkheid om Content Fragment-modellen van tags te voorzien en het maken van Content Fragment toe te staan in een map met beleid per tag of pad.

* Verbeteringen op gebied van bruikbaarheid in de Content Fragment-editor, inclusief publicatieactie en weergave van het model waarop een fragment is gebaseerd.

* Mogelijkheid om JSON-uitvoer direct voor te vertonen in de Content Fragment Editor.


## [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] als [!DNL Cloud Service] breidt de functionaliteit Slimme tags uit ter ondersteuning van de identificatie van trefwoorden en entiteiten in op tekst gebaseerde elementen. De tekst wordt geïdentificeerd, geïndexeerd, en ter beschikking gesteld als meta-gegevens om de onderzoekservaring zonder de behoefte aan om het even welke configuratie te verbeteren. Zie [Slimme tags](/help/assets/smart-tags.md).

* MXF-bestandsindeling wordt nu ondersteund. Zie [ondersteunde bestandsindelingen](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Product Experience Management: Nieuw tabblad &#39;Commerce&#39;-eigenschappen voor Elementen en Geniet-fragmenten. Op dit tabblad kunt u producten/categorieën koppelen aan Elementen en Fragmenten ervaren. Op het tabblad vindt u ook real-time gegevens voor gekoppelde producten/categorieën en een koppeling om details weer te geven in de productconsole.

* Release CIF Venia Reference Site - 2021.02.02 die de nieuwste versie CIF Core Components versie v1.7.0 bevat. Zie [CIF Venia-referentiegebied](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02) voor meer informatie .

* Uitgegeven CIF Core Components v1.7.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0) voor meer informatie .

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.1.0 is 14 januari 2021.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Assets Production-instantie kan soms de Brand Portal-status weergeven op het tabblad **Omgevingen** detailpagina als *In behandeling* zonder dat de gebruiker een actie mag uitvoeren.

* Bij het activeren van een dehibernate vanuit Cloud Manager werd soms een foutbericht weergegeven, zelfs wanneer de dehibernatie met succes werd gestart.

* Zeldzame gevallen van fouten die zijn aangetroffen bij het creëren of verwijderen van een omgeving, zijn opgelost.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuwe functies in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat foutoplossingen voor de AEM Dispatcher Converter en de Repository Modernizer en ondersteunt ook een nieuw hulpprogramma - Index Converter. Zie [Unieke ervaring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html#benefits) voor meer informatie over deze plug-in.

* De Omzetter van de index is een nut dat kan worden gebruikt om de Definities van de Index van de Douane van een klant om te zetten in AEM as a Cloud Service compatibele Definities van de Index van OAK. Zie [Indexconversie](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) voor meer informatie .

* Nieuwe functie toegevoegd aan [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) dat een afzonderlijk pakket maakt `ui.config` om alle configuraties te bevatten OSGi.

### Opgeloste problemen {#crt-bug-fixes}

* Verscheidene insectenmoeilijke situaties die op de AEM Convertor van de Verzender en de Modernizer van de Bewaarplaats worden gedaan hulpmiddelen. Zie [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) en [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## AEM as a Cloud Service stichting {#aem-as-a-cloud-service-foundation}

### Nieuwe functies {#what-is-new-foundation}

* Server-aan-server voor authentiek verklaarde API vraag - produceer de aangewezen toegangstokens om voor authentiek verklaarde server-aan-server API vraag tussen uw externe toepassingen en AEM as a Cloud Service milieu&#39;s te maken. Meer informatie via lezen [de documentatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) of door [zelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication).

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM as a Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren.

Voor deze afgifte zijn twee nieuwe analysatoren toegevoegd:

* herpuntanalyse
* bundle-nativecode

Raadpleeg de documentatie voor meer informatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing).

## Gereedschappen voor cloudovergang {#code-transition-tools}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.2.2 is 1 februari 2021.

### Nieuwe functies in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Nieuwe mogelijkheid en interface toegevoegd aan het gereedschap voor inhoudsoverdracht - Toewijzing van gebruikers. Deze functie wijst automatisch bestaande gebruikers en groepen toe aan hun Adobe Identity Management System IDs als deel van de activiteit van de inhoudsmigratie. Zie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) voor meer informatie .
* Met het gereedschap Inhoud overbrengen worden nu alle groepen en gebruikers gemigreerd waarnaar in de migratieset wordt verwezen, inclusief kinderen.
* Gebruikers mogen bepaalde paden selecteren onder `/etc` bij het maken van migratiesets.
