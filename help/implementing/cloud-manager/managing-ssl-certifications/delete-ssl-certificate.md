---
title: SSL-certificaten verwijderen - SSL-certificaten beheren
description: SSL-certificaten verwijderen - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: 99eb33c3c42094f787d853871aee3a3607856316
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Een SSL-certificaat {#deleting-an-ssl-certificate} verwijderen

>[!IMPORTANT]
>Certificaten verwijderen uit Cloud Manager is een permanente handeling die niet ongedaan kan worden gemaakt. De beste manier is om alle vereiste SSL-bestanden lokaal op te slaan voordat u ze verwijdert in de gebruikersinterface van Cloud Manager.

Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat te verwijderen in Cloud Manager. Met Cloud Manager kunt u geen SSL-certificaat verwijderen waaraan een of meer domeinen zijn gekoppeld.  Alle bijbehorende domeinen moeten worden geschrapt alvorens het SSL certificaat te schrappen. Raadpleeg [Een aangepaste domeinnaam verwijderen](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) voor meer informatie.

Voer de onderstaande stappen uit om een SSL-certificaat te verwijderen:

1. Navigeer naar het scherm **SSL Certificates** van de pagina **Environments**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
1. Identificeer de rij waar de SSL certificaatnaam u wenst te schrappen is vermeld.
1. **selecteren..** menu van het uiterst juiste eind van de rij.
1. Selecteer **Verwijderen**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete01.png)
1. Bevestig uw verzending via het dialoogvenster **SSL-certificaat verwijderen**.
