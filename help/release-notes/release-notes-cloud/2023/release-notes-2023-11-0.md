---
title: Nota's van de versie voor 2023.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 19cff082-80aa-445c-9462-5e319b7fe0e9
feature: Release Information
role: Admin
source-git-commit: 0845447c1c4f47b77debd179f24eac95a0d2c2db
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.11.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.11.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.11.0) is 30 november 2023. De volgende release met functies (2023.12.0) is gepland voor 14 december 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Heb een blik bij de Video van het Overzicht van de Versie van november 2023 voor een samenvatting van de eigenschappen die in de versie 2023.11.0 worden toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Programma voor vroege adoptie {#sites-early-adopter}

**[vind en vervangt koorden in de Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)**: De Console van het Fragment van de Inhoud voorziet gebruikers van een gemakkelijke en intuïtieve manier om een koord te vervangen dat in veelvoudige inhoudsfragmenten tegelijkertijd verschijnt om inhoudssnelheid te helpen versnellen.

![ vinden en vervangen ](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

Wilt u de functie proberen en feedback delen? Verzend een e-mail naar **aemcs-headless-adopter@adobe.com** van uw officiële e-mailidentiteitskaart om meer over het vroege adoptieprogramma te leren.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in Assets View {#assets-view-features}

* **Ingebedde redacteur van Adobe Express in AEM Assets**: De gebruikers met toegang tot Uitdrukkelijke hebben nu beeld het uitgeven en creatie hulpmiddelen van Adobe Express en Adobe Firefly beschikbaar direct binnen AEM Assets om inhoudshergebruik te verbeteren en inhoudssnelheid te versnellen.

  ![ wijs meta-gegevensvorm aan een omslag ](/help/assets/assets/adobe-express-aem-assets.png) toe

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **het gebruiksrapporten van de Opslag in Inzichten**: De beheerders hebben nu de capaciteit om de rapporten van het opslaggebruik beschikbaar als deel van Inzichten te bekijken.

  ![ de inzichten van het opslaggebruik ](/help/assets/assets/storage-usage-insights.png)

* **de eerste homepageconfiguratie van het 0&rbrace; Onderzoek &lbrace;: Experience Manager Assets laat u nu toe om de homepage ervaring voor uw organisatie te vormen.** Als u eerst zoeken selecteert als startpagina, kunt u de uitlijning van de zoekbalk, de achtergrondafbeelding en het logo voor uw organisatie configureren.

  ![ onderzoek eerste configuratie ](/help/assets/assets/search-first-configuration.png)

### Nieuwe functies in Prerelease voor Admin View {#admin-view-features-prerelease}

**VideoVoorproef**: AEM Assets produceert nu voorproefvertoningen van alle gesteunde videoformaten door gebrek, zonder de behoefte om een verwerkingsprofiel te vormen.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* **[CheckBox component ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html?lang=nl-NL)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een checkbox component omvatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

* **[de component van de Bepalingen en van de Voorwaarden ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html?lang=nl-NL)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een component van de Voorwaarden en van de Voorwaarden omvatten. Hiermee kunnen auteurs van formulieren een specifieke sectie in het formulier invoeren waarin gebruikers de voorwaarden, juridische overeenkomsten of het gebruik van een service, product of platform krijgen aangeboden. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

  ![ Checkbox, Termen en Voorwaarden, en Verticale lusjecomponenten ](/help/forms/assets/forms-components.png)

* **[Verticale de component van lusjes ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html?lang=nl-NL)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan vorminhoud in een verticale lijst van lusjes nu organiseren, die een gestructureerde en navigeerbare lay-out verstrekken. Het gebruik van verticale tabbladen in een formulier kan de algehele gebruikerservaring verbeteren door de navigatie te vereenvoudigen en de organisatie van formulierinhoud te verbeteren, met name in situaties waarin een formulier meerdere secties of complexe informatie bevat.



### Nieuwe functies in [!DNL Forms] Prerelease {#prerelease-features-forms}

* **[verbind een Aangepaste Forms met de Lijst van SharePoint Microsoft®](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms verstrekt een integratie OTB om vormgegevens aan de Lijst van SharePoint direct voor te leggen, toelatend u om de mogelijkheden van de Lijsten van SharePoint te gebruiken. U kunt de Lijst van Microsoft SharePoint als gegevensbron voor een Model van de Gegevens van de Vorm vormen en **gebruiken voorleggen gebruikend het Model van de Gegevens van de Vorm** actie om een Aangepast Vorm met de Lijst van SharePoint te verbinden.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programma voor vroege adoptie {#forms-early-adopter}

* **voorlegt een Aangepast Vorm aan het Scenario van de Fusie van Adobe Workfront**: Forms as a Cloud Service biedt een uit-van-de-doosopties aan om een Aangepast Vorm met Adobe Workfront moeiteloos aan te sluiten. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

* **Recht aan linkertaalsteun**: De adaptieve Forms die op de Componenten van de Kern wordt gebouwd kan nu in een (RTL) taal zoals Arabisch, Perzisch, en Urdu worden voorgesteld. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en op RTL-markten tikken. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

  ![ Recht aan linkertaalsteun ](/help/forms/assets/right-to-left-language-support.png)

* **[bescherm uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### WAF Traffic Filter Rules can now be licensed {#cdn-waf-license}

De Regels van de Filter van het verkeer werden vrijgegeven in Oktober, en omvatten een nota dat de speciale categorie van de regels van de Firewall van de Toepassing van het Web (WAF) later dit jaar beschikbaar zou zijn om de regels aan te vullen die reeds beschikbaar aan Plaatsen en klanten van Forms zijn. Voor de WAF-DDoS Protection-aanbieding kan nu een licentie worden verleend.

Zodra vergunning gegeven, kunnen deze geavanceerde regels van WAF aan CDN worden opgesteld gebruikend de Pijpleiding van de Configuratie van Cloud Manager om een extra laag van bescherming tegen Webaanvallen toe te voegen.

Lees over [ Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md), met inbegrip van WAF. Bespreek een licentie voor WAF-DDoS-beveiliging of Enhanced Security met uw AEM-accountteam.

### Programma voor vroege adoptie van domeintoewijzing {#cdn-config-early-adopter}

Naast onlangs vrijgegeven [ Regels van de Filter van het Verkeer (met inbegrip van WAF) ](/help/security/traffic-filter-rules-including-waf.md), is er een kans om de Pijpleiding van de Configuratie te gebruiken om andere types van configuratie te verklaren en op te stellen CDN. We zouden graag iets over uw gebruiksgevallen horen, zoals:
* 301/302 omleidingen op de client
* verzoeken aan de rand van willekeurige oorsprong proxying
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken
* verificatie via gebruikersnaam/wachtwoord
* andere handige CDN-configuraties

Verzend een e-mail naar **aemcs-cdn-config-adopter@adobe.com** van uw officiële e-mailidentiteitskaart met uw terugkoppelt.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Bekende problemen {#known-issues}

* Kan Adaptieve Forms niet verzenden op basis van Core Components. Dit probleem doet zich voor bij Adaptive Forms die is gebouwd met Core Components versies 2.0.38 - 2.0.60.

  U lost dit probleem op. u kunt overschakelen naar Adaptive Form Core Components versie 2.0.62 of hoger. Als u een versie van Adaptive Forms Core Components voor uw omgeving wilt instellen, stelt u versies in van de afhankelijkheden `core.forms.components.version` , `core.forms.components.af.version` en `core.wcm.components.version component` in uw Forms as a Cloud Service-opslagplaats of op AEM Archetype gebaseerd project en implementeert u de wijzigingen in uw Forms as a Cloud Service-omgeving. U kunt de recentste versie van de Adaptieve Verdedigingen van de Componenten van de Kern van Forms van de Kern bij [ Aangepaste bewaarplaats van het Git van de Componenten van de Forms vinden ](https://github.com/adobe/aem-core-forms-components#system-requirements).
