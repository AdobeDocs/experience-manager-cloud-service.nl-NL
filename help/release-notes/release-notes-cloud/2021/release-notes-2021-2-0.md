---
title: Nota's van de versie voor 2021.2.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2021.2.0."
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] as a Cloud Service beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.2.0 is 25 februari 2021.
De volgende release (2021.3.0) vindt plaats op 25 maart 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Beheer van inhoud zonder hoofd {#headless}

* **[GraphQL API voor de Levering van het Fragment van de Inhoud](/help/headless/graphql-api/content-fragments.md)**: Mogelijkheid om de Fragmenten van de Inhoud te vragen gebruikend de syntaxis van GraphQL, en schema&#39;s die op de modellen van het Fragment van de Inhoud worden gebaseerd, voor output in formaat JSON.

* **[Steun van de Authentificatie voor GraphQL API Verzoeken](/help/headless/security/authentication.md)**: Mogelijkheid om GraphQL API verzoeken met toegangstokens voor server-kant APIs voor authentiek te verklaren.

* **[de Component RemotePage](/help/implementing/developing/hybrid/remote-page.md)**: Toegevoegde steun voor het bekijken van en het uitgeven van externe SPA binnen AEM gebruiken.

* **[Uitgevend een Externe SPA binnen AEM](/help/implementing/developing/hybrid/editing-external-spa.md)**: Toegevoegde capaciteit om een standalone enig-paginatoepassing aan een AEM instantie te uploaden, editable secties van inhoud toe te voegen, en creatie toe te laten.

* Verbeterde JSON-uitvoer van de GraphQL API, inclusief de mogelijkheid om RTF-tekst uit te voeren in JSON-indeling en landinstellingen.

* Ondersteuning voor het nesten van modellen van inhoudsfragmenten om het maken van geneste structuren voor inhoudsfragmenten mogelijk te maken, via specifieke gegevenstypen van Content Fragment Reference of inline verwijzingen van inhoudsfragmenten in tekstvelden met meerdere regels.

* Aanvullende validatieregels beschikbaar in de gegevenstypen van het inhoudsfragmentmodel, waaronder &quot;uniek&quot;, &quot;vereist&quot; en &quot;vertaalbaar&quot;.

* Mogelijkheid om Content Fragment-modellen van tags te voorzien en het maken van Content Fragment toe te staan in een map met beleid per tag of pad.

* Verbeteringen op gebied van bruikbaarheid in de Content Fragment-editor, inclusief publicatieactie en weergave van het model waarop een fragment is gebaseerd.

* Mogelijkheid om JSON-uitvoer direct voor te vertonen in de Content Fragment Editor.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/sites-console/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

## Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* Assets kan worden aangeschaft met [!DNL Experience Manager Assets Brand Portal] . Het helpt om activa van de uitzendingsgebruikers voor nieuwe marketing campagnes, foto&#39;s, en projecten te betrekken.

* [!DNL Experience Manager Assets] als een [!DNL Cloud Service] heeft het recht om een vooraf geconfigureerde [!DNL Brand Portal] -instantie te hebben. De [!DNL Cloud Manager] -gebruiker kan [!DNL Brand Portal] on [!DNL Experience Manager Assets] activeren als een [!DNL Cloud Service] . Zie [ Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=nl-NL) activeren.

* Bedrijven kunnen nu elementen aanschaffen met [!DNL Brand Portal] . De functie voor het aanschaffen van bedrijfsmiddelen gebruikt [!DNL Brand Portal] om klanten te helpen bij het aanschaffen van bedrijfsmiddelen voor nieuwe marketingcampagnes, foto&#39;s en projecten. Zie [ activa die in  [!DNL Brand Portal] ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=nl-NL) betrekken.

* In het gebruiksrapport van [!DNL Brand Portal] worden nu alleen de actieve gebruikers weergegeven. De inactieve gebruikers worden nu niet weergegeven. Actieve gebruikers zijn gebruikers van wie de account is toegewezen aan een productprofiel in de [!DNL Admin Console] . Zie [[!DNL Brand Portal]  rapporten ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html?lang=nl-NL).

* In [!DNL Brand Portal] wordt een nieuwe downloadinstelling geïntroduceerd, waarmee u voor elk element een aparte map kunt maken wanneer u mappen, verzamelingen en dergelijke downloadt. Zie [ downloadmontages ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=nl-NL).

## Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* Wanneer meerdere elementen zijn geselecteerd om de eigenschappen bij te werken, treedt soms een fout op of worden de eigenschappen van een niet-geselecteerd element bijgewerkt. (CQ-4316532)
* Wanneer u [!UICONTROL Assets Admin Search Rail] probeert te openen, blijft de pagina leeg en wanneer u op [!UICONTROL Edit] > [!UICONTROL Settings] klikt, wordt een fout gegenereerd. (CQ-4315/079)
* Wanneer een nieuwe versie van een bestaand element wordt gemaakt nadat het naamconflict is opgelost, worden de metagegevens van het oorspronkelijke element overschreven. (CQ-4313594)
* Wanneer een element met lange annotatietekst wordt afgedrukt, wordt de annotatietekst bijgesneden, zelfs als er ruimte beschikbaar is. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Product Experience Management: verrijk de productcataloguspagina&#39;s afzonderlijk met Experience Fragments.

* Uitgebreide eigenschappen van de productconsole om verbonden Assets en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

* Release CIF Venia Reference Site - 2021.02.24 die de nieuwste versie CIF Core Components versie v1.8.0 bevat. Zie [ CIF de Plaats van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24) voor meer details.

* Uitgegeven CIF Core Components v1.8.0. Zie [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) voor meer details.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.2.0 is 11 februari 2021.

### Nieuwe functies {#what-is-new-cloud-manager}


* Assets-klanten kunnen nu kiezen wanneer en waar ze hun Brand Portal-exemplaar op een zelfbedieningsmanier kunnen implementeren via de Cloud Manager-interface. Voor een regulier (niet-sandbox) programma met Assets-oplossing kan Brand Portal nu worden ingericht op de productieomgeving. De levering kan slechts eenmaal op het milieu van de Productie worden gedaan.

* Het AEM Project Archetype dat in Project en Sandbox creatie wordt gebruikt is bijgewerkt aan versie 25.

* De lijst met afgekeurde API&#39;s die tijdens het scannen van code zijn geïdentificeerd, is verfijnd en bevat nu extra klassen en methoden die zijn afgekeurd in de meest recente SDK-versies van de Cloud Service.

* SonarQube-profiel voor Cloud Manager bijgewerkt om Sonar rule squid:S2142 te verwijderen. Dit is niet langer in conflict met de controles van de Onderbreking van de thread.

* Cloud Manager UI zal de gebruiker informeren die tijdelijk niet domeinnaam kan toevoegen/bijwerken omdat het bijbehorende milieu of een lopende pijpleiding in bijlage aan het of momenteel in het wachten op de goedkeuringsstap heeft.

* Eigenschappen die zijn ingesteld in `pom.xml` -bestanden van de klant die vooraf zijn voorzien van sonar, worden nu dynamisch verwijderd om fouten met het scannen van build en kwaliteit te voorkomen.

* Cloud Manager UI zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein in gebruik is die momenteel wordt opgesteld.

* Er zijn aanvullende regels voor de kwaliteit van code toegevoegd om compatibiliteitsproblemen met Cloud Servicen te verhelpen.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Het vergelijken van SSL-certificaat met een domeinnaam is niet langer hoofdlettergevoelig.

* De gebruikersinterface van Cloud Manager stelt een gebruiker nu op de hoogte als de persoonlijke certificaatsleutels niet met een geschikt foutbericht aan de limiet van 2048 bits voldoen.

* De gebruikersinterface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein in gebruik is die momenteel wordt opgesteld.

* In sommige gevallen kan een intern probleem ertoe leiden dat het verwijderen van het milieu vastloopt.

* Sommige pijpleidingsmislukkingen werden verkeerd gemeld als pijpleidingsfouten.

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.2.4 is 10 februari 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* Bij het toewijzen van meerdere gebruikers werden IMS-id&#39;s van sommige gebruikers onjuist toegewezen. Dit is opgelost.

### Releasedatum {#release-date-ctt-feb}

De releasedatum voor Content Transfer Tool v1.2.2 is 1 februari 2021.

### Nieuw in gereedschap voor inhoudsoverdracht {#what-is-new-ctt}

* Nieuwe mogelijkheid en interface toegevoegd aan het gereedschap voor inhoudsoverdracht - Toewijzing van gebruikers. Deze functie wijst automatisch bestaande gebruikers en groepen toe aan hun Adobe Identity Management System IDs als deel van de activiteit van de inhoudsmigratie.
Zie [ Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=nl-NL) voor meer details.
* Met het gereedschap Inhoud overbrengen worden nu alle groepen en gebruikers gemigreerd waarnaar in de migratieset wordt verwezen, inclusief kinderen.
* Gebruikers mogen bepaalde paden onder `/etc` selecteren bij het maken van migratiesets.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.2 is 18 februari 2021.

### Nieuwe functies in Analyzer best practices {#what-is-new-bpa}

* Mogelijkheid om het gebruik van de AEM Forms- en AEM Forms-implementatie te detecteren en gebieden aan te geven die relevant zijn voor de migratie naar AEM Forms-as a Cloud Service.
* Mogelijkheid om het gebruik en het aantal aangepaste componenten en sjablonen te detecteren en te rapporteren.
* Capaciteit om het type van knoopopslag en gebruikte gegevensopslag te ontdekken.
* Mogelijkheid om het gebruik van Dynamic Media te detecteren.
* Mogelijkheid om de gebruikte Java-versie te detecteren.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuw in de Hulpmiddelen van de Refactoring van de Code {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat verschillende foutoplossingen voor de Repository Modernizer.
Zie [ Verenigde Ervaring ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=nl-NL#benefits) om meer over deze stop te leren.

### Opgeloste problemen {#bug-fixes-crt}

* Verschillende opgeloste problemen zijn opgelost in de Repository Modernizer.
Zie [ Middel GitHub: aem-wolk-dienst-bron-migratie ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer details.
