---
title: Wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen
description: Meer informatie over de wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen die naar AEM as a Cloud Service komen
feature: Security
role: Admin
hide: true
hidefromtoc: true
source-git-commit: c3e3905d3896d79149a386241d798f78631184b3
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# Wijzigingen in de synchronisatie van gebruikersgroepen en productprofielen {#changes-in-user-group-and-product-profile-synchronization}

Wanneer een gebruiker zich aanmeldt bij AEM as a Cloud Service of een toegangstoken wordt gebruikt, worden Adobe Admin Console-gebruikersgroepen, productprofielen en services voor productprofielen als groepen gesynchroniseerd in de AEM repository.

Op 28 januari zullen er enkele wijzigingen in het synchronisatiegedrag optreden plaatsvinden, zodat de gebruikersinterface overzichtelijker wordt en de prestaties worden geoptimaliseerd. Hierdoor zullen er minder groepen in AEM verschijnen. Twee categorieën van AEM worden verwijderd:

1. AEM groepen met achtervoegsel `GROUP_NAME_SUFFIX` . Deze groepen verschijnen niet in Adobe Developer Console, maar in het scherm van het Beheer van de Groep van de AEM, zoals hieronder getoond. In het onwaarschijnlijke geval dat uw AEM toepassing naar deze groepen verwijst, zorg ervoor om de gebruikersgroepen van Adobe Admin Console in plaats daarvan te gebruiken.

   ![ Verwijderde groepen 1 ](/help/security/assets/removed-groups-1.png)

1. AEM groepen die zijn gekoppeld aan Adobe Admin Console-productprofielen die geen verband houden met de specifieke combinatie van AEM of omgeving (bijvoorbeeld `author` of `e4535` ). Dit kunnen productprofielen zijn die:

   * in verband met andere Adobe producten
   * in verband met andere AEM
   * gerelateerd aan andere AEM omgevingen in hetzelfde AEM
   * gerelateerd aan een andere laag (bijvoorbeeld `author` vs `publish` ) in dezelfde AEM.
   * gerelateerd aan Cloud Manager (bijvoorbeeld `Business Owner - Cloud Service`)

   In de onderstaande afbeelding ziet u bijvoorbeeld een groot aantal rijen met het patroon `AEM Administrators-<suffix>` of `AEM Users-<suffix>` , waarbij het achtervoegsel niet gerelateerd is aan de huidige omgeving.

   ![ Verwijderde groepen 2 ](/help/security/assets/removed-groups-2.png)

U kunt controleren welk achtervoegsel met het huidige milieu verwant is door te selecteren leidt **Toegang - de Profielen van de Auteur** (of **Publish Profielen**) in het de actiemenu van het milieu in Cloud Manager.

![ achtervoegsels van de Controle ](/help/security/assets/suffix-check.png)

Hiermee navigeert u naar de Adobe Admin Console, zoals hieronder in de schermafbeelding wordt getoond. De `<suffix>` kan een willekeurige set tekens zijn, of liever de laag, en programma- en omgeving-id (bijvoorbeeld `author - Program 12345 - Environment 45678` ).

![ Achtervoegsels in de Admin Console ](/help/security/assets/admin-console-profile-suffixes.png)

In het onwaarschijnlijke geval dat uw AEM toepassing naar deze groepen verwijst, zorg ervoor om de gebruikersgroepen van Adobe Admin Console in plaats daarvan te gebruiken.

>[!NOTE]
>
>Let vooral op deze potentiële valkuilen:
>
>1. Uw AEM toepassing is afhankelijk van een AEM groep die vanuit een Cloud Manager-productprofiel is gesynchroniseerd
>1. De publicatielaag van de AEM toepassing is afhankelijk van een AEM groep die vanuit een productprofiel voor de auteurslaag is gesynchroniseerd. Dit geldt ook voor het omgekeerde scenario (auteurslaag die op publicatielaag baseert).