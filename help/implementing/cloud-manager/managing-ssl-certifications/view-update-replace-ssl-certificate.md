---
title: 'Een SSL-certificaat bijwerken en vervangen - SSL beheren '
description: Een SSL-certificaat bijwerken en vervangen - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: 54171b90f99a14fd43c4dc01308264b9a954b927
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# SSL-certificaten {#view-update-replace-ssl-certificate} weergeven en bijwerken en vervangen

## Een SSL-certificaat {#view-update} weergeven en bijwerken

Wanneer gebruikt u deze opties in de interface van Cloud Manager:

* Een bestaand certificaat verloopt bijna. De gebruiker heeft het certificaat met de certificaatverkoper vernieuwd en wenst bestaande te vervangen die op het punt staat te verlopen. Opmerking: alleen gebruikers met de juiste machtigingen kunnen updates uitvoeren.
* Met het menu **Beeld en bijwerken** kunt u gewoon de SSL-certificaatdetails weergeven.
* U kunt ook de naam wijzigen die is gebruikt om naar een certificaat te verwijzen vanuit dit scherm.
   >[!NOTE]
   >Alleen gebruikers met de juiste machtigingen kunnen updates uitvoeren.


## Een SSL-certificaat bijwerken dat {#update-ssl-certificate} vervalt

>[!NOTE]
>Wanneer een certificaat verloopt, werken domeinen die in gebruik zijn met het verlopen certificaat niet meer. Als u een verlopen certificaat wilt bijwerken, moet u de onderstaande stappen volgen. Zo blijft uw domein naar wens werken. Wanneer u een nieuw certificaat toevoegt, moet u de aangepaste domeinnaam met het nieuwe certificaat bijwerken voordat de domeinen naar wens werken. Raadpleeg [Een aangepaste domeinnaam bekijken en bijwerken en vervangen](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md)voor meer informatie

Voer de onderstaande stappen uit om een SSL-certificaat bij te werken:

>[!NOTE]
>Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat bij te werken in Cloud Manager.

1. Navigeer van de pagina **Environments** naar het scherm SSL-certificaten.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma.
1. De menuopties voor elke rij kunnen worden betreden door de drie knopen bij het uiterst juiste eind van de rij van belang te selecteren.
1. Selecteer **Weergave &amp; update**. De certificaatdetails kunnen van hier worden bekeken.

## SSL-certificaten vervangen {#replace-ssl-certificate}

Voer de onderstaande stappen uit om een SSL-certificaat te vervangen:

1. Navigeer van de pagina **Environments** naar het scherm SSL-certificaten.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma.
1. De menuopties voor elke rij kunnen worden betreden door de drie knopen bij het uiterst juiste eind van de rij van belang te selecteren.
1. Selecteer **Weergave &amp; update**.
1. Als u het certificaat wilt vervangen, plakt u de nieuwe inhoud in de juiste invoervelden en klikt u op **Opslaan**. U moet eventuele fouten oplossen.

   Verwijs naar [Certificaatfouten](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-error) om door algemeen ondervonden kwesties te werken.