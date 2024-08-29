---
title: Groepsmigratie
description: Overzicht van groepsmigratie in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 1f9526f8e8aa6a070e95827fab16431b0ee7566b
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---


# Groepsmigratie {#group-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_groupmigration"
>title="Groepsmigratie"
>abstract="Met het gereedschap Inhoud overbrengen kunt u groepen van uw bestaande Adobe Experience Manager-systeem (AEM) kopiëren naar AEM as a Cloud Service."

>[!NOTE]
>Voor vorige versies van het Hulpmiddel van de Toewijzing van de Gebruiker, zie de [ erfenisdocumentatie ](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Inleiding {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermigration"
>title="Gebruikers worden niet gemigreerd"
>abstract="Het gereedschap Inhoud overbrengen migreert gebruikers niet meer. De gebruikers zouden in de Admin Console moeten worden beheerd."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

In het kader van de overgang naar Adobe Experience Manager (AEM) as a Cloud Service moeten groepen van bestaande AEM naar AEM as a Cloud Service worden overgebracht. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as a Cloud Service is het volledig geïntegreerde gebruik van Adobe-id&#39;s voor toegang tot de auteurslaag. Dit proces vereist gebruik van [ Adobe Admin Console ](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gegevens van het gebruikersprofiel zijn gecentraliseerd in het Adobe Identity Management System (IMS), dat één aanmelding voor alle Adobe cloudtoepassingen biedt. Voor meer details, zie [ Identity Management ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). Vanwege deze wijziging worden gebruikers automatisch op AEM gemaakt wanneer ze zich voor het eerst via IMS aanmelden.  Hierdoor migreert CTT de gebruikers niet naar het cloudsysteem.  IMS-gebruikers moeten worden geplaatst in IMS-groepen, die gemigreerde groepen of nieuwe groepen kunnen zijn die worden geplaatst in de AEM groepen die toestemming hebben gekregen om toegang te krijgen tot de AEM inhoud die wordt gemigreerd.  Op die manier hebben gebruikers op het wolkensysteem dezelfde toegang als op hun AEM.

## Groepsmigratiegegevens {#group-migration-detail}

Met het gereedschap Inhoud overbrengen en Cloud Acceleration Manager kunt u groepen migreren die zijn gekoppeld aan de inhoud die wordt gemigreerd naar het cloudsysteem. Dit doet u met het gereedschap Inhoud overbrengen door tijdens het extractieproces alle groepen van het bron- AEM systeem te kopiëren. Met CAM-inname worden dan alleen bepaalde groepen geselecteerd en gemigreerd:

* Er zijn een aantal geïntegreerde groepen die al aanwezig zijn op het doelwolkensysteem; deze worden nooit gemigreerd.
* De directe lidgroepen van om het even welke ingebouwde groep die direct of indirect in ACL of het beleid van de GIDS van gemigreerde inhoud wordt bedoeld zullen worden gemigreerd, om gebruikers te verzekeren die directe of indirecte leden van dergelijke groepen zijn hun toegang tot de gemigreerde inhoud handhaven.
* Als een groep op ACL of het beleid van de GIDS van gemigreerde inhoud is, zal die groep worden gemigreerd.
* Andere groepen, zoals die niet gevonden op ACL of beleid van de GIDS, die reeds op het bestemmingssysteem, en die met om het even welke uniek-beperkte gegevens reeds op het doelsysteem, zullen niet worden gemigreerd.

Merk op dat de weg die voor een groep wordt geregistreerd/wordt gemeld slechts de eerste weg is die die groep teweegbracht om worden gemigreerd, en die groep kon ook op andere inhoudspaden zijn.

De meeste gemigreerde groepen zijn geconfigureerd om te worden beheerd door IMS.  Dit betekent dat een groep in IMS met dezelfde naam wordt gekoppeld aan de groep in AEM en dat alle IMS-gebruikers in de IMS-groep AEM gebruikers en leden van de groep in AEM worden.  Dit staat die gebruikers toe om toegang tot de inhoud volgens ACLs of beleid CUGs voor de groep te hebben.

De uitzondering op deze IMS-configuratie geldt voor groepen die zijn gemaakt met Assets Collections. Wanneer een inzameling op AEM wordt gecreeerd, worden de groepen gecreeerd voor toegang tot die inzameling; dergelijke groepen worden gemigreerd naar het wolkensysteem, maar zij worden niet gevormd om door IMS te worden beheerd.  Als u IMS-gebruikers aan deze groepen wilt toevoegen, moeten ze op de pagina Groepseigenschappen in de Assets-gebruikersinterface worden toegevoegd, afzonderlijk of gezamenlijk als onderdeel van een andere IMS-groep.


## Migratie buiten groep uitschakelen {#group-migration-option}

CTT versie 3.0.20 en hoger bevat een optie om de migratie van groepen uit te schakelen.  Dit wordt gevormd in de console OSGI als volgt:

* De configuratie van OSGI openen `(http://<server> /system/console/configMgr)`
* Klik op de configuratie genoemd {de Configuratie van de Dienst van de Uitwinning van het Hulpmiddel van de Overdracht van 0} Inhoud ****
* Uncheck **omvat Groepen in migratie** om groepsmigraties onbruikbaar te maken
* Klik **sparen** om de configuratie te verzekeren wordt bewaard en op de server actief

Als deze instelling is uitgeschakeld, worden groepen niet gemigreerd en zijn er geen rapport over de belangrijkste migratie of gebruikersrapport beschikbaar.

## Gebruikersrapport {#user-report}

Tijdens migratie worden gebruikers niet gemigreerd, maar de user-group relaties op het bronsysteem gaan verloren, tenzij ze op een of andere manier worden vastgelegd.  In het gebruikersrapport worden sommige van deze gegevens in tekstopmaak vastgelegd in een gebruikersrapport. Elke gebruiker wordt hierin gerapporteerd (één per regel) samen met een lijst met groepen waarvan het lid is (maar groepen die niet zijn gemigreerd, worden niet in deze lijst geplaatst), tenzij de lijst met groepen leeg is. In dat geval wordt de gebruiker niet weergegeven. De groepen die samen met elke gebruiker worden gemeld zijn die de gebruiker een lid van direct of indirect in het bronsysteem is; aangezien de groepen in het bronsysteem kunnen worden genesteld terwijl in het doelsysteem zij niet zijn, steunt deze lijst van groepen de nieuwe afgevlakte groepsstructuur in IMS.

In het geval van een sluitereffect en een niet-sluiteropname, worden in de gebruikerslijst de groepen opgenomen die in een van beide fasen zijn gemigreerd.

Naast de groepen voor elke gebruiker, is er een gebied in het rapport waar de nota&#39;s voor de gebruiker kunnen worden toegevoegd (en een gedetailleerde beschrijving van de betekenis van de nota is ook in het rapport).  Mogelijke opmerkingen zijn:

* De gebruikers die direct in ACL van verwijzingen worden voorzien zullen *nota-A* in hun nota&#39;s sectie hebben, aangezien dit geen geadviseerd gebruiksgeval of beste praktijken is.
* De gebruikers die directe leden van een ingebouwde groep zijn zullen *Nota-B* in hun nota&#39;s sectie hebben, aangezien dit ook geen geadviseerd gebruiksgeval of beste praktijken is.

Deze gevallen kunnen tegelijkertijd en ook op hetzelfde moment als de eerdere gevallen plaatsvinden.

Het Rapport van de Gebruiker wordt toegevoegd aan het eind van (en is daarom deel van) het Belangrijkste Rapport van de Migratie (zie [ Definitief Samenvatting en Rapport ](#final-summary-and-report) hieronder).

## Aanvullende overwegingen {#additional-considerations}

* Als het plaatsen **bestaande inhoud op de instantie van de Wolk alvorens wordt geplaatst** ontspant, worden de groepen eerder overgebracht naar de instantie van de Cloud Service geschrapt samen met de volledige bestaande bewaarplaats; een nieuwe bewaarplaats wordt gecreeerd waarin inhoud wordt opgenomen. Dit proces stelt ook alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terug en is waar voor om het even welke gebruiker die aan de **wordt toegevoegd beheerders** groep. De admin gebruiker moet aan de **beheerders** groep opnieuw worden toegevoegd om het toegangstoken voor Ingestie terug te winnen CTT/CAM.
* Wanneer niet-veeggebaren ingestions worden uitgevoerd (**Wipe bestaande inhoud** is unset), als de inhoud niet wordt overgebracht omdat het niet sinds de vorige overdracht is veranderd, worden de groepen verbonden aan die inhoud niet overgebracht. Deze regel geldt ook als de groepen zijn gewijzigd op het bronsysteem. Dit komt doordat groepen alleen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld. Wegens dit, in dit geval zullen om het even welke groepen die lid van een groep op het bronsysteem zijn niet worden gemigreerd tenzij zij deel van een verschillende groep uitmaken die wordt gemigreerd, of in ACL van verschillende inhoud die wordt gemigreerd. Als u deze groepen nadien wilt migreren, kunt u pakketten gebruiken, groepen van het doel verwijderen en de relevante inhoud opnieuw migreren, of opnieuw migreren met een sluitereffect.
* Tijdens een niet-veeggebaar opname, als een groep met om het even welke zelfde uniek-beperkte gegevens (rep:principalName, rep:authorizableId, jcr:uid of rep:externalId) op zowel de bron AEM instantie als de doelinstantie van AEM Cloud Service bestaat, is de groep in kwestie _niet_ gemigreerd en de vorige bestaande groep op de wolk blijft onveranderd. Dit wordt geregistreerd in het Belangrijkste Rapport van de Migratie.
* Zie [ het Migreren van Gesloten Groepen van de Gebruiker ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen voor groepen die in een gesloten beleid van de Groep van de Gebruiker (CUG) worden gebruikt.

## Laatste samenvatting en rapport

Nadat de extractie en inname met succes zijn voltooid, wordt een rapport gegenereerd met de migratiegegevens van de groep. Zie [ hoe te de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration) voor de details bevestigen.
