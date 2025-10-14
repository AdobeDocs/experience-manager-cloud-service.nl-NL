---
title: Inhoudsoverdrachten valideren
description: Gebruik het gereedschap Inhoud overbrengen om inhoudsoverdrachten te valideren
exl-id: a12059c3-c15a-4b6d-b2f4-df128ed0eea5
feature: Migration
role: Admin
source-git-commit: 9b05ed38e8eb337b3a07ee2051c6a0d530088af2
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 0%

---


# Inhoudsoverdrachten valideren {#validating-content-transfers}

## Aan de slag {#getting-started}

Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Deze validatiefunctie werkt door een overzicht te vergelijken van de paden van alle knooppunten die bij de extractie betrokken waren, met een overzicht van de paden van alle knooppunten die bij de opname betrokken waren. Als er knoopwegen inbegrepen in de extractiesamenvatting zijn die van de opname digest missen, wordt de bevestiging beschouwd als ontbroken, en de extra handbevestiging kan noodzakelijk zijn.

>[!INFO]
>
>Deze functie is beschikbaar vanaf versie 1.8.x van het Content Transfer Tool (CTT). De doelomgeving van AEM Cloud Service moet ten minste versie 6158 of hoger zijn. Het vereist ook het bronmilieu om opstelling te zijn om [&#x200B; pre-exemplaar &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step) in werking te stellen. De bevestigingseigenschap zoekt het azcopy.config- dossier op de bron. Als dit bestand niet wordt gevonden, wordt de validatie niet uitgevoerd. Meer over leren hoe te om een dossier te vormen azcopy.config, zie [&#x200B; Behandelend Grote Inhoudsbewaarplaatsen van de Inhoud - vorm een dossier azcopy.config &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

Het valideren van een inhoudsoverdracht is een optionele functie. Als u deze functie inschakelt, duurt het langer om een extractie en opname uit te voeren. Als u deze functie wilt gebruiken, schakelt u deze in de System Console van de AEM-bronomgeving in door de volgende stappen uit te voeren:

1. Navigeer aan de Console van het Web van Adobe Experience Manager op uw broninstantie, door **Hulpmiddelen te gaan - Verrichtingen - de Console van het Web** of direct aan URL in *https://serveraddress:serverport/system/console/configMgr*
1. Onderzoek naar {de Configuratie van de Dienst van de Extractie van het Hulpmiddel van de Overdracht van 0} Inhoud **&#x200B;**
1. Gebruik de knop voor het potloodpictogram om de configuratiewaarden ervan te bewerken
1. Laat **toe de Bevestiging van de Migratie tijdens extractie** plaatsen, dan druk **sparen**:

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Als deze instelling is ingeschakeld en de AEM Cloud Service-doelomgeving een compatibele release uitvoert, vindt migratievalidatie plaats tijdens alle volgende extractie- en insluitingen.

Voor meer informatie over hoe te om het Hulpmiddel van de Overdracht van de Inhoud te installeren, zie [&#x200B; Begonnen het Worden met het Hulpmiddel van de Overdracht van de Inhoud &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Hoe te om een Overdracht van de Inhoud te bevestigen {#how-to-validate-a-content-transfer}

Als migratievalidatie is ingeschakeld in de AEM-bronomgeving, begint u met extraheren.

Als **staging container tijdens extractie** overschrijft wordt toegelaten, worden alle knopen die met de extractie betrokken zijn geregistreerd aan de samenvatting van de extractieweg. Wanneer dit het plaatsen wordt gebruikt, is het belangrijk om **toe te laten Wipe bestaande inhoud op de instantie van de Wolk alvorens** het plaatsen in te nemen tijdens opname, anders kunnen er knopen missen van de ingestipingssamenvatting lijken. Dit zijn de knooppunten die al aanwezig zijn op het doel na eerdere inname.

Zie de volgende voorbeelden voor een grafische illustratie hiervan:

### Voorbeeld 1 {#example-1}

* **Extractie (Overschrijven)**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/example1-extraction.png)

* **Ingestie (Sluitereffect)**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validation-02.png)

* **Nota&#39;s**

  Deze combinatie van &quot;Overschrijven&quot; en &quot;Sluitereffect&quot; resulteert in consistente validatieresultaten, zelfs voor herhaalde inname.

### Voorbeeld 2 {#example-2}

* **Extractie**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/example2-extraction.png)

* **Ingestie**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validation-04.png)

* **Nota&#39;s**

  Deze combinatie van &quot;Overschrijven&quot; en &quot;Sluitereffect&quot; resulteert in consistente validatieresultaten voor de eerste opname.

  Als inname wordt herhaald, is de innamesamenvatting leeg en lijkt de validatie te zijn mislukt. De controlesamenvatting is leeg omdat alle knooppunten van deze extractie al aanwezig zijn op het doel.

Zodra de extractie is voltooid, begint u met innemen.

De bovenkant van het innamelogboek bevat een item, vergelijkbaar met `aem-ethos/tools:1.2.438` . Verzeker dit versieaantal **1.2.438** of groter is, anders wordt de bevestiging niet gesteund door de versie van AEM as a Cloud Service die u gebruikt.

Nadat de opname volledig is en de bevestiging begint, wordt de volgende logboekingang genoteerd in het innamelogboek:

```
Gathering artifacts for migration validation...
```

De details van de validatie volgen op deze vermelding. Hier vindt u een voorbeeld van een grote migratie:

```
Beginning publish migration validation. Migration job id=[3aba1f96-84b6-4bd0-8642-c61c0d528387]
Extraction path digest is being processed...
Extraction path digest processing took 982 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 999 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 51674784
INGESTION: Number of nodes ingested: 51674784
----------------------------------------------------------
Validation succeeded! No entries were detected to be missing from the ingestion digest.
----------------------------------------------------------
Comparing the path digests took 29 seconds
Migration validation took 33 minutes
```

Dit is een voorbeeld van een validatie die is geslaagd, aangezien er geen items ontbraken in de opname-digest die aanwezig waren in de extractiedigest.

Om te vergelijken, is hier hoe een bevestigingsrapport zou kijken als de bevestiging (of als een top-up migratie werd uitgevoerd) ontbrak:

```
Beginning publish migration validation. Migration job id=[ac217e5a-a08d-4e81-cbd6-f39f88b174ce]
Extraction path digest is being processed...
Extraction path digest processing took 0 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 0 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 4635
INGESTION: Number of nodes ingested: 0
----------------------------------------------------------
Validation failed. However, the following nodes may already be present in the target environment.
See our Migration Validation FAQ (https://www.adobe.com/go/aem_cloud_ctt_validation_en) or open a ticket with Customer Care.
There are 4635 entries present in the extraction digest that are missing from the ingestion digest.
/content/dam/bruce
/content/dam/bruce-assets
... more paths listed (up to 10k) ...
----------------------------------------------------------
Comparing the path digests took 0 seconds
Migration validation took 0 minutes
```

Het bovenstaande mislukkingsvoorbeeld werd bereikt door een opname in werking te stellen, en dan opnieuw de zelfde inname opnieuw in werking te stellen met Wipe gehandicapt, zodat geen knopen tijdens inname betrokken waren — alles was reeds aanwezig op het doel.

Naast wordt inbegrepen in het innamelogboek, kan het bevestigingsrapport ook van het **1&rbrace; gebruikersinterface van de Banen van de Ingestie &lbrace;in Cloud Acceleration Manager worden betreden.** Om dit te doen, klik de drie punten (**..**) dan **het rapport van de Bevestiging** in drop-down om het bevestigingsrapport te bekijken.


![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/CTTvalidationreportnew.png)

## Hoe te om de Belangrijkste Migratie te bevestigen {#how-to-validate-group-migration}

Zie [&#128279;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) de Migratie van de Groep van 0&rbrace; om de belangrijkste migratiedetails te lezen en waarom het noodzakelijk is.

Nadat de extractie en inname met succes zijn voltooid, is een samenvatting en rapport van de belangrijkste migratie beschikbaar. Deze informatie kan worden gebruikt om te valideren welke groepen succesvol zijn gemigreerd, en misschien om te bepalen waarom sommige niet.

Ga naar Cloud Acceleration Manager om deze gegevens te bekijken. Klik op de projectkaart en klik op de kaart voor inhoudsoverdracht. Navigeer aan **Banen van de Opname** en bepaal de plaats van de opname die u wilt verifiëren. Klik de drie punten (**...**) voor die opname, dan klik **belangrijkste samenvatting van de Mening** in drop-down.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-action.png)

Er wordt een dialoogvenster weergegeven met de overzichtsgegevens. Gebruik de Help-pictogrammen om een meer volledige beschrijving te lezen. Om het volledige komma-gescheiden (CSV) Belangrijkste Rapport van de Migratie te downloaden **Belangrijkste Rapport van de Migratie** van de drop-down lijst onder **Download een dossier...** en klik de **Download** knoop. Merk ook op dat aan het eind van dit rapport het Rapport van de Gebruiker is, dat voor post-migratie gebruikersbeheer kan worden gebruikt.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-dialog.png)

In het rapport &quot;Belangrijkste migratie&quot; wordt het volgende vermeld:

* Elke groep is gemigreerd en het eerste inhoudspad dat ertoe heeft geleid dat die groep is gemigreerd. De groep kan zich ook op andere paden bevinden, maar alleen het eerste pad dat voor een bepaalde groep is gevonden, wordt gerapporteerd. Het meldt ook of het in ACL of een beleid van de CUG werd gevonden.
* Elke groep die als een lokale groep is gemigreerd, krijgt het woord &quot;lokaal&quot; dat op de regel van de groep wordt aangegeven.
* Elke groep is niet gemigreerd en de reden waarom deze niet is gemigreerd.  Doorgaans is dit een van de volgende redenen:
   * Het is een ingebouwde groep
   * Het bevindt zich al op het doelsysteem
   * Het is niet in ACL of het beleid van de CUG over de inhoud die wordt gemigreerd
   * Het heeft een dubbel uniek gebied (één van rep:principalName, rep:authorizableId, jcr:uid of rep:externalId is reeds op de bestemming, maar deze allen moeten uniek zijn)

## Problemen oplossen {#troubleshooting}

### Validatie mislukt. Wat nu? {#validation-fail}

De eerste stap bestaat uit het bepalen of de opname echt is mislukt of of de geëxtraheerde inhoud al aanwezig is in de doelomgeving. Dit kan voorkomen als een opname met **wordt herhaald Wipe bestaande inhoud op de instantie van de Wolk alvorens inname** gehandicapte optie.

Kies een pad in het validatierapport en controleer of dit aanwezig is in de doelomgeving. Als dit een publicatieomgeving is, kunt u zich beperken tot het rechtstreeks controleren van pagina&#39;s en middelen. Open een ticket met de klantenservice als u hulp nodig hebt bij deze stap.

### Het aantal knooppunten is lager dan ik had verwacht. Waarom is dat? {#node-count-lower-than-expected}

Sommige paden uit de extractie- en innamesamenvattingen worden doelbewust uitgesloten om de grootte van deze bestanden beheerbaar te houden, met als doel het resultaat van de migratievalidatie binnen twee uur na voltooiing van de inname te kunnen berekenen.

De paden die we momenteel uitsluiten van de samenvattingen zijn: `cqdam.text.txt` uitvoeringen, knooppunten binnen `/home` en knooppunten binnen `/jcr:system` .

### Gesloten gebruikersgroepen {#validating-cugs}

Zie [&#x200B; het Migreren van Gesloten Groepen van de Gebruiker &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen wanneer het gebruiken van een Gesloten beleid van de Groep van de Gebruiker (CUG).
