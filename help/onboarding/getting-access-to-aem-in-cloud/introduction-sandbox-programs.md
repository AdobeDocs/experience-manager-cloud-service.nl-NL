---
title: 'Inleiding tot Sandbox-programma''s '
description: Inleiding tot Sandbox-programma's
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: 1ecadc0d2b45ee8c94af8d91b35dbd40b08e89b5
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Inleiding tot Sandbox-programma&#39;s {#sandbox-programs}

## Inleiding {#introduction}

Een Sandbox-programma is een van de twee soorten programma&#39;s die beschikbaar zijn in AEM Cloud Service, terwijl een ander programma een productieprogramma is.

Een zandbak wordt typisch gecreeerd om de doeleinden van opleiding, lopende demo&#39;s, enablement, of van het Bewijs van Concept (POC) te dienen. Ze zijn niet bedoeld om levend verkeer te vervoeren. Zij zijn niet onderworpen aan [AEM als Cloud Service Verbintenissen](https://www.adobe.com/legal/service-commitments.html).

De omgevingen die in een sandbox worden gemaakt, zijn niet geconfigureerd voor automatisch schalen. Daarom zijn deze omgevingen niet geschikt voor het testen van prestaties of belasting.

Sandboxprogramma&#39;s omvatten [!DNL Sites] en [!DNL Assets] en worden automatisch gevuld met een Git-opslagplaats, een ontwikkelomgeving en een niet-productiepijplijn.  De gegevensopslagplaats van het Git wordt bevolkt met een steekproefproject dat op het AEM archetype van het Project wordt gebaseerd.

Verwijs naar [Begrijpend Programma en Types van Programma](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) om meer over de Types van Programma te leren.

### Attributen van Sandbox-programma&#39;s {#attributes-sandbox}

Sandbox-programma&#39;s hebben de volgende kenmerken:

1. **Programma maken:** het maken van het Sandbox-programma omvat automatisch:
   * opstelling van project met steekproefcode en inhoud
   * totstandbrenging van een ontwikkelomgeving
   * de aanleg van een niet-productiepijpleiding die naar ontwikkelomgeving (master tak die aan ontwikkelomgeving opstelt)

1. **Oplossingen:** Sandbox-programma&#39;s bevatten AEM  [!DNL Sites] en  [!DNL Assets].

1. **AEM Updates:** AEM updates kunnen handmatig worden toegepast op omgevingen in een Sandbox-programma en worden niet automatisch doorgeduwd.
Raadpleeg [Updates AEM naar Sandbox-omgevingen](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md#aem-updates-sandbox) voor meer informatie.

1. **Sluimerstand:** omgevingen in een Sandbox-programma worden automatisch genummerd als er gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Sandboxen worden in het hibernatieknooppunt geplaatst na 8 uur inactiviteit, waarna ze kunnen worden gedehiberneerd. Gesamberde omgevingen kunnen handmatig worden gedehiberteerd.
Raadpleeg [Sluimerende en Shibernating Sandbox-omgevingen](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md) voor meer informatie.

1. **Verwijderen**: Sandboxen worden verwijderd na 6 maanden van continuhibernatiemodus, waarna ze opnieuw kunnen worden gemaakt.
