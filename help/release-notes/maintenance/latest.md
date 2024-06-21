---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 53b692b9f668387c889c28498bb20c67149e36be
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 16799 {#release-16799}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 16799 samengevat, die op 18 juni 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16544.

2024.6.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie .

### Verbeteringen {#enhancements-16799}

* ASSETS-31977: Verbeterde activiteiten voor het verplaatsen, kopiëren en verwijderen van bedrijfsmiddelen.
* ASSETS-33618: automatische transcriptie- en vertaalmogelijkheden voor video&#39;s in Dynamic Media.
* ASSETS-35185: Approval Action for ContentHub and DM and add properties to damAssetLucene properties.
* ASSETS-35533: Voeg DRM- en CAI-eigenschappen toe aan damAssetLucene-index.
* ASSETS-37280: Opeenvolgende taakafhandeling voor vertaling wanneer bronondertitel (vtt) nog steeds wordt verwerkt.
* ASSETS-37559: gebeurtenis Improved asset deleted.
* ASSETS-37723: Implementeer activa gepubliceerde gebeurtenis.
* ASSETS-37724: Implementeer activa niet-gepubliceerde gebeurtenis.
* ASSETS-38614: de verhogingen van de Verbinding van het aandeel UI.
* ASSETS-39601: pas validatieregex automatisch toe op de naam van de Asset Livecopy.
* ASSETS-39454: Upgrade to viewers 2024.5.0 in QuickStart.
* CNTBF-184: Onderliggende steunpaden `/conf` in Content Backflow.

### Opgeloste problemen {#fixed-issues-16799}

* ASSETS-37335: als u het deelvenster Zoeken in filter bewerkt, worden alle vakken uitgeschakeld.
* ASSETS-38069: AEM DAM-probleem met de voorvertoning van de PDF bij de selectie van de tijdlijnfilter.
* ASSETS-38215: Adobe Stock-licentieknop wordt weergegeven in AEM as a Cloud Service voor Enterprise-abonnement.
* ASSETS-38578: Onjuiste hyperlinks in het rapport voor het delen van middelenkoppelingen.
* ASSETS-38678: weergave-instellingen verbroken in Gegevens verzameling.
* ASSETS-39071: Voor het web geoptimaliseerde levering kan een uitzondering genereren als het oorspronkelijke renditiematype null is.
* ASSETS-39316: Sorteren op naam werkt niet in verzamelingen.
* ASSETS-39377: Bulk-import van OneDrive kan mislukken bij het ontvangen van backpressure van externe API.
* ASSETS-39428: Rendering issues in Copyright Management UI.
* CQ-4357150: Guava in cq-content-sync-bundel.
* GRANITE-52573: Verzoeken met een dubbele slash `//` worden geweigerd met statuscode 400.
* SCRNS-4194: Verwijder afhankelijkheid van Google Guava API&#39;s.
* SCRNS-4360: Ontbrekende Manage Publication &amp; Quick Publish Knoop voor niet-admin gebruikers in Inhoudsleverancier voor Kanalen.
* SCRNS-4323: Verberg/maak lanceringen van screens.html onbruikbaar.

### Bekende problemen {#known-issues-16799}

>[!NOTE]
> AEM de Techniek heeft een regressie voor de functionaliteit van Lanceringen geïdentificeerd die huidige AEM versies die met 16461 beginnen beïnvloedt. Vanwege deze regressie worden nieuwe opstarters (gemaakt nadat nieuwe releases zijn toegepast) die niet-diepe pagina&#39;s bevatten, niet goed gepromoveerd omdat er configuraties ontbreken.
> Als uw milieu&#39;s worden beïnvloed, is een shell manuscript om ontbrekende configuraties te identificeren en bij te werken beschikbaar door klantensteun (interne verwijzing SITES-22457).
> Er wordt een oplossing voor de langere termijn beschikbaar gesteld die ervoor zorgt dat nieuwe opstartversies worden gemaakt met alle juiste configuraties. Tot die tijd is er ook een interne patchrelease beschikbaar op aanvraag.

#### Forms

1. Als een gebruiker de nieuwste AEM Forms SDK downloadt (`AEM Forms add-on v2024.05.04.00-240400`), kan het batchbestand de Docker-service niet starten. U lost dit probleem als volgt op:
   1. Download de [map](/help/forms/assets/sdk_hotfix.zip).
   1. Extraheer de inhoud uit de gedownloade map en kopieer de `sdk.sh` en `sdk.bat` bestanden.
   1. Bestaande vervangen `sdk.sh` en `sdk.bat` in de SDK van AEM Forms met de nieuwe bestanden.

### Kennisgeving wijzigen {#change-notice-16799}

* Deze versie bevat de volgende nieuwe versies van de productindex:
   * **damAssetLucene-11**
   * **fragmenten-11**

  Aangepaste versies van de vorige indexversies worden automatisch samengevoegd met de nieuwe versie van de productindex. Pas verdere aangepaste updates toe op de samengevoegde versie.

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [de documentatie](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer informatie .

### Verouderde functies en API&#39;s {#deprecated-16799}

Als u wilt weten wat er is vervangen of verwijderd in AEM as a Cloud Service, raadpleegt u [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md).

### Ingesloten technologieën {#embedded-tech-16799}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM | 1 64,0 | [API voor eik 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,25,4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
