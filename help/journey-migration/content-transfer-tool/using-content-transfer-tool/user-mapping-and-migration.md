---
title: Toewijzing van gebruikers en belangrijkste migratie
description: Overzicht van de toewijzing van gebruikers en de belangrijkste migratie
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 25bfcd521e9bbc54bff3b87d17cdeb0f99a68511
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 3%

---

# Toewijzing van gebruikers en belangrijkste migratie {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Gebruikerstoewijzing"
>abstract="Met het gereedschap Inhoud overbrengen kunt u gebruikers en groepen van het bestaande AEM naar AEM as a Cloud Service verplaatsen. Bestaande gebruikers moeten worden toegewezen aan hun IMS-id&#39;s om te voorkomen dat ze worden gedupliceerd op de auteurinstantie van de Cloud Service."

>[!NOTE]
>Voor vorige versies van het Hulpmiddel van de Toewijzing van de Gebruiker, zie [oudere documentatie](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Inleiding {#introduction}

Als onderdeel van de as a Cloud Service overgang naar Adobe Experience Manager (AEM) moet u gebruikers en groepen verplaatsen van uw bestaande AEM naar AEM as a Cloud Service. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag. Hiervoor moet gebruik worden gemaakt van de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) dat Single Sign-On biedt voor alle Adobe-cloudtoepassingen. Raadpleeg voor meer informatie [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html#identity-management). Vanwege deze wijziging moeten bestaande gebruikers worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers op de auteur-instantie van de Cloud Service te voorkomen. Aangezien groepen in traditionele AEM fundamenteel verschillen van groepen in IMS, worden groepen niet in kaart gebracht, maar moeten de twee groepen na de migratie met elkaar in overeenstemming worden gebracht.

## Gebruikerstoewijzing en migratiegegevens {#user-mapping-detail}

Met het gereedschap Overdracht van inhoud en het beheer van Cloud Acceleration worden alle gebruikers gemigreerd die zijn gekoppeld aan de inhoud die wordt gemigreerd. Deze toewijzing wordt automatisch uitgevoerd en of dit gebeurt, kan worden geregeld door een schakelknop voordat de extractie wordt gestart. De standaardinstelling van de schakeloptie kan door de gebruiker worden genegeerd wanneer de extractie wordt gestart.

* Als het bronsysteem een auteurinstantie is, door gebrek is de keus om de afbeelding te doen _op_, aangezien dit het aanbevolen proces is.
* Als het bronsysteem een publicatie-instantie is, kunt u de toewijzing standaard uitvoeren _uit_, aangezien gebruikers gewoonlijk niet worden gemigreerd of gebruikt op publicatieinstanties.

## Belangrijke overwegingen bij het in kaart brengen van en het Migreren van Gebruikers {#important-considerations}


### Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres heeft in het dialoogvenster `profile/email` van hun *jcr* de gebruiker of de groep in kwestie kan worden gemigreerd maar zal niet in kaart worden gebracht. Dit is zelfs het geval als het e-mailadres wordt gebruikt als gebruikersnaam voor het aanmelden.

1. Als de gebruiker is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld. Deze wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

1. Als een gebruiker op de doelinstantie van AEM Cloud Service met de zelfde gebruikersnaam (rep:principalName) zoals één van de gebruikers op de bron AEM instantie bestaat, zal de gebruiker of de groep in kwestie niet worden gemigreerd.

1. Als een gebruiker wordt gemigreerd zonder eerst in kaart te worden gebracht via Gebruikerstoewijzing, of als zijn e-mailadres niet overeenkomt met het e-mailadres dat wordt gebruikt om zich aan te melden bij IMS, kunnen de gebruikers zich op het doelcloudsysteem niet aanmelden met hun IMS-id. Ze kunnen zich misschien aanmelden met de traditionele AEM, maar houd er rekening mee dat dit normaal gesproken niet het gewenste of verwachte resultaat is.


## Aanvullende overwegingen {#additional-considerations}

* Als de instelling **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingesteld, worden reeds overgedragen gebruikers op de instantie Cloud Service samen met de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt om inhoud in te voeren. Hiermee worden ook alle instellingen opnieuw ingesteld, inclusief de machtigingen voor de Cloud Service-instantie van het doel. Dit geldt ook voor een beheerder die aan de **beheerders** groep. De gebruiker van admin moet aan opnieuw worden toegevoegd **beheerders** groep om het toegangstoken voor CTT terug te winnen.
* Wanneer de inhoud toevoegt wordt uitgevoerd, als de inhoud niet wordt overgebracht omdat het sinds de vorige overdracht niet is veranderd, worden de gebruikers en de groepen verbonden aan die inhoud ook niet overgebracht, zelfs als de gebruikers en de groepen ondertussen zijn veranderd. Dit komt doordat gebruikers en groepen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.
* Als het doel-AEM Cloud Service-exemplaar een gebruiker heeft met een andere gebruikersnaam maar hetzelfde e-mailadres als een van de gebruikers op de bron AEM instantie en de functie Toewijzing gebruiker is ingeschakeld, wordt een foutbericht geschreven in de logboeken en wordt de bron AEM gebruiker niet overgebracht, aangezien slechts één gebruiker met een opgegeven e-mailadres op het doelsysteem is toegestaan.

## Laatste samenvatting en rapport {#final-report}

Nadat de extractie en inname met succes zijn voltooid, wordt een rapport gegenereerd met de belangrijkste migratiedetails. Zie [Hoe te om de Belangrijkste Migratie te bevestigen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) voor nadere bijzonderheden.
