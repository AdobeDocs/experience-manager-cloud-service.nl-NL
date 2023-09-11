---
title: Adobe Analytics inschakelen voor een adaptief formulier met behulp van Experience Cloud Setup Automation
description: Met de Experience Cloud Setup Automation kunt u Adobe Analytics verbinden met een adaptief formulier. Het helpt bij het bijhouden en analyseren van gebruikersinteractie met een adaptief formulier, zodat u inzichten krijgt in de interactie en betrokkenheid van bezoekers.
source-git-commit: 96b3986f73ab71bad02b00ddc699aeecd498aebd
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---


# Adobe Analytics inschakelen voor een adaptief formulier met behulp van Experience Cloud Setup Automation {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

Met Experience Cloud Setup Automation kunt u Adobe Analytics verbinden met Adaptive Forms. Dit helpt u bij het bijhouden en analyseren van gebruikersinteractie met uw formulieren en biedt u inzicht in de interactie en betrokkenheid van bezoekers. De Automatisering van de Opstelling van het Experience Cloud helpt ook vormprestaties controleren die metriek zoals voltooiingstijden en drop-off punten impliceren. Deze analyse helpt formulieren te optimaliseren voor een betere gebruikerservaring en maakt onderscheid tussen gebruikersgedrag op basis van bijvoorbeeld de aanmeldingsstatus van anonieme gebruikers, om algemene trends en patronen te identificeren.

## Voordelen van de integratie van Adobe Analytics met Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Inzichten in eindgebruikergedrag**: Adobe Analytics helpt inzicht te krijgen in het gedrag van de eindgebruiker, onthult acties van de gebruiker, drop-outs en voltooiingspercentages, waardoor een beter inzicht ontstaat in hoe individuen omgaan met formulieren.
* **Niet-technische zakelijke gebruikers toegang geven tot inzicht**: Adobe Analytics biedt via zijn gebruiksvriendelijke interface zelfs niet-technische gebruikers de mogelijkheid om toegang te krijgen tot en gegevens te interpreteren over het gebruik van formulieren, waardoor gegevensgestuurde beslissingen worden bevorderd om de ervaring met inschrijving te verbeteren.
* **Ervaring voor gegevensvastlegging optimaliseren op basis van gebruik**: Organisaties identificeren eenvoudig pijnpunten in het vastleggen van gegevens, wat leidt tot gerichte verbeteringen die de bruikbaarheid van formulieren verbeteren en het plaatsen van gegevens met succes verhogen.

## Bereik van adaptieve Forms-gebruiksmaatstaven {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics biedt een uitgebreide reeks maatstaven voor Adaptive Forms-prestaties die zijn ontworpen om waardevolle inzichten in formuliergebruik te bieden. Deze cijfers zijn:

* **Formulieruitvoeringen, formulierverzendingen, validatiefouten en unieke bezoekers**, zodat u het gebruik en de doeltreffendheid van uw formulieren kunt beoordelen.

* **Inzichten van bezoekers** met bezoek- en verzendfrequenties en unieke aantallen bezoekers, zodat u een uitgebreide weergave van het publiek van uw formulier kunt weergeven.

* **Apparaattype** gegevens die u informeren over de apparaten die gebruikers gebruiken om toegang te krijgen tot uw formulieren.

* **Geografische indeling** onthult de regionale distributie van uw vormgebruikers.

* **Verkeerbronnen** en **Populaire formulieren** Metrische gegevens die bestaan uit de belangrijkste verwijzende domeinen en de meest bezochte formulieren, helpen u te begrijpen waar uw verkeer vandaan komt en welke formulieren het populairst zijn.

* **Gebruikersactiviteiten op de belangrijkste formulieren** biedt inzichten in veldbezoeken, formulieruitvoeringen, validatiefouten, verlaten formulieren en het verzenden van formulieren, zodat u het gedrag van de gebruiker kunt analyseren.

* **Tijdlijn voor aan formulieren bestede tijd** Deze weergave biedt een tijdlijnweergave van de betrokkenheid van gebruikers bij uw formulieren.

* **Gebieden waar bijstand van bezoekers nodig is** metriek die hulpmeningen, bevestigingsfouteninstanties, en de frequenties van het veldbezoek omvatten, die benadrukken waar de gebruikers hulp bij het invullen van formulieren kunnen nodig hebben.

![Analyserapport](assets/analytics-report.png)


Voor gedetailleerde informatie over elke metrisch, bezoek [AEM Forms-analyserapporten weergeven en begrijpen](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Vereisten {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

Voor Experience Cloud Setup Automation in Adobe Experience Manager Forms is een **Adobe Analytics-licentie**, **Gegevensverzameling (voorheen Adobe starten)** om het volgen manuscripten, en integratie met te beheren **Experience Platform Launch (API)** voor gestroomlijnde gegevenssamenvoeging en het genereren van inzichten.

Als u een actieve vergunning voor de Automatisering van de Opstelling van het Experience Cloud, Adobe Analytics, en Experience Platform Launch API hebt, zou u hun beschikbaarheid binnen uw ontwikkelaarsconsole moeten verifiëren.

Als u wilt controleren of het bovenstaande beschikbaar is voor uw as a Cloud Service Forms-omgeving, gaat u naar de [ontwikkelingsconsole](https://developer.adobe.com/console/projects)navigeer naar het project en doorzoek uw project met de programma-id, bijvoorbeeld voor de omgeving met URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, programma-id is `p45913-e175111`. Zorg ervoor dat de Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API vermeld zijn. Als deze worden vermeld, kunt u Adobe Analytics inschakelen voor uw Adaptieve Forms.

![Forms Analytics Integration vereist](assets/analytics-aem.png)

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html)
-->

## Adobe Analytics configureren {#configure-adobe-analytics}

Voer de onderstaande stappen uit om Adobe Analytics voor uw Adaptive Forms in te schakelen en te configureren:

* [Adobe Analytics for Adaptive Forms inschakelen op basis van Foundation Components](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [Adobe Analytics for Adaptive Forms inschakelen op basis van Core Components](#integrate-adobe-analytics-with-aem-forms-for-core-components)

### Adobe Analytics inschakelen met Adaptive Forms for Foundation Component {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. Een configuratiecontainer maken voor cloudservices:
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   1. Selecteer of creeer een Container van de Configuratie en laat de omslag voor toe **[!UICONTROL Cloud Configurations]**.
   1. Tikken **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.
1. Ga op uw AEM naar **[Forms]** >> **[Forms en Document]**.
1. Selecteer uw **[!UICONTROL Form]** >> **[!UICONTROL Properties]** in de **[!UICONTROL Configuration Container]** selecteert u de configuratiecontainer die u in het dialoogvenster **[!UICONTROL Configuration Browser]** in Stap 1.
1. Selecteer het taakvenster op het linkerspoor en klik op **Analyses instellen** en **Adobe Analytics activeren**.
1. Geef de gewenste naam op voor de rapportsuite. Klik op **[!UICONTROL Next]** en **[!UICONTROL Save]**.
1. Nadat u het project hebt opgeslagen, wordt de installatie enige tijd uitgevoerd tot de integratie van Adobe Analytics met uw adaptieve formulier, kunt u ook de knop **integratiestatus**.

   >[!NOTE]
   >
   >Als het instellen langer duurt dan 15 minuten, schakelt u de analysemogelijkheden voor uw formulieren opnieuw in.

1. Ga op uw AEM naar **[!UICONTROL Forms]** >> **[Forms en Document]** en selecteer uw **[!UICONTROL Form]**, ziet u dat Adobe Analytics is geïntegreerd in uw formulier, zoals wordt weergegeven in de onderstaande afbeelding.
1. Nu kunt u uw [Adobe Analytics-rapport Adaptief formulier](#view-adobe-analytics-report).

![Geïntegreerde AEM Analytics](assets/analytics-aem-integrated.png)

### Adobe Analytics inschakelen met Adaptive Forms for Core Components {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. Ga op uw AEM naar **[!UICONTROL Forms]** >> **[!UICONTROL Forms and Document]** en selecteer uw **[!UICONTROL Form]**.
1. Selecteer het Taakvenster links en klik op **Analyses instellen** en **Adobe Analytics activeren**.
1. Geef de gewenste naam op voor de rapportsuite. Klik op **[!UICONTROL Next]** en **[!UICONTROL Save]**.
1. Nadat u het project hebt opgeslagen, wordt de installatie enige tijd uitgevoerd tot de integratie van Adobe Analytics met uw adaptieve formulier, kunt u ook de knop **integratiestatus**.

   >[!NOTE]
   >
   >Als het instellen langer duurt dan 15 minuten, schakelt u de analysemogelijkheden voor uw formulieren opnieuw in.

1. Ga op uw AEM naar **[!UICONTROL Forms]** >> **[!UICONTROL Forms and Document]** en selecteer uw **[!UICONTROL Form]**, ziet u dat Adobe Analytics is geïntegreerd in uw formulier.
1. Nu kunt u uw [Adobe Analytics-rapport Adaptief formulier](#view-adobe-analytics-report).

## Adaptief Forms Adobe Analytics-rapport weergeven {#view-adobe-analytics-report}

1. Ga op uw AEM naar **[!UICONTROL Forms]** >> **[!UICONTROL Forms and Document]**.
1. Selecteer uw formulier. Adobe Analytics wordt geïntegreerd zoals links in het scherm wordt weergegeven, terwijl de Forms wordt geactiveerd voor Adobe Analytics.

   ![Rapport weergeven](assets/activ-aa.png)

1. Klikken **Adobe Analytics** om uw rapport te bekijken en prestatiesgegevens te analyseren.

