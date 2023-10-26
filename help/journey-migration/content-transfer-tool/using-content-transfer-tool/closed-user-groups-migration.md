---
title: Gesloten gebruikersgroepen migreren
description: Meer informatie over de vereiste speciale voorwaarden om Gesloten gebruikersgroepen in te schakelen na het migreren van inhoud naar Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
source-git-commit: 0109cea1be85e647fb6c04dde4714b162bdc75a5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Gesloten gebruikersgroepen migreren {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migratie van gesloten gebruikersgroepen"
>abstract="De migratie van Gesloten Gebruikersgroepen (CUG) vereist momenteel een paar controles en stappen om het na een migratie operationeel te maken."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html" text="Gesloten gebruikersgroepen in AEM"

Momenteel, hebben de Gesloten Gebruikersgroepen (CUG) sommige extra stappen nodig om in het bestemmingsmilieu van een migratie functioneel te zijn. Dit document verklaart het scenario, en de stappen die worden vereist om hen te hebben knopen op de voorgenomen manier beschermen.

## Migratie van groepen

Principals (met inbegrip van groepen) worden automatisch opgenomen in een migratie naar Adobe Experience Manager as a Cloud Service als zij aan de gemigreerde inhoud door ACL van die inhoud worden geassocieerd.

## Gesloten gebruikersgroepen in migratie

Momenteel gekoppelde groepen *alleen* met een beleid van de Gesloten Gebruikersgroep (CUG) zijn *niet* wordt automatisch opgenomen in de opname. Zoals hierboven vermeld, worden zij gemigreerd als zij met om het even welke inhoud door ACL worden geassocieerd. De verificatie van de groep en haar leden moet plaatsvinden voordat zij live gaat. Het Belangrijkste Rapport, dat door de mening van de Baan van Ingesties wordt gedownload, kan worden gebruikt om te zien of was de groep in kwestie inbegrepen, of niet omdat het niet in ACL was. Als de groep niet bestaat, moet deze worden gemaakt in de instantie Auteur, waarbij de juiste leden worden toegevoegd en geactiveerd om deze te laten bestaan in de instantie Publiceren. Dit kan worden gedaan gebruikend pakketten die op de bron worden gecreeerd.

Tot slot moeten de processen worden teweeggebracht en de eigenschappen moeten worden geplaatst om CUGs toe te laten. Hiertoe publiceert u alle pagina&#39;s die aan een CUG-beleid zijn gekoppeld opnieuw. Dit kalibreert de instantie Publish om het beleid te volgen.

Dit laat het beleid van de GECG op Publish toe, en de inhoud is slechts toegankelijk voor die voor authentiek verklaarde gebruikers die lid van de groep verbonden aan het beleid zijn.

## Actieve ontwikkeling

Het migratieteam werkt eraan om het beleid van CUG te maken automatisch migreren en functioneren, zonder enige extra stappen na het opnemen van de inhoud.
Neem de CUG-functionaliteit op in alle testprocessen voordat u live gaat.

## Samenvatting

Samengevat, zijn deze stappen om CUG na een migratie toe te laten:

1. Zorg ervoor dat elke groep die in CUG-beleid wordt gebruikt, bestaat bij Publiceren na de migratie.
   - Een groep kan bestaan als inbegrepen in ACL van gemigreerde inhoud.
   - Als dit niet het geval is, gebruikt u Packages om de toepassing op de doelinstantie te installeren (of maakt u deze daar handmatig) en activeert u de instantie en de betreffende leden. Controleer vervolgens of het bestand aanwezig is in Publiceren.
1. Publiceer alle pagina&#39;s verbonden aan een beleid van de GING, die ervoor zorgen het door, bijvoorbeeld, eerst het uitgeven van de pagina wordt gepubliceerd. Het is belangrijk dat ze allemaal opnieuw worden gepubliceerd.
   - Nadat alle pagina&#39;s opnieuw zijn gepubliceerd, controleert u de functionaliteit voor elke pagina die met CUG is beveiligd.
