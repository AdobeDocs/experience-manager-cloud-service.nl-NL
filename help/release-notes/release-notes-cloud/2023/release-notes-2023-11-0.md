---
title: Opmerkingen bij de release 2023.11.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.11.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 19cff082-80aa-445c-9462-5e319b7fe0e9
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.11.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.11.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige eigenschapversie (2023.11.0) is 30 november 2023. De volgende release met functies (2023.12.0) is gepland voor 14 december 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Heb een blik bij de Video van het Overzicht van de Versie van november 2023 voor een samenvatting van de eigenschappen die in de versie 2023.11.0 worden toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Programma voor vroege adoptie {#sites-early-adopter}

**[Tekenreeksen zoeken en vervangen in inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)**: Met de inhoudsfragmentconsole kunnen gebruikers op eenvoudige en intuïtieve wijze een tekenreeks die in meerdere inhoudsfragmenten tegelijk wordt weergegeven, vervangen om de snelheid van de inhoud te versnellen.

![Zoeken en vervangen](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

Wilt u de functie proberen en feedback delen? Een e-mail verzenden naar **aemcs-headless-adopter@adobe.com** van uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de weergave Elementen {#assets-view-features}

* **Ingesloten Adobe Express-editor in AEM Assets**: Gebruikers met toegang tot Express beschikken nu over geïntegreerde gereedschappen voor het bewerken en maken van afbeeldingen op basis van Adobe Express en Adobe Firefly die rechtstreeks in AEM Assets beschikbaar zijn om het hergebruik van inhoud te verbeteren en de snelheid van de inhoud te versnellen.

  ![metagegevensformulier toewijzen aan een map](/help/assets/assets/adobe-express-aem-assets.png)

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **Opslaggebruiksrapporten in Insights**: Beheerders kunnen nu de rapporten over het opslaggebruik bekijken die beschikbaar zijn als onderdeel van Inzichten.

  ![inzichten in opslaggebruik](/help/assets/assets/storage-usage-insights.png)

* **Eerste homepage-configuratie zoeken**: Met Experience Manager Assets kunt u nu de homepage-ervaring voor uw organisatie configureren. Als u eerst zoeken selecteert als startpagina, kunt u de uitlijning van de zoekbalk, de achtergrondafbeelding en het logo voor uw organisatie configureren.

  ![eerste zoekconfiguratie](/help/assets/assets/search-first-configuration.png)

### Nieuwe functies in Prerelease voor Admin View {#admin-view-features-prerelease}

**Voorvertoning video**: AEM Assets genereert nu standaard voorvertoningen van alle ondersteunde video-indelingen, zonder dat u een verwerkingsprofiel hoeft te configureren.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* **[Component CheckBox](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: Adaptieve Forms op basis van Core Components kan nu een component checkbox bevatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

* **[Component Voorwaarden en bepalingen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: Adaptieve Forms op basis van kerncomponenten kan nu een component Voorwaarden en Voorwaarden bevatten. Hiermee kunnen auteurs van formulieren een specifieke sectie in het formulier invoeren waarin gebruikers de voorwaarden, juridische overeenkomsten of het gebruik van een service, product of platform krijgen aangeboden. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

  ![Selectievakje, Voorwaarden en Voorwaarden en Verticale tabcomponenten](/help/forms/assets/forms-components.png)

* **[De component Verticale tabbladen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: Adaptieve Forms op basis van Core Components kan nu formulierinhoud ordenen in een verticale lijst met tabbladen, zodat u over een gestructureerde en navigeerbare indeling beschikt. Het gebruik van verticale tabbladen in een formulier kan de algehele gebruikerservaring verbeteren door de navigatie te vereenvoudigen en de organisatie van formulierinhoud te verbeteren, met name in situaties waarin een formulier meerdere secties of complexe informatie bevat.



### Nieuwe functies in [!DNL Forms] Prerelease {#prerelease-features-forms}

* **[Een adaptieve Forms verbinden met de Microsoft® SharePoint List](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms biedt een OOTB-integratie voor het rechtstreeks verzenden van formuliergegevens naar SharePoint List, zodat u de mogelijkheden van SharePoint List kunt benutten. U kunt de Microsoft SharePoint List configureren als gegevensbron voor een formuliergegevensmodel en de **Verzenden met gebruik van formuliergegevensmodel** verzenden, actie om een adaptief formulier te verbinden met de SharePoint-lijst.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programma voor vroege adoptie {#forms-early-adopter}

* **Een adaptief formulier verzenden naar het Adobe Workfront Fusion-scenario**: Forms as a Cloud Service biedt een out-of-the-box optie om een adaptief formulier moeiteloos aan te sluiten op Adobe Workfront. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

* **Ondersteuning voor talen van rechts naar links**: Adaptieve Forms die is gebaseerd op Core Components, kan nu worden weergegeven in een RTL-taal (rechts naar links), zoals Arabisch, Perzisch en Urdu. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en op RTL-markten tikken. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

  ![Ondersteuning voor talen van rechts naar links](/help/forms/assets/right-to-left-language-support.png)

* **[Protect uw documenten met DocAssurance-API&#39;s (onderdeel van communicatie-API&#39;s)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance-API&#39;s stellen u in staat gevoelige informatie te beveiligen door de documenten te ondertekenen en te versleutelen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt schrijven naar `aem-forms-ea@adobe.com` van uw officiële e-mailidentiteitskaart om zich bij het vroege adoptieprogramma aan te sluiten en toegang tot het vermogen te verzoeken.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### WAF-filterregels kunnen nu worden gelicentieerd {#cdn-waf-license}

De Regels van de Filter van het verkeer werden vrijgegeven in Oktober, en omvatten een nota dat de speciale categorie van de regels van de Firewall van de Toepassing van het Web (WAF) later dit jaar beschikbaar zou zijn om de regels aan te vullen die reeds beschikbaar aan Sites en klanten van Forms zijn. Als update kan het WAF-DDoS Protection-aanbod nu een licentie krijgen.

Zodra vergunning gegeven, kunnen deze geavanceerde regels van WAF aan CDN worden opgesteld gebruikend de Pijpleiding van de Configuratie van de Manager van de Wolk om een extra laag van bescherming tegen Webaanvallen toe te voegen.

Meer informatie [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), inclusief WAF. Neem contact op met uw AEM accountteam over het verlenen van licenties voor WAF-DDoS-beveiliging of uitgebreide beveiliging.

### Programma voor vroege adopter van CDN-configuratie {#cdn-config-early-adopter}

Naast de onlangs vrijgelaten [Verkeersfilterregels (inclusief WAF)](/help/security/traffic-filter-rules-including-waf.md), is er een kans om de Pijpleiding van de Configuratie te gebruiken om andere types van configuratie te verklaren en op te stellen CDN. We zouden graag iets over uw gebruiksgevallen horen, zoals:
* 301/302 omleidingen op de client
* verzoeken aan de rand van willekeurige oorsprong proxying
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken
* verificatie via gebruikersnaam/wachtwoord
* andere handige CDN-configuraties

Een e-mail verzenden naar **aemcs-cdn-config-adopter@adobe.com** van je officiële e-mailadres met je feedback.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Bekende problemen {#known-issues}

* Kan Adaptieve Forms niet verzenden op basis van Core Components. Dit probleem doet zich voor bij Adaptive Forms die is gebouwd met Core Components versies 2.0.38 - 2.0.60.

  U lost dit probleem op. u kunt overschakelen naar Adaptive Form Core Components versie 2.0.62 of hoger. Een versie van Adaptive Forms Core Components instellen voor uw omgeving [versies instellen van de component core.forms.components.version, core.forms.components.af.version en core.wcm.components.version](/help/forms/enable-adaptive-forms-core-components.md#2-add-adaptive-forms-core-components-dependencies-to-your-git-repository) afhankelijkheden in uw as a Cloud Service Forms-opslagplaats of op Archetype gebaseerd project en [de wijzigingen in uw as a Cloud Service Forms-omgeving implementeren](/help/forms/enable-adaptive-forms-core-components.md#build-and-deploy-updated-code-on-an-aem-forms-as-a-cloud-service-environment). U vindt de nieuwste versie van Adaptive Forms Core Components Afhankelijkheden via [Adaptive Forms Core Components Git-opslagplaats](https://github.com/adobe/aem-core-forms-components#system-requirements).
