---
title: Hoe kunnen we een op kerncomponenten gebaseerde adaptieve vorm vertalen?
description: Leer om een Model van de Gegevens van de Vorm (FDM) in AEM Forms tot stand te brengen, het model met steekproefgegevens en de diensten te testen, en diverse optie voor een model te vormen.
feature: Adaptive Forms, Core Components
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# Gebruik machinevertaling of menselijke vertaling om een adaptief formulier met kerncomponenten te vertalen {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u Adaptive Forms en de bijbehorende documenten van record lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** gebruiken om een AanpassingsVorm te lokaliseren.

## Een adaptief formulier en een document met records vertalen met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De dienst van de machinevertaling vertaalt onmiddellijk uw inhoud in Aangepaste Vorm en [ Document van Verslag ](/help/forms/generate-document-of-record-core-components.md). AEM Forms as a Cloud Service is vooraf geconfigureerd voor het gebruik van een proefversie van Microsoft Translator voor machinevertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw Adaptieve Forms en Document of Record:

1. Selecteer een formulier in de gebruikersinterface van AEM Forms en selecteer de optie **[!UICONTROL Add Dictionary]** .
1. Kies in het scherm Woordenboek toevoegen aan vertaalproject de optie **[!UICONTROL Project]**

   * Om een vertaalproject tot stand te brengen, selecteer de **[!UICONTROL Create a new translation project]** optie en op het **gebied van de Titel van het Project**, specificeer de titel. Bijvoorbeeld: `Government Reference Site - German locale.`
   * Als u een nieuw woordenboek wilt toevoegen aan een bestaand vertaalproject, selecteert u de optie **[!UICONTROL Add to an existing translation project]** en selecteert u een **[!UICONTROL Existing translation project]** .
1. Op het **gebied van de Talen van het Doel**, specificeer een scène (bijvoorbeeld, `German(de)`). U kunt meerdere landinstellingen opgeven. De vorm wordt vertaald aan alle scènes die in het **gebied van de Talen van het Doel** worden gespecificeerd. Klik **Gedaan**.
1. In het Woordenboek toegevoegde dialoogvakje, klik **Open Projecten**.
1. Klik in het scherm Projecten op het gemaakte project. Bijvoorbeeld, klik de **Plaats van de Verwijzing van de Regering - Duitse scène** tegel.
1. Op de **tegel van de VertaalBaan**, klik ![ aem62forms_downarrow ](assets/aem62forms_downarrow.png) pictogram, en klik **Begin**. De status van de tegel verandert in Concept. Na voltooiing van de vertaling, verandert de status in **Goedgekeurd**. Vernieuw de pagina na een paar minuten en controleer de status.

   ![ Vertaling van het Begin ](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. Na de statusveranderingen in **Goedgekeurd** op de **Taal van de VertaalBaan**, klik ![ aem62forms_downarrow ](assets/aem62forms_downarrow.png) pictogram, en klik **Volledig**.

1. Als u een voorbeeld van het gelokaliseerde formulier wilt bekijken, selecteert u het gelokaliseerde formulier in de gebruikersinterface van AEM Forms. Klik **[!UICONTROL Preview]** > **[!UICONTROL Preview as HTML]**. Open het formulier opnieuw nadat u de `afAcceptLang=<locale code>` aan de URL van het formulier hebt toegevoegd. Voeg bijvoorbeeld `afAcceptLang=de` toe om de Duitse versie van het formulier te openen.


   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.

<!-- 
   Along with the Adaptive form, the auto-generated document of record is also localized.

   For more information on Document of Record settings and configuration, see:

   [Document of Record Template](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document of Record settings](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Customize the branding information of the document of record](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) and ensure that the browser locale is set to the same language to which you have localized the Adaptive Form using machine language. The browser locale helps localize the branding information in the document of record.
1. To view the localized document of record, select Generate Preview. The document of record PDF is generated and opened in a new tab in your browser.

-->

## Een adaptief formulier en het bijbehorende document lokaliseren met behulp van menselijke vertaling {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In menselijke vertaling wordt de inhoud naar een vertaalbureau gestuurd en vertaald door professionele vertalers. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt de inhoud automatisch verzonden tussen AEM en de vertaalprovider.

Voor vertaling wordt een woordenboek met bestanden in XLIFF-indeling gedeeld met de professionele vertalers. Het woordenboek bevat een apart XLIFF-bestand voor elke landinstelling. Elk XLIFF-bestand bevat tekst die aan de eindgebruikers en plaatsaanduidingen voor de bijbehorende gelokaliseerde tekst wordt weergegeven.

Voer de volgende stappen uit om een formulier en het bijbehorende document te lokaliseren met behulp van Human Translators:

1. Selecteer een formulier in de gebruikersinterface van AEM Forms en selecteer de optie **[!UICONTROL Add Dictionary]** .
1. Kies in het scherm Woordenboek toevoegen aan vertaalproject de optie **[!UICONTROL Project]**

   * Om een vertaalproject tot stand te brengen, selecteer de **[!UICONTROL Create a new translation project]** optie en op het **gebied van de Titel van het Project**, specificeer de titel. Bijvoorbeeld: `Government Reference Site - German locale.`
   * Als u een nieuw woordenboek wilt toevoegen aan een bestaand vertaalproject, selecteert u de optie **[!UICONTROL Add to an existing translation project]** en selecteert u een **[!UICONTROL Existing translation project]** .
1. Op het **gebied van de Talen van het Doel**, specificeer een scène (bijvoorbeeld, `German(de)`). U kunt meerdere landinstellingen opgeven. De vorm wordt vertaald aan alle scènes die in het **gebied van de Talen van het Doel** worden gespecificeerd. Klik **Gedaan**.
1. In het Woordenboek toegevoegde dialoogvakje, klik **Open Projecten**.
1. Klik in het scherm Projecten op het gemaakte project. Bijvoorbeeld, klik de **Plaats van de Verwijzing van de Regering - Duitse scène** tegel.
1. Bij de bodem van de **Summiere** tegel, klik de **ellipsen**. Het scherm Projecteigenschappen omzetten wordt geopend.
1. Open het **[!UICONTROL Advanced]** lusje bij de bovenkant van het **scherm van de Eigenschappen van het Project van de Vertaling**. Selecteer **[!UICONTROL Human Translation]** voor **[!UICONTROL Translation field]** . Klik **sparen &amp; dicht** bij de bovenkant van het scherm.
1. Op de **tegel van de VertaalBaan**, klik ![ aem62forms_downarrow ](assets/aem62forms_downarrow.png) pictogram, en klik **Uitvoer**. Klik in het dialoogvenster Exporteren op de optie Geëxporteerd bestand downloaden. Er wordt een ZIP-bestand gedownload.
   ![ de vertaaldossier van de Uitvoer ](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. Extraheer het gedownloade .zip-bestand. De geëxtraheerde map heeft twee bestanden:
   * transleren_export_summary.xml
   * [ vorm-gebieden-dossier ].xml.
1. Open [ vorm-gebieden-dossier ] .xml voor het uitgeven. Voeg de gelokaliseerde tekenreeksen en berichten voor formuliervelden toe. Sla het bestand op en sluit het.
1. Zip de dossiers translate_export_summary.xml en [ vorm-gebieden-dossier ] .xml.
1. Op de **tegel van de VertaalBaan**, klik ![ aem62forms_downarrow ](assets/aem62forms_downarrow.png) pictogram, en klik **de Invoer**. Selecteer het archief dat [ vorm-gebieden-dossier ].xml bevat. met gelokaliseerde tekenreeksen en berichten voor formuliervelden.

   ![ de vertaaldossier van de Invoer ](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. Als u een voorbeeld van het gelokaliseerde formulier wilt bekijken, selecteert u het gelokaliseerde formulier in de gebruikersinterface van AEM Forms. Klik **[!UICONTROL Preview]** > **[!UICONTROL Preview as HTML]**. Open het formulier opnieuw nadat u de `afAcceptLang=<locale code>` aan de URL van het formulier hebt toegevoegd. Voeg bijvoorbeeld `afAcceptLang=de` toe om de Duitse versie van het formulier te openen.

## Zie ook {#see-also}

{{see-also}}