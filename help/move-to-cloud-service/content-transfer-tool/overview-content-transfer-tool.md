---
title: Overzicht van de tool Content Transfer
description: Overzicht van de tool Content Transfer
translation-type: tm+mt
source-git-commit: f2a6b67e3673bf6dfeb63d445074f6d1e05971cf
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 100%

---


# Overzicht {#overview-content-transfer-tool}

De tool Content Transfer is door Adobe ontwikkeld. Hiermee kunt u bestaande content van een AEM-broninstantie (On-Premise of AMS) verplaatsen naar de doelinstantie van AEM Cloud Service.

Met de tool worden &#39;principals&#39; (gebruikers of groepen) automatisch overgedragen.

De overdracht van content bestaat uit twee fasen:

1. **Extractie**: Dit heeft betrekking op het extraheren van content van de AEM-broninstantie naar een tijdelijke locatie, de zogenaamde *migratieset*. Een *migratieset* is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie.

   Raadpleeg [Extractieproces in Content Transfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process) voor meer informatie.

2. **Opname**: Dit verwijst naar het verplaatsen en opnemen van content uit de *migratieset* naar de Cloud Service-doelinstantie.

   Raadpleeg [Opnameproces in Content Transfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process) voor meer informatie.

Een *migratieset* heeft de volgende kenmerken:

* Tijdens de contentoverdracht kunnen er maximaal vier migratiesets worden gemaakt en onderhouden.
* Elke migratieset moet een unieke naam hebben.
* Als een migratieset langer dan 30 dagen inactief is geweest, wordt deze automatisch verwijderd.
* Wanneer u een migratieset maakt, wordt deze gekoppeld aan een specifieke omgeving. U kunt alleen content opnemen in een auteur- of publicatie-instantie van dezelfde omgeving.

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
> Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Als u in de extractiefase een bestaande migratieset wilt ***aanvullen***, moet de optie voor *overschrijven* zijn uitgeschakeld. Raadpleeg [Extractie aanvullen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process) voor meer informatie.

Als u in de opnamefase de deltacontent boven op de huidige content wilt toepassen, moet de optie voor *wissen* zijn uitgeschakeld. Zie [Opname aanvullen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process) voor meer informatie.


## Richtlijnen en best practices {#best-practices}

Volg de onderstaande sectie voor meer informatie over richtlijnen en aanbevolen procedures voor het gebruik van de Content Transfer-tool:

* Het is aan te raden om vooraf &#39;data store&#39;-controles uit te voeren op de consistentie van de repository&#39;s om mogelijke problemen te detecteren en het om aantal aanwezige, eerder verwijderde bestanden in de repository te verkleinen.

* Als de AEM Cloud CDN-configuratie (Content Delivery Network) is geconfigureerd met een IP-whitelist, moet u ervoor zorgen dat de IP&#39;s van de bronomgeving worden toegevoegd aan de whitelist, zodat de bronomgeving en de AEM Cloud-omgeving met elkaar kunnen communiceren.

* Tijdens de opnamefase wordt het aanbevolen dat u de modus voor *wissen* inschakelt. Hiermee wordt de bestaande repository (auteur of publicatie) in de AEM Cloud Service-doelomgeving volledig gewist en vervolgens bijgewerkt met de content van de migratieset. Deze modus is veel sneller dan de modus voor niet-wissen, waarbij de migratieset boven op de huidige content wordt toegepast.

* Wanneer alle content is verplaatst, is de juiste projectstructuur in de Cloud Service-omgeving vereist. Anders wordt de content niet correct weergegeven in de Cloud Service-omgeving.
