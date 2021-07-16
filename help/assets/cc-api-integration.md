---
title: Inhoud automatiseren voor Creative Cloud-integratie
description: Variaties van elementen genereren met Creative Cloud-integratie
contentOwner: AG
feature: Uploaden, Asset Processing, Publiceren, Asset compute Microservices, Workflow
role: User,Admin
source-git-commit: 997f292be2498624c5218addd61ec40727eb48bc
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---


# Variaties van elementen genereren met behulp van [!DNL Adobe Creative Cloud]-integratie {#content-automation}

Inhoudsautomatisering-invoegtoepassing integreert [!DNL Adobe Experience Manager Assets as a Cloud Service]- en [!DNL Adobe Creative Cloud]-API&#39;s om uw elementen op schaal creatief te verwerken. [!DNL Experience Manager] gebruikt cloudgebaseerde  [asset-](/help/assets/asset-microservices-overview.md) microservices om de  [!DNL Adobe Creative Cloud] functies te gebruiken en het maken van middelen en het verwerken van media te automatiseren.

Als u elementen wilt bewerken in [!DNL Adobe Photoshop] en [!DNL Adobe Lightroom], hoeft u geen elementen te downloaden van [!DNL Experience Manager Assets], deze te bewerken en opnieuw te uploaden. U hoeft alleen een verwerkingsprofiel te maken en te configureren in [!DNL Experience Manager], het profiel toe te passen op een map en de middelen naar de map te uploaden. De geüploade elementen worden opnieuw verwerkt op basis van de verwerkingsprofielen en deze elementen kunnen variëren. De consequente en moeiteloze bulkverwerking bespaart handmatige inspanningen en verhoogt de snelheid van de inhoud, ook zonder de behoefte aan uitstekende creatieve vaardigheden. Ook, kunnen de ontwikkelaars en de partners de activa microservices met directe toegang tot deze APIs uitbreiden en douanelogica omvatten.
Gebruikers kunnen verwerkingsprofielen maken om de volgende creatieve bewerkingen op hun middelen te automatiseren:

* **Automatische tint**: Hierbij wordt gebruikgemaakt van kunstmatige intelligentie om de inhoud van de afbeelding te analyseren en op intelligente wijze licht- en kleurcorrecties toe te passen op basis van de unieke kenmerken van de afbeelding.
* **Automatisch rechtop**: Gebruikt kunstmatige intelligentie om de inhoud van het beeld te analyseren en scheefgetrokken perspectief in beelden te verbeteren. Bijvoorbeeld om niveauhorizonten te maken.
* **Lightroom-voorinstellingen**: Hiermee past u een door de gebruiker gedefinieerde vormgeving toe op afbeeldingen voor een consistente weergave met behulp van aangepaste voorinstellingen.
* **Knipsel** afbeelding: Gebruikt kunstmatige intelligentie om selectie rond aliente voorwerpen tot stand te brengen en achtergrond met één enkele bevel te verwijderen.
* **Afbeeldingsmasker**: Gebruikt kunstmatige intelligentie om masker rond aliente voorwerpen met één enkele bevel tot stand te brengen.
* **Photoshop-handelingen**: Hiermee wordt een reeks taken (in Photoshop) toegepast op een bestand of een groep bestanden.
* **Vervanging** slim object: Hiermee past u de weergave op schaal aan door afbeeldingen om te wisselen met behoud van alle effecten en aanpassingen die in een PSD-bestand zijn toegepast.

## Een verwerkingsprofiel gebruiken om uw creatieve middelen bulksgewijs te bewerken {#process-assets}

Ga als volgt te werk als u verwerkingsprofielen wilt gebruiken om automatisch variaties te maken:

1. Neem contact op met de [klantenservice Adobe](https://experienceleague.adobe.com/#support) om de licentie te ontvangen.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**.

1. Selecteer **[!UICONTROL Create]** en geef een **[!UICONTROL Name]** op.

1. Selecteer de tab **[!UICONTROL Creative]**, geef de uitvoermap op en selecteer **[!UICONTROL Add New]** om een creatieve configuratie toe te voegen.

1. Geef **[!UICONTROL Rendition Name]** (of uitvoernaam), **[!UICONTROL Extension]** (of bestandstype), selecteer **[!UICONTROL Quality]** (of uitvoerparameters), selecteer Includes and Excludes MIME type lists (of filter invoerelement) en selecteer de vereiste creatieve bewerking.
   ![tabblad Creatief in verwerkingsprofiel](assets/creative-processing-profile.png)

1. Sommige bewerkingen vereisen extra parameters (element). Geef indien nodig waarden op voor deze extra parameters.

1. Voeg meer creatieve bewerkingen toe als onderdeel van hetzelfde verwerkingsprofiel of sla het profiel op.

1. Pas het verwerkingsprofiel toe op een map. Selecteer **[!UICONTROL Asset Processing]** op de pagina **[!UICONTROL Properties]** van een map en selecteer het verwerkingsprofiel dat u wilt toepassen.

Nadat het verwerkingsprofiel is toegepast op een DAM-map, worden naast de standaardverwerking ook de gedefinieerde bewerkingen uitgevoerd door alle elementen die in deze map zijn geüpload of bijgewerkt. De submappen overerven dezelfde profielen als die zijn toegepast op de bovenliggende mappen. Gebruikers kunnen deze overerving overschrijven.

Als u de bestaande elementen wilt verwerken, selecteert u de elementen, selecteert u **[!UICONTROL Reprocess]** en selecteert u vervolgens het gewenste verwerkingsprofiel.

## Tips en beperkingen {#limitations-best-practices}

* [!DNL Experience Manager] beperkt de verwerking van bedrijfsmiddelen tot 300 verzoeken per minuut per omgeving en 700 verzoeken per minuut per organisatie.
* De bestandsgrootte is beperkt tot 4 GB voor [!DNL Adobe Photoshop] API-bewerkingen en 1 GB voor [!DNL Adobe Lightroom]-bewerkingen.

>[!MORELIKETHIS]
>
>* [Configureer en gebruik de assetmicroservices via verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] Integreren met [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [Inname en verwerking van bedrijfsmiddelen met asset microservices: Een overzicht](/help/assets/asset-microservices-overview.md).

