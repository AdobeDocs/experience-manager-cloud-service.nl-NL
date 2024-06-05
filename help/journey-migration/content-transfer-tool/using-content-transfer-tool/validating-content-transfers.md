---
title: Inhoudsoverdrachten valideren
description: Gebruik het gereedschap Inhoud overbrengen om inhoudsoverdrachten te valideren
exl-id: a12059c3-c15a-4b6d-b2f4-df128ed0eea5
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Inhoudsoverdrachten valideren {#validating-content-transfers}

## Aan de slag {#getting-started}

Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Deze validatiefunctie werkt door een overzicht te vergelijken van de paden van alle knooppunten die bij de extractie betrokken waren, met een overzicht van de paden van alle knooppunten die bij de opname betrokken waren. Als er knoopwegen inbegrepen in de extractiesamenvatting zijn die van de opname digest missen, wordt de bevestiging beschouwd als ontbroken, en de extra handbevestiging kan noodzakelijk zijn.

>[!INFO]
>
>Deze functie is beschikbaar vanaf versie 1.8.x van het Content Transfer Tool (CTT). De AEM Cloud Service-doelomgeving moet ten minste versie 6158 of hoger zijn. Het vereist ook het bronmilieu om opstelling te zijn om in werking te stellen [voorkopie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). De bevestigingseigenschap zoekt het azcopy.config- dossier op de bron. Als dit bestand niet wordt gevonden, wordt de validatie niet uitgevoerd. Meer over leren hoe te om een dossier te vormen azcopy.config, zie [deze pagina](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

Het valideren van een inhoudsoverdracht is een optionele functie. Als u deze functie inschakelt, duurt het langer om een extractie en opname uit te voeren. Om de eigenschap te gebruiken, laat het in de Console van het Systeem van de bron AEM milieu door deze stappen toe te volgen:

1. Navigeer naar de Adobe Experience Manager Web Console op uw broninstantie door naar **Gereedschappen - Bewerkingen - Webconsole** of rechtstreeks naar de URL op *https://serveraddress:serverport/system/console/configMgr*
1. Zoeken naar **Configuratie van de service Content Transfer Tool Extraction**
1. Gebruik de knop voor het potloodpictogram om de configuratiewaarden ervan te bewerken
1. De optie **Migratievalidatie tijdens extractie inschakelen** instellen en vervolgens op **Opslaan**:

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Als deze instelling is ingeschakeld en de AEM Cloud Service-doelomgeving waarop een compatibele release wordt uitgevoerd, vindt migratievalidatie plaats tijdens alle volgende extractie- en innameacties.

Voor meer informatie over het installeren van het gereedschap Inhoud overbrengen raadpleegt u [Aan de slag met het gereedschap Inhoud overbrengen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Hoe te om een Overdracht van de Inhoud te bevestigen {#how-to-validate-a-content-transfer}

Als migratievalidatie is ingeschakeld in de AEM bronomgeving, begint u met extraheren.

Indien **Stapelcontainer overschrijven tijdens extractie** wordt toegelaten, worden alle knopen die met de extractie betrokken zijn geregistreerd aan de samenvatting van de extractiepad. Wanneer deze instelling wordt gebruikt, is het belangrijk om de optie **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** instelling tijdens inname, anders lijken er wellicht knooppunten te ontbreken in de ingeslipsamenvatting. Dit zijn de knooppunten die al aanwezig zijn op het doel na eerdere inname.

Zie de volgende voorbeelden voor een grafische illustratie hiervan:

### Voorbeeld 1 {#example-1}

* **Extractie (overschrijven)**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validation-01.png)

* **Verontreiniging (sluitereffect)**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validation-02.png)

* **Notities**

  Deze combinatie van &quot;Overschrijven&quot; en &quot;Sluitereffect&quot; resulteert in consistente validatieresultaten, zelfs voor herhaalde inname.

### Voorbeeld 2 {#example-2}

* **Extractie**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validation-03.png)

* **Inname**

  ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/validation-04.png)

* **Notities**

  Deze combinatie van &quot;Overschrijven&quot; en &quot;Sluitereffect&quot; resulteert in consistente validatieresultaten voor de eerste opname.

  Als inname wordt herhaald, is de innamesamenvatting leeg en lijkt de validatie te zijn mislukt. De controlesamenvatting is leeg omdat alle knooppunten van deze extractie al aanwezig zijn op het doel.

Zodra de extractie is voltooid, begint u met innemen.

De bovenkant van het innamelogboek zal een ingang bevatten, gelijkend op `aem-ethos/tools:1.2.438`. Controleer of dit versienummer **1.2.438** of hoger, anders wordt de bevestiging niet gesteund door de versie van AEM as a Cloud Service die u gebruikt.

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

Het validatierapport kan niet alleen worden opgenomen in het innamelogboek, maar ook worden geopend vanuit de **Ingestietaken** gebruikersinterface in Cloud Acceleration Manager. Klik hiertoe op de drie stippen (**...**) en klik vervolgens op **Validatierapport** in de vervolgkeuzelijst om het validatierapport weer te geven.


![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/CTTvalidationreportnew.png)

## Hoe te om de Belangrijkste Migratie te bevestigen {#how-to-validate-principal-migration}

Zie [Toewijzing van gebruikers en belangrijkste migratie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) de belangrijkste migratiegegevens te lezen en de redenen daarvoor .

Nadat de extractie en inname met succes zijn voltooid, is een samenvatting en rapport van de belangrijkste migratie beschikbaar. Deze informatie kan worden gebruikt om te valideren welke gebruikers en groepen met succes zijn gemigreerd, en misschien om te bepalen waarom sommige niet.

Ga naar Cloud Acceleration Manager om deze informatie weer te geven. Klik op de projectkaart en klik op de kaart voor inhoudsoverdracht. Navigeren naar **Ingestietaken** en zoek de inname die u wilt controleren. Klik op de drie stippen (**...**) voor die opname, klikt u op **Hoofdoverzicht weergeven** in de vervolgkeuzelijst.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-action.png)

Er wordt een dialoogvenster weergegeven met de overzichtsgegevens. Gebruik de Help-pictogrammen om een meer volledige beschrijving te lezen. Klik op de knop **Rapport downloaden** om het volledige door komma&#39;s gescheiden (CSV) rapport te downloaden.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-dialog.png)

>[!NOTE]
>
>Als gebruikerstoewijzing is uitgeschakeld, wordt een andere variant van dit dialoogvenster weergegeven. Dit geeft aan dat gebruikerstoewijzing is uitgeschakeld en dat de drie velden met gebruikerstoewijzingswaarden niet worden weergegeven.

## Problemen oplossen {#troubleshooting}

### Validatie mislukt. Wat nu? {#validation-fail}

De eerste stap bestaat uit het bepalen of de opname echt is mislukt of of de geëxtraheerde inhoud al aanwezig is in de doelomgeving. Dit kan zich voordoen als een ingestie wordt herhaald met de **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** optie uitgeschakeld.

Kies een pad in het validatierapport en controleer of dit aanwezig is in de doelomgeving. Als dit een publicatieomgeving is, kunt u zich beperken tot het rechtstreeks controleren van pagina&#39;s en middelen. Open een ticket met de klantenservice als u hulp nodig hebt bij deze stap.

### Het aantal knooppunten is lager dan ik had verwacht. Waarom is dat? {#node-count-lower-than-expected}

Sommige paden uit de extractie- en innamesamenvattingen worden doelbewust uitgesloten om de grootte van deze bestanden beheerbaar te houden, met als doel het resultaat van de migratievalidatie binnen twee uur na voltooiing van de inname te kunnen berekenen.

De paden die we momenteel uitsluiten van de samenvattingen zijn: `cqdam.text.txt` vertoningen, knooppunten binnen `/home`en knooppunten binnen `/jcr:system`.

### Gesloten gebruikersgroepen functioneren niet {#validating-cugs}

Zie [Gesloten gebruikersgroepen migreren](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen wanneer het gebruiken van een Gesloten beleid van de Groep van de Gebruiker (CUG).
