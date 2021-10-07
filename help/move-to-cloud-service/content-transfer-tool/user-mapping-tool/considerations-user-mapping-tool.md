---
title: Belangrijke overwegingen voor het gereedschap Toewijzing van gebruikers
description: Belangrijke overwegingen voor het gereedschap Toewijzing van gebruikers
source-git-commit: 60e67e92f4f1ecaaf12c58f16f4324868d223934
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Belangrijke overwegingen voor het gereedschap Toewijzing van gebruikers {#important-considerations}


## Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres heeft op het `profile/email` gebied van hun *jcr* knoop zal de gebruiker of de groep in kwestie worden gemigreerd maar niet in kaart gebracht.

1. Als een bepaalde e-mail niet wordt gevonden op het Adobe Identity Management System (IMS) voor de gebruikte organisatie-id (of als de IMS-id om een andere reden niet kan worden opgehaald), wordt de gebruiker of groep in kwestie gemigreerd, maar niet toegewezen.

1. Als de gebruiker momenteel is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld. Het wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

1. Als een gebruiker op de doelinstantie van AEM Cloud Service met de zelfde gebruikersnaam (rep:principalName) zoals één van de gebruikers op de bron AEM instantie bestaat zal de gebruiker of de groep in kwestie niet worden gemigreerd.

## Aanvullende overwegingen {#additional-considerations}

* Als de instelling **Bestaande inhoud vegen op een Cloud-instantie voordat inname** wordt ingesteld, worden reeds overgedragen gebruikers op de Cloud Service-instantie samen met de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt om inhoud in te voeren. Dit stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor een admin gebruiker die aan **beheerders** groep wordt toegevoegd. De admin gebruiker zal aan **beheerders** groep opnieuw moeten worden toegevoegd om het toegangstoken voor CTT terug te winnen.

* Het wordt geadviseerd om het even welke bestaande gebruiker uit de AEM van de doelCloud Service te verwijderen alvorens CTT met Toewijzing van de Gebruiker in werking te stellen. Hiermee wordt elk conflict voorkomen tussen het migreren van gebruikers van de AEM naar de AEM instantie van het doel. Conflicten treden op tijdens inname als dezelfde gebruiker bestaat op de bron AEM instantie en de AEM instantie.

* Wanneer de inhoud toevoegt wordt uitgevoerd, als de inhoud niet wordt overgebracht omdat het sinds de vorige overdracht niet is veranderd, zullen de gebruikers en de groepen verbonden aan die inhoud ook niet worden overgebracht, zelfs als de gebruikers en de groepen ondertussen zijn veranderd. Dit komt doordat gebruikers en groepen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.

* Als het doel-AEM Cloud Service-exemplaar een gebruiker heeft met een andere gebruikersnaam maar hetzelfde e-mailadres als een van de gebruikers op de bron-AEM en Gebruikerstoewijzing is ingeschakeld, wordt een foutbericht geschreven in de logboeken en wordt de bron-AEM niet overgebracht, aangezien slechts één gebruiker met een opgegeven e-mailadres op het doelsysteem is toegestaan.

* Als twee gebruikers op de bron AEM instantie hetzelfde e-mailadres hebben en Gebruikerstoewijzing is ingeschakeld, wordt een foutbericht geschreven in de logboeken en wordt een van de bron AEM gebruikers niet overgebracht, omdat slechts één gebruiker met een opgegeven e-mailadres op het doelsysteem is toegestaan.

### Volgende functies {#whats-next}

Zodra u de belangrijke overwegingen en de uitzonderlijke gevallen hebt geleerd, bent u nu klaar om het hulpmiddel te gebruiken. Zie [Gebruikend het Hulpmiddel van de Toewijzing van de Gebruiker](/help/move-to-cloud-service/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.md) voor meer details.