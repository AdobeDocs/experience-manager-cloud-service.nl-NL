---
title: Belangrijke overwegingen voor het Hulpmiddel van de Toewijzing van de Gebruiker (Verouderd)
description: Belangrijke overwegingen voor het Hulpmiddel van de Toewijzing van de Gebruiker (Verouderd)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 0%

---

# Belangrijke overwegingen voor het Hulpmiddel van de Toewijzing van de Gebruiker (Verouderd) {#important-considerations}

>[!INFO]
>
>Deze documentatie verwijst naar een verouderde versie van het hulpmiddel. Voor meer informatie over de meest recente versie raadpleegt u [Toewijzing van gebruikers en belangrijkste migratie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

## Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres heeft in het dialoogvenster `profile/email` van hun *jcr* wordt de gebruiker of groep in kwestie gemigreerd, maar niet toegewezen.  Deze regel geldt zelfs als het e-mailadres wordt gebruikt als gebruikersnaam voor het aanmelden.

1. Als een bepaalde e-mail niet wordt gevonden op het systeem van het Adobe Identity Management System (IMS) voor de gebruikte organisatie-id (of als de IMS-id om een andere reden niet kan worden opgehaald), wordt de betrokken gebruiker of groep gemigreerd, maar niet toegewezen.

1. Als de gebruiker momenteel is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld. Deze wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

1. Als een gebruiker op de doelinstantie van AEM Cloud Service met de zelfde gebruikersnaam (rep:principalName) zoals één van de gebruikers op de bron AEM instantie bestaat wordt de gebruiker of de groep in kwestie niet gemigreerd.

1. Als een gebruiker wordt gemigreerd zonder dat deze eerst via gebruikerstoewijzing wordt toegewezen, kunnen deze zich op het doelwolkensysteem niet aanmelden met hun IMS-id.  Ze kunnen zich misschien aanmelden met de traditionele AEM, maar houd er rekening mee dat dit normaal gesproken niet het gewenste of verwachte resultaat is.

## Aanvullende overwegingen {#additional-considerations}

* Als de instelling **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingesteld, worden reeds overgedragen gebruikers op de instantie Cloud Service samen met de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt om inhoud in te voeren. Hiermee worden ook alle instellingen opnieuw ingesteld, inclusief de machtigingen voor de Cloud Service-instantie van het doel. Dit geldt ook voor een beheerder die aan de **beheerders** groep. De beheerder-gebruiker moet opnieuw worden toegevoegd aan de **beheerders** groep om het toegangstoken voor CTT terug te winnen.

* Het wordt geadviseerd om het even welke bestaande gebruiker uit de AEM van de doelCloud Service te verwijderen alvorens CTT met Toewijzing van de Gebruiker in werking te stellen. Hiermee wordt elk conflict voorkomen tussen het migreren van gebruikers van de AEM naar de AEM instantie van het doel. Conflicten treden op tijdens inname als dezelfde gebruiker bestaat op de bron AEM instantie en de AEM instantie.

* Wanneer de inhoud toevoegt wordt uitgevoerd, als de inhoud niet wordt overgebracht omdat het sinds de vorige overdracht niet is veranderd, zullen de gebruikers en de groepen verbonden aan die inhoud ook niet worden overgebracht, zelfs als de gebruikers en de groepen ondertussen zijn veranderd. Dit komt doordat gebruikers en groepen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.

* Als de AEM Cloud Service-doelinstantie een gebruiker heeft met een andere gebruikersnaam maar hetzelfde e-mailadres als een van de gebruikers op de AEM-broninstantie en de functie Toewijzing gebruiker is ingeschakeld, wordt een foutbericht geschreven in de logboeken en wordt de bron AEM gebruiker niet overgebracht, aangezien slechts één gebruiker met een opgegeven e-mailadres op het doelsysteem is toegestaan.

* Als twee gebruikers op de bron AEM instantie hetzelfde e-mailadres hebben en Gebruikerstoewijzing is ingeschakeld, wordt een foutbericht geschreven in de logboeken en wordt een van de bron AEM gebruikers niet overgebracht, omdat slechts één gebruiker met een opgegeven e-mailadres op het doelsysteem is toegestaan.

### Volgende functies {#whats-next}

Zodra u de belangrijke overwegingen en de uitzonderlijke gevallen hebt geleerd, bent u nu klaar om het hulpmiddel te gebruiken. Zie [Gebruikerstoewijzing gebruiken](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md) voor meer informatie .
