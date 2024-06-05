---
title: Aangepaste domeinnamen beheren
description: Leer hoe u met Cloud Manager aangepaste domeinnamen kunt weergeven, bijwerken, vervangen en verwijderen.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Aangepaste domeinnamen beheren {#managing-custom-domain-names}

Met Cloud Manager kunt u aangepaste domeinnamen weergeven, bijwerken, vervangen en verwijderen.

## Weergeven en bijwerken {#view-and-update}

Gebruik de **Weergeven en bijwerken** om de details van om het even welk van uw namen van het douanedomein te bekijken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** -console, selecteert u het programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Identificeer de rij van de naam van het douanedomein u bekijken of wilt bijwerken.

1. Klik op de knop met de ellips helemaal rechts van de rij.

1. Selecteer de **Weergeven en bijwerken** -optie.

## SSL-certificaat van aangepaste domeinnaam bijwerken {#update-cert}

U kunt volgen [dezelfde stappen volgen om een aangepaste domeinnaam weer te geven en bij te werken](#view-and-update) om het SSL-certificaat van een aangepaste domeinnaam bij te werken.

>[!NOTE]
>
>Het SSL-certificaat moet geldig zijn, [reeds geconfigureerd,](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) en bevat de aangepaste domeinnaam die u bijwerkt.

## Een aangepaste domeinnaam verwijderen {#deleting}

Een gebruiker met de **Zakelijke eigenaar** of **Implementatiebeheer** Met de rol kunt u Cloud Manager gebruiken om een aangepaste domeinnaam te verwijderen.

### Een aangepaste domeinnaam verwijderen uit alle bijbehorende omgevingen {#delete-cdn-all}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Domeininstellingen** pagina van de **Overzicht** scherm.

1. Identificeer de rij van de naam van het douanedomein u wilt schrappen.

1. Klik op de knop met de ellips helemaal rechts van de rij.

1. Selecteren **Verwijderen**.

1. Bevestig je verzending.

### Een aangepaste domeinnaam uit een specifieke omgeving verwijderen {#delete-cdn-specific}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.
1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.
1. Van de **Omgevingen** pagina, navigeer naar het detailscherm van de omgeving van belang.
1. Identificeer in de tabel met domeinnamen de rij van de aangepaste domeinnaam die u wilt verwijderen.
1. Klik op de knop met de ellips helemaal rechts van de rij.
1. Selecteren **Verwijderen**.
1. Bevestig je verzending.
