---
title: Gereedheidsfase in Cloud Acceleration Manager
description: Deze pagina bevat een overzicht van de gereedheidsfase in Cloud Acceleration Manager.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
source-git-commit: ecf4c06fd290d250c14386b3135250633b26c910
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 3%

---

# Gereedheidsfase in Cloud Acceleration Manager {#readiness-phase-cam}

Nadat u een project hebt gemaakt in Cloud Acceleration Manager, kunt u de huidige Adobe Experience Manager (AEM)-implementatie nu beoordelen in de gereedheidsfase.

De gereedheidsfase omvat:

* [Analyse van best practices](#best-practices-analysis)
* [Planning en installatie](#planning-setup)

Ga als volgt te werk om naar de gereedheidsfase te navigeren:

1. Klik op uw projectkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. Ga op de bestemmingspagina van het project naar de **Gereedheid** in de onderstaande afbeelding.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Zie Een project maken en beheren in Cloud Acceleration Manager voor meer informatie.

## De kaart van de Analyse van Beste praktijken gebruiken {#best-practices-analysis}

1. Klikken **Controleren** van de **Analyse van best practices** kaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. Download Best Practices Analyzer (BPA).

   >[!NOTE]
   >Om een effect op bedrijfskritieke instanties te vermijden, raadt de Adobe u aan BPA in een Auteuromgeving uit te voeren. De omgeving moet zich zo dicht mogelijk bij de productieomgeving bevinden op het gebied van aanpassingen, configuraties, inhoud en gebruikerstoepassingen. Het kan ook worden uitgevoerd op een kloon van de productieauteur-omgeving.

   1. Ga naar de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) de Analysator van Beste praktijken als zip dossier openen en downloaden.

      >[!NOTE]
      >Controleren [Analysator van best practices gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html#imp-considerations) om te leren hoe u BPA kunt uitvoeren.

   1. Het rapport exporteren in CSV-indeling

1. Klikken **Nieuw rapport uploaden** zodat kunt u BPA- rapport in CAM uploaden.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Rapport kan niet worden geüpload als u in de Incognito-modus van de browser werkt.

1. Nadat u een nieuw rapport hebt geüpload, kunt u het rapport van de Analyse van Beste praktijken zien.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Het dashboard van de Analyse van Beste praktijken van het overzicht en onderzoek in CAM. Zie [Rapport Analyse van beste praktijken](#analysis-report) voor meer informatie .

   >[!NOTE]
   >Als u een nieuw rapport uploadt, worden alle beoordelingen opnieuw ingesteld.

### Afdrukvoorbeeld gebruiken {#print-preview-cam}

U kunt de optie voor afdrukvoorvertoningen selecteren in Cloud Acceleration Manager om de rapporten af te drukken of om het rapport af te drukken naar een PDF-indeling, zodat u het gemakkelijk kunt delen.

Voer de onderstaande stappen uit:

1. Klik op de knop **Afdrukvoorbeeld** pictogram.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Klik op het nieuwe tabblad met het rapport in een afdrukbare voorvertoning op **Afdrukken** om het rapport af te drukken naar een PDF-indeling.

   >[!IMPORTANT]
   >
   >* De optie **Opslaan als PDF** wordt aanbevolen en ondersteund voor de bovenstaande functionaliteit.
   >* Als de knop Afdrukken van de browser wordt gebruikt, wordt slechts één pagina afgedrukt.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### Trendline weergeven gebruiken {#trendline-view-cam}

Wanneer u meer dan één rapport van de Analysator van Beste praktijken (BPA) in een Project uploadt, kunt u selecteren **Trendline weergeven** optie om resultaten van de historische BPA-rapporten te bekijken en te vergelijken.

Voer de onderstaande stappen uit om rapporten van de optie Trendline weer te geven:

>[!NOTE]
>Wanneer u meer dan één BPA- rapport in een Project uploadt, ziet u **...** pictogram.

1. Ga naar uw project en klik op **Controleren** van de **Analyse van best practices** in de **Gereedheid** fase.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klikken **...**.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >Het getoonde rapport is altijd het rapport dat de recentste rapportdatum heeft.

1. Klik in de vervolgkeuzelijst op **Trendline weergeven**, zoals weergegeven in onderstaande afbeelding.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klikken **Trendline weergeven** Hiermee opent u de trendlijnweergave van het rapport.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Het Trendline Rapport toont de resultaten van de historische BPA- rapporten in een grafische vertegenwoordiging.
   >
   >U ziet twee grafieken waarin de trend van de:
   > 
   >1. **Trend van bevindingen rapport**
   >1. **Aangepaste componenten en sjabloontrend**
   >
   >U kunt de grafische weergave toevoegen of wijzigen in de keuzelijst, zoals in de onderstaande afbeelding wordt getoond:
   >![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Rapport Analyse van beste praktijken {#analysis-report}

Onderzoek de volgende kaarten beschikbaar in de pagina van het Rapport van de Analyse van Beste praktijken:

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Met elke kaart kunt u:
>
>* het bijbehorende tabblad openen
>* bladwijzer alle rapportlusjes (met inbegrip van het filtreren) voor het delen of toekomstige herwinning
>* gebruik het detailspictogram om de details van elk rapport te bekijken vinden

#### Rapporteigenschappen {#report-properties}

De **Rapporteigenschappen** De kaart biedt informatie over rapporteigenschappen zoals rapportdatum, duur, filters, uploaddatum en Adobe Experience Manager (AEM)-gegevens.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### Overzicht van rapporten {#report-overview}

Dit **Overzicht van rapporten** kaart geeft de bevindingen en ernst van het rapport weer die van toepassing zijn bij het beoordelen van de gereedheid om over te gaan naar AEM as a Cloud Service, zoals in onderstaande afbeelding wordt getoond.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

Als u op dit rapport klikt, wordt het dialoogvenster **Rapport** tab.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

U kunt het rapport filtreren dat op belangrijkheid, subtype, of telling wordt gebaseerd.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Zie [Het rapport met de analyse van best practices interpreteren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html) voor meer informatie over de categorieën bevindingen en de belangrijkste niveaus.

#### Evaluatie van best practices {#best-practices-assessment}

De optie Beoordeling van Beste praktijken verstrekt een beoordeling van uw huidige AEM instantie en verstrekt raad over volgende stappen om AEM beste praktijken goed te keuren. U kunt de volgende informatie bekijken vanaf dit tabblad:

* Overzicht van AEM
* Aangepaste componenten en sjablonen
* Aanvullende bevindingen
* Langzame query&#39;s
* Onderhoudstaken

#### Complexiteit-evaluatie van migratie {#migration-complexity-assessment}

De optie voor de beoordeling van de complexiteit van migratie biedt een beoordeling van de complexiteit om de bestaande AEM te migreren naar AEM as a Cloud Service.

U kunt de volgende informatie bekijken vanaf dit tabblad:

* Overzicht van AEM
* Beoordeling
* Overwegingen bij migratie van inhoud

  ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Planning en de Kaart van de Opstelling gebruiken {#planning-setup}

1. Klikken **Weergave** van de **Planning en installatie** kaart. Deze kaart biedt alle relevante inhoud die u helpt uw AEM te plannen en in te stellen.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. Een inhoudscarrousel geeft alle relevante informatie weer voor deze fase van de migratiereis.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Het schrappen van een Rapport van de Analyse van de Beste praktijken van de mening Trendline {#delete-trendline}

>[!IMPORTANT]
>Een rapport kan slechts worden geschrapt wanneer meer dan één rapport in een project is geupload.

1. Ga naar uw project en klik op **Controleren** van de **Analyse van best practices** in de **Gereedheid** fase.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klikken **...**.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. Klik in de vervolgkeuzelijst op **Trendline weergeven**, zoals weergegeven in onderstaande afbeelding.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klik op het verwijderpictogram in het menu **Trendline-rapport** scherm.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Klikken **Verwijderen** om de schrapping te bevestigen.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u zich kunt aanmelden bij de functie voor de functie voor het maken van een project, kunt u nu verdergaan met het evalueren van de volgende stap in het dialoogvenster [Implementatiefase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html).
