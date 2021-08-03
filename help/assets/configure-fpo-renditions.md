---
title: Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign
description: Genereer FPO-uitvoeringen van nieuwe en bestaande elementen met behulp van de workflow voor Experience Manager Assets en ImageMagick.
contentOwner: Vishabh Gupta
role: Admin
feature: Uitvoeringen
exl-id: null
source-git-commit: 69f1ac34dc24f92cae47e1bfcffb39f6f3b03b7b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign {#fpo-renditions}

Bij het plaatsen van grote activa van Experience Manager in Adobe InDesign documenten, moet een creatieve beroeps op een aanzienlijke tijd wachten nadat zij [een activa ](https://helpx.adobe.com/indesign/using/placing-graphics.html) plaatsen. Ondertussen wordt de gebruiker verhinderd InDesign te gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in InDesign-documenten plaatsen, zodat deze beginnen. Wanneer de uiteindelijke uitvoer vereist is, bijvoorbeeld voor drukwerk- en publicatieworkflows, vervangen de oorspronkelijke elementen met volledige resolutie de tijdelijke uitvoering op de achtergrond. Deze asynchrone update op de achtergrond versnelt het ontwerpproces om de productiviteit te verbeteren en belemmert het creatieve proces niet.

Elementen bieden uitvoeringen die alleen voor plaatsing (FPO) worden gebruikt. Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding. Als een FPO-uitvoering niet beschikbaar is voor een element, gebruikt Adobe InDesign in plaats daarvan het oorspronkelijke element. Dit fallback-mechanisme zorgt ervoor dat de creatieve workflow zonder onderbrekingen doorgaat.

Experience Manager als Cloud Service biedt de mogelijkheid om eigen middelen in de cloud te verwerken om de FPO-uitvoeringen te genereren. Gebruik asset microservices voor het genereren van vertoningen. U kunt het genereren van vertoningen configureren van nieuw geüploade elementen en van de elementen in de Experience Manager.

Hier volgen de stappen voor het genereren van FPO-uitvoeringen:
1. [Maak een verwerkingsprofiel](#create-processing-profile).
1. Vorm Experience Manager om dit profiel te gebruiken om nieuwe activa [te verwerken ](#generate-renditions-of-new-assets).
1. Gebruik de profielen om bestaande elementen [te verwerken.](#generate-renditions-of-existing-assets)

## Een verwerkingsprofiel maken {#create-processing-profile}

Als u FPO-uitvoeringen wilt genereren, maakt u een **[!UICONTROL Processing Profile]**. De profielen gebruiken cloud-native asset-microservices voor verwerking. Zie [Procesprofielen maken voor de elementmicroservices](asset-microservices-configure-and-use.md) voor instructies.

Selecteer **[!UICONTROL Create FPO Rendition]** om FPO-uitvoering te genereren. Klik optioneel op **[!UICONTROL Add New]** om nog een vertoningsinstelling aan hetzelfde profiel toe te voegen.

![create-processing-profile-fpo-renditions](assets/create-processing-profile-fpo-renditions.png)

## Uitvoeringen van nieuwe elementen genereren {#generate-renditions-of-new-assets}

Als u FPO-uitvoeringen van nieuwe elementen wilt genereren, past u **[!UICONTROL Processing Profile]** toe op de map in mapeigenschappen. Klik op **[!UICONTROL Asset Processing]** op de pagina Eigenschappen van een map, selecteer **[!UICONTROL FPO profile]** als een **[!UICONTROL Processing Profile]** en sla de wijzigingen op. Alle nieuwe elementen die naar de map zijn geüpload, worden met dit profiel verwerkt.

![add-fpo-rendition](assets/add-fpo-rendition.png)


## Uitvoeringen van bestaande elementen genereren {#generate-renditions-of-existing-assets}

Selecteer de elementen en voer de volgende stappen uit om uitvoeringen te genereren.

![fpo-existing-asset-reprocess](assets/fpo-existing-asset-reprocess.gif)


## FPO-uitvoeringen weergeven {#view-fpo-renditions}

U kunt de gegenereerde FPO-uitvoeringen controleren nadat de workflow is voltooid. Klik in de gebruikersinterface Experience Manager Assets op het element om een grote voorvertoning te openen. Open de linkerspoorstaaf en selecteer **[!UICONTROL Renditions]**. U kunt ook de sneltoets `Alt + 3` gebruiken wanneer de voorvertoning is geopend.

Klik **[!UICONTROL FPO rendition]** om zijn voorproef te laden. U kunt ook met de rechtermuisknop op de vertoning klikken en deze opslaan in uw bestandssysteem. Controleren op beschikbare uitvoeringen in de linkertrack.

![rendition_list](assets/list-renditions.png)
