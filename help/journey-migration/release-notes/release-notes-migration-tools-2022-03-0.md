---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.3.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.3.0
feature: Release Information
exl-id: ab43605d-d46e-43de-b71f-fab610609550
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.3.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.3.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.26 is 16 maart 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om niet-verwerkte activa te detecteren. Als niet-verwerkte elementen worden gedetecteerd, moeten deze elementen zijn ingesteld op verwerkt of worden verwijderd uit de migratieset tijdens de overdracht van inhoud om te voorkomen dat problemen optreden tijdens het opnemen van inhoud.
* Mogelijkheid om te detecteren of inhoud meer dan 1000 vanity-URL&#39;s heeft. Het gebruik van een hoog aantal vanity-URL&#39;s is niet de beste manier, omdat hiermee een laadbewerking wordt uitgevoerd op de servers Dispatcher en Publish.
* Mogelijkheid om problemen met betrekking tot de definities van de eikenindex te identificeren en incompatibiliteiten met AEM as a Cloud Service vast te stellen.
* Mogelijkheid om het gebruik van Externalzer-configuraties te detecteren en hierover verslag uit te brengen. In AEM as a Cloud Service externalizer worden configuraties ingesteld door Cloud Manager. Daarom moeten de bestaande configuraties ExternalAlizer worden gerefactored om verenigbaarheid te handhaven.

### Opgeloste problemen {#bug-fixes-bpa}

* In sommige gevallen kon BPA niet worden uitgevoerd omdat FormsSelectiveFeaturesAnalysis een assertiefout genereerde.
* BPA rapporteerde bevindingen met betrekking tot het WRK-patroon als MAJOR in plaats van als KRITIEK.
* BPA rapporteerde onjuist bevindingen met betrekking tot de definities van de eikenindex in ui.apps als CRITICAL.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.9.0 is 28 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Hulplijnen voor grootte controleren - Met de functie voor het controleren van de grootte van het gereedschap Inhoud overbrengen kunt u mislukte overdrachten van inhoud reduceren. Met de functie Grootte controleren kunnen gebruikers bepalen of ze voldoende schijfruimte hebben in het dialoogvenster `crx-quickstart` submap voor extractie. En, kunnen zij de migratie schatten vastgestelde grootte en verifiëren of het wordt gesteund. Als één of beide controles worden overtreden, zien de gebruikers waarschuwingen in het CTT gebruikersinterface. Met deze garantie kunt u mislukte inhoudsoverdrachten voorkomen en de migratieopties proactief bespreken met de klantenservice van de Adobe. Zie [Grootte en schijfruimte van migratieset bepalen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#migration-set-size) voor meer informatie .
