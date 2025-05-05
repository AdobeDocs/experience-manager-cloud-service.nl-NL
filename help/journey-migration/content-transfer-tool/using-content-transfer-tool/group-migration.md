---
title: Groepsmigratie
description: Overzicht van groepsmigratie in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 50c8dd725e20cbd372a7d7858fc67b0f53a8d6d4
workflow-type: tm+mt
source-wordcount: '1921'
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
>abstract="Het gereedschap Inhoud overbrengen migreert gebruikers niet meer. Gebruikers dienen te worden beheerd in de Admin Console."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console-documentatie"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

In het kader van de overgang naar Adobe Experience Manager (AEM) as a Cloud Service moeten groepen van bestaande AEM-systemen naar AEM as a Cloud Service worden gemigreerd. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as a Cloud Service is het volledig geïntegreerde gebruik van Adobe-id&#39;s voor toegang tot de auteurslaag. Dit proces vereist gebruik van [ Adobe Admin Console ](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gegevens van het gebruikersprofiel zijn gecentraliseerd in het Adobe Identity Management System (IMS), dat één aanmelding biedt voor alle Adobe-cloudtoepassingen. Voor meer details, zie [ Identity Management ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). Vanwege deze wijziging worden gebruikers automatisch op AEM gemaakt wanneer ze zich voor het eerst via IMS aanmelden.  Hierdoor migreert CTT de gebruikers niet naar het cloudsysteem.  IMS-gebruikers moeten worden geplaatst in IMS-groepen, die gemigreerde groepen of nieuwe groepen kunnen zijn die worden geplaatst in AEM-groepen die toestemming hebben gekregen om toegang te krijgen tot de AEM-inhoud die wordt gemigreerd.  Op die manier hebben gebruikers op het cloudsysteem dezelfde toegang als op hun AEM-bronsysteem.

## Groepsmigratiegegevens {#group-migration-detail}

Met het gereedschap Inhoud overbrengen en Cloud Acceleration Manager kunt u groepen migreren die zijn gekoppeld aan de inhoud die wordt gemigreerd naar het cloudsysteem. Met het gereedschap Inhoud overbrengen kopieert u alle groepen van het AEM-bronsysteem tijdens het extractieproces. Met CAM-inname worden dan alleen bepaalde groepen geselecteerd en gemigreerd:

* Als een groep op ACL of het beleid van de GIDS van gemigreerde inhoud is, zal die groep worden gemigreerd, met een paar hieronder vermelde uitzonderingen.
* Er zijn een aantal geïntegreerde groepen die al aanwezig zijn op het doelwolkensysteem; deze worden nooit gemigreerd.
   * Sommige ingebouwde groepen kunnen lidgroepen omvatten die _niet_ ingebouwd zijn; om het even welke dergelijke lidgroepen (directe leden of leden van leden, enz.) die in ACL of het beleid van de GIDS van gemigreerde inhoud van verwijzingen worden voorzien zullen worden gemigreerd, om gebruikers te verzekeren die (of direct of indirect) lid van deze groepen zijn hun toegang tot de gemigreerde inhoud handhaven.
* Andere groepen, zoals die niet gevonden op ACL of beleid van de GIDS, die reeds op het bestemmingssysteem, en die met om het even welke uniek-beperkte gegevens reeds op het doelsysteem, zullen niet worden gemigreerd.

Merk op dat de weg die voor een groep wordt geregistreerd/wordt gemeld slechts de eerste weg is die die groep teweegbracht om worden gemigreerd, en die groep kon ook op andere inhoudspaden zijn.

De meeste gemigreerde groepen zijn geconfigureerd om te worden beheerd door IMS.  Dit betekent dat een groep in IMS met dezelfde naam wordt gekoppeld aan de groep in AEM en dat alle IMS-gebruikers in de IMS-groep AEM-gebruikers en leden van de groep in AEM worden.  Dit staat die gebruikers toe om toegang tot de inhoud volgens ACLs of beleid CUGs voor de groep te hebben.

Merk op dat gemigreerde groepen niet langer als &quot;lokale groepen&quot; van AEM worden beschouwd; het zijn groepen die klaar zijn voor IMS in AEM, hoewel zij misschien nog niet in IMS bestaan.  Ze moeten afzonderlijk opnieuw worden gemaakt in IMS, zodat ze kunnen worden gesynchroniseerd tussen AEM en IMS.  Groepen kunnen in IMS worden gemaakt via onder andere Admin Console, afzonderlijk of bulksgewijs.  Zie [ gebruikersgroepen ](https://helpx.adobe.com/enterprise/using/user-groups.html) voor details over het creëren van groepen individueel of in bulk op Admin Console leiden.

De uitzondering op deze configuratie IMS is met groepen die door de Inzamelingen van Assets en PrivéOmslagen worden gecreeerd. Wanneer op AEM een verzameling of een privémap wordt gemaakt, worden groepen gemaakt voor toegang tot die inhoud. Dergelijke groepen worden naar het cloudsysteem gemigreerd, maar ze zijn niet geconfigureerd voor beheer door IMS.  Als u IMS-gebruikers aan deze groepen wilt toevoegen, moeten ze op de pagina Groepseigenschappen in de Assets-gebruikersinterface worden toegevoegd, afzonderlijk of gezamenlijk als onderdeel van een andere IMS-groep.


## Migratie buiten groep uitschakelen {#group-migration-option}

CTT versie 3.0.20 en hoger bevat een optie om de migratie van groepen uit te schakelen.  Dit wordt gevormd in de console OSGI als volgt:

* De configuratie van OSGI openen `(http://<server>/system/console/configMgr)`
* Klik op de configuratie genoemd {de Configuratie van de Dienst van de Uitwinning van het Hulpmiddel van de Overdracht van 0} Inhoud **&#x200B;**
* Uncheck **omvat Groepen in migratie** om groepsmigraties onbruikbaar te maken
* Klik **sparen** om de configuratie te verzekeren wordt bewaard en op de server actief

Als deze instelling is uitgeschakeld, worden groepen niet gemigreerd en is er geen rapport over primaire migratie of gebruikersrapport (zie hieronder).

## Belangrijkste migratierapport en gebruikersrapport {#principal-migration-report}

Wanneer groepen tijdens migratie (het gebrek) worden omvat, wordt een Hoofd Rapport van de Migratie bewaard die schetst wat aan elke groep tijdens de migratie gebeurt.  Dit rapport downloaden na een geslaagde opname:
* Ga in CAM naar Inhoud overbrengen en selecteer Ingestietaken.
* Klik op de ellips (...) op de regel van de desbetreffende inscriptie en kies Hoofdsamenvatting weergeven.
* Selecteer in het dialoogvenster dat wordt weergegeven de optie &#39;Rapport voor primaire migratie&#39; in de vervolgkeuzelijst onder &#39;Een bestand downloaden...&#39; en klik op de knop Downloaden.
* Sla het CSV-bestand op.

Een aantal van de gegevens die per groep zijn opgenomen, is:
* Indien gemigreerd, de weg aan eerste ACL of KUG die de groep veroorzaakte om worden gemigreerd.
* Of de groep eerder gemigreerd was; als de huidige inname een inname zonder sluitereffect was, kunnen sommige groepen gemigreerd zijn tijdens een eerdere inname.
* Of de groep een ingebouwde groep is; deze groepen worden niet gemigreerd omdat zij altijd op het doelAEMaaCS milieu zijn.
* Als de groep geen deel van ACL of een KUG op de gemigreerde inhoud maakte, zou het niet gemigreerd zijn.
* Als de groep een lokale groep was, zoals een groep die door een Inzameling van Assets werd gecreeerd, kan het zijn gemigreerd, en in dit geval wordt het woord &quot;lokaal&quot;toegevoegd aan het rapport voor die groep.

Tijdens migratie worden gebruikers niet gemigreerd, maar de gebruiker-groep relaties op het bronsysteem zouden verloren gaan tenzij zij op een of andere manier werden gevangen. In het Ingestieproces wordt een deel van deze informatie in tekstindeling vastgelegd in een gebruikersrapport, dat aan het einde van het rapport Hoofdmigratie staat.

### Gebruikersrapport {#user-report}

In de sectie Rapport van de Gebruiker worden de gebruikers gemeld (één per lijn) samen met hun e-mailadres en een lijst van IMS-Toegelaten groepen die tijdens deze opname werden gemigreerd.  Groepen die niet zijn gemigreerd, die tijdens een eerdere opname zijn gemigreerd of die lokale groepen zijn, worden niet in de lijst opgenomen.   Als een gebruiker niet in om het even welke gemigreerde IMS-Toegelaten groep is, en het heeft geen extra nota&#39;s erop wijzen die het een speciaal geval (zie **Nota&#39;s** hieronder) is, die gebruiker _niet_ in het rapport verschijnt. De groepen die samen met elke gebruiker worden gemeld zijn die de gebruiker direct of indirect lid van, in het bronsysteem is; aangezien de groepen in het bronsysteem kunnen worden genesteld terwijl in het doelsysteem zij niet zijn, steunt deze lijst van groepen de nieuwe afgevlakte groepsstructuur in IMS.

In het geval van een sluitereffect en vervolgens een niet-sluiteropname, zijn de groepen in de lijst van een gebruiker die geen sluitereffect hebben, alleen die groepen die tijdens de niet-sluiterfase zijn gemigreerd.

#### Notities {#user-report-notes}

Naast de groepen voor elke gebruiker, is er een gebied in het Rapport van de Gebruiker waar nota&#39;s over de gebruiker kunnen worden verstrekt (en een gedetailleerde beschrijving van de betekenis van de nota is ook in het rapport) voor informatiedoeleinden.  Mogelijke opmerkingen zijn:

* **nota-A** Gebruikers die direct in ACL van verwijzingen worden voorzien zullen *nota-A* in hun nota&#39;s sectie hebben, aangezien dit geen geadviseerd gebruiksgeval of beste praktijken is.
* **nota-B** Gebruikers die directe leden van een ingebouwde groep zijn zullen *nota-B* in hun nota&#39;s sectie hebben, aangezien dit ook geen geadviseerd gebruiksgeval of beste praktijken is.
* **nota-C** Gebruikers die direct van indirecte leden van een gemigreerde lokale groep (zoals een groep die door een Inzameling van Assets wordt gecreeerd) zijn zullen *nota-C* in hun nota&#39;s sectie hebben, aangezien de lokale groepen niet worden gevormd om door IMS te worden beheerd.

Deze gevallen kunnen tegelijkertijd en ook op hetzelfde moment als de eerdere gevallen plaatsvinden.  _voor extra informatie waarover groepen elke Nota naar voor elke gebruiker verwijst, controleer het Logboek van de Opname; het rapporteert deze informatie voor elke gebruiker._

Het Rapport van de Gebruiker wordt toegevoegd aan het eind van (en is daarom deel van) het Belangrijkste Rapport van de Migratie (zie [ Definitief Samenvatting en Rapport ](#final-summary-and-report) hieronder) om klanten een vollediger inzicht in de groepen en de gebruikers, en hun verhoudingen te geven.

## Opsommingsbestanden uploaden {#bulk-upload-files}

Aangezien groepen alleen naar AEM as a Cloud Service worden gemigreerd, moeten ze ook aan IMS worden toegevoegd, zodat ze in de cloud correct kunnen werken met AEM. Bovendien worden gebruikers niet gemigreerd, zodat zij ook aan IMS moeten worden toegevoegd. De CTT/CAM migratiehulpmiddelen voeren deze stap niet uit, maar het Ingestieproces leidt tot twee bulkupload dossiers, voor groepen en voor gebruikers. Deze bestanden kunnen worden bewerkt en vervolgens worden gebruikt, samen met de Admin Console-functionaliteit voor bulkupload, om IMS-groepen en -gebruikers te maken op basis van uw AEM-groepen en -gebruikers.

Zie [ de Groep van het Bulk en Gebruiker die aan IMS ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md) voor details over hoe te om bulk te gebruiken uploadt dossiers om gebruikers en groepen tot stand te brengen gebruikend Admin Console.

Zie ook [ gebruikers ](https://helpx.adobe.com/ca/enterprise/using/users.html) voor extra details over het beheren van de gebruikers van AEM as a Cloud Service leiden.

## Aanvullende overwegingen {#additional-considerations}

* Als het plaatsen **bestaande inhoud op de instantie van de Wolk alvorens wordt geplaatst** ontspant, worden de groepen die eerder aan de instantie van Cloud Service worden overgebracht geschrapt samen met de volledige bestaande bewaarplaats; een nieuwe bewaarplaats wordt gecreeerd waarin inhoud wordt opgenomen. Dit proces stelt ook alle montages met inbegrip van toestemmingen op de instantie van doelCloud Service terug en is waar voor om het even welke gebruiker die aan de **wordt toegevoegd beheerders** groep. De admin gebruiker moet aan de **beheerders** groep opnieuw worden toegevoegd om het toegangstoken voor Ingestie terug te winnen CTT/CAM.
* Wanneer niet-veeggebaren ingestions worden uitgevoerd (**Wipe bestaande inhoud** is unset), als de inhoud niet wordt overgebracht omdat het niet sinds de vorige overdracht is veranderd, worden de groepen verbonden aan die inhoud niet overgebracht. Deze regel geldt ook als de groepen zijn gewijzigd op het bronsysteem. Dit komt doordat groepen alleen worden gemigreerd met de inhoud waaraan ze zijn gekoppeld. Wegens dit, in dit geval zullen om het even welke groepen die lid van een groep op het bronsysteem zijn niet worden gemigreerd tenzij zij deel van een verschillende groep uitmaken die wordt gemigreerd, of in ACL van verschillende inhoud die wordt gemigreerd. Als u deze groepen nadien wilt migreren, kunt u pakketten gebruiken, groepen van het doel verwijderen en de relevante inhoud opnieuw migreren, of opnieuw migreren met een sluitereffect.
* Tijdens een niet-veeggebaar opname, als een groep met om het even welke zelfde uniek-beperkte gegevens (rep:principalName, rep:authorizableId, jcr:uid of rep:externalId) op zowel de bronAEM instantie als de doelAEM Cloud de instantie van de Dienst bestaat, is de groep in kwestie _niet_ gemigreerd en de eerder bestaande groep op het wolkensysteem blijft. Dit wordt geregistreerd in het Belangrijkste Rapport van de Migratie.
* Zie [ het Migreren van Gesloten Groepen van de Gebruiker ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen voor groepen die in een gesloten beleid van de Groep van de Gebruiker (CUG) worden gebruikt.

## Laatste samenvatting en rapport

Nadat de extractie en inname met succes zijn voltooid, wordt een rapport gegenereerd met de migratiegegevens van de groep. Zie [ hoe te de Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration) voor de details bevestigen.
