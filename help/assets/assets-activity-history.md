---
title: Activiteitsstroom in tijdlijn
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 37%

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

De activiteitenlogboeken die in de tijdlijn moeten worden weergegeven, worden opgehaald vanaf de locatie `/var/audit/com.day.cq.dam/content/dam` in CRX, waar logboekbestanden worden opgeslagen. Bovendien wordt de tijdlijnactiviteit vastgelegd wanneer nieuwe assets worden geüpload of wanneer bestaande assets worden gewijzigd en gecontroleerd in AEM via de [Adobe Asset Link](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) of de [AEM-desktopapp](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html).

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u een optie in de lijst GlobalNav. **[!UICONTROL Timeline]**

<!-- ![timeline-2](assets/timeline-2.png) -->

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

<!-- ![activity_stream](assets/activity_stream.png) -->

>[!NOTE]
>
>De standaardopslaglocatie voor logboekbestanden voor de taken **[!UICONTROL Publish]** en **[!UICONTROL Unpublish]** is `/var/audit/com.day.cq.replication/content`. Voor de taken **[!UICONTROL Move]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
