---
title: Integreren met Adobe Analytics
description: Leer hoe u Adobe Analytics kunt integreren met AEM as a Cloud Service.
feature: Administering
role: Admin
exl-id: e353a1fa-3e99-4d79-a0d1-40851bc55506
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 1%

---

# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM as a Cloud Service te integreren, kunt u uw webpaginageactiviteit volgen. De integratie vereist:

* met de Touch-gebruikersinterface een analytische configuratie maken in AEM as a Cloud Service. IMS-verificatie is vereist om Adobe Analytics te integreren met AEM as a Cloud Service.
* Adobe Analytics toevoegen en configureren als extensie in [Adobe starten](#analytics-launch). Ga voor meer informatie over het starten van Adobe naar [deze pagina](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html).

Vergeleken met vorige versies van AEM, wordt de kadersteun niet verstrekt in de Configuratie van Analytics in AEM as a Cloud Service. In plaats daarvan wordt het nu gedaan door Adobe Launch, dat het feitelijk hulpmiddel is om een AEM plaats met Analytische mogelijkheden (bibliotheken JS) van instrumenten te voorzien. In de Lancering van Adobe, wordt een bezit gecreeerd waar de uitbreiding van Adobe Analytics kan worden gevormd en de regels worden gecreeerd om gegevens naar Adobe Analytics te verzenden. Adobe Launch heeft in de plaats getreden van de door de sitecatalyst geleverde analytische taak.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service-klanten die geen bestaande account voor Analytics hebben, kunnen toegang aanvragen tot het Analytics Foundation Pack voor Experience Cloud. This Foundation Pack provided volume limited use of Analytics.

## Adobe Analytics-configuratie maken {#analytics-configuration}

1. Navigeren naar **Gereedschappen** → **Cloud Services**.
2. Selecteren **Adobe Analytics**.
   ![Adobe Analytics-venster](assets/analytics_screen2.png "Adobe Analytics-venster")
3. Selecteer de **Maken** knop.
4. Vul de details in (zie hieronder), en klik **Verbinden**.

### Configuratieparameters {#configuration-parameters}

De velden in het configuratievenster zijn als volgt:

![Configuratieparameters](assets/properties_field2.png "Configuratieparameters")

| Eigenschap | Beschrijving |
|---|---|
| Titel | De configuratienaam |
| IMS-configuratie | De IMS-configuratie selecteren (zie het hoofdstuk hieronder) |
| Segment | Optie voor het gebruik van een analysesegment dat is gedefinieerd in de huidige rapporteringssuite. De analyserapporten worden gefilterd op basis van het segment. Zie [deze pagina](https://experienceleague.adobe.com/docs/analytics/components/segmentation/seg-overview.html) voor meer informatie. |
| Rapportageopties | Een opslagplaats waar u gegevens en trekkingsrapporten verzendt. Een rapportsuite definieert de volledige, onafhankelijke rapportage op een gekozen website, een set websites of een subset van websitepagina&#39;s. U kunt de rapporten bekijken die van één enkele rapportreeks worden gehaald en kunt dit gebied in een configuratie op elk ogenblik overeenkomstig uw vereisten uitgeven. |

### Adobe Analytics met IMS-verificatie {#configuration-parameters-ims}

Een IMS-configuratie is vereist om Adobe Analytics op de juiste manier te integreren met AEM as a Cloud Service. Deze configuratie moet worden gecreeerd zodat zie [page](/help/sites-cloud/integrating/integration-adobe-analytics-ims.md) om te leren hoe te om de configuratie van Analytics IMS tot stand te brengen.

### Een configuratie toevoegen aan een site {#add-configuration}

Ga als volgt te werk om een Touch UI-configuratie op een site toe te passen: **Sites** → **Een sitepagina selecteren** → **Eigenschappen** → **Geavanceerd** → **Configuratie** → selecteer de configuratiehuurder.

## Adobe Analytics integreren op AEM sites met behulp van Adobe starten {#analytics-launch}

Adobe Analytics kan als extensie worden toegevoegd aan de eigenschap Launch. De regels kunnen worden bepaald om afbeelding uit te voeren en een postvraag aan Adobe Analytics te maken:

* Controle [deze video](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/via-adobe-launch/basic-configuration-of-the-analytics-launch-extension.html) om te leren hoe te om de uitbreiding van Analytics in Lancering voor een basisplaats te vormen.

* Zie [deze pagina](https://experienceleague.adobe.com/docs/core-services-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html) voor meer informatie over hoe u regels maakt en gegevens naar Adobe Analytics verzendt.

>[!NOTE]
>
>De configuratie IMS (technische rekeningen) voor Lancering wordt preconfigured in AEM as a Cloud Service. U hoeft deze configuratie niet te maken.

>[!NOTE]
>
>Bestaande (verouderde) frameworks werken nog, maar kunnen niet worden geconfigureerd in de aanraakinterface. Het is raadzaam om de configuraties van de veranderlijke afbeelding in Lancering opnieuw op te bouwen.
