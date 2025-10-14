---
title: Hulpprogramma voor migratie/AEM Moderniseert tools voor het converteren van adaptieve Forms op basis van Foundation Components naar Core Component-formulieren
description: Leer om Hulpmiddelen van het Hulpprogramma van de Modernisering van de Migratie te installeren en te gebruiken van het Hulpprogramma van de Migratie/AEM om AanpassingsForms om te zetten die op de Componenten van de Stichting wordt gebaseerd aan de vormen van de Component van de Kern.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
exl-id: ee71a576-96a7-4c81-b3a3-1d678f010cba
feature: Adaptive Forms, Core Components
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 0%

---

# Inleiding

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Het Nut van de Omzetting van Forms, een deel van de [&#x200B; AEM Moderniseer Hulpmiddel &#x200B;](https://opensource.adobe.com/aem-modernize-tools/) reeks, helpt u Aanpassings Forms gemakkelijk omzetten die met de componenten van de erfenisStichting aan vormen wordt gebouwd die hefboomwerking de moderne, gesteunde mogelijkheden van de Componenten van de Kern.

## Wat zijn de moderniseringsgereedschappen van AEM?

[&#x200B; AEM Moderniseert Hulpmiddelen &#x200B;](https://opensource.adobe.com/aem-modernize-tools/) verwijst naar een reeks nut of softwaretoepassingen die worden ontworpen om het proces te vergemakkelijken om de projecten van Adobe Experience Manager (AEM) te moderniseren of bij te werken. Met deze gereedschappen kunt u doorgaans oudere componenten of functies in AEM converteren naar nieuwere, efficiëntere en ondersteunde alternatieven. Het Forms Conversion-hulpprogramma is geïnstalleerd onder de Moderniseringsprogramma&#39;s van AEM om Adaptive Forms op basis van Foundation Components om te zetten in op Core Component gebaseerde formulieren.

Het Forms Conversion-hulpprogramma zet Adaptive Forms die is gebaseerd op oudere Foundation Components om in nieuwere op Core Component gebaseerde formulieren. Dit conversieproces zorgt ervoor dat de formulieren zijn afgestemd op moderne standaarden en mogelijkheden, waardoor de prestaties, compatibiliteit en het onderhoudsgemak in de AEM-omgeving kunnen worden verbeterd.

![&#x200B; AEM moderniseert Hulpmiddelen &#x200B;](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
>U wordt aangeraden de AEM Modernize Tools te installeren op uw lokale AEM-installatie. Migreer de adaptieve Forms op basis van Foundation Components naar Core Component-formulieren. Download het formulier samen met de bijbehorende middelen. Vervolgens uploadt u het formulier en de bijbehorende elementen naar de vereiste omgeving.

## Overwegingen bij het gebruik van de AEM Modernize Tools {#considerations}

* Bij geslaagde conversies worden alle regels verwijderd die op het formulier worden toegepast. Regels worden niet automatisch gemigreerd. U moet deze regels handmatig opnieuw maken en toepassen op het geconverteerde formulier.
* De vertaalinstellingen die in het oorspronkelijke formulier worden gebruikt, worden niet overgenomen. Vertaling voor het geconverteerde formulier opnieuw configureren.
* Als de vorm die op de Componenten van de Stichting wordt gebouwd manuscripten of de regels van de douanefunctie bevat, moet u deze voor het omgezette vorm herschrijven die op de Componenten van de Kern wordt gebaseerd.
* De volgende OOTB-basiscomponenten worden nog niet ondersteund in Core Components (Basiscomponenten) en worden daarom verwijderd in het geconverteerde formulier:

   * Adobe Sign Block
   * Diagram
   * Lijst met bestandsbijlagen
   * Plaatsaanduiding voetnoot
   * Afbeeldingskeuze
   * Volgende knop
   * Vorige knop
   * Krabbelhandtekening
   * Samenvattingsstap
   * Werkbalk

## Voorwaarden voor het gebruik van de Moderniseringsgereedschappen van AEM

* [&#x200B; opstelling lokale ontwikkelomgeving voor AEM Forms &#x200B;](/help/forms/setup-local-development-environment.md).
* Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.
* Voeg uw gebruikers toe aan de groep [!DNL forms-users] . De leden van de groep [!DNL forms-users] hebben machtigingen om een adaptief formulier te maken.
* Gebruikers met de volgende rollen hebben de machtigingen om de AEM Modernize Tools in een AEM-omgeving te installeren:

   * Ontwikkelingsrol
   * Beheerdersrol

Voor een gedetailleerde lijst van vorm-specifieke gebruikersgroepen, zie [&#x200B; Groepen en toestemmingen &#x200B;](forms-groups-privileges-tasks.md).

## AEM-moderniseringsgereedschappen installeren en configureren

U installeert en configureert als volgt de moderniseringsgereedschappen voor AEM:

1. [Installeer de Moderniseringsgereedschappen van AEM in uw lokale AEM Forms-omgeving](#install-aem-modernize-Tools)
1. [AEM-tools voor modernisering inschakelen voor uw lokale AEM Forms-omgeving](#enable-aem-modernize-Tools)

### Installeer de Moderniseringsgereedschappen van AEM in uw lokale AEM Forms-omgeving {#install-aem-modernize-Tools}

Voer de volgende stappen uit om AEM Modernize Tools in uw lokale AEM Forms-omgeving te installeren:

1. Open de opdrachtprompt of terminal.
1. Start de lokale AEM Author Service. Voer bijvoorbeeld de volgende code uit van het begin naar het begin van de lokale AEM Author-instantie:

   `java -jar aem-author-p4502.jar`

1. Kloon de [&#x200B; AEM Modernize Hulpmiddel &#x200B;](https://github.com/adobe/forms-modernizer) bewaarplaats in uw lokaal systeem.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Nadat u de opdracht met succes hebt uitgevoerd, beschikt u over een lokale kopie van de gegevensopslagruimte van het AEM Modernize Tool op uw computer.

1. Navigeer aan `[AEM Modernize Tool Repository]` in uw lokaal systeem.
1. Voer de volgende opdracht uit:

   ```Shell
       mvn clean install 
   ```

![&#x200B; Succesvol installatiekopie &#x200B;](/help/forms/assets/aem-modernize-install-steps.png)

Nadat de installatie is voltooid, worden de Moderniseringsgereedschappen van AEM beschikbaar voor uw omgeving.

![&#x200B; laat het Hulpmiddel van het Nut van de Migratie van AEM &#x200B;](/help/forms/assets/enable-aem-modernizer-tools.png) toe


### AEM-tools voor modernisering inschakelen voor uw lokale AEM Forms-omgeving{#enable-aem-modernize-Tools}

Om AEM toe te laten en te gebruiken moderniseert Hulpmiddelen voor uw Milieu van AEM, is het belangrijk om de regels voor het migreren van de Componenten van de Stichting aan de Componenten van de Kern in kaart te brengen:

1. Meld u aan bij de auteur.
1. Navigeren naar `http://[host]:[port]/system/console/configMgr`
1. Zoek en bewerk de `AEM Modernize Tools - Component Rewrite Rule Service` .
1. Voeg de lus `Component Rule Paths` as `/apps/forms-modernizer/rules` toe.
1. Klik **sparen** om de veranderingen te bewaren.

![&#x200B; AEM moderniseert de Regel van de Component &#x200B;](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Voer het hulpprogramma Formulierconversie uit om formulieren op basis van Foundation Components om te zetten in formulieren op basis van Core Component

1. Ga naar **[!UICONTROL Tools > AEM Modernize Tools > Forms Conversion]** .

   ![&#x200B; Uitgezochte AEM Moderniseren Hulpmiddelen &#x200B;](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Selecteer de optie **[!UICONTROL Forms Conversion]** .

   ![&#x200B; Uitgezochte de optie van de Omzetting van Forms &#x200B;](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klik **creëren** om een nieuwe baan tot stand te brengen.

   ![&#x200B; AEM moderniseert Hulpmiddelen creëren Baan &#x200B;](/help/forms/assets/aem-modernize-tools-create-job.png)

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

   ![&#x200B; AEM moderniseert de Hulpmiddelen selecteren Vorm &#x200B;](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Klik op **[!UICONTROL Select]**.
1. Klik op **[!UICONTROL Schedule Job]** om het conversieproces te starten.
1. Klik op **[!UICONTROL Convert]** in het dialoogvenster **[!UICONTROL Convert Pages]** .

   ![&#x200B; AEM Moderniseert Hulpmiddelen zet Pagina&#39;s &#x200B;](/help/forms/assets/aem-modernize-tools-convert-form.png) om

   Wanneer de status van het proces wordt gewijzigd in `success` . Navigeer naar de `target folder` om het geconverteerde formulier te zien.

   ![&#x200B; AEM moderniseert het Succes van Hulpmiddelen &#x200B;](/help/forms/assets/aem-modernize-tools-success.png)

1. Selecteer het adaptieve formulier en selecteer > **[!UICONTROL Properties]** . De pagina Formuliereigenschappen wordt geopend.

   ![&#x200B; de Moderniseren Omslag van de Bestemming van Hulpmiddelen van AEM &#x200B;](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Selecteer **[!UICONTROL Save and Close]** om de eigenschappen van het geconverteerde formulier opnieuw op te slaan.
   ![&#x200B; AEM moderniseert Hulpmiddelen Adpatieve Eigenschappen van de Vorm &#x200B;](/help/forms/assets/aem-modernize-tools-af-properties.png)

U kunt nu zien dat de Adaptieve Vorm die op de Componenten van de Stichting wordt gebouwd in de Adaptieve Vorm omzet die op de Componenten van de Kern wordt gebouwd.

## Aanbevolen procedures {#best-practices}

* Verzeker uw op componenten gebaseerde vormen van de Stichting, gebruik slechts die componenten die een gelijkwaardige [&#x200B; beschikbare Componenten van de Kern hebben 0&rbrace;. &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) In gevallen waar u de Componenten van de Stichting gebruikt die geen gelijkwaardige Component van de Kern hebben, wordt de Component van de Stichting niet omgezet. Hierdoor werkt het niet correct tijdens het ontwerpen van een formulier
* Zorg ervoor dat de regels om de Componenten van de Stichting aan de Componenten van de Kern te behandelen in XML worden geformatteerd.
