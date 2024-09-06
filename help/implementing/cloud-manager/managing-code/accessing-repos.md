---
title: Toegang tot opslagplaats
description: Leer hoe u toegang krijgt tot en beheer krijgt van uw door de Adobe beheerde it-opslagruimten met behulp van het zelfbedienings-git-accountbeheer van Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# Toegang tot opslagplaats {#accessing-repos}

Leer hoe u toegang krijgt tot en beheer krijgt van uw door de Adobe beheerde it-opslagruimten met behulp van het zelfbedienings-git-accountbeheer van Cloud Manager.

## Toegang tot informatie over opslagplaats via de overzichtspagina {#overview-page}

Cloud Manager maakt het gemakkelijk om uw informatie van de bewaarplaatstoegang voor Adobe-geleide bewaarplaatsen terug te winnen door de **knoop van de Reparatie van de Toegang te gebruiken** beschikbaar hoofdzakelijk op de pijpleidingskaart.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan **Pijpleidingen** kaart van uw **pagina van het Overzicht van het Programma**.

   ![ de knoop van Info van de Reparatie van de Toegang op de kaart van Milieu ](assets/pipelines-card.png)

1. Tik of klik de **knoop van Info van de Reactie van de Toegang** om de **Info van de Bewaarplaats** dialoog en mening te openen:

   * De git-gebruikersnaam.
   * Het wachtwoord voor de it.
   * De URL naar de Cloud Manager-it-opslagplaats.
   * Vooraf gebouwde git-opdrachten waarmee u snel een externe server aan uw git-repo- en pushcode kunt toevoegen.

   ![ het venster van Info van de Bewaarplaats ](assets/repository-info.png)

1. Om tot het wachtwoord toegang te hebben, moet een nieuw wachtwoord worden geproduceerd. Om dit te doen, ontvang of klik **wachtwoord** knoop produceren.

1. Bevestig wachtwoordgeneratie in **bent u zeker..** dialoog door te tikken of te klikken **produceert wachtwoord**.

   ![ Bevestig wachtwoordgeneratie ](assets/confirm-password-generation.png)

1. Het wachtwoord wordt geproduceerd en is zichtbaar voor het kopiëren op het **gebied van het Wachtwoord**.

   * Als u een wachtwoord genereert, wordt het vorige wachtwoord ongeldig.
   * Cloud Manager slaat het wachtwoord niet op. Het is uw verantwoordelijkheid om dit wachtwoord veilig op te slaan.
   * Omdat Cloud Manager het wachtwoord niet opslaat, moet u een nieuw wachtwoord opnieuw genereren als u het wachtwoord verliest.

   ![ Voorbeeld van een geproduceerd wachtwoord ](assets/generated-password.png)

Met behulp van deze referenties kunt u een lokale kopie van de opslagplaats klonen, wijzigingen aanbrengen in die lokale opslagplaats en, wanneer u klaar bent, wijzigingen in de code terugsturen naar de externe gegevensopslagruimte in Cloud Manager.

>[!NOTE]
>
>* De **optie van Info van de Reactie van de Toegang** is zichtbaar aan gebruikers met **Ontwikkelaar** of **de rollen van de Manager van de Plaatsing**.
>* De **knoop van Info van de Reactie van de Toegang** toont slechts de informatie van de bewaarplaatstoegang voor Adobe-beheerde bewaarplaatsen. De informatie van de toegang over [ privé bewaarplaatsen ](private-repositories.md) is niet beschikbaar in Cloud Manager.

## Toegang tot gegevens opslagplaats vanuit het venster Opslagplaatsen {#repositories-window}

Een **knoop van Info van de Reactie van de Toegang** is ook beschikbaar in de toolbar van het [**venster van Bewaarplaatsen** ](managing-repositories.md). Het toont de zelfde informatie over de toegang tot van Adobe-beheerde bewaarplaatsen.

## Een toegangswachtwoord intrekken {#revoke-password}

U kunt een toegangswachtwoord op elk ogenblik intrekken. Om dit te doen, [ creeer een steunkaartje voor dit verzoek ](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support).

Het kaartje zal met hoge prioriteit worden behandeld en moet binnen één dag worden ingetrokken.
