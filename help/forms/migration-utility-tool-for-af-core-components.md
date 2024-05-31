---
title: Migratiehulpprogramma voor het converteren van adaptieve Forms op basis van basiscomponenten naar basiscomponentformulieren
description: Leer om het Nut van de Migratie te installeren en te gebruiken om Adaptive Forms die op de componenten van de Stichting wordt gebaseerd in kerncomponentengebaseerde vormen om te zetten.
Keywords: Migration Utility tool, Convert Adaptive Forms based on foundation components to core component based forms, Convert Foundation forms to Core components forms, Using Modernizer tool to convert Foundation Components to Core components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---


# Inleiding

U kunt het migratiehulpprogramma gebruiken om adaptieve Forms op basis van stichtingscomponenten om te zetten in kerncomponentformulieren. U kunt de [Gereedschap AEM moderniseren](https://opensource.adobe.com/aem-modernize-tools/) als migratiehulpprogramma. De [Gereedschappen AEM moderniseren](https://opensource.adobe.com/aem-modernize-tools/) bieden een reeks hulpprogramma&#39;s die worden gebruikt voor de conversie van Adaptive Forms op basis van basiscomponenten naar de moderne en ondersteunde mogelijkheden van kerncomponenten.

## Wat is AEM moderniseringsgereedschappen?

[Gereedschappen AEM moderniseren](https://opensource.adobe.com/aem-modernize-tools/) verwijst naar een reeks hulpprogramma&#39;s of softwaretoepassingen die zijn ontworpen om het proces van modernisering of actualisering van Adobe Experience Manager-projecten (AEM) te vergemakkelijken. Deze hulpmiddelen helpen typisch bij het omzetten van oudere componenten of functionaliteit binnen AEM in nieuwere, efficiëntere, en gesteunde alternatieven.

AEM Moderniseringsgereedschappen converteert Adaptief Forms dat is gebaseerd op oudere basiscomponenten naar nieuwere, op componenten gebaseerde basisformulieren. Dit conversieproces zorgt ervoor dat de formulieren zijn afgestemd op moderne standaarden en mogelijkheden, waardoor de prestaties, compatibiliteit en het onderhoudsgemak binnen de AEM kunnen worden verbeterd.

![Gereedschappen AEM moderniseren](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> U wordt aangeraden de AEM Moderniseren Tools op uw lokale AEM te installeren. Migreer de op stichting-gebaseerde vormen aan kern op component-gebaseerde vormen. Download het formulier samen met de bijbehorende middelen. Vervolgens uploadt u het formulier en de bijbehorende elementen naar de vereiste omgeving.

## Voorwaarden voor het gebruik AEM Moderniseren van gereedschappen

* [Lokale ontwikkelomgeving instellen voor AEM Forms](/help/forms/setup-local-development-environment.md)
* [Aangepaste Forms-kerncomponenten voor uw omgeving inschakelen.](/help/forms/enable-adaptive-forms-core-components.md)

* Voeg uw gebruikers aan toe [!DNL forms-users] groep. De leden van de [!DNL forms-users] groep heeft machtigingen om een adaptief formulier te maken.

* De gebruikers met de volgende rollen hebben de toestemmingen om de AEM Moderniseren Hulpmiddelen binnen een AEM milieu te installeren:
   * Ontwikkelingsrol
   * Beheerdersrol Voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen raadpleegt u [Groepen en machtigingen](forms-groups-privileges-tasks.md).

## Installeren en configureren AEM Moderniseringsgereedschappen

Stappen om te installeren en te vormen AEM de Hulpmiddelen van de Modernisering:

1. [Installeer AEM Moderniseringsgereedschappen in uw lokale AEM Forms-omgeving](#install-aem-modernize-tools)
2. [Gereedschappen AEM moderniseren inschakelen voor uw lokale AEM Forms-omgeving](#enable-aem-modernize-tools)

### Installeer AEM Moderniseringsgereedschappen in uw lokale AEM Forms-omgeving {#install-aem-modernize-tools}

Voer de volgende stappen uit om AEM Moderniseer Hulpmiddelen aan uw lokale milieu van AEM Forms te installeren:

1. Start de lokale AEM Auteur Service door het volgende uit te voeren vanaf de opdrachtregel:

   `java -jar aem-author-p4502.jar`

   >[!NOTE]
   >
   > Geef het beheerderswachtwoord op als `admin`. Om het even welk admin wachtwoord is aanvaardbaar, nochtans adviseert het gebruiken van het gebrek voor lokale ontwikkeling om de behoefte te verminderen om opnieuw te vormen.

1. Klonen met [Gereedschappen AEM moderniseren](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) in uw lokale systeem.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tools]
   ```
   Vervang de [Het pad van de Git-opslagplaats van AEM Moderniseringsgereedschappen] met de werkelijke URL van de overeenkomstige Git Repository van de AEM Moderniseren Hulpmiddelen.
Nadat de opdracht met succes is uitgevoerd, beschikt u over een lokale kopie van de AEM opslagplaats voor moderniseringsgereedschappen die beschikbaar is op uw computer.

1. Ga naar de`[AEM Modernize Tools Repository]`  in uw lokale systeem.
1. Voer de volgende opdracht uit:

   ```Shell
       mvn clean install 
   ```
![Installatieafbeelding gelukt](/help/forms/assets/aem-modernize-install-steps.png)

Na succesvolle installatie, AEM de Moderniseren Hulpmiddelen beschikbaar voor uw milieu.

![Gereedschappen AEM moderniseren inschakelen](/help/forms/assets/enable-aem-modernizer-tools.png)


### Gereedschappen AEM moderniseren inschakelen voor uw lokale AEM Forms-omgeving{#enable-aem-modernize-tools}

Om de AEM Moderniseren Hulpmiddelen voor uw AEM Milieu toe te laten en te gebruiken, is het belangrijk om de regels voor het migreren van stichtingscomponenten aan kerncomponenten in kaart te brengen:

1. Meld u aan bij de auteur.
1. Navigeren naar `http://[host]:[port]/system/console/configMgr`
1. De opdracht Zoeken en bewerken `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Voeg de `Component Rule Paths` als `/apps/forms-modernizer/rules`.
1. Klikken **Opslaan** om de wijzigingen op te slaan

![Componentregel AEM moderniseren](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Voer AEM Moderniseringsgereedschappen uit om basiscomponenten te converteren naar basiscomponentformulieren

1. Ga naar **[!UICONTROL Tools > AEM Modernize Tools > Forms Conversion]**.

   ![Gereedschappen voor AEM moderniseren selecteren](/help/forms/assets/aem-modernize-tools-select.png)

1. Selecteer de **[!UICONTROL Forms Conversion]** -optie.

   ![Forms-conversie selecteren, optie](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Klikken **Maken** om een nieuwe baan te creëren.

   ![AEM moderniseringsgereedschappen maken taak](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Geef de **[!UICONTROL Job Name]**.
1. In de **[!UICONTROL Form]** kunt u een van de volgende opties selecteren:
   * **Geen** : Selecteer deze optie als formulierverwerking niet is vereist.
   * **Herstellen** : Selecteer deze optie als u het formulier wilt terugzetten naar de status vóór de laatste conversie.
   * **Kopiëren naar doel**: Selecteer deze optie als u het formulier wilt kopiëren voordat u de conversie uitvoert.
In ons geval **Kopiëren naar doel** is geselecteerd. Als de **Kopiëren naar doel** is geselecteerd, wordt de **[!UICONTROL Source Path]** en **[!UICONTROL Target Path]** worden weergegeven.

1. Geef de `source folder` naam in de **[!UICONTROL Source Path]**.
1. Geef de `target folder` naam in de **[!UICONTROL Target Path]**.
1. Selecteren **[!UICONTROL Next]**.
1. Klikken op **[!UICONTROL Add Forms]**. Alle formulieren in het dialoogvenster `source folder` verschijnt op het scherm.
1. Selecteer het formulier op basis van basiscomponenten om het te converteren naar een formulier op basis van basiscomponenten. U kunt ook meerdere formulieren selecteren.

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

U ziet nu dat het adaptieve formulier dat is gebaseerd op basiscomponenten, wordt getransformeerd naar het adaptieve formulier dat is gebaseerd op basiscomponenten.

## Overwegingen bij het gebruik van het migratiehulpprogramma {#considerations}

* Als het formulier dat is gebaseerd op basiscomponenten aangepaste functieregels bevat, moet u deze regels voor het geconverteerde formulier herschrijven op basis van kerncomponenten.
* Het omgezette formulier bevat geen regels in de regeleditor, waardoor de regels voor het omgezette formulier moeten worden herschreven.
* U moet de vertaaltaak opnieuw maken voor het geconverteerde formulier.

## Aanbevolen procedures {#best-practices}

* Het formulier dat is gebaseerd op basiscomponenten, bevat alleen de componenten die zijn gevonden in de op kerncomponenten gebaseerde componenten.
* Controleer of de regels zijn opgemaakt in XML.


