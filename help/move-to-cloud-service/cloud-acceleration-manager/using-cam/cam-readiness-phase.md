---
title: Gereedheidsfase in Cloud Acceleration Manager
description: Deze pagina bevat een overzicht van de gereedheidsfase in Cloud Acceleration Manager.
exl-id: 91a13cae-4934-42e8-9538-896fd72f5acb
source-git-commit: 399698d512252b0a683f83a06ffbc71cd606ed72
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 4%

---

# Gereedheidsfase in Cloud Acceleration Manager {#readiness-phase-cam}

Nadat u een project hebt gemaakt in Cloud Acceleration Manager, kunt u nu de evaluatie starten van de huidige AEM-implementatie in de gereedheidsfase.

De gereedheidsfase omvat:

* [Analyse van best practices](#best-practices-analysis)
* [Planning en installatie](#planning-setup)

Ga als volgt te werk om naar de gereedheidsfase te navigeren:

1. Klik op uw projectkaart om de bestemmingspagina van het project te openen.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. Ga naar de **Gereedheid** in de onderstaande afbeelding.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Zie Een project maken en beheren in de Cloud Acceleration Manager voor meer informatie.

## De kaart van de Analyse van Beste praktijken gebruiken {#best-practices-analysis}

Volg de stappen hieronder om de kaart van de Analyse van Beste praktijken te gebruiken:

1. Klik op de knop **Controleren** van de knop **Analyse van best practices** kaart.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. Voer de volgende stappen uit om BPA (Best Practices Analyzer) te downloaden.

   >[!NOTE]
   >Om een effect op zaken kritieke instanties te vermijden, adviseert men dat u BPA op een milieu van de Auteur in werking stelt dat zo dicht mogelijk aan de milieu van de Productie op de gebieden van aanpassingen, configuraties, inhoud en gebruikerstoepassingen is. CRA kan ook worden uitgevoerd op een kloon van de auteurlaag van de productieomgeving.

   1. Navigeren naar [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) de Analysator van Beste praktijken als zip dossier openen en downloaden.

      >[!NOTE]
      >Controleren [Analysator van best practices gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations) om te leren hoe u BPA kunt uitvoeren.

   1. Het rapport exporteren in CSV-indeling

1. Klikken op **Nieuw rapport uploaden** om BPA- rapport in CAM te uploaden.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Rapport kan niet worden geüpload als u in de Incognito-modus van de browser werkt.

1. Zodra u een nieuw rapport hebt geüpload, zult u het rapport van de Analyse van Beste praktijken zien.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Het dashboard van de Analyse van Beste praktijken van het overzicht en onderzoek in CAM. Zie de onderstaande sectie [Rapport Analyse van beste praktijken](#analysis-report) voor meer informatie .

   >[!NOTE]
   >Als u een nieuw rapport uploadt, worden alle beoordelingen opnieuw ingesteld.

### Afdrukvoorbeeld gebruiken {#print-preview-cam}

U kunt de optie voor afdrukvoorvertoningen selecteren in Cloud Acceleration Manager om de rapporten af te drukken of om het rapport af te drukken naar een PDF-indeling, zodat u het gemakkelijk kunt delen.

Voer de onderstaande stappen uit:

1. Klikken op **Afdrukvoorbeeld** zoals hieronder weergegeven.

   ![afbeelding](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Klikken op **Afdrukvoorbeeld** Hiermee opent u een nieuw tabblad met het rapport dat in een afdrukbare voorvertoning wordt weergegeven. Klikken op **Afdrukken** om het rapport af te drukken naar een PDF-indeling.

   >[!IMPORTANT]
   >* De optie **Opslaan als PDF** wordt aanbevolen en ondersteund voor de bovenstaande functionaliteit.
   >* Als de knop Afdrukken van de browser wordt gebruikt, wordt slechts één pagina afgedrukt.


   ![afbeelding](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview2.png)

### Trendline weergeven gebruiken {#trendline-view-cam}

Wanneer u meer dan één rapport van de Analysator van Beste praktijken (BPA) in een Project uploadt, kunt u selecteren **Trendline weergeven** optie om resultaten van de oude BPA-rapporten te bekijken en te vergelijken.

Voer de onderstaande stappen uit om rapporten van de optie Trendline weer te geven:

>[!NOTE]
>Wanneer u meer dan één BPA- rapport in een Project uploadt, zult u zien **...** pictogram.

1. Navigeer naar uw project en klik op **Controleren** van de **Analyse van best practices** in de **Gereedheid** fase.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klik op de knop **...** om de vervolgkeuzelijst weer te geven.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >Het rapport dat wordt weergegeven in het dialoogvenster **Trendline-rapportscherm** is altijd de datum van het recente verslag.

1. Klikken op **Trendline weergeven**, zoals weergegeven in onderstaande afbeelding.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klikken op **Trendline weergeven** Hiermee opent u de trendlijnweergave van het rapport, zoals in de onderstaande afbeelding wordt getoond.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view3.png)

   >[!NOTE]
   >Het Trendline Rapport toont de resultaten van de historische BPA- rapporten in een grafische vertegenwoordiging.
   >
   >Er worden twee grafieken weergegeven met de trend van de:
   >1. **Trend van bevindingen rapport**
   >1. **Aangepaste componenten en sjabloontrend**

   >
   >U kunt de grafische weergave toevoegen of wijzigen via de vervolgkeuzelijst, zoals in de onderstaande afbeelding wordt getoond:
   >![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view4.png)

#### Het Trendline-rapport verwijderen {#delete-trendline}

Voer de onderstaande stappen uit om een rapport uit de weergave Trendline te verwijderen:

1. Navigeer naar uw project en klik op **Controleren** van de **Analyse van best practices** in de **Gereedheid** fase.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klik op de knop **...** om de vervolgkeuzelijst weer te geven.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view1.png)

1. Klikken op **Trendline weergeven**, zoals weergegeven in onderstaande afbeelding.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klik op het verwijderpictogram in het pop-upmenu **Trendline-rapport** scherm.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view5.png)

1. Klikken op **Verwijderen** om de schrapping te bevestigen.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/trendline-view6.png)


### Rapport Analyse van beste praktijken {#analysis-report}

Onderzoek de volgende kaarten beschikbaar in de pagina van het Rapport van de Analyse van Beste praktijken:

![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Met elke kaart kunt u:
>* klik op elke kaart om het bijbehorende tabblad te openen
>* bladwijzer alle rapportlusjes (met inbegrip van het filtreren) voor het delen of toekomstige herwinning
>* gebruik het detailspictogram om de details van elk rapport te bekijken vinden


#### Rapporteigenschappen {#report-properties}

De **Rapporteigenschappen** De kaart biedt informatie over rapporteigenschappen zoals rapportdatum, duur, filters, uploaddatum en Adobe Experience Manager (AEM)-gegevens.

![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-properties.png)

#### Overzicht van rapporten {#report-overview}

Dit **Overzicht van rapporten** kaart geeft de bevindingen en ernst van het rapport weer die van toepassing zijn bij het beoordelen van de gereedheid om over te gaan naar AEM as a Cloud Service, zoals in onderstaande afbeelding wordt getoond.

![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview.png)

Als u op dit rapport klikt, wordt het **Rapport** tab.

![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview2.png)

U kunt het rapport filteren op basis van belang, subtype of aantal.

![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Zie [Het rapport met de analyse van best practices interpreteren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en) voor meer informatie over de categorieën bevindingen en de belangrijkste niveaus.

#### Evaluatie van best practices {#best-practices-assessment}

De optie Beoordeling van Beste praktijken verstrekt een beoordeling van uw huidige AEM instantie en verstrekt raad over volgende stappen om AEM beste praktijken goed te keuren. U kunt de volgende informatie bekijken vanaf dit tabblad:

* Overzicht AEM
* Aangepaste componenten en sjablonen
* Aanvullende bevindingen
* Langzame query&#39;s
* Onderhoudstaken

#### Complexiteit-evaluatie van migratie {#migration-complexity-assessment}

De optie voor de beoordeling van de complexiteit van migratie biedt een beoordeling van de complexiteit om de bestaande AEM te migreren naar AEM as a Cloud Service.

U kunt de volgende informatie bekijken vanaf dit tabblad:

* Overzicht AEM
* Beoordeling
* Overwegingen bij migratie van inhoud

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Planning en de Kaart van de Opstelling gebruiken {#planning-setup}

Volg deze sectie om de de activiteitenkaart van de Planning en van de Opstelling te onderzoeken.

1. Klik op de knop **Weergave** van de knop **Planning en installatie** kaart. Deze kaart biedt alle relevante inhoud die u helpt bij het plannen en instellen van uw AEM migratie.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-view.png)

1. Een inhoudscarrousel geeft alle relevante informatie weer voor deze fase van de migratiereis.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

## Volgende functies {#whats-next}

Als u eenmaal hebt geleerd hoe u zich kunt aanmelden bij Cloud Acceleration Manager en hoe u een project kunt maken, kunt u nu verdergaan met het evalueren van de volgende stap in het dialoogvenster [Implementatiefase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en).
