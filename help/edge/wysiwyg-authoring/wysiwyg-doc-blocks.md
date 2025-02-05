---
title: Blokken voor WYSIWYG en op documenten gebaseerde authoring
description: Leer hoe u blokken kunt maken die kunnen worden gebruikt voor zowel WYSIWYG-authoring als documentgebaseerd schrijven.
feature: Edge Delivery Services
role: User
exl-id: f039c70a-e1a0-4fcc-8f42-dfa0f8bb3764
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Blokken voor WYSIWYG en op documenten gebaseerde authoring {#wysiwyg-and-doc-blocks}

Leer hoe u blokken kunt maken die kunnen worden gebruikt voor zowel WYSIWYG-authoring als documentgebaseerd schrijven.

## Overzicht {#overview}

Voor bepaalde projecten, kunt u zowel [ het auteursrecht van WYSIWYG willen steunen gebruikend de Universele Redacteur ](/help/edge/wysiwyg-authoring/authoring.md) evenals [ op document-gebaseerde het schrijven ](/help/edge/docs/authoring.md). Als u de ontwikkelingstijd wilt beperken en dezelfde ervaring met sites wilt garanderen, kunt u één set blokken maken die beide gebruiksgevallen ondersteunen.

Hiervoor moet u dezelfde methode voor het modelleren van inhoud gebruiken voor zowel uw WYSIWYG-ontwerpinstellingen als uw op documenten gebaseerde ontwerpinstellingen.

## Benadering {#approach}

In WYSIWYG authoring in AEM, verklaart u [ een model ](/help/edge/wysiwyg-authoring/content-modeling.md) en verstrekt het noemen overeenkomsten. Gegevens worden vervolgens met Edge Delivery gerenderd in blokstructuren die vergelijkbaar zijn met tabellen, op dezelfde manier als wanneer de tabel handmatig zou zijn gemaakt met behulp van op documenten gebaseerde authoring.

Om dit te bereiken, worden bepaalde veronderstellingen gemaakt zoals voor een eenvoudig blok als een gummetje dat alle eigenschappen en groepen eigenschappen worden weergegeven in 1..n rijen met elk één kolom. Voor blokken met 1..In items (zoals carrousel en kaarten) worden de items na deze rijen toegevoegd met telkens één rij en een kolom voor elke eigenschap/groep eigenschappen.

Als u dezelfde aanpak kiest voor op documenten gebaseerde ontwerpen, kunt u uw WYSIWYG-blokken opnieuw gebruiken.
