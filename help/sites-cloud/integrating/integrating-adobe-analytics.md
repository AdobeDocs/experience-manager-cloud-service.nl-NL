---
title: Integreren met Adobe Analytics
description: 'Integreren met Adobe Analytics '
translation-type: tm+mt
source-git-commit: ec747361935b94a729cdd5b6712aee6d3ce1b8a2
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 2%

---


# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM als Cloud Service te integreren, kunt u uw webpaginageactiviteit volgen. De integratie vereist:

* met de aanraakinterface een Analytics Configuration in AEM als Cloud Service maken.
* Adobe Analytics toevoegen en configureren als een extensie in [Adobe Launch].(https://docs.adobe.com/content/help/en/launch/using/intro/get-started/quick-start.html).

Vergeleken met vorige versies van AEM, wordt de kadersteun niet verstrekt in de Configuratie van Analytics in AEM als Cloud Service. In plaats daarvan gebeurt dit nu via Adobe Launch, dat het defacto instrument is voor het instrumenteren van een AEM site met Analytics-mogelijkheden (JS-bibliotheken). In Adobe Launch, wordt een bezit gecreeerd waar de uitbreiding van Adobe Analytics kan worden gevormd en de regels worden gecreeerd om gegevens naar Adobe Analytics te verzenden. Adobe Launch heeft in de plaats getreden van de door de sitecatalyst geleverde analytische taak.

>[!NOTE]
>
>Adobe Experience Manager als klanten van de Cloud Service die geen bestaande rekening van Analytics hebben, kan om toegang tot het Pak van de Stichting van Analytics voor Experience Cloud verzoeken. This Foundation Pack provided volume limited use of Analytics.

## Analytics-configuratie maken {#analytics-configuration}

1. Navigeer naar **Gereedschappen** → **Cloud Servicen**.
2. Selecteer **Adobe Analytics Configurations**.
   ![Analytics](assets/analytics_screen.png "WindowAnalytics-venster")
3. Selecteer de knop **Maken** .
4. Vul de gegevens in (zie hieronder) en klik op **Verbinden**.

### Configuratieparameters {#configuration-parameters}

De configuratiegebieden in het venster van de Configuratie van Adobe Analytics zijn:

![Configuratieparameters](assets/properties_field.png "ParametersConfiguration")

| Eigenschap | Beschrijving |
|---|---|
| Bedrijf | Adobe Analytics Login Company |
| Gebruikersnaam | Adobe Analytics API-gebruiker |
| Wachtwoord | Adobe Analytics-wachtwoord voor verificatie |
| Datacenter | Het Adobe Analytics-datacenter waaraan uw account is gekoppeld (server bijvoorbeeld San Jose, Londen) |
| Segment | Optie voor het gebruik van een Analytics-segment dat is gedefinieerd in de huidige rapporteringssuite. De Analytics-rapporten worden gefilterd op basis van het segment. Raadpleeg [deze pagina](https://docs.adobe.com/content/help/en/analytics/components/segmentation/seg-overview.html) voor meer informatie. |
| Rapportageopties | Een opslagplaats waar u gegevens en trekkingsrapporten verzendt. Een rapportsuite definieert de volledige, onafhankelijke rapportage op een gekozen website, een set websites of een subset van websitepagina&#39;s. U kunt de rapporten bekijken die van één enkele rapportreeks worden gehaald en kunt dit gebied in een configuratie op elk ogenblik overeenkomstig uw vereisten uitgeven. |

### Een configuratie toevoegen aan een site {#add-configuration}

Ga naar: **Plaatsen** → **selecteer om het even welke plaatspagina** → **Eigenschappen** → **Geavanceerd** → **Configuratie** → selecteer de configuratiehuurder.

## Adobe Analytics integreren op AEM sites met behulp van Adobe starten

Adobe Analytics kan als extensie worden toegevoegd aan de eigenschap Launch. De regels kunnen worden bepaald om afbeelding uit te voeren en een postvraag aan Adobe Analytics te maken:

* Bekijk [deze video](https://docs.adobe.com/content/help/en/analytics-learn/tutorials/implementation/via-adobe-launch/basic-configuration-of-the-analytics-launch-extension.html) voor informatie over het configureren van de Analytics-extensie in Launch voor een basissite.

* Zie [deze pagina](https://docs.adobe.com/content/help/en/core-services-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html) voor meer informatie over het maken van regels en het verzenden van gegevens naar Adobe Analytics.

>[!NOTE]
>
>Bestaande (verouderde) frameworks werken nog, maar kunnen niet worden geconfigureerd in de aanraakinterface. Het is raadzaam om de configuraties van de veranderlijke afbeelding in Lancering opnieuw op te bouwen.

>[!NOTE]
>
>De configuratie IMS (technische rekeningen) voor Lancering wordt preconfigured in AEM als Cloud Service. Gebruikers hoeven deze configuratie niet te maken.
