---
title: Inhoud voorbereiden voor vertaling
description: Leer hoe u inhoud voorbereidt voor vertaling bij het ontwikkelen van meertalige websites.
feature: Language Copy
role: Admin
exl-id: afc577a2-2791-481a-ac77-468011e4302e
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Inhoud voorbereiden voor vertaling {#preparing-content-for-translation}

Meertalige websites bieden over het algemeen inhoud in meerdere talen. De site is gemaakt in één taal en wordt vervolgens vertaald in andere talen. In het algemeen bestaan meertalige sites uit vertakkingen van pagina&#39;s, waarbij elke vertakking de pagina&#39;s van de site in een andere taal bevat.

>[!TIP]
>
>Als u aan het vertalen van inhoud nieuw bent, zie [&#128279;](/help/journey-sites/translation/overview.md) de Vertaalreis van 0&rbrace; Plaatsen, die geleid weg door uw inhoud van AEM Sites te vertalen gebruikend AEM krachtige vertaalhulpmiddelen, ideaal voor die zonder AEM of vertaalervaring.

De [&#x200B; plaats van het WKND leerprogramma &#x200B;](/help/implementing/developing/introduction/develop-wknd-tutorial.md) omvat verscheidene taaltakken en gebruikt de volgende structuur:

```text
/content
    |- wknd
        |- language-masters
            |- en
            |- de
            |- es
            |- fr
            |- it
        |- us
            |- en
            |- es
        |- ca
            |- en
            |- fr
        |- ch
            |- de
            |- fr
            |- it
        |- de
            |- de
        |- fr
            |- fr
        |- es
            |- es
        |- it
            |- it
```

De taalkopie waarvoor u oorspronkelijk site-inhoud hebt gemaakt, is de hoofdtaal. De taalmaster is de bron die in andere talen wordt vertaald.

Elke taalvertakking van een site wordt een taalkopie genoemd. De hoofdpagina van een taalkopie, ook wel de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. `/content/wknd/fr` is bijvoorbeeld de hoofdtaal van de Franse taalkopie. De exemplaren van de taal moeten a [&#x200B; correct gevormde taalwortel &#x200B;](preparation.md#creating-a-language-root) gebruiken zodat de correcte taal wordt gericht wanneer de vertalingen van een bronplaats worden uitgevoerd.

Gebruik de volgende stappen om uw site voor te bereiden op vertaling:

1. Maak de hoofdmap van de taal van het stramien. De hoofdtaalsite van de Engelse WKND-demosite is bijvoorbeeld `/content/wknd/language-masters/en` . Zorg ervoor dat de taalwortel correct volgens de informatie in [&#x200B; Creërend een Wortel van de Taal &#x200B;](preparation.md#creating-a-language-root) wordt gevormd.
1. Ontwerp de inhoud van uw taalstramien.
1. Maak de hoofdmap van elke taalkopie voor uw site. De Franse taalkopie van de WKND-voorbeeldsite is bijvoorbeeld `/content/wknd/language-masters/fr` .

Nadat u de inhoud hebt voorbereid voor vertaling, kunt u automatisch ontbrekende pagina&#39;s maken in uw taalkopieën en bijbehorende vertaalprojecten. (Zie [&#x200B; Creërend een Project van de Vertaling &#x200B;](managing-projects.md).) voor een overzicht van het proces van de inhoudsomzetting in AEM, zie [&#x200B; Vertaalende Inhoud voor Meertalige Websites &#x200B;](overview.md).

## Een hoofdmap voor talen maken {#creating-a-language-root}

Maak een taalhoofdmap als de hoofdpagina van een taalkopie die de taal van de inhoud identificeert. Nadat u de taalwortel creeert, kunt u vertaalprojecten tot stand brengen die het taalexemplaar omvatten.

Om de taalwortel tot stand te brengen creeert u een pagina en gebruikt een de taalcode van ISO als waarde voor het **bezit van de Naam**. De taalcode moet een van de volgende notaties hebben:

* `<language-code>` - De ondersteunde taalcode is een tweelettercode zoals gedefinieerd in ISO-639-1, bijvoorbeeld `en` .
* `<language-code>_<country-code>` of `<language-code>-<country-code>` - De ondersteunde landcode is een code van twee kleine letters of hoofdletters zoals gedefinieerd in ISO 3166, bijvoorbeeld `en_US` , `en_us` , `en_GB` , `en-gb` .

U kunt beide indelingen gebruiken op basis van de structuur die u voor uw globale site hebt gekozen. Bijvoorbeeld, heeft de wortelpagina van het Franse taalexemplaar van de plaats WKND `fr` als **Naam** bezit. Het **bezit van de Naam** wordt gebruikt als naam van de paginaknooppunt in de bewaarplaats, en bepaalt daarom de weg van de pagina (`http://<host>:<4502>/content/wknd/language-masters/fr.html`).

1. Navigeer naar sites.
1. Selecteer de site waarvoor u een taalkopie wilt maken.
1. Selecteer **creeer**, en selecteer dan **Pagina**.

   ![&#x200B; creeer pagina &#x200B;](../assets/create-page.png)

1. Selecteer het paginamalplaatje en selecteer dan **daarna**.
1. In het **gebied van de Naam** type de landcode in het formaat van `<language-code>` of `<language-code>_<country-code>`, bijvoorbeeld, `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Typ een titel voor de pagina.

   ![&#x200B; creeer de pagina van de taalwortel &#x200B;](../assets/create-language-root.png)

1. Selecteer **Maken**. In de bevestigingsdialoogdoos, selecteer of **Gedaan** om aan de console van Plaatsen terug te keren, of **Open** om het taalexemplaar te openen.

## De status van taalwortels bekijken {#seeing-the-status-of-language-roots}

AEM verstrekt a **spoor van Verwijzingen** dat een lijst van taalwortels toont die zijn gecreeerd.

![&#x200B; wortels van de Taal &#x200B;](../assets/language-roots.png)

Gebruik de volgende proceduremening de taalexemplaren voor een pagina gebruikend de [&#x200B; spoorselecteur &#x200B;](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

1. Voor de plaatsenconsole, selecteer een pagina van de plaats en selecteer dan **Verwijzingen**.

   ![&#x200B; Open verwijzingen spoorstaaf &#x200B;](../assets/opening-references-rail.png)

1. In de verwijzingenspoorstaaf, de uitgezochte **Kopieën van de Taal**. De spoorstaaf toont de taalexemplaren van de website.

## Taalkopieën op meerdere niveaus {#multiple-levels}

De wortels van de taal kunnen ook onder knopen, bijvoorbeeld, door regio worden gegroepeerd, terwijl nog als wortels van taalexemplaren worden erkend.

```text
/content
    |- wknd
        |- language-masters
            |- europe
                |- de
                |- fr
                |- it
                |- es
                ]- pt
            |- americas
                |- en
                |- es
                |- fr
                |- pt
            |- asia
                |- ...
            |- africa
                |- ...
            |- oceania
                |- ...
        |- europe
        |- americas
        |- asia
        |- africa
        |- oceania            
```

>[!NOTE]
>
>Er is slechts één niveau toegestaan. Met de volgende code kan de pagina `es` bijvoorbeeld niet worden omgezet in een taalkopie:
>
>* `/content/wknd/language-masters/en`
>* `/content/wknd/language-masters/americas/central-america/es`
>
> Deze `es` -taalkopie wordt niet gedetecteerd omdat deze zich op 2 niveaus (`americas/central-america` ) van het knooppunt `en` bevindt.

>[!TIP]
>
>In dergelijke opstelling, kunnen de taalwortels om het even welke paginanaam, eerder dan enkel de ISO-code van de taal hebben. AEM controleert altijd eerst het pad en de naam, maar als de paginanaam geen taal identificeert, controleert AEM de eigenschap `cq:language` van de pagina op de taalidentificatie.
