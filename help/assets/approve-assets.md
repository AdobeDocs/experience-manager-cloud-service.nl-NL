---
title: Elementen goedkeuren in Experience Manager
description: Leer hoe te om activa in  [!DNL Experience Manager] goed te keuren.
role: User
exl-id: fe61a0f1-94d3-409a-acb9-195979668c25
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 0%

---

# Elementen goedkeuren in [!DNL Experience Manager]

Merkbeheerders en marketeers houden strikte controle over merkmiddelen. Alleen goedgekeurde en nieuwste versie van het middel is beschikbaar voor gebruik, zodat alle kanalen en toepassingen consistent blijven.

U kunt in AEM Assets middelen goedkeuren om het beheer van bedrijfsmiddelen te stroomlijnen, zodat u verzekerd bent van een gecontroleerd en efficiënt proces voor het verwerken van bedrijfsmiddelen.

## Voordat u begint {#pre-requisites}

U moet toegang hebben tot AEM Assets as a Cloud Service en machtigingen hebben om de eigenschap **[!UICONTROL Review Status]** voor een element te bewerken.

## Configuratie

Voordat u een element kunt goedkeuren, moet u het toepasselijke metagegevensschema in de beheerweergave eenmalig bijwerken. U kunt deze configuratie voor de weergave Assets overslaan. Voer de volgende stappen uit om het metagegevensschema te configureren:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .
1. Selecteer het toepasselijke metagegevensschema en klik op **[!UICONTROL Edit]** . <br> **[!UICONTROL Metadata Schema Form Editor]** opent met het **[!UICONTROL Basic]** benadrukte lusje.
1. Schuif omlaag en klik op **[!UICONTROL Review Status]** .
1. Klik op de tab **[!UICONTROL Rules]** aan de rechterkant van het deelvenster.
1. Schakel **[!UICONTROL Disable edit]** uit.
Als u de eigenschap wilt weergeven waaraan het veld **[!UICONTROL Review Status]** is toegewezen, navigeert u naar de tab **[!UICONTROL Settings]** en bekijkt u de waarde `./jcr:content/metadata/dam:status` in het veld **[!UICONTROL Map to property]** .
1. Sleep een **[!UICONTROL Dropdown]** -veld van de sectie **[!UICONTROL Build Form]** naar de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in _Doel van de Goedkeuring_.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:activationTarget_.
   1. Voeg de opties toe met `contenthub` en `delivery` als optiewaarden.

   >[!NOTE]
   >
   >Wanneer u het goedkeuringsdoel selecteert als Content Hub in de Assets-weergave, worden de elementen in Content Hub beschikbaar gesteld voor de gebruikers die deel uitmaken van dezelfde organisatie. Wanneer u goedkeuringsdoel als Levering selecteert, zijn de activa beschikbaar aan alle gebruikers.

1. Klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Als uw elementen of mappen een ander standaardschema hebben, moet u deze update uitvoeren in dat specifieke schema.

## Elementen goedkeuren {#approve-assets}

Voer de volgende stappen uit om elementen in [!DNL Experience Manager Admin view] goed te keuren:

1. Selecteer de elementen en klik op **[!UICONTROL Properties]** in het bovenste deelvenster.
1. Schuif omlaag naar **[!UICONTROL Review Status]** op het tabblad **[!UICONTROL Basic]** .
1. Wijzig de revisiestatus in **[!UICONTROL Approved]** .
   ![afbeelding](/help/assets/assets/approve-old-ui.png)
1. Klik op **[!UICONTROL Save & Close]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   Op dezelfde manier kunt u activa goedkeuren gebruikend de [ nieuwe mening van Assets ](/help/assets/manage-organize-assets-view.md).

## Elementen in bulk goedkeuren {#bulk-approve-assets}

Stroomlijn uw workflow door snel meerdere middelen tegelijk goed te keuren. U kunt in bulk goedgekeurde activa goedkeuren om het goedkeuringsproces te versnellen, tijd te besparen en productiviteit te verbeteren.
<br> volg deze stappen om bulkactiva in [!DNL Experience Manager Admin view] goed te keuren:

1. Maak een map in de ontwerpomgeving (https://author-pXXX-eYYY.adobeaemcloud.com). Vervang _XXX_ met uw programmaidentiteitskaart en _JJJ_ met milieuidentiteitskaart van Experience Manager.
1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** .
1. Klik op **[!UICONTROL Create]** rechtsboven op de pagina.
1. Voeg een profieltitel toe en klik op **[!UICONTROL Create]** . Het metagegevensprofiel is gemaakt.
1. Selecteer het nieuwe metagegevensprofiel en klik op **[!UICONTROL Edit _(e)_]** . <br> Het **[!UICONTROL Edit Metadata Profile]** -formulier wordt geopend met de tab **[!UICONTROL Basic]** gemarkeerd.
1. Sleep een **[!UICONTROL Single Line Text Field]** van de sectie **[!UICONTROL Build Form]** naar de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in _Goedgekeurde Assets_.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:status_.
   1. Verander de Standaardwaarde in _goedgekeurd_.

1. Sleep een **[!UICONTROL Dropdown]** -veld van de sectie **[!UICONTROL Build Form]** naar de rechterkant van de sectie Metagegevens in het formulier.
1. Klik op het veld dat u zojuist hebt toegevoegd en voer de volgende updates uit in het deelvenster **[!UICONTROL Settings]** :
   1. Verander **[!UICONTROL Field Label]** in _Doel van de Goedkeuring_.
   1. Werk **[!UICONTROL Map to property]** aan _bij./jcr:content/metadata/dam:activationTarget_.
   1. Voeg de opties toe met `contenthub` en `delivery` als optiewaarden.

   >[!NOTE]
   >
   >Wanneer u het goedkeuringsdoel selecteert als Content Hub in de Assets-weergave, worden de elementen in Content Hub beschikbaar gesteld voor de gebruikers die deel uitmaken van dezelfde organisatie. Wanneer u goedkeuringsdoel als Levering selecteert, zijn de activa beschikbaar aan alle gebruikers.
1. Klik op **[!UICONTROL Save]**.
1. Selecteer op de pagina **[!UICONTROL Metadata Profiles]** het nieuwe metagegevensprofiel.
1. Klik op **[!UICONTROL Apply Metadata Profile to Folder(s)]** in de bovenste actiebalk.
1. Selecteer de map(pen) die u wilt goedkeuren en klik op **[!UICONTROL Apply]** .
   <br> De machtiging voor de gehele map wordt ingesteld op goedkeuring en alle middelen die naar deze map worden geüpload, worden automatisch goedgekeurd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Met deze methode worden de nieuwe elementen in de map goedgekeurd. Voor bestaande elementen in de map moet u deze handmatig selecteren en goedkeuren. <br> U kunt ook de optie **[!UICONTROL Reprocess]** gebruiken om de wijzigingen van het metagegevensprofiel toe te passen op oudere elementen.

En als u een grote hoeveelheid gegevens in een map in de Assets-weergave wilt selecteren, gaat u als volgt te werk:

1. Selecteer de elementen en klik op **[!UICONTROL Bulk Metadata Edit]** .

1. Selecteer **[!UICONTROL Approved]** in het **[!UICONTROL Status]** -veld dat beschikbaar is in de sectie [!UICONTROL Properties] in het rechterdeelvenster.

   Als u de status als `Approved` selecteert, en als [ Dynamische Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) of [ Content Hub ](/help/assets/product-overview.md), of allebei voor uw Experience Manager Assets worden toegelaten, kunt u `Delivery` bekijken en `Content Hub` opties beschikbaar op het **[!UICONTROL Approval Target]** gebied.

   * Selecteer **[!UICONTROL Delivery]** om de middelen beschikbaar te maken voor zowel Dynamic Media met OpenAPI-mogelijkheden als Content Hub. Als Content Hub niet is ingeschakeld, maakt u met deze optie de middelen alleen beschikbaar voor Dynamic Media met OpenAPI-mogelijkheden.
   * Selecteer **[!UICONTROL Content Hub]** om de middelen beschikbaar te maken voor Content Hub.

   ![ de status van de Goedkeuring ](/help/assets/assets/approval-status-delivery.png)

   Als u niet de standaardmeta-gegevensvorm gebruikt en niet het **[!UICONTROL Approval Target]** gebied kunt bekijken, [ geef uw meta-gegevensvorm ](/help/assets/metadata-assets-view.md#metadata-forms) uit om het **[!UICONTROL Approval for]** gebied van de beschikbare componenten aan uw meta-gegevensvorm te slepen en klik **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Als u het doel voor goedkeuring als `Content Hub` selecteert met de Assets-weergave binnen een organisatie, worden de elementen in Content Hub beschikbaar gesteld voor de gebruikers die deel uitmaken van dezelfde organisatie.

1. Klik op **[!UICONTROL Save]**.

## Leverings-URL kopiëren voor goedgekeurde elementen {#copy-delivery-url-approved-assets}

De leverings-URL voor alle goedgekeurde middelen in de opslagplaats is beschikbaar als u [!UICONTROL Dynamic Media with OpenAPI capabilities] hebt ingeschakeld voor uw AEM as a Cloud Service-instantie.

Om levering URL voor een goedgekeurd middel binnen de bewaarplaats te kopiëren:

1. Selecteer het element en klik op **[!UICONTROL Details]** .

1. Klik op het pictogram Dynamische media in het rechterdeelvenster.

1. Selecteer **[!UICONTROL Dynamic Media with OpenAPI]** beschikbaar in het deelvenster **[!UICONTROL Dynamic Media]** .

1. Klik op **[!UICONTROL Copy URL]** om de URL van de levering van het element te kopiëren.
   ![ dynamische vertoningen ](/help/assets/assets/dm-with-openapi-non-image-assets.png)

   >[!NOTE]
   >
   >De optie voor het kopiëren van de URL voor levering voor goedgekeurde middelen is alleen beschikbaar in de weergave Assets.

Voor informatie over andere vertoningen die binnen het Dynamische paneel van Media tonen, zie [ Mening en download Dynamische vertoningen van Media ](/help/assets/renditions.md#view-download-dm-renditions).
