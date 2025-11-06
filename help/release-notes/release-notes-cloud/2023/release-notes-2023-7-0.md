---
title: Nota's van de versie voor 2023.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 7866d94c-e54c-4bb2-aaa6-66c019e46336
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.7.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.7.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.7.0) is 27 juli 2023. De volgende release met functies (2023.8.0) is gepland voor 31 augustus 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juli 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.7.0:

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* MSM voor inhoudsfragmenten. AEM Multisite Manager is nu beschikbaar voor inhoudsfragmenten, zodat u Actieve kopieën van inhoudsfragmenten kunt maken voor distributie van bulkinhoud. De korrelige overervingscontroles zijn beschikbaar neer aan het Element van het Fragment van de Inhoud en het niveau van de Variatie.

### Nieuwe functies in [!DNL Experience Manager Sites] prerelease {#prerelease-sites}

* De [&#x200B; Console van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html) staat nu gebruikers toe om markeringen en onderzoek door markeringen te bekijken die als meta-gegevens op de Fragmenten van de Inhoud worden toegepast. Gebruikers hoeven voor deze functie niet meer over te schakelen op de gebruikersinterface van Assets, waardoor contextomschakeling wordt beperkt en de efficiëntie wordt verbeterd.

![&#x200B; Tags toevoegen in de Console van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de Assets-weergave {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

**Verbeterd kunstmatig intelligentiekader voor beeld Slimme Markeringen**

Experience Manager Assets maakt nu gebruik van een verbeterd kunstmatig intelligentiekader voor slimme tags voor afbeeldingen. Deze inhoudsinfo geeft een betere relevantie en nauwkeurigheid van slimme tags die beschikbaar zijn voor alle afbeeldingselementen bij opname.

**vorm vertoning van kolommen voor de mening van de Lijst van Assets**

De Hoofdzaak van activa verstrekt nu de capaciteit om de kolommen te selecteren die in de mening van de Lijst van Assets, zoals Status, Formaat, Dimensies, Grootte, etc. tonen.

![&#x200B; vorm kolommen &#x200B;](/help/release-notes/assets/configure-columns.png)

**de onderzoeksresultaten van de Soort die op relevantie** worden gebaseerd

De Hoofdzaak van activa sorteert nu de onderzoeksresultaten die op Relevantie worden gebaseerd, door gebrek. U kunt de gezochte elementen in toenemende of afnemende volgorde van `Name`, `Relevance`, `Size`, `Modified` en `Created` sorteren.


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**uit de vakthema&#39;s**](/help/forms/using-themes-in-core-components.md) **en malplaatjes**: Kickstart uw proces van de vormverwezenlijking met onze gebruiksklare OTB- thema&#39;s en malplaatjes, die aan macht zowel gekruiste beroeps als nieuwe vormauteurs worden aangepast. Dankzij deze nauwgezette thema&#39;s en sjablonen, die naadloos zijn gebouwd met Adaptive Forms Core Components, kunt u snel formulieren maken voor veelgebruikte toepassingen.

* **[Reageer Componenten voor Hoofdloze Forms &#x200B;](https://github.com/adobe/aem-forms-headless-components/tree/main/packages/react-vanilla-components)**: U kunt nu voorproef en aanpassen   Koploze adaptieve formulieruitvoeringen met de React-componenten in het tekstvak. Deze componenten gebruiken BEM-klassen van Adaptive Forms Core Components voor opmaken, waardoor het voor u gemakkelijker wordt om de weergave aan te passen aan uw specifieke vereisten.

* [**creeer Aanpassings Forms met herhaalbare secties**](/help/forms/create-forms-repeatable-sections.md): U kunt [&#x200B; Accordeon &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [&#x200B; Tovenaar &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [&#x200B; Comité &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), en [&#x200B; Horizontale 9&rbrace; componenten van Lusjes {van 9} componenten maken gebaseerde Aangepaste Vorm herhaalbaar voor veelvoudige gegevens registreren.  &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html)  Met deze herhaalbare secties kunt u eenvoudig meerdere gegevensitems opgeven. Dit is handig wanneer de vereiste instanties van gegevens vooraf onbekend zijn. Een invuller van een formulier kan eenvoudig secties toevoegen of verwijderen, waardoor formulieren kunnen worden aangepast aan verschillende scenario&#39;s voor gegevensinvoer en de verzameling van meerdere exemplaren van dezelfde gegevensrecord kan worden vereenvoudigd.


### Functies voor pre-release beschikbaar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* [**Google reCAPTCHA ondernemingssteun**](/help/forms/captcha-adaptive-forms.md): De Onderneming van Google reCAPTCHA in een AanpassingsVorm gebruiken om betere bescherming tegen frauduleuze activiteit en spam te verstrekken, die een veiliger gebruikerservaring verstrekken. Met een geavanceerde risicoanalyse en naadloze integratie kunnen echte gebruikers eenvoudig formulieren indienen terwijl de bots effectief worden geblokkeerd.

  >[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Het gebruik [&#x200B; Zwaardeloze Aanpassings Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) om uw ontwikkelaars toe te laten om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditioneel grafisch gebruikersinterface kunnen worden betreden en worden in wisselwerking getreden. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail naar `aem-forms-headless@adobe.com` verzenden vanuit uw officiële e-mailadres om deel te nemen aan het programma voor vroegtijdige adoptie.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Handelingencentrum {#actions-center}

Abonneer u op e-mailmeldingen die u waarschuwen wanneer zich kritieke incidenten voordoen die onmiddellijke actie vereisen, en ook op persoonlijke titel aanbevelingen om uw site te optimaliseren. [&#x200B; Centrum van Acties &#x200B;](/help/operations/actions-center.md) dient als hub waar u deze alarm, zoals geblokkeerde replicatierijen of het verlopen van geloofsbrieven kunt herzien, en hen als opgelost merken.

![&#x200B; het schermschot van het Centrum van Acties &#x200B;](/help/assets/assets/actions-center.png)

### Programma voor vroege adoptie van CDN- en WAF-regels {#waf-early-adopter}

Het verkeer van de filter bij CDN die op wordt gebaseerd:

* aanvraagheaders en -eigenschappen (bijvoorbeeld IP-adres)
* verkeerspatronen gekend om met kwaadwillig verkeer worden geassocieerd

Wilt u de functie proberen en feedback delen? Verzend een e-mail naar **aemcs-waf-adopter@adobe.com** van uw officiële e-mailidentiteitskaart om meer over het vroege adoptieprogramma te leren. De ruimte is beperkt.

Leer meer over de eigenschap in het artikel [&#x200B; hier &#x200B;](/help/security/traffic-filter-rules-including-waf.md).

### Andere wijzigingen in de Stichting {#other-foundation-changes}

* In de week van 7 augustus retourneert AEM foutcode 429 in plaats van foutcode 503 wanneer aanvragen naar AEM-instanties een gezond niveau overschrijden. [&#x200B; leer meer &#x200B;](/help/implementing/developing/introduction/development-guidelines.md).

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
