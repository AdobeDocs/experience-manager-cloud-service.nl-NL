---
title: Programma's en programmatypen
description: Leer meer over de hiërarchie van Cloud Manager en hoe de verschillende typen programma's in de structuur passen en hoe ze verschillen.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Programma&#39;s en programmatypen {#understanding-programs}

Cloud Manager is opgebouwd rond een hiërarchie van entiteiten. De details hiervan zijn niet van essentieel belang voor uw dagelijkse werk in Cloud Manager, maar een overzicht hiervan helpt u bij het begrijpen van programma&#39;s en het opzetten van uw eigen programma.

![Hiërarchie van Cloud Manager](assets/program-types1.png)

* **TENANT** - Dit is de top van de hiërarchie. Elke klant is provisioned met een huurder.
* **PROGRAMMA&#39;S** - elke huurder een of meer programma&#39;s heeft, [die vaak de gelicentieerde oplossingen van de klant weerspiegelen.](introduction-production-programs.md)
* **OMGEVINGEN** - Elk programma heeft meerdere omgevingen, zoals productie voor live-inhoud, één voor staging en één voor ontwikkelingsdoeleinden.
   * Elk programma kan slechts één productiemilieu, maar veelvoudige non-production milieu&#39;s hebben.
* **BEVESTIGING** - Programma&#39;s beschikken over git-opslagplaatsen waar de toepassing en front-end code worden onderhouden voor de omgevingen.
* **GEREEDSCHAPPEN EN WORKFLOWS** - De pijpleidingen beheren de plaatsing van code van de bewaarplaatsen aan de milieu&#39;s terwijl andere hulpmiddelen voor toegang tot logboeken, controle, en milieubeheer toestaan.

Een voorbeeld is vaak handig bij het contextualiseren van deze hiërarchie.

* WKND Travel and Adventure Enterprises zou een **huurder** die zich richt op reisgerelateerde media.
* De huurder van WKND Reizen en Adventure Enterprises zou twee kunnen hebben **programma&#39;s**: één Sites-programma voor WKND Magazine en één Assets-programma voor WKND Media.
* De programma&#39;s WKND Magazine en WKND Media zouden zowel dev, stadium, als productie hebben **omgevingen**.

## Broncodeopslagplaats {#source-code-repository}

Er wordt automatisch een programma voor Cloud Manager geleverd met een eigen git-opslagruimte.

Om tot de gegevensopslagplaats van de Manager van de Wolk toegang te hebben, moeten de gebruikers een git cliënt met een bevel-lijn hulpmiddel, een standalone visuele git cliënt, of winde van de gebruiker van keus zoals Eclipse, IntelliJ, of NetBeans gebruiken.

Zodra een client is ingesteld, kunt u de git-opslagruimte beheren vanuit de gebruikersinterface van Cloud Manager. Ga voor meer informatie over het beheren van git met de gebruikersinterface van Cloud Manager naar [Toegang tot it](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

Als u de AEM Cloud-toepassing wilt gaan ontwikkelen, moet u een lokale kopie van de toepassingscode maken door deze uit te checken van de opslagplaats van Cloud Manager naar een locatie op uw lokale computer.

```java
$ git clone {URL}
```

De workflow is dus een standaard git-workflow.

1. Een gebruiker klonen een lokale kopie van de it-opslagplaats.
1. De gebruiker brengt wijzigingen aan in de lokale gegevensopslagruimte voor code.
1. Als dit gereed is, legt de gebruiker de wijzigingen weer vast aan de externe git-opslagplaats.

Het enige verschil is dat de externe git-opslagplaats deel uitmaakt van Cloud Manager, die transparant is voor de ontwikkelaar.

## Programmatypen {#program-types}

Een gebruiker kan een **productie** programma of een **sandbox** programma.

* A **productieprogramma** wordt gemaakt om live verkeer voor uw site in te schakelen.
   * Zie [Inleiding tot productieprogramma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer informatie .
* A **sandboxprogramma** wordt typisch gecreeerd ten behoeve van opleiding, lopende demo&#39;s, enablement, POCs, of documentatie.
   * Een zandbakomgeving is niet bedoeld voor het vervoer van levend verkeer en zal beperkingen hebben die een productieprogramma niet zal hebben.
   * Het omvat Plaatsen en Activa en wordt geleverd automatisch bevolkt met een git tak die steekproefcode, een ontwikkelomgeving, en een niet productiepijplijn omvat.
   * Zie [Inleiding tot Sandbox-programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) voor meer informatie .
