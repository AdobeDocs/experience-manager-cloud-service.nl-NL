---
title: Release-aantekeningen voor 2020.10.0-release van [!DNL Adobe Experience Manager] als Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van de Cloud Service voor 2020.10.0.'
translation-type: tm+mt
source-git-commit: 13774cc8684166c98f85bf4096d2c7de8d257746
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.10.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] beschreven als een Cloud Service 2020.10.0.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2020.10.0 is 28 oktober 2020.
De volgende release (2020.11.0) vindt plaats op 1 december 2020.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

### Nieuw in [!DNL Sites] {#what-is-new-sites}

* **[Core Components 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)**: AEM als Cloud Service profiteert van automatische updates van de nieuwste versie van de Core Components. Versie 2.12.0 omvat de recentste verbeteringen die door de gemeenschap zoals [een nieuwe POST vormmanager worden bijgedragen;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) de capaciteit om douaneCSS, Javascript, en meta-gegevens [markeringen via contextbewuste configuratie te omvatten;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) en een [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) nut om de integratie van de Laag van de Gegevens van Adobe in douanecomponenten te vereenvoudigen. Zie de [lijst met wijzigingen](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) in 2.12.0.

* **[Projectarchetype 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)**: De geadviseerde stichting om een nieuw AEM project te beginnen werd beter, nu met inbegrip van de nieuwe Laag [ van de Gegevens van de Cliënt van ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html)Adobe, optie om plaats in AMP te  [leveren,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) en nieuwe  [uitbreidingspunten om project CSS/JS toe te voegen.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub-mappen](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Capaciteit om publieksomslagen tot stand te brengen om publiekssegmenten gemakkelijk te organiseren, te vinden en te selecteren voor de aanbieding ContextHub richtend mogelijkheden.

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

* **[!DNL Adobe Sensei]Slimme tags** voor gemotoriseerde video: Door gebruik te maken van AI-modellen voor het analyseren van video-inhoud voor object- en actiespecifieke tags, kunnen DAM-gebruikers minder tijd besteden aan het toevoegen van tags en meer tijd besteden aan het gebruik van de rijke informatie die wordt weergegeven om klanten de juiste ervaring te bieden. Zie [Slimme-tagvideo-elementen](/help/assets/smart-tags-video-assets.md).

* **Verbeteringen** merkportal: De volgende nieuwe functies en meer zijn beschikbaar in  [!DNL Brand Portal]. Zie [[!DNL Brand Portal] Opmerkingen bij de release](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html) voor meer informatie.

   * [Verbeterde downloadervaring ](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) voor vereenvoudigde, snelle downloads. De extra downloadconfiguraties kunnen door beheerders worden gevormd om een ervaring aan te bieden die de behoeften van de gebruikers en de ondernemingen aanpast.
   * Een-klik navigatie aan Dossiers, [Inzamelingen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html), en Gedeelde Verbindingen is nu mogelijk van om het even welke pagina.
   * Gebruikers kunnen nu [specifieke uitvoeringen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) selecteren en downloaden. De nieuwe optie voor het downloaden van vertoningen is beschikbaar in het deelvenster Uitvoeringen op de pagina met elementdetails.
   * Een onderbreking van 15 minuten voor gastgebruikerszittingen verzekert een betere ervaring aan alle gezamenlijke gebruikers.

* **[!DNL Adobe Asset Link]versie 2.1**: Een nieuwe versie van  [Adobe Asset ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) Linkextension voor  [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator]en  [!DNL Adobe InDesign] is beschikbaar. Het voegt verenigbaarheid met de recentste [!DNL Adobe Creative Cloud] toepassingen met versie 2021 toe, die in Oktober 2020 wordt vrijgegeven.

* **[!DNL Assets]WebP-bestandsondersteuning**:  [!DNL Assets] als Cloud Service nu de WebP-afbeeldingsindeling ondersteunt. WebP is een nieuwe afbeeldingsindeling die door Google is gemaakt. Afbeeldingen in de WebP-bestandsindeling zijn visueel niet te onderscheiden van JPG- of PNG-bestanden en de bestanden zijn veel kleiner. Door de bestandsgrootte van elementen te verlagen, worden de pagina&#39;s sneller geladen en krijgen de makers van inhoud een snellere webervaring. Zie hoe te om WebP in [creeer verwerkingsprofiel](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile) te gebruiken.

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgebrachte CIF Venia Reference Site - 2020.10.2 die de snelste versie van de CIF Core Components v1.4.0 omvat. Raadpleeg [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) voor meer informatie.

* Uitgebrachte CIF Core Components v1.4.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) voor meer informatie.

### Opgeloste problemen {#bug-fixes-commerce}

* GraphQL-aanvragen in de productconsole en de pakjes zijn gedaan via HTTP-POST. Dit is bevestigd om ervoor te zorgen dat de cliënt van Apollo GraphQL het plaatsen in de cliëntOSGi van GraphQL configuratie respecteert om verzoeken van GET te steunen indien gevormd.

* De configuratiegebruikersinterface van de CIF-cloud gaf de knoppen &quot;Opslaan en sluiten&quot; weer voor configuraties in /lib en /apps/. Maar dit zijn alleen-lezen; de gebruikersinterface is daarom alleen geschikt voor het weergeven van de knop Sluiten.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.10.0 is 20 oktober 2020.

### Nieuw in [!DNL Cloud Manager] {#what-is-new-cm}

* De pagina Omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* De buildcontainer van Cloud Manager ondersteunt nu het compileren van projecten met behulp van Java 8 of Java 11. Ondersteuning voor Java 11 wordt geleverd door het Maven-toolketensysteem.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De kaart van het Milieu op de pagina van het Overzicht zal nu tot drie milieu&#39;s een lijst maken. Gebruikers kunnen de knop **Alles weergeven** selecteren om naar de overzichtspagina Omgeving te navigeren en een tabel met een volledige lijst met omgevingen weer te geven.
Zie [Omgeving weergeven](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De knoppen Annuleren en Opslaan op de pagina Bewerken zonder productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.

## Adobe Experience Manager als Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie [Workflowinstanties zoeken](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## De tool Content Transfer {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Opgeloste problemen {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat met gedeeltelijk vergelijkbare bestandsnamen. Dit is opgelost.
