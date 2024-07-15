---
title: Hoe te om uit de montages van het Bureau in AEM Forms te vormen?
description: Taken delegeren tijdens of buiten het kantoor voor een naadloze workflowuitvoering.
exl-id: c7e436f1-8e1c-4334-b3dc-ab9800695301
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# Vorm uit Bureau het plaatsen {#configure-out-of-office-settings}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/configure-out-of-office-settings.html) |
| AEM as a Cloud Service | Dit artikel |

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.

U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als de instellingen buiten het kantoor van toepassing zijn. Als u in een verschillende tijdzone van de server wordt gevestigd, is de gebruikte tijdzone die van de cliënt.

U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. U kunt ook uitzonderingen opgeven voor items van specifieke processen die naar een andere gebruiker moeten worden verzonden of die in uw Postvak IN moeten blijven totdat u terugkeert. Als de aangewezen persoon ook uit het bureau is, gaat het punt naar de gebruiker die zij hebben aangewezen. Als het punt niet aan een gebruiker kan worden toegewezen die niet uit het bureau is, blijft het punt in uw Inbox.

U kunt item-delegatie scheiden op basis van de workflowmodellen. Bijvoorbeeld, kunt u een punt met betrekking tot Werkschema A aan gebruiker A toewijzen en een punt met betrekking tot Werkschema B toewijzen wordt toegewezen aan gebruiker B.


>[!NOTE]
>
>* Wanneer u uit Bureau het plaatsen toelaat, blijven alle punten beschikbaar in uw Inbox, alvorens het plaatsen in uw inbox toe te laten. Alleen items die worden ontvangen nadat de instelling is ingeschakeld, worden gedelegeerd.
>* Wanneer u uit het Bureau het plaatsen van de draaien weg, worden de gedelegeerde punten niet automatisch toegewezen terug aan u. U kunt de claimfunctionaliteit gebruiken om items aan u toe te wijzen.
>* Wanneer Gebruiker A punten aan Gebruiker B en Gebruiker B afgevaardigden verder aan Gebruiker C delegeert, dan worden de punten toegewezen slechts aan Gebruiker C en niet Gebruiker B.
>* Wanneer er een lus in taak is, blijven de taken bij de originele gebruiker. Bijvoorbeeld, wanneer Gebruiker A punten aan Gebruiker B van de Gebruiker B afgevaardigden aan Gebruiker C delegeert, delegeert de Gebruiker C aan Gebruiker D, en de afgevaardigden van Gebruiker D aan Gebruiker B, een lijn in gecreeerd. In een dergelijke situatie, blijft het punt met de originele Gebruiker. Gebruiker A is de oorspronkelijke gebruiker in het bovenstaande voorbeeld.

## De instelling Buiten Office voor uw account inschakelen {#enable-out-of-office}

Voer de volgende stappen uit om de instelling Buiten-Office voor uw account in te schakelen en uw Inbox-items te delegeren aan een andere gebruiker:

1. Meld u aan bij uw AEM. Selecteer het ![ Inbox ](assets/bell.svg) pictogram en selecteer **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer het ![ pictogram van de Selecteur van de Mening ](assets/viewlist.svg) of ![ van de Selecteur van de Mening ](assets/calendar.svg) naast de **[!UICONTROL Create]** knoop en selecteer **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Open het tabblad **[!UICONTROL Out of Office]** in het dialoogvenster met instellingen.
1. Selecteer de knop **[!UICONTROL Enable/Disable]** om de instelling Buiten Office in te schakelen.
1. Geef de **[!UICONTROL Start Time]** en **[!UICONTROL End Time]** voor de instelling op. De items worden alleen gedelegeerd tijdens de opgegeven periode. Laat het veld **[!UICONTROL End Time]** leeg om items voor onbepaalde tijd te delegeren.
1. Schakel het selectievakje **[!UICONTROL Forward my items during this period]** in. Als je deze optie niet selecteert en geen ontvanger opgeeft, worden je objecten niet doorgestuurd naar een gebruiker. Hoewel u weg bent en het plaatsen wordt toegelaten, blijven de punten in uw Inbox.
1. Selecteer **[!UICONTROL Add Assignee]**. Geef een gebruiker op in het veld **[!UICONTROL Assignee]** waarnaar de items moeten worden gedelegeerd. Geef de **[!UICONTROL Workflow Model]** op die u wilt delegeren aan de opgegeven gebruiker. U kunt meerdere workflowmodellen selecteren.

   Als u bovendien alle items, ongeacht het workflowmodel, aan een bepaalde gebruiker wilt toewijzen, selecteert u **[!UICONTROL All Workflows]** in de vervolgkeuzelijst Werkstroommodel. <br>

   Als u items aan een bepaalde gebruiker wilt toewijzen voor alle workflowmodellen, met uitzondering van enkele, selecteert u **[!UICONTROL All Workflows]** in de vervolgkeuzelijst Werkstroommodel, selecteert u **[!UICONTROL + Add Exceptions]** en geeft u de workflowmodellen op die u wilt uitsluiten.
   <br>

   Herhaal de stap om meer toewijzingen toe te voegen. <br>

   >[!NOTE]
   >
   >De volgorde van de toewijzingen is belangrijk. Wanneer een punt aan een gebruiker wordt toegewezen die uit bureau het plaatsen hebben toegelaten, wordt het punt geëvalueerd tegen de gespecificeerde toewijzingslijst in de orde worden de wijzers toegevoegd. Wanneer een item voldoet aan de criteria, wordt het toegewezen aan de ontvanger en wordt de volgende toegewezen persoon niet gecontroleerd.


1. Selecteer **[!UICONTROL Save]**. De instelling wordt van kracht op de opgegeven begindatum en -tijd. Als u zich aanmeldt terwijl u zich buiten het kantoor bevindt, wordt u pas overwogen op het kantoor wanneer u uw instellingen wijzigt.

Nu, worden de punten die aan u tijdens uit de periode van het Bureau worden toegewezen automatisch toegewezen aan de gespecificeerde ontvanger.
![ uit-van-bureau ](assets/out-of-office.png)

>[!NOTE]
>
>(Alleen voor Forms-gecentreerde workflowitems) Schakel de optie **[!UICONTROL Allow assignee to delegate using the 'Out of Office' settings]** van de stap **[!UICONTROL Assign task]** in de workflow in. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden gedelegeerd aan andere gebruikers.
>(Alleen voor Forms-gecentreerde workflowitems) Schakel de optie **[!UICONTROL Allow assignee to delegate using 'Out of Office' settings]** van de stap **[!UICONTROL Assign task]** in de workflow in. Alleen items waarvoor de eerder vermelde optie is ingeschakeld, worden gedelegeerd aan andere gebruikers.

## Beperkingen {#limitations}

* Het toewijzen van items aan een groep wordt niet ondersteund.
* Het toelaten uit Bureau voor projecttaken wordt momenteel niet gesteund.
