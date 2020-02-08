---
title: Activiteitsstroom in tijdlijn
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Logbestanden van elementbewerking weergeven in activiteitsstroom {#activity-stream-in-timeline}

Deze functie geeft activiteitenlogboeken voor elementen op de tijdlijn weer. Als u een van de volgende elementgerelateerde bewerkingen uitvoert in Adobe Experience Manager (AEM) Assets, werkt de functie Activiteitsstroom de tijdlijn bij om de activiteit weer te geven.

De volgende bewerkingen worden in de activiteitsstroom aangemeld:

* Maken
* Verwijderen
* Downloaden (inclusief uitvoeringen)
* Publiceren
* Publiceren ongedaan maken
* Goedkeuren
* Afwijzen
* Verplaatsen

De activiteitenlogboeken die in de chronologie moeten worden getoond worden opgehaald van de plaats `/var/audit/com.day.cq.dam/content/dam` in CRX, waar de logboekdossiers worden opgeslagen.  Bovendien wordt de tijdlijnactiviteit vastgelegd wanneer nieuwe elementen worden geüpload of bestaande elementen worden gewijzigd en gecontroleerd in AEM via de [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) of de AEM-bureaubladtoepassing [](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html).

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u vervolgens **[!UICONTROL Tijdlijn]** in de lijst GlobalNav.

<!-- ![timeline-2](assets/timeline-2.png) -->

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

<!-- ![activity_stream](assets/activity_stream.png) -->

>[!NOTE]
>
>De standaardopslaglocatie voor logbestanden voor **[!UICONTROL publicatie]** - en **[!UICONTROL Unpublish]** -taken is `/var/audit/com.day.cq.replication/content`. Voor **[!UICONTROL Verplaatsen]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
