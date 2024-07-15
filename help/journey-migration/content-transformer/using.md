---
title: Inhoudstransformator gebruiken
description: Leer hoe u de inhoudsstructuur kunt transformeren ter voorbereiding op de migratie naar AEM as a Cloud Service.
exl-id: 40516ff7-5686-42e6-bdd1-c9c6de432b09
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---

# Inhoudstransformator gebruiken {#using-ct}

## Belangrijke overwegingen voor het gebruik van Content Transformer {#imp-considerations-ct}

Volg de onderstaande sectie om de belangrijke overwegingen voor het gebruik van de Content Transformer (CT) te begrijpen:

* Als u de Content Transformer wilt gebruiken, moet u eerst de Analysator voor aanbevolen procedures uitvoeren in uw Adobe Experience Manager-omgeving (AEM).
* Hoewel u de Transformer van de Inhoud op uw milieu van de Productie kunt in werking stellen, adviseert men dat u de Transformer van de Inhoud op een kloon van uw milieu van de Productie in werking stelt. Nog belangrijker, moet u ervoor zorgen dat BPA en CT op het zelfde milieu in werking worden gesteld.
* U moet beheerder op het milieu zijn waar u de Transformer van de Inhoud wilt in werking stellen.
* Elke bewerking die de broninhoud kan wijzigen ( verplaatsen/verwijderen/hernoemen ), maakt standaard een back-uppakket van de bronpaden onder `/etc/packages/content-transformation` vóór de transformatie. Hoewel elk dialoogvenster voor bewerkingen een optie bevat om het maken van back-uppakketten uit te schakelen of in te schakelen, wordt het ten strengste aanbevolen om het maken van pakketten altijd in te schakelen.
* Elke pagina in de Content Transformer is zo geconfigureerd dat er maximaal 50 bevindingen worden vermeld. Op een bepaald moment kunnen maximaal 50 bevindingen worden omgezet. Dit wordt gedaan om een chronologiereactie op UI te verstrekken.

## Beschikbaarheid {#availability-ct}

De transformator van de Inhoud wordt gebundeld met het [ Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) dat als zip dossier van het Portaal van de Distributie van de Software kan worden gedownload. U kunt het pakket installeren via Package Manager op uw AEM.

>[!NOTE]
>De Content Transformer is beschikbaar met Content Transfer Tool v2.0.20 of hoger.

## De inhoudstransformator openen {#opening-ct}

1. Meld u als beheerder aan bij de bron AEM instantie en ga naar de startpagina: https://host:port/aem/start.html.
1. Ga naar Gereedschappen > Bewerkingen > Inhoud migreren

   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-1.png)

   >[!NOTE]
   > Zorg ervoor dat u het BPA-rapport eerder hebt uitgevoerd en controleer dit met de URL http://host:port/apps/best-practices-analyzer/content/BestPracticesReport.html

1. Klik de kaart met titel **Transformer van de Inhoud voor BPA- rapport**

   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-2.png)

   Hieronder ziet u een voorbeeld van hoe de pagina Overzicht van Content Transformer eruit zal zien als het maken van het BPA-rapport is gelukt en als er inhoudgerelateerde problemen zijn aangetroffen.

   De resterende tijd voor het BPA-verslag staat vermeld op de zijspoor. U wordt aangeraden de inhoudstransformator met het meest recente BPA-rapport uit te voeren om te voorkomen dat er bevindingen met betrekking tot inhoud ontbreken.

   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-3.png)

1. U kunt de problemen filteren op basis van `Pattern Code` , `Subtype` , `Importance` en `Source` .

   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-4.png)

1. U kunt alle of specifieke problemen selecteren en deze verplaatsen, verwijderen of hernoemen om ze op te lossen. De wegen van de douane kunnen ook worden toegevoegd gebruikend **voegt de knoop van Wegen** op de hoger-juiste hoek toe.

   >[!NOTE]
   > Wanneer u de verplaatsingsbewerking gebruikt, wordt aangeraden alle paden naar slechts één map te verplaatsen (bijvoorbeeld onder `/etc/packages/content-transformation/paths` ). Wanneer de back-uppakketten zijn geïnstalleerd om de instantie terug te brengen naar de oorspronkelijke staat, kan de map ( `/etc/packages/content-transformation/paths` ) worden verwijderd met behulp van de verwijderbewerking om de grootte van de opslagplaats te reduceren.

   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-5.png)
   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-6.png)

   >[!NOTE]
   > Om het even welke verrichting die de broninhoud (`move` kan veranderen/ `remove`/ `rename`) zal door gebrek tot een reservepakket van de bronwegen onder `/etc/packages/content-transformation` vóór de transformatie leiden. Hoewel elk dialoogvenster voor bewerkingen een optie bevat om het maken van back-uppakketten uit te schakelen of in te schakelen, wordt het ten strengste aanbevolen om het maken van pakketten altijd in te schakelen.

1. Hieronder ziet u een voorbeeld van een back-uppakket dat is gemaakt voor het verplaatsen van paden. Klik op Installeren om de bronpaden terug te halen. De installatie brengt alleen de bronpaden terug naar hun oorspronkelijke locatie en verwijdert niet de paden waar ze tijdens de transformatie zijn verplaatst. Om de wegen in de bewogen plaats te schrappen, **te klikken voegt de knoop van Wegen** toe om de plaats (bijvoorbeeld, `/etc/packages/content-transformation/paths`) toe te voegen, de plaats te selecteren en **te klikken verwijdert**.

   >[!CAUTION]
   > Verwijder `/etc/packages/content-transformation` niet omdat dit de locatie is waar de back-uppakketten zich bevinden. Alleen als u zeker weet dat u deze pakketten niet meer nodig hebt, kunt u deze locatie verwijderen om de grootte van de opslagplaats te reduceren.

   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-7.png)
   ![afbeelding](/help/journey-migration/content-transformer/assets/ct-8.png)
