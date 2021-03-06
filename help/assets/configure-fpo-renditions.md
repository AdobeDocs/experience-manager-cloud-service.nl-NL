---
title: Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign
description: Genereer FPO-uitvoeringen van nieuwe en bestaande elementen met gebruik van de Experience Manager Assets-workflow en ImageMagick.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
exl-id: 869c1c34-6287-4d62-bb7a-aa4df580ac0e
source-git-commit: 7cc0bd5bbd51edb6f3bc2cfcccfa0a35a0d7a790
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign {#fpo-renditions}

Wanneer grote activa van de Experience Manager in Adobe InDesign documenten worden geplaatst, moet een creatieve beroeps op lange termijn wachten [een element plaatsen](https://helpx.adobe.com/indesign/using/placing-graphics.html). Ondertussen wordt de gebruiker verhinderd InDesign te gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in InDesign-documenten plaatsen, zodat deze beginnen. Wanneer de uiteindelijke uitvoer vereist is, bijvoorbeeld voor drukwerk- en publicatieworkflows, vervangen de oorspronkelijke elementen met volledige resolutie de tijdelijke uitvoering op de achtergrond. Deze asynchrone update op de achtergrond versnelt het ontwerpproces om de productiviteit te verbeteren en belemmert het creatieve proces niet.

Elementen bieden uitvoeringen die alleen voor plaatsing (FPO) worden gebruikt. Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding. Als een FPO-uitvoering niet beschikbaar is voor een element, gebruikt Adobe InDesign in plaats daarvan het oorspronkelijke element. Dit fallback-mechanisme zorgt ervoor dat de creatieve workflow zonder onderbrekingen doorgaat.

Experience Manager as a Cloud Service biedt mogelijkheden voor de native asset-processing in de cloud om de FPO-uitvoeringen te genereren. Gebruik asset microservices voor het genereren van vertoningen. U kunt het genereren van vertoningen configureren van nieuw geüploade elementen en van de elementen in de Experience Manager.

Hier volgen de stappen voor het genereren van FPO-uitvoeringen:

1. [Een verwerkingsprofiel maken](#create-processing-profile).

1. Experience Manager configureren om dit profiel te gebruiken [nieuwe elementen verwerken](#generate-renditions-of-new-assets).
1. Profielen gebruiken voor [bestaande elementen verwerken](#generate-renditions-of-existing-assets).

## Een verwerkingsprofiel maken {#create-processing-profile}

Als u FPO-uitvoeringen wilt genereren, maakt u een **[!UICONTROL Processing Profile]**. De profielen gebruiken cloud-native asset-microservices voor verwerking. Zie voor instructies [verwerkingsprofielen maken voor assetmicroservices](asset-microservices-configure-and-use.md).

Selecteren **[!UICONTROL Create FPO Rendition]** om FPO-uitvoering te genereren. Klik optioneel op **[!UICONTROL Add New]** om nog een renderinstelling aan hetzelfde profiel toe te voegen.

![create-processing-profile-fpo-renditions](assets/create-processing-profile-fpo-renditions.png)

## Uitvoeringen van nieuwe elementen genereren {#generate-renditions-of-new-assets}

Als u FPO-uitvoeringen van nieuwe elementen wilt genereren, past u de **[!UICONTROL Processing Profile]** naar de map in mapeigenschappen. Klik op de pagina Eigenschappen van een map op **[!UICONTROL Asset Processing]** selecteert u de **[!UICONTROL FPO profile]** als **[!UICONTROL Processing Profile]** en sla de wijzigingen op. Alle nieuwe elementen die naar de map zijn geüpload, worden met dit profiel verwerkt.

![add-fpo-rendition](assets/add-fpo-rendition.png)


## Uitvoeringen van bestaande elementen genereren {#generate-renditions-of-existing-assets}

Selecteer de elementen en voer de volgende stappen uit om uitvoeringen te genereren.

![fpo-existing-asset-reprocess](assets/fpo-existing-asset-reprocess.gif)


## FPO-uitvoeringen weergeven {#view-fpo-renditions}

U kunt de gegenereerde FPO-uitvoeringen controleren nadat de workflow is voltooid. Klik in de Experience Manager Assets-gebruikersinterface op het element om een grote voorvertoning te openen. Open het linkerspoor en selecteer **[!UICONTROL Renditions]**. U kunt ook de sneltoets gebruiken `Alt + 3` wanneer de voorvertoning is geopend.

Klikken **[!UICONTROL FPO rendition]** om de voorvertoning te laden. U kunt ook met de rechtermuisknop op de vertoning klikken en deze opslaan in uw bestandssysteem. Controleren op beschikbare uitvoeringen in de linkertrack.

![rendition_list](assets/list-renditions.png)
