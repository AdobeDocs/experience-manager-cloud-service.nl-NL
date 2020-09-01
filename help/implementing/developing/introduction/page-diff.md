---
title: Developing and Page Diff
description: Begrijp hoe de functie Pagina Diff werkt en hoe deze een ontwikkelaar kan beïnvloeden
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# Developing and Page Diff {#developing-and-page-diff}

## Overzicht van functies {#feature-overview}

Het maken van inhoud is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina met een vorige versie naast elkaar kunnen vergelijken met de gemarkeerde verschillen.

Met het paginagecheidingsteken kan de gebruiker de huidige pagina vergelijken met opstarters, vorige versies, enzovoort. Zie [Pagina Diff](/help/sites-cloud/authoring/features/page-diff.md)voor meer informatie over deze gebruikersfunctie.

## Bewerkingsdetails {#operation-details}

Wanneer u versies van een pagina vergelijkt, wordt de vorige versie die de gebruiker wil vergelijken opnieuw gemaakt door op de achtergrond AEM te plaatsen om het afschuiven te vergemakkelijken. Dit is nodig om de inhoud [voor vergelijking](/help/sites-cloud/authoring/features/page-diff.md)naast elkaar te kunnen weergeven.

Deze recreatiebewerking wordt intern AEM uitgevoerd en is transparant voor de gebruiker en vereist geen interventie. Nochtans zou een beheerder die de bewaarplaats bijvoorbeeld in CRX DE Lite bekijkt deze ontspannen versies binnen de inhoudsstructuur zien.

Wanneer de inhoud wordt vergeleken, wordt de hele structuur tot aan de te vergelijken pagina opnieuw gemaakt op de volgende locatie:

`/tmp/versionhistory/`

Er wordt automatisch een opschoningstaak uitgevoerd om deze tijdelijke inhoud op te schonen.

## Machtigingen {#permissions}

Het diff komt cliënt-kant via DOM vergelijking voor, die het diff proces eenvoudig maken, nochtans zijn er een aantal beperkingen die door de ontwikkelaar moeten worden overwogen.

* Deze functie gebruikt CSS-klassen die geen naamruimte zijn met de AEM Product. Als andere aangepaste CSS-klassen of CSS-klassen van derden met dezelfde namen op de pagina worden opgenomen, kan dit van invloed zijn op de weergave van het diff.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Omdat het diff cliënt-kant is en op paginading uitvoert, zullen om het even welke aanpassingen aan DOM nadat de cliënt-zijdiff dienst is in werking gesteld niet administratief worden verwerkt. Dit kan

   * Componenten die AJAX gebruiken om inhoud op te nemen
   * Toepassingen voor één pagina
   * Op JavaScript gebaseerde componenten die het DOM op gebruikersinteractie manipuleren.
