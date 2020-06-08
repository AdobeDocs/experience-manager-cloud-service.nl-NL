---
title: Gebruikers en rollen toevoegen - wat is vereist
description: Gebruikers en rollen toevoegen - wat is vereist
translation-type: tm+mt
source-git-commit: 936e42f273b75f0ea7776c51f57af44ec9e6d96f
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 9%

---


# Gebruikers en rollen toevoegen {#add-users-roles}


Veel functies in [!UICONTROL Cloud Manager] vereisen specifieke machtigingen om te werken. Zo kunnen alleen bepaalde gebruikers de KPI&#39;s (Key Performance Indicators) voor een programma instellen. Deze toestemmingen worden logisch gezien gegroepeerd in rollen.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

>[!CAUTION]
>
>U moet beschikken over een Adobe-id en de productcontext van Adobe Managed Services om deze te kunnen gebruiken. [!UICONTROL Cloud Manager]

## Roldefinities {#role-definitions}

>[!NOTE]
>
>De ontwikkelaarspersona in Admin Console is niet gerelateerd aan de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager].

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Cloud Manager] Rollen | Beschrijving |
|--- |--- |
| Business Owner | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Program Manager | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Deployment Manager | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] om werkgebied/productieplaatsingen uit te voeren. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Developer | Ontwikkelt en test aangepaste toepassingscode. Wordt voornamelijk gebruikt [!UICONTROL Cloud Manager] om de status weer te geven. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Inhoudsauteur | Over het algemeen heeft dit geen invloed op [!UICONTROL Cloud Manager]de interactie. Kan de Schakelaar van het Programma gebruiken [!UICONTROL Cloud Manager] (die van [!UICONTROL Experience Cloud]) is genavigeerd om tot AEM toegang te hebben. |