---
title: Metagegevensprofielen
description: Informatie over metagegevensprofielen voor elementen. Leer hoe u een metagegevensprofiel maakt en toepast op mapelementen.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: eef90c6a-b354-4342-8b97-21d067ae2979
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 17%

---

# Metagegevensprofielen {#metadata-profiles}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-config.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Met een metagegevensprofiel kunt u standaardmetagegevens toepassen op elementen in een map. Maak een metagegevensprofiel en pas dit toe op een map. Elk element dat u vervolgens naar de map uploadt, neemt de standaardmetagegevens over die u in het metagegevensprofiel hebt geconfigureerd.

Een belangrijk concept voor het gebruik van profielen in Experience Manager Assets is dat deze aan mappen worden toegewezen. Binnen een profiel bevinden zich instellingen in de vorm van metagegevensprofielen, samen met videoprofielen of afbeeldingsprofielen. Met deze instellingen wordt de inhoud van een map samen met een van de submappen van de map verwerkt. Daarom heeft de manier waarop u bestanden en mappen benoemt, de manier waarop u submappen rangschikt en de manier waarop u de bestanden in deze mappen verwerkt, een grote invloed op de manier waarop deze elementen door een profiel worden verwerkt.
Door consistente en geschikte naamgevingsstrategieën voor bestanden en mappen en goede praktijken voor metagegevens te gebruiken, kunt u optimaal gebruikmaken van de verzameling van digitale elementen en ervoor zorgen dat de juiste bestanden door het juiste profiel worden verwerkt.

## Een metagegevensprofiel toevoegen {#adding-a-metadata-profile}

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** en klik vervolgens op **[!UICONTROL Create]** .
1. Voer een titel in voor Metagegevensprofiel, bijvoorbeeld Voorbeeldmetagegevens, en selecteer **[!UICONTROL Submit]** . Het bewerkingsformulier voor het metagegevensprofiel wordt weergegeven.
1. Klik op een component en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** . Klik bijvoorbeeld op de component **[!UICONTROL Description]** en bewerk de eigenschappen ervan.
Bewerk de volgende eigenschappen voor de component **[!UICONTROL Description]** :

   * **[!UICONTROL Field Label]** - De weergavenaam van de eigenschap metadata. Dit is alleen voor de gebruikersverwijzing.
   * **[!UICONTROL Map to Property]** - De waarde van deze eigenschap geeft het relatieve pad/de relatieve naam aan naar het knooppunt met middelen waar het in de opslagplaats is opgeslagen. De waarde moet altijd beginnen met `./` omdat dit aangeeft dat het pad zich onder het knooppunt van het element bevindt.

     De waarde die u opgeeft voor **[!UICONTROL Map to property]** , wordt opgeslagen als een eigenschap onder het metagegevensknooppunt van het element. Als u bijvoorbeeld `/jcr:content/metadata/dc:desc` als de naam van **[!UICONTROL Map to property]** , slaat [!DNL Adobe Experience Manager Assets] de waarde `dc:desc` op in het metagegevensknooppunt van het element.

   * **[!UICONTROL Default Value]** - Gebruik deze eigenschap om een standaardwaarde voor de metagegevenscomponent toe te voegen. Als u bijvoorbeeld &quot;Mijn beschrijving&quot; opgeeft, wordt deze waarde toegewezen aan de eigenschap `dc:desc` bij het metagegevensknooppunt van het element.

     >[!NOTE]
     >
     >Als u een standaardwaarde toevoegt aan een nieuwe eigenschap metadata (die niet bestaat op het knooppunt `/jcr:content/metadata` ), worden de eigenschap en de waarde ervan standaard niet weergegeven op de pagina Eigenschappen van het element. Als u de nieuwe eigenschap op de pagina [!UICONTROL Properties] wilt weergeven, wijzigt u het bijbehorende schema.

1. (Optioneel) Voeg op het tabblad **[!UICONTROL Build Form]** meer componenten toe aan het formulier Bewerken en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**. De volgende eigenschappen zijn beschikbaar op het tabblad **[!UICONTROL Build Form]**:

| Component | Eigenschappen |
|------------------|----------------------------------------------------|
| Sectiekop | Veldlabel, Beschrijving |
| Tekst met één regel | Veld, label, toewijzen aan eigenschap, standaardwaarde |
| Meerdere waardetekst | Veld, label, toewijzen aan eigenschap, standaardwaarde |
| Getal | Veld, label, toewijzen aan eigenschap, standaardwaarde |
| Datum | Veld, label, toewijzen aan eigenschap, standaardwaarde |
| Standaardlabels | Veldlabel, Toewijzen aan eigenschap, Standaardwaarde, Beschrijving |

1. Klik op **[!UICONTROL Done]**. Het metagegevensprofiel wordt toegevoegd aan de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]** .

## Een metagegevensprofiel kopiëren {#copying-a-metadata-profile}

1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** een metagegevensprofiel om er een kopie van te maken.
1. Klik op **[!UICONTROL Copy]** op de werkbalk.
1. Voer in het dialoogvenster **[!UICONTROL Copy Metadata Profile]** een titel in voor de nieuwe kopie van het metagegevensprofiel.
1. Klik op **[!UICONTROL Copy]**. De kopie van het metadataprofiel wordt weergegeven in de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]**.

## Een metagegevensprofiel verwijderen {#deleting-a-metadata-profile}

1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** een profiel dat u wilt verwijderen.
1. Klik op **[!UICONTROL Delete Metadata Profiles]** op de werkbalk.
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

1. Navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]** .
1. Selecteer het metagegevensprofiel dat u wilt toepassen op een of meerdere mappen.
1. Klik op **[!UICONTROL Apply Metadata Profile to Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen. Klik vervolgens op **[!UICONTROL Done]** . Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Metagegevensprofielen toepassen op mappen vanuit Eigenschappen {#applying-metadata-profiles-to-folders-from-properties}

1. Klik in de linkertrack op **[!UICONTROL Assets]** en navigeer naar de map waarop u een metagegevensprofiel wilt toepassen.
1. Voor de omslag, selecteer het vinkje om het te selecteren en dan **Eigenschappen** te selecteren.
1. Selecteer de tab **[!UICONTROL Metadata Profiles]** , selecteer het profiel in de vervolgkeuzelijst en klik op **[!UICONTROL Save]** . Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

### Een metagegevensprofiel algemeen toepassen {#applying-a-metadata-profile-globally}

Naast het toepassen van een profiel op een map, kunt u er ook een globaal toepassen, zodat het geselecteerde profiel wordt toegepast op inhoud die in [!DNL Experience Manager Assets] in een map is geüpload.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**om een meta-gegevensprofiel globaal toe te passen, doe één van het volgende**

* Navigeer naar `https://[aem_server]/mnt/overlay/dam/gui/content/assets/v2/foldersharewizard.html/content/dam` en pas het juiste profiel toe en klik op **[!UICONTROL Save]** .

* Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content` . Voeg de eigenschap `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` toe. Klik **sparen allen**.

## Een metagegevensprofiel uit mappen verwijderen {#removing-a-metadata-profile-from-folders}

Wanneer u een metagegevensprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een metadataprofiel uit een map verwijderen vanuit het menu **Gereedschappen**, of vanuit de **Eigenschappen** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u metadataprofielen op beide manieren uit mappen kunt verwijderen.

### Metagegevensprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klik op het Experience Manager-logo en navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]** .
1. Selecteer het metagegevensprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Klik op **[!UICONTROL Remove Metadata Profile from Folders]** , selecteer de map of meerdere mappen waaruit u een profiel wilt verwijderen en klik op **[!UICONTROL Done]** .

   U kunt bevestigen dat het metagegevensprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Metagegevensprofielen uit mappen verwijderen via eigenschappen {#removing-metadata-profiles-from-folders-via-properties}

1. Klik op het Experience Manager-logo en navigeer **[!UICONTROL Assets]** naar de map waaruit u een metagegevensprofiel wilt verwijderen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens op **[!UICONTROL Properties]** .
1. Selecteer het tabblad **[!UICONTROL Metadata Profiles]**, selecteer **[!UICONTROL None]** in het vervolgkeuzemenu en klik op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
