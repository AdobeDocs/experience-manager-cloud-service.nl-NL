---
title: Aanpassing gedetecteerd
description: Aanpassing gedetecteerd
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 2%

---


# Aanpassing gedetecteerd {#cust-pattern}

Op deze pagina vindt u een beschrijving van de patrooncode die is aangetroffen bij Aanpassing.

## Achtergrond {#background}

Deze patrooncode wordt gebruikt om aanpassingen te identificeren die aan de instantie AEM zijn aangebracht. Omdat AEM vaak wordt aangepast, geeft dit patroon niet noodzakelijkerwijs aan dat er een probleem is. Het identificeert een verslag van aanpassingen zodat zij met betrekking tot hun effect op verbeteringsplannen kunnen worden beoordeeld.

Tot de gevonden aanpassingen behoren:

* Klantcode (pakketten) en configuraties
* Pakketten van derden
* Integraties met services van derden
* Niet-standaard eiken-indexen

## Patroongegevens {#pattern-data}

De volgende objecten worden opgenomen in de JSON-weergave van het patroon:

* **item.message**: verwijst naar het bericht van het patroon.
* **item.context**: verwijst naar aanvullende informatie over de overzichtsinformatie:
   * *type*: aanpassing.gedetecteerd.
   * *gegevens*: Een JSON-object met de gegevens die de aanpassing beschrijven

### Mogelijke gevolgen en risico&#39;s {#possible-implications}

Niet van toepassing.

### Mogelijke oplossingen  {#possible-solutions}

Niet van toepassing.
