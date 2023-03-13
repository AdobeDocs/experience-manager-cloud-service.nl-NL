---
title: Inhoud voorbereiden voor vertaling
description: Leer hoe u inhoud voorbereidt voor vertaling.
feature: Language Copy
role: Admin
exl-id: afc577a2-2791-481a-ac77-468011e4302e
source-git-commit: 47910a27118a11a8add6cbcba6a614c6314ffe2a
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 0%

---

# Inhoud voorbereiden voor vertaling {#preparing-content-for-translation}

Meertalige websites bieden over het algemeen inhoud in meerdere talen. De site is gemaakt in één taal en wordt vervolgens vertaald in andere talen. In het algemeen bestaan meertalige sites uit vertakkingen van pagina&#39;s, waarbij elke vertakking de pagina&#39;s van de site in een andere taal bevat.

>[!TIP]
>
>Als u nog geen ervaring hebt met het vertalen van inhoud, raadpleegt u onze [Sites Translation Journey,](/help/journey-sites/translation/overview.md) Dit is een geleid pad door uw AEM Sites-inhoud te vertalen met de krachtige vertaalgereedschappen van AEM, ideaal voor mensen zonder AEM of vertaalervaring.

De [WKND-zelfstudiesite](/help/implementing/developing/introduction/develop-wknd-tutorial.md) bevat verschillende taalvertakkingen en gebruikt de volgende structuur:

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

De taalkopie waarvoor u oorspronkelijk site-inhoud hebt gemaakt, is de master taal. De master taal is de bron die in andere talen wordt vertaald.

Elke taalvertakking van een site wordt een taalkopie genoemd. De hoofdpagina van een taalkopie, ook wel de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. Bijvoorbeeld: `/content/wknd/fr` Dit is de hoofdtaal van de Franse taalkopie. Taalkopieën moeten een [correct geconfigureerde taalhoofdmap](preparation.md#creating-a-language-root) zodat de juiste taal wordt gebruikt wanneer vertalingen van een bronsite worden uitgevoerd.

Gebruik de volgende stappen om uw site voor te bereiden op vertaling:

1. Maak de hoofdmap van de master taal. De hoofdtaalsite van de Engelse WKND-demosite is bijvoorbeeld `/content/wknd/language-masters/en`. Zorg ervoor dat de taalwortel correct volgens de informatie in wordt gevormd [Een hoofdmap voor talen maken](preparation.md#creating-a-language-root).
1. Ontwerp de inhoud van uw master taal.
1. Maak de hoofdmap van elke taalkopie voor uw site. De Franse taalkopie van de WKND-voorbeeldsite is bijvoorbeeld `/content/wknd/language-masters/fr`.

Nadat u de inhoud hebt voorbereid voor vertaling, kunt u automatisch ontbrekende pagina&#39;s maken in uw taalkopieën en bijbehorende vertaalprojecten. (Zie [Een vertaalproject maken](managing-projects.md).) Voor een overzicht van het vertaalproces van de inhoud in AEM raadpleegt u [Inhoud vertalen voor meertalige websites](overview.md).

## Een hoofdmap voor talen maken {#creating-a-language-root}

Maak een taalhoofdmap als de hoofdpagina van een taalkopie die de taal van de inhoud identificeert. Nadat u de taalwortel creeert, kunt u vertaalprojecten tot stand brengen die het taalexemplaar omvatten.

Als u de hoofdtaal wilt maken, maakt u een pagina en gebruikt u een ISO-taalcode als waarde voor de **Naam** eigenschap. De taalcode moet een van de volgende notaties hebben:

* `<language-code>` - De ondersteunde taalcode is bijvoorbeeld een tweelettercode zoals gedefinieerd in ISO-639-1 `en`.
* `<language-code>_<country-code>` of `<language-code>-<country-code>` - De ondersteunde landcode is bijvoorbeeld een tweelettercode in kleine letters of hoofdletters, zoals gedefinieerd in ISO 3166. `en_US`, `en_us`, `en_GB`, `en-gb`.

U kunt beide indelingen gebruiken op basis van de structuur die u voor uw globale site hebt gekozen. De hoofdpagina van de Franse taalkopie van de WKND-site heeft bijvoorbeeld `fr` als de **Naam** eigenschap. De **Naam** eigenschap wordt gebruikt als de naam van het paginaknooppunt in de repository en bepaalt daarom het pad van de pagina (`http://<host>:<4502>/content/wknd/language-masters/fr.html`).

1. Navigeer naar sites.
1. Klik of tik op de site waarvoor u een taalkopie wilt maken.
1. Klikken of tikken **Maken** en klik of tik op **Pagina**.

   ![Pagina maken](../assets/create-page.png)

1. Selecteer de paginasjabloon en klik of tik op **Volgende**.
1. In de **Naam** veldtype de landcode in het formaat `<language-code>` of `<language-code>_<country-code>`bijvoorbeeld `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Typ een titel voor de pagina.

   ![Hoofdpagina van taal maken](../assets/create-language-root.png)

1. Klikken of tikken **Maken**. Klik of tik in het bevestigingsdialoogvenster op **Gereed** om naar de console van Plaatsen terug te keren, of **Openen** om de taalkopie te openen.

## De status van taalwortels bekijken {#seeing-the-status-of-language-roots}

AEM biedt een **Verwijzingen** rail die een lijst toont van taalwortels die zijn gecreeerd.

![Taalwortels](../assets/language-roots.png)

Gebruik de volgende procedure om de taalkopieën voor een pagina te bekijken met de [spoorkiezer.](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)

1. Selecteer in de siteconsole een pagina van de site en klik of tik op **Verwijzingen**.

   ![Open Reference rail](../assets/opening-references-rail.png)

1. Klik of tik in de referentiespoor **Taalkopieën**. De spoorstaaf toont de taalexemplaren van de website.

## Taalkopieën op meerdere niveaus {#multiple-levels}

Taalwortels kunnen ook worden gegroepeerd onder knooppunten, bijvoorbeeld per regio, terwijl ze nog steeds worden herkend als wortels van taalkopieën.

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
>Er is slechts één niveau toegestaan. Het volgende staat bijvoorbeeld het `es` pagina die moet worden omgezet in een taalkopie:
>
>* `/content/wknd/language-masters/en`
>* `/content/wknd/language-masters/americas/central-america/es`
>
> Dit `es` De taalkopie wordt niet gedetecteerd omdat deze twee niveaus heeft (`americas/central-america`) weg van de `en` knooppunt.

>[!TIP]
>
>In dergelijke opstelling, kunnen de taalwortels om het even welke paginanaam, eerder dan enkel de ISO-code van de taal hebben. AEM zal altijd het pad en de naam eerst controleren, maar als de paginanaam geen taal identificeert, zal AEM de `cq:language` eigenschap van de pagina voor de taalidentificatie.
