---
title: Toegang tot opslagplaatsen
description: Leer hoe u uw git-opslagplaats kunt openen en beheren met behulp van het beheer van een git-account voor zelfbediening vanuit Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 4729574eb31e01077f0d2a35efcef6d134f6aa5c
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Toegang tot opslagplaatsen {#accessing-repos}

Leer hoe u uw git-opslagplaats kunt openen en beheren met behulp van het beheer van een git-account voor zelfbediening vanuit Cloud Manager.

## Accountbeheer voor Zelf-servicereservering gebruiken {#self-service-repos}

Met Cloud Manager kunt u eenvoudig gegevens van uw opslagplaats ophalen met de **Repo-info openen** de knoop is duidelijk beschikbaar op de pijpleidingskaart.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Navigeren naar **Pijpleidingen** kaart van uw **Programmaoverzicht** pagina en zoek de **Repo-info openen** om toegang te krijgen tot uw Git Repository en deze te beheren.

   ![De knop Repo-info openen op de milieucokaart](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klik op de knop **Repo-info weergeven** om een dialoogvenster te openen dat wordt weergegeven:

   * De URL naar de gegevensopslagruimte van Cloud Manager.
   * De git-gebruikersnaam.
   * Het wachtwoord voor de it, waarvan de waarde wordt weergegeven wanneer de optie **Wachtwoord genereren** wordt geklikt.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Met behulp van deze referenties kan de gebruiker een lokale kopie van de opslagplaats klonen en wijzigingen aanbrengen in die lokale opslagplaats, en wanneer hij klaar is, alle wijzigingen in de code terugsturen naar de externe opslagplaats voor code in Cloud Manager.

De **Repo-info openen** deze optie is ook beschikbaar op de **Niet-productie** pijplijntabblad van de **Pijpleidingen** kaart.

![Knop Repo-info benaderen op niet-productietabblad](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>De **Repo-info openen** deze optie is zichtbaar voor gebruikers met **Ontwikkelaar** of **Implementatiebeheer** rollen.
