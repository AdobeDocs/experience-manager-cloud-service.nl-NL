---
title: Toewijzing van gebruikers en belangrijkste migratie
description: Overzicht van gebruikerstoewijzing en belangrijkste migratie in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---

# Toewijzing van gebruikers en belangrijkste migratie {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Gebruikersmigratie"
>abstract="Met het gereedschap Inhoud overbrengen kunt u gebruikers en groepen verplaatsen van uw bestaande Adobe Experience Manager-systeem (AEM) naar AEM as a Cloud Service. Bestaande gebruikers moeten worden toegewezen, zodat ze zich via hun IMS-id&#39;s kunnen aanmelden."

>[!NOTE]
>Voor vorige versies van het Hulpmiddel van de Toewijzing van de Gebruiker, zie de [ erfenisdocumentatie ](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Inleiding {#introduction}

In het kader van de overgang naar Adobe Experience Manager (AEM) as a Cloud Service moeten gebruikers en groepen (of &#39;hoofden&#39;) van bestaande AEM naar AEM as a Cloud Service worden overgebracht. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as a Cloud Service is het volledig geïntegreerde gebruik van Adobe-id&#39;s voor toegang tot de auteurslaag. Dit proces vereist gebruik van [ Adobe Admin Console ](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gegevens van het gebruikersprofiel zijn gecentraliseerd in het Adobe Identity Management System (IMS), dat één aanmelding voor alle Adobe cloudtoepassingen biedt. Voor meer details, zie [ Identity Management ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). Vanwege deze wijziging moeten bestaande gebruikers worden toegewezen aan hun IMS-id&#39;s, zodat ze toegang hebben tot AEMaaCS met hun IMS-profielen. Aangezien groepen in traditionele AEM fundamenteel verschillen van groepen in IMS, worden groepen niet in kaart gebracht, maar moeten de twee groepen na de migratie met elkaar in overeenstemming worden gebracht.

## Belangrijkste migratiegegevens {#principal-migration-detail}

Met het gereedschap Inhoud overbrengen en Cloud Acceleration Manager migreert u naar het cloudsysteem naar alle principes die horen bij de inhoud die wordt gemigreerd. Dit doet u met het gereedschap Inhoud overbrengen door tijdens het extractieproces alle hoofdelementen van het AEM bronsysteem te kopiëren. CAM Ingestie selecteert en migreert dan slechts die principes verbonden aan de inhoud die worden opgenomen. Als een hoofd op ACL of het beleid van de GIDS van gemigreerde inhoud is, dat hoofd en alle groepen het binnen is en hun voorvader (ouder) groepen allen zullen worden gemigreerd. Bovendien, als een hoofd op de inhoud een groep is, zullen al zijn afstammende (kind) groepen en gebruikers ook worden gemigreerd.

## Details gebruikerstoewijzing {#user-mapping-detail}

AEM gebruikers kunnen worden toegewezen aan overeenkomstige gebruikers van Adobe IMS met hetzelfde e-mailadres. Deze toewijzing kan automatisch plaatsvinden in CTT (tijdens de extractiestap) en of dit gebeurt of niet door een knevel kan worden geregeld voordat de extractie wordt gestart. De standaardinstelling van de schakeloptie kan door de gebruiker worden genegeerd wanneer de extractie wordt gestart.

* Als het bronsysteem een auteursinstantie is, door gebrek is de keus om de afbeelding te doen __, omdat het het geadviseerde proces is.
* Als het bronsysteem publiceer instantie is, door gebrek is de keus om de afbeelding te doen _weg_, omdat de gebruikers niet normaal gemigreerd of gebruikt op publiceer instanties zijn; of als zij worden gebruikt, wordt een verschillend authentificatiesysteem (namelijk niet IMS) typisch gebruikt voor hen.

Of gebruikers tijdens de extractie al dan niet worden toegewezen, ze worden samen met de groepen tijdens de opname naar het wolkensysteem gemigreerd als ze zijn gekoppeld aan inhoud die wordt gemigreerd.

## Belangrijke overwegingen bij het in kaart brengen van en het Migreren van Gebruikers {#important-considerations}

### Uitzonderlijke gevallen {#exceptional-cases}

De volgende specifieke gevallen worden geregistreerd:

1. Als een gebruiker geen e-mailadres op het `profile/email` gebied van hun *jcr* knoop heeft, kan de gebruiker in kwestie worden gemigreerd maar niet in kaart gebracht. Dit scenario is het geval zelfs als het e-mailadres als gebruikersnaam voor het programma openen wordt gebruikt.
2. Als de gebruiker is uitgeschakeld, wordt deze op dezelfde manier behandeld als andere gebruikers. De gebruiker wordt toegewezen en gemigreerd als normaal en blijft uitgeschakeld in de cloudinstantie.
3. Als een principal met om het even welk van de zelfde uniek-beperkte gegevens (rep:principalName, rep:authorizableId, jcr:uid of rep:externalId) op zowel de bron AEM instantie als de doelAEM Cloud Service instantie bestaat, wordt het hoofd in kwestie niet gemigreerd en het eerder bestaande hoofd op het wolkensysteem blijft onveranderd. Dit wordt geregistreerd in het Belangrijkste Rapport van de Migratie.
4. Als een gebruiker niet via gebruikerstoewijzing aan IMS wordt toegewezen, wordt het gebruikersprofiel op het AEM van de cloud niet herkend door IMS. In dit geval wordt bij aanmelding via IMS een nieuw (duplicaat) profiel gemaakt op AEM, maar bevat het geen vorige profielgegevens. Het oorspronkelijke gebruikersprofiel bestaat op het AEM van de cloud, maar kan niet via IMS worden aangemeld, alleen met behulp van de traditionele AEM methode (lokale aanmelding). Daarom wordt het toewijzen van alle gebruikers ten zeerste aanbevolen voor alle auteur-migraties.

## Aanvullende overwegingen {#additional-considerations}

* Als het plaatsen **bestaande inhoud op de instantie van de Wolk alvorens wordt geplaatst** ontspant, worden de hoofden eerder overgebracht naar de instantie van de Cloud Service geschrapt samen met de volledige bestaande bewaarplaats; een nieuwe bewaarplaats wordt gecreeerd waarin inhoud wordt opgenomen. Dit proces stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor een admin gebruiker die aan de **wordt toegevoegd beheerders** groep. De admin gebruiker moet aan de **beheerders** groep opnieuw worden toegevoegd om het toegangstoken voor Ingestie terug te winnen CTT/CAM.
* Wanneer niet-veeggebaren ingestions worden uitgevoerd (**Wipe bestaande inhoud** is unset), als de inhoud niet wordt overgebracht omdat het niet sinds de vorige overdracht is veranderd, worden de gebruikers en de groepen verbonden aan die inhoud niet overgebracht. Deze regel geldt zelfs als de gebruikers en groepen op het bronsysteem zijn gewijzigd. Dit komt doordat gebruikers en groepen alleen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld. Wegens dit, zullen om het even welke hoofden nieuw aan een groep op het bronsysteem niet worden gemigreerd tenzij zij deel van een verschillende groep uitmaken die wordt gemigreerd, of in ACL van verschillende inhoud die wordt gemigreerd. Als u deze hoofdrolspelers achteraf wilt migreren, kunt u pakketten gebruiken of principes uit het doel verwijderen en de relevante inhoud opnieuw migreren (Extraheren met overschrijven en Samenvoegen met sluitereffect).
* Dubbele e-mailadressen zijn niet toegestaan in IMS, maar wel in AEM (zowel op locatie als in de cloud). Een gebruiker kan zich via IMS aanmelden bij AEM via zijn e-mailadres en deze worden aangemeld bij het gebruikersprofiel waarnaar IMS verwijst.
* Zie [ het Migreren van Gesloten Groepen van de Gebruiker ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen voor hoofden die in een beleid van de Gesloten Groep van de Gebruiker (CUG) worden gebruikt.

## Laatste samenvatting en rapport {#final-report}

Nadat de extractie en inname met succes zijn voltooid, wordt een rapport gegenereerd met de belangrijkste migratiedetails. Zie [ hoe te om de Belangrijkste Migratie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) voor de details te bevestigen.
