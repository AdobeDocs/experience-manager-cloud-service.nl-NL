---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9303ecadea38d83bd71ed0d440067bae5c419940
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 16971 {#release-16971}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 16971 samengevat, die op 3 juli 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16799.

2024.7.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie .

### Verbeteringen {#enhancements-16971}

* SITES-22948: Verwijder handelsverwijzingen in stichtingsinhoud voor AEM CS.
* SITES-22141 [Inhoudsfragmenten] SegmentNotFoundException van CFM ModelChangeRepositoryImpl na OnRC.
* SITES-21893: Uitsnijdprobleem van afbeeldingen bij de auteur-instantie.
* SITES-21788: [Inhoudsfragmenten] Toon NOTA in CF en CF modelredacteur wanneer uiSchema voor het model wordt toegelaten.
* SITES-21688: Bij MSM-rollout wordt het fragmentpad (XF) niet bijgewerkt op pagina&#39;s met live kopieën.
* SITES-21659: Terugkeer volledige naam van de gebruiker die een Model middel creeert/wijzigt/repliceert.
* SITES-21609: eindpunt OpenAPI om inhoudsfragmenten van één model aan andere te migreren.
* SITES-21598: [API openen] Creeer CFM - terugkeerfout als de bepaalde Weg van de Configuratie niet bestaat.
* SITES-21491: [API openen] Het eindpunt van CF-PATCH moet live relaties op veldniveau respecteren.
* SITES-21434: [API openen] Het eindpunt van CF-GET moet live relaties op veldniveau respecteren.
* SITES-21415: CF Editor - ondersteuning UUID-verwijzingen.
* SITES-21326: [API openen] Geef informatie over de aanwezigheid van referenties voor een inhoudsfragment.
* SITES-21310: [API openen] Id van inhoudsfragment toevoegen in API-reactie voor vertalingen.
* SITES-20859: CF Open API - Return references when retrieve a fragment by path.
* SITES-20687: [API openen] Eindpunt voor het terugwinnen van de status van de partijverwerking.
* SITES-20657: [API openen] Een optie geven voor het hele woord van match bij het vervangen van een tekenreeks met `FindAndReplace` eindpunt.
* SITES-20587: [API openen] Maken `COPY` eindpunt voor inhoudsfragmenten.
* SITES-20584: [API openen] Ophalen van verwijzingen optimaliseren.
* SITES-20308: [API openen] Batchverwerking op API inschakelen.
* SITES-1976: [API openen] Algemeen UI-schema voor voorwaardelijke velden.
* SITES-1956: [Inhoudsfragmenten] Werk uiSchema bij als dit bestaat wanneer het model wordt bewerkt.
* 18056: [API openen] Neem verwijzingen op wanneer u een inhoudsfragment naar Voorvertoning publiceert.
* SITES-16898: [Schema] Het eindpunt van OpenAPI om inhoudsfragmenten van één model aan andere te migreren.
* SITES-16609: Het eindpunt van Lanceringen van de Lijst.
* SITES-16606: Create Launch Endpoint.
* SITES-21617: [Xwalk] Maak Pagina-eigenschappen/Metagegevens bewerkbaar binnen de UE.
* SITES-19614: [Xwalk] Paginering van werkbladeditors en oneindig schuiven.
* SITES-22163 [Xwalk] Verbeterde ondersteuning voor inhoud die wordt aangeboden via de publicatielaag voor Edge Delivery-sites.
* SITES-22109: [Xwalk] Verbeterde verwerking van richtext-opmaakcodes na verwerking.
* SITES-2035: [Xwalk] Verbeterde verwerking van MSM en Launches.
* SITES-21839: [Xwalk] Verbeterde padtoewijzing en ontsmetting voor inhoud die niet door Edge Delivery wordt aangeboden.

### Opgeloste problemen {#fixed-issues-16971}

* CQ-4356898: [Vertaling] outOfMemory fout voor CF die een ongebruikelijk groot aantal verbindingen bevat.
* CQ-4357055: [Vertaling] Automatische omzetting werkt niet met de Rest API.
* CQ-4353931: [Vertaling] Voeg jcr:uuid toe in de pagina van de vertaalbron/xf/element als deze ontbreekt.
* CQ-4357591: [Vertaling] Wijzig de workflow &quot;Koppelen aan JCR:UID&quot; om te werken voor Pagina&#39;s/XF.
* FORMS-14844: Adaptive Forms staat het verzenden van formulieren toe, ondanks onvoldoende reCAPTCHA-verificatie.
* FORMS-14984: Forms met CAPTCHA slaat validatie over als &quot;submitMetaData&quot; niet aanwezig is in de verzonden gegevens.
* FORMS-14477: De opties &#39;Is na&#39; en &#39;Is voor&#39; in de regeleditor functioneren niet naar behoren in de datumkiezervalidatie.
* FORMS-14019: De functie &quot;Invoke Service&quot; van de redacteur van de Regel werkt niet in Universele Redacteur.
* FORMS-14336: Als er geen formulierveld is geselecteerd, moet de editor worden geopend met focus op het gehele formulierelement.
* FORMS-15061: De cirkel van de Lader blijft eindeloos bij het gebruiken aanhalen van de de dienstoptie in de regelredacteur.
* SITES-22457: Het bevorderen van een lancering die niet diep is werkt broninhoud niet bij.
* SITES-22748 [Inhoudsfragmenten] Foutafhandeling verbeteren voor updatetaak van inhoudsfragment
* SITES-22349 [Inhoudsfragmenten] ContentType voor lege cf-elementen met meerdere regels kan niet worden gewijzigd.
* SITES-22343 [Inhoudsfragmenten] Semantisch type &quot;opsomming&quot; wordt verbroken.
* SITES-22194: Na het instellen van de omleiding werkt model.json niet meer.
* SITES-21953: [API openen] Etag wordt gewijzigd op basis van de volgorde van de validationStatus.
* SITES-21894: [API openen] Verbeter de validatie van bovenliggende paden bij het maken van CF&#39;s.
* SITES-2187: [API openen] Ongeldige ETag die door POST variaties eindpunt is teruggekeerd.
* SITES-21657: [API openen] Verbeter bevestiging op het bezit van de Weg van het Onderzoek CF.
* SITES-21949: ongeldige cursor voor zoek-API&#39;s retourneert 500.
* SITES-20927: zoek APIs keert 500 terug wanneer de vraag mist.
* SITES-2054: [API openen] Wijzig het genereren van publicatiepakketnamen om ongewenste conflicten te voorkomen.
* SITES-19710: CVE-2022-47937 - Verwijder alle toepassingen van org.apache.sling.commons.json uit de Pagina-editor.
* SITES-1992: [Toegankelijkheid] Knop Staalkiezer voor notities bevat geen toegankelijke naam.
* SITES-10979: [Toegankelijkheid] Label is niet blijvend.
* SITES-10962: [Toegankelijkheid] Knop: de knop heeft geen rol.
* SITES-10905: [Toegankelijkheid] De status van de actieve component heeft geen contrastverhouding van 3 tot 1.
* SITES-2974:  [Toegankelijkheid] - Horizontaal schuiven bij een breedte van 320 px.
* SITES-22026: Kan ervaringsfragmenten niet verplaatsen tussen mappen in AEM
* SITES-22106: Taalswitchfunctionaliteit in de nieuwe editor voor contentfragmenten
* SITES-21980: Inconsistente verwerking voor op UUID-gebaseerde verwijzingstypen.
* SITES-7257: NPE in ThumbnailServlet.

### Bekende problemen {#known-issues-16971}

Geen.

### Kennisgeving wijzigen {#change-notice-16971}

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [de documentatie](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer informatie .

### Verouderde functies en API&#39;s {#deprecated-16971}

Als u wilt weten wat in AEM as a Cloud Service is vervangen of verwijderd, raadpleegt u [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md).

### Ingesloten technologieën {#embedded-tech-16971}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 64,0 | [Oak API 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,25,4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
