---
title: Release-aantekeningen voor de release 2020.10.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van de Cloud Service voor 2020.10.0.'
translation-type: tm+mt
source-git-commit: 65752c7c51538de27aa2b21695e8eb6c6695a5f5
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---


# Opmerkingen bij de release [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release [!DNL Experience Manager] als Cloud Service 2020.10.0 beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2020.10.0 is 28 oktober 2020.
De volgende release (2020.11.0) vindt plaats op 1 december 2020.

## [!DNL Adobe Experience Manager Sites] als Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

<!-- add when release done: * **Core Components 2.12.0**: With Core Components being on auto-update, benefit from the latest improvements contributed by the community. See list of changes since 2.11.1: Release Notes -->

* **Projectarchetype 24**: De geadviseerde stichting om een nieuw AEM project te beginnen werd beter, nu met inbegrip van de nieuwe Laag van Gegevens van de Cliënt van Adobe, optie om plaats in AMP en nieuwe uitbreidingspunten te leveren om project CSS/JS toe te voegen.

* **ContextHub-mappen**: Capaciteit om publieksomslagen tot stand te brengen om publiekssegmenten gemakkelijk te organiseren, te vinden en te selecteren voor de aanbieding ContextHub richtend mogelijkheden.

## [!DNL Adobe Experience Manager Assets] als Cloud Service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* **[!DNL Adobe Sensei]Slimme tags** voor gemotoriseerde video: Door gebruik te maken van AI-modellen voor het analyseren van video-inhoud voor object- en actiespecifieke tags, kunnen DAM-gebruikers minder tijd besteden aan het toevoegen van tags en meer tijd besteden aan het gebruik van de rijke informatie die wordt weergegeven om klanten de juiste ervaring te bieden. Zie [Slimme tags toepassen op video-elementen](/help/assets/smart-tags-video-assets.md).

* **Verbeteringen** merkportal: De volgende nieuwe functies en meer zijn beschikbaar in [!DNL Brand Portal]. Zie Opmerkingen bij de [[!DNL Brand Portal] release voor meer informatie](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Verbeterde downloadervaring](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) voor vereenvoudigde, snelle downloads. De extra downloadconfiguraties kunnen door beheerders worden gevormd om een ervaring aan te bieden die de behoeften van de gebruikers en de ondernemingen aanpast.
   * Een-klik navigatie aan Dossiers, [Inzamelingen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html), en Gedeelde Verbindingen is nu mogelijk van om het even welke pagina.
   * Gebruikers kunnen nu specifieke uitvoeringen [selecteren en downloaden](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) . De nieuwe optie voor het downloaden van vertoningen is beschikbaar in het deelvenster Uitvoeringen op de pagina met elementdetails.
   * Een onderbreking van 15 minuten voor gastgebruikerszittingen verzekert een betere ervaring aan alle gezamenlijke gebruikers.

* **[!DNL Adobe Asset Link]versie 2.1**: Een nieuwe versie van de uitbreiding van de Verbinding [van Activa van](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) Adobe voor [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign] is beschikbaar. Het voegt compatibiliteit met de meest recente [!DNL Adobe Creative Cloud] toepassingen toe met versie 2021, die in oktober 2020 is uitgebracht.

* **[!DNL Assets]WebP-bestandsondersteuning**: [!DNL Assets] als Cloud Service nu de WebP-afbeeldingsindeling ondersteunt. WebP is een nieuwe afbeeldingsindeling die door Google is gemaakt. Afbeeldingen in de WebP-bestandsindeling zijn visueel niet te onderscheiden van JPG- of PNG-bestanden en de bestanden zijn veel kleiner. Door de bestandsgrootte van elementen te verlagen, worden de pagina&#39;s sneller geladen en krijgen de makers van inhoud een snellere webervaring. Zie [Een standaardverwerkingsprofiel](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile)maken.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgebrachte CIF Venia Reference Site - 2020.10.2 die de snelste versie van de CIF Core Components v1.4.0 omvat. Raadpleeg de [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) voor meer informatie.

* Uitgebrachte CIF Core Components v1.4.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) voor meer informatie.

### Bug Fixes {#bug-fixes-commerce}

* GraphQL-aanvragen in de productconsole en de pakjes zijn gedaan via HTTP-POST. Dit is bevestigd om ervoor te zorgen dat de cliënt van Apollo GraphQL het plaatsen in de cliëntOSGi van GraphQL configuratie respecteert om verzoeken van GET te steunen indien gevormd.

* De configuratiegebruikersinterface van de CIF-cloud gaf de knoppen &quot;Opslaan en sluiten&quot; weer voor configuraties in /lib en /apps/. Maar dit zijn alleen-lezen; de gebruikersinterface is daarom alleen geschikt voor het weergeven van de knop Sluiten.

## Cloud Manager {#cloud-manager}

* De pagina Omgevingen is opnieuw ontworpen.

* In gedownneerde omgevingen wordt nu een aparte status weergegeven in Cloud Manager wanneer deze worden gehiberneerd.

* De buildcontainer van Cloud Manager ondersteunt nu het compileren van projecten met behulp van Java 8 of Java 11. Ondersteuning voor Java 11 wordt geleverd door het Maven-toolketensysteem.

* Het aantal omgevingsvariabelen per omgeving is verhoogd tot 200.

* De kaart van het Milieu op de pagina van het Overzicht zal nu tot drie milieu&#39;s een lijst maken. Gebruikers kunnen de knop Alles **** tonen selecteren om naar de overzichtspagina Omgeving te navigeren en een tabel met een volledige lijst met omgevingen weer te geven.
Zie [Weergaveomgeving](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie.

### Bug Fixes {#bug-fixes-cloud-manager}

* De koppeling van Cloud Manager naar de Developer Console was onjuist actief voordat omgevingen volledig werden gemaakt.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager gaf de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer.

* De knoppen Annuleren en Opslaan op de pagina Bewerken zonder productiepijplijn zijn niet altijd zichtbaar.

* Bepaalde fouten in het proces van de codekwaliteit kunnen ertoe leiden dat het logbestand niet correct wordt gegenereerd.

* Bij het maken van een nieuw programma retourneert de voorgestelde naam soms een duplicaat van een bestaande programmanaam.

* Sommige logboeken van grote pijpleidingsstappen konden niet constant door het gebruikersinterface worden gedownload.

* De validatie van omgevingsnamen had een off-by-one fout.

* Op de pagina Milieu&#39;s worden soms publicatie- en verzendingssegmenten weergegeven wanneer er geen aanwezig was.


## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie [Workflowinstanties](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html)zoeken.

## De tool Content Transfer {#content-transfer-tool}

Ga als volgt te werk om te leren wat nieuw is en de updates voor [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Bug Fixes {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat met gedeeltelijk vergelijkbare bestandsnamen. Dit is opgelost.
