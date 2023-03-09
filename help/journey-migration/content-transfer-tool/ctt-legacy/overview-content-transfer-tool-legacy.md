---
title: Overzicht naar het gereedschap Inhoud overbrengen (verouderd)
description: Overzicht van de tool Content Transfer
hide: true
hidefromtoc: true
exl-id: dd031580-e9d7-461e-8689-9bc3dbb2121b
source-git-commit: 3c8035e4db5729f58bae29136a32a0b9944d6a2f
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 56%

---

# Overzicht van het gereedschap Inhoudsoverdracht (verouderd) {#overview-content-transfer-tool}

De tool Content Transfer is door Adobe ontwikkeld. Hiermee kunt u bestaande content van een AEM-broninstantie (On-Premise of AMS) verplaatsen naar de doelinstantie van AEM Cloud Service.

Met de tool worden &#39;principals&#39; (gebruikers of groepen) automatisch overgedragen.

## Fasen in gereedschap Inhoud overbrengen {#phases-content-transfer-tool}

De overdracht van content bestaat uit twee fasen:

1. **Extractie**: Dit heeft betrekking op het extraheren van content van de AEM-broninstantie naar een tijdelijke locatie, de zogenaamde *migratieset*. Een *migratieset* is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie.

   Raadpleeg [Extractieproces in Content Transfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html) voor meer informatie.

   >[!NOTE]
   >Voer het gereedschap Toewijzing gebruiker uit als onderdeel van de extractiefase. Zie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=en) voor meer informatie .

1. **Opname**: Dit verwijst naar het verplaatsen en opnemen van content uit de *migratieset* naar de Cloud Service-doelinstantie.

   Zie [Ingestieproces in inhoudsoverdracht](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html) voor meer informatie .

## Attributen van een migratieset {#attributes-migration-set}

Een migratieset heeft de volgende kenmerken:

* U kunt maximaal tien migratiesets tegelijk maken en onderhouden tijdens de activiteit voor inhoudsoverdracht.
* Elke migratieset moet een unieke naam hebben.
* Als een migratieset langer dan 30 dagen inactief is, wordt deze automatisch verwijderd.
* Wanneer u een migratieset maakt, wordt deze gekoppeld aan een specifieke omgeving. U kunt alleen content opnemen in een auteur- of publicatie-instantie van dezelfde omgeving.


De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

In de extractiefase wordt ***boven*** een bestaande migratieset, de *overschrijven* Deze optie moet zijn uitgeschakeld. Raadpleeg [Extractie aanvullen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=en#top-up-extraction-process) voor meer informatie.

Als u in de opnamefase de deltacontent boven op de huidige content wilt toepassen, moet de optie voor *wissen* zijn uitgeschakeld. Zie [Opname aanvullen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en#top-up-ingestion-process) voor meer informatie.

## Volgende functies {#whats-next}

Nadat u over het Hulpmiddel van de Overdracht van de Inhoud en zijn overzicht hebt geleerd, kan dit hulpmiddel worden gebruikt om bestaande inhoud over van een bron AEM instantie (op-gebouw of AMS) aan de instantie van doelAEM Cloud Service te bewegen. Controleren [Voorwaarden voor het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en).
