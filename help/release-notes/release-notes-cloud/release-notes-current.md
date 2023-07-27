---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 8efe5d66929d1e2ccd7af71a2de8ae02f2bbc290
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

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

Bekijk de video Overzicht van de release van juli 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.6.0:

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

* MSM voor inhoudsfragmenten. AEM Multisite Manager is nu beschikbaar voor inhoudsfragmenten, zodat u Actieve kopieën van inhoudsfragmenten kunt maken voor distributie van bulkinhoud. De korrelige overervingscontroles zijn beschikbaar neer aan het Element van het Fragment van de Inhoud en het niveau van de Variatie.

### Nieuwe functies in [!DNL Experience Manager Sites] prerelease {#prerelease-sites}

* De [Console voor inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en) Gebruikers kunnen nu tags weergeven en zoeken op tags die als metagegevens zijn toegepast op Inhoudsfragmenten. Gebruikers hoeven voor deze mogelijkheid niet meer over te schakelen op de interface Elementen, waardoor contextomschakeling wordt beperkt en de efficiëntie wordt verbeterd.

![Tags toevoegen in Content Fragment Console](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de weergave Elementen {#assets-view-features}

**Metagegevensformulier toewijzen aan een map**

U kunt nu een metagegevensformulier toewijzen aan een specifieke map in uw Assets Essentials-implementatie. Alle elementen in de map, inclusief de elementen in de submappen, geven vervolgens de eigenschappen weer die in het toegewezen metagegevensformulier zijn gedefinieerd.

![metagegevensformulier toewijzen aan een map](/help/release-notes/assets/assign-to-folder.png)

**Verbeterd kunstmatig intelligentiekader voor beeld Slimme Markeringen**

Experience Manager Assets maakt nu gebruik van een verbeterd kader voor kunstmatige intelligentie voor slimme afbeeldingstags. Deze inhoudsinfo geeft een betere relevantie en nauwkeurigheid van slimme tags die beschikbaar zijn voor alle afbeeldingselementen bij opname.

**Weergave van kolommen configureren voor de weergave Lijst met elementen**

Assets Essentials biedt nu de mogelijkheid om de kolommen te selecteren die in de weergave Lijst met elementen worden weergegeven, zoals Status, Indeling, Dimension, Grootte, enzovoort.

![Kolommen configureren](/help/release-notes/assets/configure-columns.png)

**Zoekresultaten sorteren op basis van relevantie**

Assets Essentials sorteert de zoekresultaten nu standaard op Relevance. U kunt de gezochte middelen in stijgende of dalende orde van sorteren `Name`, `Relevance`, `Size`, `Modified`, en `Created`.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Buiten-de-box thema&#39;s**](/help/forms/using-themes-in-core-components.md) **en sjablonen**: Kickstart uw formulierontwerpproces met onze gebruiksklare OTB-thema&#39;s en -sjablonen, speciaal ontworpen voor ervaren professionals en nieuwe formulierauteurs. Dankzij deze nauwgezette thema&#39;s en sjablonen, die naadloos zijn gebouwd met Adaptive Forms Core Components, kunt u snel formulieren maken voor veelgebruikte toepassingen.


* **Componenten reageren voor Forms zonder hoofd**: U kunt nu een voorbeeld bekijken van de koploze adaptieve formulieruitvoeringen en deze aanpassen met de React-componenten in het vak. Deze componenten maken gebruik van BEM-klassen van Adaptive Forms Core Components for styling, waardoor het voor u gemakkelijker wordt om de weergave aan te passen aan uw specifieke vereisten.

  Dankzij de integratie met Adobe Acrobat Sign Solutions for Government kunnen Adobe en klanten van de overheid elektronische handtekeningen gebruiken in Adaptive Forms voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die Adobe klanten van vrede van mening voorzien.

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

Meer informatie over de functie in het artikel [hier](/help/security/cdn-and-waf-rules.md).

### Andere wijzigingen in de Stichting {#other-foundation-changes}

* In de week van 7 augustus retourneert AEM foutcode 429 in plaats van foutcode 503 wanneer aanvragen om AEM instanties een gezond niveau overschrijden. [Meer informatie](/help/implementing/developing/introduction/development-guidelines.md).

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
