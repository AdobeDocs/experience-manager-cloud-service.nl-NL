---
title: Problemen met 502 fouten oplossen in Aangepaste verzendhandeling voor Adaptieve Forms
description: Leer hoe u 502 foutpagina's kunt identificeren en oplossen die optreden wanneer u aangepaste verzendacties gebruikt in Adaptive Forms (Core Components). Deze gids verklaart gemeenschappelijke oorzaken, zoals unhandled uitzonderingen, en verstrekt resolutiestappen.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Problemen oplossen: 502 foutpagina in Aangepaste verzendhandeling

Wanneer het werken met Adaptieve Forms (de Componenten van de Kern), kunt u a **502 foutenpagina HTML** ontmoeten na het voorleggen van een vorm die een douane gebruikt voorlegt actie.

## Probleem

**Fout:** A 502 foutenpagina HTML wordt getoond wanneer een douane voorlegt actieservice ontbreekt.

**Reden:** dit gebeurt als de douane voorlegt actie een niet-behandelde fout, bijvoorbeeld, ongeldige wijzer, ongeldige API reactie, of runtime mislukking veroorzaakt.

## Resolutie

Als u de 502-foutpagina wilt voorkomen, plaatst u de logica voor verzending tussen blokken die de fout proberen af te vangen.

Voor gedetailleerde stappen, zie [&#x200B; een douane aanmaken voorlegt actie voor Adaptieve Forms (de Componenten van de Kern) &#x200B;](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md).
