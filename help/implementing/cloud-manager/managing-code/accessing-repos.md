---
title: Toegang tot opslagplaats
description: Leer hoe u uw door Adobe beheerde Git-opslagruimten kunt openen en beheren met behulp van het zelf-service Git-accountbeheer van Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Toegang tot opslagplaats {#accessing-repos}

Leer hoe u uw door Adobe beheerde Git-opslagruimten kunt openen en beheren met behulp van het zelf-service Git-accountbeheer van Cloud Manager.

## Toegang tot gegevens in de opslagplaats via de overzichtspagina {#overview-page}

Cloud Manager maakt het gemakkelijk om uw informatie van de bewaarplaatstoegang voor Adobe-Beheerde bewaarplaatsen terug te winnen gebruikend **RepoInfo van de Toegang** van de **Pijpleidingen** kaart.

Het **dialoogvakje van Info van de Bewaarplaats 0&rbrace; &lbrace;laat u de volgende toegangsinformatie voor Adobe-Beheerde bewaarplaatsen zien:**

* De Git-gebruikersnaam.
* Het wachtwoord voor Actief.
* De URL naar de Cloud Manager Git-opslagplaats.
* De vooraf gebouwde bevelen van de Git om een ver aan uw reactie van de Git en duwcode toe te voegen snel.

![&#x200B; het venster van Info van de Bewaarplaats &#x200B;](assets/repository-info.png)

De informatie van de toegang over [&#x200B; privé bewaarplaatsen &#x200B;](private-repositories.md) is niet beschikbaar in Cloud Manager.

De **eigenschap van Info van de Reactie van de Toegang** is zichtbaar aan gebruikers met **Ontwikkelaar** of **de rollen van de Manager van de Plaatsing**.

**om tot gegevensopslagplaats van de pagina van het Overzicht toegang te hebben:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, onder de **Pipelines** kaart, klik **Info van de Reactie van de Toegang**.

   ![&#x200B; Info van de Reparatie van de Toegang op de kaart van Pijpleidingen &#x200B;](assets/pipelines-card.png)

1. Om tot het wachtwoord toegang te hebben, moet een nieuw wachtwoord worden geproduceerd. In het **de dialoogvakje van Info van de Bewaarplaats**, uitgezochte **produceert wachtwoord**.

1. In de bevestigingsdialoogdoos, produceert de uitgezochte **wachtwoord**.

   ![&#x200B; Bevestig wachtwoordgeneratie &#x200B;](assets/confirm-generated-password.png)

1. Aan het recht van het **1&rbrace; gebied van het Wachtwoord &lbrace;, klik** pictogram van het Exemplaar ![&#x200B; om het wachtwoord aan het klembord te kopiëren.](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)

   * Als u een wachtwoord genereert, wordt het vorige wachtwoord ongeldig.
   * Cloud Manager slaat het wachtwoord niet op. Het is uw verantwoordelijkheid om het wachtwoord veilig op te slaan.
   * Omdat Cloud Manager het wachtwoord niet opslaat, moet u een nieuw wachtwoord opnieuw genereren als u het wachtwoord verliest.

   ![&#x200B; het wachtwoord van het Exemplaar in de dialoogdoos van Info van de Bewaarplaats &#x200B;](/help/implementing/cloud-manager/managing-code/assets/repository-copy-password.png)

Met behulp van deze referenties kunt u een lokale kopie van de opslagplaats klonen, wijzigingen aanbrengen in die lokale opslagplaats en, wanneer u klaar bent, wijzigingen in de code terugsturen naar de externe gegevensopslagruimte in Cloud Manager.

## Toegang tot gegevens in de opslagplaats via de pagina Opslagplaatsen {#repositories-window}

De **eigenschap van Info van de Reactie van de Toegang** is ook beschikbaar bij [**Bewaarplaatsen** pagina &#x200B;](managing-repositories.md). Dezelfde informatie over toegang tot door Adobe beheerde opslagruimten wordt weergegeven.

## Een toegangswachtwoord intrekken {#revoke-password}

U kunt een toegangswachtwoord op elk ogenblik intrekken.

Om dit te doen, [&#x200B; creeer een steunkaartje voor dit verzoek &#x200B;](https://experienceleague.adobe.com/nl?support-solution=Experience+Manager&support-tab=home#support). Het kaartje wordt met hoge prioriteit behandeld en wordt gewoonlijk binnen één dag ingetrokken.
