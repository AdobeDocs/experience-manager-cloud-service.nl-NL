---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service release 2022.02.0
description: Dit zijn de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service release 2022.02.0.
feature: Release Information
source-git-commit: d1fe713f0c35a96cf6ba3172ea11986fd9d42fd6
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2022.02.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2022.02.0.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2022.02.0 is 10 februari 2022. De volgende release is gepland voor 10 maart 2022.

## Wat is er nieuw? {#what-is-new}

* Nieuw versneld [Webservicepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) zijn geïntroduceerd om HTTPD/verzender-configuratie uitsluitend te implementeren.
   * U moet AEM versie hebben `2021.12.6151.20211217T120950Z` of nieuwer en [deelnemen aan de flexibele modus van de verzendingsprogramma&#39;s](/help/implementing/dispatcher/disp-overview.md#validation-debug) om deze functie te gebruiken.
   * Dit onderdeel wordt geleidelijk ingevoerd gedurende de twee weken na de release van 2022.02.0.
* De landingservaring van Cloud Manager is vernieuwd voor verbeterde navigatie, eenvoudig schakelen tussen raster-/tegelweergaven en pop-ups voor snel overzicht van het programma.
* Een nieuwe drempelwaarde voor onvoldoende prestaties (`< D`) is toegevoegd aan de [betrouwbaarheidsmaatstaf.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * Klanten met ernstige kwaliteitsproblemen die van invloed zijn op de stabiliteit van het systeem, voornamelijk in verband met ongeldige indexen en workflowprocessen, kunnen pas implementeren als deze problemen zijn opgelost.
* De ernst van de `BannedPath` [kwaliteitsregel](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) is veranderd van blokker in kritiek.
* De pijplijntovenaar zal de gebruiker informeren wanneer een AEM omgevingsupdate alvorens een [Webservicepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) ermee geassocieerd.

## Opgeloste problemen {#bug-fixes}

* De oude wachtwoorden van de git-opslagplaats worden nu altijd ongeldig gemaakt wanneer een nieuw wachtwoord wordt gegenereerd.
* Het bijwerken van omgevingsvariabelen via de API heeft in zeldzame situaties geen invloed meer op de uitvoering van een pijpleiding.
