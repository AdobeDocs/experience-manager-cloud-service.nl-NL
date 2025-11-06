---
title: Inleiding tot Sandbox-programma's
description: Leer welke sandboxprogramma's zijn en hoe ze verschillen van productieprogramma's.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Inleiding tot sandboxprogramma&#39;s {#sandbox-programs}

Leer welke sandboxprogramma&#39;s zijn en hoe ze verschillen van productieprogramma&#39;s.

## Inleiding {#introduction}

Een zandbakprogramma wordt typisch gecreeerd om ten behoeve van opleiding, lopende demo&#39;s, enablement, of het bewijs van concepten (POCs) te dienen en daarom niet bedoeld om levend verkeer te vervoeren.

Een zandbakprogramma is één van de twee soorten programma&#39;s beschikbaar in de Dienst van de Wolk AEM, andere die a [&#x200B; productieprogramma &#x200B;](introduction-production-programs.md) zijn. Zie [&#x200B; Begrijpend Programma&#39;s en de Types van Programma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) om meer over programmatypes te leren.

## Automatisch maken {#auto-creation}

Sandboxprogramma&#39;s maken automatisch ontwerp mogelijk. Wanneer u [&#x200B; een zandbakprogramma &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) creeert, automatisch Cloud Manager:

* Hiermee voegt u AEM Sites, Assets en Edge Delivery Services toe als standaardoplossingen voor uw programma.

  ![&#x200B; Uitgezochte oplossingen en toe:voegen-ons voor een zandbak &#x200B;](assets/sandbox-solutions-add-ons.png)

* Plaatst omhoog een opslagplaats van de projectgit met een steekproefproject dat op [&#x200B; wordt gebaseerd Archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/developing/archetype/overview).
* Maakt een ontwikkelomgeving.
* Creeert een niet-productiepijpleiding die aan de ontwikkelomgeving opstelt.

Een sandboxprogramma heeft slechts één ontwikkelomgeving.

## Gebruiksnotities en -voorwaarden {#usage-notes-conditions}

Omdat ze niet voor levend verkeer bedoeld zijn, hebben sandboxprogramma&#39;s bepaalde beperkingen en voorwaarden voor hun gebruik, waardoor ze zich onderscheiden van productieprogramma&#39;s.

| Beperking/voorwaarde | Beschrijving |
| --- | --- |
| Geen live verkeer | De programma&#39;s van zandbak zijn niet bedoeld om levend verkeer te dragen en zijn daarom niet onderworpen aan [&#x200B; verbintenissen van AEM as a Cloud Service &#x200B;](https://www.adobe.com/legal/service-commitments.html). |
| Geen automatische schaling | De milieu&#39;s die in een zandbakprogramma worden gecreeerd worden niet gevormd voor auto-schrapen. Daarom zijn deze omgevingen niet geschikt voor het testen van prestaties of belasting. |
| Geen aangepaste domeinen of IP-Lijsten van gewenste personen | [&#x200B; de domeinen van de Douane &#x200B;](/help/implementing/cloud-manager/custom-domain-names/introduction.md) en [&#x200B; IP Lijsten van gewenste personen &#x200B;](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) zijn niet beschikbaar in zandbakprogramma&#39;s. |
| Geen publicatiegebieden meer | [&#x200B; extra publiceer gebieden &#x200B;](/help/operations/additional-publish-regions.md) zijn niet beschikbaar in zandbakprogramma&#39;s. |
| Nr. 99,99% SLA | [&#x200B; 99.99% SLA &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) is niet op zandbakprogramma&#39;s van toepassing. |
| Geen geavanceerde netwerken | [&#x200B; Geavanceerde voorzien van een netwerkeigenschappen &#x200B;](/help/security/configuring-advanced-networking.md) (bijvoorbeeld, self-serve levering van VPN, niet-standaardhavens, specifieke IP adressen van de uitgang, etc.) zijn niet beschikbaar in zandbakprogramma&#39;s. |
| Geen automatische AEM-updates | AEM-updates worden niet automatisch doorgegeven aan sandboxprogramma&#39;s, maar kunnen handmatig worden toegepast op de omgevingen in uw sandboxprogramma.<br>・ Een handmatige update kan alleen worden uitgevoerd wanneer de beoogde omgeving een correct geconfigureerde pijplijn heeft.<br>・ Een handmatige update van een productie- of testomgeving werkt automatisch de andere bij. De Production+Stage-omgeving moet zich op dezelfde AEM-release bevinden.<br> zie [&#x200B; de versiupdates van AEM &#x200B;](/help/implementing/deploying/aem-version-updates.md) voor meer details.<br> zie [&#x200B; Bijwerkend Milieu &#x200B;](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) leren hoe te om een milieu bij te werken. |
| Geen technische ondersteuning | Aangezien een sandboxprogramma doorgaans wordt gemaakt voor trainingsdoeleinden, het uitvoeren van demo&#39;s, activering of concepttest, is technische ondersteuning niet beschikbaar voor problemen die worden ervaren in een sandboxprogramma.<br> als u problemen ervaart die tot uw zandbakprogramma&#39;s leiden, zijn deze kwesties binnen het werkingsgebied van technische steun. |
| Sluimerstand en verwijdering | De omgevingen in een sandboxprogramma worden na acht uur inactiviteit automatisch genummerd. Sandbox-omgevingen worden verwijderd na zes opeenvolgende maanden van hibernatie.<br> zie [&#x200B; Sluipende en Sneeuwende Milieu&#39;s van Sandbox &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md) voor meer details over hoe te om milieu&#39;s en automatische zandbakschrapping te ontruimen. |
