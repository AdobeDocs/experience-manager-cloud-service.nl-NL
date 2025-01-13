---
title: Wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen
description: Meer informatie over de wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen die naar AEM as a Cloud Service komen
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 0b097ab3-bf1d-4d43-9e19-d544594844ef
source-git-commit: 605a8032430b1be4aacebfcf73cfc16ba7691349
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen {#changes-in-user-group-and-product-profile-synchronization}

Wanneer een gebruiker zich aanmeldt bij AEM as a Cloud Service of een toegangstoken wordt gebruikt, worden Adobe Admin Console-gebruikersgroepen, productprofielen en services voor productprofielen als groepen gesynchroniseerd in de AEM repository.

Op 27 januari zullen er enkele wijzigingen in het synchronisatiegedrag optreden plaatsvinden, zodat de gebruikersinterface overzichtelijker wordt en de prestaties worden geoptimaliseerd. Hierdoor zullen er minder groepen in AEM verschijnen. Twee categorieën van AEM worden verwijderd:

1. AEM groepen met achtervoegsel `GROUP_NAME_SUFFIX` . Deze groepen verschijnen niet in Adobe Developer Console, maar in het scherm van het Beheer van de Groep van de AEM, zoals hieronder getoond. In het onwaarschijnlijke geval dat uw AEM toepassing naar deze groepen verwijst, zorg ervoor om Adobe Admin Console gebruikersgroepen zonder dat achtervoegsel in plaats daarvan van verwijzingen te voorzien.

   ![ Verwijderde groepen 1 ](/help/security/assets/removed-groups-1.png)

1. AEM groepen die verbonden zijn met Adobe Admin Console-productprofielen die geen verband houden met de specifieke omgeving. Dit kunnen productprofielen zijn die:

   * in verband met andere Adobe producten
   * in verband met andere AEM
   * gerelateerd aan andere AEM omgevingen in hetzelfde AEM
   * gerelateerd aan Cloud Manager (bijvoorbeeld `Business Owner - Cloud Service`)

   In de onderstaande afbeelding ziet u bijvoorbeeld een groot aantal rijen met het patroon `AEM Administrators-<suffix>` of `AEM Users-<suffix>` , waarbij het achtervoegsel niet gerelateerd is aan de huidige omgeving.

   ![ Verwijderde groepen 2 ](/help/security/assets/removed-groups-2.png)

U kunt controleren welk achtervoegsel met het huidige milieu verwant is door te selecteren leidt **Toegang - de Profielen van de Auteur** (of **Publish Profielen**) in het de actiemenu van het milieu in Cloud Manager.

![ achtervoegsels van de Controle ](/help/security/assets/suffix-check.png)

Hiermee navigeert u naar de Adobe Admin Console, zoals hieronder in de schermafbeelding wordt getoond. De `<suffix>` kan een willekeurige set tekens zijn, of liever de laag, en programma- en omgeving-id (bijvoorbeeld `author - Program 12345 - Environment 45678` ).

![ Achtervoegsels in de Admin Console ](/help/security/assets/admin-console-profile-suffixes.png)

In het onwaarschijnlijke geval dat uw AEM toepassing verwijst naar een groep die niet meer in AEM wordt weergegeven, moet u in plaats daarvan i) een productprofiel uit de rechterAEM of ii) een Adobe Admin Console-gebruikersgroep gebruiken.

