---
title: Hoe kan AEM SDK opnieuw worden gestart?
description: Aanbevolen procedures om AEM SDK opnieuw te starten
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 5fec2a93-1dda-4240-8690-24a6afae5c2b
source-git-commit: 62be3c6e98df9002cdfbeef50dd5475c4daa1576
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# De AEM SDK opnieuw starten

Als u de AEM SDK opnieuw start door de Java™-processen te stoppen, kan dit leiden tot inconsistenties in de AEM ontwikkelomgeving en treedt er een fout op als:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![ nieuw begin-naam-sdk-fout ](/help/forms/assets/restart-sdk-error.png)

## Oplossing

Als u de AEM SDK opnieuw wilt starten, gaat u naar het actieve opdrachtvenster en drukt u op de opdracht `Ctrl + C` om de SDK opnieuw te starten.

Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java™-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Zie ook

* [Lokale ontwikkelomgeving instellen voor AEM Forms](/help/forms/setup-local-development-environment.md)
* [Adaptieve Forms Core-componenten inschakelen](/help/forms/enable-adaptive-forms-core-components.md)
