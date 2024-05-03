---
title: Hoe kunnen we een op kerncomponenten gebaseerde adaptieve vorm vertalen?
description: Leer om een Model van de Gegevens van de Vorm (FDM) in AEM Forms tot stand te brengen, het model met steekproefgegevens en de diensten te testen, en diverse optie voor een model te vormen.
feature: Adaptive Forms, Core Components
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# Gebruik machinevertaling of menselijke vertaling om een adaptief formulier met kerncomponenten te vertalen {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u Adaptive Forms en de bijbehorende documenten van record lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** om een adaptief formulier te lokaliseren.

## Een adaptief formulier en een document met records vertalen met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in Adaptief formulier en [Document van record](/help/forms/generate-document-of-record-core-components.md). AEM Forms as a Cloud Service is vooraf geconfigureerd voor het gebruik van een proefversie van Microsoft Translator voor machinevertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw Adaptieve Forms en Document of Record:

1. Selecteer in de gebruikersinterface van AEM Forms een formulier en selecteer de **[!UICONTROL Add Dictionary]** -optie.
1. In Add Woordenboek aan het scherm van het Project van de Vertaling, voor **[!UICONTROL Project]** option

   * Als u een vertaalproject wilt maken, selecteert u de optie **[!UICONTROL Create a new translation project]** en in de **Projecttitel** -veld, geeft u de titel op. Bijvoorbeeld: `Government Reference Site - German locale.`
   * Als u een nieuw woordenboek wilt toevoegen aan een bestaand vertaalproject, selecteert u de optie **[!UICONTROL Add to an existing translation project]** en selecteert u een **[!UICONTROL Existing translation project]**.
1. In de **Doeltalen** veld, geef een landinstelling op (bijvoorbeeld `German(de)`). U kunt meerdere landinstellingen opgeven. Het formulier wordt vertaald naar alle landinstellingen die in het dialoogvenster **Doeltalen** veld. Klikken **Gereed**.
1. Klik in het dialoogvenster Woordenboek toegevoegd op **Projecten openen**.
1. Klik in het scherm Projecten op het gemaakte project. Klik bijvoorbeeld op de knop **Referentiesite van de overheid - Duitse landinstelling** tegel.
1. Op de **Vertaaltaak** tegel, klik op de knop ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Start**. De status van de tegel verandert in Concept. Na de vertaling verandert de status in **Goedgekeurd**. Vernieuw de pagina na een paar minuten en controleer de status.

   ![Vertaling starten](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. Nadat de status is gewijzigd in **Goedgekeurd** op de **Vertaaltaak** tegel, klik op de knop ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Voltooid**.

1. Als u een voorbeeld van het gelokaliseerde formulier wilt bekijken, selecteert u het gelokaliseerde formulier in de gebruikersinterface van AEM Forms. Klikken **[!UICONTROL Preview]** >**[!UICONTROL Preview as HTML]**. Open het formulier opnieuw nadat u het `afAcceptLang=<locale code>` naar de URL van het formulier. Voeg bijvoorbeeld `afAcceptLang=de`om de Duitse versie van het formulier te openen.


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

1. Selecteer in de gebruikersinterface van AEM Forms een formulier en selecteer de **[!UICONTROL Add Dictionary]** -optie.
1. In Add Woordenboek aan het scherm van het Project van de Vertaling, voor **[!UICONTROL Project]** option

   * Als u een vertaalproject wilt maken, selecteert u de optie **[!UICONTROL Create a new translation project]** en in de **Projecttitel** -veld, geeft u de titel op. Bijvoorbeeld: `Government Reference Site - German locale.`
   * Als u een nieuw woordenboek wilt toevoegen aan een bestaand vertaalproject, selecteert u de optie **[!UICONTROL Add to an existing translation project]** en selecteert u een **[!UICONTROL Existing translation project]**.
1. In de **Doeltalen** veld, geef een landinstelling op (bijvoorbeeld `German(de)`). U kunt meerdere landinstellingen opgeven. Het formulier wordt vertaald naar alle landinstellingen die in het dialoogvenster **Doeltalen** veld. Klikken **Gereed**.
1. Klik in het dialoogvenster Woordenboek toegevoegd op **Projecten openen**.
1. Klik in het scherm Projecten op het gemaakte project. Klik bijvoorbeeld op de knop **Referentiesite van de overheid - Duitse landinstelling** tegel.
1. Onder aan het dialoogvenster **Samenvatting** tegel, klik op de knop **ovalen**. Het scherm Projecteigenschappen omzetten wordt geopend.
1. Open de **[!UICONTROL Advanced]** tabblad boven aan het dialoogvenster **Eigenschappen van vertaalproject** scherm. Voor de **[!UICONTROL Translation field]**, selecteert u **[!UICONTROL Human Translation]**. Klikken **Opslaan en sluiten** boven aan het scherm.
1. Op de **Vertaaltaak** tegel, klik op de knop ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Exporteren**. Klik in het dialoogvenster Exporteren op de optie Geëxporteerd bestand downloaden. Er wordt een ZIP-bestand gedownload.
   ![Omzetbestand exporteren](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. Extraheer het gedownloade .zip-bestand. De geëxtraheerde map heeft twee bestanden:
   * transleren_export_summary.xml
   * [formuliervelden-bestand].xml.
1. Open de [formuliervelden-bestand].xml voor bewerking. Voeg de gelokaliseerde tekenreeksen en berichten voor formuliervelden toe. Sla het bestand op en sluit het.
1. De bestanden transleren_export_summary.xml en [formuliervelden-bestand].xml.
1. Op de **Vertaaltaak** tegel, klik op de knop ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Importeren**. Selecteer het archief met [formuliervelden-bestand].xml. met gelokaliseerde tekenreeksen en berichten voor formuliervelden.

   ![Omzetbestand importeren](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. Als u een voorbeeld van het gelokaliseerde formulier wilt bekijken, selecteert u het gelokaliseerde formulier in de gebruikersinterface van AEM Forms. Klikken **[!UICONTROL Preview]** >**[!UICONTROL Preview as HTML]**. Open het formulier opnieuw nadat u het `afAcceptLang=<locale code>` naar de URL van het formulier. Voeg bijvoorbeeld `afAcceptLang=de`om de Duitse versie van het formulier te openen.

## Zie ook {#see-also}

{{see-also}}