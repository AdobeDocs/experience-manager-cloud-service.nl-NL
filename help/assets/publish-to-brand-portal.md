---
title: Middelen, mappen en verzamelingen naar Brand Portal publiceren
seo-title: Middelen, mappen en verzamelingen naar Brand Portal publiceren
description: Leer hoe u elementen, mappen en verzamelingen naar Brand Portal publiceert en de publicatie ervan ongedaan maakt.
seo-description: Leer hoe u elementen, mappen en verzamelingen naar Brand Portal publiceert en de publicatie ervan ongedaan maakt.
uuid: null
contentOwner: Vishabh Gupta
products: SG_EXPERIENCEMANAGER/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: null
translation-type: tm+mt
source-git-commit: 7e0375b6ebdf0959dbe50ad3ae2cd0b77709b4c1

---


# AEM-middelen publiceren naar Brand Portal {#publish-aem-assets-to-brand-portal}

Als beheerder van Adobe Experience Manager (AEM)-middelen kunt u elementen, mappen en verzamelingen publiceren naar de AEM Assets Brand Portal-instantie. Bovendien kunt u de publicatieworkflow van een middel of map plannen op een latere datum of tijd. Zodra gepubliceerd, kunnen de gebruikers van het Portaal van het Merk tot de activa, de omslagen, en de inzamelingen aan andere gebruikers toegang hebben en verder verspreiden.

Nochtans, moet u AEM Middelen met het Portaal van het Merk eerst vormen. Zie AEM-elementen [configureren met Brand Portal](configure-aem-assets-with-brand-portal.md)voor meer informatie.

Als u volgende wijzigingen aanbrengt in het oorspronkelijke element, de oorspronkelijke map of de oorspronkelijke verzameling in AEM Assets, worden de wijzigingen pas doorgevoerd in Brand Portal als u het bestand opnieuw publiceert vanaf AEM Assets. Met deze functie zorgt u ervoor dat wijzigingen die momenteel worden uitgevoerd, niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

* [Middelen publiceren naar Brand Portal](#publish-assets-to-bp)
* [Mappen publiceren naar Brand Portal](#publish-folders-to-brand-portal)
* [Verzamelingen publiceren naar Brand Portal](#publish-collections-to-brand-portal)

>[!NOTE]
>
>Adobe raadt gefaseerde publicatie aan, bij voorkeur tijdens niet-piekuren, zodat de AEM-auteur niet te veel bronnen in beslag neemt.


## Middelen publiceren naar Brand Portal {#publish-assets-to-bp}

Hier volgen de stappen voor het publiceren van elementen van AEM Assets naar Brand Portal:

1. Open vanuit de middelenconsole de bovenliggende map en selecteer alle elementen die u wilt publiceren, en klik op de werkbalk op de optie **[!UICONTROL Snel publiceren]** .


   ![publish2bp-2](assets/publish2bp.png)

1. Hieronder vindt u een overzicht van de twee manieren waarop u elementen kunt publiceren:
   * [Nu](#publish-to-bp-now) publiceren (elementen direct publiceren)
   * [Later](#publish-to-bp-now) publiceren (publicatiemiddelen plannen)

### Elementen nu publiceren {#publish-to-bp-now}

Voer een van de volgende twee handelingen uit om de geselecteerde elementen te publiceren naar Brand Portal:

* Selecteer **[!UICONTROL Snel publiceren]** op de werkbalk. Klik in het menu op **[!UICONTROL Publiceren naar Brand Portal]**.

* Selecteer Publicatie **[!UICONTROL beheren in de werkbalk]**.

   1. Van **[!UICONTROL Actie]**, uitgezocht **[!UICONTROL Publiceren aan het Portaal]** van de Merk, en van **[!UICONTROL Planning]**, uitgezocht **[!UICONTROL nu]**. Click **[!UICONTROL Next]**.

   2. Bevestig uw selectie in **[!UICONTROL Toepassingsgebied]** en klik op **[!UICONTROL Publiceren naar Brand Portal]**.

Er verschijnt een bericht waarin wordt aangegeven dat de elementen in de wachtrij zijn geplaatst voor publicatie naar Brand Portal. Meld u aan bij de interface Brand Portal om de gepubliceerde elementen te bekijken.

### Elementen later publiceren {#publish-to-bp-later}

Publiceren van de elementen naar Brand Portal naar een latere datum of tijd plannen:

1. Selecteer de elementen die u wilt plannen voor publiceren, en selecteer Publicatie **** beheren in de werkbalk bovenaan.

1. Selecteer op de pagina Publicatie **** beheren de optie **[!UICONTROL Publiceren naar Brand Portal]** in **[!UICONTROL Actie]** en selecteer **[!UICONTROL Later]** in **[!UICONTROL Planning]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

1. Selecteer een **activeringsdatum** en geef de tijd op. Click **Next**.

1. Geef een **[!UICONTROL workflowtitel]** op in **[!UICONTROL Workflows]**. Klik op Later **** publiceren.

   ![publicatieworkflow](assets/publishworkflow.png)

Meld u aan bij de interface Brand Portal om te zien hoe de gepubliceerde middelen beschikbaar zijn.

![bp_landing_page](assets/bp_landing_page.png)

<!--

End - Publish assets to Brand Portal
Start- Publish folders to Brand Portal
-->


## Mappen publiceren naar Brand Portal{#publish-folders-to-brand-portal}

U kunt de mappen met elementen direct publiceren of verwijderen of op een latere datum of tijd plannen.

### Mappen publiceren naar Brand Portal {#publish-folders-to-brand-portal-1}

1. Selecteer in de middelenconsole de mappen die u wilt publiceren en klik op de werkbalk op de optie **[!UICONTROL Snel publiceren]** .

   ![publish2bp](assets/publish2bp.png)

1. **Mappen nu publiceren**

   Voer een van de volgende twee handelingen uit om de geselecteerde mappen naar Brand Portal te publiceren:

   * Selecteer **[!UICONTROL Snel publiceren]** op de werkbalk. Selecteer in het menu de optie **[!UICONTROL Publiceren naar Brand Portal]**.

   * Selecteer Publicatie **[!UICONTROL beheren in de werkbalk]**.

      1. Kies in **[!UICONTROL Actie]** de optie **[!UICONTROL Publiceren naar Brand Portal]**. Selecteer **[!UICONTROL Nu]** bij **[!UICONTROL planning]**. Click **[!UICONTROL Next]**.
      1. Bevestig uw selectie in **[!UICONTROL Toepassingsgebied]** en klik op **[!UICONTROL Publiceren naar Brand Portal]**.
   Er wordt een bericht weergegeven met de mededeling dat de map in de wachtrij is geplaatst voor publicatie naar Brand Portal. Meld u aan bij de interface van uw Brand Portal om de gepubliceerde map weer te geven.

1. **Mappen later publiceren**

   Publiceren van de mappen met elementen naar een latere datum of tijd plannen.

   1. Selecteer de mappen die u voor publicatie wilt plannen, selecteer Publicatie **** beheren in de werkbalk boven in het scherm.
   1. Van **[!UICONTROL Actie]**, uitgezocht **[!UICONTROL Publiceren aan het Portaal]** van de Merk, en van het **[!UICONTROL Plannen]** uitgezocht **[!UICONTROL Later]**.

      ![uitgeverij](assets/publishlaterbp.png)

   1. Selecteer een **[!UICONTROL activeringsdatum]** en geef de tijd op. Click **[!UICONTROL Next]**.
   1. Bevestig uw selectie in **[!UICONTROL Bereik]**. Click **[!UICONTROL Next]**.
   1. Geef een workflowtitel op onder **[!UICONTROL Workflows]**. Klik op Later **** publiceren.

      ![manageplannulepub](assets/manageschedulepub.png)

### Mappen van Brand Portal verwijderen {#unpublish-folders-from-brand-portal}

U kunt elke elementmap die naar Brand Portal is gepubliceerd, verwijderen door de publicatie ongedaan te maken van de AEM Assets-instantie. Nadat u de publicatie van de oorspronkelijke map ongedaan hebt gemaakt, is de kopie ervan niet meer beschikbaar voor de gebruikers van de Brand Portal.

U kunt de publicatie van middelenmappen onmiddellijk ongedaan maken vanaf Brand Portal of deze later plannen.

De publicatie van middelenmappen op Brand Portal ongedaan maken:

1. Selecteer in de AEM Assets-console de map waarvan u de publicatie wilt ongedaan maken.

   ![publish2bp-1](assets/publish2bp.png)

1. Klik op Publicatie **[!UICONTROL beheren op de werkbalk]**.

1. **Publiceren via Brand Portal nu ongedaan maken**

   U kunt als volgt de publicatie van de geselecteerde map onmiddellijk ongedaan maken via Brand Portal:

   1. Selecteer Publicatie **beheren in de werkbalk**.
   1. Kies in **Handeling** de optie **Publiceren ongedaan maken in Brand Portal** en in **Planning** de optie **Nu**. Click **Next.**
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Publiceren ongedaan maken via Brand Portal**.
   ![bevestigen-ongedaan maken](assets/confirm-unpublish.png)

1. **Publiceren via Brand Portal later ongedaan maken**

   U kunt als volgt de publicatie van een map van Brand Portal naar een latere datum en tijd plannen:

   1. Selecteer Publicatie **beheren in de werkbalk**.
   1. Kies in **Actie** de optie **Publiceren ongedaan maken in Brand Portal** en **Planning** de optie **Later**.
   1. Selecteer een **activeringsdatum** en geef de tijd op. Click **Next**.
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Volgende**.
   1. Geef een **workflowtitel** op in **Workflows**. Klik op Later **publiceren ongedaan maken.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


<!--
End - Publish folders to Brand Portal
Start- Publish Collections to Brand Portal

-->

## Verzamelingen publiceren naar Brand Portal {#publish-collections-to-brand-portal}

U kunt verzamelingen publiceren of de publicatie ervan ongedaan maken vanuit uw AEM Assets-instantie.

>[!NOTE]
>
>Inhoudsfragmenten kunnen niet worden gepubliceerd naar de Brand Portal. Daarom is de actie **[!UICONTROL Publiceren naar Brand Portal]** niet beschikbaar als u inhoudfragment(en) selecteert in AEM Asset.
>
>Als verzamelingen met inhoudsfragmenten van AEM Assets naar Brand Portal worden gepubliceerd, wordt alle inhoud van de map behalve inhoudsfragmenten gerepliceerd naar de interface Brand Portal.

### Verzamelingen publiceren {#publish-a-collection-to-brand-portal}

Hier volgen de stappen voor het publiceren van verzamelingen van AEM Assets naar Brand Portal:

1. Klik in de UI voor AEM-middelen op AEM-logo.
1. Ga vanuit de **navigatiepagina** naar **[!UICONTROL Middelen]** > **[!UICONTROL Verzamelingen]**.
1. Van de console van **Inzamelingen** , selecteer de inzamelingen die u aan het Portaal van het Merk wilt publiceren.

   ![select_collection](assets/select_collection.png)

1. Klik op de werkbalk op **[!UICONTROL Publiceren naar Brand Portal]**.
1. Klik in het bevestigingsvenster op **[!UICONTROL Publiceren]**.
1. Sluit het bevestigingsbericht.

   Meld u aan bij Brand Portal als beheerder. De gepubliceerde inzameling is beschikbaar in de console van **[!UICONTROL Inzamelingen]** .

   ![gepubliceerde verzameling](assets/published_collection.png)

## Publicatie van verzamelingen ongedaan maken {#unpublish-collections}

U kunt elke verzameling die naar Brand Portal is gepubliceerd, verwijderen door de publicatie ervan uit uw AEM Assets-instantie ongedaan te maken. Nadat u de publicatie van de oorspronkelijke verzameling ongedaan hebt gemaakt, is de kopie ervan niet meer beschikbaar voor de gebruikers van het Brand Portal.

Hier volgen de stappen voor het ongedaan maken van de publicatie van verzamelingen:

1. Selecteer in de Collections console of your AEM Assets instance de verzameling die u wilt verwijderen.

   ![select_collection-1](assets/select_collection-1.png)

1. Klik op het pictogram **[!UICONTROL Verwijderen uit Brand Portal]** op de werkbalk.
1. Klik in het dialoogvenster op **[!UICONTROL Publiceren]** ongedaan maken.
1. Sluit het bevestigingsbericht. De verzameling wordt verwijderd uit de interface Brand Portal.

Zie de documentatie [van het Portaal van de](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) Merk voor meer informatie over distributie van activa, omslagen, en inzamelingen aan het eind - gebruikers.

<!--

End - Publish Collections to Brand Portal

-->

