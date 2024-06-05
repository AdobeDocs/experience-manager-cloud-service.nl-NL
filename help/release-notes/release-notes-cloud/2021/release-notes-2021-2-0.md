---
title: Opmerkingen bij de release 2021.2.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2021.2.0."
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Experience Manager] as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.2.0 is 25 februari 2021.
De volgende release (2021.3.0) vindt plaats op 25 maart 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Beheer van inhoud zonder hoofd {#headless}

* **[GraphQL API voor levering van inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)**: Mogelijkheid om inhoudfragmenten te controleren met gebruik van GraphQL-syntaxis en schema&#39;s die zijn gebaseerd op modellen van inhoudsfragmenten, voor uitvoer in JSON-indeling.

* **[Verificatieondersteuning voor GraphQL API-verzoeken](/help/headless/security/authentication.md)**: Mogelijkheid om GraphQL API-aanvragen te verifiëren met toegangstokens voor server-side API&#39;s.

* **[De RemotePage-component](/help/implementing/developing/hybrid/remote-page.md)**: Extra ondersteuning voor het weergeven en bewerken van externe SPA in AEM.

* **[Een externe SPA bewerken in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)**: Mogelijkheid toegevoegd om een zelfstandige toepassing van één pagina naar een AEM instantie te uploaden, bewerkbare gedeelten van inhoud toe te voegen en het schrijven van inhoud in te schakelen.

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

## [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] {#assets}

## Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* Elementen kunnen worden aangekocht met [!DNL Experience Manager Assets Brand Portal]. Het helpt om activa van de uitzendingsgebruikers voor nieuwe marketing campagnes, foto&#39;s, en projecten te betrekken.

* [!DNL Experience Manager Assets] als [!DNL Cloud Service] heeft het recht om een pre-gevormde [!DNL Brand Portal] -instantie. De [!DNL Cloud Manager] gebruiker kan activeren [!DNL Brand Portal] op [!DNL Experience Manager Assets] als [!DNL Cloud Service]. Zie [Brand Portal activeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html).

* Bedrijven kunnen nu elementen bronnen met [!DNL Brand Portal]. Functie voor het aanschaffen van bedrijfsmiddelen gebruikt [!DNL Brand Portal] om klanten te helpen bij het aantrekken van middelen voor nieuwe marketingcampagnes, foto&#39;s en projecten. Zie [asset sourcing in [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html).

* De [!DNL Brand Portal] in het gebruiksrapport worden nu alleen de actieve gebruikers weergegeven. De inactieve gebruikers worden nu niet weergegeven. Actieve gebruikers zijn de gebruikers van wie de account is toegewezen aan een productprofiel in de [!DNL Admin Console]. Zie [[!DNL Brand Portal] rapporten](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* In [!DNL Brand Portal]Er wordt een nieuwe downloadinstelling geïntroduceerd, waarmee u voor elk element een aparte map kunt maken wanneer u mappen, verzamelingen en dergelijke downloadt. Zie [downloadinstellingen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

## Bugfixes in [!DNL Assets] {#bug-fixes-assets}

* Wanneer meerdere elementen zijn geselecteerd om de eigenschappen bij te werken, treedt soms een fout op of worden de eigenschappen van een niet-geselecteerd element bijgewerkt. (CQ-4316532)
* Bij poging om te openen [!UICONTROL Assets Admin Search Rail], blijft de pagina leeg en klikt u op [!UICONTROL Edit] > [!UICONTROL Settings] genereert een fout. (CQ-4315/079)
* Wanneer een nieuwe versie van een bestaand element wordt gemaakt nadat het naamconflict is opgelost, worden de metagegevens van het oorspronkelijke element overschreven. (CQ-4313594)
* Wanneer een element met lange annotatietekst wordt afgedrukt, wordt de annotatietekst bijgesneden, zelfs als er ruimte beschikbaar is. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Product Experience Management: verrijk de productcataloguspagina&#39;s afzonderlijk met Experience Fragments.

* Uitgebreide eigenschappen van de productconsole om verbonden Middelen en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

* Release CIF Venia Reference Site - 2021.02.24 die de nieuwste versie CIF Core Components versie v1.8.0 bevat. Zie [CIF Venia-referentiegebied](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24) voor meer informatie .

* Uitgegeven CIF Core Components v1.8.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) voor meer informatie .

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.2.0 is 11 februari 2021.

### Nieuwe functies {#what-is-new-cloud-manager}


* Klanten van middelen kunnen nu kiezen wanneer en waar ze hun Brand Portal-exemplaar op een zelfbedieningsmanier implementeren via de interface van Cloud Manager. Voor een normaal (niet-sandbox) programma met middelenoplossing kan Brand Portal nu worden ingericht op de productieomgeving. De levering kan slechts eenmaal op het milieu van de Productie worden gedaan.

* Het AEM Project Archetype dat in Project en Sandbox creatie wordt gebruikt is bijgewerkt aan versie 25.

* De lijst met afgekeurde API&#39;s die tijdens het scannen van code zijn geïdentificeerd, is verfijnd en bevat nu extra klassen en methoden die zijn afgekeurd in de meest recente SDK-versies van de Cloud Service.

* SonarQube-profiel voor Cloud Manager bijgewerkt om Sonar rule squid:S2142 te verwijderen. Dit is niet langer in conflict met de controles van de Onderbreking van de thread.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk niet domeinnaam kan toevoegen/bijwerken omdat het bijbehorende milieu of een lopende pijpleiding in bijlage aan het of momenteel in het wachten op de goedkeuringsstap heeft.

* Eigenschappen ingesteld in klant `pom.xml` bestanden die vooraf met sonar zijn gemaakt, worden nu dynamisch verwijderd om fouten met het maken van een build en het scannen van kwaliteit te voorkomen.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein in gebruik is die momenteel wordt opgesteld.

* Er zijn aanvullende regels voor de kwaliteit van code toegevoegd om compatibiliteitsproblemen met Cloud Servicen te verhelpen.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Het vergelijken van SSL-certificaat met een domeinnaam is niet langer hoofdlettergevoelig.

* De gebruikersinterface van Cloud Manager stelt de gebruiker nu op de hoogte als de persoonlijke certificaatsleutels niet voldoen aan de limiet van 2048 bits met een geschikt foutbericht.

* De interface van Cloud Manager zal de gebruiker informeren die tijdelijk geen SSL certificaat kan selecteren als het door een Naam van het Domein wordt gebruikt die momenteel wordt opgesteld.

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
Zie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) voor meer informatie .
* Met het gereedschap Inhoud overbrengen worden nu alle groepen en gebruikers gemigreerd waarnaar in de migratieset wordt verwezen, inclusief kinderen.
* Gebruikers mogen bepaalde paden selecteren onder `/etc` bij het maken van migratiesets.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.2 is 18 februari 2021.

### Nieuwe functies in Analyzer best practices {#what-is-new-bpa}

* Mogelijkheid om het gebruik van de implementatie van AEM Forms en AEM Forms te detecteren en gebieden aan te geven die relevant zijn voor de migratie naar AEM Forms as a Cloud Service.
* Mogelijkheid om het gebruik en het aantal aangepaste componenten en sjablonen te detecteren en te rapporteren.
* Capaciteit om het type van knoopopslag en gebruikte gegevensopslag te ontdekken.
* Mogelijkheid om het gebruik van Dynamic Media te detecteren.
* Mogelijkheid om de gebruikte Java-versie te detecteren.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuw in de Hulpmiddelen van de Refactoring van de Code {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat verschillende foutoplossingen voor de Repository Modernizer.
Zie [Unieke ervaring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html#benefits) voor meer informatie over deze plug-in.

### Opgeloste problemen {#bug-fixes-crt}

* Verschillende opgeloste problemen zijn opgelost in de Repository Modernizer.
Zie [GitHub Resource: aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer informatie .
