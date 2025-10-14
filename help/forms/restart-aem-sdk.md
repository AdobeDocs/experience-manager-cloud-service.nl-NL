---
title: Hoe start u AEM SDK opnieuw?
description: Aanbevolen procedures voor het opnieuw opstarten van AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 5fec2a93-1dda-4240-8690-24a6afae5c2b
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# AEM SDK opnieuw opstarten

Als u de AEM SDK opnieuw start door de Java™-processen te stoppen, kan dit leiden tot inconsistenties in de AEM-ontwikkelomgeving en treedt er een fout op als:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![&#x200B; nieuw begin-naam-sdk-fout &#x200B;](/help/forms/assets/restart-sdk-error.png)

## Oplossing

Als u de AEM SDK opnieuw wilt starten, gaat u naar het actieve opdrachtvenster en drukt u op de opdracht `Ctrl + C` om de SDK opnieuw te starten.

U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java™-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

## Zie ook

* [Lokale ontwikkelomgeving instellen voor AEM Forms](/help/forms/setup-local-development-environment.md)

