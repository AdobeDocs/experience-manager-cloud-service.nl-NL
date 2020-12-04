---
title: Activiteitsstroom in tijdlijn
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3207151a76c51637551907d15a34f1a6b7450d02
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 21%

---


# Elementbewerking weergeven in activiteitenstroom {#activity-stream-in-timeline}

Deze functie geeft activiteitenlogboeken voor elementen op de tijdlijn weer. Als u een van de volgende bewerkingen met betrekking tot elementen uitvoert in [!DNL Experience Manager Assets], werkt de functie Activiteitenstroom de tijdlijn bij om de activiteit weer te geven.

De volgende bewerkingen worden in de activiteitsstroom aangemeld:

* Maken
* Verwijderen
* Downloaden (inclusief uitvoeringen)
* Publicatie
* Publiceren ongedaan maken
* Goedkeuren
* Afwijzen
* Verplaatsen

De activiteitenlogboeken die in de tijdlijn moeten worden weergegeven, worden opgehaald vanaf de locatie `/var/audit/com.day.cq.dam/content/dam` in CRX, waar logboekbestanden worden opgeslagen. Bovendien wordt de tijdlijnactiviteit geregistreerd wanneer nieuwe activa worden geupload of bestaande activa worden gewijzigd en in [!DNL Experience Manager] via [Adobe Activa Link](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) of [[!DNL Experience Manager] Desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=en) worden gecontroleerd.

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u **[!UICONTROL Timeline]** in de lijst GlobalNav.

<!-- ![timeline-2](assets/timeline-2.png) -->

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

<!-- ![activity_stream](assets/activity_stream.png) -->

>[!NOTE]
>
>De standaardopslaglocatie voor logboekbestanden voor de taken **[!UICONTROL Publish]** en **[!UICONTROL Unpublish]** is `/var/audit/com.day.cq.replication/content`. Voor de taken **[!UICONTROL Move]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
