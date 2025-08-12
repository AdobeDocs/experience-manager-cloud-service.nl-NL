---
title: Elementen voorvertonen voordat ze op AEM Sites-pagina's worden gebruikt
description: Met Dynamic Media met OpenAPI-mogelijkheden kunt u elementen voorvertonen op voorvertoningspagina's van Adobe Experience Manager (AEM)-sites. Met deze voorvertoning van elementen kunnen u en uw belanghebbenden de updates van uw elementen controleren en valideren voordat u de auteurspagina's (met bijgewerkte elementen) voor openbaar gebruik publiceert.
role: Admin, User
exl-id: 6f071ca9-0f84-45fc-a6b3-047cca9d5e65
source-git-commit: 3f3e091d09b94418fc2cda0bd3b3ce950555b7a9
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---


# Elementen voorvertonen voordat ze op AEM Sites-pagina&#39;s worden gebruikt {#asset-preview-using-Dynamic-Media-with-OpenAPI-capabilities}

Met [!DNL Dynamic Media with OpenAPI capabilities] kunt u een voorvertoning weergeven van elementen die beschikbaar zijn op de [!DNL Adobe Experience Manager (AEM) Sites] -auteurspagina&#39;s voordat u deze openbaar maakt. De voorvertoning van het element is beschikbaar op de auteur en de voorvertoningslaag van uw site.

Aan [ voorproefactiva op de voorproefpagina&#39;s van AEM Sites ](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities), werk de auteurspagina&#39;s van uw plaats bij door of de activa toe te voegen u voorproef of bestaande beschikbare degenen in uw levende plaatspagina wilt vervangen. Publiceer de bijgewerkte auteurspagina&#39;s aan de voorproefrij om een voorproef URL te produceren.

Deel de voorvertoningspagina met de belanghebbenden om feedback te verzamelen over de visuele kwaliteit en contextafhankelijke uitlijning van de bijgewerkte elementen. Verfijn de elementen op basis van feedback. Meerdere versies van het element maken en beheren tijdens de revisiecyclus.

Nadat u de elementen hebt voltooid voor openbaar gebruik, werkt u ze op de pagina&#39;s van uw auteur bij en publiceert u de pagina&#39;s naar de publicatielijst voor openbare toegang.

## Voordat u begint{#prerequisites-for-previewing-assets-using-Dynamic-Media-with-OpenAPI-capabilities}

Zorg ervoor dat u:

* Toegang tot [!DNL AEM Assets as a Cloud Service] .
* Machtiging om de eigenschap Status van elementen te bewerken.
* [ toegevoegde [!UICONTROL Preview] waarde aan het [!UICONTROL &#x200B; Status] meta-gegevensbezit beschikbaar in [!UICONTROL Basic] lusje ](/help/assets/metadata-assets-view.md#edit-metadata-forms) van de meta-gegevensvorm die op de omslag wordt toegepast die de activa bevat aan voorproef.
  ![ voeg de optie van de Voorproef ](/help/assets/assets/metedata-form-preview.png) toe
* De sleutel om het voorproefteken te produceren. [ de steun van Adobe van het Contact ](https://helpx.adobe.com/in/contact.html) en wint een verzoek voor de sleutel op.

## Elementen voorvertonen op de voorvertoningspagina van uw sites {#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities}

U kunt een voorvertoning weergeven van nieuwe elementen of elementen die al zijn goedgekeurd. Goedgekeurde elementen worden alleen op uw live sitepagina&#39;s weergegeven.

Voer de volgende stappen uit om de elementstatus in te stellen op voorvertoning in [!DNL Assets View] en publiceer vervolgens de sitepagina naar de voorvertoningslaag om een voorbeeld-URL van de pagina te genereren:

1. Stel de elementstatus in op **[!UICONTROL Preview]** door de volgende stappen uit te voeren:

   1. Selecteer [!DNL Assets View] in **[!UICONTROL Assets]** en navigeer naar de map.
   1. Selecteer het element waarvan u een voorvertoning wilt weergeven.
   1. Klik op **[!UICONTROL Details]**.
   1. Stel in de [!UICONTROL Information Panel] de waarde **[!UICONTROL Status]** in op **[!UICONTROL Preview]** en klik op **[!UICONTROL Save]** .
      ![ Voorproef ](/help/assets/assets/preview-boat-at-bay.png)

1. Navigeer naar de ontwerppagina voor sites. Voer de stappen in [ de verre activa van de Toegang in de sectie van de Redacteur van de Pagina van AEM uit ](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) om het paneel van de Selecteur van Activa te gebruiken voor het selecteren van de activa u onlangs aan Voorproef (status) plaatste.

   >[!NOTE]
   >
   > Elementen worden weergegeven met de meest recente statusupdate ingesteld op Goedgekeurd of Voorvertoning.

1. Publiceer de pagina naar de voorvertoningslaag met de optie **[!UICONTROL Manage Publication]** . Voer de stappen in de [ het Publiceren Inhoud aan de sectie van de Voorproef ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/previewing-content) uit om uw pagina aan de voorproefrij te publiceren. Na publicatie een voorbeeld-URL van uw pagina genereren. Op de pagina Voorbeeld worden de elementen (met de meest recente statusupdates) weergegeven op de pagina Sites.

Deel deze voorproef URL met de belanghebbenden voor overzicht en terugkoppelen. Zorg ervoor dat uw belanghebbenden toegang hebben tot de voorvertoningspagina. Zie [ toegang tot de voorproefdienst ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments#access-preview-service) voor informatie bij het verlenen van toegang tot de voorproefpagina&#39;s.

>[!NOTE]
>
>De [ de kerncomponent van het Beeld V3 ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/wcm-components/image#version-and-compatibility) steunt voorproefversie van activa door gebrek. Wanneer u een voorproefversie van activa (activa met voorproefstatus) gebruikend het [ paneel van de Selecteur van Activa ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/asset-selector-upload) selecteert, geeft de component van het Beeld V3 het automatisch in de rij van de Voorproef (een voorproefversie op uw de auteurspagina van Plaatsen) terug.

Na het voltooien van de activaversie, [ publiceer uw pagina&#39;s aan publiceer rij ](#publish-your-pages-to-publish-tier) voor openbare consumptie.

## Pagina&#39;s met goedgekeurde middelen publiceren voor openbaar gebruik{#publish-your-pages-to-publish-tier}

Nadat u de elementversie voor openbaar gebruik hebt voltooid, stelt u de elementstatus in op **[!UICONTROL Approved]** . Publiceer uw pagina&#39;s vervolgens naar de publicatielijst. Voer de volgende stappen uit om uw pagina&#39;s te publiceren:

1. Volg stap 1 in [ activa van de Voorproef in uw pagina van de de voorproef van plaatsen ](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities) sectie hierboven om activastatus in **[!UICONTROL Approved]** te veranderen.
1. Navigeer naar de auteurspagina van uw Sites en publiceer deze naar [!DNL Publish tier]. Publiceer de pagina&#39;s door de stappen in [ het Publiceren van de sectie van de Redacteur van de Pagina uit te voeren ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/sites/authoring/page-editor/publishing#publishing-from-the-page-editor).
Alternatief, volg de stappen in [ het Publiceren Pagina&#39;s van de sectie van de Console van Plaatsen ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/publishing-pages#publishing-from-the-sites-console) om uw pagina van de console van uw plaats te publiceren.

   >[!NOTE]
   >
   > Alleen goedgekeurde elementen kunnen worden geleverd op de publicatielijst. Goedkeuren van de elementen voordat u uw pagina publiceert naar de publicatielijst voor openbaar gebruik.

   ![ de pagina is gepubliceerd ](/help/assets/assets/the-page-has-been-publushed.png)
Er wordt een bevestigingsbericht **[!UICONTROL The page has been published]** weergegeven na het publiceren. Navigeer op de publicatielijst naar de gepubliceerde pagina om te bevestigen dat de updates actief zijn en dat de inhoud naar behoren wordt weergegeven.
