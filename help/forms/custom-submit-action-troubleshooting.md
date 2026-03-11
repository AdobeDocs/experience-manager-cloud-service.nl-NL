---
title: Problemen met 502 fouten oplossen in Aangepaste verzendhandeling voor Adaptieve Forms
description: Leer hoe u 502 foutpagina's kunt identificeren en oplossen die optreden wanneer u aangepaste verzendacties gebruikt in Adaptive Forms (Core Components). Deze gids verklaart gemeenschappelijke oorzaken, zoals unhandled uitzonderingen, en verstrekt resolutiestappen.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
badgeSaas: label="AEM Forms" type="Positive" tooltip="van toepassing op AEM Forms)."
exl-id: a7469926-7059-4aca-90ff-2554d14c3944
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Problemen oplossen: 502 foutpagina in Aangepaste verzendhandeling

Wanneer het werken met Adaptieve Forms (de Componenten van de Kern), kunt u a **502 foutenpagina HTML** ontmoeten na het voorleggen van een vorm die een douane gebruikt voorlegt actie.

## Probleem

**Fout:** A 502 foutenpagina HTML wordt getoond wanneer een douane voorlegt actieservice ontbreekt.

**Reden:** dit gebeurt als de douane voorlegt actie een niet-behandelde fout, bijvoorbeeld, ongeldige wijzer, ongeldige API reactie, of runtime mislukking veroorzaakt.

## Resolutie

Als u de 502-foutpagina wilt voorkomen, plaatst u de logica voor verzending tussen blokken die de fout proberen af te vangen.

Voor gedetailleerde stappen, zie [ een douane aanmaken voorlegt actie voor Adaptieve Forms (de Componenten van de Kern) ](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md).
