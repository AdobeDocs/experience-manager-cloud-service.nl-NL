---
title: Opmerkingen bij de release 2023.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 7866d94c-e54c-4bb2-aaa6-66c019e46336
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.7.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.7.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.7.0) is 27 juli 2023. De volgende release met functies (2023.8.0) is gepland voor 31 augustus 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juli 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.7.0:

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* MSM voor inhoudsfragmenten. AEM Multisite Manager is nu beschikbaar voor inhoudsfragmenten, zodat u Actieve kopieën van inhoudsfragmenten kunt maken voor distributie van bulkinhoud. De korrelige overervingscontroles zijn beschikbaar neer aan het Element van het Fragment van de Inhoud en het niveau van de Variatie.

### Nieuwe functies in [!DNL Experience Manager Sites] prerelease {#prerelease-sites}

* De [Console voor inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html) Gebruikers kunnen nu tags weergeven en zoeken op tags die als metagegevens zijn toegepast op Inhoudsfragmenten. Gebruikers hoeven voor deze mogelijkheid niet meer over te schakelen op de interface Elementen, waardoor contextomschakeling wordt beperkt en de efficiëntie wordt verbeterd.

![Tags toevoegen in Content Fragment Console](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de weergave Elementen {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

**Verbeterd kunstmatig intelligentiekader voor beeld Slimme Markeringen**

Experience Manager Assets maakt nu gebruik van een verbeterd kunstmatig intelligentiekader voor slimme tags voor afbeeldingen. Deze inhoudsinfo geeft een betere relevantie en nauwkeurigheid van slimme tags die beschikbaar zijn voor alle afbeeldingselementen bij opname.

**Weergave van kolommen configureren voor de weergave Lijst met elementen**

Met Assets Essentials kunt u nu de kolommen selecteren die worden weergegeven in de weergave Lijst met elementen, zoals Status, Indeling, Dimensionen, Grootte, enzovoort.

![Kolommen configureren](/help/release-notes/assets/configure-columns.png)

**Zoekresultaten sorteren op basis van relevantie**

Assets Essentials sorteren nu standaard de zoekresultaten op Relevantie. U kunt de gezochte middelen in stijgende of dalende orde van sorteren `Name`, `Relevance`, `Size`, `Modified`, en `Created`.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Buiten-de-box thema&#39;s**](/help/forms/using-themes-in-core-components.md) **en sjablonen**: Kickstart uw formulierontwerpproces met onze gebruiksklare OTB-thema&#39;s en -sjablonen, speciaal ontworpen voor ervaren professionals en nieuwe formulierauteurs. Dankzij deze nauwgezette thema&#39;s en sjablonen, die naadloos zijn gebouwd met Adaptive Forms Core Components, kunt u snel formulieren maken voor veelgebruikte toepassingen.

* **[Componenten reageren voor Forms zonder hoofd](https://github.com/adobe/aem-forms-headless-components/tree/main/packages/react-vanilla-components)**: U kunt nu een voorbeeld bekijken van de koploze adaptieve formulieruitvoeringen en deze aanpassen met de React-componenten in het vak. Deze componenten gebruiken BEM-klassen van Adaptive Forms Core Components voor opmaken, waardoor het voor u gemakkelijker wordt om de weergave aan te passen aan uw specifieke vereisten.

* [**Adaptieve Forms maken met herhaalbare secties**](/help/forms/create-forms-repeatable-sections.md): U kunt nu maken [Accordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Wizard](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [Deelvenster](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), en [Horizontale tabs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) componenten gebaseerd op Adaptief formulier herhaalbaar voor het vastleggen van meerdere gegevensrecords.  Met deze herhaalbare secties kunt u eenvoudig meerdere gegevensitems opgeven. Dit is handig wanneer de vereiste instanties van gegevens vooraf onbekend zijn. Een invuller van een formulier kan eenvoudig secties toevoegen of verwijderen, waardoor formulieren kunnen worden aangepast aan verschillende scenario&#39;s voor gegevensinvoer en de verzameling van meerdere exemplaren van dezelfde gegevensrecord kan worden vereenvoudigd.


### Functies voor pre-release beschikbaar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* [**Google reCAPTCHA-bedrijfsondersteuning**](/help/forms/captcha-adaptive-forms.md): Gebruik Google reCAPTCHA Enterprise in een adaptieve vorm om een betere bescherming te bieden tegen frauduleuze activiteiten en spam, zodat gebruikers veiliger worden. Met een geavanceerde risicoanalyse en naadloze integratie kunnen echte gebruikers eenvoudig formulieren indienen terwijl de bots effectief worden geblokkeerd.

  >[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruiken [Forms zonder hoofdadapter](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) om uw ontwikkelaars in staat te stellen om interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden benaderd en waarmee interactie mogelijk is, in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt een e-mail verzenden naar `aem-forms-headless@adobe.com` van uw officiële e-mailadres om deel te nemen aan het vroege adoptieprogramma.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Handelingencentrum {#actions-center}

Abonneer u op e-mailmeldingen die u waarschuwen wanneer zich kritieke incidenten voordoen die onmiddellijke actie vereisen, en ook op persoonlijke titel aanbevelingen om uw site te optimaliseren. [Handelingencentrum](/help/operations/actions-center.md) dient als hub waar u deze alarm, zoals geblokkeerde replicatierijen of het verlopen van geloofsbrieven kunt herzien, en hen kunt merken zoals opgelost.

![Screenshot van Handacenter](/help/assets/assets/actions-center.png)

### Voortijdig-adoptieprogramma voor CDN- en WAF-regels {#waf-early-adopter}

Het verkeer van de filter bij CDN die op wordt gebaseerd:
* aanvraagheaders en -eigenschappen (bijvoorbeeld IP-adres)
* verkeerspatronen gekend om met kwaadwillig verkeer worden geassocieerd

Wilt u de functie proberen en feedback delen? Een e-mail verzenden naar **aemcs-waf-adopter@adobe.com** van uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie. De ruimte is beperkt.

Meer informatie over de functie in het artikel [hier](/help/security/traffic-filter-rules-including-waf.md).

### Andere wijzigingen in de Stichting {#other-foundation-changes}

* In de week van 7 augustus retourneert AEM foutcode 429 in plaats van foutcode 503 wanneer aanvragen om AEM instanties een gezond niveau overschrijden. [Meer informatie](/help/implementing/developing/introduction/development-guidelines.md).

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
