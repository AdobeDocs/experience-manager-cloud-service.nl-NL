---
title: Gebruikers en rollen toevoegen - wat is vereist
description: Gebruikers en rollen toevoegen - wat is vereist
translation-type: tm+mt
source-git-commit: 936e42f273b75f0ea7776c51f57af44ec9e6d96f

---


# Gebruikers en rollen toevoegen {#add-users-roles}


Voor veel functies in [!UICONTROL Cloud Manager] zijn specifieke machtigingen vereist. Zo kunnen alleen bepaalde gebruikers de KPI&#39;s (Key Performance Indicators) voor een programma instellen. Deze toestemmingen worden logisch gezien gegroepeerd in rollen.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Zakelijke eigenaar
* Programmabeheerder
* Implementatiebeheer
* Ontwikkelaar

>[!CAUTION]
>
>Als u [!UICONTROL Cloud Manager]wilt gebruiken, hebt u een Adobe-id en de Adobe Managed Services-productcontext nodig.

## Roldefinities {#role-definitions}

>[!NOTE]
>
>De ontwikkelaarspersona in Admin Console is niet gerelateerd aan de rol van de ontwikkelaar in [!UICONTROL Cloud Manager].

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Rollen in Cloud Manager] | Beschrijving |
|--- |--- |
| Zakelijke eigenaar | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Programmabeheerder | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Implementatiebeheer | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] voor het uitvoeren van stage/productie-implementaties. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Ontwikkelaar | Ontwikkelt en test aangepaste toepassingscode. Hiermee wordt voornamelijk [!UICONTROL Cloud Manager] gebruikt om de status weer te geven. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Inhoudsauteur | In het algemeen heeft dit geen invloed op [!UICONTROL Cloud Manager]. Kan [!UICONTROL Cloud Manager] Program Switcher (na navigeer vanuit [!UICONTROL Experience Cloud]) gebruiken om toegang te krijgen tot AEM. |