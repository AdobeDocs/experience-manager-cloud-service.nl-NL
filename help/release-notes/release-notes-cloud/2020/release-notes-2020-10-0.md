---
title: Opmerkingen bij de release 2020.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2020.10.0."
exl-id: ac741744-5b47-47a4-b5af-e1089e92c3f0
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Experience Manager] as a Cloud Service 2020.10.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 is 28 oktober 2020.
De volgende release (2020.11.0) vindt plaats op 1 december 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* **[Core Components 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)**: Adobe Experience Manager as a Cloud Service profiteert van automatische updates van de nieuwste versie van de Core Components. Versie 2.12.0 bevat de meest recente verbeteringen die de gemeenschap heeft aangebracht. Tot de verbeteringen behoren [een nieuwe POST-formulierhandler;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) de mogelijkheid om aangepaste CSS, JavaScript en metagegevens op te nemen [tags via contextbewuste configuratie;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) en [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) nut om de integratie van de Laag van Gegevens van de Adobe in douanecomponenten te vereenvoudigen. Zie de [lijst met wijzigingen](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) in 2.12.0.

* **[Projectarchetype 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)**: De aanbevolen basis voor het starten van een nieuw Experience Manager project werd beter. Het bevat nu de nieuwe [Gegevenslaag client-Adobe](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html), optie om [site in AMP leveren;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) en nieuwe [extensiepunten om project-CSS/JS toe te voegen.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub-mappen](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Mogelijkheid om publieksomslagen tot stand te brengen om, publiekssegmenten gemakkelijk te organiseren te vinden en te selecteren voor aanbieding ContextHub richtend mogelijkheden.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

* **[!DNL Adobe Sensei]Slimme tags toepassen op gemotoriseerde video**: Door AI-modellen toe te passen om video-inhoud te analyseren op object- en actiespecifieke tags, kunnen DAM-gebruikers minder tijd besteden aan het toevoegen van tags en meer tijd aan het gebruik van de belichte, rijke informatie. Op uw beurt levert u de juiste ervaring aan klanten. Zie [Slimme tag-video-elementen](/help/assets/smart-tags-video-assets.md).

* **Verbeteringen voor Brand Portal**: De volgende nieuwe functies en meer zijn beschikbaar in [!DNL Brand Portal]. Zie voor meer informatie [[!DNL Brand Portal] releaseopmerkingen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Verbeterde downloadervaring](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) voor vereenvoudigde, snelle downloads. De extra downloadconfiguraties kunnen door beheerders worden gevormd om een ervaring aan te bieden die de behoeften van de gebruikers en de ondernemingen aanpast.
   * One-click navigation to Files, [Verzamelingen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/share/brand-portal-share-collection.html)en Gedeelde koppelingen zijn nu mogelijk vanaf elke pagina.
   * Gebruikers kunnen [specifieke vertoningen selecteren en downloaden](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) nu. De nieuwe optie voor het downloaden van vertoningen is beschikbaar in het deelvenster Uitvoeringen op de pagina met elementdetails.
   * Een onderbreking van 15 minuten voor gastgebruikerszittingen verzekert een betere ervaring aan alle gezamenlijke gebruikers.

* **[!DNL Adobe Asset Link]versie 2.1**: Een nieuwe versie van [Adobe-itemkoppeling](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) verlenging voor [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign] is beschikbaar. Het voegt verenigbaarheid met recentste toe [!DNL Adobe Creative Cloud] aanvragen met versie 2021, gepubliceerd in oktober 2020.

* **[!DNL Assets]Ondersteuning voor WebP-bestanden**: [!DNL Assets] as a Cloud Service ondersteunt nu de WebP-afbeeldingsindeling. WebP is een nieuwe afbeeldingsindeling die door Google wordt gemaakt. Afbeeldingen in de WebP-bestandsindeling zijn visueel niet te onderscheiden van JPG- of PNG-bestanden en de bestanden zijn veel kleiner. Door de bestandsgrootte van elementen te verlagen, worden de pagina&#39;s sneller geladen en krijgen de makers van inhoud een snellere webervaring. Zie hoe u WebP kunt gebruiken in [verwerkingsprofiel maken](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## [!DNL Adobe Experience Manager Forms] as a Cloud Service {#forms-oct-2021}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analyses voor Adaptive Forms**: U kunt nu het gedrag vastleggen en bijhouden van zowel aangemelde als niet-aangemelde (anonieme) gegevens via Adobe Analytics for Adaptive Forms om gebruikersinzichten te verzamelen. Zakelijke gebruikers kunnen op basis van de verzamelde inzichten beslissingen nemen over aangepaste formulierinhoud, lay-out en stijl.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms-oct-2021}

* **Externe AEM workflowgegevens voor veilige verwerking**: U kunt in-process AEM gegevens van de variabelen van het Werkschema opslaan die de Gevoelige elementen van Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. Tijdens de verwerking van de workflow worden de gegevens die in workflowvariabelen zijn opgeslagen, niet in AEM opslagplaats bewaard. Het wordt opgehaald op bestelling van de klant-beheerde bewaarplaats.

### Bètafuncties van [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) Hiermee kunt u een sjabloon en XML-gegevens combineren om documenten in verschillende indelingen te genereren. Met deze service kunt u documenten in synchrone modus en in batchmodus genereren.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Release CIF Venia Reference Site - 2020.10.2 die de nieuwste versie CIF Core Components versie v1.4.0 bevat. Zie [CIF Venia-referentiegebied](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) voor meer informatie .

* Uitgegeven CIF Core Components v1.4.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) voor meer informatie .

### Opgeloste problemen {#bug-fixes-commerce}

* GraphQL-aanvragen die zich in de productconsole bevonden en Pickers werden uitgevoerd via HTTP-POST. Deze kwestie is opgelost om ervoor te zorgen dat de cliënt van Apollo GraphQL het plaatsen in de cliëntOSGi van GraphQL configuratie respecteert om GET verzoeken te steunen als gevormd.

* CIF Cloud config UI toonde &quot;sparen &amp; dicht&quot;knopen voor vormen in /lib en /apps/. Maar deze interfaces zijn read-only vandaar UI vast om &quot;dicht&quot;knoop slechts te tonen.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in Experience Manager as a Cloud Service 2020.10.0 is 20 oktober 2020.

### Nieuwe functies in [!DNL Cloud Manager] {#what-is-new-cm}

* De pagina Omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* De &quot;build container&quot; van Cloud Manager ondersteunt nu het compileren van projecten met Java™ 8 of Java™ 11. Ondersteuning voor Java™ 11 wordt geleverd door het Maven-toolketensysteem.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De kaart van het Milieu op de pagina van het Overzicht maakt nu een lijst van maximaal drie milieu&#39;s. Gebruikers kunnen de **Alles tonen** om naar de overzichtspagina van het Milieu te navigeren om een lijst met een volledige lijst van milieu&#39;s te bekijken.
Zie [Weergaveomgeving](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie .

### Opgeloste problemen {#bug-fixes-cloud-manager}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De knoppen Annuleren en Opslaan op de pagina Bewerken zonder productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Omgevingen worden soms de publicatiesegmenten en de Dispatcher-segmenten weergegeven wanneer er geen aanwezig was.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie [Workflowinstanties zoeken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## Inhoud overbrengen {#content-transfer-tool}

Meer informatie over nieuwe functies en updates voor [Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Opgeloste problemen {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat die gedeeltelijk vergelijkbare bestandsnamen bevatten.
