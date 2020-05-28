---
title: Overzicht van het gereedschap Inhoud overbrengen
description: Overzicht van het gereedschap Inhoud overbrengen
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Overzicht {#overview-content-transfer-tool}

Het gereedschap Inhoud overbrengen is een door Adobe ontwikkeld programma waarmee u bestaande inhoud van een AEM-broninstantie (on-premise of AMS) naar de AEM Cloud Service-doelinstantie van AEM kunt verplaatsen.

Met dit gereedschap worden ook opdrachtgevers (gebruikers of groepen) automatisch overgedragen.

Er zijn twee fasen gekoppeld aan de overdracht van inhoud:

1. **Extractie**:  Extractie heeft betrekking op het extraheren van inhoud van de AEM-broninstantie naar een tijdelijk gebied, de zogenaamde *migratieset*. Een *migratieset* is een opslaggebied voor de cloud dat door Adobe wordt geleverd om de overgedragen inhoud tijdelijk op te slaan tussen de AEM-broninstantie en de AEM-instantie voor de cloudservice.

   Raadpleeg [Extractieproces in Inhoud overbrengen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process) voor meer informatie.

2. **Inname**: Ingestie verwijst naar het opnemen van inhoud van de *migratie die is ingesteld* in de cloudservice-instantie van het doel.

   Raadpleeg [Ingestieproces in Inhoud overbrengen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process) voor meer informatie.

Een *migratieset* heeft de volgende kenmerken:

* Er kunnen maximaal vier migratiesets worden gemaakt en onderhouden tijdens de activiteit voor inhoudsoverdracht.
* Elke migratieset moet een unieke naam hebben.
* Als een migratieset langer dan 30 dagen inactief is geweest, wordt deze automatisch verwijderd.
* Wanneer u een migratieset maakt, wordt deze gekoppeld aan een specifieke omgeving. U kunt alleen inhoud toevoegen aan een auteur of een publicatie-instantie van dezelfde omgeving.

Het gereedschap Inhoud overbrengen heeft een functie die ondersteuning biedt voor differentiële aanvulling van inhoud, waarbij alleen wijzigingen kunnen worden overgebracht die zijn aangebracht sinds de vorige activiteit voor inhoudsoverdracht.

>[!NOTE]
> Na de eerste overdracht van inhoud wordt aangeraden regelmatig differentiële toevoegingen aan inhoud uit te voeren om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat u live gaat met de Cloud Service.

Als u in de extractiefase een bestaande migratieset wilt ***aanvullen*** , moet de optie *Overschrijven* zijn uitgeschakeld. Raadpleeg [Uitpakken](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process) boven voor meer informatie.

Als u in de invoerfase de deltainhoud boven op de huidige inhoud wilt toepassen, moet de optie *Wissen* zijn uitgeschakeld. Zie [Top Up Ingestie](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process) voor meer informatie.


## Richtlijnen en beste praktijken {#best-practices}

Volg de onderstaande sectie voor meer informatie over richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen:

* Het is aan te raden om vóór de hand controles uit te voeren op de consistentie van de gegevensopslagruimten om mogelijke problemen te detecteren en ook de hoeveelheid afval in de opslagplaats te verminderen.

* Als de configuratie van het Netwerk van de Levering van de Inhoud van de Inhoud van de Auteur AEM Cloud (CDN) wordt gevormd om een whitelist van IPs te hebben dan zou het moeten worden gewaarborgd dat de bronmilieu IPs ook aan whitelist wordt toegevoegd zodat het bronmilieu en het milieu van de Wolk AEM met elkaar kunnen communiceren.

* In de introductiefase wordt aanbevolen de opname uit te voeren met de *sluitermodus* ingeschakeld, waarbij de bestaande opslagruimte (auteur of publicatie) in de AEM Cloud Service-doelomgeving volledig wordt verwijderd en vervolgens wordt bijgewerkt met de gegevens van de migratieset. Deze modus is veel sneller dan de modus Vegen, waarbij de migratieset boven op de huidige inhoud wordt toegepast.

* Nadat de activiteit voor de overdracht van inhoud is voltooid, is de juiste projectstructuur vereist in de Cloud Service-omgeving om ervoor te zorgen dat de inhoud correct wordt weergegeven in de Cloud Service-omgeving.