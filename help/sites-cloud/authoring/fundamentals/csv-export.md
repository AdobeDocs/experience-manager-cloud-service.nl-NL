---
title: Exporteren naar CSV
description: Informatie over uw pagina's exporteren naar een CSV-bestand op uw lokale systeem
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Exporteren naar CSV {#export-to-csv}

**Met CSV-rapport** maken kunt u gegevens over uw pagina&#39;s exporteren naar een CSV-bestand op uw lokale systeem.

* Het gedownloade bestand wordt aangeroepen `export.csv`
* De inhoud is afhankelijk van de eigenschappen die u selecteert.
* U kunt het pad samen met de diepte van het exporteren definiëren.

>[!NOTE]
>
>De downloadfunctie en de standaardbestemming van uw browser worden gebruikt.

Met de wizard **CSV-export** maken kunt u het volgende selecteren:

* Te exporteren eigenschappen
   * Metagegevens
      * Naam
      * Gewijzigd
      * Gepubliceerd
      * Sjabloonmodel
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

Het resulterende `export.csv` bestand kan worden geopend in Excel of een andere compatibele toepassing.

Een CSV-export maken:

1. Open de **Sites** -console en navigeer indien nodig naar de gewenste locatie.
   * De optie **CSV-rapport** maken is beschikbaar wanneer u in de **Sites** -console bladert (in de lijstweergave)
   * Dit is een optie in het keuzemenu **Maken** :

      ![CSV maken, optie](/help/sites-cloud/authoring/assets/csv-create.png)

1. Selecteer op de werkbalk de optie **Maken** en vervolgens **CSV-rapport** om de wizard te openen:

   ![CSV-exportopties](/help/sites-cloud/authoring/assets/csv-options.png)

1. Selecteer de eigenschappen die u wilt exporteren.
1. Selecteer **Maken**.
   ![Resulterende CSV-export in Excel](/help/sites-cloud/authoring/assets/csv-example.png)
