---
title: Een interactieve communicatie maken
description: Creeer gepersonaliseerde, gegeven-gedreven mededelingen. Ontdek de belangrijkste functies, instapstappen en praktijkvoorbeelden met handleidingen en zelfstudies.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: c23145c9-078d-4b03-a8f4-2d835cdd1592
source-git-commit: d24e88b545a17e50c1e80e1aedbb1d0adf55f609
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---


# Een interactieve communicatie maken

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

De interactieve mededeling laat u toe om, gepersonaliseerde en interactieve mededelingen tot stand te brengen te beheren en te leveren, met inbegrip van de klantendienst, het factureren, het aan boord gaan documenten, brieven, rekeningsupdates, en meer aan te bieden. Het wordt ontworpen om om het even welk scenario te steunen waar de dynamische, gebruiker-specifieke inhoud de communicatie ervaring over industrieën verbetert.

Stel dat u een bankafschrift, een verzekeringspolis of een nutsrekening naar duizenden klanten moet sturen. Elk bestand heeft dezelfde indeling, maar is gepersonaliseerd. Interactieve communicatie (IC) maakt dat mogelijk efficiënt.

![ vind IC Docu ](/help/forms/interactive-communication/assets/introduction.png)

Het handmatig maken van deze documenten kan tijdrovend zijn en leidt vaak tot inconsistenties, vooral wanneer personalisatie en gegevensintegratie vereist zijn. Met de Interactieve Communicatie Redacteur, kunnen de gebruikers het proces stroomlijnen om Interactieve mededeling tot stand te brengen.

## Vereiste

* [Zorg ervoor dat de auteur lid is van de groep met gebruikers van formulieren](/help/forms/setup-forms-cloud-service.md#configure-users)

## Een interactieve communicatie maken

Kies uit verschillende scenario&#39;s om een Interactieve Mededeling tot stand te brengen, die op het vereiste niveau van hergebruik en gegevensintegratie wordt gebaseerd:

+++ Lege interactieve communicatie maken

Als u een lege interactieve communicatie maakt, kunt u helemaal niets beginnen. Dit is ideaal als u volledige controle wilt hebben over de lay-out, structuur en logica.
Te volgen stappen:

1. Open uw **Adobe Experience Manager (AEM) de instantie van Forms as a Cloud Service**.
1. Navigeer aan **Forms > Forms &amp; Documenten**.
1. Klik **creëren > Interactieve Communicatie**.

   ![ vind IC Docu ](/help/forms/interactive-communication/assets/comm.png)

1. In het verwezenlijking scherm, verlaat het **Malplaatje** gebiedsspatie.

   ![ vind IC Docu ](/help/forms/interactive-communication/assets/create-ic-document.png)

1. Vul andere gegevens in, zoals Titel, Naam, Auteur, enz.
1. Klik **creeer** om Interactieve Communicatie Redacteur UI in te gaan en begin het ontwerpen.
1. Het opent de Redacteur van IC, waar u kunt beginnen ontwerpend uw mededeling.
+++

+++ Creeer een op malplaatje-gebaseerde Interactieve Communicatie

Door een sjabloon te gebruiken, kunt u sneller ontwerpen maken door consistente lay-outelementen zoals kop- en voetteksten, logo&#39;s of standaardopmaak opnieuw te gebruiken.
Sjablonen garanderen de consistentie van merken en besparen tijd voor veelgebruikte communicatietypen. Voer de volgende stappen uit:

1. Open AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **Forms > Forms &amp; Documenten**, klik **creëren > Interactieve Communicatie**.
1. In de creatievorm, **selecteer** een toegelaten malplaatje van dropdown.
1. Vul andere gegevens in, zoals Titel, Naam, Auteur, enz.
1. Klik **creëren** om uw mededeling met de geselecteerde malplaatjestructuur te ontwerpen.
1. Het opent de Redacteur van IC, waar u kunt beginnen ontwerpend uw mededeling.
+++

+++ Creeer een gegeven-Interactieve Communicatie

Met gegevens communicaties worden inhoud automatisch aangepast met behulp van back-endgegevens.
Ideaal voor instructies, facturen of berichten waarbij de structuur constant blijft, maar de gegevens per ontvanger verschillen. Te volgen stappen:

1. Open AEM Forms as a Cloud Service-exemplaar.
1. Ga naar **Forms > Forms &amp; Documenten**, klik **creëren > Interactieve Communicatie**.
1. Op het **Model van de Gegevens van de Vorm** gebied, verbind uw vooraf bepaalde **FDM (het Model van Gegevens van de Vorm)**.
1. Vul andere gegevens in, zoals Titel, Naam, Auteur, enz.
1. Het Model van Gegevens van het gebruik **binnen de redacteur om gebieden aan dynamische gegevens (b.v., klantennaam, saldo, rekeningsaantal) te binden.**
1. Gebruik **Gebieden van de Inhoud, Subforms**, en **Fragmenten** om gegevens te structureren en te herhalen waar nodig.
1. De voorproef die **Voorproef van PDF** gebruikt en voltooit de mededeling voor levering.
1. Het opent de Redacteur van IC, waar u kunt beginnen ontwerpend uw mededeling.

![ vind IC Docu ](/help/forms/interactive-communication/assets/ic-ui.png)
+++

Begin de bouw van Interactieve Mededelingen om uw werkschema&#39;s te stroomlijnen en impacttieve, gebruiker-specifieke ervaringen te leveren.

## Volgende stappen

[ creeer een interactief communicatieMalplaatje ](/help/forms/interactive-communication/create-interactive-communication-template.md)
[ creeer een interactief communicatieFragment ](/help/forms/interactive-communication/create-interactive-communication-fragment.md)
