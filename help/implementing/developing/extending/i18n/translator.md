---
title: Internationalisatie van UI-tekenreeksen
description: AEM biedt een console voor het beheer van de verschillende vertalingen van teksten die worden gebruikt in de gebruikersinterface van componenten.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 14a6516872f842d099b902b9f633b1d6f984266d
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---


# Woordenboeken beheren met Vertaler{#using-translator-to-manage-dictionaries}

AEM biedt een console voor het beheer van de verschillende vertalingen van teksten die worden gebruikt in de gebruikersinterface van componenten. Deze console is beschikbaar op:

`https://<hostname>:<port-number>/libs/cq/i18n/gui/translator.html`

Gebruik het gereedschap Vertaler voor het beheren van Engelse tekenreeksen en de bijbehorende vertalingen. De woordenboeken worden bijvoorbeeld gemaakt in de opslagplaats `/apps/myproject/i18n` .

Het gereedschap Vertaler en de woordenboeken die u beheert, zijn bedoeld voor het weergeven van de gebruikersinterface van de component in verschillende talen. Als u pagina&#39;s wilt vertalen, zie [ Vertaal Inhoud voor Meertalige Plaatsen ](/help/sites-cloud/administering/translation/overview.md).

## Woordenboek maken {#creating-a-dictionary}

Ontwikkelaars kunnen i18n-woordenboeken maken in AEM om gelokaliseerde componenttekenreeksen te beheren. Woordenboeken maken doorgaans deel uit van componentcode in `/apps` . Hier volgt een voorbeeld van de AEM WKND-code met één sleutel/waardepaar dat in alle WKND-componenten wordt gebruikt.

```
{
  "&copy; {0} WKND Site Site. All rights reserved." : "&copy; {0} WKND Site Site. Tous droits réservés."
}
```

Ontwikkelaars kunnen aanvullende woordenboeken maken door een basisknooppunt (`sling:Folder`) toe te voegen voor een nieuw woordenboek waarin taaldefinities voor componenttekenreeksen staan.

```shell
/apps/myProject/i18n [sling:Folder]
    - de.json [nt:file] [mix:language]
        + jcr:language = de
    - fr.json [nt:file] [mix:language]
        + jcr:language = fr
```

>[!NOTE]
>
>Dit is de structuur van de [ Verschuivende i18n module ](https://sling.apache.org/site/internationalization-support.html).

Zodra gecreeerd in een AEM bewaarplaats GitHub, kunnen de woordenboeken via een AEM [ CI/CD pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) worden opgesteld.

## Locaties woordenboek {#dictionary-locations}

Het staat ontwikkelaars vrij om een brontaalwoordenboek te maken in `/apps` of `/content/cq:i18n` . Als u begint met AEM voorbeeldcode van het type archetype, bevinden de oorspronkelijke woordenboeken zich gewoonlijk in het `/apps` -pad. Als het de bedoeling is om overeenkomstige woordenboektaalexemplaren ook in `/apps` op te slaan, dan moeten die taalexemplaren manueel worden gecreeerd en door ontwikkelaars in componentencode worden gehandhaafd.

Het nieuwe vertaalproces voor AEM runtime voor i18n-woordenboeken maakt ook vertaalde woordenboeken in `/content/cq:i18n/<projectName>` , ongeacht of het bronwoordenboek is opgeslagen in `/apps` of `/content` .

Bij het bepalen van de plaats waar i18n-woordenboeken, bron- en taalkopieën moeten worden gevonden, moeten de volgende criteria worden gehanteerd:

* `/apps`
   * standaardlocatie voor woordenboeken met componenttekenreeksvertalingen, volgens AEM archetype en WKND-voorbeeldcode
   * hoogste het teruggeven orde, per het Verdelen ([ de Hiërarchieën van het Onderzoek van de Bundel van het Middel ](https://sling.apache.org/documentation/bundles/internationalization-support-i18n.html#resourcebundle-hierarchies))
   * maar het is niet mogelijk om woordenboeken tijdens runtime te bewerken of te vertalen, aangezien `/apps` in AEM as a Cloud Service-omgevingen onveranderlijk is

* `/content/cq:i18n`
   * alternatieve locatie voor i18n-woordenboeken als
      * runtime vertaling van woordenboeken is vereist
      * de mogelijkheid om een woordenboek tijdens runtime te bewerken is vereist
   * standaardlocatie waar bij het vertalen van het runtimewoordenboek taalkopieën worden gemaakt.

Omdat `/apps` altijd de waarde `/content` vervangt in de rendervolgorde Verschuiven, is het belangrijk om in gedachten te houden dat woordenboeken met identieke sleutel/waardeparen niet gelijktijdig in `/apps` en `/content/cq:i18n` mogen bestaan, aangezien het woordenboek in `/content/cq:i18n` nooit zal worden gebruikt voor rendering. Als er al een kopie van een woordenboektaal (de vertaalbestemming) in `/apps` bestaat en het doel is deze tijdens runtime in AEM as a Cloud Service te vertalen, moet de oorspronkelijke woordenboektaalkopie in `/apps` naar `/content/cq:i18n` worden verplaatst of in `/apps` worden verwijderd en automatisch opnieuw worden gemaakt in `/content/cq:i18n` door het bronwoordenboek te vertalen. Met dit vertaalproces worden de taalkopieën automatisch gemaakt in `/content/cq:i18n` .

## Automatisch woordenboek maken {#automatic-creation}

Voor AEM pagina&#39;s en ervaringsfragmenten die AEM kerncomponenten bevatten, doorzoekt het nieuwe woordenboekvertaalproces ook die pagina&#39;s of ervaren fragmenten voor componenten en componenttekenreeksen die moeten worden vertaald. Het systeem maakt vervolgens automatisch overeenkomstige kopieën van nieuwe woordenboektalen in `/content/cq:i18n` . Dit is niet van toepassing op inhoudsfragmenten, aangezien het zuivere, gestructureerde inhoud zonder het gebruik van AEM kerncomponenten betreft.

## Woordenboek exporteren {#exporting-a-dictionary}

Hoewel runtimevertaling van i18n-woordenboeken op `/apps` - of `/libs` -locaties niet mogelijk is in AEM as a Cloud Service omdat deze locaties onveranderlijk zijn, kunnen deze woordenboeken tijdens runtime wel worden geëxporteerd voor asynchrone vertaling buiten AEM.

U kunt als volgt de tekenreeksen voor de brontaal van een woordenboek exporteren naar een XLIFF-bestand:

1. Het gereedschap Vertalen openen `http://<host>:<port>/libs/cq/i18n/gui/translator.html`

   >[!NOTE]
   >
   >Het gereedschap is alleen beschikbaar via deze URL en is niet toegankelijk via de gebruikersinterface van het AEM product.

1. Gebruik het vervolgkeuzemenu Woordenboeken om het woordenboek te selecteren dat u wilt exporteren.
1. Klik op XLIFF-omzetting exporteren en Exporteer vervolgens de volledige `<locale>` xliff.

## Woordenboek importeren {#importing-a-dictionary}

Een XLIFF-bestand importeren in een woordenboek om de inhoud van het woordenboek te vullen:

1. Het gereedschap Vertalen openen `http://<host>:<port>/libs/cq/i18n/gui/translator.html`
1. Klik op Importeren en vervolgens op XLIFF-translaties.
1. Selecteer het te importeren bestand en klik op OK.
