---
title: 'Inleiding tot productieprogramma''s '
description: 'Inleiding tot productieprogramma''s '
translation-type: tm+mt
source-git-commit: aa42ccf73a6be9050a06f9cbea0d16b80b039d89
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---


# Inleiding tot productieprogramma&#39;s {#production-programs}

Een *Production* programma is bedoeld voor een gebruiker die vertrouwd is met AEM en Cloud Manager en klaar is om code te schrijven, te bouwen en te testen met als doel deze te implementeren in Production.

>[!NOTE]
>Je kunt een productieprogramma niet verwijderen.

Een wizard voor het maken van programma&#39;s begeleidt de gebruiker bij het maken van selecties, afhankelijk van het doel van de gebruiker bij het maken van het programma. Op basis van de ongebruikte oplossingsrechten die beschikbaar zijn voor de specifieke klant of organisatie, heeft de gebruiker controle over hoe beschikbare (ongebruikte) oplossingsrechten moeten worden toegewezen aan programma&#39;s van de Cloud Manager.

## Overwegingen bij het maken van programma&#39;s {#program-creation-considerations}

In de onderstaande tabel worden algemene scenario&#39;s beschreven waarmee rekening moet worden gehouden bij het maken van programma&#39;s in Cloud Manager:

| Ongebruikte rechten voor oplossingen beschikbaar in de organisatie | Programmaopties maken | Wat is inbegrepen | Wanneer en andere overwegingen gebruiken |
|--- |--- |--- |--- |
| 1 Sites-oplossing | Alleen programma 1 site maken | 1 productie + 1 fase, 1 ontwikkeling | NA |
| 1 sites + 1 sites | Maak afzonderlijke programma&#39;s: 1 Alleen voor sites en 1 alleen voor sites | 1 productie + 1 fase, 1 ontwikkeling 1 productie + 1 fase, 1 ontwikkeling | Implementaties van sites voor meerdere gebruikers. Meerdere sites met hun eigen releaseplanning en toegewezen ontwikkelings- en inhoudsteams. *Algemene voorbeelden*: Twee handelsmerken met specifieke websites en afzonderlijke ontwikkelingsteams |
| 1 sites + 1 middelen | Eén programma maken: 1 Sites &amp; Assets-programma | 1 Productie + 1 Fase, 2 Ontwikkeling | De meeste digitale elementen worden gebruikt om de implementatie van sites te ondersteunen. De meeste digitale middelen zijn in een voltooide staat, klaar om voor kanaalervaringen via Plaatsen te worden gebruikt.Typisch, is één enkel team verantwoordelijk voor het beheren van inhoud voor zowel Plaatsen als Activa. *Algemene voorbeelden*: Afbeeldingen die voornamelijk voor een website worden gebruikt. PDF&#39;s die worden gedistribueerd via een interne portal die in AEM Sites is gemaakt. |
| 1 sites + 1 middelen | Maak afzonderlijke programma&#39;s: 1 Alleen site-programma &amp; 1 alleen Middelen-programma | 1 productie + 1 fase, 1 ontwikkeling 1 productie + 1 fase, 1 ontwikkeling | Veel digitale elementen bieden geen directe ondersteuning voor de implementatie van sites. Elementen die worden beheerd, bevinden zich in verschillende statussen, waaronder Raw-bestandstypen en werken in uitvoering. Een speciaal creatief team beheert digitale middelen via zijn eigen levenscyclus en heeft aparte workflows en releasecycli dan het Sites-inhoudbeheerteam. *Algemene voorbeelden*: Raw-afbeeldingen van een foto worden opgeslagen in het programma Elementen en er worden slechts een paar foto&#39;s gebruikt voor de implementatie van Sites. Een groot aantal bestandstypen Creative Cloud, zoals Photoshop en Illustrator, worden in AEM Assets beheerd en doorlopen hun eigen goedkeuringswerkstroom voordat een voltooid-element wordt gegenereerd. Functies voor hefboomwerking: [Aangesloten elementen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=en#overview-of-connected-assets) |
| 1 Elementenoplossing | Alleen programma voor 1 elementen maken | 1 productie + 1 fase, 1 ontwikkeling | NA |


