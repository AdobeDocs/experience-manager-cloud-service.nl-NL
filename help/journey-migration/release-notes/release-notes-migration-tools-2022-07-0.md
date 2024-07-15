---
title: Opmerkingen bij de release AEM as a Cloud Service 2022.7.0 voor migratiehulpprogramma's
description: Opmerkingen bij de release AEM as a Cloud Service 2022.7.0 voor migratiehulpprogramma's
feature: Release Information
exl-id: bc8f1a80-867e-423a-9c03-4a53b1ebc57c
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---

# Opmerkingen bij de release AEM as a Cloud Service 2022.7.0 voor migratiehulpprogramma&#39;s {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.7.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.30 is 27 juli 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* BPA kan nu de totale migreerbare grootte van de Index van Lucene ontdekken en rapporteren die Totale Lucene Index exclusief `/oak:index/lucene` en `/oak:index/damAssetLucene` is.
* Nieuw patroon toegevoegd in BPA om het gebruik van een aangepast i18n-woordenboek te detecteren en er een melding van te maken. Translator.html is niet beschikbaar in AEM as a Cloud Service en het aangepaste i18n-woordenboek moet worden geïmplementeerd vanuit Git via de Cloud Manager CI/CD-pijplijn.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA rapporteerde over ontbrekende originele uitvoeringen voor inhoudsfragmenten. Omdat inhoudsfragmenten geen uitvoeringen hebben, wordt deze controle nu overgeslagen voor inhoudsfragmenten.
* De optie om ACS-gemeenschappelijke bevindingen te filtreren ontbrak in BPA UI. Dit is opgelost.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v2.0.12 is 19 juli 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Gebruikers die zijn aangemeld via LDAP, kunnen nu functies voor grootte controleren en gebruikerstoewijzing in CTT uitvoeren.
* Gebruikers kunnen SSL-logboekregistratie nu inschakelen om problemen met SSL/TLS-verbindingen tijdens extracties te verhelpen.
* Om te helpen bronconnectiviteitskwesties zuiveren, worden de subdomeinnamen nu gedrukt in logboeken wanneer de verbinding aan Azure ontbreekt.
* Om problemen met foutopsporing tijdens de precopy te helpen oplossen, worden AzCopy-logboeken nu toegevoegd aan de extractielogboeken wanneer de precopy mislukt.
* Als u wilt voorkomen dat de resultaten van de groottecontrole worden weergegeven, kunnen gebruikers de optie Grootte controleren pas opnieuw uitvoeren nadat de vorige grootte van de controle is voltooid.

### Opgeloste problemen {#bug-fixes-ctt}

* Eerdere extractielogboeken werden weergegeven nadat een migratieset was verwijderd en opnieuw werd gemaakt. Dit is opgelost.
* De knop Voortgang weergeven was niet beschikbaar voor migratiesets met de status STOPPED. Dit is opgelost.
* De knop Handeling verwijderen was niet beschikbaar voor migratiesets met een verlopen extractietoets. Dit is opgelost.
* Meerdere UI-bugs gecorrigeerd.

## Cloud Acceleration Manager {#cam-release}

### Releasedatum {#release-date-cam}

De Releasedatum voor Cloud Acceleration Manager is 15 juli 2022.

### Wat is er nieuw? {#what-is-new-cam}

* Cloud Acceleration Manager biedt gebruikers nu de mogelijkheid om het migratietoken handmatig op te halen om een opname te kunnen starten wanneer het automatisch ophalen mislukt. De automatische herwinning kan ontbreken als de klanten opstelling IP allow-list hebben die CAM blokkeert of als een niet-admin gebruiker probeert om een opname te beginnen. Zie [ het Oplossen van problemen ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) voor meer informatie.
* Lange tabellen op de pagina Complexiteit migratie kunnen nu worden samengevouwen, zodat u ze eenvoudig kunt gebruiken.
