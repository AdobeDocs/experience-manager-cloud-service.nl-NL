---
title: Domein verifiëren
description: Domein verifiëren
translation-type: tm+mt
source-git-commit: d2a98cf340dc755407250a9a9649addb75ad87d2
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Domein {#verify-domain-name} verifiëren

Een DNS TXT-record machtigt een domein om in een CDN-service te worden gehost. De klant moet een DNS TXT- verslag in de streek tot stand brengen die de Manager van de Wolk machtigt om de Dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze koppeling staat volledig onder de controle van de klant en machtigt Cloud Manager sterk om inhoud van de service aan een domein te leveren. Deze vergunning kan worden verleend en ingetrokken. De TXT-record is specifiek voor het domein en de omgeving van Cloud Manager.

1. Login aan uw Gastheer van het Domein en bezoek de DNS archiefsectie.
1. Kopieer en plak de TXT-vermelding in uw DNS-zone waar uw aangepaste domein zich bevindt, precies zoals deze wordt weergegeven. Als u een &quot;naam&quot;voor uw ingang nodig hebt, geef het `@`.

>[!NOTE]
>Verschillende DNS-opzoekgereedschappen, zoals [DNS-opzoekgereedschap](https://www.ultratools.com/tools/dnsLookup), kunnen worden gebruikt om TXT-opzoekopdrachten op te zoeken en te bepalen of de TXT-record ontbreekt of onjuist is.
