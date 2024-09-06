---
title: Aangepaste domeinnamen beheren
description: Leer hoe u met Cloud Manager aangepaste domeinnamen kunt weergeven, bijwerken, vervangen en verwijderen.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4e887b753eaf09e104c68484792f00dcb08ee304
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Aangepaste domeinnamen beheren {#managing-custom-domain-names}

Met Cloud Manager kunt u aangepaste domeinnamen weergeven, bijwerken, vervangen en verwijderen.

## Een aangepaste domeinnaam weergeven en bijwerken {#view-and-update}

Gebruik het **menu van de Mening en van de Update** om de details van om het even welk van uw namen van het douanedomein te bekijken.

**om een naam van het douanedomein te bekijken en bij te werken:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Identificeer de rij van de naam van het douanedomein die u wilt bekijken of bijwerken.

1. Klik op de knop met de ellips helemaal rechts van de rij.

1. Selecteer de **Mening &amp; van de Update** optie.

## Het SSL-certificaat van een aangepaste domeinnaam bijwerken {#update-cert}

U kunt [ de zelfde stappen volgen om een naam van het douanedomein ](#view-and-update) te bekijken en bij te werken om SSL van een douanedomeinnaam certificaat bij te werken.

>[!NOTE]
>
>Het SSL certificaat moet geldig zijn, [ reeds gevormd ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md), en bevat de naam van het douanedomein u bijwerkt.

## Een aangepaste domeinnaam verwijderen {#deleting}

Een gebruiker met de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan Cloud Manager gebruiken om een naam van het douanedomein te schrappen.

### Een aangepaste domeinnaam uit alle bijbehorende omgevingen verwijderen {#delete-cdn-all}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **pagina van de Montages van het Domein** van het **scherm van het Overzicht**.

1. Identificeer de rij van de naam van het douanedomein die u wilt schrappen.

1. Klik op de knop met de ellips helemaal rechts van de rij.

1. Selecteer **Schrapping**.

1. Bevestig je verzending.

### Een aangepaste domeinnaam uit een specifieke omgeving verwijderen {#delete-cdn-specific}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.
1. Van de **pagina van Milieu&#39;s**, navigeer aan een detailsscherm van het milieu van belang.
1. Identificeer in de tabel met domeinnamen de rij van de aangepaste domeinnaam die u wilt verwijderen.
1. Klik op de knop met de ellips helemaal rechts van de rij.
1. Selecteer **Schrapping**.
1. Bevestig je verzending.
