---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 372e40eb90d87d9ed366e08a3c0117068542680b
workflow-type: tm+mt
source-wordcount: '1427'
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
De volgende release (2022.4.0) is op 28 april 2022.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release maart 2022](https://video.tv.adobe.com/v/341465) video voor een overzicht van de functies die in de release 2022.3.0 zijn toegevoegd.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] biedt nu de flexibiliteit om [één alias-account configureren](/help/assets/dynamic-media/dm-alias-account.md) in de gebruikersinterface, waarbij ervoor wordt gezorgd dat Dynamic Media-URL&#39;s en code voor insluiten van de viewer buiten de box worden bijgewerkt. Dit heeft een positieve invloed op SEO om de updates te weerspiegelen die zijn aangebracht in uw zakelijke context, zoals herbranding.

* U kunt nu de opdracht [!DNL Experience Manager Assets] gebruikersinterface naar:

   * Configureer de [detectie van dubbele elementen](/help/assets/manage-digital-assets.md#detect-duplicate-assets) in een opslagplaats.

   * Configureren [toevoegen van digitale watermerken](/help/assets/watermark-assets.md) naar afbeeldingen.

* De beheerders kunnen nu de e-mailservice configureren voor grote downloads. Hiermee kunnen gebruikers [e-mailmeldingen inschakelen voor grote downloads](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) van de [!DNL Experience Manager Assets] interface. De gebruiker ontvangt een e-mailbericht met de downloadkoppeling van de gearchiveerde ZIP-map na voltooiing van het downloadproces.

* De [Publicatie beheren](/help/assets/manage-publication.md) wordt verbeterd met een verbeterde gebruikersinterface. De gebruikers kunnen inhoud publiceren of unpublish aan en van de geselecteerde bestemming. [Inhoud toevoegen](/help/assets/manage-publication.md#add-content) naar de publicatielijst vanuit de DAM-opslagplaats, [Inclusief mapinstellingen](/help/assets/manage-publication.md#include-folder-settings) de inhoud van de geselecteerde mappen publiceren en filters toepassen, en [publiceren plannen](/help/assets/manage-publication.md#publish-assets-later) naar een latere datum of tijd.

### Nieuwe functies beschikbaar in [!DNL Assets] prerelease-kanaal {#prerelease-features-assets}

* U kunt [sorteertags](/help/assets/organize-assets.md#use-tags-to-organize-assets) bij het maken van slimme tags en bij het toepassen van zoekfilters met behulp van de tags prediken.

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

* Bèta: AEM ondersteuning voor Kerncomponent CIF Search Commerce LiveSearch
* Verbeterde SEO voor meerdere winkelscenario&#39;s: URL-indelingen voor PDP/PLP kunnen nu op archiefniveau worden geconfigureerd via de CIF Cloud Config-eigenschappen
* Productkiezer ondersteunt gefaseerde producten via een nieuwe filteroptie in de gebruikersinterface.  Hierdoor kunnen gebruikers van inhoud het beheer van de productinhoud voorbereiden op de volgende productlanceringen
* Vereenvoudigd CIF-configuratiebeheer en foutafhandeling door CIF Cloud Config-naam te gebruiken in plaats van proxyURL te configureren
* Handmatige categorieselectie voor productlijst en carrouselcomponenten. Hierdoor kunnen gebruikers van inhoud deze componenten gebruiken op inhoudspagina&#39;s, buiten de ervaring met catalogi

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Voor efficiëntere en effectievere probleemoplossing van aangepaste functies in cloudomgevingen hebben we een nieuwe ontwikkelaarstool uitgebracht - [de Repository Browser](/help/implementing/developing/tools/repository-browser.md). Het is een lichte, alleen-lezen browser van de HTML die u kunt starten vanuit de Developer Console. U krijgt zichtbaarheid in de opslagplaats voor inhoud op de uitgever-, auteur- en voorvertoningslagen en in alle omgevingen, inclusief productie, werkgebied en ontwikkeling. Blader door de inhoudsstructuur, de weergave-eigenschappen en de binaire bestanden voor voorvertoningen en downloads.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* De referenties die worden gebruikt voor het verifiëren van API-aanroepen van server naar server (bijvoorbeeld voor GraphQL API-aanvragen) kunnen nu worden vernieuwd voordat deze verlopen op een zelfstandige manier vanuit de Developer Console. Zie de [documentatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) voor meer informatie.

* De het zuiveren van de versie en de taken van het de zuiveringslogboek van de controle, die niet eerder waren toegelaten, zullen voor nieuwe milieu&#39;s worden toegelaten. Zie de gekoppelde waarden in het dialoogvenster [Onderhoudstaken](/help/operations/maintenance.md) artikel.

* AEM as a Cloud Service SDK Dispatcher Tools biedt nu ondersteuning voor Mac-computers met de M1-chip

## Cloud Manager {#cloud-manager}

### Releasedatum februari {#release-date-cm-feb}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2022.02.0 is 10 februari 2022. De volgende release is gepland voor 10 maart 2022.

### Wat is er nieuw? {#what-is-new-cm-feb}

* Nieuw versneld [Webservicepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) zijn geïntroduceerd om HTTPD/verzender-configuratie uitsluitend te implementeren.
   * U moet AEM versie hebben `2021.12.6151.20211217T120950Z` of nieuwer en [deelnemen aan de flexibele modus van de verzendingsprogramma&#39;s](/help/implementing/dispatcher/disp-overview.md#validation-debug) om deze functie te gebruiken.
   * Dit onderdeel wordt geleidelijk ingevoerd gedurende de twee weken na de release van 2022.02.0.
* De landingservaring van Cloud Manager is vernieuwd voor verbeterde navigatie, eenvoudig schakelen tussen raster-/tegelweergaven en pop-ups voor snel overzicht van het programma.
* Een nieuwe drempelwaarde voor onvoldoende prestaties (`< D`) is toegevoegd aan de [betrouwbaarheidsmaatstaf.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * Klanten met ernstige kwaliteitsproblemen die van invloed zijn op de stabiliteit van het systeem, voornamelijk in verband met ongeldige indexen en workflowprocessen, kunnen pas implementeren als deze problemen zijn opgelost.
* De ernst van de `BannedPath` [kwaliteitsregel](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) is veranderd van blokker in kritiek.
* De pijplijntovenaar zal de gebruiker informeren wanneer een AEM omgevingsupdate alvorens een [Webservicepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) ermee geassocieerd.

### Opgeloste problemen {#bug-fixes-cm-feb}

* De oude wachtwoorden van de git-opslagplaats worden nu altijd ongeldig gemaakt wanneer een nieuw wachtwoord wordt gegenereerd.
* Het bijwerken van omgevingsvariabelen via de API heeft in zeldzame situaties geen invloed meer op de uitvoering van een pijpleiding.

### Releasedatum maart {#release-date-cm-march}

De releasedatum voor Cloud Manager versie 2022.3.0 in AEM as a Cloud Service 10 maart 2022. De volgende release is gepland voor 7 april 2022.

### Wat is er nieuw? {#what-is-new-cm-march}

* De toegang tot AEM het logboek van het Milieu kan worden gedaan gebruikend de rol van de Ontwikkelaar.

### Opgeloste problemen {#bug-fixes-cm-march}

* Een subset van handmatig gemaakte it-opslagruimten had een onjuiste naamwaarde waardoor de functie voor hergebruik van bouwmateriaal niet doeltreffend was. De namen van deze opslagruimten zijn gewijzigd en gebruikers zien de gecorrigeerde naam in de API/UI van Cloud Manager.
* Bij de productie van volledige stapelleidingen werden bouwartefacten van niet-productiepijpleidingen onjuist opnieuw gebruikt.
* Wanneer het toevoegen van of het uitgeven van een pijpleiding van de codekwaliteit, worden de opties om metrische mislukkingen te behandelen niet meer getoond.
* Sommige onverwachte configuraties van pijpleidingsvariabele konden in de bouwstijlstap veroorzaken.

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
