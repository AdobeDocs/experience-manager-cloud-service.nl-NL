---
title: Belangrijkste functies beheren na migratie
description: Leer hoe u gebruikers en groepen instelt in IMS en AEM
source-git-commit: 5b0dfb847a1769665899d6dd693a7946832fe7d1
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---


# Belangrijkste functies beheren na migratie {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="Belangrijkste functies beheren na migratie"
>abstract="Leer hoe u gebruikers en groepen instelt in IMS en AEM"

In dit document worden de stappen beschreven die klanten op hoog niveau moeten ondernemen om hun gebruikers en groepen in IMS op te zetten en AEM met hun AEM as a Cloud Service-omgeving te werken.

## Belangrijkste functies beheren {#managing-principals}

Voor AEM as a Cloud Service moeten gebruikers en groepen primair worden beheerd met behulp van de Admin Console.  Bij het overwegen van een migratie kunnen sommige van deze taken worden uitgevoerd voordat de migratie van de inhoud plaatsvindt.  Hoofdzakelijk van deze hoofdtaakgroepen

* Gebruikers en groepen maken in IMS
* Gebruikers toewijzen aan groepen in IMS
* IMS-groepen toewijzen aan AEM (indien nodig)

de eerste twee kunnen worden uitgevoerd vóór of na de migratie van de inhoud.  Het zijn stappen die gebruikers en groepen in IMS slechts beïnvloeden, misschien met inbegrip van integratie met externe IDP zoals Actieve Folder of LDAP.  Deze stappen worden beschreven in [ het Leiden Belangrijkste in IMS met de Admin Console ](/help/journey-migration/managing-principals.md).

Wanneer de inhoud naar de AEM as a Cloud Service-omgeving is gemigreerd, kan de derde stap worden uitgevoerd.

### Migrerende groepen

Tijdens de innamefase van de migratie, worden de groepen gemigreerd als zij worden vereist om aan ACLs of het beleid van de CUG op de gemigreerde inhoud te voldoen.  Zie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) van de Migratie van de Groep 0} voor meer details.[

Gemigreerde groepen (die niet door de verwezenlijking van de Inzameling van Assets worden gecreeerd — zie hieronder Inzamelingen) worden gevormd als groepen IMS.  Dit betekent dat elke groep met dezelfde naam die in IMS wordt gemaakt (bijvoorbeeld via de Admin Console), in AEM wordt gekoppeld aan de groep en dat gebruikers die lid zijn van de IMS-groep ook in AEM lid worden van de groep.  Om deze koppeling tot stand te brengen, moet de groep ook eerst in IMS worden gecreeerd.  Gebruik de Admin Console om groepen, individueel of in bulk, in uw AEM instantie tot stand te brengen, zoals die in [ wordt beschreven Leidend Belangrijkste Belanghebbenden in IMS met de Admin Console ](/help/journey-migration/managing-principals.md).

Gebruik de interface AEM beveiliging om IMS-groepen toe te wijzen aan lokale AEM.  Zie [ Creërend en Vormend Groepen ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-groups#edit-a-group).  Hoewel dit document is bedoeld voor AEM 6.5, is het ook van toepassing op het toevoegen van groepen aan andere groepen in AEM as a Cloud Service.

### IMS-gebruikers

Aangezien gebruikers niet worden gemigreerd, moeten ze in IMS worden gemaakt, zodat ze in AEM kunnen worden gebruikt.  Er zijn verschillende manieren om dit te bereiken, maar het is belangrijk dat de gemaakte gebruikers worden toegewezen aan de juiste IMS-groepen, zodat de gebruikers dezelfde toegang hebben tot de inhoud die zij in het vorige AEM hadden.  Een van de gereedschappen die hiervoor kunnen worden gebruikt, is de functie voor het bulkuploaden in de Admin Console. Gebruik de bulkuploader om gebruikers en groepen waarvan ze lid moeten zijn, te uploaden.  Voordat u dit doet, moeten de groepen eerst in IMS worden gemaakt, zoals hierboven beschreven.

Om te weten welke groepen elke gebruiker tot zou moeten behoren, kunt u gebruik maken van het Rapport van de Gebruiker (zie [ de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)).  Dit rapport bevat een lijst met de groepen waarvan elke gebruiker lid moet zijn en deze lijst kan worden opgenomen in het invoerbestand van de bulkuploadfunctionaliteit voor Admin Consoles.

### Verzamelingen

Als u een Assets-verzameling maakt, worden ook automatisch bepaalde groepen gemaakt voor het beheer van de toegang tot die verzameling.  Deze groepen worden gemigreerd als zij op gemigreerde inzamelingen worden vermeld, maar zij worden niet gevormd om met groepen IMS direct te verbinden; in AEM blijven zij &quot;lokale groepen&quot;, en zij kunnen niet via IMS worden beheerd.

Aangezien deze groepen zich niet in IMS bevinden, kan het gereedschap voor bulkupload niet worden gebruikt om gebruikers als hun directe leden te maken.  IMS-gebruikers die zich ook in AEM bevinden, kunnen afzonderlijk aan deze groepen worden toegevoegd, maar dit bulksgewijs doen vereist een extra stap.  Dit kan op één manier gebeuren:
* Creeer een nieuwe groep of groepen in Admin Console/IMS voor toegang tot inzamelingen en vorm hen voor AEM.
* Meld u aan als lid van de groep(en), zodat de groep(en) in AEM wordt (worden) gemaakt.
* Voor de gemigreerde verzamelingen gebruikt u de gebruikersinterface van Assets-verzamelingen om de nieuwe groep toe te voegen als editor/eigenaar/viewer.
* Voeg gebruikers toe (of bulkupload) aan de nieuwe groep(en) in Admin Console.
* Wanneer de gebruiker zich voor de eerste keer aanmeldt, wordt de IMS-gebruiker in AEM gemaakt en moeten deze toegang hebben tot de nieuwe groep(en) en daardoor tot de oorspronkelijke verzamelingsgroepen.

Opmerking: voor het bulksgewijs toewijzen van gebruikers moeten de bovenstaande stappen worden gebruikt om de gebruikers in IMS te maken. Gebruikers die al in IMS bestaan, kunnen niet opnieuw bulksgewijs worden gemaakt.


