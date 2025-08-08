---
title: Hoe te om het Model van de Gegevens van de Vorm (FDM) voor een vorm met Aangepast Vorm te integreren?
description: Leer formulieren te maken op basis van een formuliergegevensmodel (FDM). Voorbeeldgegevens voor gegevensmodelobjecten in de FDM genereren en bewerken.
feature: Edge Delivery Services, Adaptive Forms, Form Data Model
role: Admin, User
source-git-commit: 87650caea6eb907093f0f327f1dbc19641098e4a
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Formulieren integreren met formuliergegevensmodel

Door formulieren te integreren met een FDM (Form Data Model) kunt u verschillende backendgegevensbronnen gebruiken om een FDM (Form Data Model) te maken. U kunt het formuliergegevensmodel (FDM) gebruiken als een schema in verschillende formulierworkflows. Vorm de gegevensbronnen en creeer een Model van de Gegevens van de Vorm (FDM) dat op de voorwerpen en de diensten van het gegevensmodel beschikbaar in gegevensbronnen wordt gebaseerd.

## Voordelen van het integreren van Forms met het Model van de Gegevens van het Vorm (FDM)

* **Naadloze Connectiviteit Backend**: Verbind vormen met diverse achterste deelsystemen (b.v., gegevensbestanden, REST APIs, de diensten van SOAP, CRMs) zonder douanecode. Dit maakt realtime gegevensuitwisseling mogelijk en vermindert de integratie-inspanning.
* **Gecentraliseerd het Schema van Gegevens** Het Model van de Gegevens van de Vorm dient als verenigd gegevensschema dat afbeelding en beheer van gegevensvoorwerpen en de diensten vereenvoudigt die over veelvoudige vormen en werkschema&#39;s worden gebruikt.

* **Verbeterde Vooraf ingevulde en Verzending van de Vorm**: Vorm gemakkelijk vooraf ingevulde en voorlegging acties gebruikend de diensten van de Gegevens van de Vorm, die nauwkeurige en bijgewerkte gegevensherwinning en opslag verzekeren.

* **Steun voor Dynamische Werkschema&#39;s**: Het Model van de Gegevens van de vorm kan met werkschema&#39;s worden geïntegreerd om bedrijfsprocessen te automatiseren die op voorgelegde of opgehaalde gegevens worden gebaseerd, die algemene efficiency verbeteren.

## Vereisten

Voordat u het formulier configureert met het formuliergegevensmodel, moet u de volgende stappen uitvoeren:

* [ vorm Gegevens Source ](/help/forms/configure-data-sources.md): Opstelling de gegevensbron om uw vorm aan achterste gegevens te verbinden.
* [ creeer het Model van de Gegevens van de Vorm (FDM) ](/help/forms/create-form-data-models.md): Bouw een gegevensmodel gebruikend gegevensvoorwerpen en de diensten van de gevormde gegevensbron.
* [ vormt de ModelVoorwerpen en de Diensten van Gegevens ](/help/forms/work-with-form-data-model.md): Wijs de voorwerpen en de diensten van het gegevensmodel in kaart om vlotte gegevensstroom tussen de vorm en de gegevensbron te verzekeren.

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Voer de volgende stappen uit om het Model van de Gegevens van de Vorm met Aangepaste Vorm te vormen die op de Component van de Stichting wordt gebaseerd als:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit Using Form Data Model]**.

   ![ voorleggen gebruikend het Model van de Gegevens van de Vorm ](/help/forms/assets/submit-uisng-fdm-fc.png)

1. Selecteer de gemaakte **[!UICONTROL Data Model to submit]** configuratie.
Om gehechtheid aan het gegevensbestand voor te leggen selecteer **vormgehechtheid** voorleggen. Het Document van Recore (DoR) wordt bewaard in gegevensbestand door **te selecteren legt Document van Verslag** voor.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

>[!TAB  Component van de Kern ]

Voer de volgende stappen uit om Formuliergegevensmodel te configureren met adaptief formulier op basis van kerncomponent als:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Van de **[!UICONTROL Submit Action]** drop-down lijst, uitgezochte **[voorleggen Gebruikend het Model van Gegevens van de Vorm]**.
   ![ voorleggen gebruikend het Model van de Gegevens van de Vorm ](/help/forms/assets/submit-uisng-fdm-cc.png)

1. Selecteer de gemaakte **[!UICONTROL Data Model to submit]** configuratie.
Om gehechtheid aan het gegevensbestand voor te leggen selecteer **vormgehechtheid** voorleggen. Het Document van Recore (DoR) wordt bewaard in gegevensbestand door **te selecteren legt Document van Verslag** voor.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

>[!TAB  Universele Redacteur ]

Voer de volgende stappen uit om Formuliergegevensmodel te configureren met Adaptief formulier dat in Universal is geschreven als:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.

   Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3} uitbreiding van de Eigenschappen van de Vorm {in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

1. Klik **Verzending** tabel en selecteer **[!UICONTROL Submit using Form Data Model]**.

   ![ OneDrive GIF ](/help/forms/assets/submit-uisng-fdm-ue.png)
Als u **sparen Bijlagen met Oorspronkelijke Naam** selecteert, worden de gehechtheid opgeslagen in de omslag gebruikend hun originele filenames. U kunt Document of Record (DoR) ook opslaan in de Azure Blob Storage.

1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klikken **[!UICONTROL Save&Close]**

Voor gedetailleerde instructies op hoe te om vormen te integreren authored in de Universele Redacteur, verwijs naar het artikel [ integreer Forms met het Model van de Gegevens van de Vorm in Universele Redacteur ](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

>[!ENDTABS]

## Verwante artikelen

{{af-submit-action}}
