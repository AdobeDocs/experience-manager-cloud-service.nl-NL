---
title: Toewijzing van gebruikers en belangrijkste migratie
description: Overzicht van gebruikerstoewijzing en belangrijkste migratie in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 2f5eeb0333cee13b12edefd0f95541a891e30960
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 2%

---

# Toewijzing van gebruikers en belangrijkste migratie {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Gebruikerstoewijzing"
>abstract="Met het gereedschap Inhoud overbrengen kunt u gebruikers en groepen verplaatsen van uw bestaande Adobe Experience Manager-systeem (AEM) naar AEM as a Cloud Service. Bestaande gebruikers moeten worden toegewezen aan hun IMS-id&#39;s om te voorkomen dat ze worden gedupliceerd op de auteurinstantie van de Cloud Service."

>[!NOTE]
>Voor eerdere versies van het gereedschap Toewijzing gebruiker raadpleegt u de [oudere documentatie](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Inleiding {#introduction}

In het kader van de overgang naar as a Cloud Service Adobe Experience Manager (AEM) moeten gebruikers en groepen (of &#39;hoofden&#39;) van bestaande AEM naar AEM as a Cloud Service worden gemigreerd. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag. Voor dit proces moet gebruik worden gemaakt van de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS), dat één aanmelding voor alle Adobe cloudtoepassingen biedt. Zie voor meer informatie [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). Vanwege deze wijziging moeten bestaande gebruikers worden toegewezen aan hun IMS-id&#39;s om te voorkomen dat dubbele gebruikers worden gemaakt op de auteurinstantie van de Cloud Service. Aangezien groepen in traditionele AEM fundamenteel verschillen van groepen in IMS, worden groepen niet in kaart gebracht, maar moeten de twee groepen na de migratie met elkaar in overeenstemming worden gebracht.

## Belangrijkste migratiegegevens {#principal-migration-detail}

Met het gereedschap Inhoud overbrengen en het beheer van cloudversnelling kunt u alle principes die aan de gemigreerde inhoud zijn gekoppeld, migreren naar het cloudsysteem.  Dit doet u met het gereedschap Inhoud overbrengen door tijdens het extractieproces alle hoofdelementen van het AEM bronsysteem te kopiëren.  CAM Ingestie selecteert en migreert dan slechts die principes verbonden aan de inhoud die worden opgenomen. Als een hoofd op ACL of het beleid van de GIDS van gemigreerde inhoud is, dat hoofd en alle groepen het binnen is en hun voorvader (ouder) groepen allen zullen worden gemigreerd. Bovendien, als een hoofd op de inhoud een groep is, zullen al zijn afstammende (kind) groepen en gebruikers ook worden gemigreerd.

## Details gebruikerstoewijzing {#user-mapping-detail}

AEM gebruikers kunnen worden toegewezen aan overeenkomstige gebruikers van Adobe IMS met hetzelfde e-mailadres.  Deze toewijzing kan automatisch plaatsvinden in CTT (tijdens de extractiestap) en of dit gebeurt of niet door een knevel kan worden geregeld voordat de extractie wordt gestart. De standaardinstelling van de schakeloptie kan door de gebruiker worden genegeerd wanneer de extractie wordt gestart.

* Als het bronsysteem een auteurinstantie is, door gebrek is de keus om de afbeelding te doen _op_, omdat dit het aanbevolen proces is.
* Als het bronsysteem een publicatie-instantie is, kunt u de toewijzing standaard uitvoeren _uit_, omdat gebruikers gewoonlijk niet worden gemigreerd of gebruikt op publicatieinstanties; of als zij worden gebruikt, wordt een verschillend authentificatiesysteem (d.w.z., niet IMS) typisch gebruikt voor hen.

Of gebruikers tijdens de extractie al dan niet worden toegewezen, ze worden samen met de groepen tijdens de opname naar het wolkensysteem gemigreerd als ze zijn gekoppeld aan inhoud die wordt gemigreerd.

## Belangrijke overwegingen bij het in kaart brengen van en het Migreren van Gebruikers {#important-considerations}

### Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres heeft in het dialoogvenster `profile/email` van hun *jcr* knooppunt, de gebruiker of groep in kwestie kan worden gemigreerd, maar is niet toegewezen. Dit scenario is het geval zelfs als het e-mailadres als gebruikersnaam voor het programma openen wordt gebruikt.
2. Als de gebruiker is uitgeschakeld, wordt deze op dezelfde manier behandeld als andere gebruikers. De gebruiker wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.
3. Als een principal met dezelfde naam (rep:principalName) op zowel de bron AEM instantie als de doel-AEM Cloud Service-instantie bestaat, wordt de principal in kwestie niet gemigreerd en blijft de eerder bestaande principal op het wolkensysteem ongewijzigd.
4. Als een gebruiker wordt gemigreerd zonder dat deze is toegewezen via gebruikerstoewijzing, kan de gebruiker zich op het doelwolkensysteem niet aanmelden met zijn IMS-id. Of als hun e-mailadres niet overeenkomt met het e-mailadres dat wordt gebruikt voor aanmelding bij IMS, kunnen zij zich op het doelcloudsysteem ook niet aanmelden met hun IMS-id. Ze kunnen zich misschien aanmelden met de traditionele AEM methode (lokale aanmelding), maar deze methode is normaal gesproken niet wat wordt gewild of verwacht.

## Aanvullende overwegingen {#additional-considerations}

* Als de instelling **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingesteld, worden reeds overgedragen gebruikers op de instantie Cloud Service samen met de gehele bestaande opslagplaats verwijderd; er wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt opgenomen. Dit proces stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor een admin gebruiker die aan wordt toegevoegd **beheerders** groep. De gebruiker van admin moet aan opnieuw worden toegevoegd **beheerders** groep om het toegangstoken voor Ingestie CTT/CAM terug te winnen.
* Als de inhoud wordt uitgebreid en de inhoud niet wordt overgedragen omdat deze niet is gewijzigd sinds de vorige overdracht, worden gebruikers en groepen die aan de inhoud zijn gekoppeld, ook niet overgedragen. Deze regel geldt zelfs als de gebruikers en groepen op het bronsysteem zijn gewijzigd. De reden hiervoor is dat gebruikers en groepen alleen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld.
* Als het doel-AEM Cloud Service-exemplaar een gebruiker heeft met een andere gebruikersnaam maar hetzelfde e-mailadres als een van de gebruikers op de bron-AEM en Gebruikerstoewijzing is ingeschakeld, wordt in het logbestand een foutbericht opgenomen. Bovendien wordt de bron AEM gebruiker niet overgedragen, aangezien slechts één gebruiker met een bepaald e-mailadres op het doelsysteem is toegestaan.
* Zie [Gesloten gebruikersgroepen migreren](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen voor hoofden die in een Gesloten beleid van de Groep van de Gebruiker (CUG) worden gebruikt.

## Laatste samenvatting en rapport {#final-report}

Nadat de extractie en inname met succes zijn voltooid, wordt een rapport gegenereerd met de belangrijkste migratiedetails. Zie [Hoe te om de Belangrijkste Migratie te bevestigen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) voor nadere bijzonderheden.
