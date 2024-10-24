---
title: Gesloten gebruikersgroepen migreren
description: Meer informatie over de vereiste speciale voorwaarden om Gesloten gebruikersgroepen in te schakelen na het migreren van inhoud naar Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: c721a8db801602389822222b08ca4ea1fd2293e4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Gesloten gebruikersgroepen migreren {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migratie van gesloten gebruikersgroepen"
>abstract="De migratie van Gesloten Gebruikersgroepen (CUG) vereist momenteel een paar controles en stappen om het na een migratie operationeel te maken."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html" text="Gesloten gebruikersgroepen in AEM"

Momenteel, hebben de Gesloten Gebruikersgroepen (CUG) sommige extra stappen nodig om in het bestemmingsmilieu van een migratie functioneel te zijn. Dit document verklaart het scenario, en de stappen die worden vereist om hen te hebben knopen op de voorgenomen manier beschermen.

## Migratie van gesloten gebruikersgroepen (CUG&#39;s)

De groepen zijn automatisch inbegrepen in een migratie CTT/CAM aan Adobe Experience Manager as a Cloud Service als zij aan de gemigreerde inhoud via ACL van die inhoud of zijn beleidsknoop van de GIDS worden geassocieerd. De verificatie van het bestaan van de groep en haar leden dient te worden uitgevoerd voordat zij live gaan. De groepen die op een beleid van de CUG van verwijzingen worden voorzien worden bedoeld hier als &quot;groepen CUGs.&quot;

Als u CUG&#39;s wilt gebruiken in AEM as a Cloud Service, moeten gebruikers aanwezig zijn op de instantie Auteur en lid zijn van de relevante CUG&#39;s-groepen.  Dit kan worden verwezenlijkt gebruikend pakketten, of als de gebruikers van CUGs gebruikers IMS zijn, kunnen zij reeds aanwezig zijn.  De gebruikers van CUGs moeten dan tot leden van de groepen van AEMCUGs worden gemaakt.

Het gedrag CUG&#39;s inschakelen op de Publish-instantie
1. De CUGs-groepen moeten worden geactiveerd (waardoor ze en hun leden naar de Publish-instantie worden gerepliceerd),
1. *Alle* pagina&#39;s die met beleid CUGs worden beschermd moeten unpublished (om de globale telling van CUGs te ontruimen) zijn, en
1. De pagina&#39;s die met het beleid van CUGs worden beschermd moeten dan worden gepubliceerd (dat de instantie van Publish toelaat en het beleid registreert).
1. Nadat alle pagina&#39;s zijn gepubliceerd, controleert u de functionaliteit voor elke pagina die met CUG is beveiligd.

Voor extra informatie, zie [ Gesloten Gebruikersgroepen ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html).
