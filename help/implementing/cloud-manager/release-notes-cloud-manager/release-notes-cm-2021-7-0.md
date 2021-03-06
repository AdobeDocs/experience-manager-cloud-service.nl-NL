---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.7.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.7.0
feature: Release Information
exl-id: 7ef738a5-4657-482d-848b-e95e4fb816f9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.7.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.7.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.7.0 is 15 juli 2021.


### Wat is er nieuw? {#what-is-new}

* Klanten kunnen nu 8 en 11 JDK&#39;s gebruiken voor hun buildprocessen in Cloud Manager en kunnen een van deze JDK&#39;s selecteren voor gebruik van met toolketens compatibele Maven-plug-ins *of* de volledige uitvoering van het Maven-proces.

* Uitgaande uitgang IP zal nu het programma worden geopend het dossier van het bouwstijlstaplogboek.

* Stage- en productieomgevingen met oude versies van AEM rapporteren nu de status van **Update beschikbaar**.

* Het maximum aantal ondersteunde SSL-certificaten is gestegen tot 20 per programma.

* Het maximumaantal domeinen dat kan worden gevormd is verhoogd tot 500 per milieu.

* De **Git beheren** knoppen zijn hernoemd naar **Toegang tot informatie over toegang** en het dialoogvenster is visueel vernieuwd.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 28.

### Opgeloste problemen {#bug-fixes}

* In sommige situaties, was de Voorproef geen beschikbare optie toen het binden van een IP Lijst van gewenste personen aan een milieu.

* Wanneer u handmatig naar de pagina met uitvoeringsdetails voor een niet-bestaande uitvoering navigeerde, werd geen fout weergegeven, alleen een eindeloos laadscherm.

* Het foutbericht dat wordt weergegeven wanneer het maximumaantal SSL-certificaten is bereikt, is niet nuttig.

* In sommige omstandigheden kan er een discrepantie optreden in de releaseversie die wordt weergegeven op de pijplijnkaart op de **Overzicht** pagina.

* De wizard Programma toevoegen heeft onjuist aangegeven dat de naam na het maken niet kan worden gewijzigd.

### Bekende problemen {#known-issues}

Klanten die overstappen op de Azul JDK&#39;s moeten zich ervan bewust zijn dat niet alle bestaande toepassingen zonder fout zullen compileren op Azul JDK. Het wordt hoogst geadviseerd om plaatselijk v????r omschakeling te testen.
