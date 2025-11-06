---
title: Inleiding tot productieprogramma's
description: Leer welke productieprogramma's en suggesties voor het instellen van uw eigen programma zijn.
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---


# Inleiding tot productieprogramma&#39;s {#production-programs}

Een productieprogramma is voorgenomen voor een team dat klaar is beginnen te schrijven, bouwend, en testend code met het doel om het op te stellen om levend verkeer te ontvangen.

Nadat u [ uw productieprogramma ](creating-production-programs.md) creeert, leidt de tovenaar van de a [ programmaverwezenlijking ](using-the-wizard.md) de gebruiker door selecties afhankelijk van het doel van de gebruiker in het creëren van het programma.

## Opties voor programmaontwerp {#program-creation-options}

Uw contractuele overeenkomst met Adobe bepaalt het aantal en de typen oplossingen die beschikbaar zijn voor uw specifieke organisatie wanneer u productieprogramma&#39;s maakt. U hebt controle over hoe u de beschikbare oplossingen aan Cloud Manager-programma&#39;s kunt toewijzen.

In de volgende tabel worden de algemene scenario&#39;s beschreven van de beschikbare oplossingen en de typische productieprogramma&#39;s die op deze oplossingen zijn gebaseerd.

| Beschikbare oplossingen | Programmaopties | Wat is inbegrepen | Wanneer gebruiken | Voorbeelden |
|---------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 Sites-oplossing | 1 programma voor alleen sites maken | 1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling | NVT | NVT |
| 1 Assets-oplossing | 1 Assets-programma maken | 1 productie + 1 fase, 1 ontwikkeling, 1 snelle ontwikkeling | NVT | NVT |
| 1 sites +1 Assets | Eén programma maken: <br> 1 Sites &amp; Assets-programma | 1 productie + 1 fase, 2 ontwikkeling, 2 snelle ontwikkeling | Wanneer een meerderheid van de digitale activa wordt gebruikt om de plaatsimplementatie te steunen.<br> In dergelijke gevallen, zijn de meeste digitale activa in een gebeëindigde staat, klaar om voor kanaalervaringen via Plaatsen te worden gebruikt.<br> typisch, is één enkel team verantwoordelijk voor het beheren van inhoud voor zowel Plaatsen als Assets. | Afbeeldingen die voornamelijk voor een website worden gebruikt.<br> een intern portaal die in AEM Sites wordt gebouwd verspreidt PDFs. |
| 1 sites +1 Assets | Creeer afzonderlijke programma&#39;s:<br> 1 slechts het programma van Plaatsen &amp; 1 slechts het programma van Assets | 1 Productie + 1 Stadium, 1 Ontwikkeling, 1 Snelle Ontwikkeling <br> 1 Productie + 1 Stadium, 1 Ontwikkeling, 1 Snelle Ontwikkeling | Wanneer veel digitale elementen de implementatie van sites niet rechtstreeks ondersteunen.<br> In dergelijke gevallen bevinden elementen zich in verschillende statussen, waaronder Raw-bestandstypen en werken in uitvoering.<br> een specifiek creatief team beheert digitale activa door zijn eigen levenscyclus en heeft afzonderlijke werkschema&#39;s en versiecycli dan het de inhoudbeheerteam van Plaatsen. | Raw-afbeeldingen van een fotoshoot worden opgeslagen in het Assets-programma en er worden slechts een paar foto&#39;s gebruikt voor de implementatie van Sites.<br> een groot aantal Creative Cloud dossiertypes, zoals Photoshop en Illustrator, worden beheerd in AEM Assets en gaan door hun eigen goedkeuringswerkschema alvorens een gebeëindigde activa wordt geproduceerd.<br> overweeg gebruikend [ Verbonden Assets ](/help/assets/use-assets-across-connected-assets-instances.md#overview-of-connected-assets) in dergelijke gevallen. |
| 1 sites + 1 sites | Creeer afzonderlijke programma&#39;s:<br> 1 slechts het programma van Plaatsen &amp; 1 slechts programma van Plaatsen | 1 Productie + 1 Stadium, 1 Ontwikkeling, 1 Snelle Ontwikkeling <br> 1 Productie + 1 Stadium, 1 Ontwikkeling, 1 Snelle Ontwikkeling | Voor implementaties van multi-huurdersplaatsen.<br> in dergelijke gevallen, moeten de veelvoudige plaatsen met hun eigen versieschema en specifieke ontwikkeling en inhoudsteams worden beheerd. | Twee handelsmerken met specifieke websites en afzonderlijke ontwikkelingsteams |


>[!NOTE]
>
>De programma&#39;s van de productie [ kunnen worden uitgegeven maar niet worden geschrapt ](editing-programs.md).
