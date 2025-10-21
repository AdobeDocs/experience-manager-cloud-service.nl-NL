---
title: Toegang verlenen aan de front-end ontwikkelaar
description: Aan boord van de front-end ontwikkelaars in Cloud Manager zodat ze toegang hebben tot uw AEM-site git-opslagplaats en -pijpleiding.
exl-id: 58e95c92-b859-4bb9-aa62-7766510486fd
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
recommendations: display, noCatalog
source-git-commit: 0a458616afad836efae27e67dbe145fc44bee968
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---


# Toegang verlenen aan de front-end ontwikkelaar {#grant-fed-access}

{{traditional-aem}}

Aan boord van de front-end ontwikkelaars in Cloud Manager zodat ze toegang hebben tot uw AEM-site git-opslagplaats en -pijpleiding.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de reis van de Aanmaak van de Plaats van AEM Snelle, [&#x200B; Opstelling Uw Pijpleiding &#x200B;](pipeline-setup.md), leerde u hoe te om een front-end pijpleiding tot stand te brengen om de aanpassing van het thema van uw plaats te beheren, en u zou nu moeten:

* Begrijp wat een front-end pijpleiding is.
* Weet hoe u een front-end pijpleiding in Cloud Manager kunt opzetten.

U moet nu uw front-end ontwikkelaar toegang tot Cloud Manager verlenen via het instapproces, zodat de front-end ontwikkelaar toegang heeft tot de AEM git-opslagplaats en de pijpleiding die u hebt gemaakt.

## Doelstelling {#objective}

Het proces om toegang tot Cloud Manager te verlenen en gebruikersrollen toe te wijzen aan uw gebruikers wordt genoemd onboarding. In dit document wordt een overzicht gegeven van de belangrijkste stappen voor het instappen van een front-end ontwikkelaar. Na het lezen weet u:

* Een front-end ontwikkelaar toevoegen als een gebruiker.
* Hoe te om de vereiste rollen aan de front-end ontwikkelaar te verlenen.

>[!TIP]
>
>Er is een volledige documentatietraject gewijd aan het aan boord gaan van uw team op AEM als dienst van de Wolk, verbonden aan in de [&#x200B; Extra sectie van Middelen &#x200B;](#additional-resources) van dit document, als u extra details over het proces nodig hebt.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis is van toepassing op de beheerder van Cloud Manager.

## Vereisten {#requirements}

* U moet een lid van **rol van BedrijfsEigenaar** in Cloud Manager zijn.
* U moet Admin van a **Sys** in Cloud Manager zijn.
* U moet toegang hebben tot de Admin Console.

## Voeg de Front-End Ontwikkelaar als Gebruiker toe {#add-fed-user}

Eerst moet u de front-end ontwikkelaar als gebruiker toevoegen door de Admin Console te gebruiken.

1. Teken in Admin Console in [&#x200B; https://adminconsole.adobe.com/ &#x200B;](https://adminconsole.adobe.com/).

1. Nadat u zich hebt aangemeld, krijgt u een overzichtspagina te zien die lijkt op de volgende afbeelding.

   ![&#x200B; overzicht van Admin Console &#x200B;](assets/admin-console.png)

1. Controleer de naam van de org in de rechterbovenhoek van het scherm en zorg ervoor dat u zich op de juiste org bevindt.

   ![&#x200B; de naam van de Controle org &#x200B;](assets/correct-org.png)

1. Selecteer **Adobe Experience Manager as a Cloud Service** van de **Producten en de diensten** kaart.

   ![&#x200B; Uitgezochte AEMaaCS &#x200B;](assets/select-aemaacs.png)

1. U ziet de lijst met vooraf geconfigureerde Cloud Manager-productprofielen. Als deze profielen niet worden weergegeven, neemt u contact op met de Cloud Manager-beheerder omdat u mogelijk niet de juiste machtigingen op uw org hebt.

   ![&#x200B; Profielen van het Product &#x200B;](assets/product-profiles.png)

1. Om de front-end ontwikkelaar aan de correcte profielen toe te wijzen, selecteer het **lusje van Gebruikers** en dan **voeg Gebruiker** knoop toe.

   ![&#x200B; voeg gebruiker &#x200B;](assets/add-user.png) toe

1. In **voeg gebruikers aan uw team** dialoogdoos toe, typ e-mailidentiteitskaart van de gebruiker u wilt toevoegen. Selecteer Adobe ID bij Type id als de Federated ID voor uw teamleden nog niet is ingesteld.

   ![&#x200B; voeg gebruiker aan team &#x200B;](assets/add-to-team.png) toe

1. In de **selectie van het Product**, selecteer het plusteken en selecteer dan **Adobe Experience Manager as a Cloud Service** en wijs de **Manager van de Plaatsing** en **het productprofielen van de Ontwikkelaar** aan de gebruiker toe.

   ![&#x200B; wijs teamprofielen &#x200B;](assets/assign-team.png) toe

1. Selecteer **sparen** en een welkome e-mail wordt verzonden naar de front-end ontwikkelaar u als gebruiker toevoegde.

De uitgenodigde front-end ontwikkelaar kan tot Cloud Manager toegang hebben door de verbinding in welkome e-mail te klikken en zich binnen te ondertekenen gebruikend hun Adobe ID.

## Overhandigen aan front-end ontwikkelaar {#handover}

Met een e-mailuitnodiging aan Cloud Manager onderweg naar de front-end ontwikkelaar, kunnen u en de AEM-beheerder de front-end ontwikkelaar nu de resterende benodigde informatie verschaffen om met aanpassingen te beginnen.

* A [&#x200B; weg aan typische inhoud &#x200B;](#example-page)
* De themabron die [&#x200B; u &#x200B;](#download-theme) downloadde
* De [&#x200B; geloofsbrieven van de volmachtsgebruiker &#x200B;](#proxy-user)
* De naam van het programma of URL aan het [&#x200B; gekopieerd van Cloud Manager &#x200B;](pipeline-setup.md#login)
* De ontwerpvereisten aan de voorzijde

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Quick Site Creation-reis hebt voltooid, moet u het volgende weten:

* Een front-end ontwikkelaar toevoegen als een gebruiker.
* Hoe te om de vereiste rollen aan de front-end ontwikkelaar te verlenen.

Bouw op deze kennis voort en zet uw reis van de Gemaakt van de Plaats van AEM Snelle door het document te herzien [&#x200B; de Informatie van de Toegang van de Toegang van de Bewaarplaats van de it &#x200B;](retrieve-access.md), die perspectief aan de front-end ontwikkelaar exclusief overschakelt en verklaart hoe de front-end ontwikkelaarsgebruikers Cloud Manager om tot informatie van de gogegevensopslagplaats toegang te hebben.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de Snelle reis van de Verwezenlijking van de Plaats door het document [&#x200B; te herzien verwerft de Geloofsbrieven van de Ontwikkelaar van het front-End &#x200B;](retrieve-access.md) beweegt, zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de reis verder te gaan.

* [&#x200B; Onboarding Reis &#x200B;](/help/journey-onboarding/overview.md) - Deze gids dient als uw uitgangspunt om ervoor te zorgen dat uw teams opstelling zijn en toegang tot AEM as a Cloud Service hebben.
