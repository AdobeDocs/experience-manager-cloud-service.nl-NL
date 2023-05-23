---
title: Toewijzing van gebruikers en belangrijkste migratie
description: Overzicht van de toewijzing van gebruikers en de belangrijkste migratie
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 91a13f8b23136298e0ccf494e51fccf94fa1e0b4
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 3%

---

# Toewijzing van gebruikers en belangrijkste migratie {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Gebruikerstoewijzing"
>abstract="Met het gereedschap Inhoud overbrengen kunt u gebruikers en groepen verplaatsen van uw bestaande Adobe Experience Manager-systeem (AEM) naar AEM as a Cloud Service. Bestaande gebruikers moeten worden toegewezen aan hun IMS-id&#39;s om te voorkomen dat ze worden gedupliceerd op de auteurinstantie van de Cloud Service."

>[!NOTE]
>Voor vorige versies van het Hulpmiddel van de Toewijzing van de Gebruiker, zie [oudere documentatie](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Inleiding {#introduction}

Als onderdeel van de as a Cloud Service overgang naar Adobe Experience Manager (AEM) moet u gebruikers en groepen van uw bestaande AEM naar AEM as a Cloud Service verplaatsen. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag. Voor dit proces moet gebruik worden gemaakt van de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS), dat één aanmelding voor alle Adobe-cloudtoepassingen biedt. Raadpleeg voor meer informatie [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). Vanwege deze wijziging moeten bestaande gebruikers worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers op de auteur-instantie van de Cloud Service te voorkomen. Aangezien groepen in traditionele AEM fundamenteel verschillen van groepen in IMS, worden groepen niet in kaart gebracht, maar moeten de twee groepen na de migratie met elkaar in overeenstemming worden gebracht.

## Gebruikerstoewijzing en migratiegegevens {#user-mapping-detail}

Met het gereedschap Inhoud overbrengen en het programma voor cloudversnelling kunt u alle gebruikers migreren die zijn gekoppeld aan de inhoud die wordt gemigreerd. Deze toewijzing wordt automatisch uitgevoerd en of dit gebeurt, kan worden geregeld door een schakelknop voordat de extractie wordt gestart. De standaardinstelling van de schakeloptie kan door de gebruiker worden genegeerd wanneer de extractie wordt gestart.

* Als het bronsysteem een auteurinstantie is, door gebrek is de keus om de afbeelding te doen _op_, omdat dit het aanbevolen proces is.
* Als het bronsysteem een publicatie-instantie is, kunt u de toewijzing standaard uitvoeren _uit_, omdat gebruikers gewoonlijk niet worden gemigreerd of gebruikt op publicatieinstanties.

## Belangrijke overwegingen bij het in kaart brengen van en het Migreren van Gebruikers {#important-considerations}


### Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres heeft in het dialoogvenster `profile/email` van hun *jcr* knooppunt, de gebruiker of groep in kwestie kan worden gemigreerd, maar is niet toegewezen. Dit scenario is het geval zelfs als het e-mailadres als gebruikersnaam voor het programma openen wordt gebruikt.

1. Als de gebruiker is uitgeschakeld, wordt deze op dezelfde manier behandeld als wanneer de gebruiker niet is uitgeschakeld. Deze wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.

1. Als een gebruiker op de doelAEM Cloud Service instantie met de zelfde gebruikersnaam (rep:principalName) zoals één van de gebruikers op de bron AEM instantie bestaat, wordt de gebruiker in kwestie niet gemigreerd.

1. Als een gebruiker wordt gemigreerd zonder dat deze is toegewezen via gebruikerstoewijzing, kunnen deze zich op het doelwolkensysteem niet aanmelden met hun IMS-id. Of als hun e-mailadres niet overeenkomt met het e-mailadres dat wordt gebruikt voor aanmelding bij IMS, kunnen zij zich op het doelcloudsysteem ook niet aanmelden met hun IMS-id. Ze kunnen zich misschien aanmelden met de traditionele AEM, maar deze methode is normaal gesproken niet wat gewenst of verwacht wordt.


## Aanvullende overwegingen {#additional-considerations}

* Als de instelling **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingesteld, worden reeds overgedragen gebruikers op de instantie Cloud Service samen met de gehele bestaande opslagplaats verwijderd. En er wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt opgenomen. Dit proces stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor een admin gebruiker die aan wordt toegevoegd **beheerders** groep. De gebruiker van admin moet aan de **beheerders** groep om het toegangstoken voor CTT terug te winnen.
* Als de inhoud wordt uitgebreid en de inhoud niet wordt overgedragen omdat deze niet is gewijzigd sinds de vorige overdracht, worden gebruikers en groepen die aan de inhoud zijn gekoppeld, ook niet overgedragen. Deze regel geldt ook als de gebruikers en groepen inmiddels zijn gewijzigd. De reden hiervoor is dat gebruikers en groepen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.
* Als het doel-AEM Cloud Service-exemplaar een gebruiker heeft met een andere gebruikersnaam maar hetzelfde e-mailadres als een van de gebruikers op de bron-AEM en Gebruikerstoewijzing is ingeschakeld, wordt in het logbestand een foutbericht opgenomen. Bovendien wordt de bron AEM gebruiker niet overgedragen, aangezien slechts één gebruiker met een bepaald e-mailadres op het doelsysteem is toegestaan.

## Laatste samenvatting en rapport {#final-report}

Nadat de extractie en inname met succes zijn voltooid, wordt een rapport gegenereerd met de belangrijkste migratiedetails. Zie [Hoe te om de Belangrijkste Migratie te bevestigen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) voor nadere bijzonderheden.
