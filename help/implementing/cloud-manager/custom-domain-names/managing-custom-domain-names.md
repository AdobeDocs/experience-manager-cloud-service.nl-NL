---
title: Aangepaste domeinnamen beheren
description: Leer hoe u met Cloud Manager aangepaste domeinnamen kunt weergeven, bijwerken, vervangen en verwijderen.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8e2fc0d4ee82e79d1a822a528b1a46acce3c192a
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Aangepaste domeinnamen beheren {#managing-custom-domain-names}

Met Cloud Manager kunt u aangepaste domeinnamen bewerken, bijwerken, vervangen en verwijderen.

## Een aangepaste domeinnaamconfiguratie bewerken {#view-and-update}

In Adobe Cloud Manager, zou u een configuratie van de douanedomeinnaam om de volgende redenen kunnen willen uitgeven:

* **Omschakelende milieu&#39;s**: Om de correcte configuratie toe te passen afhankelijk van of u inhoud aan eind - gebruikers (Publish) of interne gebruikers (Auteur) dient.
* **de updates van de Veiligheid**: Om aan een nieuwer SSL certificaat voor verbeterde veiligheid of nalevingsdoeleinden te bevorderen.
* **Veranderende plaatsingsstrategie**: Om ervoor te zorgen wordt het correcte SSL certificaat toegepast op een specifiek milieu voor juiste encryptie en plaatstoegang.

**om een configuratie van de douanedomeinnaam uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Klik in de linkerbovenhoek van de pagina op het hamburgerpictogram om het linkernavigatiemenu weer te geven.
1. Onder de **rubriek van de Diensten**, klik **Configuraties CDN**.
1. Voor de **CDN Configuraties** pagina, klik de ellips aan het eind van een rij waarvan CDN u wilt uitgeven.
1. Klik **uitgeven**.
1. In **geef CDN configuratie** dialoogdoos uit, doe het volgende:
   * In de **drop-down lijst 0} Rij, selecteer de rij (Auteur of Publish) u wilt gebruiken.**
   * In de **SSL certificaat** drop-down lijst, selecteer het SSL certificaat u wilt gebruiken.
1. Klik **Update**.


## Het SSL-certificaat van een aangepaste domeinnaam bijwerken {#update-cert}

U kunt [ de zelfde stappen volgen om een naam van het douanedomein ](#view-and-update) te bekijken en bij te werken om SSL van een douanedomeinnaam certificaat bij te werken.

>[!NOTE]
>
>Het SSL certificaat moet geldig zijn, [ reeds gevormd ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), en bevat de naam van het douanedomein u bijwerkt.


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
