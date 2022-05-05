---
title: Opmerkingen bij de release 2022.3.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.3.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 5d0f6fb726527434c57dc058bcf3a7b9d512b551
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021, enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] De huidige release (2022.3.0) is 31 maart 2022.
De volgende release (2022.4.0) is gepland voor 5 mei 2022.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release maart 2022](https://video.tv.adobe.com/v/341465) video voor een overzicht van de functies die in de release 2022.3.0 zijn toegevoegd.

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies beschikbaar in [!DNL Sites] prerelease-kanaal {#prerelease-features-sites}

* De gegevenstypen van het inhoudsmodel kunnen nu worden gedefinieerd als vertaalbaar met behulp van een eenvoudig selectievakje in de inhoudsmodeleditor. Bovendien worden AEM vertaalregels en configuraties automatisch bijgewerkt.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] biedt nu de flexibiliteit om [één alias-account configureren](/help/assets/dynamic-media/dm-alias-account.md) in de gebruikersinterface, waarbij ervoor wordt gezorgd dat Dynamic Media-URL&#39;s en code voor insluiten van de viewer buiten de box worden bijgewerkt. Dit heeft een positieve invloed op SEO om de updates te weerspiegelen die zijn aangebracht in uw zakelijke context, zoals herbranding.

* U kunt nu de opdracht [!DNL Experience Manager Assets] gebruikersinterface naar:

   * Configureer de [detectie van dubbele elementen](/help/assets/manage-digital-assets.md#detect-duplicate-assets) in een opslagplaats.

   * Configureren [toevoegen van digitale watermerken](/help/assets/watermark-assets.md) naar afbeeldingen.

* De beheerders kunnen nu de e-mailservice configureren voor grote downloads. Hiermee kunnen gebruikers [e-mailmeldingen inschakelen voor grote downloads](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) van de [!DNL Experience Manager Assets] interface. De gebruiker ontvangt een e-mailbericht met de downloadkoppeling van de gearchiveerde ZIP-map na voltooiing van het downloadproces.

* De [Publicatie beheren](/help/assets/manage-publication.md) wordt verbeterd met een verbeterde gebruikersinterface. De gebruikers kunnen inhoud publiceren of unpublish aan en van de geselecteerde bestemming. [Inhoud toevoegen](/help/assets/manage-publication.md#add-content) naar de publicatielijst vanuit de DAM-opslagplaats, [Inclusief mapinstellingen](/help/assets/manage-publication.md#include-folder-settings) de inhoud van de geselecteerde mappen publiceren en filters toepassen, en [publiceren plannen](/help/assets/manage-publication.md#publish-assets-later) naar een latere datum of tijd.

### Nieuwe functies beschikbaar in [!DNL Assets] prerelease-kanaal {#prerelease-features-assets}

* U kunt nu [sorteertags](/help/assets/organize-assets.md#use-tags-to-organize-assets) in het venster met de tagkiezer in oplopende of aflopende volgorde op basis van de tagnaam, aanmaakdatum of wijzigingsdatum.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [API&#39;s voor het genereren van documenten](/help/forms/aem-forms-cloud-service-communications.md) Help bij het combineren, herschikken en valideren van PDF-documenten. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Stel PDF-documenten samen.
   * U kunt PDF-documenten deassembleren.
   * Converteren naar documenten die compatibel zijn met PDF/A en deze valideren.

* **Automatisch PDF forms van meer dan 15 pagina&#39;s converteren naar adaptieve formulieren**: U kunt nu de service automatede form conversion gebruiken om PDF forms met maximaal 40 pagina&#39;s om te zetten in adaptieve formulieren. De service biedt nu opties om secties met formulieren groter dan 15 pagina&#39;s om te zetten in adaptieve formulierfragmenten. Het verbetert de rendersnelheid van geconverteerde formulieren en maakt het gemakkelijker om grote formulieren in een adaptieve formuliereditor te laden.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **Aangepaste XCI gebruiken voor het genereren van een document met records**: U kunt nu een aangepast XCI-bestand gebruiken om verschillende eigenschappen van een Document of Record in te stellen. Het treedt master XCI met de douaneveranderingen met voeten.

* **Onzichtbare CAPTCHA gebruiken in een adaptieve vorm**: U kunt de onzichtbare CAPTCHA gebruiken om de CAPTCHA-uitdaging alleen te tonen in het geval van een verdachte activiteit. Als er geen verdachte activiteit wordt gevonden, wordt de CAPTCHA-uitdaging niet weergegeven.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Verbeterde SEO voor meerdere winkelscenario&#39;s: URL-indelingen voor PDP/PLP kunnen nu op archiefniveau worden geconfigureerd via de CIF Cloud Config-eigenschappen
* Productkiezer ondersteunt gefaseerde producten via een nieuwe filteroptie in de gebruikersinterface.  Hierdoor kunnen gebruikers van inhoud het beheer van de productinhoud voorbereiden op de volgende productlanceringen
* Vereenvoudigd CIF-configuratiebeheer en foutafhandeling door CIF Cloud Config-naam te gebruiken in plaats van proxyURL te configureren
* Handmatige categorieselectie voor productlijst en carrouselcomponenten. Hierdoor kunnen gebruikers van inhoud deze componenten gebruiken op inhoudspagina&#39;s, buiten de ervaring met catalogi

### Nieuwe functies beschikbaar in het CIF-prerelease-kanaal {#prerelease-features-cif}

* AEM ondersteuning voor Kerncomponent CIF Search Commerce LiveSearch

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Voor efficiëntere en effectievere probleemoplossing van aangepaste functies in cloudomgevingen hebben we een nieuwe ontwikkelaarstool uitgebracht - [de Repository Browser](/help/implementing/developing/tools/repository-browser.md). Het is een lichte, alleen-lezen browser van de HTML die u kunt starten vanuit de Developer Console. U krijgt zichtbaarheid in de opslagplaats voor inhoud op de uitgever-, auteur- en voorvertoningslagen en in alle omgevingen, inclusief productie, werkgebied en ontwikkeling. Blader door de inhoudsstructuur, de weergave-eigenschappen en de binaire bestanden voor voorvertoningen en downloads.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* De referenties die worden gebruikt voor het verifiëren van API-aanroepen van server naar server (bijvoorbeeld voor GraphQL API-aanvragen) kunnen nu worden vernieuwd voordat deze verlopen op een zelfstandige manier vanuit de Developer Console. Zie de [documentatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) voor meer informatie.

* De het zuiveren van de versie en de taken van het de zuiveringslogboek van de controle, die niet eerder waren toegelaten, zullen voor nieuwe milieu&#39;s worden toegelaten. Zie de gekoppelde waarden in het dialoogvenster [Onderhoudstaken](/help/operations/maintenance.md) artikel.

* AEM as a Cloud Service SDK Dispatcher Tools biedt nu ondersteuning voor Mac-computers met de M1-chip

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.9.0 is 28 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Hulplijnen voor grootte controleren - Met de functie voor het controleren van de grootte van het gereedschap Inhoud overbrengen kunt u mislukte overdrachten van inhoud reduceren.  Met de functie Grootte controleren kunnen gebruikers 1) bepalen of ze voldoende schijfruimte hebben in het dialoogvenster `crx-quickstart` subdirectory voor extractie en 2) maak een schatting van de grootte van de migratieset en controleer of deze wordt ondersteund. Als één of beide controles worden geschonden, zullen de gebruikers waarschuwingen in CTT UI zien. Met deze garantie kunt u mislukte inhoudsoverdrachten voorkomen en de migratieopties proactief bespreken met de klantenservice van Adobe. Zie [Grootte en schijfruimte van migratieset bepalen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) voor meer informatie .

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.26 is 16 maart 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om niet-verwerkte activa te detecteren. Als onverwerkte middelen worden ontdekt, moeten deze activa of aan verwerkt worden geplaatst of moeten uit de migratie worden verwijderd die tijdens inhoudstransmissie wordt geplaatst om lopende in kwesties tijdens inhoudsinname te vermijden.
* Mogelijkheid om te detecteren of inhoud meer dan 1000 vanity-URL&#39;s heeft. Het gebruik van een hoog aantal vanity-URL&#39;s is niet de beste manier, omdat hiermee een laadbewerking wordt uitgevoerd op de servers Dispatcher en Publish.
* Mogelijkheid om problemen met betrekking tot de definities van de eikenindex te identificeren en incompatibiliteiten met AEM as a Cloud Service vast te stellen.
* Mogelijkheid om het gebruik van Externalzer-configuraties te detecteren en hierover verslag uit te brengen. In AEM as a Cloud Service configuraties Externalzer worden ingesteld door Cloud Manager. Daarom moeten bestaande configuraties Externalzer worden vernieuwd om de compatibiliteit te behouden.

### Opgeloste problemen {#bug-fixes-bpa}

* In sommige gevallen kon BPA niet worden uitgevoerd omdat FormsSelectiveFeaturesAnalysis een assertiefout genereerde. Dit is opgelost.
* BPA rapporteerde bevindingen met betrekking tot het WRK-patroon als MAJOR in plaats van als KRITIEK. Dit is opgelost.
* BPA rapporteerde onjuist bevindingen met betrekking tot OAK-indexdefinities in ui.apps als CRITICAL. Dit is opgelost
