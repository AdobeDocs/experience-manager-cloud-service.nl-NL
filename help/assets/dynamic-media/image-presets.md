---
title: Dynamische voorinstellingen voor mediaafbeeldingen toepassen
description: Leer hoe u voorinstellingen voor afbeeldingen kunt toepassen in Dynamische media.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: ad21b52e-594f-4421-9b5a-2382d032ec5a
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---

# Dynamische voorinstellingen voor mediaafbeeldingen toepassen {#applying-image-presets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Met Voorinstellingen voor afbeeldingen kunnen elementen dynamisch afbeeldingen van verschillende grootten, indelingen of andere afbeeldingseigenschappen leveren. U kunt een voorinstelling kiezen wanneer u afbeeldingen exporteert om deze opnieuw op te maken volgens de specificaties die de beheerder heeft aangegeven.

Daarnaast kunt u een voorinstelling voor een afbeelding kiezen die reageert (aangeduid met de knop **[!UICONTROL RESS]** nadat u deze hebt geselecteerd).

[ de Beheerders kunnen beeld tot stand brengen en vormen vooraf instelt ](managing-image-presets.md).

>[!NOTE]
>
>Slimme beeldbewerking werkt met uw bestaande voorinstellingen voor afbeeldingen. Het gebruikt intelligentie bij de laatste milliseconde van levering om beelddossiergrootte verder te verminderen die op browser of netwerkverbindingssnelheid wordt gebaseerd. Zie [ Slimme Beeldvorming ](imaging-faq.md) voor meer informatie.

U kunt een voorinstelling voor afbeeldingen op elk gewenst moment op een afbeelding toepassen.

**om het Dynamische Beeld van Media toe te passen vooraf instelt:**

1. Open het element en selecteer in de linkertrack de vervolgkeuzelijst en selecteer vervolgens **[!UICONTROL Renditions]** .

   >[!NOTE]
   >
   >* Statische vertoningen worden weergegeven in de bovenste helft van het epaan. Dynamische uitvoeringen worden weergegeven in de onderste helft. Alleen bij dynamische uitvoeringen kunt u de URL gebruiken om de afbeelding weer te geven. De knop **[!UICONTROL URL]** wordt alleen weergegeven als u een dynamische uitvoering selecteert. De knop **[!UICONTROL RESS]** wordt alleen weergegeven als u een voorinstelling voor een responsieve afbeelding selecteert.
   >
   >* Het systeem toont talrijke vertoningen wanneer u **[!UICONTROL Renditions]** in de mening van het Detail van activa selecteert. U kunt het aantal weergegeven voorinstellingen verhogen. Zie [ Verhoogend het aantal beeld vooraf instelt dat vertoning ](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).

   ![ chlimage_1-208 ](assets/chlimage_1-208.png)

1. Voer een van de volgende handelingen uit:

   * Selecteer een dynamische vertoning om een voorvertoning van de voorinstelling weer te geven.
   * Selecteer **[!UICONTROL URL]** , **[!UICONTROL Embed]** of **[!UICONTROL RESS]** om het pop-upvenster weer te geven.

   >[!NOTE]
   >
   >Als de activa *en* vooraf ingesteld beeld nog niet worden gepubliceerd, is de **[!UICONTROL URL]** knoop (of knopen URL en RESS, indien van toepassing) niet beschikbaar.
   >
   >Afbeeldingsvoorinstellingen worden automatisch gepubliceerd op een Dynamic Media S7-server.
