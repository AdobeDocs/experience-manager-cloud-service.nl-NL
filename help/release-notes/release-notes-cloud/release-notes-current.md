---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: 5b702dd33169939d7b16df07f29f8149cafa82bd
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als een Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>Vanuit deze locatie kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2021.2.0 is 25 februari 2021.
De volgende release (2021.3.0) vindt plaats op 25 maart 2021.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

* **[De RemotePage-component](/help/implementing/developing/hybrid/remote-page.md)**: Extra ondersteuning voor het weergeven en bewerken van externe SPA in AEM.

* **[Een externe SPA bewerken in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)**: Mogelijkheid toegevoegd om een zelfstandige toepassing van één pagina naar een AEM instantie te uploaden, bewerkbare gedeelten van inhoud toe te voegen en het schrijven van inhoud in te schakelen.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

## Nieuw in [!DNL Assets] {#what-is-new-assets}

* Bedrijven kunnen nu elementen aanschaffen met [!DNL Brand Portal]. De functie voor het aanschaffen van bedrijfsmiddelen gebruikt [!DNL Brand Portal] om klanten te helpen bij het aantrekken van bedrijfsmiddelen voor nieuwe marketingcampagnes, foto&#39;s en projecten. Zie [asset sourcing in [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html).

* In het gebruiksrapport [!DNL Brand Portal] worden nu alleen de actieve gebruikers weergegeven. De inactieve gebruikers worden nu niet weergegeven. Actieve gebruikers zijn de gebruikers van wie de account is toegewezen aan een productprofiel in [!DNL Admin Console]. Zie [[!DNL Brand Portal] rapporten](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* In [!DNL Brand Portal] wordt een nieuwe downloadinstelling geïntroduceerd, waarmee u voor elk element een aparte map kunt maken wanneer u mappen, verzamelingen en dergelijke downloadt. Zie [downloadinstellingen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  -->

## Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* Wanneer een nieuwe versie van een bestaand element wordt gemaakt nadat het naamconflict is opgelost, worden de metagegevens van het oorspronkelijke element overschreven. (CQ-4313594)
* Wanneer een element met lange annotatietekst wordt afgedrukt, wordt de annotatietekst bijgesneden, zelfs als er ruimte beschikbaar is. (CQ-4314101)
* Wanneer meerdere elementen zijn geselecteerd om de eigenschappen bij te werken, treedt soms een fout op of worden de eigenschappen van een niet-geselecteerd element bijgewerkt. (CQ-4316532)
* Wanneer u [!UICONTROL Assets Admin Search Rail] probeert te openen, blijft de pagina leeg en wanneer u op [!UICONTROL Edit] > [!UICONTROL Settings] klikt, wordt een fout gegenereerd. (CQ-4315/079)

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Product Experience Management: Verrijk de pagina&#39;s van de productcatalogus individueel met de Fragmenten van de Ervaring.

* Uitgebreide eigenschappen van de productconsole om verbonden Middelen en de Fragmenten van de Ervaring te tonen, met inbegrip van actie om snel aan de bijbehorende inhoud te navigeren.

* Uitgebrachte CIF Venia Reference Site - 2021.02.24 met de nieuwste versie van CIF Core Components v1.8.0. Raadpleeg [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24) voor meer informatie.

* Uitgebrachte CIF Core Components v1.8.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) voor meer informatie.

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








