---
title: 'Bekende problemen '
description: Communicatie beste praktijken, bekende kwesties, en beperkingen
source-git-commit: 06da7d2a5063e163aa1534bedbc79ae50ef27515
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 1%

---


# Veelgestelde vragen, best practices, bekende problemen en beperkingen {#best-practices-known-issues-and-limitations}

Voordat u begint met het gebruik van communicatie-API&#39;s, vaak gestelde vragen, moet u de volgende bekende problemen en beperkingen controleren:

## Bekende problemen

- U kunt een specifiek rendertype (PDF, AFDRUKKEN) slechts eenmaal gebruiken in de lijst met afdrukopties. U kunt bijvoorbeeld niet beschikken over twee PRINT-opties die elk een PCL-rendertype opgeven.

- Voor een batchconfiguratie is slechts één instantie van een combinatie van waarden van OutputType (PDF, PRINT) en RenderType (PostScript, PCL, IPL, ZPL, enz.) is toegestaan.

## Best practices voor

- Adobe raadt aan gegevensbestanden op te slaan in een blob-containerarchief in het cloudgebied dat door AEM Cloud Service wordt gebruikt.

## Veelgestelde vragen {#faq}

**Kan ik een gecontroleerde map of andere opslagmechanismen gebruiken om invoer en uitvoer op te slaan?**

Op dit moment kunt u Microsoft Azure Storage gebruiken om invoergegevens en gegenereerde documenten op te slaan. Microsoft Azure-opslag biedt verschillende opties voor [geautomatiseerde gegevensverplaatsingsbewerkingen](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10).

**Is een Microsoft Azure Storage-account inbegrepen bij een Experience Manager Forms Cloud Service-licentie?**

Microsoft Azure Storage account is onafhankelijk van Experience Manager Forms Cloud Service license.

**Slaat de Communicatie APIs gegevens op de servers van de Cloud Service van Experience Manager Forms op?**

Invoer- en uitvoergegevens worden alleen opgeslagen op Microsoft Azure Storage.

**Zijn communicatie-API&#39;s alleen beschikbaar voor Experience Manager Forms Cloud Service? Kan ik vergelijkbare functionaliteit krijgen in een on-premise omgeving?**

U kunt de dienst van de Output van AEM Forms gebruiken om een malplaatje (XFA of PDF) met klantengegevens te combineren om documenten in PDF, PS, PCL, en formaten te produceren ZPL.

In vergelijking met een omgeving op locatie biedt de Cloud Service extra voordelen van automatisch schalen en kosteneffectiviteit.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**Kan ik veelvoudige partijverrichtingen gelijktijdig in werking stellen?**
Ja, u kunt meerdere batchbewerkingen tegelijkertijd uitvoeren. Gebruik altijd verschillende bron- en doelmappen voor elke bewerking om conflicten te voorkomen.
