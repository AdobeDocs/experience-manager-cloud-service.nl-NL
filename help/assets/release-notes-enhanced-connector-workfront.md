---
title: Opmerkingen bij de release [!DNL Workfront for Experience Manager enhanced connector]
description: Opmerkingen bij de release [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 081f7ed8c39382408285887928163e2569c5cbfe
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Opmerkingen bij de release [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Workfront for Experience Manager enhanced connector].

## Releasedatum {#release-date}

De releasedatum voor de nieuwste versie 1.9.0 van [!DNL Workfront for Experience Manager enhanced connector] is 16 juni 2022.

## Geen hooglichten {#release-highlights}

De meest recente versie van de [!DNL Workfront for Experience Manager enhanced connector] bevat de volgende opgeloste problemen:

* Wanneer u uploadt via een gekoppelde map of de `Send To` Actie beschikbaar in Workfront om elementen te uploaden naar as a Cloud Service Experience Manager. De elementen worden beschadigd en kunnen niet worden geopend in Adobe Photoshop.

>[!IMPORTANT]
>
>Adobe raadt u aan [upgrade naar de nieuwste versie van 1.9.0](../assets/update-workfront-enhanced-connector.md) van de [!DNL Workfront for Experience Manager enhanced connector].

## Bekende problemen {#known-issues}

* Tijdens het vormen van project verbonden omslagen met AEM 6.4, slaat de Experience Manager niet de waarden voor **[!UICONTROL sub-folders]** en **[!UICONTROL Create linked folder in projects with portfolio]** velden. De waarde voor de **[!UICONTROL sub-folders]** veld bijwerken naar **[!UICONTROL undefined]** en de waarde voor de **[!UICONTROL Create linked folder in projects with portfolio]** veld bijwerken naar **[!UICONTROL Default Portfolio]** automatisch na het opslaan van de configuratie.

* Wanneer u de klassieke Workfront-ervaring gebruikt, kunt u de **[!UICONTROL Send to]** beschikbaar in het dialoogvenster **[!UICONTROL More]** in de vervolgkeuzelijst kunt u de doelbestemming in de Experience Manager niet selecteren. De **[!UICONTROL Send to]** Deze optie werkt correct met de **[!UICONTROL Document Actions]** vervolgkeuzelijst. De **[!UICONTROL Send to]** deze optie werkt correct voor **[!UICONTROL More]** en de **[!UICONTROL Document Actions]** keuzelijst beschikbaar in de nieuwe Workfront-ervaring.

## Eerdere versies {#previous-releases}

### Release van maart 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] bevat nu de volgende updates:

* U kunt nu gekoppelde mappen maken tussen Adobe Workfront en AEM Assets as a Cloud Service, zelfs als er meerdere aan een project gekoppelde mapconfiguraties zijn.

* Extra ondersteuning voor paginering van abonnementen voor gebeurtenissen.

* Toegevoegde ondersteuning voor AEM 6.4.x.

* Extra ondersteuning voor proxyomgevingen.

* Verscheidene insectenmoeilijke situaties die op partner en klant worden gebaseerd terugkoppelen.

>[!MORELIKETHIS]
>
>* [Integreren [!DNL Workfront for Experience Manager enhanced connector] met Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
>* [Integreren [!DNL Workfront for Experience Manager enhanced connector] met Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=en)

