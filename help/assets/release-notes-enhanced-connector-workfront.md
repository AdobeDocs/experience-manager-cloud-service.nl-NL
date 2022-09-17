---
title: Opmerkingen bij de release [!DNL Workfront for Experience Manager enhanced connector]
description: Opmerkingen bij de release [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 14b779c476b88ff1ee9d2798296add14f337dbfa
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Opmerkingen bij de release [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Workfront for Experience Manager enhanced connector].

## Releasedatum {#release-date}

De releasedatum voor de laatste versie 1.9.3 van [!DNL Workfront for Experience Manager enhanced connector] is 16 september 2022.

## Geen hooglichten {#release-highlights}

De meest recente versie van de [!DNL Workfront for Experience Manager enhanced connector] bevat de volgende verbeteringen en foutoplossingen:

* Kan geen bestand uploaden dat groter is dan 8 GB.
* Problemen bij het automatisch publiceren van middelen die van Workfront naar AEM worden verzonden.
* Het veld Basispad is niet beschikbaar voor het veld Codes tijdens het bewerken van een standaardformulier voor een metagegevensschema.
* Problemen tijdens het toevoegen van nieuwe versies in Workfront via AEM workflows.
* Wanneer u een AEM zoekopdracht uitvoert naar middelen die beschikbaar zijn in Workfront, AEM een foutbericht wordt weergegeven.
* Wanneer u een AEM werkstroom maakt voor het maken van taken op basis van een element en geen bovenliggende taaknaam definieert, wordt de taak niet in Workfront gemaakt.



>[!IMPORTANT]
>
>Adobe raadt u aan [upgrade naar de nieuwste versie 1.9.3](../assets/update-workfront-enhanced-connector.md) van de [!DNL Workfront for Experience Manager enhanced connector].

## Bekende problemen {#known-issues}

* Tijdens het vormen van project verbonden omslagen met AEM 6.4, slaat de Experience Manager niet de waarden voor **[!UICONTROL sub-folders]** en **[!UICONTROL Create linked folder in projects with portfolio]** velden. De waarde voor de **[!UICONTROL sub-folders]** veld bijwerken naar **[!UICONTROL undefined]** en de waarde voor de **[!UICONTROL Create linked folder in projects with portfolio]** veld bijwerken naar **[!UICONTROL Default Portfolio]** automatisch na het opslaan van de configuratie.

* Wanneer u de klassieke Workfront-ervaring gebruikt, kunt u de **[!UICONTROL Send to]** beschikbaar in het dialoogvenster **[!UICONTROL More]** in de vervolgkeuzelijst kunt u de doelbestemming in de Experience Manager niet selecteren. De **[!UICONTROL Send to]** Deze optie werkt correct met de **[!UICONTROL Document Actions]** vervolgkeuzelijst. De **[!UICONTROL Send to]** deze optie werkt correct voor **[!UICONTROL More]** en de **[!UICONTROL Document Actions]** keuzelijst beschikbaar in de nieuwe Workfront-ervaring.

* Workfront geeft een `SERVER_ERROR` bericht tijdens het koppelen van documenten aan AEM na de upgrade naar versie 8316. Als u het probleem wilt oplossen, wijst u `rep:readProperties` tot `content/dam/collections` for `wf-workfront-user` AEM Gebruikersgroep.

## Eerdere versies {#previous-releases}

### Release van augustus 2022 {#august-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.2, die in augustus 2003 is uitgebracht, bevat de volgende updates:

* De **[!UICONTROL Upload Document]** werkstroomstap kan geen document aan Workfront koppelen.

* De **[!UICONTROL Upload Document]** kan geen document aan Taken en problemen in Workfront koppelen. De werkstroomstap koppelt een document aan Projecten met succes.

### Release juli 2022 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.1 bevat de volgende updates:

* Toegevoegde ondersteuning voor verificatie tussen Experience Manager- en Workfront-toepassingen met Workfront API-sleutel voor instanties die naar Adobe IMS zijn gemigreerd.

* Wanneer u externe bestanden of mappen koppelt, worden in de Workfront-toepassing de `SERVER_ERROR` foutbericht. Het foutbericht verwijst naar een niet-geautoriseerde uitzondering vanwege een onjuiste combinatie van API-sleutels.

* Wanneer u een Create werkstroom van de Taak voor activa uitvoert, toont de Null uitzondering van de Wijzer in de logboekberichten.

* Wanneer u de optie `Replace Spaces with DASH` onder Geavanceerde instellingen in Experience Manager resulteert dit in het maken van dubbele mappen in Workfront.

### Release juni 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] bevat nu de volgende updates:

* Wanneer u uploadt via een gekoppelde map of de `Send To` Actie beschikbaar in Workfront om elementen te uploaden naar as a Cloud Service Experience Manager. De elementen worden beschadigd en kunnen niet worden geopend in Adobe Photoshop.

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

