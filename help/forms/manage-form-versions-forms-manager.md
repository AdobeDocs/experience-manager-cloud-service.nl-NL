---
title: Formulierversies beheren in Forms Manager
description: Leer om versies van Adaptive Forms, formulierfragmenten, thema's en andere middelen te maken en te beheren in de gebruikersinterface van Forms Manager.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer, Admin
source-git-commit: 52d6e8163ef24d362287cbedf54c2977fff9c87b
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---


# Assets-versies van formulieren beheren in de gebruikersinterface van Forms Manager

<span class="preview"> Deze functie is beschikbaar via het programma Vroege toegang. Om toegang te verzoeken, verzend een e-mail van uw officieel adres naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com). </span>

Forms Manager ondersteunt nu versioning voor formulierelementen. U kunt versies maken, versiehistorie weergeven en eerdere versies van uw elementen herstellen via de gebruikersinterface van Forms Manager.

## Ondersteunde elementtypen {#supported-asset-types}

U kunt versies maken en beheren voor de volgende elementtypen:

| Type element | Beschrijving |
|---|---|
| Adaptieve Forms (Core Components) | Adaptieve Forms gebouwd met behulp van Core Components |
| Adaptive Forms (Foundation Components) | Adaptieve Forms gebouwd met behulp van Foundation Components |
| Formulierfragmenten | Herbruikbare formuliersecties die door meerdere formulieren worden gedeeld |
| Thema&#39;s | Visuele stijldefinities toegepast op Adaptive Forms |
| XDP-sjablonen | Op XFA gebaseerde formuliersjablonen |
| Binaire activa | Andere bestanden die zijn opgeslagen onder de DAM-opslagplaats voor formulieren |

## Een versie maken {#create-version-forms-manager}

Een versie van een formulierelement maken:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer het formulier of element.
1. Selecteer **[!UICONTROL Timeline]** in het linkerdeelvenster.
1. Klik op **[!UICONTROL Save as Version]** op de tijdlijnwerkbalk.
   ![ sparen als Versie ](/help/forms/assets/create-version.png)
1. Voer een **[!UICONTROL Label]** en een optioneel **[!UICONTROL Comment]** in om de wijzigingen te beschrijven.
1. Klik op **[!UICONTROL Create]**.
   ![ sparen als Version2 ](/help/forms/assets/create-version1.png)

De versie wordt in het tijdlijndeelvenster weergegeven met het label, de opmerking en het tijdstempel.

## Middelen tijdens het uploaden versen {#version-on-upload}

Wanneer u activa met de zelfde naam zoals bestaand activa uploadt, toont de Manager van Forms a **Dossier uploadt** dialoog die van de activa een lijst maakt die moeten worden bijgewerkt. In het dialoogvenster ziet u de naam, de sectie en het pad van het element.

Wanneer al een element met dezelfde naam bestaat, wordt het bestaande element vervangen door de upload en wordt automatisch een nieuwe versie gemaakt. U kunt de gemaakte versie weergeven in de tijdlijn.

![ Dossier uploadt dialoog die versioned toont upload ](/help/forms/assets/version-upload.png)

## Versiehistorie weergeven {#view-version-history}

De versiegeschiedenis van een element weergeven:

1. Selecteer het element in Forms Manager.
1. Selecteer **[!UICONTROL Timeline]** in het linkerdeelvenster.
   ![ Geschiedenis van de Versie ](/help/forms/assets/version-history.png)

In de tijdlijn worden alle versie-items samen met activity-gebeurtenissen weergegeven. Elke ingang toont het etiket, de commentaar, de auteur, en timestamp.

## Een vorige versie herstellen {#restore-version}

Een element terugzetten naar een eerdere versie:

1. Selecteer het element in Forms Manager.
1. Selecteer **[!UICONTROL Timeline]** in het linkerdeelvenster.
1. Selecteer de versie die u wilt herstellen.
1. Klik op **[!UICONTROL Revert to this Version]**.
   ![ keert Versie ](/help/forms/assets/revert-version.png) terug

>[!NOTE]
>
>Afbeeldingen kunnen niet worden teruggezet naar een vorige versie. Alle andere elementtypen, zoals Adaptive Forms, formulierfragmenten, thema&#39;s en XDP-sjablonen, ondersteunen versietestering.

## Zie ook {#see-also}

* [Versioning, revisie en opmerkingen op een adaptief formulier](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)
* [Formulieren en gerelateerde activa importeren en exporteren](/help/forms/import-export-forms-templates.md)
* [Formulieren publiceren en verwijderen](/help/forms/publishing-unpublishing-forms.md)
