---
title: Hoe kunnen we AEM vertaalworkflow gebruiken om Adaptive Forms en Document of Record te lokaliseren?
description: Leer hoe u AEM vertaalworkflows kunt gebruiken om Adaptive Forms en Document of Record te lokaliseren.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Aangepast Forms en document met record lokaliseren{#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u Adaptive Forms en de bijbehorende documenten van record lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** gebruiken om een AanpassingsVorm te lokaliseren.

In dit artikel wordt uitgelegd hoe u AEM vertaalworkflow kunt gebruiken met Adaptive Forms en recorddocumenten.

## Een adaptief formulier en document met record lokaliseren met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in Adaptief formulier en Document of Record. [!DNL AEM Forms] is vooraf geconfigureerd voor het gebruik van een proefversie van [!DNL Microsoft Translator] voor machinevertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw Adaptieve Forms en Document of Record:

1. Voor [!DNL AEM Forms] UI, selecteer een vorm, en selecteer **voeg Woordenboek** optie toe.
1. In **voeg Woordenboek aan het scherm van het Project van de Vertaling** toe, selecteer **een nieuw vertaalproject** of **voeg aan een bestaand vertaalproject** optie toe.
1. Op het **gebied van de Titel van het Project**, specificeer de titel. Bijvoorbeeld: `Government Reference Site - German locale.`
1. Op het **gebied van de Talen van het Doel**, specificeer een scène (bijvoorbeeld, `German(de)`), en klik **Gedaan**. U kunt meerdere landinstellingen opgeven. De vorm wordt vertaald aan alle scènes die in het **gebied van de Talen van het Doel** worden gespecificeerd.
1. In het Woordenboek toegevoegde dialoogvakje, klik **Open Projecten**. Open het gemaakte project in het scherm Projecten.
1. Klik de **ellipsen** bij de bodem van de **Vertaling Summiere** tegel. Het scherm Translation Summary wordt geopend.
1. Klik **uitgeven** pictogram bij de bovenkant van het **Summiere van de Vertaling** scherm. Open het **Vertaal** lusje en selecteer de Vertaling van de Machine in het **Vertaalmethode** scherm. Selecteer de aangewezen **Vertaalleverancier** en **Configuratie van de Wolk**. Klik het **Gereed** pictogram bij de bovenkant van het scherm.
1. Op de **tegel van de VertaalBaan**, klik ![ aem62forms_downarrow ](assets/aem62forms_downarrow.png) pictogram, en klik **Begin**. De status van de tegel verandert in Concept. Na voltooiing van de vertaling, de statusveranderingen in **Klaar voor overzicht**. Vernieuw de pagina na een paar minuten en controleer de status.
1. Na de statusveranderingen in **Klaar voor overzicht** op de **Taal van de VertaalBaan**, open de vorm in een browser venster. Er wordt een gelokaliseerde versie van het formulier weergegeven.

   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (right to left). Bijvoorbeeld Hebreeuws.

   Het automatisch gegenereerde Document of Record wordt samen met het adaptieve formulier ook gelokaliseerd.

   Zie voor meer informatie over de instellingen en configuratie van Document of Record:

[Document met recordsjabloonconfiguratie](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Document met recordinstellingen](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [ pas de het brandmerken informatie van het Document van Verslag ](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) aan en zorg ervoor dat de browser scène aan de zelfde taal wordt geplaatst waaraan u de Aangepaste Vorm gebruikend machinetaal hebt gelokaliseerd. Met de landinstelling van de browser kunt u de brandinggegevens in het document of Record lokaliseren.
1. Als u het gelokaliseerde document met records wilt weergeven, selecteert u Voorvertoning genereren. Het PDF Document of Record wordt gegenereerd en geopend op een nieuw tabblad in uw browser.

<!-- ## Localizing an Adaptive Form and its Document of Record using Human Translation {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In Human translation the content is sent to a translation provider and translated by professional translators. When complete, the translated content is returned and imported into AEM. When your translation provider is integrated with AEM, content is automatically sent between AEM and the translation provider.

For translation, a dictionary containing files in XLIFF format is shared with the professional translators. The dictionary includes a separate XLIFF file for each locale. Each XLIFF file contains text that is displayed to the end users and placeholders for the corresponding localized text.

Perform the following steps to localize a form and its Document of Record using Human Translators:

1. [Connect AEM with your translation service provider](/help/sites-administering/tc-tic.md) and [create translation integration framework configurations](/help/sites-administering/tc-tic.md).

1. [Associate the pages of your language master](/help/sites-administering/tc-tic.md) with the translation service and framework configurations.

1. [Identify the type of content](/help/sites-administering/tc-rules.md) to translate.

1. [Prepare the content for translation](/help/sites-administering/tc-prep.md) by authoring the language master and creating the root pages of language copies.

1. [Create translation projects](/help/sites-administering/tc-manage.md) to gather the content to translate and to prepare the translation process.

1. Use the translation projects to [manage the content translation process](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Adaptive Form components do not support right to left (RTL) languages. For example, Hebrew.
> -->

