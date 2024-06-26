---
title: Hoe kan ik fouten bij het maken van formulieren oplossen?
description: Problemen met het maken van formulieren in AEM Forms as a Cloud Service-omgeving oplossen.
feature: Adaptive Forms
role: User
exl-id: 169ea727-0941-4a1d-bc33-d9fe208b27ab
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Probleem tijdens het publiceren van formulieren{#form-creation-fails}

Nadat gebruikers een update naar AEM Forms as a Cloud Service hebben uitgevoerd `2024.5.16461`:

**Sommige gebruikers** Bij het maken van formulieren kan het volgende probleem optreden: wanneer een gebruiker een formulier maakt, verschijnt het volgende foutbericht in het dialoogvenster Maken:

`A server error occurred. Try again after sometime.`

## Oorzaak {#cause-form-creation-fails}

Het probleem doet zich voor omdat de auteur het formulier zonder **eerst de sjabloon publiceren** erin gebruikt. Dit resulteert in de toevoeging van de `jcr:uuid` en andere beschermde en door het systeem gegenereerde eigenschappen `<template-path>/initial/jcr:content` knoop, veroorzakend mislukkingen in verdere vormverwezenlijking.

## Workaround {#resolution-form-creation-fails}

Voer de volgende stappen uit om het probleem op te lossen:

1. Zorg ervoor dat de sjabloon die u in het formulier gebruikt, niet de `jcr:uuid` en andere door het systeem gegenereerde beschermde eigenschappen op het pad `<template-path>/initial/jcr:content node`.
1. Publish de sjabloon expliciet met behulp van de sjabloonconsole.
1. Wanneer de sjabloon wordt gepubliceerd, kunt u nu nieuwe formulieren maken met de sjabloon.
1. Als de sjabloon die u hebt gebruikt in de toekomstige versies bijwerkt, Publish de sjabloon opnieuw (zoals beschreven in stap 2) om problemen met het maken van formulieren te voorkomen.


<!--

# Issue {#form-creation-fails}

After updating to AEM Forms as a Cloud Service version `2024.5.16461.20240524T172309Z`, When a user publishes a form using an unpublished template, it fails to create a form and shows an error:

`Property is protected: jcr:uuid = 09e0d6be-f619-4405-b021-27eb1c5326d3`

## Solution {#troubleshoot-form-creation-fails}

To resolve the issue, perform the following workaround steps:

1. Publish the template explicitly using the template console.
    
    >[!NOTE]
    > Prior to this step ensure that the (unpublished) template does not have `jcr:uuid` and other system generated properties under the initial content's `jcr:content node`. To sort out it, first, sanitize the template to publish it explicitly.

    >[!NOTE]
    > This action doesn't replicate the initial content node.
1. Now, when your template is published, try creating new forms using the template.
1. If the template is changed in the future, publish it again as mentioned in the step 1.

-->
