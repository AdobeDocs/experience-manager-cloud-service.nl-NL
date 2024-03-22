---
title: Native AEM Assets-integratie met Adobe Express
description: Dankzij de native integratie van AEM Assets met Adobe Express hebt u rechtstreeks vanuit de gebruikersinterface van de Adobe Express toegang tot de elementen die in AEM Assets zijn opgeslagen.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
source-git-commit: 8bbf9a2ba8f708a5a03d11bc0388d39b32d4c7b3
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Native integratie met Adobe Express {#native-integration-adobe-express}

AEM Assets integreert native met Adobe Express, waardoor u rechtstreeks vanuit de gebruikersinterface van de Adobe Express toegang hebt tot de elementen die in AEM Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats. De integratie biedt de volgende belangrijke voordelen:

* Grotere hergebruik van inhoud door nieuwe elementen te bewerken en op te slaan in AEM.

* Lagere algemene tijd en moeite om nieuwe elementen te maken of nieuwe versies van bestaande elementen te maken.

## Vereisten {#prerequisites}

Rechten op toegang tot Adobe Express en ten minste één omgeving in AEM Assets. De omgeving kan elk van de opslagplaatsen binnen as a Cloud Service activa of Assets Essentials zijn.


## AEM Assets gebruiken in Adobe Express-editor {#use-aem-assets-in-express}

Voer de volgende stappen uit om AEM Assets te gaan gebruiken in de Adobe Express-editor:

1. Open de Adobe Express webtoepassing.

1. Open een nieuw leeg canvas door een nieuwe sjabloon of een project te laden of door een element te maken.

1. Klikken **[!UICONTROL Assets]** beschikbaar in het linkernavigatiegebied. Adobe Express geeft de lijst met opslagplaatsen weer die u mag openen, samen met de lijst met elementen en mappen die beschikbaar zijn op hoofdniveau.

1. Blader door of zoek naar middelen in uw repository om ze naar het canvas te slepen. U kunt elementen filteren met behulp van verschillende beschikbare filters, zoals bestandstype, MIME-type en afmetingen.

   ![Elementen opnemen uit de invoegtoepassing Elementen](assets/adobe-express-native-integration.png)


## Adobe Express-projecten opslaan in AEM Assets {#save-express-projects-in-assets}

Nadat u de juiste wijzigingen hebt aangebracht in het Express-canvas, kunt u het opslaan in de AEM Assets-opslagruimte.

1. Klikken **[!UICONTROL Share]** om de **[!UICONTROL Share]** in.

   ![Elementen opslaan in AEM](assets/adobe-express-share.png)

1. Selecteren **[!UICONTROL AEM Assets]** van de **[!UICONTROL Storage]** in het rechterdeelvenster. Met Adobe Express wordt het dialoogvenster voor uploaden weergegeven.
1. Geef een naam en indeling voor het element op. U kunt de inhoud van het canvas opslaan in de indeling PNG of JPEG.

1. Klik op het mappictogram naast de knop **[!UICONTROL Location]** , navigeer naar de locatie waar u het element wilt opslaan en klik op **[!UICONTROL Select]**. De naam van de map wordt weergegeven in de **[!UICONTROL Location]** veld.

   ![Elementen opslaan in AEM](assets/adobe-express-upload.png)

1. Optioneel: u kunt campagnemetagegevens voor uploaden toevoegen met de opdracht **[!UICONTROL Project or campaign name]** veld. U kunt een bestaande naam gebruiken of een nieuwe naam maken. U kunt meerdere project- of campagnenamen definiëren voor het uploaden. Terwijl u een naam typt, klikt u ergens anders in het dialoogvenster of drukt u op de knop `,` (Komma) om de naam te registreren.

   Als beste praktijken, beveelt de Adobe het specificeren van waarden in de rest gebieden evenals het leidt tot een verbeterde onderzoekservaring voor uw geupload activa.
1. Definieer op dezelfde manier waarden voor de **[!UICONTROL Keywords]** en **[!UICONTROL Channels]** velden.

1. Klikken **[!UICONTROL Upload]** om het middel te uploaden naar AEM Assets.




## Beperkingen {#limitations}

Er is een bekende fout opgetreden bij sommige gebruikers die toegang hebben tot meer dan één opslagplaats voor middelen wanneer ze een document opslaan met elementen van meerdere opslagplaatsen.
