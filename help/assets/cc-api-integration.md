---
title: Automatisering van inhoud voor integratie van Creatives Cloud
description: Variaties van elementen genereren met behulp van Creative Cloud-integratie
contentOwner: AG
feature: Upload, Asset Processing, Publishing, Asset Compute Microservices
role: User, Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Variaties van elementen genereren met [!DNL Adobe Creative Cloud] integratie {#content-automation}

Invoegtoepassing voor automatisering van inhoud integreert [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] en [!DNL Adobe Creative Cloud] API&#39;s om uw elementen op schaal creatief te verwerken. [!DNL Experience Manager] gebruikt cloudgebaseerd [microservices voor bedrijfsmiddelen](/help/assets/asset-microservices-overview.md) om de [!DNL Adobe Creative Cloud] en automatiseert het maken van bedrijfsmiddelen en de verwerking van media.

Elementen bewerken in [!DNL Adobe Photoshop] en [!DNL Adobe Lightroom], hoeft u geen elementen te downloaden van [!DNL Experience Manager Assets], bewerken en opnieuw uploaden. U maakt en configureert een verwerkingsprofiel in [!DNL Experience Manager], past u het profiel toe op een map en uploadt u de middelen naar de map. De geüploade elementen worden opnieuw verwerkt op basis van de verwerkingsprofielen en deze elementen kunnen variëren. De consequente en moeiteloze bulkverwerking bespaart handmatige inspanningen en verhoogt de snelheid van de inhoud, ook zonder de behoefte aan uitstekende creatieve vaardigheden. Ook, kunnen de ontwikkelaars en de partners de activa microservices met directe toegang tot deze APIs uitbreiden en douanelogica omvatten.

Gebruikers kunnen verwerkingsprofielen maken om de volgende creatieve bewerkingen op hun middelen te automatiseren:

* **Automatische tinten**: Hiermee gebruikt u kunstmatige intelligentie om de inhoud van de afbeelding te analyseren en maakt u op intelligente wijze licht- en kleurcorrecties op basis van de unieke kenmerken van de afbeelding.

* **Automatisch rechtop**: Hiermee gebruikt u kunstmatige intelligentie om de inhoud van de afbeelding te analyseren en schuine perspectieven in afbeeldingen te corrigeren. Bijvoorbeeld om niveauhorizonten te maken.

  ![automatische tint](/help/assets/assets/content-automation-autotone.png)

  *Afbeelding: Automatische tinten en automatisch rechttrekken kunnen scheve afbeeldingen verbeteren.*

* **Lightroom-voorinstellingen**: Hiermee past u een door de gebruiker gedefinieerde vormgeving toe op afbeeldingen voor een consistente weergave met behulp van aangepaste voorinstellingen.

  ![Lightroom-voorinstelling](/help/assets/assets/content-automation-lrpresets.png)

  *Afbeelding: Adobe Lightroom-voorinstelling om de afbeeldingskwaliteit voor veel afbeeldingen op consistente wijze te verbeteren.*

* **Knipsel van afbeelding**: Hiermee gebruikt u kunstmatige intelligentie om selectie te maken rond aliente objecten en achtergrond te verwijderen met één opdracht.

  ![Achtergrond verwijderen en een afbeelding uit een foto knippen](/help/assets/assets/content-automation-backgroundremove.png)

* **Afbeeldingsmasker**: gebruikt kunstmatige intelligentie om masker rond aliente voorwerpen met één enkele bevel tot stand te brengen.

  ![Een afbeelding maskeren met AI](/help/assets/assets/content-automation-mask.png)

* **Photoshop-handelingen**: Hiermee past u een reeks [!DNL Adobe Photoshop] taken uit te voeren naar een bestand of een groep bestanden.

  ![Photoshop-acties](/help/assets/assets/content-automation-psactions.png)

* **Vervanging slim object**: past zich aan de schaal aan door afbeeldingen om te wisselen met behoud van alle effecten en aanpassingen die in een PSD-bestand zijn toegepast.

  ![Objecten slim vervangen](/help/assets/assets/content-automation-objectreplace.png)

## Inhoudsautomatisering inschakelen voor AEM as a Cloud Service programma {#enable-content-automation}

De add-on voor automatisering van inhoud inschakelen voor AEM as a Cloud Service programma met gebruik van Cloud Manager:

1. Neem contact op met uw accountvertegenwoordiger om een licentie te verkrijgen voor de add-on Inhoudsautomatisering.
1. Open Cloud Manager en schakel over naar uw organisatie met de bedrijfskiezer.
1. Klikken **[!UICONTROL Add Program]** en geeft u een programmanaam op.
1. Klik op **[!UICONTROL Continue]**.
1. Uitbreiden **[!UICONTROL Assets]** en selecteert u **[!UICONTROL Content Automation]**.
1. Klik op **[!UICONTROL Create]**.
1. De pijplijn in werking stellen aan [Wijzigingen in Cloud Manager implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

Als u de invoegtoepassing voor het automatiseren van inhoud wilt toevoegen aan een bestaand AEM as a Cloud Service programma in Cloud Manager:

1. Klik op ... op de programmakaart.

1. Selecteren **[!UICONTROL Edit Program]** en selecteer vervolgens **[!UICONTROL Solutions & Add-ons]** tab.

1. Uitbreiden **[!UICONTROL Assets]** en selecteert u **[!UICONTROL Content Automation]**.
1. Klik op **[!UICONTROL Update]**.
1. De pijplijn in werking stellen aan [Wijzigingen in Cloud Manager implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

## Een verwerkingsprofiel gebruiken om uw creatieve middelen bulksgewijs te bewerken {#process-assets}

Ga als volgt te werk als u verwerkingsprofielen wilt gebruiken om automatisch variaties te maken:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**.

1. Selecteren **[!UICONTROL Create]** en geeft u een **[!UICONTROL Name]**.

1. Selecteer de **[!UICONTROL Creative]** -tabblad, geeft u de uitvoermap op en selecteert u **[!UICONTROL Add New]** een creatieve configuratie toevoegen.

1. Verlenen **[!UICONTROL Rendition Name]** (of naam uitvoer), **[!UICONTROL Extension]** (of bestandstype), selecteert u **[!UICONTROL Quality]** (of uitvoerparameters), selecteert u **[!UICONTROL Includes]** en **[!UICONTROL Excludes]** MIME-typelijsten (of filter voor invoerelementen) en selecteer de vereiste creatieve bewerking.

   ![[!UICONTROL Creative] tab in [!UICONTROL Processing Profile]](assets/creative-processing-profile.png)

1. Sommige bewerkingen vereisen extra parameters (element). Geef indien nodig waarden op voor deze extra parameters.

1. Voeg meer creatieve bewerkingen toe als onderdeel van hetzelfde verwerkingsprofiel of sla het profiel op.

1. Pas het verwerkingsprofiel toe op een map. Op een map **[!UICONTROL Properties]** pagina, selecteert u **[!UICONTROL Asset Processing]** en selecteert u het verwerkingsprofiel dat u wilt toepassen.

Nadat u het verwerkingsprofiel op een DAM-map hebt toegepast, worden naast de standaardverwerking ook de gedefinieerde bewerkingen uitgevoerd door alle elementen die in deze map zijn geüpload of bijgewerkt. De submappen overerven dezelfde profielen als die zijn toegepast op de bovenliggende mappen. Gebruikers kunnen deze overerving overschrijven.

Selecteer de elementen om de bestaande elementen te verwerken **[!UICONTROL Reprocess]** en selecteert u het gewenste verwerkingsprofiel.

## Tips en beperkingen {#limitations-best-practices}

* [!DNL Experience Manager] beperkt de verwerking van bedrijfsmiddelen tot 300 verzoeken per minuut per omgeving en 700 verzoeken per minuut per organisatie.
* Bestandsgrootte is beperkt tot 4 GB voor [!DNL Adobe Photoshop] API-bewerkingen en 1 GB voor [!DNL Adobe Lightroom] bewerkingen.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Elementmicroservices configureren en gebruiken via verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).
>* [Integreren [!DNL Experience Manager] with [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [Inname en verwerking van bedrijfsmiddelen met asset microservices: een overzicht](/help/assets/asset-microservices-overview.md).
