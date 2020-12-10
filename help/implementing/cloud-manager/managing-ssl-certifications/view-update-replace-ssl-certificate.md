---
title: 'Een SSL-certificaat bijwerken en vervangen - SSL beheren '
description: Een SSL-certificaat bijwerken en vervangen - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: d1301d4414f87b30f5ab732eacbb61c96f102262
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# SSL-certificaten {#view-update-replace-ssl-certificate} weergeven en bijwerken en vervangen

## Een SSL-certificaat {#view-update} weergeven en bijwerken

Wanneer gebruikt u deze optie in de interface van Cloud Manager:

* Een bestaand certificaat verloopt bijna. De gebruiker heeft het certificaat met de certificaatverkoper vernieuwd en wenst bestaande te vervangen die op het punt staat te verlopen. Opmerking: alleen gebruikers met de juiste machtigingen kunnen updates uitvoeren.
* Met het menu Beeld en bijwerken kunt u gewoon de SSL-certificaatdetails weergeven.
* U kunt ook de naam wijzigen die is gebruikt om naar een certificaat te verwijzen vanuit dit scherm.
   >[!NOTE]
   >Alleen gebruikers met de juiste machtigingen kunnen updates uitvoeren.


## Een SSL-certificaat bijwerken dat {#update-ssl-certificate} vervalt


>[!NOTE]
>Wanneer een certificaat verloopt, werken domeinen die in gebruik zijn met het verlopen certificaat niet meer. Als u een verlopen certificaat wilt bijwerken, moet u de onderstaande stappen volgen. Zo blijft uw domein naar wens werken. Wanneer u een nieuw certificaat toevoegt, moet u de aangepaste domeinnaam met het nieuwe certificaat bijwerken voordat de domeinen naar wens werken. Raadpleeg Aangepaste domeinnaam weergeven en bijwerken voor meer informatie

Voer de onderstaande stappen uit om een SSL-certificaat bij te werken:

>[!NOTE]
>Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat bij te werken in Cloud Manager.

1. Navigeer van de pagina **Environments** naar het scherm SSL-certificaten.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma.
1. De menuopties voor elke rij kunnen worden betreden door de drie knopen bij het uiterst juiste eind van de rij van belang te selecteren. Van hier, uitgezochte Mening &amp; Update. De certificaatdetails kunnen vanaf hier worden weergegeven, zoals in het onderstaande voorbeeld wordt geïllustreerd.
1. Als u het certificaat wilt vervangen, plakt u de nieuwe inhoud in de juiste invoervelden en slaat u deze op. U moet eventuele fouten oplossen. Verwijs de sectie van de Fouten van het Certificaat om door algemeen ondervonden kwesties te werken.