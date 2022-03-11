---
title: 'Een SSL-certificaat bijwerken en vervangen - SSL beheren '
description: Een SSL-certificaat bijwerken en vervangen - SSL-certificaten beheren
exl-id: 662494b1-a710-4822-97ef-057043ef89ba
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Een SSL-certificaat weergeven, bijwerken en vervangen  {#view-update-replace-ssl-certificate}

## Een SSL-certificaat weergeven en bijwerken {#view-update}

Wanneer gebruikt u deze opties in de interface van Cloud Manager:

* Een bestaand certificaat verloopt bijna. De gebruiker heeft het certificaat met de certificaatverkoper vernieuwd en wenst bestaande te vervangen die op het punt staat te verlopen. Opmerking: alleen gebruikers met de juiste machtigingen kunnen updates uitvoeren.
* Gebruik de **Weergeven en bijwerken** om de SSL-certificaatdetails gewoon weer te geven.
* U kunt ook de naam wijzigen die is gebruikt om naar een certificaat te verwijzen vanuit dit scherm.
* Alleen gebruikers met de juiste machtigingen kunnen updates uitvoeren.


## Een SSL-certificaat bijwerken dat binnenkort vervalt {#update-ssl-certificate}

Wanneer een certificaat verloopt, werken domeinen die in gebruik zijn met het verlopen certificaat niet meer. Als u een verlopen certificaat wilt bijwerken, moet u de onderstaande stappen volgen. Zo blijft uw domein naar wens werken. Wanneer u een nieuw certificaat toevoegt, moet u de aangepaste domeinnaam met het nieuwe certificaat bijwerken voordat de domeinen naar wens werken. Zie [Een aangepaste domeinnaam weergeven, bijwerken en vervangen](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md) voor meer informatie .

Voer de onderstaande stappen uit om een SSL-certificaat bij te werken:

>[!NOTE]
>Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat bij te werken in Cloud Manager.

1. Navigeer vanuit het deelvenster SSL-certificaten naar het scherm SSL-certificaten **Omgevingen** pagina.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma.
1. De menuopties voor elke rij kunnen worden betreden door de drie knopen bij het uiterst juiste eind van de rij van belang te selecteren.
1. Selecteren **Weergeven en bijwerken**. De certificaatdetails kunnen van hier worden bekeken.

## Een SSL-certificaat vervangen {#replace-ssl-certificate}

Voer de onderstaande stappen uit om een SSL-certificaat te vervangen:

1. Navigeer vanuit het deelvenster SSL-certificaten naar het scherm SSL-certificaten **Omgevingen** pagina.
1. Er wordt een tabel met een rij weergegeven voor elk SSL-certificaat dat is geïnstalleerd in uw programma.
1. De menuopties voor elke rij kunnen worden betreden door de drie knopen bij het uiterst juiste eind van de rij van belang te selecteren.
1. Selecteren **Weergeven en bijwerken**.
1. Als u het certificaat wilt vervangen, plakt u de nieuwe inhoud in de juiste invoervelden en klikt u op **Opslaan**. U moet eventuele fouten oplossen.

   Zie [Certificaatfouten](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-error) om door algemeen ondervonden kwesties te werken.
