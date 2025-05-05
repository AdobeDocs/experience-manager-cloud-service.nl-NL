---
title: Nota's van de versie voor 2022.3.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.3.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 761f1605-c421-4f3a-8f90-af23f4f047b1
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.3.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.3.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.3.0) is 31 maart 2022.
De volgende release (2022.4.0) is gepland voor 5 mei 2022.

## Video vrijgeven {#release-video}

Heb een blik bij de [ Maart 2022 het Overzicht van de Versie ](https://video.tv.adobe.com/v/341465) video voor een samenvatting van de eigenschappen die in de versie 2022.3.0 worden toegevoegd.

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies beschikbaar in [!DNL Sites] prereleasekanaal {#prerelease-features-sites}

* De gegevenstypen van het inhoudsmodel kunnen nu worden gedefinieerd als vertaalbaar met behulp van een eenvoudig selectievakje in de inhoudsmodeleditor. Bovendien worden AEM vertaalregels en -configuraties automatisch bijgewerkt.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] verstrekt nu de flexibiliteit om [ één alias rekening ](/help/assets/dynamic-media/dm-alias-account.md) in het gebruikersinterface te vormen, daardoor het verzekeren van uit-van-de-doos Dynamic Media URLs en de Kijker bedt code wordt bijgewerkt. Dit heeft een positieve invloed op SEO om de updates te weerspiegelen die zijn aangebracht in uw zakelijke context, zoals herbranding.

* U kunt nu de gebruikersinterface van [!DNL Experience Manager Assets] gebruiken om:

   * Vorm de [ opsporing van dubbele activa ](/help/assets/detect-duplicate-assets.md) in een bewaarplaats.

   * Vorm [ toevoegend digitale watermerken ](/help/assets/watermark-assets.md) aan beelden.

* De beheerders kunnen nu de e-mailservice configureren voor grote downloads. Het staat de gebruikers toe om [ e-mailberichten voor grote downloads ](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) van de [!DNL Experience Manager Assets] interface toe te laten. De gebruiker ontvangt een e-mailbericht met de downloadkoppeling van de gearchiveerde ZIP-map na voltooiing van het downloadproces.

* [ leidt de eigenschap van de Publicatie ](/help/assets/manage-publication.md) wordt verbeterd met een beter gebruikersinterface. De gebruikers kunnen inhoud publiceren of unpublish aan en van de geselecteerde bestemming, [ toevoegen Inhoud ](/help/assets/manage-publication.md#add-content) aan de het publiceren lijst van over de bewaarplaats DAM, [ omvatten de Montages van de Omslag ](/help/assets/manage-publication.md#include-folder-settings) om inhoud van de geselecteerde omslagen te publiceren en filters toe te passen, en [ plannen het publiceren ](/help/assets/manage-publication.md#publish-assets-later) aan een recentere datum of een tijd.

### Nieuwe functies beschikbaar in [!DNL Assets] prereleasekanaal {#prerelease-features-assets}

* U kunt [ soortmarkeringen ](/help/assets/organize-assets.md#use-tags-to-organize-assets) in het venster van de markeringsplukker nu in het stijgen of dalende orde die op de markeringsnaam, datum van verwezenlijking, of datum van wijziging wordt gebaseerd.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [ de Generatie APIs van het Document ](/help/forms/aem-forms-cloud-service-communications.md) helpen om, PDF documenten te combineren opnieuw te rangschikken en te bevestigen. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Stel PDF-documenten samen.
   * U kunt PDF-documenten deassembleren.
   * Converteren naar documenten die compatibel zijn met PDF/A en deze valideren.

* **zet automatisch PDF forms die groter zijn dan 15 pagina&#39;s in adaptieve vormen** om: U kunt de dienst van de automatede form conversion nu gebruiken om PDF forms met maximaal 40 pagina&#39;s in adaptieve vormen om te zetten. De service biedt nu opties om secties met formulieren groter dan 15 pagina&#39;s om te zetten in adaptieve formulierfragmenten. Het verbetert de rendersnelheid van geconverteerde formulieren en maakt het gemakkelijker om grote formulieren in een adaptieve formuliereditor te laden.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* **douane XCI van het Gebruik voor het produceren van een Document van Verslag**: U kunt een douaneXCI dossier nu gebruiken om diverse eigenschappen van een Document van Verslag te plaatsen. De aangepaste wijzigingen hebben voorrang op de hoofd-XCI.

* **Onzichtbare CAPTCHA van het Gebruik in een adaptieve vorm**: U kunt onzichtbare CAPTCHA gebruiken om de uitdaging van CAPTCHA slechts in het geval van een verdachte activiteit te tonen. Als er geen verdachte activiteit wordt gevonden, wordt de CAPTCHA-uitdaging niet weergegeven.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Verbeterde SEO voor meerdere opslagscenario&#39;s: URL-indelingen voor PDP / PLP kunnen nu op archiefniveau worden geconfigureerd via de CIF Cloud Config-eigenschappen
* Productkiezer ondersteunt gefaseerde producten via een nieuwe filteroptie in de gebruikersinterface.  Hierdoor kunnen gebruikers van inhoud het beheer van de productinhoud voorbereiden op de volgende productlanceringen
* Vereenvoudigd CIF configuratiebeheer en foutafhandeling met de naam CIF Cloud Config in plaats van proxyURL te configureren
* Handmatige categorieselectie voor productlijst en carrouselcomponenten. Hierdoor kunnen gebruikers van inhoud deze componenten gebruiken op inhoudspagina&#39;s, buiten de ervaring met catalogi

### Nieuwe functies beschikbaar in CIF prerelease-kanaal {#prerelease-features-cif}

* AEM CIF Core-component zoeken ondersteunt Commerce LiveSearch

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Voor efficiëntere en effectievere het oplossen van problemen van douaneeigenschappen in de milieu&#39;s van de Wolk, hebben wij een nieuw ontwikkelaarshulpmiddel vrijgegeven - [ Browser van de Bewaarplaats ](/help/implementing/developing/tools/repository-browser.md). Het is een lichtgewicht, alleen-lezen, HTML-browser die u kunt starten vanuit de Developer Console. U krijgt zichtbaarheid in de opslagplaats voor inhoud op de uitgever-, auteur- en voorvertoningslagen en in alle omgevingen, inclusief productie, werkgebied en ontwikkeling. Blader door de inhoudsstructuur, de weergave-eigenschappen en de binaire bestanden voor voorvertoningen en downloaden.

  ![ repobrowserrelnotes ](/help/release-notes/assets/repobrowserrelnotes.png)

* De referenties die worden gebruikt voor het verifiëren van API-aanroepen van server naar server (bijvoorbeeld voor GraphQL API-aanvragen) kunnen nu worden vernieuwd voordat ze verlopen op een zelfstandige manier vanuit de Developer Console. Zie de [ documentatie ](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) voor meer info.

* De het zuiveren van de versie en de taken van het de zuiveringslogboek van de controle, die niet eerder waren toegelaten, worden nu toegelaten voor nieuwe milieu&#39;s. Zie de bijbehorende waarden in het [&#128279;](/help/operations/maintenance.md) artikel van de Taak van 0&rbrace; Onderhoud &lbrace;.

* AEM as a Cloud Service SDK Dispatcher Tools biedt nu ondersteuning voor Mac-computers met de M1-chip

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.9.0 is 28 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Hulplijnen voor grootte controleren - Met de functie voor het controleren van de grootte van het gereedschap Inhoud overbrengen kunt u mislukte overdrachten van inhoud reduceren.  Met de functie Grootte controleren kunnen gebruikers 1) bepalen of ze voldoende schijfruimte hebben in de submap `crx-quickstart` voordat ze de map extraheren, en 2) de grootte van de migratieset schatten en controleren of deze wordt ondersteund. Als één of allebei van deze controles worden geschonden, zien de gebruikers waarschuwingen in CTT UI. Met deze garantie kunt u mislukte inhoudsoverdrachten voorkomen en de migratieopties proactief bespreken met de klantenservice van de Adobe. Zie [ het Bepalen van migratie vastgestelde grootte en schijfruimte ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#migration-set-size) voor meer details.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.26 is 16 maart 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om niet-verwerkte activa te detecteren. Als onverwerkte middelen worden ontdekt, moeten deze activa of aan verwerkt worden geplaatst of moeten uit de migratie worden verwijderd die tijdens inhoudstransmissie wordt geplaatst om lopende in kwesties tijdens inhoudsinname te vermijden.
* Mogelijkheid om te detecteren of inhoud meer dan 1000 vanity-URL&#39;s heeft. Het gebruik van een hoge mate van ijdelheid-URL&#39;s is niet de beste manier, omdat het laden ervan op Dispatcher- en Publish-servers plaatsvindt.
* Mogelijkheid om problemen met betrekking tot Oak-indexdefinities te identificeren en incompatibiliteiten met AEM as a Cloud Service op te sporen.
* Mogelijkheid om het gebruik van Externalzer-configuraties te detecteren en hierover verslag uit te brengen. In de configuraties van Externalalizer van AEM as a Cloud Service worden geplaatst door Cloud Manager, vandaar, moeten de bestaande configuraties Externalzer worden verfijnd om verenigbaarheid te handhaven.

### Opgeloste problemen {#bug-fixes-bpa}

* In sommige gevallen kon BPA niet worden uitgevoerd omdat FormsSelectiveFeaturesAnalysis een assertiefout genereerde. Dit is opgelost.
* BPA rapporteerde bevindingen met betrekking tot het WRK-patroon als MAJOR in plaats van als KRITIEK. Dit is opgelost.
* BPA rapporteerde onjuist bevindingen met betrekking tot OAK-indexdefinities in ui.apps als CRITICAL. Dit is opgelost
