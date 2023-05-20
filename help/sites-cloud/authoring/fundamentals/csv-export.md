---
title: Exporteren naar CSV
description: Informatie over uw pagina's exporteren naar een CSV-bestand op uw lokale systeem
exl-id: 818e927e-40b2-4ccb-bfb3-88284ad49829
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 28%

---

# Exporteren naar CSV {#export-to-csv}

**CSV-rapport maken** kunt u informatie over uw pagina&#39;s naar een CSV-bestand op uw lokale systeem exporteren.

* Het gedownloade bestand wordt aangeroepen `export.csv`
* De inhoud is afhankelijk van de eigenschappen die u selecteert.
* U kunt het pad samen met de diepte van het exporteren definiëren.

>[!NOTE]
>
>De downloadfunctie en de standaardbestemming van uw browser worden gebruikt.

Met de wizard **CSV-export maken** kunt u het volgende selecteren:

* Te exporteren eigenschappen
   * Metagegevens
      * Naam
      * Gewijzigd
      * Gepubliceerd
      * Sjabloon
      * Workflow
   * Vertaling
      * Vertaald
   * Analyse
      * Paginaweergaven
      * Unieke bezoekers
      * Tijd op pagina
* Diepte
   * Bovenliggend pad
   * Alleen directe kinderen
   * Aanvullende niveaus voor kinderen
   * Niveaus

Het resultaat `export.csv` kan worden geopend in Excel of een andere compatibele toepassing.

Een CSV-export maken:

1. Open de **Sites**-console en ga indien nodig naar de gewenste locatie.
   * De optie **CSV-rapport** maken is beschikbaar wanneer u in de **Sites**-console bladert (in de lijstweergave)
   * Het is een optie van **Maken** vervolgkeuzemenu:

      ![CSV maken, optie](/help/sites-cloud/authoring/assets/csv-create.png)

1. Selecteer op de werkbalk de optie **Maken** en vervolgens **CSV-rapport** om de wizard te openen:

   ![CSV-exportopties](/help/sites-cloud/authoring/assets/csv-options.png)

1. Selecteer de eigenschappen die u wilt exporteren.
1. Selecteer **Maken**.
   ![Resulterende CSV-export in Excel](/help/sites-cloud/authoring/assets/csv-example.png)
