---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.7.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.7.0
feature: Release Information
source-git-commit: 3542d5a6b89b8673444786e3f9062dae0d315946
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.7.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.7.0.

>[!NOTE]
>Om de huidige Nota&#39;s van de Versie voor Adobe Experience Manager as a Cloud Service te zien, klik [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.7.0 is 15 juli 2021.


### Wat is er nieuw? {#what-is-new}

* Klanten kunnen nu Azul 8 en 11 JDK&#39;s gebruiken voor hun buildprocessen in Cloud Manager en kunnen een van deze JDK&#39;s selecteren voor met toolketens compatibele Maven-plug-ins *of* voor de volledige uitvoering van het Maven-proces.

* Uitgaande uitgang IP zal nu het programma worden geopend het dossier van het bouwstijlstaplogboek.

* Werkgebied- en productieomgevingen met oude versies van AEM rapporteren nu de status **Update Available**.

* Het maximum aantal ondersteunde SSL-certificaten is gestegen tot 20 per programma.

* Het maximumaantal domeinen dat kan worden gevormd is verhoogd tot 500 per milieu.

* De knoppen **Git beheren** hebben een nieuwe naam gekregen in **Git-info benaderen** en het dialoogvenster is visueel vernieuwd.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 28.

### Opgeloste problemen {#bug-fixes}

* In sommige situaties, was de Voorproef geen beschikbare optie toen het binden van een IP Lijst van gewenste personen aan een milieu.

* Wanneer u handmatig naar de pagina met uitvoeringsdetails voor een niet-bestaande uitvoering navigeerde, werd geen fout weergegeven, alleen een eindeloos laadscherm.

* Het foutbericht dat wordt weergegeven wanneer het maximumaantal SSL-certificaten is bereikt, is niet nuttig.

* In sommige omstandigheden, zou er een discrepantie in de versieversie kunnen zijn die in de pijpleidingskaart op **Overview** pagina wordt getoond.

* De wizard Programma toevoegen heeft onjuist aangegeven dat de naam na het maken niet kan worden gewijzigd.

### Bekende problemen {#known-issues}

Klanten die overstappen op de Azul JDK&#39;s moeten zich ervan bewust zijn dat niet alle bestaande toepassingen zonder fout zullen compileren op Azul JDK. Het wordt hoogst geadviseerd om plaatselijk vóór omschakeling te testen.

