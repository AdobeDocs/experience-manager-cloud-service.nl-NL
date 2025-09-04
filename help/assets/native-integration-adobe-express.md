---
title: Native AEM Assets-integratie met Adobe Express
description: Dankzij de native integratie van AEM Assets met Adobe Express hebt u rechtstreeks vanuit de Adobe Express-gebruikersinterface toegang tot de middelen die in AEM Assets zijn opgeslagen.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: 200d0ae5546b5d50e8bad590f496b0fab62f0fe3
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Native integratie met Adobe Express {#native-integration-adobe-express}

AEM Assets kan op een native manier worden geïntegreerd met Adobe Express, waardoor u rechtstreeks vanuit de Adobe Express-gebruikersinterface toegang hebt tot de elementen die in AEM Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats. De integratie biedt de volgende belangrijke voordelen:

* Meer hergebruik van inhoud door nieuwe elementen te bewerken en op te slaan in AEM.

* Lagere algemene tijd en moeite om nieuwe elementen te maken of nieuwe versies van bestaande elementen te maken.

## Vereisten {#prerequisites}

Toegang tot Adobe Express en ten minste één omgeving in AEM Assets. De omgeving kan elk van de opslagruimten in Assets as a Cloud Service of Assets Essentials zijn.

## AEM Assets gebruiken in Adobe Express-editor {#use-aem-assets-in-express}

Voer de volgende stappen uit om AEM Assets in Adobe Express Editor te gaan gebruiken:

1. Open de Adobe Express-webtoepassing.

2. Open een nieuw leeg canvas door een nieuwe sjabloon of een project te laden of door een element te maken.

3. Klik op **[!UICONTROL Assets]** in het navigatievenster aan de linkerkant. In Adobe Express wordt de lijst met opslagplaatsen weergegeven die u kunt openen, samen met de lijst met elementen en mappen die beschikbaar zijn op hoofdniveau.

4. Blader door of zoek naar middelen in uw repository om ze naar het canvas te slepen. U kunt elementen filteren met behulp van verschillende beschikbare filters, zoals bestandstype, MIME-type en afmetingen.

   >[!NOTE]
   >
   >Filteren op dimensie is niet van toepassing op video&#39;s.

   ![ omvat activa van Assets toe:voegen-op ](assets/adobe-express-native-integration.png)


## Adobe Express-projecten opslaan in AEM Assets {#save-express-projects-in-assets}

Nadat u de juiste wijzigingen hebt aangebracht in het Express-canvas, kunt u het opslaan in de AEM Assets-opslagruimte.

1. Klik op **[!UICONTROL Share]** om het dialoogvenster **[!UICONTROL Share]** te openen.

   ![ sparen activa in AEM ](assets/adobe-express-share.png)

2. Van de **[!UICONTROL Recommended]** sectie in de juiste ruit, uitgezochte **AEM Assets**. Adobe Express geeft het dialoogvenster voor uploaden weer.

   ![ sparen activa in AEM ](assets/adobe-express-aem.png)

3. Selecteer of **Huidige Pagina** of **Alle Pagina&#39;s**. Geef een naam en indeling op voor de elementen die u wilt exporteren. U kunt de inhoud van het canvas exporteren in de indelingen PNG, JPEG, PDF, MP4, MP4+PNG of MP4+JPEG. De opmaak wordt automatisch aangepast op basis van de elementen op de canvaspagina(&#39;s).
Het selecteren van **Huidige Pagina** slaat de activa op uw huidige pagina aan uw bestemmingsomslag op. Als u **Alle Pagina&#39;s** selecteert en het uitvoerformaat niet PDF is, worden alle canvaspagina&#39;s bewaard als afzonderlijke dossiers in een nieuwe omslag binnen uw bestemmingsomslag. Als de exportindeling PDF is, worden alle canvaspagina&#39;s als één PDF-bestand opgeslagen in de doelmap.

4. Klik het omslagpictogram onder **Omslag van de Bestemming** om een plaats te selecteren en de activa te bewaren.

   ![ sparen activa in AEM ](/help/assets/assets/page-selection-and-destination-folder.svg)

5. Facultatief: U kunt campagnemetagegevens voor uw toevoegen gebruikend het **project of campagnenaam** gebied. U kunt een bestaande naam gebruiken of een nieuwe naam maken. U kunt meerdere project- of campagnenamen definiëren voor het uploaden. Als u de naam wilt registreren, typt u gewoon de naam en klikt u op Enter.
Het wordt aanbevolen dat Adobe waarden opgeeft in de rest van de velden en een verbeterde zoekervaring maakt voor uw geüploade elementen.

6. Definieer ook waarden voor de velden **[!UICONTROL Keywords]** en **[!UICONTROL Channels]** .

7. Klik op **[!UICONTROL Upload]** om de elementen te uploaden naar AEM Assets.

<table> 
    <tbody>
     <tr>
      <th><strong>Ondersteunde indelingen</strong></th>
      <th><strong>Grootte</strong></th>
     </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
        <td> 8000 x 8000 pixels, maximaal 40 MB</td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
        <td> 8000 x 8000 pixels, maximaal 40 MB</td>
    </tr>
    <tr>
        <td>[!UICONTROL SVG]</td>
        <td> Maximaal 250 kB</td>
    </tr>
    <tr>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
        <td> 3840 x 3840 pixels, maximaal 200 MB</td>
    </tr>
    </tbody>
</table>

## Beperkingen {#limitations}

1. Voor het importeren en exporteren is MP4 het ondersteunde videobestandstype.

2. Voor **MP4 videoinvoer**, worden de video&#39;s met transparante achtergronden (alpha- kanaal) niet gesteund.
   <!--
   1. The maximum file size supported is 200 MB. If this limit exceeds, an alert message displays.
   2. The maximum supported resolution is 3840 X 3840 pixels.
   3. Videos with transparent backgrounds (alpha channel) are not supported.
   -->

3. Voor **MP4 videouitvoer**, is de maximumgesteunde dossiergrootte 200 MB. Als deze limiet wordt overschreden, wordt in een waarschuwing aanbevolen de video te verkleinen tot 200 MB of minder, of deze handmatig te uploaden naar de AEM Assets-doelmap nadat deze is gedownload.



