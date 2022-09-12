---
title: Inhoudsoverdrachten valideren (verouderd)
description: Gebruik het gereedschap Inhoud overbrengen om inhoudsoverdrachten te valideren
hide: true
hidefromtoc: true
exl-id: 304b7aee-1d84-4d90-a89b-0c532d5d9c92
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 1%

---

# Inhoudsoverdrachten valideren (verouderd) {#validating-content-transfers}

## Aan de slag {#getting-started}

Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Deze validatiefunctie werkt door een overzicht te vergelijken van de knooppunten die bij de extractie betrokken waren, met een overzicht van de knooppunten die bij de opname betrokken waren. Als er knoopwegen inbegrepen in de extractiesamenvatting zijn die van de opname digest missen, wordt de bevestiging beschouwd als ontbroken, en de extra handbevestiging kan noodzakelijk zijn.

>[!INFO]
>
>Deze functie is beschikbaar vanaf versie 1.8.x van het Content Transfer Tool (CTT). De AEM Cloud Service-doelomgeving moet ten minste versie 6158 of hoger zijn. Het vereist ook het bronmilieu om opstelling te zijn om in werking te stellen [voorkopie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). De bevestigingseigenschap zoekt het azcopy.config- dossier op de bron. Als dit bestand niet wordt gevonden, wordt de validatie niet uitgevoerd. Meer over leren hoe te om een dossier te vormen azcopy.config, zie [deze pagina](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

Het valideren van een inhoudsoverdracht is een optionele functie. Als u deze functie inschakelt, duurt het langer om zowel een extractie als een opname uit te voeren. Om de eigenschap te gebruiken, laat het in de Console van het Systeem van het bron AEM milieu door deze stappen toe te volgen:

1. Navigeer naar de Adobe Experience Manager Web Console op uw broninstantie door naar **Gereedschappen - Bewerkingen - Webconsole** of rechtstreeks naar de URL op *https://serveraddress:serverport/system/console/configMgr*
1. Zoeken naar **Configuratie van de service Content Transfer Tool Extraction**
1. Gebruik de knop voor het potloodpictogram om de configuratiewaarden ervan te bewerken
1. De optie **Migratievalidatie tijdens extractie inschakelen** instellen en vervolgens op **Opslaan**:

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Als deze instelling is ingeschakeld en de AEM Cloud Service-doelomgeving waarop een compatibele release wordt uitgevoerd, vindt migratievalidatie plaats tijdens alle volgende extractie- en innameacties.

Voor meer informatie over het installeren van het gereedschap Inhoud overbrengen raadpleegt u [Aan de slag met het gereedschap Inhoud overbrengen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Hoe te om een Overdracht van de Inhoud te bevestigen {#how-to-validate-a-content-transfer}

Als migratievalidatie is ingeschakeld in de AEM bronomgeving, begint u met extraheren.

Indien **Stapelcontainer overschrijven tijdens extractie** wordt toegelaten, zullen alle knopen die met de extractie betrokken zijn aan de samenvatting van de extractiepad worden geregistreerd. Wanneer deze instelling wordt gebruikt, is het belangrijk om de optie **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** instelling tijdens inname, anders lijken er wellicht knooppunten te ontbreken in de ingeslipsamenvatting. Dit zijn de knooppunten die al aanwezig zijn op het doel na eerdere inname.

Voor een grafische illustratie hiervan, verwijs naar de voorbeelden hieronder:

### Voorbeeld 1 {#example-1}

* **Extractie (overschrijven)**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTextractionoverwrite.png)

* **Verontreiniging (sluitereffect)**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTingestionwipe.png)

* **Opmerkingen**

   Deze combinatie van &quot;Overschrijven&quot; en &quot;Sluitereffect&quot; resulteert in consistente validatieresultaten, zelfs voor herhaalde inname.

### Voorbeeld 2 {#example-2}

* **Extractie**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTextraction.png)

* **Inname**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTingestion.png)

* **Opmerkingen**

   Deze combinatie van &quot;Overschrijven&quot; en &quot;Sluitereffect&quot; resulteert in consistente validatieresultaten voor de eerste opname.

   Als inname wordt herhaald, is de innamesamenvatting leeg en lijkt de validatie te zijn mislukt. De controlesamenvatting is leeg omdat alle knooppunten van deze extractie al aanwezig zijn op het doel.

Zodra de extractie is voltooid, begint u met innemen.

De bovenkant van het innamelogboek zal een ingang bevatten, gelijkend op `aem-ethos/tools:1.2.438`. Controleer of dit versienummer **1.2.438** of hoger, anders wordt de bevestiging niet gesteund door de versie van AEM as a Cloud Service die u gebruikt.

Zodra de opname volledig is en de bevestiging begint, zal de volgende logboekingang in het innamelogboek worden genoteerd:

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

Om te vergelijken, hier is hoe een bevestigingsrapport zou kijken als de bevestiging had ontbroken:

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
Please refer to our Migration Validation FAQ (https://www.adobe.com/go/aem_cloud_ctt_validation_en) or open a ticket with Customer Care.
There are 4635 entries present in the extraction digest that are missing from the ingestion digest.
/content/dam/bruce
/content/dam/bruce-assets
... more paths listed (up to 10k) ...
----------------------------------------------------------
Comparing the path digests took 0 seconds
Migration validation took 0 minutes
```

Het bovenstaande mislukkingsvoorbeeld werd bereikt door een opname in werking te stellen, en dan opnieuw de zelfde inname opnieuw in werking te stellen met Wipe gehandicapt, zodat geen knopen tijdens inname betrokken waren — alles was reeds aanwezig op het doel.

Het validatierapport is niet alleen opgenomen in het innamelogboek, maar kan ook worden geopend vanuit de gebruikersinterface van het gereedschap Inhoudsoverdracht. Selecteer hiertoe een migratieset en klik op de knop **Valideren** knop op de actiebalk:


![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTvalidatebutton.png)

Het dialoogvenster Validatielogbestanden wordt geopend:

![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTvalidationlogs.png)

Gebruik de **Rapport voor publicatie/auteur van validatie** om het validatierapport te bekijken voor de meest recente opname in de opgegeven laag van uw doelomgeving. Zie hieronder een voorbeeld van een kleine publicatieopname:

![afbeelding](/help/journey-migration/content-transfer-tool/assets/CTTvalidationreport.png)

>[!NOTE]
>
>De **Rapport voor publicatie/auteur van validatie** Als de inname is voltooid, verschijnt er een koppeling. Bovendien, blijven de bevestigingsrapporten voortbestaan, zodat verlopen zij niet nadat de opname voltooit, zoals de innamelogboeken.

## Problemen oplossen {#troubleshooting}

### Validatie mislukt. Wat nu? {#validation-fail}

De eerste stap bestaat uit het bepalen of de opname echt is mislukt of of de geëxtraheerde inhoud al aanwezig is in de doelomgeving. Dit kan zich voordoen als een ingestie wordt herhaald met de **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** optie uitgeschakeld.

Kies een pad in het validatierapport en controleer of dit aanwezig is in de doelomgeving. Als dit een publicatieomgeving is, kunt u zich beperken tot het rechtstreeks controleren van pagina&#39;s en middelen. Open een ticket met de klantenservice als u hulp nodig hebt bij deze stap.

### Het aantal knooppunten is lager dan ik had verwacht. Waarom is dat? {#node-count-lower-than-expected}

Sommige paden uit de extractie- en innamesamenvattingen worden doelbewust uitgesloten om de grootte van deze bestanden beheerbaar te houden, met als doel het resultaat van de migratievalidatie binnen twee uur na voltooiing van de inname te kunnen berekenen.

De paden die we momenteel uitsluiten van de samenvattingen zijn: `cqdam.text.txt` vertoningen, knooppunten binnen `/home`en knooppunten binnen `/jcr:system`.
