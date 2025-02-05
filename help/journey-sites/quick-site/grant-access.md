---
title: Toegang verlenen aan de front-end ontwikkelaar
description: Aan boord van de front-end ontwikkelaars in Cloud Manager zodat hebben zij toegang tot uw AEM plaats git bewaarplaats en pijpleiding.
exl-id: 58e95c92-b859-4bb9-aa62-7766510486fd
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Toegang verlenen aan de front-end ontwikkelaar {#grant-fed-access}

Aan boord van de front-end ontwikkelaars in Cloud Manager zodat hebben zij toegang tot uw AEM plaats git bewaarplaats en pijpleiding.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de reis van de Aanmaak van de AEM Snelle Plaats, [ Opstelling Uw Pijpleiding ](pipeline-setup.md), leerde u hoe te om een front-end pijpleiding tot stand te brengen om de aanpassing van het thema van uw plaats te beheren, en u zou nu moeten:

* Begrijp wat een front-end pijpleiding is.
* Weet hoe u een front-end pijpleiding in Cloud Manager kunt opzetten.

U moet nu uw front-end ontwikkelaar toegang tot Cloud Manager verlenen via het instapproces, zodat de front-end ontwikkelaar toegang heeft tot de AEM git repository en de pijpleiding die u hebt gemaakt.

## Doelstelling {#objective}

Het proces om toegang tot Cloud Manager te verlenen en gebruikersrollen toe te wijzen aan uw gebruikers wordt genoemd onboarding. In dit document wordt een overzicht gegeven van de belangrijkste stappen voor het instappen van een front-end ontwikkelaar. Na het lezen weet u:

* Een front-end ontwikkelaar toevoegen als een gebruiker.
* Hoe te om de vereiste rollen aan de front-end ontwikkelaar te verlenen.

>[!TIP]
>
>Er is een volledige documentatietraject gewijd aan het aan boord gaan van uw team op AEM als dienst van de Wolk, verbonden aan in de [ Extra sectie van Middelen ](#additional-resources) van dit document, als u extra details over het proces nodig hebt.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis is van toepassing op de beheerder van Cloud Manager.

## Vereisten {#requirements}

* U moet een lid van **rol van BedrijfsEigenaar** in Cloud Manager zijn.
* U moet Admin van a **Sys** in Cloud Manager zijn.
* U moet toegang tot de Admin Console hebben.

## Voeg de Front-End Ontwikkelaar als Gebruiker toe {#add-fed-user}

Eerst moet u de front-end ontwikkelaar als gebruiker toevoegen door de Admin Console te gebruiken.

1. Teken in de Admin Console in [ https://adminconsole.adobe.com/ ](https://adminconsole.adobe.com/).

1. Nadat u zich hebt aangemeld, krijgt u een overzichtspagina te zien die lijkt op de volgende afbeelding.

   ![ overzicht van de Admin Console ](assets/admin-console.png)

1. Controleer de naam van de org in de rechterbovenhoek van het scherm en zorg ervoor dat u zich op de juiste org bevindt.

   ![ de naam van de Controle org ](assets/correct-org.png)

1. Selecteer **Adobe Experience Manager as a Cloud Service** van de **Producten en de diensten** kaart.

   ![ Uitgezochte AEMaaCS ](assets/select-aemaacs.png)

1. U ziet de lijst met vooraf geconfigureerde Cloud Manager-productprofielen. Als deze profielen niet worden weergegeven, neemt u contact op met de Cloud Manager-beheerder omdat u mogelijk niet de juiste machtigingen op uw org hebt.

   ![ Profielen van het Product ](assets/product-profiles.png)

1. Om de front-end ontwikkelaar aan de correcte profielen toe te wijzen, selecteer het **lusje van Gebruikers** en dan **voeg Gebruiker** knoop toe.

   ![ voeg gebruiker ](assets/add-user.png) toe

1. In **voeg gebruikers aan uw team** dialoogdoos toe, typ e-mailidentiteitskaart van de gebruiker u wilt toevoegen. Selecteer Adobe ID bij Type id als de Federated ID voor uw teamleden nog niet is ingesteld.

   ![ voeg gebruiker aan team ](assets/add-to-team.png) toe

1. In de **selectie van het Product**, selecteer het plusteken en selecteer dan **Adobe Experience Manager as a Cloud Service** en wijs de **Manager van de Plaatsing** en **het productprofielen van de Ontwikkelaar** aan de gebruiker toe.

   ![ wijs teamprofielen ](assets/assign-team.png) toe

1. Selecteer **sparen** en een welkome e-mail wordt verzonden naar de front-end ontwikkelaar u als gebruiker toevoegde.

De uitgenodigde front-end ontwikkelaar kan tot Cloud Manager toegang hebben door de verbinding in welkome e-mail te klikken en zich binnen te ondertekenen gebruikend hun Adobe ID.

## Overhandigen aan front-end ontwikkelaar {#handover}

Met een e-mailuitnodiging aan Cloud Manager onderweg naar de front-end ontwikkelaar, kunnen u en de AEM nu de front-end ontwikkelaar de resterende benodigde informatie geven om met aanpassingen te beginnen.

* A [ weg aan typische inhoud ](#example-page)
* De themabron die [ u ](#download-theme) downloadde
* De [ geloofsbrieven van de volmachtsgebruiker ](#proxy-user)
* De naam van het programma of URL aan het [ gekopieerd van Cloud Manager ](pipeline-setup.md#login)
* De ontwerpvereisten aan de voorzijde

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de AEM snelle reis van de Plaats hebt voltooid zou u moeten weten:

* Een front-end ontwikkelaar toevoegen als een gebruiker.
* Hoe te om de vereiste rollen aan de front-end ontwikkelaar te verlenen.

Bouw op deze kennis voort en zet uw AEM Snelle reis van de Aanmaak van de Plaats door het document [ opnieuw te bekijken Wint de Informatie van de Toegang van de Bewaarplaats van de it ](retrieve-access.md) voort, die perspectief aan de front-end ontwikkelaar exclusief schakelt en verklaart hoe de front-end ontwikkelaarsgebruikers Cloud Manager om tot de informatie van de gogegevensopslagplaats toegang te hebben.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de Snelle reis van de Verwezenlijking van de Plaats door het document [ te herzien verwerft de Geloofsbrieven van de Ontwikkelaar van het front-End ](retrieve-access.md) beweegt, zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de reis verder te gaan.

* [ Onboarding Reis ](/help/journey-onboarding/overview.md) - Deze gids dient als uw uitgangspunt om ervoor te zorgen dat uw teams opstelling zijn en toegang tot AEM as a Cloud Service hebben.
