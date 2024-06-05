---
title: Inleiding tot productieprogramma's
description: Leer welke productieprogramma's en suggesties voor het instellen van uw eigen programma zijn.
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---


# Inleiding tot productieprogramma&#39;s {#production-programs}

Een productieprogramma is voorgenomen voor een team dat klaar is beginnen te schrijven, bouwend, en testend code met het doel om het op te stellen om levend verkeer te ontvangen.

Na u [uw productieprogramma op te zetten,](creating-production-programs.md) a [wizard voor het maken van programma](using-the-wizard.md) begeleidt de gebruiker door selecties afhankelijk van het doel van de gebruiker bij het maken van het programma.

## Opties voor het maken van programma {#program-creation-options}

Uw contractuele overeenkomst met Adobe bepaalt het aantal en de soorten oplossingen beschikbaar aan uw specifieke organisatie wanneer het creëren van productieprogramma&#39;s. U hebt controle over de manier waarop u de beschikbare oplossingen kunt toewijzen aan programma&#39;s van Cloud Manager.

In de volgende tabel worden de algemene scenario&#39;s beschreven van de beschikbare oplossingen en de typische productieprogramma&#39;s die op deze oplossingen zijn gebaseerd.

| Beschikbare oplossingen | Programmaopties | Wat is inbegrepen | Wanneer gebruiken | Voorbeelden |
|---------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 Sites-oplossing | 1 programma voor alleen sites maken | 1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling | NVT | NVT |
| 1 Elementenoplossing | 1 programma met alleen elementen maken | 1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling | NVT | NVT |
| 1 sites + 1 middelen | Eén programma maken: <br>1 Sites &amp; Assets-programma | 1 productie + 1 fase, 2 ontwikkeling, 2 snelle ontwikkeling | Wanneer een meerderheid van de digitale activa wordt gebruikt om de plaatsimplementatie te steunen.<br>In dergelijke gevallen bevinden de meeste digitale middelen zich in een voltooide staat en kunnen ze worden gebruikt voor kanaaloverschrijdende ervaringen via sites.<br>Doorgaans is één team verantwoordelijk voor het beheer van inhoud voor zowel sites als middelen. | Afbeeldingen die voornamelijk voor een website worden gebruikt.<br>PDF die worden gedistribueerd via een intern portaal dat in AEM Sites is gebouwd. |
| 1 sites + 1 middelen | Maak afzonderlijke programma&#39;s:<br>1 Alleen site-programma &amp; 1 alleen Middelen-programma | 1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling<br>1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling | Wanneer veel digitale elementen de implementatie van sites niet rechtstreeks ondersteunen.<br> In dergelijke gevallen bevinden de elementen zich in verschillende statussen, waaronder Raw-bestandstypen en werken in uitvoering.<br>Een speciaal creatief team beheert digitale middelen via zijn eigen levenscyclus en heeft aparte workflows en releasecycli dan het Sites-inhoudbeheerteam. | Raw-afbeeldingen van een fotoshoot worden opgeslagen in het programma Elementen en er worden slechts een paar foto&#39;s gebruikt voor de implementatie van Sites.<br>Een groot aantal bestandstypen van Creatives Cloud, zoals Photoshop en Illustrator, worden in AEM Assets beheerd en doorlopen hun eigen goedkeuringswerkstroom voordat een voltooid  wordt gegenereerd.<br>Gebruik [Verbonden elementen](/help/assets/use-assets-across-connected-assets-instances.md#overview-of-connected-assets) in dergelijke gevallen. |
| 1 sites + 1 sites | Maak afzonderlijke programma&#39;s:<br>1 Alleen voor sites en 1 alleen voor sites | 1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling<br>1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling | Voor plaatsen multi-huurder implementaties.<br>In dergelijke gevallen, moeten de veelvoudige plaatsen met hun eigen versieschema en specifieke ontwikkeling en inhoudsteams worden beheerd. | Twee handelsmerken met specifieke websites en afzonderlijke ontwikkelingsteams |


>[!NOTE]
>
>Productieprogramma&#39;s [kan worden bewerkt en niet worden verwijderd.](editing-programs.md)
