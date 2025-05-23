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

# Adobe Analytics inschakelen voor een adaptief formulier met Experience Cloud Setup Automation {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dit artikel |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/configure-analytics-forms-documents.html) |

Met Experience Cloud Setup Automation kunt u Adobe Analytics verbinden met Adaptive Forms. Dit biedt een snelle analyse van de interactie van gebruikers met uw formulieren en inzicht in de interactie en betrokkenheid van bezoekers. Met Experience Cloud Setup Automation kunt u ook de prestaties van formulieren controleren. Hierbij worden metrische gegevens zoals voltooiingstijden en aflooppunten geëvalueerd. Deze analyse helpt formulieren te optimaliseren voor een betere gebruikerservaring en maakt onderscheid tussen gebruikersgedrag op basis van bijvoorbeeld de aanmeldingsstatus van anonieme gebruikers, om algemene trends en patronen te identificeren.

## Voordelen van de integratie van Adobe Analytics met Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Inzichten in eindgebruikergedrag**: Adobe Analytics helpt om inzichten over eindgebruikergedrag te krijgen, onthult gebruikersacties, drop-outs, en voltooiingstarieven, toelatend een dieper inzicht in hoe de individuen met vormen in dienst nemen.
* **toelatend niet-technische bedrijfsgebruikers om inzichten** te bereiken: Adobe Analytics door zijn gemakkelijk te gebruiken interface laat zelfs niet-technische gebruikers toe om tot vormgebruiksgegevens toegang te hebben en te interpreteren, bevorderend gegeven-gedreven besluiten voor het verbeteren van inschrijvingservaringen.
* **Optimizing gegevens vangen ervaring die op gebruik** wordt gebaseerd: De organisaties identificeren gemakkelijk pijnpunten in gegevensvangst, die tot gerichte verbeteringen leiden die vormbruikbaarheid verbeteren en succesvolle voorlegging verhogen.

## Bereik van adaptieve Forms-gebruiksmaatstaven {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics biedt een uitgebreide reeks maatstaven voor Adaptive Forms-prestaties die zijn ontworpen om waardevolle inzichten in formuliergebruik te bieden en biedt een snelle analyse. Deze cijfers zijn:

* **de vertoningen van de Vorm, de inzendingen van de Vorm, de fouten van de Bevestiging, en Unieke bezoekers**, toestaand u om het gebruik en de doeltreffendheid van uw vormen te beoordelen.

* **de inzichten van de Bezoeker** die bezoek en voorleggingsfrequenties, en unieke bezoekersaantallen omvatten, die een uitvoerige mening van uw vormpubliek aanbieden.

* **het type van Apparaat** gegevens die u over de apparatengebruikers informeren om tot uw vormen toegang te hebben.

* **Geografische verdeling** onthult de regionale distributie van uw vormgebruikers.

* **bronnen van het Verkeer** en **Populaire vormen** metriek die uit de hoogste verwijzende domeinen en de meest-bezochte vormen bestaan, helpen u begrijpen waar uw verkeer voortkomt en welke vormen het populairst zijn.

* **activiteit van de Gebruiker op hoogste vormen** verstrekt inzichten in veldbezoeken, vormuitvoeringen, bevestigingsfouten, verlaten vormen, en vormvoorlegging, toestaand u om gebruikersgedrag te analyseren.

* **Chronologie voor tijd die aan vormen** wordt doorgebracht die een op chronologie-gebaseerde mening van gebruikersbetrokkenheid met uw vormen aanbiedt.

* **Gebieden die bezoekershulp** metriek vereisen die hulpmeningen, de instanties van de bevestigingsfout, en de frequenties van het veldbezoek omvatten, die benadrukken waar de gebruikers hulp bij het invullen van vormen kunnen nodig hebben.

![ Rapport van Analytics ](assets/analytics-report.png){width="100%"}


Voor gedetailleerde informatie over elke metrisch, bezoek [ het Bekijken en het Begrip van de Rapporten van de Analytics van AEM Forms ](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Vereisten {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

De Automatisering van de Opstelling van Experience Cloud vereist een **vergunning van Adobe Analytics**, **Inzameling van Gegevens (vroeger de Lancering van Adobe)** om het volgen manuscripten, en **vergunning van Experience Manager Forms** voor gestroomlijnde gegevenssamenvoeging en de generatie van insight te beheren.

Als u een actieve vergunning voor **Adobe Analytics** en **Experience Manager Forms** hebt, en u integratie met **de Inzameling van Gegevens (vroeger de Lancering van Adobe)** hebt, zou u hun beschikbaarheid binnen uw ontwikkelaarsconsole moeten verifiëren.

Om bovengenoemde te verifiëren zijn beschikbaar voor uw milieu van Forms as a Cloud Service, bezoek de [ ontwikkelaarsconsole ](https://developer.adobe.com/console/projects), navigeer aan project en onderzoek uw project met programma identiteitskaart - milieu identiteitskaart, bijvoorbeeld, voor het milieu met URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, programma identiteitskaart - milieu identiteitskaart is `p45913-e175111`. Zorg ervoor dat de Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API wordt vermeld. Als deze worden vermeld, kunt u Adobe Analytics inschakelen voor een snelle analyse van uw Adaptive Forms.

![ prequiste de Integratie van de Analytics van Forms ](assets/analytics-aem.png){width="100%"}

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
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. Selecteer of creeer een Container van de Configuratie, en laat de omslag voor **[!UICONTROL Cloud Configurations]** toe.
   1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.
1. Op uw instantie van AEM, ga **[Forms]** >> **[Forms en Document]**.
1. Selecteer **[!UICONTROL Form]** >> **[!UICONTROL Properties]** in **[!UICONTROL Configuration Container]** de configuratiecontainer die u in **[!UICONTROL Configuration Browser]** in Stap 1 hebt gemaakt of geselecteerd.
1. Selecteer het Comité van de Taak op het Linkerspoor en klik **Analytics van de Opstelling** en **activeer Adobe Analytics**.
1. Geef de gewenste naam op voor de rapportsuite. Klik op **[!UICONTROL Next]** en **[!UICONTROL Save]** .
1. Zodra u sparen het project, de opstellingslooppas voor wat tijd tot de integratie van Adobe Analytics met uw AanpassingsVorm, kunt u de **integratiestatus** ook controleren.

   >[!NOTE]
   >
   >Als het instellen langer duurt dan 15 minuten, schakelt u de analysemogelijkheden voor uw formulieren opnieuw in.

1. Op uw instantie van AEM, ga naar **[!UICONTROL Forms]** >> **[Forms en Document]** en selecteer uw **[!UICONTROL Form]**, ziet u dat Adobe Analytics aan uw vorm zoals aangetoond in het hieronder beeld wordt geïntegreerd.
1. Nu kunt u uw [ Adaptief rapport van Adobe Analytics van de Vorm bekijken ](#view-adobe-analytics-report).

![ Geïntegreerde Analytics van AEM ](assets/analytics-aem-integrated.png){width="100%"}


### Adobe Analytics inschakelen met Adaptive Forms for Core Components {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. Ga in uw AEM-instantie naar **[!UICONTROL Forms]** >> **[!UICONTROL Forms and Document]** en selecteer uw **[!UICONTROL Form]** .
1. Selecteer het Comité van de Taak op de linkerzijde en klik **Analytics van de Opstelling** en **activeer Adobe Analytics**.
1. Geef de gewenste naam op voor de rapportsuite. Klik op **[!UICONTROL Next]** en **[!UICONTROL Save]** .
1. Zodra u sparen het project, de opstellingslooppas voor wat tijd tot de integratie van Adobe Analytics met uw AanpassingsVorm, kunt u de **integratiestatus** ook controleren.

   >[!NOTE]
   >
   >Als het instellen langer duurt dan 15 minuten, schakelt u de analysemogelijkheden voor uw formulieren opnieuw in.

1. Ga in uw AEM-exemplaar naar **[!UICONTROL Forms]** >> **[!UICONTROL Forms and Document]** en selecteer **[!UICONTROL Form]** . Adobe Analytics is nu geïntegreerd in uw formulier.
1. Nu kunt u uw [ Adaptief rapport van Adobe Analytics van de Vorm bekijken ](#view-adobe-analytics-report).

## Adaptief Forms Adobe Analytics-rapport weergeven {#view-adobe-analytics-report}

1. Ga in uw AEM-instantie naar **[!UICONTROL Forms]** >> **[!UICONTROL Forms and Document]** .
1. Selecteer uw formulier. Adobe Analytics wordt geïntegreerd zoals links in het scherm wordt weergegeven, terwijl de Forms wordt geactiveerd voor Adobe Analytics.

   ![ Rapport van de Mening ](assets/activ-aa.png){width="100%"}

1. Klik **Adobe Analytics** om uw rapport te bekijken en prestatiesgegevens te analyseren.

Om een AanpassingsVorm met Adobe Analytics te verbinden gebruikend de handmethode, ga [ AEM Forms met Adobe Analytics ](/help/forms/integrate-aem-forms-with-adobe-analytics.md) integreren.

## Analyses inschakelen voor adaptieve Forms op sites {#Connect-Analytics-to-Adaptive-Forms-in-Sites}

Door de snelle analyse van uw adaptieve formulier in AEM Sites te configureren, kunt u gebruikersinteracties en formulierverzendingen bijhouden op de pagina Formulier in Sites. Door de analyses naadloos te integreren in uw Sites Forms krijgt u waardevolle inzichten in gebruikersgedrag, conversietarieven en gebieden voor verbetering in uw formulier.

### Vereisten {#Prerequisites-to-connect-forms-analytics-to-sites}

Als u verbinding wilt maken met en analyses wilt inschakelen in Adaptive Forms for AEM Sites, moet u ervoor zorgen dat uw AEM Sites een actieve Adobe Analytics heeft.

### Aangepaste Forms op sites verbinden om Analyse in te schakelen {#Connect-analytics-to-adaptive-forms}

Als u Adaptief formulier wilt verbinden met een AEM Sites-pagina om Analytics voor een snelle-trackanalyse in te schakelen, neemt u de `customfooterlibs` -clientbibliotheek op naar de AEM Sites-pagina met behulp van de AEM Archetype/Git Repository and Deployment-pijplijn.

1. Open uw [ Archetype van AEM Forms of het gekloonde project van de Bewaarplaats van de it ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) in een tekstredacteur. Bijvoorbeeld, de Code van Visual Studio.

1. Navigeer naar de pagina van uw sites waar uw adaptieve formulier aanwezig is, bijvoorbeeld In dit demoproject hebben we `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml` .

1. Kopieer de waarde van `sling:resourceSuperType` . De waarde is bijvoorbeeld `core/wcm/components/page/v3/page` .

   ![ sling middel ](/help/forms/assets/slingresource.png){width="100%"}

1. Maak een vergelijkbare structuur op dezelfde locatie `ui.apps/src/main/content/jcr_root/apps` als `core/wcm/components/page/v3/page` .

   ![ bekledingsstructuur ](/help/forms/assets/overlaystructure.png){width="100%"}

1. Voeg een `customfooterlibs.html` -bestand toe.

   ```
   // customheaderlibs.html
   <sly data-sly-use.page="com.adobe.cq.wcm.core.components.models.Page">
   <sly data-sly-test="${page.data && page.dataLayerClientlibIncluded}" data-sly-call="${clientlib.js @ categories='core.forms.components.commons.v1.datalayer', async=true}"></sly>
   </sly>
   ```

   `customfooterlibs.html` wordt gebruikt voor JavaScript.

1. [ stel de pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) in werking om de veranderingen op te stellen.

### Regels voor formulieranalyse op Forms in sites inschakelen {#bind-forms-analytics-rules-to-forms-in-sites}

1. Bezoek de **Inzameling van Gegevens van Adobe Experience Platform**.
1. Klik **Markeringen** die op de linkerkant worden gevestigd.
1. Zoek in uw project met de programma-id, zoals in de onderstaande afbeelding wordt getoond, bijvoorbeeld voor de omgeving met URL `https://author-p45921-e175111-cmstg.adobeaemcloud.com/index.html` , is programma-id `45921` .

   ![ onderzoek-uw-vorm-in-gegeven-inzameling ](/help/forms/assets/aep-data-collection.png){width="100%"}

1. Voeg configuratie voor **Regels van de Vorm** en **Elementen van Gegevens** zoals hieronder gegeven toe:

#### Formulierregels toevoegen {#form-rules}

1. Selecteer uw vorm en voeg **Nieuw bezit** toe dat op het hogere recht wordt gevestigd, of klik uw vorm.
1. Voor de eigenschappen pagina, klik **Regels** en selecteer gebeurtenissen voor uw vorm, in het voorbeeld hieronder, is het **Gebeurtenissen van de Vorm**.

   ![ onderzoek-uw-vorm-in-gegeven-inzameling ](/help/forms/assets/aep-form-event-properties.png){width="100%"}

1. Selecteer alle gebeurtenissen van uw vorm en **exemplaar** dat op het hogere juiste spoor wordt gevestigd.
1. Zodra u kopieert, verschijnt pop-up van de Regel van het a **Exemplaar** waar u uw pagina van Plaatsen met project-identiteitskaart zoekt, om de Regels van de Vorm te kleven.

   ![ kopiëren-vorm-regels ](/help/forms/assets/copy-form-rules.png){width="100%"}

1. Klik **exemplaar** om de vormregels aan de pagina van Plaatsen te kleven.

#### Gegevenselementen toevoegen {#data-elements}

1. Selecteer uw vorm en voeg **Nieuw bezit** toe dat op het hogere recht wordt gevestigd, of klik uw vorm.
1. Voor de eigenschappen pagina, klik {de Elementen van Gegevens 0} **en selecteer gebeurtenissen voor uw vorm.**
1. Selecteer alle gebeurtenissen van uw vorm en **exemplaar** die op het hogere juiste spoor worden gevestigd.
1. Zodra u kopieert, verschijnt pop-up van de Regel van het a **Exemplaar** waar u uw pagina van Plaatsen met project-identiteitskaart zoekt, om de Regels van de Vorm te kleven.
1. Klik **exemplaar** om de vormregels aan de pagina van Plaatsen te kleven.

   ![ vorm-gegeven-elementen ](/help/forms/assets/form-data-elements.png){width="100%"}

Nadat u de regels Formulier en Sites hebt gekoppeld via de bovenstaande stappen, voert u de volgende stappen uit om Analytics in te schakelen voor uw Adaptief formulier op de pagina Sites:

1. Klik **het Publiceren Stroom** op de linkerzijde.
1. Klik **toevoegen Bibliotheek** en ga de naam in u verkiest.
1. In het **Milieu** drop-down op het recht, uitgezochte **ontwikkeling**.
1. Klik **toevoegen Alle Gewijzigde Middelen**.
1. Klik **sparen en bouwen aan Ontwikkeling**.

![ publiceren-aan-ontwikkeling ](/help/forms/assets/publish-to-dev.png){width="100%"}


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
