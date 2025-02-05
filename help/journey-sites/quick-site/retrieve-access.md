---
title: Toegang tot Git Repository ophalen
description: Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot informatie in de git-opslagplaats.
exl-id: 3ef1cf86-6da4-4c09-9cfc-acafc8f6dd5c
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 3%

---

# Toegang tot Git Repository ophalen {#retrieve-access}

Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot informatie in de git-opslagplaats.

## Het verhaal tot nu toe {#story-so-far}

Als u een front-end ontwikkelaar slechts verantwoordelijk voor de aanpassing van het plaatsthema bent, hebt u geen kennis van hoe AEM opstelling was vereist en kan aan de [ Doelstelling ](#objective) sectie van dit document overslaan.

Als u ook de rol van Cloud Manager of AEM beheerder en front-end ontwikkelaar dient, leerde u in het vorige document van de reis van de Aanmaak van de AEM Snelle Plaats, [ Toegang van de Verlening tot de Voorste-Eind Ontwikkelaar ](grant-access.md), hoe te aan boord de front-end ontwikkelaar zodat hebben zij toegang tot de git bewaarplaats, en u zou nu moeten weten:

* Een front-end ontwikkelaar toevoegen als een gebruiker.
* Hoe te om de vereiste rollen aan de front-end ontwikkelaar te verlenen.

Dit artikel neemt de volgende stap om te tonen hoe de front-end ontwikkelaar de toegang van Cloud Manager gebruikt om geloofsbrieven terug te winnen om tot de AEM git bewaarplaats toegang te hebben.

Nu er een plaats is die op een malplaatje wordt gecreeerd, is er een pijpleidingsopstelling, wordt de front-end ontwikkelaar bewaakt en heeft alle informatie zij nodig hebben, verschuift dit artikel perspectief van de beheerders en exclusief aan de front-end ontwikkelaarrol.

## Doelstelling {#objective}

In dit document wordt uitgelegd hoe u, in de rol van de front-end ontwikkelaar, toegang kunt krijgen tot Cloud Manager en toegangsreferenties kunt ophalen naar de AEM git-opslagplaats. Na het lezen zult u:

* Begrijp op een hoog niveau wat Cloud Manager is.
* Uw referenties zijn opgehaald voor toegang tot de AEM, zodat u uw aanpassingen kunt doorvoeren.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis geldt voor de front-end ontwikkelaar.

## Vereisten {#requirements}

Met het gereedschap Snel site maken kunnen ontwikkelaars aan de voorkant onafhankelijk werken zonder kennis van AEM of hoe ze zijn ingesteld. Nochtans, moet de beheerder van Cloud Manager op de front-end ontwikkelaar in het projectteam en de AEM beheerder u van wat vereiste informatie voorzien. Controleer of u de volgende informatie hebt voordat u doorgaat.

* Van de AEM beheerder:
   * Themabronbestanden om aan te passen
   * Pad naar een voorbeeldpagina die als basis voor verwijzing moet worden gebruikt
   * Proxy-gebruikersgegevens om uw aanpassingen te testen op live AEM-inhoud
   * Voorste ontwerpvereisten
* Van de Cloud Manager-beheerder:
   * Een welkomstbericht van Cloud Manager waarin u op de hoogte wordt gesteld van toegang
   * De naam van het programma of de URL in Cloud Manager

Neem contact op met de AEM beheerder of de Cloud Manager-beheerder als u een van deze items mist.

Aangenomen wordt dat de front-end ontwikkelaar uitgebreide ervaring heeft met front-end ontwikkelingsworkflows en gangbare geïnstalleerde gereedschappen, waaronder:

* git
* npm
* webpack
* Een voorkeurseditor

## Cloud Manager begrijpen {#understanding-cloud-manager}

Cloud Manager stelt organisaties in staat zelf AEM te beheren in de cloud. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid.

Voor de front-end ontwikkelaar, is het de gateway aan:

* Toegang tot AEM informatie over de opslagplaats zodat u uw aanpassingen vooraf kunt doorvoeren.
* Begin de plaatsingspijpleiding om uw aanpassingen op te stellen.

De Cloud Manager-beheerder heeft u als Cloud Manager-gebruiker aangemeld. U zou een welkome e-mail gelijkend op het volgende moeten ontvangen hebben.

![ Welkome e-mail ](assets/welcome-email.png)

Neem contact op met de Cloud Manager-beheerder als u dit e-mailbericht niet hebt ontvangen.

## Toegang tot Cloud Manager {#access-cloud-manager}

1. Logboek in Adobe Experience Cloud bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) of klik de verbinding die in welkome e-mail wordt verstrekt.

1. Cloud Manager geeft een overzicht van de verschillende beschikbare programma&#39;s. Selecteer het bestand dat u wilt openen, zoals opgegeven door de Cloud Manager-beheerder. Als dit uw eerste front-end project voor AEMaaCS is, hebt u waarschijnlijk slechts één programma beschikbaar.

   ![ Selecterend een programma in Cloud Manager ](assets/cloud-manager-select-program.png)

U ziet nu een overzicht van uw programma. De pagina ziet er anders uit, maar is vergelijkbaar met dit voorbeeld.

![ overzicht van Cloud Manager ](assets/cloud-manager-overview.png)

## Toegang tot opslagplaats ophalen {#repo-access}

1. In de **sectie van Pijpleidingen** van de pagina van Cloud Manager, selecteer de **knoop van Info van de Reparatie van de Toegang**.

   ![ Pijpleidingen ](assets/pipelines-repo-info.png)

1. Het **dialoog van Info van de Bewaarplaats 0} {opent.**

   ![ Repo info ](assets/repo-info.png)

1. Selecteer **produceer wachtwoord** knoop om een wachtwoord voor zich tot stand te brengen.

1. Sla het gegenereerde wachtwoord op in een beveiligd wachtwoordbeheer. Het wachtwoord wordt nooit meer weergegeven.

1. Kopieer ook de **gebruikersbenaming** en **van de Git bevellijn** gebieden. U gebruikt deze gegevens later om toegang te krijgen tot het bericht.

1. Selecteer **dicht**.

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de AEM Quick Site Creation-reis hebt voltooid, moet u:

* Begrijp op een hoog niveau wat Cloud Manager is.
* Uw referenties zijn opgehaald voor toegang tot de AEM, zodat u uw aanpassingen kunt doorvoeren.

Bouw op deze kennis voort en ga uw AEM Snelle reis van de Aanmaak van de Plaats door het document [ opnieuw te bekijken aanpassen het Thema van de Plaats ](customize-theme.md) voort, waar u leert hoe het plaatsthema wordt gebouwd, hoe te, en hoe te om het gebruiken van levende AEM inhoud te testen.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de Snelle reis van de Verwezenlijking van de Plaats door het document [ te herzien aanpast het Thema van de Plaats ](customize-theme.md), zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige die concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de reis verder te gaan.

* [ de Documentatie van Adobe Experience Manager Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) - Onderzoek de documentatie van Cloud Manager voor volledige details van zijn eigenschappen.
