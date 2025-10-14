---
title: Wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen
description: Meer informatie over de wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen die naar AEM as a Cloud Service komen
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 0b097ab3-bf1d-4d43-9e19-d544594844ef
source-git-commit: 5c103fcce1ae47bc89f4f572d89967c62c1f7603
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen {#changes-in-user-group-and-product-profile-synchronization}

Wanneer een gebruiker zich aanmeldt bij AEM as a Cloud Service of een toegangstoken wordt gebruikt, worden Adobe Admin Console-gebruikersgroepen, productprofielen en services voor productprofielen als groepen gesynchroniseerd in de AEM repository.

Vanaf AEM Maintenance Release 19149 wordt het gedrag van groepssynchronisatie gewijzigd om de gebruikersinterface overzichtelijker te maken en de prestaties te optimaliseren. Specifiek, zal het lidmaatschap van de gebruikersgroep van de volgende twee categorieën van AEM groepen niet meer worden gesynchroniseerd:

1. AEM groepen met achtervoegsel `GROUP_NAME_SUFFIX` . Deze groepen verschijnen niet in Adobe Developer Console, maar in het scherm van het Beheer van de Groep van de AEM, zoals hieronder getoond. In het onwaarschijnlijke geval dat uw AEM toepassing naar deze groepen verwijst, zorg ervoor om Adobe Admin Console gebruikersgroepen zonder dat achtervoegsel in plaats daarvan van verwijzingen te voorzien.

   ![&#x200B; Verwijderde groepen 1 &#x200B;](/help/security/assets/removed-groups-1.png)

1. AEM groepen die verbonden zijn met Adobe Admin Console-productprofielen die geen verband houden met de specifieke omgeving. Dit kunnen productprofielen zijn die:

   * in verband met andere Adobe producten
   * in verband met andere AEM
   * gerelateerd aan andere AEM omgevingen in hetzelfde AEM
   * gerelateerd aan Cloud Manager (bijvoorbeeld `Business Owner - Cloud Service`)

   In de onderstaande afbeelding ziet u bijvoorbeeld een groot aantal rijen met het patroon `AEM Administrators-<suffix>` of `AEM Users-<suffix>` , waarbij het achtervoegsel niet gerelateerd is aan de huidige omgeving.

   ![&#x200B; Verwijderde groepen 2 &#x200B;](/help/security/assets/removed-groups-2.png)

U kunt controleren welk achtervoegsel met het huidige milieu verwant is door te selecteren leidt **Toegang - de Profielen van de Auteur** (of **Publish Profielen**) in het de actiemenu van het milieu in Cloud Manager.

![&#x200B; achtervoegsels van de Controle &#x200B;](/help/security/assets/suffix-check.png)

Hiermee navigeert u naar de Adobe Admin Console, zoals hieronder in de schermafbeelding wordt getoond. De `<suffix>` kan een willekeurige set tekens zijn, of liever de laag, en programma- en omgeving-id (bijvoorbeeld `author - Program 12345 - Environment 45678` ).

![&#x200B; Achtervoegsels in de Admin Console &#x200B;](/help/security/assets/admin-console-profile-suffixes.png)

In het onwaarschijnlijke geval dat uw AEM toepassing verwijst naar een groep die niet meer in AEM wordt weergegeven, moet u in plaats daarvan i) een productprofiel uit de rechterAEM of ii) een Adobe Admin Console-gebruikersgroep gebruiken.

De groepslidmaatschappen van de gebruiker worden gesynchroniseerd wanneer zij in het milieu registreren, en zij worden verwijderd uit groepen niet verwant met het huidige milieu. De groepen zelf blijven en bevatten gebruikers die zich niet hebben aangemeld sinds de functie is ingeschakeld.
