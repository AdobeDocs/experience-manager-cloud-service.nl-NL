---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.7.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.7.0
feature: Release Information
source-git-commit: f84327096951772e1bed8656334841e1292d6bcf
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 2%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.7.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.7.0.

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v2.0.12 is 19 juli 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Gebruikers die zijn aangemeld via LDAP, kunnen nu functies voor grootte controleren en gebruikerstoewijzing in CTT uitvoeren.
* Gebruikers kunnen SSL-logboekregistratie nu inschakelen om problemen met SSL/TLS-verbindingen tijdens extracties te verhelpen.
* Om te helpen bronconnectiviteitskwesties zuiveren, worden de subdomeinnamen nu gedrukt in logboeken wanneer de verbinding aan Azure ontbreekt.
* Om problemen met foutopsporing tijdens de precopy te helpen oplossen, worden AzCopy-logboeken nu toegevoegd aan de extractielogboeken wanneer de precopy mislukt.
* Als u wilt voorkomen dat de resultaten van Grootte van de schaalcontrole worden weergegeven, kunnen gebruikers de optie Grootte controleren pas opnieuw uitvoeren nadat de vorige grootte van de controle is voltooid.

### Opgeloste problemen {#bug-fixes-ctt}

* Eerdere extractielogboeken werden weergegeven nadat een migratieset was verwijderd en opnieuw werd gemaakt. Dit is opgelost.
* De knop Voortgang weergeven was niet beschikbaar voor migratiesets met de status STOPPED. Dit is opgelost.
* De knop Handeling verwijderen was niet beschikbaar voor migratiesets met een verlopen extractietoets. Dit is opgelost.
* Meerdere UI-bugs gecorrigeerd.

## Cloud Acceleration Manager {#cam-release}

### Releasedatum {#release-date-cam}

De releasedatum voor Cloud Acceleration Manager is 15 juli 2022.

### Wat is er nieuw? {#what-is-new-cam}

* Cloud Acceleration Manager biedt gebruikers nu de mogelijkheid om het migratietoken handmatig op te halen om een opname te kunnen starten wanneer automatisch ophalen mislukt. De automatische herwinning kan ontbreken als de klanten opstelling IP allow-list hebben die CAM blokkeert of als een niet-admin gebruiker probeert om een opname te beginnen. Zie [Problemen oplossen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) voor meer informatie .
* Lange tabellen op de pagina Complexiteit migratie kunnen nu worden samengevouwen, zodat u ze eenvoudig kunt gebruiken.

