---
title: Upgrade uw inhoudsfragmenten voor UUID-verwijzingen
description: Leer hoe u de inhoudsfragmenten kunt upgraden voor geoptimaliseerde UUID-verwijzingen in Adobe Experience Manager as a Cloud Service voor het leveren van inhoud zonder kop.
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
exl-id: 004d1340-8e3a-4e9a-82dc-fa013cea45a7
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---

# Upgrade uw inhoudsfragmenten voor UUID-verwijzingen {#upgrade-content-fragments-for-UUID-references}

Om de stabiliteit van uw filters van GraphQL te optimaliseren, kunt u de inhoud en fragmentverwijzingen in uw Inhoudsfragmenten bevorderen zodat zij universeel unieke herkenningstekens (UUID) gebruiken.

Oorspronkelijk verstrekten de Modellen van het Fragment van de Inhoud de gegevenstypes van **Verwijzing van de Inhoud** en **Verwijzing van het Fragment**. Beide verwijzingen gebruiken een weg om aan het referenced middel te richten, en deze weg kan verouderd worden als het middel wordt bewogen. Hoewel dergelijke verwijzingen in de meeste scenario&#39;s meer dan toereikend zijn, zijn de Modellen van het Fragment van de Inhoud uitgebreid om verwijzingen ook te verstrekken die op UUID worden gebaseerd:

* **Verwijzing van de Inhoud (UUID)**
* **Verwijzing van het Fragment (UUID)**.

Deze nieuwe referentietypen kunnen zowel in nieuwe modellen en fragmenten van het Fragment van de Inhoud worden gebruikt als bestaande instanties uitbreiden.

Als u bestaande inhoudsfragmenten en -modellen wilt bijwerken, kunt u de hier beschreven procedure uitvoeren.

>[!CAUTION]
>
>Alvorens de verbeteringsprocedure in werking te stellen zou u [&#x200B; een droge looppas &#x200B;](#execute-a-dry-run) altijd moeten uitvoeren om het even welke potentiële kwesties met uw inhoud te benadrukken.

## Wat is bijgewerkt {#what-is-upgraded}

De volgende updates worden uitgevoerd:

* Velden van de gegevenstypen:
   * **Verwijzing van de Inhoud** wordt omgezet in **Verwijzing van de Inhoud (UUID)**
   * **Verwijzing van het fragment** wordt omgezet in **Verwijzing van het Fragment (UUID)**
* De waarden van de op paden gebaseerde verwijzingen in deze velden worden vervangen door de overeenkomstige UUID&#39;s

>[!NOTE]
>
>Na de verbetering zijn beide Types van Gegevens nog beschikbaar in de Modelredacteur van het Fragment van de Inhoud. U kunt nieuwe velden maken op basis van beide typen (hoewel u de op UUID gebaseerde typen zult gebruiken) en de upgrade indien nodig opnieuw uitvoeren.

## Wat NIET is bijgewerkt {#what-is-not-upgraded}

De volgende referenties worden niet bijgewerkt:

* Paginaverwijzingen - UUID&#39;s worden nog niet ondersteund
* Ongeldige verwijzingen, bijvoorbeeld wanneer het doel van het pad van het inhoudsfragment of het middelenpad niet bestaat

   * Ongeldige verwijzingen worden niet bijgewerkt, alsof het pad van het inhoudsfragment of het middelenpad ongeldig is. Er is geen overeenkomstige UUID die moet worden toegewezen. De oorspronkelijke verwijzing blijft ongewijzigd.

   * Gebruik a [&#x200B; droge looppas &#x200B;](#execute-a-dry-run) om het even welke ongeldige verwijzingen te ontmoedigen.

  >[!NOTE]
  >
  >Als ongeldig, zijn zij niet bruikbaar, ongeacht de verbetering.

## Wanneer u geen upgrade moet uitvoeren {#when-you-should-not-upgrade}

Geen upgrade uitvoeren:

* Wanneer een van uw inhoudsfragmenten paginaverwijzingen gebruikt; aangezien UUID&#39;s nog niet worden ondersteund voor paginaverwijzingen

## Beperkingen van UUID-verwijzingen {#limitations-of-uuid-references}

Momenteel zijn de volgende beperkingen van toepassing wanneer het gebruiken van verwijzingen die op een UUID worden gebaseerd:

* Modellen

   * Nieuwe Content Fragment-modellen met UUID-velden voor inhoudsfragment of UUID-velden voor inhoudsverwijzing kunnen niet worden gemaakt met OpenAPI.
   * Het veld `id` voor modellen is niet gewijzigd in UUID-gebaseerd. Het gebruikt base64 gedecodeerde weg van het model. Modellen kunnen niet worden verplaatst, zodat deze waarde nog steeds stabiel is.

* Assets

   * Wanneer u een inhoudsfragment maakt via OpenAPI, moeten `fragment-reference` - of `content-reference` -veldtypen worden gebruikt voor het opgeven van verwijzingen naar respectievelijk een fragment of element, zelfs wanneer u de waarde van een verwijzingsveld op basis van UUID instelt.

## Upgradeplanning {#upgrade-planning}

Er zijn een paar voorbereidingsstappen voordat u de upgrade uitvoert.

### Een droge run uitvoeren {#execute-a-dry-run}

Het wordt geadviseerd dat *elke* tijd u uw inhoud bevordert, u eerst een droge looppas uitvoert. Hiermee worden logbestanden gemaakt met items die mogelijke problemen aangeven:

* Ongeldige verwijzingen
* Paginaverwijzingen

Voer de upgrade van de inhoud in de modus `dryRun` uit naar:

* eventuele ongeldige verwijzingen identificeren; door deze weer te geven in de logbestanden
U kunt deze verwijzingen vervolgens corrigeren voordat u de daadwerkelijke upgrade van de inhoud uitvoert.
* alle paginaverwijzingen identificeren; door deze weer te geven in de logbestanden
Wanneer de paginaverwijzingen worden ontdekt zou u [&#x200B; niet de inhoudsverbetering &#x200B;](#when-you-should-not-upgrade) in werking moeten stellen.


### Inhoud bevriezen {#enforce-a-content-freeze}

De uitvoering van de upgrade van de inhoud moet worden gepland tijdens een periode waarin de inhoud wordt vastgezet.

De duur van het vastzetten van de inhoud is afhankelijk van het volume van de inhoudsfragmenten die worden bijgewerkt. De upgrade kan dan ook een paar minuten tot een paar uur duren en is afhankelijk van de parameters die worden gebruikt bij het starten van de upgrade van de inhoud.

## De upgrade van de inhoud uitvoeren {#running-the-content-upgrade}

De inhoudsupgrade kan worden beheerd met behulp van het eindpunt: `/libs/dam/cfm/maintenance.json`

>[!NOTE]
>
>Uw account heeft de `Administrator` -rol nodig om toegang te krijgen tot het eindpunt.

### Een upgrade van de inhoud starten {#start-a-content-upgrade}

| Endpoint | HTTP-aanvraagtype | Opmerking |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **de parameters van het Verzoek** | **Waarde** | |
| action | `start` | |
| serviceTypeId | `uuidUpgradeService` | De service type-id (vooraf gedefinieerde, vaste waarde). |
|  segmentSize | `1000` | Het aantal Inhoudsfragmenten of -modellen dat in één segment (batch) wordt bijgewerkt. |
| basePath | `/conf` | Geef een van de volgende instellingen op:<ul><li>de basis `/conf` om alle AEM-configuraties te upgraden</li><li>een geselecteerd AEM-configuratiepad. waarvoor de inhoudsupgrade wordt uitgevoerd <br> Bijvoorbeeld: `/conf/wknd-shared` bevordert slechts één enkele huurder `wknd-shared`</li></ul> |
| interval | `10` | Interval in seconden, waarna het volgende segment van Inhoudsfragmenten, of modellen wordt bevorderd. |
| mode | `replicate`, `noReplicate` | <ul><li>`replicate`: dezelfde taak wordt op alle publicatie-instanties van AEM overgenomen</li><li>`noReplicate`: voert de taak alleen uit op instanties van AEM Author</li></ul> |
| dryRun |  `true`, `false` | <ul><li>`false`: de upgrade van de inhoud simuleren, zonder wijzigingen in de inhoud op te slaan</li><li>`true`: voer de upgrade van de inhoud uit en sla wijzigingen in de inhoud op</li></ul> |
| **Details van de Reactie** | **Waarde** | |
| jobId | `UUID` |  De id van de taak die de upgrade van de inhoud uitvoert.<ul><li>Deze identiteitskaart wordt vereist in om het even welke verdere vraag met betrekking tot deze uitvoering.</li><li>Als de `mode` -waarde is ingesteld op `replicate` , moet de uitvoering in AEM Publish-instanties ook onder dezelfde `jobId` staan.</li></ul> |
| parameters | De parameters voor het upgraden van de inhoud | Deze omvatten de aanvankelijke parameters die worden verstrekt om de inhoudsupgrade te beginnen, en sommige interne gebreken. |


### Aanvraag voor upgrade van inhoud {#example-content-upgrade-request}

+++Verzoek

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
 
{
    "action": "start",
    "serviceTypeId": "uuidUpgradeService",
    "segmentSize": 1000,
    "basePath": "/conf/wknd-shared",
    "interval": 10,
    "mode": "replicate",
    "dryRun": true
}
```

+++

+++Antwoord

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:34:37 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 386
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "basePath": "/conf/wknd-shared",
    "topic": "cfm/maintenance",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  }
}
```

+++

### De status van een contentupgrade ophalen {#get-the-status-of-a-content-upgrade}

| Endpoint | HTTP-aanvraagtype | Opmerking |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `GET` | |
| **de parameters van het Verzoek** | **Waarde** | |
| action | status | |
| jobId | `<UUID>` | De `jobId` die is geretourneerd van de aanroep om de upgrade van de inhoud te starten. |
| **Details van de Reactie** | **Waarde** | |
| status | JSON-waarden | Bevat de gedetailleerde status van de upgrade van de inhoud:<ul><li>Bijgewerkt na elk interval (seconden).</li><li>`uuidUpgradeService` -uitvoering bestaat uit twee fasen:<ol><li>fase-0 om de modellen van het inhoudsfragment te bevorderen</li><li>fase-1 voor het bijwerken van inhoudsfragmenten</li></ol></li><li>In elke fase, worden de statistieken bijgewerkt na elk interval.</li><li>&quot;jobStatus&quot;: &quot;COMPLETED&quot; markeert dat de upgrade is voltooid.</li><li>Andere statuswaarden zijn een uitleg.</li></ul> |

### Voorbeeld van statusaanvraag voor upgrade van inhoud {#example-content-upgrade-status-request}

+++Verzoek

```http
GET http://localhost:4502/libs/dam/cfm/maintenance.json?action=status&jobId=91af43a6-63ff-45e5-ac7b-06ccf565bdfa
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
```

+++

+++Antwoord

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:35:51 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 1116
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "eventProcessed": 1,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "confPath": "/conf/wknd-shared",
    "topic": "cfm/uuid-migration",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  },
  "status": {
    "jobStatus": "COMPLETED",
    "lastModified": 1729089310301,
    "currentPhaseIndex": 1,
    "phases": {
      "phase-0": {
        "bookmark": 1727183332520,
        "stats": {
          "successCount": 2,
          "skippedCount": 1,
          "errorCount": 0
        },
        "name": "modelUpgrade",
        "lastModified": 1729089290040,
        "isCompleted": true
      },
      "phase-1": {
        "bookmark": 1727183347990,
        "stats": {
          "successCount": 29,
          "skippedCount": 0,
          "errorCount": 1
        },
        "name": "cfUpgrade",
        "lastModified": 1729089310298,
        "isCompleted": true
      }
    }
  }
}
```

+++

+++Voorbeeldlogbestanden

Naast de status van een actieve inhoudsupgrade die wordt verkregen van het HTTP-eindpunt, bieden AEM-logboeken gedetailleerde informatie over de voortgang op het inhoudsniveau. Bijvoorbeeld:

```xml
#Successful model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/article , status: SUCCESS, skips: [], errors: []
 
#Successful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/san-diego-surf-spots/san-diego-surfspots , status: SUCCESS, skips: [], errors: []
 
#Unsuccessful/Skipped model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/adventure , status: SKIPPED, skips: [Model: '/conf/wknd-shared/settings/dam/cfm/models/adventure', no upgradeable fields found], errors: []
 
#Unsuccessful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van , status: FAILED, skips: [], errors: [Path '/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van', Variation: 'master' Field 'featuredImage', Value '/content/dam/wknd-shared/en/magazine/western-australia/adobestock_156407519.jpeg' is invalid; will not upgrade this field.] 
```

Bovendien, na de verwerking van elk segment (partij) van de Fragmenten en de Modellen van de Inhoud, wordt een geaccumuleerde status geregistreerd, die de vooruitgang tot dusver samenvatten. Bijvoorbeeld:

```xml
com.adobe.cq.dam.cfm.impl.servicing.PhaseChainProcessor Phase phase-x, processed a segment, stats: {successCount=29, skippedCount=0, errorCount=1}
```

+++

### Een upgrade van inhoud afbreken {#abort-a-content-upgrade}

>[!CAUTION]
>
>Een inhoudsupgrade afbreken (dat is geen droog programma):
>
>* worden reeds aangebrachte wijzigingen niet ongedaan gemaakt
>* inhoud mogelijk in een gemengde status laten
>
>Wees voorzichtig met deze handeling.

| Endpoint | HTTP-aanvraagtype | Opmerking |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **de parameters van het Verzoek** | **Waarde** | |
| action | afbreken | |
| jobId | `<UUID>` | De `jobId` die is geretourneerd van de aanroep om de upgrade van de inhoud te starten. |
| **Details van de Reactie** | **Waarde** | |
| status | JSON-waarden | Bevat de gedetailleerde status van de upgrade van de inhoud:<ul><li>De status om op te merken is &quot;jobStatus&quot;: &quot;ABORTED&quot;.<br> na een afbreekactie, zullen om het even welke hangende segmenten van gegevens niet worden verwerkt.</li><li>Als jobStatus &quot;COMPLETED&quot;vóór een abort is, heeft de vraag geen effect.</li></ul> |

### Voorbeeld Een aanvraag voor een upgrade van inhoud afbreken {#example-abort-content-upgrade-request}

+++Verzoek

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: Basic YWRtaW46YWRtaW4=
Accept: application/json
 
{
    "action": "abort",
    "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807"
    "mode": "replicate",
}
```

+++

+++Antwoord

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:39:03 GMT
 
{
  "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807",
   ...
  "eventProcessed": 2,
  "parameters": {
    ...
    "abort": true,
    ...
  },
  "status": {
     "jobStatus": "ABORTED",
    ...
  }
}
```

+++
