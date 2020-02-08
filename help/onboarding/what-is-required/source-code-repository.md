---
title: Inschrijving broncode - cloudservices
description: Inschrijving broncode - cloudservices
translation-type: tm+mt
source-git-commit: 6f323f33663f83043eb8a15fe00e6ed872c3cac1

---


# Broncodeopslagplaats {#source-code-repository}

Cloud Manager-programma wordt automatisch ingericht met de eigen git-opslagruimte van het programma.

Gebruikers kunnen alleen toegang krijgen tot de gegevensopslagruimte van Cloud Manager als ze een Git-client gebruiken met een opdrachtregelprogramma, een zelfstandige visuele Git-client of de IDE van de gebruiker, zoals Eclipse, IntelliJ, NetBeans.

Zodra een Git-client is ingesteld, kunt u de git-opslagplaats beheren vanuit de interface van Cloud Manager. Als u wilt weten hoe u Git beheert met de interface van Cloud Manager, raadpleegt u [Toegang tot Git](/help/implementing/cloud-manager/accessing-git.md).

Als u de AEM Cloud-toepassing wilt gaan ontwikkelen, moet u een lokale kopie van de toepassingscode maken door deze uit te checken van de opslagplaats van Cloud Manager naar een locatie op de lokale computer waar ze hun opslagplaats willen maken.

```java
$ git clone {URL}
```

> [!NOTE]
> Een gebruiker kan een kopie van de code uitchecken en wijzigingen aanbrengen in de lokale gegevensopslagruimte. Als de gebruiker klaar is, kan hij of zij de wijzigingen in de code doorvoeren naar de externe opslagplaats voor code in Cloud Manager.
