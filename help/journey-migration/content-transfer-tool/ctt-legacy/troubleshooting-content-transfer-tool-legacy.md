---
title: Probleemoplossing voor het gereedschap Inhoud overbrengen (verouderd)
description: Problemen met het gereedschap Inhoud overbrengen oplossen
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 92%

---

# Probleemoplossing voor het gereedschap Inhoud overbrengen (verouderd) {#troubleshoot-content-transfer-tool}


## Ontbrekende blob-id&#39;s {#missing-blobs}

Als er ontbrekende blob-id&#39;s worden gerapporteerd, zoals hieronder vermeld, is het nodig een consistentiecontrole uit te voeren in de bestaande repository en de ontbrekende blobs te herstellen.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

De volgende opdracht wordt uitgevoerd 

>[!NOTE]
>
>`--verbose` markering is vereist om te rapporteren vanuit welke knooppuntpaden wordt verwezen naar de blobs.

**Voor repository&#39;s van AEM 6.5 (Oak 1.8 en lager)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Voor repository&#39;s met Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Raadpleeg [Oak Runnable Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) voor meer informatie.

De bestanden die in de *OUT_DIR* hierboven zijn gemaakt voor consistentie, kunnen vervolgens worden gecontroleerd op paden met ontbrekende binaire elementen en op de juiste manier gecorrigeerd, zoals herstellen via een back-up, paden verwijderen, opnieuw indexeren, enzovoort.


## Gedrag van gebruikersinterface {#ui-behavior}

Als gebruiker ziet u de volgende wijzigingen in het gedrag van de Content Transfer-gebruikersinterface:

* De pictogrammen in de gebruikersinterface van de Content Transfer-tool kunnen afwijken van de schermafbeeldingen die in deze handleiding worden getoond. Mogelijk worden ze zelfs helemaal niet weergegeven, afhankelijk van de versie van de AEM-broninstantie.
