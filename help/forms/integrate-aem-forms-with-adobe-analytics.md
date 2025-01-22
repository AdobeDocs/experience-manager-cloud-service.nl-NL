---
title: Hoe kan AEM Forms met Adobe Analytics worden geïntegreerd?
seo-title: Learn how to integrate AEM Forms with Adobe Analytics.
exl-id: 0730432e-75b8-4b35-a377-ae4a2bee6c9f
hidefromtoc: true
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: 64a8b363cff079aa0a6f56effd77830ac797deca
workflow-type: tm+mt
source-wordcount: '1508'
ht-degree: 0%

---

# AEM Forms integreren met [!DNL Adobe Analytics] {#integrate-aem-forms-with-adobe-analytics}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/configure-analytics-forms-documents.html) |
| AEM as a Cloud Service | Dit artikel |

<span class="preview"> In dit document wordt de handmatige procedure beschreven voor het inschakelen van Adobe Analytics op een adaptief formulier. Nochtans, adviseert de Adobe om [ te gebruiken laat Adobe Analytics voor een Aangepast Vorm toe gebruikend de Automatisering van de Opstelling van het Experience Cloud ](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md). </span>

AEM Forms integreert met [ Adobe Analytics ](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/overview.html?lang=en) om u toe te staan om prestatiesmetriek voor uw gepubliceerde vormen te vangen en te volgen. Het doel achter het analyseren van deze metriek is bedrijfsgebruikers toe te laten om inzicht in eindgebruikergedrag te verwerven en de ervaring van het gegevensvangst te optimaliseren. U kunt het gedrag vastleggen en volgen van zowel aangemelde als niet-aangemelde (anonieme) gebruikers via Adobe Analytics for Adaptive Forms.

Nadat u de in dit artikel vermelde handelingen hebt uitgevoerd, kunt u rapporten configureren en weergeven in [!DNL Adobe Analytics] , zoals wordt geïllustreerd in de volgende video:

>[!VIDEO](https://video.tv.adobe.com/v/337262)

U kunt [!DNL Adobe Analytics] gebruiken om interactiepatronen en problemen te ontdekken waarmee gebruikers worden geconfronteerd wanneer ze adaptieve formulieren gebruiken. In [!DNL Adobe Analytics] wordt informatie over de volgende gebeurtenissen bijgehouden en opgeslagen:

* **geeft terug**: Aantal tijden een vorm wordt geopend.

* **voorleggen**: Aantal tijden een vorm wordt voorgelegd.

* **Verlaat**: Aantal tijden de gebruikers verlaten zonder de vorm te voltooien.

* **Fout**: Aantal fouten die op het paneel en op de gebieden van het paneel worden ontmoet.

* **Hulp**: Aantal tijden een gebruiker opent hulp van een paneel en de gebieden van het paneel.

* **Bezoek van het Gebied**: Aantal tijden een gebruiker een gebied in de vorm bezoekt.

* **sparen**: Aantal tijden de gebruikers sparen een vorm aan het Portaal van Forms.

Naast deze gebeurtenissen uit het vak kunt u aangepaste gebeurtenissen definiëren in adaptieve formulieren met een regeleditor en deze gebeurtenissen toewijzen aan gebeurtenissen in [!DNL Adobe Analytics]

In de volgende afbeelding ziet u de handelingen die u moet uitvoeren voordat u rapporten kunt weergeven in [!DNL Adobe Analytics] :

![ Overzicht van Analytics ](assets/analytics-workflow.png)

## 1. Configureren [!DNL Adobe Analytics] {#Configure-adobe-analytics}

Maak voordat u [!DNL Adobe Analytics] configureert:

* Een Adobe ID aan login aan [ Adobe Experience Cloud ](https://experience.adobe.com/#/home).
* A [ rapportreeks ](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html).


### AEM Forms- en [!DNL Adobe Analytics] extensies installeren {#install-extensions}

Voer de volgende stappen uit om AEM Forms en [ Adobe Analytics ](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html) uitbreidingen te vormen:

1. Meld u aan bij Adobe Experience Cloud en selecteer de gewenste naam voor het bedrijf.

1. Selecteer **[!UICONTROL Launch/Data Collection]** en selecteer **[!UICONTROL Go to Launch/Data Collection]** .

1. Selecteer **[!UICONTROL New property]** en geef een naam op voor de configuratie.

1. Geef een domeinnaam op en selecteer **[!UICONTROL Save]** om de eigenschap op te slaan.

1. Selecteer de configuratienaam die beschikbaar is in de lijst Tageigenschappen.

1. Selecteer **[!UICONTROL Extensions]** in de sectie **[!UICONTROL Authoring]** .

1. Selecteer **[!UICONTROL Catalog]** en selecteer **[!UICONTROL Install]** voor de extensie **[!UICONTROL Adobe Experience Manager Forms]** . **[!UICONTROL Adobe Experience Manager Forms]** vertoningen in de lijst van geïnstalleerde uitbreidingen beschikbaar in het **Geïnstalleerde** lusje.

1. Selecteer **[!UICONTROL Install]** voor de extensie **[!UICONTROL Adobe Analytics]** .
1. Selecteer de naam van de rapportsuite in de vervolgkeuzelijsten **[!UICONTROL Development Report Suites]** , **[!UICONTROL Staging Report Suites]** en **[!UICONTROL Product Report Suites]** en selecteer **[!UICONTROL Save]** om de extensie op te slaan.

### Gegevenselementen configureren {#configure-data-elements}

U kunt om het even welke gevormde gegevenselementen in een regel selecteren die voor een gebeurtenis wordt gecreeerd. Wanneer een gebeurtenis plaatsvindt op een adaptief formulier, stuurt AEM Forms deze gegevenselementen naar [!DNL Adobe Analytics] .

Nadat u de extensie **[!UICONTROL Adobe Experience Manager Forms]** hebt geïnstalleerd, kunt u de volgende gegevenselementen maken:

<table>
 <tbody>
  <tr>
   <td>FieldName</th>
   <td>FieldTitle</th>
   <td>FormInstance</th>
  </tr>
  <tr>
   <td>FormName<br /> </td>
   <td>FormTitle <br /> </td>
   <td>PageName</td>
  </tr>
  <tr>
   <td>PageURL <br /> </td>
   <td>PanelTitle <br /> </td>
   <td>TimeSpent</td>
  </tr>
 </tbody>
</table>

Voer de volgende stappen uit om gegevenselementen te configureren:

1. Selecteer **[!UICONTROL Data Elements]** in de sectie **[!UICONTROL Authoring]** .

1. Selecteer **[!UICONTROL Create New Data Element]** .

1. Geef een naam op voor het gegevenselement. Bijvoorbeeld het gegevenstype Formuliertitel voor het gegevenstype FormTitle.

1. Geef **[!UICONTROL Adobe Experience Manager Forms]** op als de naam van de extensie.

1. Selecteer de **[!UICONTROL Data Element Type]** .

1. Selecteer **[!UICONTROL Save]** om het gegevenselement op te slaan.

>[!VIDEO](https://video.tv.adobe.com/v/337472)

### Regels configureren {#configure-rules}

Voer de volgende stappen uit om regels te maken op basis van de extensie **[!UICONTROL Adobe Experience Manager Forms]** :

1. Selecteer **[!UICONTROL Rules]** in de sectie **[!UICONTROL Authoring]** .

1. Selecteer **[!UICONTROL Create New Rule]** .

1. Geef een naam voor de regel op. Formulier verzenden bijvoorbeeld om formulierverzendingen op te nemen.

1. Selecteer **[!UICONTROL Add]** in de sectie **[!UICONTROL Events]** .

1. Geef **[!UICONTROL Adobe Experience Manager Forms]** op als de naam van de extensie.

1. Selecteer het gebeurtenistype. De invoer voor het veld **[!UICONTROL Name]** wordt automatisch gevuld op basis van het geselecteerde gebeurtenistype.

1. Selecteer **[!UICONTROL Keep Changes]** om de gebeurtenis op te slaan.

1. Selecteer **[!UICONTROL Add]** in de sectie **[!UICONTROL Actions]** .

1. Geef **[!UICONTROL Adobe Analytics]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Set Variables]** als het handelingstype. De volgende opties zijn beschikbaar in de vervolgkeuzelijst:

   * **[!UICONTROL Set Variables]**: Gebruik dit actietype om het gebeurtenistype te definiëren waarvoor de geselecteerde gegevenselementen van AEM Forms naar [!DNL Adobe Analytics] worden verzonden.

   * **[!UICONTROL Send Beacon]**: Gebruik dit actietype om gegevens van AEM Forms naar [!DNL Adobe Analytics] te verzenden.

   * **[!UICONTROL Clear Variables]**: Gebruik dit actietype om het gegevenstraject te wissen, zodat de gebeurtenis zich slechts eenmaal registreert in [!DNL Adobe Analytics] .

     Het wordt aanbevolen het actietype **[!UICONTROL Set Variables]** te gebruiken om de gebeurtenis en gegevenselementen te configureren, vervolgens **[!UICONTROL Send Beacon]** te gebruiken om gegevens te verzenden en vervolgens **[!UICONTROL Clear Variables]** te gebruiken om het gegevenstraject te wissen.

1. In de **[!UICONTROL Props]** sectie, kaart de opties van de rapportreeks beschikbaar in de drop-down lijst met de gegevenselementen die gebruikend [ worden bepaald gegevenselementen ](#configure-data-elements) vormen.

   Bijvoorbeeld, om **het gegevenselement van de Titel van de Vorm** van AEM Forms naar [!DNL Adobe Analytics] te verzenden wanneer u een vorm voorlegt:
   1. In de **[!UICONTROL Props]** sectie, selecteer een steun voor Titel van de Vorm beschikbaar in de rapportreeks en selecteer dan ![ pictogram van het Gegevensbestand ](assets/database-icon.svg) om het aan Titel in kaart te brengen van de Vorm die in [ wordt gecreeerd vormt gegevenselementen ](#configure-data-elements).

      ![ bepalen-props ](assets/define-props.png)

   1. Selecteer **[!UICONTROL Add Another]** om meer gegevenselementen aan de lijst toe te voegen.

1. Selecteer in de sectie **[!UICONTROL Events]** een gebeurtenis uit de opties in de rapportsuite en selecteer **[!UICONTROL Keep Changes]** .

1. Selecteer + in de sectie **[!UICONTROL Actions]** en geef **[!UICONTROL Adobe Analytics]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Send Beacon]** als het handelingstype. Selecteer **[!UICONTROL s.t()]** in het rechterdeelvenster om gegevens naar [!DNL Adobe Analytics] te verzenden en behandel deze als een paginaweergave of **[!UICONTROL s.tl()]** om gegevens naar [!DNL Adobe Analytics] te verzenden en behandel deze niet als een paginaweergave. Selecteer **[!UICONTROL Keep Changes]** .

1. Selecteer + in de sectie **[!UICONTROL Actions]** en geef **[!UICONTROL Adobe Analytics]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Clear Variables]** als het handelingstype. Selecteer **[!UICONTROL Keep Changes]**. Nadat u deze stappen hebt uitgevoerd, wordt de sectie **[!UICONTROL Actions]** weergegeven als:
   ![ Configuratie van Acties ](assets/actions-config.png)

   Pas de sectie **[!UICONTROL Actions]** aan uw wensen aan. Bijvoorbeeld, kunt u twee **verzenden de stappen van het Baken** in een stroom van de Actie bepalen om gegevens naar [!DNL Adobe Analytics] te verzenden en het als paginamening in één stap te behandelen en gegevens naar [!DNL Adobe Analytics] te verzenden en het niet als paginamening in de tweede stap te behandelen.

   ![ Configuratie van Acties ](assets/actions-config-2.png)

1. Selecteer **[!UICONTROL Save]** om de regel op te slaan.

   U kunt regels maken voor alle gebeurtenistypen, zoals Verlaten, Fout, Veldbezoek, Help, Rendering, Opslaan en Verzenden.

>[!VIDEO](https://video.tv.adobe.com/v/337425)


### Publish-stromen {#publish-flow}

Nadat u de gegevenselementen hebt gemaakt en gebruikt in regels, publiceert u de configuratie voor het verzamelen van formuliergegevens in [!DNL Adobe Analytics] .

Voer de volgende stappen uit om de configuratie te publiceren:

1. Selecteer **[!UICONTROL Publishing Flow]** in de sectie **[!UICONTROL Publishing]** .

1. Selecteer **[!UICONTROL Add Library]** en geef een naam op en selecteer de omgeving voor de bibliotheek.

1. Selecteer **[!UICONTROL Add All Changed Resources]** en selecteer vervolgens **[!UICONTROL Save & Build to Development]** .

1. In de **[!UICONTROL Development]** sectie, selecteer ![ Meer opties ](assets/more-options-icon.svg) en selecteer dan **[!UICONTROL Approve & Publish to Production]**.

1. Controleer of de wijzigingen en de publicatiestroom binnenkort worden weergegeven in de sectie **[!UICONTROL Published]** .

![ de Stroom van Publish ](assets/publish-flow.png)

## 2. AEM Forms configureren {#configure-aem-forms}

Alvorens een configuratie van de Lancering van de Adobe tot stand te brengen, creeer de Configuratie van Adobe IMS die [ AdobeLancering gebruiken als Oplossing van de Wolk ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html).

### Configuratie van Adobe starten maken {#create-adobe-launch-configuration}

Voer de volgende stappen uit om een configuratie van de Lancering van de Adobe tot stand te brengen:

1. Ga in de AEM Forms Author-instantie naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Launch Configurations]** .

1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]** .

1. Geef een titel voor de configuratie op in het veld **[!UICONTROL Title]** .

1. Selecteer de [ bijbehorende configuratie van Adobe IMS ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html).

1. Selecteer de naam van het gebruikte bedrijf terwijl [ het vormen Adobe Analytics ](#Configure-adobe-analytics).

1. Selecteer de naam van het gecreeerde bezit terwijl [ het vormen Adobe Analytics ](#install-extensions).

1. Selecteer **[!UICONTROL Save & Close]** .

1. Publish de configuratie.

### [!DNL Adobe Analytics] inschakelen voor een adaptief formulier {#enable-analytics-adaptive-form}

De [!DNL Adobe Launch] -configuratie gebruiken in een bestaand adaptief formulier:

1. Ga in de AEM Forms Author-instantie naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer het adaptieve formulier en selecteer **[!UICONTROL Properties]** .
1. In het **[!UICONTROL Basic]** lusje, selecteer de [ gebruikte configuratiecontainer ](#create-adobe-launch-configuration) terwijl het creëren van de configuratie van de Lancering van de Adobe.
1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Analytics] .
1. Publish het formulier.

Nadat u [!DNL Adobe Analytics] voor een adaptieve vorm toelaat, kunt u [ bevestigen ](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html?lang=en#validate-the-page-view-beacon) als er een aangewezen stroom van de gegevensgebeurtenis tussen AEM Forms en [!DNL Adobe Analytics] is. De integratie van AEM Forms met Adobe Analytics is voltooid. U kunt nu [ vormen en rapporten in Adobe Analytics ](#view-reports-adobe-analytics) bekijken.

### Regels maken om aangepaste gebeurtenissen vast te leggen (optioneel) {#capture-custom-events}

Maak regels voor specifieke velden van een adaptief formulier met behulp van een regeleditor om analysegegevens van een adaptief formulier te verzenden naar [!DNL Adobe Analytics] .

In een proces in twee fasen definieert u een regel voor een veld in een adaptieve vorm. De regel verzendt een gebeurtenis. De naam van de gebeurtenis wordt toegewezen aan een aangepaste vastleggebeurtenis in de Adobe Launch.

U kunt als volgt regels maken met behulp van een regeleditor:

1. Selecteer het gebied en selecteer ![ Redacteur van de Regel ](assets/rule-editor-icon.svg) om de pagina van de regelredacteur te openen.
1. Definieer een voorwaarde in de sectie [!UICONTROL When] van de regel.
1. Selecteer in de sectie [!UICONTROL Then] van de regel de optie **[!UICONTROL Dispatch Event]** in de vervolgkeuzelijst **[!UICONTROL Select Action]** .
1. Geef de naam van de gebeurtenis op in het veld **[!UICONTROL Type Event Name]** .

Bijvoorbeeld, als de geboortedatum vóór een bepaalde datum is, verzendt AEM Forms de **gebeurtenis van de Veiligheid**.

![ de Gebeurtenis van de Verzending ](assets/security-event.png)

U kunt als volgt de gebeurtenis toewijzen aan een aangepaste vastleggebeurtenis in [!DNL Adobe Analytics] :

1. [ creeer een regel ](#configure-rules).

1. Selecteer **[!UICONTROL Add]** in de sectie **[!UICONTROL Events]** .

1. Geef **[!UICONTROL Adobe Experience Manager Forms]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Capture Custom Event]** in de vervolgkeuzelijst **[!UICONTROL Event Type]** .

1. Geef de naam op van de gebeurtenis die u in stap 4 hebt opgegeven tijdens het maken van een regel met de regeleditor.

1. Selecteer **houden Veranderingen** en voer de rest acties uit die in [ worden gespecificeerd vormen Regels ](#configure-rules).

## 3. Configureer en bekijk rapporten in [!DNL Adobe Analytics] {#view-reports-adobe-analytics}

Nadat u een adaptief formulier hebt geconfigureerd om gebeurtenisgegevens naar [!DNL Adobe Analytics] te verzenden, kunt u rapporten weergeven in [!DNL Adobe Analytics] :

1. Selecteer ![ Uitgezochte Product ](assets/select-analytics.png) en selecteer **[!UICONTROL Analytics]**.

1. Selecteer **[!UICONTROL Create Project]** en selecteer **[!UICONTROL Blank project]** .

1. Selecteer de naam van de rapportsuite in de vervolgkeuzelijst rechtsboven in de vrije vorm.

1. Specificeer **Titel van de Vorm** in de **[!UICONTROL Search dimension items]** tekst om alle vormtitels te bekijken.

1. Zet de titel van het aangepaste formulier neer in het tekstvak **[!UICONTROL Drop a segment here (or any other component)]** .

1. Zet vanuit de sectie **[!UICONTROL Metrics]** de gebeurtenissen neer om bij te houden naar het tekstvak **[!UICONTROL Drop a metric here (or any other component)]** .

1. Selecteer ![ Visualisaties ](assets/visualization-icon.svg) en laat vallen een grafiektype aan de sectie Freeform. Op dezelfde manier kunt u veelvoudige grafiektypes aan de sectie van de Vrije vorm toevoegen.

1. Selecteer Ctrl + S en geef een naam op om het project op te slaan.

<!--

## Add AEM Forms and Adobe Analytics integration specific rules to Dispatcher {#forms-specific-rules-to-dispatcher}

Add AEM Forms and Adobe Analytics integration specific rules to filter the data traffic that is sent to the backend.

Perform the following steps to add AEM Forms and Adobe Analytics integration specific rules to Dispatcher for Experience Manager Forms as a Cloud Service:

1. Open your AEM Project and navigate to `\src\conf.dispatcher.d\filters`.
1. Open `filters.any` file for editing and add the following rule at the end of the file:

     ```json
     /00XX { /type "allow" /path "/content/forms/af/*" /method "POST" /selectors '(analyticsconfigparser)' /extension '(jsp|json)' }
     ```

1. Save and close the file.
1. Compile and deploy the project to your [!DNL AEM Forms] as a Cloud Service environment.



## Limitations {#limitations}

* Adobe Analytics can track form metrics only for authenticated users.

-->

>[!MORELIKETHIS]
>
>*[ laat Adobe Analytics aan een Aangepaste Vorm ](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md) toe