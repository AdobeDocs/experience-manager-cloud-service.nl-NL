---
title: Hoe kunnen we AEM vertaalworkflow gebruiken om Adaptive Forms en Document of Record te lokaliseren?
description: Leer hoe u AEM vertaalworkflows kunt gebruiken om Adaptive Forms en Document of Record te lokaliseren.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---


# Aangepast Forms en document met record lokaliseren{#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u Adaptive Forms en de bijbehorende documenten van record lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** om een adaptief formulier te lokaliseren.

In dit artikel wordt uitgelegd hoe u AEM vertaalworkflow kunt gebruiken met Adaptive Forms en recorddocumenten.

## Een adaptief formulier en document met record lokaliseren met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in Adaptief formulier en Document of Record. [!DNL AEM Forms] is vooraf geconfigureerd voor het gebruik van een proefversie van [!DNL Microsoft Translator] voor automatische vertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw Adaptieve Forms en Document of Record:

1. Op de [!DNL AEM Forms] UI, selecteert u een formulier en tikt u op **Woordenboek toevoegen** -optie.
1. In **Woordenboek toevoegen aan vertaalproject** scherm, selecteert u de **Een nieuw vertaalproject maken** of **Toevoegen aan een bestaand vertaalproject** -optie.
1. In de **Projecttitel** -veld, geeft u de titel op. Bijvoorbeeld, `Government Reference Site - German locale.`
1. In de **Doeltalen** veld, geef een landinstelling op (bijvoorbeeld `German(de)`) en klik op **Gereed**. U kunt meerdere landinstellingen opgeven. Het formulier wordt vertaald naar alle landinstellingen die in het dialoogvenster **Doeltalen** veld.
1. Klik in het dialoogvenster Woordenboek toegevoegd op **Projecten openen**. Open het nieuwe project in het scherm Projecten.
1. Klik op de knop **ovalen** onder aan het dialoogvenster **Omzettingsoverzicht** tegel. Het scherm Translation Summary wordt geopend.
1. Klik op de knop **Bewerken** pictogram boven aan **Omzettingsoverzicht** scherm. Open de **Vertaling** en selecteert u Machine Translation in het dialoogvenster **Omzettingsmethode** scherm. Selecteer de juiste **Vertaalbureau** en **Cloud Configuration**. Klik op de knop **Gereed** aan de bovenkant van het scherm.
1. Op de **Vertaaltaak** tegel, klik op de knop ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Start**. De status van de tegel verandert in Concept. Na de vertaling verandert de status in **Gereed voor revisie**. Vernieuw de pagina na een paar minuten en controleer de status.
1. Nadat de status is gewijzigd in **Gereed voor revisie** op de **Vertaaltaak** Open het formulier in een browservenster. Er wordt een gelokaliseerde versie van het formulier weergegeven.

   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (right to left). Bijvoorbeeld Hebreeuws.

   Het automatisch gegenereerde Document of Record wordt samen met het adaptieve formulier ook gelokaliseerd.

   Zie voor meer informatie over de instellingen en configuratie van Document of Record:

[Document met recordsjabloonconfiguratie](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Document met recordinstellingen](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [De brandinggegevens van het document of Record aanpassen](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) en zorg ervoor dat de landinstelling van de browser wordt ingesteld op de taal waarin u het Adaptief formulier hebt gelokaliseerd met de computertaal. Met de landinstelling van de browser kunt u de brandinggegevens in het document of Record lokaliseren.
1. Tik op Voorvertoning genereren om het gelokaliseerde document met records weer te geven. Het PDF Document of Record wordt gegenereerd en geopend op een nieuw tabblad in uw browser.

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

