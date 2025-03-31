---
title: Belangrijkste functies beheren na migratie
description: Leer hoe u gebruikers en groepen instelt in IMS en AEM
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: 50c8dd725e20cbd372a7d7858fc67b0f53a8d6d4
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Belangrijkste functies beheren na migratie {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="Belangrijkste functies beheren na migratie"
>abstract="Leer hoe u gebruikers en groepen instelt in IMS en AEM"

In dit document worden de stappen beschreven die klanten op hoog niveau moeten uitvoeren om hun gebruikers en groepen in IMS en AEM in te stellen voor hun AEM as a Cloud Service-omgeving.

Voor informatie over groepsmigratie en het Belangrijkste Rapport van de Migratie beschikbaar met elke opname, zie [ de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Voor een gids bij het gebruiken van bulkgroep en gebruikersdossiers in Admin Console, zie [ Bulk uploadt van Belangrijkste aan IMS na het gebruiken van CTT ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md).

## Belangrijkste functies beheren {#managing-principals}

Voor AEM as a Cloud Service moeten gebruikers en groepen primair worden beheerd met behulp van de Admin Console.  Bij het overwegen van een migratie kunnen sommige van deze taken worden uitgevoerd voordat de migratie van de inhoud plaatsvindt.  Hoofdzakelijk van deze hoofdtaakgroepen

* Gebruikers en groepen maken in IMS
* Gebruikers toewijzen aan groepen in IMS
* IMS-groepen toewijzen aan AEM-groepen (indien nodig)

De eerste twee kunnen worden uitgevoerd vóór of na de migratie van de inhoud.  Het zijn stappen die gebruikers en groepen in IMS slechts beïnvloeden, misschien met inbegrip van integratie met externe IDP zoals Actieve Folder of LDAP.  Deze stappen worden beschreven in [ het Leiden Belangrijkste in IMS met Admin Console ](/help/journey-migration/managing-principals.md).

Wanneer de inhoud naar de AEM as a Cloud Service-omgeving is gemigreerd, kan de derde stap worden uitgevoerd.

### Migrerende groepen

Tijdens de innamefase van de migratie, worden de groepen gemigreerd als zij worden vereist om aan ACLs of het beleid van de CUG op de gemigreerde inhoud te voldoen.  Zie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) van de Migratie van de Groep 0} voor meer details.[

Gemigreerde groepen (die niet door de Inzameling van Assets of de verwezenlijking van de Privé Omslag worden gecreeerd — zie hieronder Inzamelingen en PrivéOmslagen) worden gevormd als groepen IMS.  Dit betekent dat elke groep met dezelfde naam die in IMS wordt gemaakt (bijvoorbeeld via de Admin Console) wordt gekoppeld aan de groep in AEM en dat gebruikers die lid zijn van de IMS-groep ook lid worden van de groep in AEM.  Om deze koppeling tot stand te brengen, moet de groep ook eerst in IMS worden gecreeerd.  Gebruik Admin Console om groepen, individueel of in bulk, in uw instantie van AEM tot stand te brengen, zoals die in [ wordt beschreven het Leiden Belangrijkste in IMS met Admin Console ](/help/journey-migration/managing-principals.md).

Gebruik de gebruikersinterface van AEM Security om IMS-groepen toe te wijzen aan lokale AEM-groepen. Ga hiertoe naar de pagina Tools in AEM, klik op Security en kies Groepen.

### IMS-gebruikers

Aangezien gebruikers niet worden gemigreerd, moeten ze in IMS worden gemaakt, zodat ze in AEM kunnen worden gebruikt.  Er zijn verschillende manieren om dit te bereiken, maar het is belangrijk dat de gemaakte gebruikers worden toegewezen aan de juiste IMS-groepen, zodat de gebruikers dezelfde toegang hebben tot de inhoud die zij in het vorige AEM-systeem hadden.  Een van de gereedschappen die hiervoor kunnen worden gebruikt, is de functionaliteit voor bulkupload in de Admin Console. Gebruik de bulkuploader om gebruikers te uploaden samen met groepen waarvan ze lid moeten zijn.  Voordat u dit doet, moeten de groepen eerst in IMS worden gemaakt, zoals hierboven beschreven.

Om te weten welke groepen elke gebruiker tot zou moeten behoren, kunt u gebruik maken van het Rapport van de Gebruiker (zie [ de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)).  In dit rapport worden de groepen weergegeven waarvan elke gebruiker lid moet zijn. Deze lijst wordt normaal gesproken opgenomen in het invoerbestand voor bulkgebruikers voor gebruik met de Admin Console-functionaliteit voor bulkupload.

### Verzamelingen en privémappen

Als u een Assets-verzameling of privémap maakt, worden ook automatisch bepaalde groepen gemaakt voor het beheer van de toegang tot die Assets-inhoud.  Deze groepen worden gemigreerd als zij op de gemigreerde inhoud worden vermeld, maar zij worden niet gevormd om met groepen IMS direct te verbinden; in AEM blijven zij &quot;lokale groepen&quot;, en zij kunnen niet via IMS worden beheerd.

Aangezien deze groepen zich niet in IMS bevinden, kan het gereedschap voor bulkupload niet worden gebruikt om gebruikers als hun directe leden te maken.  IMS-gebruikers die zich ook in AEM bevinden, kunnen afzonderlijk aan deze groepen worden toegevoegd, maar dit bulksgewijs doen vereist een extra stap.  Dit kan op één manier gebeuren:
* Maak een nieuwe groep of groepen in Admin Console/IMS voor toegang tot verzamelingen/privémappen en configureer deze voor AEM.
* Meld u aan als lid van de groep(en), zodat de groep(en) in AEM wordt (worden) gemaakt.
* Voor de gemigreerde verzamelingen of privémappen gebruikt u de gebruikersinterface van Assets om de nieuwe groep toe te voegen als editor/eigenaar/viewer.
* Voeg gebruikers toe (of bulkupload) aan de nieuwe groep(en) in Admin Console.
* Wanneer de gebruiker zich voor het eerst aanmeldt, wordt de IMS-gebruiker ervan gemaakt in AEM en moeten deze toegang hebben tot de nieuwe groep(en) en daardoor tot de oorspronkelijke verzameling of tot privémapgroepen.

Nota: Voor bulktoewijzing van gebruikers, moeten de bovengenoemde stappen worden gebruikt om de gebruikers in IMS tot stand te brengen; de gebruikers die reeds in IMS bestaan kunnen niet opnieuw via bulkupload worden gecreeerd, hoewel de bulkredacteur kan worden gebruikt om die soorten veranderingen (zie [ Admin Console BulkGebruiker uploadt ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html) onder **uitgeeft gebruikersdetails**) aan te brengen.
