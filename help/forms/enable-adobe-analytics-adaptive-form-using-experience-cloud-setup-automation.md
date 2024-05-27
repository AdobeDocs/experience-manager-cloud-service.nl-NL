---
title: Hoe kan Adobe Analytics een snelle analyse van een adaptieve vorm mogelijk maken?
description: Met Experience Cloud Setup Automation kunt u Adobe Analytics verbinden met een adaptief formulier voor een snelle analyse en inzichten van de interactie en betrokkenheid van bezoekers.
keywords: Adobe Analytics inschakelen voor een adaptief formulier met Experience Cloud Setup Automation, Adobe Analytics inschakelen in Forms, Adobe Analytics in Adaptive Forms, Forms Analytics Integration, Forms en Adobe Analytics
feature: Adaptive Forms
role: Admin, User
exl-id: 0e1aa040-08b4-4c1a-b247-ad6fff410187
source-git-commit: a23576b5dc6d78a29fe19cd23f3c4788f2bee23e
workflow-type: tm+mt
source-wordcount: '1554'
ht-degree: 0%

---

# Adobe Analytics inschakelen voor een adaptief formulier met behulp van Experience Cloud Setup Automation {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dit artikel |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/configure-analytics-forms-documents.html) |

Met de Experience Cloud Setup Automation kunt u Adobe Analytics verbinden met Adaptive Forms. Dit biedt een snelle analyse van de interactie van gebruikers met uw formulieren en inzicht in de interactie en betrokkenheid van bezoekers. De Automatisering van de Opstelling van het Experience Cloud helpt ook vormprestaties controleren die metriek zoals voltooiingstijden en drop-off punten impliceren. Deze analyse helpt formulieren te optimaliseren voor een betere gebruikerservaring en maakt onderscheid tussen gebruikersgedrag op basis van bijvoorbeeld de aanmeldingsstatus van anonieme gebruikers, om algemene trends en patronen te identificeren.

## Voordelen van de integratie van Adobe Analytics met Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Inzichten in eindgebruikergedrag**: Adobe Analytics helpt inzicht te krijgen in het gedrag van de eindgebruiker, onthult acties van de gebruiker, drop-outs en voltooiingspercentages, waardoor een beter inzicht ontstaat in hoe individuen omgaan met formulieren.
* **Niet-technische zakelijke gebruikers toegang geven tot inzicht**: Adobe Analytics biedt via zijn gebruiksvriendelijke interface zelfs niet-technische gebruikers de mogelijkheid om toegang te krijgen tot en gegevens te interpreteren over het gebruik van formulieren, waardoor gegevensgestuurde beslissingen worden bevorderd om de ervaring met inschrijving te verbeteren.
* **Ervaring voor gegevensvastlegging optimaliseren op basis van gebruik**: Organisaties identificeren eenvoudig pijnpunten in het vastleggen van gegevens, wat leidt tot gerichte verbeteringen die de bruikbaarheid van formulieren verbeteren en het plaatsen van gegevens met succes verhogen.

## Bereik van adaptieve Forms-gebruiksmaatstaven {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics biedt een uitgebreide reeks maatstaven voor Adaptive Forms-prestaties die zijn ontworpen om waardevolle inzichten in formuliergebruik te bieden en biedt een snelle analyse. Deze cijfers zijn:

* **Formulieruitvoeringen, formulierverzendingen, validatiefouten en unieke bezoekers**, zodat u het gebruik en de doeltreffendheid van uw formulieren kunt beoordelen.

* **Inzichten van bezoekers** met bezoek- en verzendfrequenties en unieke aantallen bezoekers, zodat u een uitgebreide weergave van het publiek van uw formulier kunt weergeven.

* **Apparaattype** gegevens die u informeren over de apparaten die gebruikers gebruiken om toegang te krijgen tot uw formulieren.

* **Geografische indeling** onthult de regionale distributie van uw vormgebruikers.

* **Verkeerbronnen** en **Populaire formulieren** Metrische gegevens die bestaan uit de belangrijkste verwijzende domeinen en de meest bezochte formulieren, helpen u te begrijpen waar uw verkeer vandaan komt en welke formulieren het populairst zijn.

* **Gebruikersactiviteiten op de belangrijkste formulieren** biedt inzichten in veldbezoeken, formulieruitvoeringen, validatiefouten, verlaten formulieren en het verzenden van formulieren, zodat u het gedrag van de gebruiker kunt analyseren.

* **Tijdlijn voor aan formulieren bestede tijd** Deze weergave biedt een tijdlijnweergave van de betrokkenheid van gebruikers bij uw formulieren.

* **Gebieden waar bijstand van bezoekers nodig is** metriek die hulpmeningen, bevestigingsfouteninstanties, en de frequenties van het veldbezoek omvatten, die benadrukken waar de gebruikers hulp bij het invullen van formulieren kunnen nodig hebben.

![Analyserapport](assets/analytics-report.png){width="100%"}


Voor gedetailleerde informatie over elke metrisch, bezoek [AEM Forms-analyserapporten weergeven en begrijpen](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Vereisten {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

Voor Experience Cloud Setup Automation is een **Adobe Analytics-licentie**, **Gegevensverzameling (voorheen Adobe starten)** om het bijhouden van scripts te beheren, en **Experience Manager Forms-licentie** voor gestroomlijnde gegevenssamenvoeging en het genereren van inzicht.

Als u een actieve licentie hebt voor **Adobe Analytics** en **Experience Manager Forms** en u hebt integratie met **Gegevensverzameling (voorheen Adobe starten)**, zou u hun beschikbaarheid binnen uw ontwikkelaarsconsole moeten verifiëren.

Als u wilt controleren of het bovenstaande beschikbaar is voor uw as a Cloud Service Forms-omgeving, gaat u naar de [ontwikkelingsconsole](https://developer.adobe.com/console/projects)navigeer naar het project en doorzoek uw project met de programma-id - omgeving-id, bijvoorbeeld voor de omgeving met URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, programma-id - milieu-id is `p45913-e175111`. Zorg ervoor dat de Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API vermeld zijn. Als deze worden vermeld, kunt u Adobe Analytics inschakelen voor een snelle analyse van uw Adaptive Forms.

![Forms Analytics Integration vereist](assets/analytics-aem.png){width="100%"}

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html)
-->

## Adobe Analytics configureren {#configure-adobe-analytics}

Voer de onderstaande stappen uit om Adobe Analytics in te schakelen en te configureren voor een snelle analyse van uw Adaptive Forms:

* [Adobe Analytics for Adaptive Forms inschakelen op basis van Foundation Components](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [Adobe Analytics for Adaptive Forms inschakelen op basis van Core Components](#integrate-adobe-analytics-with-aem-forms-for-core-components)

>[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)


<!--
>[!NOTE]
>
> This is the demo video for **Foundation Component**. In **Core Component** you are required to perform similar steps but the container is not chosen for forms.
-->

### Adobe Analytics inschakelen met Adaptive Forms for Foundation Component {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. Een configuratiecontainer maken voor cloudservices:
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   1. Selecteer of creeer een Container van de Configuratie en laat de omslag voor toe **[!UICONTROL Cloud Configurations]**.
   1. Selecteren **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.
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

![Geïntegreerde AEM Analytics](assets/analytics-aem-integrated.png){width="100%"}


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

   ![Rapport weergeven](assets/activ-aa.png){width="100%"}

1. Klikken **Adobe Analytics** om uw rapport te bekijken en prestatiesgegevens te analyseren.

Als u via de handmatige methode een adaptief formulier wilt verbinden met Adobe Analytics, gaat u naar [AEM Forms integreren met Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md).

## Analyses inschakelen voor adaptieve Forms op sites {#Connect-Analytics-to-Adaptive-Forms-in-Sites}

Door de snelle analyse van uw adaptieve formulier in AEM Sites te configureren, kunt u gebruikersinteracties en formulierverzendingen bijhouden op de pagina Formulier in Sites. Door de analyses naadloos te integreren in uw Sites Forms krijgt u waardevolle inzichten in gebruikersgedrag, conversietarieven en gebieden voor verbetering in uw formulier.

### Vereisten {#Prerequisites-to-connect-forms-analytics-to-sites}

Als u verbinding wilt maken met en analyses wilt inschakelen in Adaptive Forms for AEM Sites, moet u ervoor zorgen dat uw AEM Sites een actieve Adobe Analytics heeft.

### Aangepaste Forms op sites verbinden om Analyse in te schakelen {#Connect-analytics-to-adaptive-forms}

Als u Adaptief formulier wilt koppelen aan een AEM Sites-pagina om Analytics voor een snelle-trackanalyse in te schakelen, neemt u de opdracht `customfooterlibs` clientbibliotheek naar de AEM Sites-pagina met behulp van de AEM Archetype/Git Repository en distributiepijplijn.

1. Open uw [AEM Forms Archetype of Cloned Git Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) in een teksteditor. Bijvoorbeeld, de Code van Visual Studio.

1. Navigeer naar de pagina van uw sites waar uw adaptieve formulier aanwezig is, bijvoorbeeld In dit demoproject hebben we `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.

1. De waarde kopiëren van `sling:resourceSuperType`. De waarde is bijvoorbeeld `core/wcm/components/page/v3/page`.

   ![slingerbron](/help/forms/assets/slingresource.png){width="100%"}

1. Een vergelijkbare structuur maken op de locatie `ui.apps/src/main/content/jcr_root/apps` gelijk aan `core/wcm/components/page/v3/page`.

   ![bedekkingsstructuur](/help/forms/assets/overlaystructure.png){width="100%"}

1. Voeg een `customfooterlibs.html` bestand.

   ```
   // customheaderlibs.html
   <sly data-sly-use.page="com.adobe.cq.wcm.core.components.models.Page">
   <sly data-sly-test="${page.data && page.dataLayerClientlibIncluded}" data-sly-call="${clientlib.js @ categories='core.forms.components.commons.v1.datalayer', async=true}"></sly>
   </sly>
   ```

   De `customfooterlibs.html` wordt gebruikt voor JavaScript.

1. [De pijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) om de wijzigingen te implementeren.

### Regels voor formulieranalyse op Forms in sites inschakelen {#bind-forms-analytics-rules-to-forms-in-sites}

1. Ga naar **Adobe Experience Platform-gegevensverzameling**.
1. Klikken **Tags** aan de linkerkant.
1. Zoek in uw project met de programma-id zoals in de onderstaande afbeelding wordt getoond, bijvoorbeeld voor de omgeving met URL `https://author-p45921-e175111-cmstg.adobeaemcloud.com/index.html`, programma-id is `45921`.

   ![Search-your-form-in-data-collection](/help/forms/assets/aep-data-collection.png){width="100%"}

1. Configuratie toevoegen voor **Formulierregels** en **Gegevenselementen** zoals hieronder aangegeven:

#### Formulierregels toevoegen {#form-rules}

1. Selecteer het formulier en voeg het toe **Nieuwe eigenschap** rechtsboven of klik op het formulier.
1. Klik op de pagina met eigenschappen **Regels** en selecteert u gebeurtenissen voor uw formulier. In de onderstaande voorbeeldafbeelding ziet u dat **Formuliergebeurtenissen**.

   ![Search-your-form-in-data-collection](/help/forms/assets/aep-form-event-properties.png){width="100%"}

1. Selecteer alle gebeurtenissen in het formulier en **kopiëren** die zich in de rechterbovenspoorlijn bevindt.
1. Wanneer u een **Regel kopiëren** verschijnt pop-up waar u uw pagina van Plaatsen met project-identiteitskaart zoekt, om de Regels van de Vorm te kleven.

   ![Formulierregels kopiëren](/help/forms/assets/copy-form-rules.png){width="100%"}

1. Klikken **kopiëren** om de formulierregels op de sitepagina te plakken.

#### Gegevenselementen toevoegen {#data-elements}

1. Selecteer het formulier en voeg het toe **Nieuwe eigenschap** rechtsboven of klik op het formulier.
1. Klik op de pagina met eigenschappen **Gegevenselementen** en selecteert u gebeurtenissen voor het formulier.
1. Selecteer alle gebeurtenissen in het formulier en **kopiëren** op de rechterbovenspoorstaaf.
1. Wanneer u een **Regel kopiëren** verschijnt pop-up waar u uw pagina van Plaatsen met project-identiteitskaart zoekt, om de Regels van de Vorm te kleven.
1. Klikken **kopiëren** om de formulierregels op de sitepagina te plakken.

   ![Formuliergegevenselementen](/help/forms/assets/form-data-elements.png){width="100%"}

Nadat u de regels Formulier en Sites hebt gekoppeld via de bovenstaande stappen, voert u de volgende stappen uit om Analytics in te schakelen voor uw Adaptief formulier op de pagina Sites:

1. Klikken **Publishing Flow** links.
1. Klikken **Bibliotheek toevoegen** en voert u de gewenste naam in.
1. In de **Omgeving** vervolgkeuzelijst rechts, selecteert u **ontwikkeling**.
1. Klikken **Alle gewijzigde bronnen toevoegen**.
1. Klikken **Opslaan en samenstellen tot ontwikkeling**.

![publicatie-aan-ontwikkeling](/help/forms/assets/publish-to-dev.png){width="100%"}


<!--

## Best Practices

1.    Verify that Adobe Analytics is enabled on all the forms activated for Adobe Analytics.

1.    Check the Adobe Analytics report periodically to gain insights into user behavior and form performance. For instance, you may set the cadence to 15 days or the period you prefer to choose for report analysis. This enables you to improve the forms enrollment experience.

1.    Enable Analytics for all or most of your forms for tracking and analyzing user interaction with your forms and to gain insights into visitor interactions and engagement.

1. Check your forms performance after you update your form fields or components.

1.    Share Analytics report with your peer groups for review, you can schedule your report for a later time.

-->

## Zie ook {#see-also}

* [Adaptieve Forms-analyserapporten weergeven en begrijpen](/help/forms/view-understand-aem-forms-analytics-reports.md)
* [Een adaptief formulier toevoegen aan een AEM Sites-pagina of Ervaar fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [AEM Forms integreren met Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md)
