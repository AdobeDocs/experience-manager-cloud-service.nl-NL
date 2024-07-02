---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3a4dd9f1d769a9c9da12fdd8febfef481112d18c
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 16799 {#release-16799}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 16799 samengevat, die op 18 juni 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16544.

2024.6.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie .

### Verbeteringen {#enhancements-16799}

* ASSETS-31977: verbeterde bewerkingen voor het verplaatsen, kopiëren en verwijderen van bedrijfsmiddelen.
* ASSETS-33618: Auto-transcriptie en vertaalmogelijkheden voor video&#39;s in Dynamic Media.
* ASSETS-35185: De Actie van de goedkeuring voor ContentHub en DM en voegt eigenschappen aan damAssetLucene eigenschappen toe.
* ASSETS-35533: Voeg DRM- en CAI-eigenschappen toe aan damAssetLucene-index.
* ASSETS-37280: Opeenvolgende taakafhandeling voor vertaling wanneer bronondertitel (vtt) nog steeds wordt verwerkt.
* ASSETS-37559: gebeurtenis Improved asset delete.
* ASSETS-37723: Gebeurtenis gepubliceerd voor het implementeren van middelen.
* ASSETS-37724: Implementeer de gebeurtenis Asset unpublished.
* ASSETS-38614: Verbeteringen in de gebruikersinterface voor het delen van koppelingen.
* ASSETS-39601: Pas validatieregex automatisch toe op de naam van de Asset Livecopy.
* ASSETS-39454: upgrade naar viewers 2024.5.0 in QuickStart.
* CNTBF-184: Onderliggende steunpaden `/conf` in Content Backflow.

### Opgeloste problemen {#fixed-issues-16799}

* ASSETS-37335: Als u het deelvenster Zoeken in filter bewerkt, worden alle vakken uitgeschakeld.
* ASSETS-38069: AEM DAM PDF Voorvertoning probleem bij selectie van tijdlijnfilter.
* ASSETS-38215: Adobe Stock-licentieknop wordt in AEM as a Cloud Service weergegeven voor een Enterprise-abonnement.
* ASSETS-38578: Onjuiste hyperlinks in Assets Link Share Report.
* ASSETS-38678: De weergave-instellingen zijn verbroken in Gegevens verzameling.
* ASSETS-39071: Voor het web geoptimaliseerde levering kan een uitzondering genereren als het oorspronkelijke renditiemimetype null is.
* ASSETS-39316: Sorteren op naam werkt niet in Verzamelingen.
* ASSETS-39377: Bulkimport van OneDrive kan mislukken bij het ontvangen van backpressure van de externe API.
* ASSETS-39428: Problemen met het renderen in de gebruikersinterface van Copyright Management.
* CQ-4357150: Guava in cq-content-sync-bundel.
* GRANITE-52573: Verzoeken met een dubbele slash `//` worden geweigerd met statuscode 400.
* SCRNS-4194: Verwijder afhankelijkheid van Google Guava API&#39;s.
* SCRNS-4360: Ontbrekende Manage Publication &amp; Quick Publish Button voor gebruikers die geen beheerder zijn in Content Provider voor kanalen.
* SCRNS-4323: Verberg/maak lanceringen van screens.html onbruikbaar.

#### Forms

* FORMS-14844: Adaptive Forms staat het verzenden van formulieren toe, ondanks onvoldoende reCAPTCHA-verificatie.
* FORMS-14984: Forms met CAPTCHA slaat validatie over als &quot;submitMetaData&quot; niet aanwezig is in de verzonden gegevens.
* FORMS-14477: De opties &#39;Is na&#39; en &#39;Is voor&#39; in de regeleditor functioneren niet naar behoren in de datumkiezervalidatie.
* FORMS-14019: De functie &quot;Invoke Service&quot; van de redacteur van de Regel werkt niet in Universele Redacteur.
* FORMS-14336: Als er geen formulierveld is geselecteerd, wordt de editor geopend met focus op het gehele formulierelement.
* FORMS-15061: De cirkel van de Lader blijft eindeloos bij het gebruiken aanhalen van de dienstoptie in de regelredacteur voortzetten.

### Bekende problemen {#known-issues-16799}

>[!NOTE]
> AEM de Techniek heeft een regressie voor de functionaliteit van Lanceringen geïdentificeerd die huidige AEM versies die met 16461 beginnen beïnvloedt. Vanwege deze regressie worden nieuwe opstarters (gemaakt nadat nieuwe releases zijn toegepast) die niet-diepe pagina&#39;s bevatten, niet goed gepromoveerd omdat er configuraties ontbreken.
> Als uw milieu&#39;s worden beïnvloed, is een shell manuscript om ontbrekende configuraties te identificeren en bij te werken beschikbaar door klantensteun (interne verwijzing SITES-22457).
> Er wordt een oplossing voor de langere termijn beschikbaar gesteld die ervoor zorgt dat nieuwe opstartversies worden gemaakt met alle juiste configuraties. Tot die tijd is er ook een interne patchrelease beschikbaar op aanvraag.

#### Forms

* Wanneer u de AEM SDK installeert en toevoegt `AEM Forms add-on v2024.05.04.00-240400`, kan de Docker-service niet worden gestart. De dockerservice is vereist om Document of Record te genereren in een lokale ontwikkelomgeving. U kunt als volgt het probleem verhelpen:
   1. Download de [hotfix](/help/forms/assets/sdk_hotfix.zip). Wanneer u de hotfix downloadt, wordt een `.zip` wordt gedownload.
   1. Pak de gedownloade hotfix uit naar een map.
   1. De map vervangen `sdk.sh` en `sdk.bat` bestanden met nieuwere bestanden in de map die zijn uitgepakt in Stap 2.

### Kennisgeving wijzigen {#change-notice-16799}

* Deze versie bevat de volgende nieuwe versies van de productindex:
   * **damAssetLucene-11**
   * **fragmenten-11**

  Aangepaste versies van de vorige indexversies worden automatisch samengevoegd met de nieuwe versie van de productindex. Pas verdere aangepaste updates toe op de samengevoegde versie.

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [de documentatie](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer informatie .

### Verouderde functies en API&#39;s {#deprecated-16799}

Als u wilt weten wat in AEM as a Cloud Service is vervangen of verwijderd, raadpleegt u [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md).

### Ingesloten technologieën {#embedded-tech-16799}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 64,0 | [Oak API 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,25,4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
