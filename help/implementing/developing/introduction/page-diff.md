---
title: Developing and Page Diff
description: Begrijp hoe de functie Pagina Diff werkt en hoe deze een ontwikkelaar kan beïnvloeden
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Developing and Page Diff {#developing-and-page-diff}

## Overzicht van functies {#feature-overview}

Inhoud maken is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina met een vorige versie naast elkaar kunnen vergelijken met de gemarkeerde verschillen.

Met het paginagecheiding kan de gebruiker de huidige pagina vergelijken met opstarters, vorige versies enzovoort. Voor details van deze gebruikerseigenschap, zie [&#x200B; Afschuiving van de Pagina &#x200B;](/help/sites-cloud/authoring/sites-console/page-diff.md).

## Bewerkingsdetails {#operation-details}

Wanneer u versies van een pagina vergelijkt, wordt de vorige versie die de gebruiker wil vergelijken, op de achtergrond opnieuw gemaakt door AEM om het schuiven te vergemakkelijken. Deze vorige versie is noodzakelijk om de inhoud [&#x200B; voor zij aan zij vergelijking &#x200B;](/help/sites-cloud/authoring/sites-console/page-diff.md) terug te geven.

Deze recreatiebewerking wordt intern AEM uitgevoerd en is transparant voor de gebruiker en vereist geen interventie. Een beheerder die de gegevensopslagruimte bijvoorbeeld in CRXDE Lite bekijkt, ziet deze opnieuw gemaakte versies echter wel binnen de inhoudsstructuur.

Wanneer de inhoud wordt vergeleken, wordt de hele structuur tot aan de te vergelijken pagina opnieuw gemaakt op de volgende locatie:

`/tmp/versionhistory/`

Er wordt automatisch een opschoningstaak uitgevoerd om deze tijdelijke inhoud op te schonen.

## Beperkingen {#limitations}

Het diff komt cliënt-kant door DOM vergelijking voor, die het diff proces eenvoudig maken. Er zijn echter verschillende beperkingen die de ontwikkelaar in overweging moet nemen.

* Deze functie gebruikt CSS-klassen die geen naamruimte hebben voor het AEM Product. Als andere aangepaste CSS-klassen of CSS-klassen van derden met dezelfde namen op de pagina worden opgenomen, kan dit van invloed zijn op de weergave van het diff.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Omdat het diff cliënt-kant is en op paginading loopt, worden om het even welke aanpassingen aan DOM nadat de cliënt-zijdiff dienst heeft gelopen niet rekenschap gegeven. Dit proces kan het volgende beïnvloeden:

   * Componenten die AJAX gebruiken om inhoud op te nemen
   * Toepassingen voor één pagina
   * Op JavaScript gebaseerde componenten die het DOM op gebruikersinteractie manipuleren.
