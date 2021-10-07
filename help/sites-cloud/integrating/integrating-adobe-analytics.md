---
title: Integreren met Adobe Analytics
description: 'Integreren met Adobe Analytics '
feature: Administering
role: Admin
exl-id: e353a1fa-3e99-4d79-a0d1-40851bc55506
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 2%

---

# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM as a Cloud Service te integreren, kunt u uw webpaginageactiviteit volgen. De integratie vereist:

* met de aanraakinterface een analytische configuratie maken in AEM as a Cloud Service.
* Adobe Analytics toevoegen en configureren als een extensie in [Adobe starten](#analytics-launch). Zie [deze pagina](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html) voor meer informatie over het starten van Adobe.

Vergeleken met vorige versies van AEM, wordt de kadersteun niet verstrekt in de Configuratie van Analytics in AEM as a Cloud Service. In plaats daarvan wordt het nu gedaan door Adobe Launch, dat het feitelijk hulpmiddel is om een AEM plaats met Analytische mogelijkheden (bibliotheken JS) van instrumenten te voorzien. In Adobe Launch, wordt een bezit gecreeerd waar de uitbreiding van Adobe Analytics kan worden gevormd en de regels worden gecreeerd om gegevens naar Adobe Analytics te verzenden. Adobe Launch heeft in de plaats getreden van de door de sitecatalyst geleverde analytische taak.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service-klanten die geen bestaande account voor Analytics hebben, kunnen toegang aanvragen tot het Analytics Foundation Pack voor Experience Cloud. This Foundation Pack provided volume limited use of Analytics.

## Adobe Analytics-configuratie maken {#analytics-configuration}

1. Navigeer naar **Tools** → **Cloud Services**.
2. Selecteer **Adobe Analytics**.
   ![Adobe Analytics ](assets/analytics_screen2.png "WindowAdobe Analytics-venster")
3. Selecteer de **Create** knoop.
4. Vul de gegevens in (zie hieronder) en klik op **Connect**.

### Configuratieparameters {#configuration-parameters}

De configuratiegebieden in het venster van de Configuratie van Adobe Analytics zijn:

![Configuratieparameters ](assets/properties_field1.png "ParametersConfiguration")

| Eigenschap | Beschrijving |
|---|---|
| Bedrijf | Adobe Analytics Login Company |
| Gebruikersnaam | Adobe Analytics API-gebruiker |
| Wachtwoord | Adobe Analytics-wachtwoord voor verificatie |
| Datacenter | Het Adobe Analytics-datacenter waaraan uw account is gekoppeld (server bijvoorbeeld San Jose, Londen) |
| Segment | Optie voor het gebruik van een analysesegment dat is gedefinieerd in de huidige rapporteringssuite. De analyserapporten worden gefilterd op basis van het segment. Raadpleeg [deze pagina](https://experienceleague.adobe.com/docs/analytics/components/segmentation/seg-overview.html) voor meer informatie. |
| Rapportageopties | Een opslagplaats waar u gegevens en trekkingsrapporten verzendt. Een rapportsuite definieert de volledige, onafhankelijke rapportage op een gekozen website, een set websites of een subset van websitepagina&#39;s. U kunt de rapporten bekijken die van één enkele rapportreeks worden gehaald en kunt dit gebied in een configuratie op elk ogenblik overeenkomstig uw vereisten uitgeven. |

### Een configuratie toevoegen aan een site {#add-configuration}

Ga naar: **Sites** → **Selecteer een sitepagina** → **Properties** → **Advanced** → **Configuration** → selecteer de configuratietechnicus.

## Adobe Analytics integreren op AEM sites met behulp van Adobe starten {#analytics-launch}

Adobe Analytics kan als extensie worden toegevoegd aan de eigenschap Launch. De regels kunnen worden bepaald om afbeelding uit te voeren en een postvraag aan Adobe Analytics te maken:

* Bekijk [deze video](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/via-adobe-launch/basic-configuration-of-the-analytics-launch-extension.html) om te leren hoe te om de uitbreiding van Analytics in Lancering voor een basisplaats te vormen.

* Zie [deze pagina](https://experienceleague.adobe.com/docs/core-services-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html) voor meer informatie over het maken van regels en het verzenden van gegevens naar Adobe Analytics.

>[!NOTE]
>
>Bestaande (verouderde) frameworks werken nog, maar kunnen niet worden geconfigureerd in de aanraakinterface. Het is raadzaam om de configuraties van de veranderlijke afbeelding in Lancering opnieuw op te bouwen.

>[!NOTE]
>
>De configuratie IMS (technische rekeningen) voor Lancering wordt preconfigured in AEM as a Cloud Service. Gebruikers hoeven deze configuratie niet te maken.
