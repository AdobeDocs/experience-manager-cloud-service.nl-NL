---
title: Inleiding tot Sandbox-programma's
description: Leer welke sandboxprogramma's verschillen van productieprogramma's.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: 05cba12cdd14c2e29f6a471047ce95fcf720abc4
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Inleiding tot Sandbox-programma&#39;s {#sandbox-programs}

Leer welke sandboxprogramma&#39;s verschillen van productieprogramma&#39;s.

## Inleiding {#introduction}

Een zandbakprogramma wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, of het bewijs van concepten (POCs) te dienen en daarom niet bedoeld om levend verkeer te vervoeren.

Een sandboxprogramma is een van de twee soorten programma&#39;s die beschikbaar zijn in AEM Cloud Service, terwijl het andere een [productieprogramma.](introduction-production-programs.md) Raadpleeg het document [Programma&#39;s en programmatypen begrijpen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) voor meer informatie over programmatypen.

## Automatisch maken {#auto-creation}

Sandboxprogramma&#39;s maken automatisch ontwerp mogelijk. Telkens wanneer u een nieuw sandboxprogramma maakt, wordt Cloud Manager automatisch:

* Hiermee voegt u AEM Sites en AEM Assets toe als oplossingen in uw programma.
* Stelt een projectgit-opslagplaats in met een voorbeeldproject dat is gebaseerd op de [AEM Projectarchetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)
* Maakt een ontwikkelomgeving.
* Creeert een niet-productiepijpleiding die aan de ontwikkelomgeving opstelt.

Een sandboxprogramma heeft slechts één ontwikkelomgeving.

## Beperkingen en voorwaarden {#limitations}

Omdat ze niet voor levend verkeer bedoeld zijn, hebben sandboxprogramma&#39;s bepaalde beperkingen en voorwaarden voor hun gebruik, waardoor ze van productieprogramma&#39;s worden onderscheiden.

### Geen actief verkeer {#live-traffic}

Sandboxprogramma&#39;s zijn niet bedoeld voor het vervoer van levend verkeer en zijn daarom niet onderworpen aan [AEM as a Cloud Service verbintenissen.](https://www.adobe.com/legal/service-commitments.html)

### Geen automatische schaling {#auto-scaling}

De milieu&#39;s die in een zandbakprogramma worden gecreeerd worden niet gevormd voor auto-schrapen. Daarom zijn deze omgevingen niet geschikt voor het testen van prestaties of belasting.

### Geen aangepaste domeinen of IP-Lijsten van gewenste personen {#ip-allow}

Aangepaste domeinen en IP-lijsten van gewenste personen zijn niet beschikbaar in sandboxprogramma&#39;s.

### Geen geavanceerde netwerken {#advanced-networking}

[Geavanceerde netwerkfuncties](/help/security/configuring-advanced-networking.md) (bv. zelfbediende levering van VPN, niet-standaardhavens, specifieke IP adressen van de uitgang, enz.) zijn niet beschikbaar in sandboxprogramma&#39;s.

### Handmatige AEM {#updates}

AEM updates worden niet automatisch doorgegeven aan sandboxprogramma&#39;s, maar kunnen handmatig worden toegepast op de omgevingen in uw sandboxprogramma.

* Een handupdate kan slechts worden in werking gesteld wanneer het gerichte milieu een behoorlijk gevormde pijpleiding heeft.
* Een handmatige update van een productie- of testomgeving werkt automatisch de andere bij. De Production+Stage-omgeving moet zich op dezelfde AEM bevinden.

Raadpleeg het document [AEM versies bijwerken](/help/implementing/deploying/aem-version-updates.md) voor meer informatie .

Raadpleeg het document [Omgeving bijwerken](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) voor meer informatie over het bijwerken van een omgeving.

### Sluimerstand en verwijdering {#hibernation}

De omgevingen in een sandboxprogramma worden na 8 uur inactiviteit automatisch genormaliseerd. Na de hiberatie kunnen ze handmatig worden gedehiberneerd.

Sandbox-programma&#39;s worden verwijderd na 6 maanden van continuhibernatiemodus, waarna ze opnieuw kunnen worden gemaakt.

Zie [Sluiende en ontsmette zandbakomgevingen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md) voor meer informatie .
