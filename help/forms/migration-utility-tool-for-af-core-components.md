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
source-git-commit: c52d649e569ef427e70c85a88fa0f48fcc534e9e
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Inleiding

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Het Nut van de Omzetting van Forms, deel van de [ AEM 1} reeks van het Hulpmiddel van de Modernisering, helpt u Aanpassings Forms gemakkelijk omzetten die met erfenisComponenten van de Stichting aan vormen wordt gebouwd die hefboomwerking de moderne, gesteunde mogelijkheden van de Componenten van de Kern.](https://opensource.adobe.com/aem-modernize-tools/)

## Wat is AEM moderniseringsgereedschappen?

[ AEM Moderniseer Hulpmiddelen ](https://opensource.adobe.com/aem-modernize-tools/) verwijst naar een reeks nut of softwaretoepassingen die worden ontworpen om het proces te vergemakkelijken om de projecten van Adobe Experience Manager (AEM) te moderniseren of bij te werken. Deze hulpmiddelen helpen typisch bij het omzetten van oudere componenten of functionaliteit binnen AEM in nieuwere, efficiëntere, en gesteunde alternatieven. Het Forms Conversion-hulpprogramma is geïnstalleerd onder AEM Moderniseringsgereedschappen voor het omzetten van adaptieve Forms op basis van Foundation Components in op Core Component gebaseerde formulieren.

Het Forms Conversion-hulpprogramma zet Adaptive Forms die is gebaseerd op oudere Foundation Components om in nieuwere op Core Component gebaseerde formulieren. Dit conversieproces zorgt ervoor dat de formulieren zijn afgestemd op moderne standaarden en mogelijkheden, waardoor de prestaties, compatibiliteit en het onderhoudsgemak binnen de AEM kunnen worden verbeterd.

![ AEM Moderniseren Hulpmiddelen ](/help/forms/assets/aem-modernize-tools.png)

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

* Voeg uw gebruikers toe aan de groep [!DNL forms-users] . De leden van de groep [!DNL forms-users] hebben machtigingen om een adaptief formulier te maken.

* De gebruikers met de volgende rollen hebben de toestemmingen om de AEM Moderniseren Hulpmiddelen binnen een AEM milieu te installeren:
   * Ontwikkelingsrol
   * Beheerdersrol

Voor een gedetailleerde lijst van vorm-specifieke gebruikersgroepen, zie [ Groepen en toestemmingen ](forms-groups-privileges-tasks.md).

## Installeren en configureren AEM Moderniseringsgereedschappen

Om de AEM Moderniseren Hulpmiddelen te installeren en te vormen:

1. [Installeer AEM Moderniseringsgereedschappen in uw lokale AEM Forms-omgeving](#install-aem-modernize-Tools)
2. [Gereedschappen AEM moderniseren inschakelen voor uw lokale AEM Forms-omgeving](#enable-aem-modernize-Tools)

### Installeer AEM Moderniseringsgereedschappen in uw lokale AEM Forms-omgeving {#install-aem-modernize-Tools}

Voer de volgende stappen uit om AEM Moderniseer Hulpmiddelen aan uw lokale milieu van AEM Forms te installeren:

1. Open de opdrachtprompt of terminal.
1. Start de lokale AEM Auteur Service. Voer bijvoorbeeld de volgende code uit van het begin tot de lokale AEM Auteur-instantie:

   `java -jar aem-author-p4502.jar`

1. Kloon de [ AEM Moderniseer Hulpmiddel ](/help/journey-migration/refactoring-tools/aem-modernization-tools.md) bewaarplaats in uw lokaal systeem.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Nadat u de opdracht met succes hebt uitgevoerd, beschikt u over een lokale kopie van de opslagplaats voor het gereedschap AEM moderniseren op uw computer.

1. Navigeer aan `[AEM Modernize Tool Repository]` in uw lokaal systeem.
1. Voer de volgende opdracht uit:

   ```Shell
       mvn clean install 
   ```
![ Succesvol installatiekopie ](/help/forms/assets/aem-modernize-install-steps.png)

Nadat de installatie is voltooid, worden de AEM Moderniseringsgereedschappen beschikbaar voor uw omgeving.

![ laat AEM Hulpmiddel van het Nut van de Migratie ](/help/forms/assets/enable-aem-modernizer-tools.png) toe


### Gereedschappen AEM moderniseren inschakelen voor uw lokale AEM Forms-omgeving{#enable-aem-modernize-Tools}

Om de AEM Moderniseren Hulpmiddelen voor uw AEM Milieu toe te laten en te gebruiken, is het belangrijk om de regels voor het migreren van de Componenten van de Stichting aan de Componenten van de Kern in kaart te brengen:

1. Meld u aan bij de auteur.
1. Navigeren naar `http://[host]:[port]/system/console/configMgr`
1. Zoek en bewerk de `AEM Modernize Tools - Component Rewrite Rule Service` .
1. Voeg de lus `Component Rule Paths` as `/apps/forms-modernizer/rules` toe.
1. Klik **sparen** om de veranderingen te bewaren.

![ AEM Moderniseer de Regel van de Component ](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Voer het hulpprogramma Formulierconversie uit om formulieren op basis van Foundation Components om te zetten in formulieren op basis van Core Component

1. Ga naar **[!UICONTROL Tools > AEM Modernize Tools > Forms Conversion]** .

   ![ Uitgezochte AEM Moderniseren Hulpmiddelen ](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Selecteer de optie **[!UICONTROL Forms Conversion]** .

   ![ Uitgezochte de optie van de Omzetting van Forms ](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klik **creëren** om een nieuwe baan tot stand te brengen.

   ![ AEM Moderniseer Hulpmiddelen creëren Baan ](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geef de waarde **[!UICONTROL Job Name]** op.
1. Op het tabblad **[!UICONTROL Form]** kunt u een van de volgende opties selecteren:
   * **niets**: Selecteer de optie als u geen exemplaar van de op componenten gebaseerde vormen van de Stichting wilt tot stand brengen alvorens de vormomzetting te beginnen.
   * **herstelt**: Selecteer de optie om de vorm aan de staat te herstellen het was alvorens de vormomzetting te beginnen.
   * **Exemplaar aan Doel**: Selecteer de optie om een exemplaar van de op componenten gebaseerde vormen van de Stichting tot stand te brengen alvorens de vormomzetting te beginnen.
In ons geval, wordt het **Exemplaar aan de optie van het Doel** geselecteerd. Als het **Exemplaar aan Doel** optie wordt geselecteerd, worden de **[!UICONTROL Source Path]** en **[!UICONTROL Target Path]** opties zichtbaar.

1. Geef de naam `source folder` op in de map **[!UICONTROL Source Path]** .
1. Geef de naam `target folder` op in de map **[!UICONTROL Target Path]** .
1. Selecteer **[!UICONTROL Next]** .
1. Klik op **[!UICONTROL Add Forms]** . Alle formulieren in de `source folder` worden op het scherm weergegeven.
1. Selecteer de adaptieve Forms op basis van Foundation Components om deze om te zetten in op kerncomponenten gebaseerde formulieren. U kunt ook meerdere formulieren selecteren.

   ![ AEM de Moderniseren Hulpmiddelen selecteren Vorm ](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Klik op **[!UICONTROL Select]**.
1. Klik op **[!UICONTROL Schedule Job]** om het conversieproces te starten.
1. Klik op **[!UICONTROL Convert]** in het dialoogvenster **[!UICONTROL Convert Pages]** .

   ![ AEM Moderniseer Hulpmiddelen zetten Pagina&#39;s ](/help/forms/assets/aem-modernize-tools-convert-form.png) om

   Wanneer de status van het proces wordt gewijzigd in `success` . Navigeer naar de `target folder` om het geconverteerde formulier te zien.

   ![ AEM het Succes van Hulpmiddelen moderniseren ](/help/forms/assets/aem-modernize-tools-success.png)

1. Selecteer het adaptieve formulier en selecteer > **[!UICONTROL Properties]** . De pagina Formuliereigenschappen wordt geopend.
   ![ AEM de Omslag van de Bestemming van Hulpmiddelen moderniseren ](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Selecteer **[!UICONTROL Save and Close]** om de eigenschappen van het geconverteerde formulier opnieuw op te slaan.
   ![ AEM de Hulpmiddelen Adverterende Eigenschappen van de Vorm ](/help/forms/assets/aem-modernize-tools-af-properties.png) moderniseren

U kunt nu zien dat de Adaptieve Vorm die op de Componenten van de Stichting wordt gebouwd in de Adaptieve Vorm omzet die op de Componenten van de Kern wordt gebouwd.

## Aanbevolen procedures {#best-practices}

* Verzeker uw op componenten gebaseerde vormen van de Stichting, gebruik slechts die componenten die een gelijkwaardige ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) beschikbare Componenten van de Kern hebben 0}. [ In gevallen waar u de Componenten van de Stichting gebruikt die geen gelijkwaardige Component van de Kern hebben, wordt de Component van de Stichting niet omgezet. Hierdoor werkt het niet correct tijdens het ontwerpen van een formulier
* Zorg ervoor dat de regels om de Componenten van de Stichting aan de Componenten van de Kern te behandelen in XML worden geformatteerd.
