---
title: SSL-certificaten verwijderen - SSL-certificaten beheren
description: SSL-certificaten verwijderen - SSL-certificaten beheren
exl-id: 43f66871-cca4-4709-95d0-68aa715c0da2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Een SSL-certificaat verwijderen {#deleting-an-ssl-certificate}

>[!IMPORTANT]
>Certificaten verwijderen uit Cloud Manager is een permanente handeling die niet ongedaan kan worden gemaakt. De beste manier is om alle vereiste SSL-bestanden lokaal op te slaan voordat u ze verwijdert in de gebruikersinterface van Cloud Manager.

Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat te verwijderen in Cloud Manager. Met Cloud Manager kunt u geen SSL-certificaat verwijderen waaraan een of meer domeinen zijn gekoppeld.  Alle bijbehorende domeinen moeten worden geschrapt alvorens het SSL certificaat te schrappen. Zie [Een aangepaste domeinnaam verwijderen](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) voor meer informatie.

Voer de onderstaande stappen uit om een SSL-certificaat te verwijderen:

1. Ga naar de **SSL-certificaten** van het scherm **Omgevingen** pagina.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
1. Identificeer de rij waar de SSL certificaatnaam u wenst te schrappen is vermeld.
1. Selecteer **...** helemaal rechts in de rij.
1. Selecteren **Verwijderen**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete01.png)
1. Je verzending bevestigen vanuit **SSL-certificaat verwijderen** in.
