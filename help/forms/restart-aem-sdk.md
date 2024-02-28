---
title: Hoe kan AEM SDK opnieuw worden gestart?
description: Aanbevolen procedures om AEM SDK opnieuw te starten
role: Admin, Developer, User
feature: Adaptive Forms
source-git-commit: a0e2c0e3020d48b171645818b8e02dc33b50c2d5
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# De AEM SDK opnieuw starten

Als u de AEM SDK opnieuw start door de Java™-processen te stoppen, kan dit leiden tot inconsistenties in de AEM ontwikkelomgeving en treedt er een fout op als:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Start-name-sdk-error](/help/forms/assets/restart-sdk-error.png)

## Oplossing

Ga naar het actieve opdrachtvenster en druk op `Ctrl + C` om de SDK opnieuw te starten.

Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java™-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Zie ook

* [Lokale ontwikkelomgeving instellen voor AEM Forms](/help/forms/setup-local-development-environment.md)
* [Adaptieve Forms Core-componenten inschakelen](/help/forms/enable-adaptive-forms-core-components.md)
