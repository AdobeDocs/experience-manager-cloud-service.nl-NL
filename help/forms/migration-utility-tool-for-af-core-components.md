---
title: Hulpmiddel van het Hulpmiddel van de migratie/AEM Moderniseer Hulpmiddelen om Aangepaste Forms om te zetten die op de Componenten van de Stichting aan de Component van de Kern wordt gebaseerd vormen
description: Leer om Hulpmiddelen van het Hulpprogramma van de Migratie te installeren en te gebruiken/AEM Moderniseren om Aangepaste Forms om te zetten die op de Componenten van de Stichting aan de Vorm van de Kern wordt gebaseerd vormen.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
exl-id: ee71a576-96a7-4c81-b3a3-1d678f010cba
feature: Adaptive Forms, Core Components
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---

# Inleiding

Het Forms Conversion-hulpprogramma, onderdeel van [Gereedschap AEM moderniseren](https://opensource.adobe.com/aem-modernize-Tools/) Met deze suite kunt u Adaptive Forms die met oudere Foundation Components is gebouwd, eenvoudig converteren naar formulieren die gebruikmaken van de moderne, ondersteunde mogelijkheden van Core Components.

## Wat is AEM moderniseringsgereedschappen?

[Gereedschappen AEM moderniseren](https://opensource.adobe.com/aem-modernize-Tools/) verwijst naar een reeks hulpprogramma&#39;s of softwaretoepassingen die zijn ontworpen om het proces van modernisering of actualisering van Adobe Experience Manager-projecten (AEM) te vergemakkelijken. Deze hulpmiddelen helpen typisch bij het omzetten van oudere componenten of functionaliteit binnen AEM in nieuwere, efficiëntere, en gesteunde alternatieven. Het Forms Conversion-hulpprogramma is geïnstalleerd onder AEM Moderniseringsgereedschappen voor het omzetten van adaptieve Forms op basis van Foundation Components in op Core Component gebaseerde formulieren.

Het Forms Conversion-hulpprogramma zet Adaptive Forms die is gebaseerd op oudere Foundation Components om in nieuwere op Core Component gebaseerde formulieren. Dit conversieproces zorgt ervoor dat de formulieren zijn afgestemd op moderne standaarden en mogelijkheden, waardoor de prestaties, compatibiliteit en het onderhoudsgemak binnen de AEM kunnen worden verbeterd.

![Gereedschappen AEM moderniseren](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> U wordt aangeraden de AEM Moderniseren Tools op uw lokale AEM te installeren. Migreer de adaptieve Forms op basis van Foundation Components naar Core Component-formulieren. Download het formulier samen met de bijbehorende middelen. Vervolgens uploadt u het formulier en de bijbehorende elementen naar de vereiste omgeving.

## Overwegingen bij het gebruiken van de AEM Moderniseren Hulpmiddelen {#considerations}

* Bij geslaagde conversies worden alle regels verwijderd die op het formulier worden toegepast. Regels worden niet automatisch gemigreerd. U moet deze regels handmatig opnieuw maken en toepassen op het geconverteerde formulier.
* De vertaalinstellingen die in het oorspronkelijke formulier worden gebruikt, worden niet overgenomen. Vertaling voor het geconverteerde formulier opnieuw configureren.
  <!-- * If the form built on Foundation Components contains custom function rules, you have to rewrite these rules for the converted form based on Core Components.-->

## Voorwaarden voor het gebruik AEM Moderniseren van gereedschappen

* [Lokale ontwikkelomgeving instellen voor AEM Forms](/help/forms/setup-local-development-environment.md)
* [Schakel Adaptieve Forms Core-componenten in voor uw omgeving.](/help/forms/enable-adaptive-forms-core-components.md)

* Voeg uw gebruikers aan toe [!DNL forms-users] groep. De leden van de [!DNL forms-users] groep heeft machtigingen om een adaptief formulier te maken.

* De gebruikers met de volgende rollen hebben de toestemmingen om de AEM Moderniseren Hulpmiddelen binnen een AEM milieu te installeren:
   * Ontwikkelingsrol
   * Beheerdersrol

Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

## Installeren en configureren AEM Moderniseringsgereedschappen

Om de AEM Moderniseren Hulpmiddelen te installeren en te vormen:

1. [Installeer AEM Moderniseringsgereedschappen in uw lokale AEM Forms-omgeving](#install-aem-modernize-Tools)
2. [Gereedschappen AEM moderniseren inschakelen voor uw lokale AEM Forms-omgeving](#enable-aem-modernize-Tools)

### Installeer AEM Moderniseringsgereedschappen in uw lokale AEM Forms-omgeving {#install-aem-modernize-Tools}

Voer de volgende stappen uit om AEM Moderniseer Hulpmiddelen aan uw lokale milieu van AEM Forms te installeren:

1. Open de opdrachtprompt of terminal.
1. Start de lokale AEM Auteur Service. Voer bijvoorbeeld de volgende code uit van het begin tot de lokale AEM Auteur-instantie:

   `java -jar aem-author-p4502.jar`

1. Klonen met [Gereedschap AEM moderniseren](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) in uw lokale systeem.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Nadat u de opdracht met succes hebt uitgevoerd, beschikt u over een lokale kopie van de opslagplaats voor het gereedschap AEM moderniseren op uw computer.

1. Ga naar de`[AEM Modernize Tool Repository]`  in uw lokale systeem.
1. Voer de volgende opdracht uit:

   ```Shell
       mvn clean install 
   ```
![Installatieafbeelding gelukt](/help/forms/assets/aem-modernize-install-steps.png)

Nadat de installatie is voltooid, worden de AEM Moderniseringsgereedschappen beschikbaar voor uw omgeving.

![Hulpprogramma AEM migratie inschakelen](/help/forms/assets/enable-aem-modernizer-tools.png)


### Gereedschappen AEM moderniseren inschakelen voor uw lokale AEM Forms-omgeving{#enable-aem-modernize-Tools}

Om de AEM Moderniseren Hulpmiddelen voor uw AEM Milieu toe te laten en te gebruiken, is het belangrijk om de regels voor het migreren van de Componenten van de Stichting aan de Componenten van de Kern in kaart te brengen:

1. Meld u aan bij de auteur.
1. Navigeren naar `http://[host]:[port]/system/console/configMgr`
1. De opdracht Zoeken en bewerken `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Voeg de `Component Rule Paths` als `/apps/forms-modernizer/rules`.
1. Klikken **Opslaan** om de wijzigingen op te slaan

![Componentregel AEM moderniseren](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Het nut van de Omzetting van de Vorm van de looppas om de op componenten gebaseerde vormen van de Stichting in de vorm van de Component van de Kern om te zetten

1. Ga naar **[!UICONTROL Tools > AEM Modernize Tools > Forms Conversion]**.

   ![Gereedschappen AEM moderniseren selecteren](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Selecteer de **[!UICONTROL Forms Conversion]** -optie.

   ![Forms-conversie selecteren, optie](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klikken **Maken** om een nieuwe baan te creëren.

   ![AEM moderniseringsgereedschappen maken taak](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geef de **[!UICONTROL Job Name]**.
1. In de **[!UICONTROL Form]** kunt u een van de volgende opties selecteren:
   * **Geen** : Selecteer de optie als u geen kopie wilt maken van de formulieren op basis van de stichtingscomponent voordat u de formulierconversie start.
   * **Herstellen** : Selecteer de optie om de status van het formulier te herstellen voordat u het formulier converteert.
   * **Kopiëren naar doel**: Selecteer de optie om een kopie te maken van de formulieren op basis van de stichtingscomponent voordat u de formulierconversie start.
In ons geval **Kopiëren naar doel** is geselecteerd. Als de **Kopiëren naar doel** is geselecteerd, wordt de **[!UICONTROL Source Path]** en **[!UICONTROL Target Path]** worden weergegeven.

1. Geef de `source folder` naam in de **[!UICONTROL Source Path]**.
1. Geef de `target folder` naam in de **[!UICONTROL Target Path]**.
1. Selecteren **[!UICONTROL Next]**.
1. Klikken op **[!UICONTROL Add Forms]**. Alle formulieren in het dialoogvenster `source folder` verschijnt op het scherm.
1. Selecteer de adaptieve Forms op basis van Foundation Components om deze om te zetten in op kerncomponenten gebaseerde formulieren. U kunt ook meerdere formulieren selecteren.

   ![Formulier selecteren voor gereedschap AEM moderniseren](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Klik op **[!UICONTROL Select]**.
1. Klikken **[!UICONTROL Schedule Job]** om het conversieproces te starten.
1. Klikken **[!UICONTROL Convert]** van de **[!UICONTROL Convert Pages]** in.

   ![AEM Gereedschappen moderniseren Pagina&#39;s converteren](/help/forms/assets/aem-modernize-tools-convert-form.png)

   Wanneer de status van het proces wordt gewijzigd in `success`. Ga naar de `target folder` om het geconverteerde formulier te bekijken.

   ![Gereedschappen moderniseren AEM geslaagd](/help/forms/assets/aem-modernize-tools-success.png)

1. Selecteer het adaptieve formulier en selecteer > **[!UICONTROL Properties]**. De pagina Formuliereigenschappen wordt geopend.
   ![Doelmap voor gereedschappen AEM moderniseren](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Selecteren **[!UICONTROL Save and Close]** om de eigenschappen van het geconverteerde formulier opnieuw op te slaan.
   ![Hulpprogramma&#39;s moderniseren positieve formuliereigenschappen](/help/forms/assets/aem-modernize-tools-af-properties.png)

U kunt nu zien dat de Adaptieve Vorm die op de Componenten van de Stichting wordt gebouwd in de Adaptieve Vorm omzet die op de Componenten van de Kern wordt gebouwd.

## Aanbevolen procedures {#best-practices}

* Verzeker uw op componenten gebaseerde vormen van de Stichting, gebruik slechts die componenten die een gelijkwaardig hebben [Kernonderdelen](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) beschikbaar. In gevallen waar u de Componenten van de Stichting gebruikt die geen gelijkwaardige Component van de Kern hebben, wordt de Component van de Stichting niet omgezet. Hierdoor werkt het niet correct tijdens het ontwerpen van een formulier
* Zorg ervoor dat de regels om de Componenten van de Stichting aan de Componenten van de Kern te behandelen in XML worden geformatteerd.
