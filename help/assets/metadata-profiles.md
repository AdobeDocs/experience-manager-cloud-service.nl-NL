---
title: Metagegevensprofielen
description: Informatie over metagegevensprofielen voor elementen. Leer hoe u een metagegevensprofiel maakt en toepast op mapelementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Metagegevensprofielen {#metadata-profiles}

Met een metagegevensprofiel kunt u standaardmetagegevens toepassen op elementen in een map. Maak een metagegevensprofiel en pas dit toe op een map. Elk element dat u vervolgens uploadt naar de map, neemt de standaardmetagegevens over die u hebt geconfigureerd in het metagegevensprofiel.

<!-- See [Profiles for Processing Metadata, Images, and Videos](processing-profiles.md).

See also [Best Practices for Organizing your Digital Assets for using Processing Profiles](/help/assets/best-practices-for-file-management.md).

-->

## Een metagegevensprofiel toevoegen {#adding-a-metadata-profile}

1. Tik op het AEM-logo en navigeer naar **[!UICONTROL Gereedschappen > Middelen > Metagegevensprofielen]** en tik vervolgens op **[!UICONTROL Maken]**.
1. Voer een titel in voor Metagegevensprofiel, bijvoorbeeld Voorbeeldmetagegevens, en tik op **[!UICONTROL Verzenden]**. Het bewerkingsformulier voor het metagegevensprofiel wordt weergegeven.
1. Klik op een component en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Instellingen]** . Klik bijvoorbeeld op de component **[!UICONTROL Beschrijving]** en bewerk de eigenschappen ervan.
Bewerk de volgende eigenschappen voor de component **[!UICONTROL Description]** :

   * **[!UICONTROL Veldlabel]** - De weergavenaam van de eigenschap metadata. Dit is alleen voor de gebruikersverwijzing.
   * **[!UICONTROL Toewijzen aan eigenschap]** - De waarde van deze eigenschap geeft het relatieve pad/de relatieve naam aan naar het knooppunt met middelen waar het wordt opgeslagen in de opslagplaats. De waarde moet altijd beginnen met `./` omdat dit aangeeft dat het pad zich onder het knooppunt van het element bevindt.

      De waarde die u opgeeft voor de eigenschap **** Map to wordt opgeslagen als een eigenschap onder het metagegevensknooppunt van het element. Bijvoorbeeld als u opgeeft. `/jcr:content/metadata/dc:desc` als naam van **[!UICONTROL Kaart aan bezit]**, slaat de Middelen van AEM de waarde `dc:desc` bij de de meta-gegevensknoop van het element op.

   * **[!UICONTROL Standaardwaarde]** - Gebruik deze eigenschap om een standaardwaarde voor de metagegevenscomponent toe te voegen. Als u bijvoorbeeld &quot;Mijn beschrijving&quot; opgeeft, wordt deze waarde toegewezen aan de eigenschap `dc:desc` in het metagegevensknooppunt van het element.

      >[!NOTE]
      >
      >Een standaardwaarde toevoegen aan een nieuwe metagegevenseigenschap (die nog niet bestaat op het tabblad . `/jcr:content/metadata` node) geeft de eigenschap en de waarde ervan standaard niet weer op de pagina Eigenschappen van het element. Als u de nieuwe eigenschap wilt weergeven op de pagina Eigenschappen van de elementen, wijzigt u het bijbehorende schema.

1. (Optioneel) Voeg meer componenten toe aan het formulier bewerken op het tabblad **[!UICONTROL Formulier]** samenstellen en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Instellingen]** . De volgende eigenschappen zijn beschikbaar op het tabblad **[!UICONTROL Formulier]** samenstellen:

| Component | Eigenschappen |
|------------------|----------------------------------------------------|
| Sectiekop | Veldlabel, Beschrijving |
| Tekst met één regel | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Meerdere waardetekst | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
|  Getal | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Date | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Standaardlabels | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde, Beschrijving |

1. Tik **[!UICONTROL op Gereed]**. Het metagegevensprofiel wordt toegevoegd aan de lijst met profielen op de pagina **[!UICONTROL Metagegevensprofielen]** .

## Een metagegevensprofiel kopiëren {#copying-a-metadata-profile}

1. Selecteer op de pagina **[!UICONTROL Metagegevensprofielen]** een metagegevensprofiel om er een kopie van te maken.
1. Tik op **[!UICONTROL Kopiëren]** van de werkbalk.
1. Voer in het dialoogvenster Metagegevensprofiel **** kopiëren een titel in voor de nieuwe kopie van het metagegevensprofiel.
1. Tik op **[!UICONTROL Kopiëren]**. De kopie van het metagegevensprofiel wordt weergegeven in de lijst met profielen op de pagina **[!UICONTROL Metagegevensprofielen]** .

## Een metagegevensprofiel verwijderen {#deleting-a-metadata-profile}

1. Selecteer op de pagina **[!UICONTROL Metagegevensprofielen]** een profiel dat u wilt verwijderen.
1. Tik op **[!UICONTROL Metagegevensprofielen]** verwijderen op de werkbalk.
1. Klik in het dialoogvenster op **[!UICONTROL Verwijderen]** om het verwijderen te bevestigen. Het metagegevensprofiel wordt uit de lijst verwijderd.

## Een metagegevensprofiel toepassen op mappen {#applying-a-metadata-profile-to-folders}

Wanneer u een metagegevensprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Dit betekent dat u slechts één metagegevensprofiel kunt toewijzen aan een map. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander metagegevensprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat in de kaartnaam wordt weergegeven.

U kunt metagegevensprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### Metagegevensprofielen toepassen op specifieke mappen {#applying-metadata-profiles-to-specific-folders}

U kunt een metagegevensprofiel toepassen op een map vanuit het menu **[!UICONTROL Gereedschappen]** of vanuit **[!UICONTROL Eigenschappen]** in de map. In deze sectie wordt beschreven hoe u op beide manieren metagegevensprofielen kunt toepassen op mappen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### Metagegevensprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tik op het AEM-logo en navigeer naar **[!UICONTROL Gereedschappen > Middelen > Metagegevensprofielen]**.
1. Selecteer het metagegevensprofiel dat u wilt toepassen op een of meerdere mappen.
1. Tik op Metagegevensprofiel **[!UICONTROL toepassen op map(pen)]** en selecteer de map of meerdere mappen die u wilt gebruiken voor de zojuist geüploade elementen en tik op **[!UICONTROL Gereed]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Metagegevensprofielen toepassen op mappen vanuit Eigenschappen {#applying-metadata-profiles-to-folders-from-properties}

1. Tik in het linkerspoor op **[!UICONTROL Middelen]** en navigeer naar de map waarop u een metagegevensprofiel wilt toepassen.
1. Tik op het vinkje of klik op het vinkje in de map om het te selecteren en tik op **Eigenschappen** of klik op Eigenschappen.
1. Selecteer het tabblad **[!UICONTROL Metagegevensprofielen]** en selecteer het profiel in de vervolgkeuzelijst en tik op **Opslaan]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

### Een metagegevensprofiel algemeen toepassen {#applying-a-metadata-profile-globally}

Naast het toepassen van een profiel op een map, kunt u er ook een globaal toepassen, zodat het geselecteerde profiel wordt toegepast op inhoud die in AEM-elementen in een map is geüpload.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**Voer een van de volgende handelingen uit als u een metagegevensprofiel globaal wilt toepassen**

* Navigeer naar `https://<AEM server>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en tik op **Opslaan**.

* Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`. Voeg de eigenschap toe `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` en tik op **Alles** opslaan.

## Een metagegevensprofiel uit mappen verwijderen {#removing-a-metadata-profile-from-folders}

Wanneer u een metagegevensprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een metagegevensprofiel uit een map verwijderen vanuit het menu **Gereedschappen** of vanuit de map **Eigenschappen**. In deze sectie wordt beschreven hoe u metagegevensprofielen op beide manieren uit mappen kunt verwijderen.

### Metagegevensprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Tik op het AEM-logo of klik op dit logo en ga naar **[!UICONTROL Gereedschappen > Middelen > Metagegevensprofielen]**.
1. Selecteer het metagegevensprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Tik op Metagegevensprofiel **[!UICONTROL verwijderen uit map(pen)]** en selecteer de map of meerdere mappen waaruit u een profiel wilt verwijderen en tik op **[!UICONTROL Gereed]**.

   U kunt bevestigen dat het metagegevensprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Metagegevensprofielen uit mappen verwijderen via eigenschappen {#removing-metadata-profiles-from-folders-via-properties}

1. Tik op het AEM-logo en navigeer naar **[!UICONTROL Middelen]** en vervolgens naar de map waaruit u een metagegevensprofiel wilt verwijderen.
1. Tik in de map op het vinkje om het te selecteren en tik vervolgens op **[!UICONTROL Eigenschappen]**.
1. Selecteer het tabblad **[!UICONTROL Metagegevensprofielen]** en selecteer **[!UICONTROL Geen]** in de vervolgkeuzelijst en klik op **[!UICONTROL Opslaan]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.
