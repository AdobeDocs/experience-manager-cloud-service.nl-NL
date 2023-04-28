---
title: Metadataprofielen
description: Informatie over metagegevensprofielen voor elementen. Leer hoe u een metagegevensprofiel maakt en toepast op mapelementen.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: eef90c6a-b354-4342-8b97-21d067ae2979
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 18%

---

# Metadataprofielen {#metadata-profiles}

Met een metagegevensprofiel kunt u standaardmetagegevens toepassen op elementen in een map. Maak een metagegevensprofiel en pas dit toe op een map. Elk element dat u vervolgens uploadt naar de map, neemt de standaardmetagegevens over die u hebt geconfigureerd in het metagegevensprofiel.

Een belangrijk concept voor het gebruik van profielen in Experience Manager Assets is dat deze aan mappen worden toegewezen. Binnen een profiel bevinden zich instellingen in de vorm van metagegevensprofielen, samen met videoprofielen of afbeeldingsprofielen. Met deze instellingen wordt de inhoud van een map samen met de submappen van de map verwerkt. Daarom heeft de manier waarop u bestanden en mappen benoemt, de manier waarop u submappen rangschikt en de manier waarop u de bestanden in deze mappen verwerkt, een grote invloed op de manier waarop deze elementen door een profiel worden verwerkt.
Door consistente en geschikte naamgevingsstrategieën voor bestanden en mappen en goede praktijken voor metagegevens te gebruiken, kunt u optimaal gebruikmaken van de verzameling van digitale elementen en ervoor zorgen dat de juiste bestanden door het juiste profiel worden verwerkt.

## Een metagegevensprofiel toevoegen {#adding-a-metadata-profile}

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** en klik vervolgens op **[!UICONTROL Create]**.
1. Voer een titel in voor het metagegevensprofiel, bijvoorbeeld Voorbeeldmetagegevens, en tik op **[!UICONTROL Submit]**. Het bewerkingsformulier voor het metagegevensprofiel wordt weergegeven.
1. Klik op een component en configureer de eigenschappen ervan in het dialoogvenster **[!UICONTROL Settings]** tab. Klik bijvoorbeeld op de knop **[!UICONTROL Description]** en de eigenschappen ervan bewerken.
Bewerk de volgende eigenschappen voor de **[!UICONTROL Description]** component:

   * **[!UICONTROL Field Label]** - De weergavenaam van de eigenschap metadata. Dit is alleen voor de gebruikersverwijzing.
   * **[!UICONTROL Map to Property]** - De waarde van deze eigenschap geeft het relatieve pad/de relatieve naam aan naar het knooppunt met middelen waar het wordt opgeslagen in de opslagplaats. De waarde moet altijd beginnen met `./` omdat het aangeeft dat het pad zich onder het knooppunt van het element bevindt.

      De waarde die u opgeeft voor **[!UICONTROL Map to property]** wordt opgeslagen als een eigenschap onder het metagegevensknooppunt van het element. Als u bijvoorbeeld `/jcr:content/metadata/dc:desc` als de naam van **[!UICONTROL Map to property]**, [!DNL Adobe Experience Manager Assets] slaat de waarde op `dc:desc` op het metagegevensknooppunt van het element.

   * **[!UICONTROL Default Value]** - Gebruik deze eigenschap om een standaardwaarde voor de metagegevenscomponent toe te voegen. Als u bijvoorbeeld &quot;Mijn beschrijving&quot; opgeeft, wordt deze waarde toegewezen aan de eigenschap `dc:desc` op het metagegevensknooppunt van het element.

      >[!NOTE]
      >
      >Een standaardwaarde toevoegen aan een nieuwe eigenschap voor metagegevens (die niet bestaat bij `/jcr:content/metadata` node) geeft de eigenschap en de waarde ervan standaard niet weer op de pagina Eigenschappen van het element. Als u de nieuwe eigenschap wilt weergeven op de knop [!UICONTROL Properties] pagina, wijzigt u het corresponderende schema-formulier.

1. (Optioneel) Voeg op het tabblad **[!UICONTROL Build Form]** meer componenten toe aan het formulier Bewerken en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**. De volgende eigenschappen zijn beschikbaar op het tabblad **[!UICONTROL Build Form]**:

| Component | Eigenschappen |
|------------------|----------------------------------------------------|
| Sectiekop | Veldlabel, Beschrijving |
| Tekst met één regel | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Meerdere waardetekst | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Getal | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Datum | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde |
| Standaardlabels | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde, Beschrijving |

1. Klik op **[!UICONTROL Done]**. Het metagegevensprofiel wordt toegevoegd aan de lijst met profielen in het dialoogvenster **[!UICONTROL Metadata Profiles]** pagina.

## Een metagegevensprofiel kopiëren {#copying-a-metadata-profile}

1. Van de **[!UICONTROL Metadata Profiles]** selecteert u een metagegevensprofiel om er een kopie van te maken.
1. Klik op **[!UICONTROL Copy]** op de werkbalk.
1. In de **[!UICONTROL Copy Metadata Profile]** voert u een titel in voor de nieuwe kopie van het metagegevensprofiel.
1. Klik op **[!UICONTROL Copy]**. De kopie van het metadataprofiel wordt weergegeven in de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]**.

## Een metagegevensprofiel verwijderen {#deleting-a-metadata-profile}

1. Van de **[!UICONTROL Metadata Profiles]** selecteert u een profiel dat u wilt verwijderen.
1. Klikken **[!UICONTROL Delete Metadata Profiles]** in de werkbalk.
1. Klik in het dialoogvenster op **[!UICONTROL Delete]** om de verwijderbewerking te bevestigen. Het metagegevensprofiel wordt uit de lijst verwijderd.

## Een metagegevensprofiel toepassen op mappen {#applying-a-metadata-profile-to-folders}

Wanneer u een metagegevensprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. De overerving stopt wanneer een ander profiel wordt toegepast op een submap. U kunt slechts één metagegevensprofiel aan een map toewijzen. Overweeg daarom zorgvuldig de mapstructuur waarin u elementen uploadt, opslaat, gebruikt en archiveert.

Als u een ander metagegevensprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die na de wijziging aan de map worden toegevoegd. U kunt metagegevensprofielen toepassen op specifieke mappen of op alle elementen.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat in de kaartnaam wordt weergegeven.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### Metagegevensprofielen toepassen op specifieke mappen {#applying-metadata-profiles-to-specific-folders}

U kunt een metadataprofiel toepassen op een map vanuit het menu **[!UICONTROL Tools]**, of vanuit **[!UICONTROL Properties]** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u op beide manieren metadataprofielen kunt toepassen op mappen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### Metagegevensprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Ga naar **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selecteer het metagegevensprofiel dat u wilt toepassen op een of meerdere mappen.
1. Klikken **[!UICONTROL Apply Metadata Profile to Folder(s)]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en klik op **[!UICONTROL Done]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Metagegevensprofielen toepassen op mappen vanuit Eigenschappen {#applying-metadata-profiles-to-folders-from-properties}

1. Klik in de linkertrack op **[!UICONTROL Assets]** Navigeer vervolgens naar de map waarop u een metagegevensprofiel wilt toepassen.
1. Klik of klik op het vinkje in de map om het te selecteren en klik of klik vervolgens op **Eigenschappen**.
1. Selecteer **[!UICONTROL Metadata Profiles]** en selecteert u het profiel in de keuzelijst en klikt u op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

### Een metagegevensprofiel algemeen toepassen {#applying-a-metadata-profile-globally}

Naast het toepassen van een profiel op een map, kunt u er ook een globaal toepassen, zodat alle inhoud die u uploadt naar [!DNL Experience Manager Assets] in een map is het geselecteerde profiel toegepast.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**Voer een van de volgende handelingen uit als u een metagegevensprofiel globaal wilt toepassen**

* Navigeren naar `https://[aem_server]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en klik op **[!UICONTROL Save]**.

* Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`. De eigenschap toevoegen `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>`. Klikken **Alles opslaan**.

## Een metagegevensprofiel uit mappen verwijderen {#removing-a-metadata-profile-from-folders}

Wanneer u een metagegevensprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een metadataprofiel uit een map verwijderen vanuit het menu **Gereedschappen**, of vanuit de **Eigenschappen** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u metadataprofielen op beide manieren uit mappen kunt verwijderen.

### Metagegevensprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selecteer het metagegevensprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Klikken **[!UICONTROL Remove Metadata Profile from Folder(s)]** en selecteer de map of meerdere mappen waaruit u een profiel wilt verwijderen en klik op **[!UICONTROL Done]**.

   U kunt bevestigen dat het metagegevensprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Metagegevensprofielen uit mappen verwijderen via eigenschappen {#removing-metadata-profiles-from-folders-via-properties}

1. Klik op het logo van de Experience Manager en navigeer **[!UICONTROL Assets]** en vervolgens naar de map waaruit u een metagegevensprofiel wilt verwijderen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens op **[!UICONTROL Properties]**.
1. Selecteer het tabblad **[!UICONTROL Metadata Profiles]**, selecteer **[!UICONTROL None]** in het vervolgkeuzemenu en klik op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [HTTP-API voor assets](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Assets doorzoeken](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Rapporten over assets](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Facetten doorzoeken](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
