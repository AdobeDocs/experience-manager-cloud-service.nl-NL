---
title: Nota's van de versie voor 2021.5.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.5.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 3f9d7339-7e37-4702-821e-f2b03cd7e224
feature: Release Information
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>Van hieruit kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.5.0 is 27 mei 2021.
De volgende release (2021.6.0) vindt plaats op 28 juni 2021.

## AEM as a Cloud Service Foundation {#foundation}

### Nieuw in AEM as a Cloud Service Foundation {#what-is-new-foundation}

* [ het Kanaal van de preRelease ](/help/release-notes/prerelease.md): Voorproef komende eigenschappen voor een volledige maand alvorens zij in productie gaan!

* [ API Verdringing ](/help/release-notes/deprecated-removed-features.md): een lijst van recentste verouderde APIs voor AEM as a Cloud Service is beschikbaar.

* [ AEM as a Cloud Service SDK bouwt Analysator Gemaakte Insteekmodule ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): Werk uw beproefde projecten aan de recentste versie bij, die een verouderde controle van Java API en andere verbeteringen omvat.

## [!DNL Adobe Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* U zult binnenkort inhoud op een nieuwe [ rij van de Voorproef ](/help/sites-cloud/authoring/sites-console/previewing-content.md) kunnen verifiëren om de definitieve ervaring te simuleren kijkt en voelt zoals u op de rij van Publish zou. Dit wordt ingeschakeld door de AEM Sites Managed Publication-wizard, waarmee u nu een publicatiebestemming kunt kiezen tussen Publish of Voorvertoning. Ervaring met Voorvertoning is dan toegankelijk via een specifieke URL. Na validatie bij Voorvertoning kan inhoud op de gebruikelijke wijze van Auteur naar Publish worden gepubliceerd. Het inschakelen van de voorvertoningsservice in AEM as a Cloud Service-omgevingen wordt in de komende weken geleidelijk uitgevoerd.

## [!DNL Adobe Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* U kunt de gedeelde elementen downloaden met de functie voor delen van koppeling. Deze download gebruikt nu een asynchrone service die sneller en ononderbroken downloads biedt, zelfs voor zeer grote downloads. Zie [ downloadactiva ](/help/assets/download-assets-from-aem.md#link-share-download).

  ![ Inbox van de Download ](/help/assets/assets/download-inbox.png)

### Nieuwe functies beschikbaar in het prerelease-kanaal {#what-is-new-assets-prerelease}

* Metagegevensschema&#39;s kunnen rechtstreeks op de mapeigenschappen worden toegepast.

  ![ voeg meta-gegevensschema van omslageigenschappen ](/help/assets/assets/metadata-schema-folder-properties.png) toe

* Met het gereedschap Asset Bulk Ingestor kunt u metagegevens toevoegen tijdens een grote opname.

* Dankzij de verbeteringen in de gebruikerservaring wordt het aantal elementen in een map weergegeven. Voor meer dan 1000 elementen in een map geeft [!DNL Assets] 1000+ weer.

  ![ Aantal activa in een omslag worden getoond op de interface ](/help/assets/assets/browse-folder-number-of-assets.png)

### Buizen gecorrigeerd in [!DNL Assets] {#assets-bugs-fixed}

* Het uploaden van zeer grote dossiers loopt [!DNL Experience Manager desktop app] neer. (CQ-4320942)
* De werkbalkopties verschillen wanneer dezelfde verzameling in een map is geselecteerd en wanneer deze is geselecteerd uit een zoekresultaat. (CQ-4321406)

#### Nieuwe functies in Dynamic Media {#what-is-new-dm}

* Met de functie Smart Imaging DPR (Device Pixel Ratio) en de optimalisatie van de netwerkbandbreedte kunt u op efficiënte wijze beelden van de beste kwaliteit leveren op apparaten met beeldschermen met hoge resolutie en beperkte netwerkbandbreedte. Voor meer informatie, zie [ Slimme beelden FAQs ](/help/assets/dynamic-media/imaging-faq.md) en [ optimalisering van het Beeld met volgende generatie beeldformaten WebP en AVIF ](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4).
* Introductie van ondersteuning voor AVIF van de volgende generatie voor afbeeldingsindeling in Dynamic Media-levering (fmt URL-modifier).

## [!DNL Adobe Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Contextafhankelijke hulp**: Toegevoegde contextafhankelijke hulp voor adaptieve vormenredacteur, malplaatjeredacteur, en themaredacteur om auteurs te helpen diverse eigenschappen van redacteurs beter begrijpen.
* **de berichten van de Fout in browser van Eigenschappen**: Toegevoegde foutenmeldingen voor elk bezit in Adaptieve browser van Eigenschappen van Forms. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

### De aanstaande bètafunctie van [!DNL Forms] {#what-is-new-forms-prerelease}

Uitvoer als cloudservice: de uitvoerservice helpt u bij het combineren van XDP-sjablonen en XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone en asynchrone batchmodus. Met uitvoerservice kunt u toepassingen maken waarmee u:

* Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
* Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
* Afdruk-PDF genereren op basis van XFA-formulier-PDF.

U kunt schrijven naar formscsbeta@adobe.com om u aan te melden voor het bètaprogramma.

### Buizen gecorrigeerd in [!DNL Forms] {#forms-bugs-fixed}

* Wanneer u in een taakstap toewijzen van AEM Forms Workflows het standaardpictogram van de actieknoppen vervangt door een koraalpictogram, wordt de workflow beëindigd en wordt een uitzondering geregistreerd. De workflow wordt op de verwachte wijze uitgevoerd wanneer standaardpictogrammen worden gebruikt.
* Als u in de lay-outlaag het aantal kolommen wijzigt, de bewerkingslaag opent en enkele componenten in een deelvenster sleept, verschijnen er vierkante blauwe vakken in het inhoudsgebied van de adaptieve formuliereditor en reageert de editor niet meer.
* Foutbericht van een optie voor een regeleditor die betrekking heeft op het opgeven van een URL van een adaptief of extern element, is te lang en is niet gebruikersvriendelijk.


## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.5.0 beschreven.

### Releasedatum {#release-date-cm-may}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.5.0 is 6 mei 2021.
De volgende release is gepland voor 3 juni 2021.

### Wat is er nieuw? {#what-is-new-may}

* De PackageOverlaps kwaliteitsregel ontdekt nu gevallen waar het zelfde pakket veelvoudige tijden, dat wil zeggen, in veelvoudige ingebedde plaatsen, in de zelfde opgestelde pakketreeks werd opgesteld.

* Het eindpunt van de repository in de Public API bevat nu de Git URL.

* Het implementatielogboek dat door een Cloud Manager-gebruiker wordt gedownload, is begrijpelijker en bevat details over fouten en successcenario&#39;s.

* Intermitterende fouten die werden aangetroffen tijdens het doorvoeren van code naar de Adobe-kit, zijn nu opgelost.

* De invoegtoepassing Commerce kan nu worden toegepast op Sandbox-programma&#39;s tijdens de workflow van het programma Bewerken.

* De ervaring met het bewerkingsprogramma is vernieuwd.

* De lijst van de Namen van het Domein in de pagina van Details van het Milieu zal tot 250 namen van Domein via paginering tonen.

* Het lusje van Oplossingen in Add Programma en geef de werkschema&#39;s van het Programma uit zal de oplossing tonen, zelfs als slechts één oplossing voor het Programma beschikbaar is.

* Het foutenbericht in het bouwstijlstaplogboek toen de bouwstijl geen opgestelde inhoudspakketten produceerde was onduidelijk.

### Opgeloste problemen {#bug-fixes-cm-may}

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* In plaats van het verwijderen van &quot;geschrapte&quot;variabelen, zou API van pijpleidingsvariabelen hen met status **VERWIJDERD** slechts merken.

* Sommige kwaliteitskwesties van het type Code Smell hadden een onjuiste invloed op de beoordeling Betrouwbaarheid.

* Omdat jokertekendomeinen niet worden ondersteund, staat de gebruikersinterface de gebruiker niet toe een jokertekendomein in te dienen.

* Wanneer een pijpleidingsuitvoering tussen middernacht en 1am UTC werd begonnen werd de artefactversie die door Cloud Manager werd geproduceerd niet gewaarborgd om groter te zijn dan een versie die de voorafgaande dag werd gecreeerd.

* Tijdens de opstelling van het programma Sandbox, zodra het project met steekproefcode met succes is gecreeerd, zal Manage Git als verbinding van de heldenkaart in de pagina van het Overzicht verschijnen.

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.4.6 is 27 mei 2021.

### Wat is er nieuw? {#what-is-new-ctt-latest}

* Er is een nieuwe logboekinstructie toegevoegd aan het foutenlogboek van de quickstart als de gebruiker geen machtigingen heeft voor het uitvoerbare bestand van Java.

* Wanneer een gebruiker een migratieset verwijdert uit de CTT-gebruikersinterface waar een extractie is uitgevoerd, wordt de `tmp` -map die aan die migratieset is gekoppeld, verwijderd om ruimte te besparen.

### Opgeloste problemen {#bug-fixes-ctt-latest}

* Bij het verwijderen van een migratieset wordt soms een onnuttig foutbericht weergegeven in de CTT-gebruikersinterface. Dit is opgelost.

* Als gebruikers tijdens het uitvoeren van de gebruikerstoewijzing hetzelfde e-mailadres op het doel en de host hadden, maar verschillende gebruikersnamen hadden, zou de volledige invoer mislukken. Dit is opgelost. In een dergelijk conflicterend scenario, wordt de gebruiker/de groep overgeslagen en als conflict in het logboekdossier geregistreerd.

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.4.0 is 11 mei 2021.

### Wat is er nieuw? {#what-is-new-ctt-may}

* Met deze versie van het gereedschap Inhoud overbrengen maakt u tekstuitvoeringen voor elementen die naar de Cloud Service worden gemigreerd. Tekstuitvoeringen zijn vereist voor ondersteuning van het zoeken naar volledige tekst op ingesloten elementen.
* Het maximumaantal migratiesets van Content Transfer Tool dat een gebruiker kan maken, is verhoogd van 4 naar 10.

### Opgeloste problemen {#bug-fixes-ctt-may}

* De veelvoudige insectenmoeilijke situaties verwant met auto-verfrissen eigenschap in het Hulpmiddel van de Overdracht van de Inhoud UI.
* Het gereedschap Inhoud overbrengen met `wipe=true` heeft geresulteerd in een onjuiste index voor de teller van het doel. Dit is opgelost.

## Commerce-invoegtoepassing {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Pagineringsondersteuning voor gekoppelde inhoud in eigenschappen van productconsole

### Opgeloste problemen {#bug-fixes-commerce}

* Miniaturen van middelen worden niet weergegeven op het tabblad Middelen van de producteigenschappen

* Breadcrumb herstelt voorvertoningsgegevens in productconsole
