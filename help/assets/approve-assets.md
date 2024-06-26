---
title: Elementen in Experience Manager goedkeuren
description: Leer hoe u middelen kunt goedkeuren in [!DNL Experience Manager].
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# Toestaan dat middelen in [!DNL Experience Manager]

Merkbeheerders en marketeers houden strikte controle over merkmiddelen. Alleen goedgekeurde en nieuwste versie van het middel is beschikbaar voor gebruik, zodat alle kanalen en toepassingen consistent blijven.

U kunt in AEM Assets middelen goedkeuren om het beheer van bedrijfsmiddelen te stroomlijnen, zodat u verzekerd bent van een gecontroleerd en efficiënt proces voor het verwerken van bedrijfsmiddelen.

## Voordat u begint {#pre-requisites}

U moet toegang hebben tot AEM Assets as a Cloud Service en machtigingen om de **[!UICONTROL Review Status]** eigenschap voor een element.

## Configuratie

Voordat u een element kunt goedkeuren, moet u het toepasselijke metagegevensschema in de beheerweergave eenmalig bijwerken. U kunt deze configuratie voor de weergave Assets overslaan. Voer de volgende stappen uit om het metagegevensschema te configureren:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. Selecteer het toepasselijke metagegevensschema en klik op **[!UICONTROL Edit]**. <br>De **[!UICONTROL Metadata Schema Form Editor]** wordt geopend met de **[!UICONTROL Basic]** gemarkeerd.
1. Omlaag schuiven en klikken **[!UICONTROL Review Status]**.
1. Klik op de knop **[!UICONTROL Rules]** aan de rechterkant van het deelvenster.
1. Uitschakelen **[!UICONTROL Disable edit]** en klik op **[!UICONTROL Save]**.
Als u het bezit moet bekijken dat **[!UICONTROL Review Status]** veld is toegewezen aan, navigeer naar **[!UICONTROL Settings]** en bekijk de `./jcr:content/metadata/dam:status` waarde in de **[!UICONTROL Map to property]** veld.

>[!NOTE]
>
>Als uw elementen of mappen een ander standaardschema hebben, moet u deze update uitvoeren in dat specifieke schema.

## Elementen goedkeuren {#approve-assets}

U kunt elementen goedkeuren in beide [!DNL Experience Manager] en [!DNL Experience Manager Assets]. Elementen goedkeuren in [!DNL Experience Manager]Voer de volgende stappen uit:

1. Selecteer de elementen en klik op **[!UICONTROL Properties]** in het bovenste deelvenster.
1. In de **[!UICONTROL Basic]** tab, omlaag schuiven naar **[!UICONTROL Review Status]**.
1. Wijzig de revisiestatus in **[!UICONTROL Approved]**.
   ![afbeelding](/help/assets/assets/approve-old-ui.png)
1. Klik op **[!UICONTROL Save & Close]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   Op dezelfde manier kunt u elementen goedkeuren met de opdracht [nieuwe Assets-weergave](/help/assets/manage-organize-assets-view.md).

## Elementen in bulk goedkeuren {#bulk-approve-assets}

Stroomlijn uw workflow door snel meerdere middelen tegelijk goed te keuren. U kunt in bulk goedgekeurde activa goedkeuren om het goedkeuringsproces te versnellen, tijd te besparen en productiviteit te verbeteren.
<br>Ga als volgt te werk om bulkmiddelen in goed te keuren [!DNL Experience Manager]:

1. Maak een map in de ontwerpomgeving (https://author-pXXX-eYYY.adobeaemcloud.com). Vervangen _XXX_ met uw programma-id en _JJJ_ met de milieu-id van de Experience Manager.
1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]**.
1. Klikken **[!UICONTROL Create]** in de rechterbovenhoek van de pagina.
1. Een profieltitel toevoegen en klikken **[!UICONTROL Create]**. Het metagegevensprofiel is gemaakt.
1. Selecteer het nieuwe metagegevensprofiel en klik op **[!UICONTROL Edit _e)_]**. <br>De **[!UICONTROL Edit Metadata Profile]** formulier wordt geopend met de **[!UICONTROL Basic]** gemarkeerd.
1. Sleep een **[!UICONTROL Single Line Text Field]** van de **[!UICONTROL Build Form]** in de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het dialoogvenster **[!UICONTROL Settings]** paneel:
   1. Wijzig de **[!UICONTROL Field Label]** tot _Goedgekeurde Assets_.
   1. Werk de **[!UICONTROL Map to property]** tot _./jcr:content/metadata/dam:status_.
   1. De standaardwaarde wijzigen in _goedgekeurd_.

1. Klik op **[!UICONTROL Save]**.
1. In de **[!UICONTROL Metadata Profiles]** selecteert u het nieuwe metagegevensprofiel.
1. Klikken **[!UICONTROL Apply Metadata Profile to Folder(s)]** in de bovenste actiebalk.
1. Selecteer de map(pen) die u wilt goedkeuren en klik op **[!UICONTROL Apply]**.
   <br> De machtiging voor de gehele map wordt ingesteld op goedkeuring en alle middelen die naar deze map worden geüpload, worden automatisch goedgekeurd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Met deze methode worden de nieuwe elementen in de map goedgekeurd. Voor bestaande elementen in de map moet u deze handmatig selecteren en goedkeuren. <br> U kunt ook de opdracht **[!UICONTROL Reprocess]** om de wijzigingen van het metagegevensprofiel toe te passen op oudere elementen.

En als u een grote hoeveelheid gegevens in een map in de Assets-weergave wilt selecteren, gaat u als volgt te werk:

1. Selecteer de elementen en klik op **[!UICONTROL Bulk Metadata Edit]**.

1. Selecteren **[!UICONTROL Approved]** in de **[!UICONTROL Status]** veld beschikbaar in [!UICONTROL Properties] in het rechterdeelvenster.

1. Klik op **[!UICONTROL Save]**.

## Leverings-URL kopiëren voor goedgekeurde elementen {#copy-delivery-url-approved-assets}

De leverings-URL voor alle goedgekeurde middelen in de opslagplaats is beschikbaar als u [!UICONTROL Dynamic Media with OpenAPI capabilities] ingeschakeld op uw AEM as a Cloud Service-exemplaar.

Om levering URL voor een goedgekeurd middel binnen de bewaarplaats te kopiëren:

1. Selecteer het element en klik op **[!UICONTROL Details]**.

1. Klik op het pictogram Uitvoeringen in het rechterdeelvenster.

1. Selecteren **[!UICONTROL Dynamic Media with OpenAPI]** beschikbaar in het **[!UICONTROL Dynamic]** sectie.

1. Klikken **[!UICONTROL Copy URL]** om de leverings-URL van het element te kopiëren.
   ![leverings-URL kopiëren](/help/assets/assets/copy-delivery-url.png)

   >[!NOTE]
   >
   >De optie voor het kopiëren van de URL voor levering voor goedgekeurde middelen is alleen beschikbaar in de weergave Assets.

