---
title: Nota's van de versie voor 2023.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 81a6cbd2-7101-429b-8572-2650c5bea963
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.10.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.10.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.10.0) is 26 oktober 2023. De volgende functieversie (2023.11.0) is gepland voor 30 november 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van oktober 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.10.0:

>[!VIDEO](https://video.tv.adobe.com/v/3425186/?quality=12)

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies {#assets-features}

**toe:voegen-op AEM Assets voor Adobe Express**: Experience Manager Assets verstrekt nu toe:voegen-op voor Adobe Express. Met de invoegtoepassing hebt u rechtstreeks vanuit de gebruikersinterface van de Adobe Express toegang tot de elementen die in Experience Manager Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats. De invoegtoepassing biedt de volgende belangrijke voordelen:

* Groter hergebruik van inhoud door nieuwe elementen te bewerken en op te slaan in AEM

* Minder tijd en moeite in het algemeen om nieuwe elementen te maken of nieuwe versies van bestaande elementen te maken

  ![ omvat activa van Assets toe:voegen-op ](/help/assets/assets/aem-assets-add-on-include-assets.png)

### Nieuwe functies in de Assets-weergave {#assets-view-features}

* **Bulk de invoeractiva van Gegevensbron OneDrive**: De beheerders hebben nu de capaciteit om groot aantal activa van OneDrive in AEM Assets [&#128279;](/help/assets/bulk-import-assets-view.md#onedrive-developer-application) in te voeren.  Tot de bijgewerkte lijst voor de ondersteunde gegevensbronnen voor bulkimport behoren Azure, AWS, Google Cloud, Dropbox en OneDrive.

  ![ wijs meta-gegevensvorm aan een omslag ](/help/assets/assets/bulk-import-source-details-onedrive.png) toe

* **Cross-Org de Steun van de Entitlement voor Bibliotheken**: Experience Manager Assets laat u nu toe om toegang tot de bibliotheken van het Creative Cloud in een verschillende organisatie te vormen IMS. Het maakt gemakkelijker toegang tot de recentste productoverschrijdende werkschema&#39;s tussen Creative Cloud en Experience Manager mogelijk en vermindert tijd en moeite voor creatieve personen.

### Functies voor pre-release beschikbaar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [ Multi-caption en multi-audio spoorsteun voor video&#39;s in Dynamic Media ](/help/assets/dynamic-media/video.md#about-msma) - u kunt veelvoudige titels en veelvoudige audiosporen aan een primaire video nu gemakkelijk toevoegen. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

  ![ Bijschriften en Audiosporen tabel op de pagina van Eigenschappen van een geselecteerd videoelement.](/help/release-notes/assets/msma-aem-cs.png)*Bijschriften en Audiosporen lusje op de pagina van Eigenschappen van geselecteerde videoactiva.*

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* **[Eigenschappen van de Douane voor Aanpassings Forms](/help/forms/template-editor-core-components.md#add-a-custom-group-name-in-the-policy-of-template-editor)**: U kunt douanekenmerken (zeer belangrijke paren) met een vormmalplaatje of een adaptieve vormcomponent associëren om vormontwikkelaars toe te staan om dynamisch vormgedrag te leveren dat zich aanpast gebaseerd op de waarden van deze douanekenmerken. Ontwikkelaars kunnen bijvoorbeeld verschillende uitvoeringen van een Forms-component zonder koptekst maken op mobiele apparaten, desktops of webplatforms, op basis van de waarden van aangepaste kenmerken. Hierdoor wordt de gebruikerservaring aanzienlijk verbeterd voor een groot aantal apparaten.

* **Thema&#39;s en malplaatjes**: Kickstart uw proces van de vormverwezenlijking met onze nieuwe thema&#39;s en malplaatjes, die aan macht zowel gekruiste beroeps als nieuwe vormauteurs worden aangepast. Dankzij deze nauwgezette thema&#39;s en sjablonen, die naadloos zijn gebouwd met Adaptive Forms Core Components, kunt u snel formulieren maken voor veelgebruikte toepassingen.

  ![ uit de vakmalplaatjes ](/help/forms/assets/form-templates-ootb.png)


### Programma voor vroegtijdige adoptie {#forms-early-adopter}

* **[Protect uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Regels voor verkeersfilters, inclusief WAF {#traffic-filter-rules-waf}

[ verkeer van de Filter bij de Adobe Beheerde CDN ](/help/security/traffic-filter-rules-including-waf.md) door regels te verklaren die websiteverkeer door eigenschappen met inbegrip van url, IP adres, en gebruikersagent aanpassen - of de grenzen van het douaneverkeer plaatsen om tegen aanvallen van Dos te beschermen. Klanten kunnen ook een licentie verlenen voor een set geavanceerde WAF-regels (Web Application Firewall) voor extra bescherming tegen geavanceerde websitebedreigingen.

Wij moedigen u aan om vertrouwd te worden met de regels van de verkeersfilter door [ het proberen van een leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html)! Het begeleidt u door vestiging een nieuwe Pijpleiding van de Configuratie van Cloud Manager, verklarende regels in een configuratiedossier, en het analyseren van CDN- logboeken voor kwaadwillig verkeer.

De filterregels van het verkeer zijn nu beschikbaar op ontwikkelomgevingen, met een geleidelijke uitrol aan stadium en prod milieu&#39;s in November. U kunt vroegere toegang op stadium en prod verzoeken door **aemcs-waf-adopter@adobe.com** te e-mailen.

De geavanceerde het verkeersfilterregels van WAF kunnen later dit jaar door de Verbeterde Veiligheid of WAF-DoS het dienstenaanbod van de Bescherming worden vergunning gegeven.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
