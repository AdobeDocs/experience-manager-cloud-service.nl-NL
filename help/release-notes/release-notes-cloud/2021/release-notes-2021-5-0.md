---
title: Opmerkingen bij de release 2021.5.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2021.5.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 3f9d7339-7e37-4702-821e-f2b03cd7e224
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>Van hieruit kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.5.0 is 27 mei 2021.
De volgende release (2021.6.0) vindt plaats op 28 juni 2021.

## AEM as a Cloud Service stichting {#foundation}

### Nieuw in AEM as a Cloud Service Stichting {#what-is-new-foundation}

* [Prerelease-kanaal](/help/release-notes/prerelease.md): Bekijk de volgende functies een volledige maand voordat u live gaat in productie!

* [API-veroudering](/help/release-notes/deprecated-removed-features.md): er is een lijst beschikbaar met de meest recente vervangen API&#39;s voor AEM as a Cloud Service.

* [AEM as a Cloud Service SDK Build Analyzer Maven Plugin](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): Werk uw gemaakte projecten bij naar de nieuwste versie, die een verouderde Java API-controle en andere verbeteringen bevat.

## [!DNL Adobe Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* U kunt de inhoud binnenkort verifiëren op een nieuwe [Voorvertoning laag](/help/sites-cloud/authoring/sites-console/previewing-content.md) om de definitieve ervaring te simuleren kijkt en voelt zoals u op de Publish rij. Dit wordt ingeschakeld door de AEM Sites Managed Publication-wizard, waarmee u nu een publicatiebestemming kunt kiezen tussen Publiceren of Voorvertoning. Ervaring met Voorvertoning is dan toegankelijk via een specifieke URL. Na validatie bij Voorvertoning kan inhoud op de gebruikelijke manier van Auteur worden gepubliceerd om te publiceren. Het inschakelen van de voorvertoningsservice in AEM as a Cloud Service omgevingen wordt in de komende weken geleidelijk uitgevoerd.

## [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* U kunt de gedeelde elementen downloaden met de functie voor delen van koppeling. Deze download gebruikt nu een asynchrone service die sneller en ononderbroken downloads biedt, zelfs voor zeer grote downloads. Zie [downloadmiddelen](/help/assets/download-assets-from-aem.md#link-share-download).

  ![Postvak IN downloaden](/help/assets/assets/download-inbox.png)

### Nieuwe functies beschikbaar in het prerelease-kanaal {#what-is-new-assets-prerelease}

* Metagegevensschema&#39;s kunnen rechtstreeks op de mapeigenschappen worden toegepast.

  ![Metagegevensschema toevoegen uit mapeigenschappen](/help/assets/assets/metadata-schema-folder-properties.png)

* Met het gereedschap Asset Bulk Ingestor kunt u metagegevens toevoegen tijdens een grote opname.

* Dankzij de verbeteringen in de gebruikerservaring wordt het aantal elementen in een map weergegeven. Voor meer dan 1000 elementen in een map: [!DNL Assets] geeft 1000+ weer.

  ![Het aantal elementen in een map wordt weergegeven op de interface](/help/assets/assets/browse-folder-number-of-assets.png)

### Buizen vastgesteld in [!DNL Assets] {#assets-bugs-fixed}

* Als u zeer grote bestanden uploadt, loopt de [!DNL Experience Manager desktop app]. (CQ-4320942)
* De werkbalkopties verschillen wanneer dezelfde verzameling in een map is geselecteerd en wanneer deze is geselecteerd uit een zoekresultaat. (CQ-4321406)

#### Nieuwe functies in Dynamic Media {#what-is-new-dm}

* Met de functie Smart Imaging DPR (Device Pixel Ratio) en de optimalisatie van de netwerkbandbreedte kunt u op efficiënte wijze beelden van de beste kwaliteit leveren op apparaten met beeldschermen met hoge resolutie en beperkte netwerkbandbreedte. Zie voor meer informatie [Veelgestelde vragen over slimme beeldverwerking](/help/assets/dynamic-media/imaging-faq.md) en [Optimalisatie van afbeeldingen met de volgende generatie afbeeldingsindelingen WebP en AVIF.](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)
* Introductie van ondersteuning voor AVIF van de volgende generatie voor afbeeldingsindeling in Dynamic Media-levering (fmt URL-modifier).

## [!DNL Adobe Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Contextafhankelijke Help**: Er is contextafhankelijke Help toegevoegd voor een aangepaste formuliereditor, sjablooneditor en themaeditor om auteurs te helpen verschillende functies van editors beter te begrijpen.
* **Foutberichten in de browser Eigenschappen**: Foutberichten toegevoegd voor elke eigenschap in de browser Adaptive Forms Properties. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

### De aanstaande bètafunctie van [!DNL Forms] {#what-is-new-forms-prerelease}

Uitvoer als cloudservice: de uitvoerservice helpt u bij het combineren van XDP-sjablonen en XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone en asynchrone batchmodus. Met uitvoerservice kunt u toepassingen maken waarmee u:

* Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
* Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
* Afdruk-PDF genereren op basis van XFA-formulier-PDF.

U kunt schrijven naar formscsbeta@adobe.com om u aan te melden voor het bètaprogramma.

### Buizen vastgesteld in [!DNL Forms] {#forms-bugs-fixed}

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

* Het implementatielogboek dat door een gebruiker van Cloud Manager is gedownload, is begrijpelijker en bevat details over fouten en successcenario&#39;s.

* Intermitterende fouten die werden aangetroffen tijdens het doorvoeren van code naar de Adobe-kit, zijn nu opgelost.

* De invoegtoepassing Commerce kan nu worden toegepast op Sandbox-programma&#39;s tijdens de workflow van het programma Bewerken.

* De ervaring met het bewerkingsprogramma is vernieuwd.

* De lijst van de Namen van het Domein in de pagina van Details van het Milieu zal tot 250 namen van Domein via paginering tonen.

* Het lusje van Oplossingen in Add Programma en geef de werkschema&#39;s van het Programma uit zal de oplossing tonen, zelfs als slechts één oplossing voor het Programma beschikbaar is.

* Het foutenbericht in het bouwstijlstaplogboek toen de bouwstijl geen opgestelde inhoudspakketten produceerde was onduidelijk.

### Opgeloste problemen {#bug-fixes-cm-may}

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* In plaats van &#39;verwijderde&#39; variabelen te verwijderen, markeert de API voor pijpleidingvariabelen deze alleen met status **VERWIJDERD**.

* Sommige kwaliteitskwesties van het type Code Smell hadden een onjuiste invloed op de beoordeling Betrouwbaarheid.

* Omdat jokertekendomeinen niet worden ondersteund, staat de gebruikersinterface de gebruiker niet toe een jokertekendomein in te dienen.

* Wanneer een pijpleidingsuitvoering tussen middernacht en 1am UTC werd begonnen, werd de artefactversie die door de Manager van de Wolk werd geproduceerd niet gewaarborgd om groter te zijn dan een versie die de vorige dag werd gecreeerd.

* Tijdens de opstelling van het programma Sandbox, zodra het project met steekproefcode met succes is gecreeerd, zal Manage Git als verbinding van de heldenkaart in de pagina van het Overzicht verschijnen.

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.4.6 is 27 mei 2021.

### Wat is er nieuw? {#what-is-new-ctt-latest}

* Er is een nieuwe logboekinstructie toegevoegd aan het foutenlogboek van de quickstart als de gebruiker geen machtigingen heeft voor het uitvoerbare bestand van Java.

* Wanneer een gebruiker een migratieset verwijdert uit de CTT-gebruikersinterface, waar een extractie is uitgevoerd, wordt `tmp` de map die aan die migratieset is gekoppeld, wordt verwijderd om ruimte te besparen.

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
* Inhoud overbrengen met `wipe=true` heeft geresulteerd in een onjuiste telindex op het doel. Dit is opgelost.

## Commerce-invoegtoepassing {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Pagineringsondersteuning voor gekoppelde inhoud in eigenschappen van productconsole

### Opgeloste problemen {#bug-fixes-commerce}

* Miniaturen van middelen worden niet weergegeven op het tabblad Middelen van de producteigenschappen

* Breadcrumb herstelt voorvertoningsgegevens in productconsole
