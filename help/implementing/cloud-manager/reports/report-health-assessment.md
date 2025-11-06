---
title: Health Assessment for Production and Stage Environment
description: Leer hoe u Cloud Manager Health Assessment gebruikt. U kunt AEM-omgevingen scannen, rapporten uitvoeren en reviseren, details van problemen bekijken, PDF's exporteren en vorige uitvoeringen beheren.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 0%

---


# Gezondheidsbeoordeling {#about-health-assessment}

Health Assessment is een geautomatiseerde, niet-indringende scan voor productie- en werkgebiedomgevingen in Cloud Manager in AEM as a Cloud Service. Het evalueert inhoud, code, en configuraties om anti-patronen te vinden en van beste praktijken af te wijken, die veiligheid en prestaties verbeteren.

De gezondheidsbeoordelingsdienst doet het volgende:

* Scant omgevingen en stelt prestatieknelpunten, inefficiënties en risico&#39;s bloot.
* Analyseert inhoudsstructuren, zoals blauwdrukken, levende exemplaren, en klantenconfiguraties.
* Detecteert verouderde afhankelijkheden, waaronder AEM SDK en bibliotheken van derden.
* Hiermee worden problemen met de codekwaliteit gemarkeerd, zoals onjuiste annotaties en inefficiënte patronen.
* Biedt activeerbare begeleiding in dashboards (bijvoorbeeld, Centrum van de Actie).
* Driveert proactieve probleemoplossing om de systeemprestaties te verbeteren.

Bij elke uitvoering worden problemen weergegeven op basis van ernst, koppelingen naar richtlijnen en aanbevolen oplossingen en wordt een PDF-export van het rapport ondersteund. U kunt de **Meest recente mening van het Rapport** voor de huidige staat gebruiken en **Verouderde Rapporten** om looppas te vergelijken.

Zie ook {de patronen van de Beoordeling van de Gezondheid 0} [&#x200B; voor regeldefinities en saneringsdetails.](#ha-patterns)

## Toegang tot de pagina Health Assessment {#access-health-assessment}

1. Teken in Cloud Manager bij [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com).
1. In de **Snelle toegang** sectie, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.
1. Selecteer de gewenste organisatie. De onderstaande afbeelding is ter illustratie. Selecteer uw eigen organisatie.

   ![&#x200B; Selecterend een organisatie in Cloud Manager &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-org.png)

1. Op de **Mijn console van Programma&#39;s**, klik het programma waarvoor u zijn rapport wilt bekijken.

1. Voer een van de volgende handelingen uit:
   * In de **kaart van Milieu**, rechts van een milieunaam, klik ![&#x200B; het pictogram van de Ellipsis of Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/ui_18/More.svg), dan kies **Beoordeling van de Gezondheid** van het menu.

     ![&#x200B; het Selecteren van de Beoordeling van de Gezondheid van het ellipsmenu in de kaart van Milieu &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-myprograms-environments-card.png)

   * Van het linkerzijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van Gegevens &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**. Voor de pagina van Milieu, rechts van een milieunaam, klik ![&#x200B; het pictogram van de Ellipsis of Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/ui_18/More.svg), dan kies **de Beoordeling van de Gezondheid** van het menu.

     ![&#x200B; het Selecteren van de Beoordeling van de Gezondheid van het ellipsmenu op de pagina van Milieu&#39;s &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-environments-page.png)

## Een nieuw rapport uitvoeren voor een geselecteerde omgeving {#run-report}

1. [&#x200B; toegang tot de pagina van de Beoordeling van de Gezondheid &#x200B;](#access-health-assessment).
1. In de hoger-juiste hoek van de **pagina van de Beoordeling van de Gezondheid**, bevestig het doelmilieu dat u op het punt staat te beoordelen.

   Als het milieu onjuist is, klik ![&#x200B; onderaan of drop-down menu aan geselecteerd een verschillend milieu &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) om het correcte milieu van de lijst te kiezen.

1. Klik **Rapport van de Looppas**.

   ![&#x200B; klik de Generate nieuwe rapportknoop op de pagina van de Beoordeling van de Gezondheid &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-run-report.png)

   Terwijl een rapport voor het geselecteerde milieu loopt, **looppas Gehandicapte de verblijven van het Rapport** tot het eindigt.

   ![&#x200B; Rapport in het midden van het lopen &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-running-report.png)

   Wanneer het rapport volledig is, verschijnt het rapport op de **pagina van de Beoordeling van de Gezondheid**, in de **Laatste sectie van het Rapport**.

## Het meest recente rapport weergeven {#view-latest-report}

* Op de **pagina van de Beoordeling van de Gezondheid**, herzie de **Laatste rapport** sectie voor de volgende informatie:

   * Resultaten van de meest recente uitvoering.
   * Datum en tijd van uitvoering.
   * Totaal aantal uitgiften.
   * Belangrijkste punten.
   * Acties: **[details van de Mening](#view-report-details)** of **[Download PDF](#download-pdf-report)** van alle kwesties.

  ![&#x200B; de Meest recente pagina van de Beoordeling na de generatie van een nieuw rapport voor een geselecteerd milieu &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-latest-report-page.png)

### Bekijk de meest recente rapportdetails {#view-report-details}

* Op de **pagina van de Beoordeling van de Gezondheid**, rechts van de **Meest recente titel van het Rapport**, klik ![&#x200B; het pictogram van de Ellipsis of Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/ui_18/More.svg), dan klik **Details van de Mening** of **Download**.

  De **optie van de Details van de Mening** toont u het volgende:

   * Een uitgebreide lijst van kwesties.
   * Mogelijkheid om bevindingen en beschrijvingen weer te geven.
   * Mogelijkheid om documentatie met mogelijke oplossingen te bekijken.

     ![&#x200B; de beschrijvingen en het vinden van de kwestie &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-issue-descriptions-and-findings.png)

   * De **optie van de Download** geeft u de capaciteit om individuele uitgifterapporten in PDF te downloaden.

     ![&#x200B; Download PDF van individuele uitgifterapporten &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-details-page-doc-links.png)


### PDF van volledig rapport downloaden {#download-pdf-report}

* Bij de hoger-juiste hoek van de rapportpagina, klik **Download**.

  Er wordt een ZIP-bestand gegenereerd dat PDF&#39;s bevat voor alle problemen die in dat rapport worden gedetecteerd.

  ![&#x200B; Download PDF van alle kwesties die in een rapport &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-download-pdf.png) worden gevonden


## Eerdere rapporten bekijken {#review-past-reports}

Op de **pagina van de Beoordeling van de Gezondheid**, herzie de **Oudere sectie van Rapporten** voor de volgende informatie:

* Bekijk details van eerdere rapporten.
* De datum van elke uitvoering weergeven.
* Download een PDF voor elk rapport.
* Sorteren op datum, aantal uitgaven of omgeving.

![&#x200B; Overzicht voorbij rapporten &#x200B;](/help/implementing/cloud-manager/reports/assets/ha-past-reports.png)

* Aan het recht van de **Oude rubriek van Rapporten**, klik ![&#x200B; onderaan of drop-down menu aan geselecteerd een verschillend milieu &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) om voorbij rapporten door datum te sorteren.
* Helemaal rechts van een rapport, klik ![&#x200B; het pictogram van de Ellipse of Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/ui_18/More.svg), dan klik **de details van de Mening** of **Download**.


## Health Assessment Patronen {#ha-patterns}

Hieronder volgt een volledige lijst van antipatronen en problemen die door Health Assessment in AEM as a Cloud Service worden vastgesteld. De lijst groepeert punten in drie types: De Analyse van de inhoud, de Analyse van de Code, en Cloud Service Optimizer anti-patronen, met een verklaring voor elk.

| Patroonnaam | Categorie | Type | Beschrijving | Gevolgen | Automatisch gecorrigeerd? |
| --- | --- | --- | --- | --- | --- |
| Aangepaste AEM-groepen met directe gebruikerstoevoeging | Beveiliging | Inhoudsanalyse | Gebruikers die rechtstreeks aan AEM-groepen zijn toegevoegd in plaats van IMS-groepen als leden toe te voegen. | Het beheer van machtigingen en het beheer van de beveiliging kunnen ingewikkeld worden. [&#x200B; IMS Steun &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/ims-support) | Nee |
| Ontbrekend JCR-inhoudsknooppunt op pagina&#39;s | Structuur opslagplaats | Inhoudsanalyse | Het knooppunt `jcr:content` ontbreekt op de pagina. | Functionele beperkingen in Experience Manager as a Cloud Service. [&#x200B; de opsporing van het Patroon - ACV &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv) | Nee |
| Ontbrekend brontype op pagina&#39;s | Structuur opslagplaats | Inhoudsanalyse | Ontbrekende `sling:resourceType` op pagina. | Functionele beperkingen in Experience Manager as a Cloud Service. [&#x200B; de opsporing van het Patroon - ACV &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv) | Nee |
| Pagina&#39;s met te veel knooppunten | Prestaties | Inhoudsanalyse | Pagina&#39;s bevatten een groot aantal knooppunten in hun structuur. | Trage laadtijden voor pagina&#39;s en slechte gebruikerservaring. [&#x200B; de opsporing van het Patroon - PCX &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/pcx) | Nee |
| Buitengewone werkstroominstanties | Prestaties | Inhoudsanalyse | Er zijn te veel workflowinstanties actief. | Algemene verslechtering van de systeemprestaties. [&#x200B; de taken van het Onderhoud &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance) | Nee |
| Niet-gezuiverde voltooide workflowinstanties | Prestaties | Inhoudsanalyse | Oudere voltooide workflowexemplaren worden niet gewist. | Minder systeemefficiëntie en hogere opslagkosten. [&#x200B; de taken van het Onderhoud &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance) | Nee |
| Statistieken inhoudsfragmentgebruik | Statistieken | Inhoudsanalyse | Tracks the number of Content Fragments in use. | NVT | NVT |
| Gebruiksstatistieken inhoudsfragmentmodel | Statistieken | Inhoudsanalyse | Tracks the number of Content Fragment Models in use. | NVT | NVT |
| MSM groot aantal blauwdrukken | Statistieken | Inhoudsanalyse | Traceert het aantal blauwdrukken. | Het kan de complexiteit van het beheer vergroten en het beheer van de inhoud bemoeilijken. | NVT |
| MSM-pagina&#39;s per vervaging | Statistieken | Inhoudsanalyse | Traceert het aantal pagina&#39;s per blauwdruk. | Het kan de complexiteit van het beheer vergroten en het beheer van de inhoud bemoeilijken. | NVT |
| Te veel levende MSM-kopieën | Statistieken | Inhoudsanalyse | Tracks the number of live copies. | Dit kan prestatieproblemen veroorzaken tijdens rollouts en de synchronisatie van inhoud bemoeilijken. | NVT |
| MSM Te veel actieve kopieën per vervaging | Statistieken | Inhoudsanalyse | Traceert het aantal actieve kopieën per blauwdruk. | Dit kan prestatieproblemen veroorzaken tijdens rollouts en de synchronisatie van inhoud bemoeilijken. | NVT |
| Aantal Assets | Statistieken | Inhoudsanalyse | Tracks the number of assets. | NVT | NVT |
| Aantal sites | Statistieken | Inhoudsanalyse | Tracks the number of sites. | NVT | NVT |
| Aantal Forms | Statistieken | Inhoudsanalyse | Tracks the number of forms. | NVT | NVT |
| Formulierfragmenten | Statistieken | Inhoudsanalyse | Tracks the number of form fragments. | NVT | NVT |
| Interactie Communicatie | Statistieken | Inhoudsanalyse | Tracks the number of form communication interactions. | NVT | NVT |
| FDM&#39;s | Statistieken | Inhoudsanalyse | Tracks the number of form data models. | NVT | NVT |
| Verouderde afhankelijkheden | Afhankelijkheden | Codeanalyse | Benadrukt verouderde gebiedsdelen in de klantenbewaarplaats. | Incompatibiliteit met nieuwere AEM-versies; potentiële kwetsbaarheden op het gebied van beveiliging. | Nee |
| Verkeerde AEM SDK-versie | Afhankelijkheden | Codeanalyse | Versies die ouder zijn dan (n-2) in vergelijking met de Cloud Manager-milieuversie. | Dit kan leiden tot constructiefouten in Cloud Manager en tot problemen in lokale ontwikkelomgevingen. | Nee |
| Verouderde Mockito Core Dependency | Afhankelijkheden | Codeanalyse | Versies onder 4.x.x worden voor AEM as a Cloud Service als verouderd beschouwd. | Dit kan leiden tot constructiefouten in Cloud Manager en tot problemen in lokale ontwikkelomgevingen. | Nee |
| Niet-ondersteunde annotaties | Afhankelijkheden | Codeanalyse | Niet-ondersteunde annotaties in de Cloud Manager-opslagplaats van de klant. | Mogelijke toepassingsfouten en verminderde prestaties. | Nee |
| @Injecteer annotatie in Sling-modellen | Afhankelijkheden | Codeanalyse | Vervangen `@Inject` aantekening. | Verminderde toepassingsprestaties door overhead van de injectieresolutie. | Nee |
| Uitgaande HTTP-verzoeken | Prestaties | Antipatronen van Cloud Service Optimizer | Het problematische gebruik in verzoekcontext, hoge onderbrekingen, of het sluiten van verbindingen. | Algemene verslechtering van de systeemprestaties en mogelijke uitvallen. | Ja |
| Langzame query&#39;s | Prestaties | Antipatronen van Cloud Service Optimizer | Langzame vragen in klantencode. | Verminderde systeemprestaties en mogelijke time-outs. | Ja |

### Categorieën {#ha-patterns-categories}

| Categorie | Beschrijving |
| --- | --- |
| Beveiliging | Patronen met betrekking tot veiligheidspraktijken, gebruikersbeheer, en toegangsbeheer. |
| Prestaties | Patronen die van invloed zijn op de prestaties van toepassingen en systemen. |
| Structuur opslagplaats | Patronen met betrekking tot de organisatie en structuur van de JCR-opslagplaats. |
| Afhankelijkheden | Patronen met betrekking tot code-afhankelijkheden en versiebeheer. |
| Statistieken | Patronen die gebruiksstatistieken en metriek vertegenwoordigen. |



