---
title: Belangrijke overwegingen voor het Hulpmiddel van de Toewijzing van de Gebruiker (Verouderd)
description: Belangrijke overwegingen voor het Hulpmiddel van de Toewijzing van de Gebruiker (Verouderd)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: 13a2386c099624a46e84126a939a9470e9b3a5f2
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Belangrijke overwegingen voor het Hulpmiddel van de Toewijzing van de Gebruiker (Verouderd) {#important-considerations}

>[!INFO]
>
>Deze documentatie verwijst naar een verouderde versie van het hulpmiddel. Voor meer informatie over de recentste versie, zie [ de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

## Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres op het `profile/email` gebied van hun *jcr* knoop heeft, wordt de gebruiker of de groep in kwestie gemigreerd maar niet in kaart gebracht. Deze regel is zelfs van toepassing als het e-mailadres wordt gebruikt als gebruikersnaam voor het aanmelden.

1. Als er geen e-mail wordt gevonden op het systeem van het Identity Management System (IMS) van de Adobe voor de gebruikte organisatie-id (of als de IMS-id niet kan worden opgehaald), wordt de gebruiker of groep gemigreerd, maar niet toegewezen.

1. Als de gebruiker is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld. Deze wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

1. Als een gebruiker op de doelinstantie van AEM Cloud Service met de zelfde gebruikersnaam (rep:principalName) zoals één van de gebruikers op de bron AEM instantie bestaat, wordt de gebruiker of de groep niet gemigreerd.

1. Als een gebruiker wordt gemigreerd zonder eerst in kaart te worden gebracht door middel van gebruikerstoewijzing, kunnen zij zich op het doelwolkensysteem niet aanmelden met hun IMS-id. Ze kunnen zich misschien aanmelden met de traditionele AEM, maar dit werkschema is normaal gesproken niet wat gewenst of verwacht wordt.

## Aanvullende overwegingen {#additional-considerations}

* Als het plaatsen **bestaande inhoud op de instantie van de Wolk alvorens worden geplaatst** wordt onttrokken, worden reeds overgebracht gebruikers op de instantie van de Cloud Service geschrapt. De gehele bestaande opslagplaats wordt ook verwijderd en er wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt opgenomen. Deze actie stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor een admin gebruiker die aan de **wordt toegevoegd beheerders** groep. De admin gebruiker moet aan de **beheerders** groep worden gelezen om het toegangstoken voor CTT terug te winnen.

* De Adobe adviseert dat u om het even welke bestaande gebruiker uit de AEM van de doelCloud Service alvorens CTT met de Toewijzing van de Gebruiker in werking te stellen verwijdert. Deze actie is nodig om conflicten te voorkomen tussen migrerende gebruikers van de bron AEM instantie aan de AEM instantie van het doel. Conflicten kunnen optreden tijdens inname als dezelfde gebruiker bestaat op de bron AEM instantie en de AEM instantie.

* Als de inhoud wordt uitgebreid en de inhoud niet wordt overgedragen omdat deze niet is gewijzigd sinds de vorige overdracht, worden gebruikers en groepen die aan de inhoud zijn gekoppeld, ook niet overgedragen. Deze regel geldt ook als de gebruikers en groepen inmiddels zijn gewijzigd. De reden hiervoor is dat gebruikers en groepen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.

* Als de AEM Cloud Service een gebruiker heeft met een andere gebruikersnaam maar hetzelfde e-mailadres als een gebruiker op de bron AEM instantie en Gebruikerstoewijzing is ingeschakeld, wordt een foutbericht geregistreerd. Bovendien wordt de bron AEM gebruiker niet overgedragen, aangezien slechts één gebruiker met een bepaald e-mailadres op het doelsysteem is toegestaan.

* Als twee gebruikers op de bron AEM instantie hetzelfde e-mailadres hebben en Gebruikerstoewijzing is ingeschakeld, wordt een foutbericht geregistreerd. Bovendien wordt een van de bron AEM gebruikers overgebracht omdat slechts één gebruiker met een bepaald e-mailadres op het doelsysteem is toegestaan.

### Volgende functies {#whats-next}

Zodra u de belangrijke overwegingen en de uitzonderlijke gevallen hebt geleerd, bent u nu klaar om het hulpmiddel te gebruiken. Zie [ Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker ](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md) voor meer details.
