---
title: Metadataprofielen
description: Informatie over metagegevensprofielen voor elementen. Leer hoe u een metagegevensprofiel maakt en toepast op mapelementen.
contentOwner: AG
feature: Metadata
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 6fa911f39d707687e453de270bc0f3ece208d380
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 20%

---


# Metadataprofielen {#metadata-profiles}

Met een metagegevensprofiel kunt u standaardmetagegevens toepassen op elementen in een map. Maak een metagegevensprofiel en pas dit toe op een map. Elk element dat u vervolgens uploadt naar de map, neemt de standaardmetagegevens over die u hebt geconfigureerd in het metagegevensprofiel.

## Een metagegevensprofiel {#adding-a-metadata-profile} toevoegen

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** en klik vervolgens op **[!UICONTROL Create]**.
1. Voer een titel in voor Metagegevensprofiel, bijvoorbeeld Voorbeeldmetagegevens, en tik **[!UICONTROL Submit]**. Het bewerkingsformulier voor het metagegevensprofiel wordt weergegeven.
1. Klik op een component en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**. Klik bijvoorbeeld op de component **[!UICONTROL Description]** en bewerk de eigenschappen ervan.
Bewerk de volgende eigenschappen voor de component **[!UICONTROL Description]**:

   * **[!UICONTROL Field Label]** - De weergavenaam van de eigenschap metadata. Dit is alleen voor de gebruikersverwijzing.
   * **[!UICONTROL Map to Property]** - De waarde van deze eigenschap geeft het relatieve pad/de relatieve naam aan naar het knooppunt met middelen waar het wordt opgeslagen in de opslagplaats. De waarde moet altijd beginnen met `./` omdat dit aangeeft dat het pad zich onder het knooppunt van het element bevindt.

      De waarde die u opgeeft voor **[!UICONTROL Map to property]**, wordt opgeslagen als een eigenschap onder het metagegevensknooppunt van het element. Als u bijvoorbeeld `/jcr:content/metadata/dc:desc` als naam van  **[!UICONTROL Map to property]**,  [!DNL Adobe Experience Manager Assets] slaat de waarde  `dc:desc` bij de de meta-gegevensknoop van het element op.

   * **[!UICONTROL Default Value]** - Gebruik deze eigenschap om een standaardwaarde voor de metagegevenscomponent toe te voegen. Als u bijvoorbeeld &quot;Mijn beschrijving&quot; opgeeft, wordt deze waarde toegewezen aan de eigenschap `dc:desc` bij het metagegevensknooppunt van het element.

      >[!NOTE]
      >
      >Als u een standaardwaarde toevoegt aan een nieuwe eigenschap metadata (die niet bestaat op het knooppunt `/jcr:content/metadata`), worden de eigenschap en de waarde ervan standaard niet weergegeven op de pagina Eigenschappen van het element. Om het nieuwe bezit op de [!UICONTROL Properties] pagina te bekijken, wijzig de overeenkomstige schemavorm.

1. (Optioneel) Voeg op het tabblad **[!UICONTROL Build Form]** meer componenten toe aan het formulier Bewerken en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**. De volgende eigenschappen zijn beschikbaar op het tabblad **[!UICONTROL Build Form]**:

| Component | Eigenschappen |
|------------------|----------------------------------------------------|
| Sectiekop | Veldlabel, Beschrijving |
| Tekst met één regel | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Meerdere waardetekst | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Getal | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Date | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Standaardlabels | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde, Beschrijving |

1. Klik op **[!UICONTROL Done]**. Het metagegevensprofiel wordt toegevoegd aan de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]**.

## Een metagegevensprofiel {#copying-a-metadata-profile} kopiëren

1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** een metagegevensprofiel om er een kopie van te maken.
1. Klik op **[!UICONTROL Copy]** op de werkbalk.
1. Voer in het dialoogvenster **[!UICONTROL Copy Metadata Profile]** een titel in voor de nieuwe kopie van het metagegevensprofiel.
1. Klik op **[!UICONTROL Copy]**. De kopie van het metadataprofiel wordt weergegeven in de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]**.

## Een metagegevensprofiel {#deleting-a-metadata-profile} verwijderen

1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** een profiel dat u wilt verwijderen.
1. Klik op **[!UICONTROL Delete Metadata Profiles]** op de werkbalk.
1. Klik in het dialoogvenster op **[!UICONTROL Delete]** om de verwijderbewerking te bevestigen. Het metagegevensprofiel wordt uit de lijst verwijderd.

## Een metagegevensprofiel toepassen op mappen {#applying-a-metadata-profile-to-folders}

Wanneer u een metagegevensprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Dit betekent dat u slechts één metagegevensprofiel kunt toewijzen aan een map. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander metagegevensprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat in de kaartnaam wordt weergegeven.

U kunt metagegevensprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### Metagegevensprofielen toepassen op specifieke mappen {#applying-metadata-profiles-to-specific-folders}

U kunt een metadataprofiel toepassen op een map vanuit het menu **[!UICONTROL Tools]**, of vanuit **[!UICONTROL Properties]** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u op beide manieren metadataprofielen kunt toepassen op mappen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### Metagegevensprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Ga naar **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selecteer het metagegevensprofiel dat u wilt toepassen op een of meerdere mappen.
1. Klik op **[!UICONTROL Apply Metadata Profile to Folder(s)]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en klik op **[!UICONTROL Done]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Metagegevensprofielen toepassen op mappen vanuit Eigenschappen {#applying-metadata-profiles-to-folders-from-properties}

1. Klik in de linkertrack op **[!UICONTROL Assets]** en navigeer naar de map waarop u een metagegevensprofiel wilt toepassen.
1. Klik of klik op het vinkje in de map om het te selecteren en klik of klik op **Eigenschappen**.
1. Selecteer de tab **[!UICONTROL Metadata Profiles]** en selecteer het profiel in de vervolgkeuzelijst en klik op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

### Een metagegevensprofiel globaal toepassen {#applying-a-metadata-profile-globally}

Naast het toepassen van een profiel op een omslag, kunt u ook globaal toepassen zodat om het even welke inhoud die in [!DNL Experience Manager Assets] in om het even welke omslag wordt geupload het geselecteerde profiel wordt toegepast.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**Voer een van de volgende handelingen uit als u een metagegevensprofiel globaal wilt toepassen**

* Navigeer naar `https://<AEM server>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het aangewezen profiel toe en klik **sparen**.

* Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`. Voeg de eigenschap `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` toe. Klik **Alles opslaan**.

## Een metagegevensprofiel verwijderen uit mappen {#removing-a-metadata-profile-from-folders}

Wanneer u een metagegevensprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Elke verwerking van bestanden die in de mappen is opgetreden, blijft echter intact.

U kunt een metadataprofiel uit een map verwijderen vanuit het menu **Gereedschappen**, of vanuit de **Eigenschappen** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u metadataprofielen op beide manieren uit mappen kunt verwijderen.

### Metagegevensprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klik op het AEM en navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selecteer het metagegevensprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Klik op **[!UICONTROL Remove Metadata Profile from Folder(s)]** en selecteer de map of meerdere mappen waaruit u een profiel wilt verwijderen en klik op **[!UICONTROL Done]**.

   U kunt bevestigen dat het metagegevensprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Metagegevensprofielen uit mappen verwijderen via Eigenschappen {#removing-metadata-profiles-from-folders-via-properties}

1. Klik op het AEM en navigeer **[!UICONTROL Assets]** naar de map waaruit u een metagegevensprofiel wilt verwijderen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens op **[!UICONTROL Properties]**.
1. Selecteer het tabblad **[!UICONTROL Metadata Profiles]**, selecteer **[!UICONTROL None]** in het vervolgkeuzemenu en klik op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.
