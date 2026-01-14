---
title: Nota's van de versie voor 2020.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: '[!DNL Adobe Experience Manager] Opmerkingen bij de release van as a Cloud Service voor 2020.10.0.'
exl-id: ac741744-5b47-47a4-b5af-e1089e92c3f0
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Opmerkingen bij de release van [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] as a Cloud Service 2020.10.0 beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 is 28 oktober 2020.
De volgende release (2020.11.0) vindt plaats op 1 december 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* **[Componenten 2.12.0 van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)**: Adobe Experience Manager as a Cloud Service profiteert van automatische updates aan de recentste versie van de Componenten van de Kern. Versie 2.12.0 bevat de meest recente verbeteringen die de gemeenschap heeft aangebracht. De verbeteringen omvatten [&#x200B; een nieuwe POST vormmanager;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) de capaciteit om douane CSS, JavaScript, en meta-gegevens [&#x200B; markeringen via context bewuste configuratie te omvatten;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) en a [`DataLayerBuilder` &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) nut om de integratie van de Laag van de Gegevens van Adobe in douanecomponenten te vereenvoudigen. Zie de [&#x200B; lijst van veranderingen &#x200B;](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) in 2.12.0.

* **[Archetype 24 van het Project &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)**: De geadviseerde stichting om een nieuw project van Experience Manager te beginnen werd beter. Het omvat nu de nieuwe [&#x200B; Laag van Gegevens van de Cliënt van Adobe &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html), optie [&#x200B; plaats in AMP &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) leveren, en nieuwe [&#x200B; uitbreidingspunten om project CSS/JS &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) toe te voegen.

* **[Omslagen ContextHub](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Mogelijkheid om publieksomslagen tot stand te brengen om, publiekssegmenten gemakkelijk te organiseren te vinden en te selecteren voor aanbieding ContextHub richtend mogelijkheden.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

* **[!DNL Adobe AI]Slimme tags toepassen op video** : DMM-gebruikers kunnen door het toepassen van AI-modellen om video-inhoud te analyseren op object- en actiespecifieke tags, minder tijd besteden aan het toevoegen van tags en meer tijd aan het gebruik van de belichte, rijke informatie. Op uw beurt levert u de juiste ervaring aan klanten. Zie [&#x200B; Slimme activa van de markeringsvideo &#x200B;](/help/assets/smart-tags-for-videos.md).

* **de verhogingen van Brand Portal**: De volgende nieuwe eigenschappen en meer zijn beschikbaar in [!DNL Brand Portal]. Voor details, zie [[!DNL Brand Portal]  versienota&#39;s &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [&#x200B; Verbeterde downloadervaring &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) voor vereenvoudigde, snelle downloads. De extra downloadconfiguraties kunnen door beheerders worden gevormd om een ervaring aan te bieden die de behoeften van de gebruikers en de ondernemingen aanpast.
   * Één-klik navigatie aan Dossiers, [&#x200B; Inzamelingen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/share/brand-portal-share-collection.html), en de Gedeelde Verbindingen zijn nu mogelijk van om het even welke pagina.
   * De gebruikers kunnen [&#x200B; specifieke vertoningen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) nu selecteren en downloaden. De nieuwe optie voor het downloaden van vertoningen is beschikbaar in het deelvenster Uitvoeringen op de pagina met elementdetails.
   * Een onderbreking van 15 minuten voor gastgebruikerszittingen verzekert een betere ervaring aan alle gezamenlijke gebruikers.

* **[!DNL Adobe Asset Link]versie 2.1**: Een nieuwe versie van [&#x200B; de uitbreiding van de Verbinding van de Activa van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) voor [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign] is beschikbaar. De toepassing voegt compatibiliteit met de nieuwste [!DNL Adobe Creative Cloud] -toepassingen toe met versie 2021, die in oktober 2020 is uitgebracht.

* **[!DNL Assets]WebP-bestandsondersteuning** : [!DNL Assets] as a Cloud Service ondersteunt nu de WebP-afbeeldingsindeling. WebP is een nieuwe afbeeldingsindeling die door Google wordt gemaakt. Afbeeldingen in de WebP-bestandsindeling zijn visueel niet te onderscheiden van JPG- of PNG-bestanden en de bestanden zijn veel kleiner. Door de bestandsgrootte van elementen te verlagen, worden de pagina&#39;s sneller geladen en krijgen de makers van inhoud een snellere webervaring. Zie hoe te om WebP in [&#x200B; te gebruiken creeer verwerkingsprofiel &#x200B;](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## [!DNL Adobe Experience Manager Forms] as a Cloud Service {#forms-oct-2021}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics voor Aanpassings Forms**: U kunt gedrag van zowel het programma geopende als niet het programma geopende (anonieme) nu vangen en volgen als Adobe Analytics voor Aanpassings Forms om gebruikersinzicht te verzamelen. Zakelijke gebruikers kunnen op basis van de verzamelde inzichten beslissingen nemen over aangepaste formulierinhoud, lay-out en stijl.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms-oct-2021}

* **externaliseer de gegevens van het Werkschema van AEM voor veilige verwerking**: U kunt de variabelen van het werkschema van AEM opslaan in-proces die de gevoelige elementen van Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. Tijdens de verwerking van de workflow worden de gegevens die in workflowvariabelen zijn opgeslagen, niet in de gegevensopslagruimte van AEM bewaard. Het wordt opgehaald op bestelling van de klant-beheerde bewaarplaats.

### Beta-functies van [!DNL Forms]  {#sep-what-is-new-forms-oct-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [&#x200B; Communicatie APIs &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) hulp u een malplaatje en de gegevens van XML combineert om documenten in diverse formaten te produceren. Met deze service kunt u documenten in synchrone modus en in batchmodus genereren.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Release CIF Venia Reference Site - 2020.10.2 die de nieuwste versie van CIF Core Components v1.4.0 bevat. Zie [&#x200B; de Plaats van de Verwijzing van CIF Venia &#x200B;](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) voor meer details.

* Uitgebrachte CIF Core Components v1.4.0. Zie [&#x200B; Componenten van de Kern van CIF &#x200B;](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) voor meer details.

### Opgeloste problemen {#bug-fixes-commerce}

* GraphQL-aanvragen die zich in de productconsole bevonden en Pickers werden uitgevoerd via HTTP POST. Deze kwestie is opgelost om ervoor te zorgen dat de cliënt van Apollo GraphQL het plaatsen in de cliëntOSGi van GraphQL configuratie respecteert om de verzoeken van GET te steunen indien gevormd.

* De configuratiegebruikersinterface van CIF Cloud waarin de knoppen &quot;Opslaan en sluiten&quot; worden weergegeven voor configuraties in /lib en /apps/. Maar deze interfaces zijn read-only vandaar UI vast om &quot;dicht&quot;knoop slechts te tonen.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De Releasedatum voor Cloud Manager in Experience Manager as a Cloud Service 2020.10.0 is 2 oktober 2020.

### Nieuwe functies in [!DNL Cloud Manager] {#what-is-new-cm}

* De pagina Omgevingen is opnieuw ontworpen.

* Gesamberde omgevingen hebben nu een aparte status in Cloud Manager wanneer ze gehiberneerd zijn.

* De Cloud Manager &quot;build container&quot; ondersteunt nu het compileren van projecten met behulp van Java™ 8 of Java™ 11. Ondersteuning voor Java™ 11 wordt geleverd door het Maven-toolketensysteem.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De kaart van het Milieu op de pagina van het Overzicht maakt nu een lijst van maximaal drie milieu&#39;s. De gebruikers kunnen **selecteren tonen Al** knoop om aan de Samenvattende pagina van het Milieu te navigeren om een lijst met een volledige lijst van milieu&#39;s te bekijken.
Zie [&#x200B; het Bekijken Milieu &#x200B;](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer details.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* De link van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de Developer Console rechtstreeks vanuit Cloud Manager gaf niet de optie weer om de omgeving van een Sandbox-programma te dehiberneren of te hiberneren.

* De knoppen Annuleren en Opslaan op de pagina Bewerken zonder productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Omgevingen worden soms de publicatiesegmenten en de Dispatcher-segmenten weergegeven wanneer er geen aanwezig was.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie {de Instanties van het Werkschema van 0} Onderzoek [.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html)

## Inhoud overbrengen {#content-transfer-tool}

Leer meer over wat nieuw is en de updates voor [&#x200B; het Hulpmiddel van de Overdracht van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Versie v1.1.12.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Opgeloste problemen {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat die gedeeltelijk vergelijkbare bestandsnamen bevatten.
