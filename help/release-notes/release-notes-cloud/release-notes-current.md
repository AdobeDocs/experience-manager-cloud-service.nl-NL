---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: 36e5e90785a1bc9a4f4f8d4febd462e00252a0ea
workflow-type: tm+mt
source-wordcount: '1669'
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

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.3.0.

## Releasedatum {#release-date-cm-march}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.3.0 is 11 maart 2021.
De volgende release is gepland voor 8 april 2021.


### Wat is er nieuw?{#what-is-new-march}

* Klanten met omgevingen met reeds bestaande aangepaste domeinnaamconfiguraties voor [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) zullen een bericht zien over hun eerdere bestaande configuraties en zullen zichzelf kunnen bedienen via de gebruikersinterface.

* Gebruikers met de vereiste machtigingen kunnen nu een programma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:

   * Voeg de oplossing van Plaatsen aan een bestaand programma met Activa (of vice versa) toe.
   * Sites (of Middelen) verwijderen uit een bestaand programma met zowel Sites als Middelen.
   * Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

* **AEM Push** Updatelabel wordt nu weergegeven voor zowel  *Pipeline* Execution als  ** Activiteitsschermen.

* Als een milieu gehiberneerd maar er ook een AEM beschikbare update is, zal **Gesambernated** status belangrijkheid over **beschikbare Update** nemen.

* Gebruikers kunnen nu hun rol(en) in de cloud Manager zien door de optie &#39;Rol(en) in de cloud-manager weergeven&#39; te selecteren nadat ze naar het pictogram Gebruikersprofiel (rechtsboven) van Unified Shell zijn genavigeerd.

* Het label **Goedkeuringsaanvraag** is voor meer duidelijkheid opnieuw gelabeld aan **Productiegoedkeuring**.

* Het **Version**-label is opnieuw gelabeld aan **Git Tag** in het uitvoeringsscherm van de productiepijplijn.

* De etiketten die het gedrag bepalen wanneer de belangrijke metriek niet de bepaalde drempel ontmoeten zijn opnieuw geëtiketteerd om op hun ware gedrag te wijzen - **annuleert onmiddellijk** en **goedkeuren Onmiddellijk**.

* De lijsten van de klasse en van de methodevervanging zijn bijgewerkt gebaseerd op versie `2021.3.4997.20210303T022849Z-210225` van de AEM Cloud Service SDK.

* De productiepijplijn van de Manager van de Wolk zal nu het testen UI van de Douane mogelijkheden omvatten.

### Opgeloste problemen {#bug-fixes-cm-march}

* Pakketversie is in sommige gevallen overgeslagen tijdens AEM upgrade.

* Bepaalde kwaliteitsproblemen zijn niet goed ontdekt wanneer pakketten in andere pakketten waren ingesloten.

* In duistere situaties, zou de standaardprogrammanaam die bij het openen van de Add dialoog van het Programma wordt geproduceerd een duplicaat van een bestaande programmanaam kunnen zijn.

* Wanneer de gebruiker bij gelegenheid vanaf de pagina voor de uitvoering van de pijpleiding navigeert onmiddellijk nadat een pijpleiding is gestart, wordt een foutbericht weergegeven met de mededeling dat de handeling is mislukt, hoewel de uitvoering daadwerkelijk wordt gestart.

* De bouwstijlstap werd onnodig opnieuw begonnen toen de klant bouwt in ongeldige pakketten resulteerde.

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.


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

### Releasedatum {#release-date-ctt-march}

De releasedatum voor Content Transfer Tool v1.3.0 is 4 maart 2021.

### Nieuw in gereedschap voor inhoudsoverdracht {#what-is-new-ctt-march}

* CTT installeert nu aan `/apps` in plaats van `/libs` Browser referenties aan bepaalde pagina&#39;s kan niet meer geldig zijn.
* Wanneer CTT wordt geïnstalleerd, zal de gebruiker een extra niveau moeten navigeren om aan de pagina van de Overdracht van de Inhoud te krijgen. Zie [Het gereedschap Inhoud overbrengen gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) voor meer informatie.

### Opgeloste problemen {#bug-fixes-ctt-march}

* Tijdens het migreren van inhoud van een specifiek pad, trekt CTT zich aan niet-gerelateerde bronnen. Dit is opgelost


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

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De nieuwste versie van deze plug-in bevat verschillende nieuwe functies en oplossingen voor problemen in de Repository Modernizer en de Dispatcher Converter.    Raadpleeg [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) voor meer informatie over deze plug-in.

* Nieuwe en verbeterde functies voor Repository Modernizer. Verwijs naar [Middel GitHub: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor de nieuwste versie.
   * Normaliseer OSGi vormt (behalve vormen RepoInit) aan het aangewezen.cfg.json formaat.
   * Wijzig de naam van de OSGi config-mappen in de opgegeven indeling.
   * Genereer het project ui.apps.structure.
   * Maak de analysemodule.

* Nieuwe en verbeterde functies voor Dispatcher Converter. Verwijs naar [Middel GitHub: Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Het maken van afzonderlijke bestanden voor verschillende insluitingen in plaats van voor het uitlijnen van de inhoud.
   * Mogelijkheid om zowel het mappad van hosts als het pad naar de hostbestanden af te handelen.
   * De generatie van landbouwbedrijfdossiers met grote klantenconfiguraties in waaier van 600 en meer.










