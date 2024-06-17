---
title: Digitale middelen opnieuw verwerken
description: Meer informatie over verschillende methoden voor het opwerken van digitale elementen
contentOwner: KK
exl-id: 4759fa8c-10c7-4446-a135-3104b9beaee8
feature: Asset Processing
role: User, Leader, Developer
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---

# Digitale middelen opnieuw verwerken {#reprocessing-digital-assets}

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. Als u de zojuist bewerkte voorinstelling opnieuw wilt toepassen op de bestaande elementen in de map, moet u de map opnieuw verwerken. U kunt zoveel elementen opnieuw verwerken als u nodig hebt.

Elementen in een map opnieuw verwerken als u een van de volgende twee situaties ervaart:

* U wilt een voorinstelling voor een batchset uitvoeren op een bestaande elementenmap waarin al elementen zijn geüpload.
* U bewerkt later een bestaande voorinstelling voor een batch-set die eerder is toegepast op een map met elementen.

## Elementen opnieuw verwerken {#reprocessing-steps}

Elementen in een map opnieuw verwerken:

1. In [!DNL Experience Manager]Selecteer op de elementenpagina de nieuw toegevoegde elementen of de elementen die u opnieuw wilt verwerken.
Als u een map selecteert:

   * In de workflow worden alle bestanden in de geselecteerde map recursief bekeken.
   * Als er een of meer submappen met elementen in de geselecteerde hoofdmap staan, worden alle elementen in de maphiërarchie opnieuw verwerkt.
   * U kunt deze workflow het beste niet uitvoeren in een mappenhiërarchie met meer dan 1000 elementen.

1. Selecteer **[!UICONTROL Reprocess Assets]**. U kunt kiezen uit de volgende twee opties:

   ![Opties voor opwerking van middelen](assets/reprocessing-assets-options.png)

   * **[!UICONTROL Full Process]:** Selecteer deze optie als u het algemene proces wilt uitvoeren, inclusief standaardprofiel, aangepast profiel, dynamische verwerking (indien geconfigureerd) en naverwerkingsworkflows.
   * **[!UICONTROL Advanced]:** Selecteer deze optie om geavanceerde opwerking te kiezen.

     ![Geavanceerde opties voor opwerkingsmiddelen](assets/reprocessing-assets-options-advanced.png)

     Kies een van de volgende geavanceerde opties:

      * **[!UICONTROL Default Preview Renditions]:** Kies deze optie als u de uitvoeringen wilt verwerken waarvan de voorvertoning standaard wordt weergegeven.

      * **[!UICONTROL Metadata]:** Kies deze optie als u metagegevens en slimme tags voor de geselecteerde elementen wilt extraheren.

      * **[!UICONTROL Processing Profiles]:** Kies deze optie als u een geselecteerd profiel opnieuw wilt verwerken. U kunt **[!UICONTROL Full Process]** gebruiken om de standaardverwerking en het aangepaste profiel op te nemen die op mapniveau zijn toegewezen.
        <!--When assets are uploaded to a folder, [!DNL Experience Manager] checks the containing folder's properties for a processing profile. If none is applied, a parent folder in the hierarchy is checked for a processing profile to apply.-->

      * **[!UICONTROL Post-processing Workflow]:** Kies deze optie als aanvullende verwerking van elementen vereist is die niet met de verwerkingsprofielen kunnen worden bereikt. Er kunnen extra nabewerkingsworkflows worden toegevoegd aan de configuratie. Na de verwerking kunt u volledig aangepaste verwerking toevoegen bovenop de configureerbare verwerking met behulp van asset microservices.

Zie [gebruik microservices en verwerkingsprofielen voor bedrijfsmiddelen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=en) voor meer informatie over verwerkingsprofielen en de workflow voor nabewerking.

![Geavanceerde opties voor opwerkingsmiddelen2](assets/reprocessing-assets-options-advanced-2.png)

Nadat u de gewenste opties hebt geselecteerd, klikt u op **[!UICONTROL Reprocess]**. De succesboodschap wordt weergegeven.

## Scenario&#39;s voor de opwerking van digitale elementen {#scenarios-reprocessing}

[!DNL Experience Manager] maakt het mogelijk digitale elementen opnieuw te verwerken voor de volgende componenten.

### Slimme tags {#reprocessing-smart-tags}

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar digitale activa van een bepaalde klasse te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt gecontroleerd, worden de elementen gemakkelijk geïdentificeerd en opgehaald.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren van digitale activa die op bedrijfstaxonomie worden gebaseerd hen op de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen.

Meer informatie over [Slimme tags voor video-elementen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/smart-tags-video-assets.html?lang=en).

Meer informatie over [Kleurcodes opnieuw verwerken voor bestaande afbeeldingen in DAM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en#color-tags-existing-images).

### Slim uitsnijden {#reprocessing-smart-crop}

Meer informatie over [Dynamic Media slim uitsnijden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=en) waarmee u specifieke uitsnijdingen kunt toepassen (**[!UICONTROL Smart Cropping]** en pixeluitsnijding) en verscherpingsconfiguratie voor de geüploade elementen.

### Metagegevens {#reprocessing-metadata}

[!DNL Adobe Experience Manager Assets] bewaart meta-gegevens voor elk middel. Het maakt het gemakkelijker om activa te categoriseren en te organiseren en het helpt mensen die naar een specifiek bezit zoeken. Dankzij de mogelijkheid om metagegevens te extraheren uit bestanden die naar Experience Manager Assets zijn geüpload, kan het beheer van metagegevens worden geïntegreerd in de creatieve workflow. Met de mogelijkheid om metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van hun metagegevens.

Meer informatie over [Metagegevensprofielen opnieuw verwerken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/metadata-profiles.html?lang=en).

### Dynamic Media-elementen in een map opnieuw verwerken {#reprocessing-dynamic-media}

U kunt elementen opnieuw verwerken in een map die al een bestaand Dynamic Media-afbeeldingsprofiel heeft of een Dynamic Media-videoprofiel dat u later hebt gewijzigd. Ga voor meer informatie naar [Dynamic Media-elementen in een map opnieuw verwerken.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/about-image-video-profiles.html?lang=en)

>[!NOTE]
>
>U moet configureren [!DNL Dynamic Media] in de omgeving om het dialoogvenster Dynamic Media in te schakelen.
>

### Workflows

Meer informatie over [verwerkingsprofielen en nabewerkingsworkflows](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=en).
