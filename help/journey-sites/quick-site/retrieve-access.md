---
title: Toegang tot Git Repository ophalen
description: Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot gegevensopslagruimte.
exl-id: 3ef1cf86-6da4-4c09-9cfc-acafc8f6dd5c
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 3%

---

# Toegang tot Git Repository ophalen {#retrieve-access}

Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot gegevensopslagruimte.

## Het verhaal tot nu toe {#story-so-far}

Als u een front-end ontwikkelaar bent die alleen verantwoordelijk is voor de aanpassing van het site-thema, hebt u geen kennis nodig van de manier waarop AEM is ingesteld en kunt u naar de [Doelstelling](#objective) van dit document.

Als u ook de rol van Cloud Manager of AEM beheerder en front-end ontwikkelaar vervult, hebt u in het vorige document van de AEM Quick Site Creation-reis geleerd, [Toegang verlenen aan de Front-End Developer,](grant-access.md) hoe u de front-end ontwikkelaar aan boord kunt nemen, zodat ze toegang hebben tot de git-opslagplaats, en u moet nu weten:

* Een front-end ontwikkelaar toevoegen als een gebruiker.
* Hoe te om de vereiste rollen aan de front-end ontwikkelaar te verlenen.

Dit artikel neemt de volgende stap om te tonen hoe de front-end ontwikkelaar de toegang van de Manager van de Wolk gebruikt om geloofsbrieven terug te winnen om tot de AEM git bewaarplaats toegang te hebben.

Nu er een plaats is die op een malplaatje wordt gecreeerd, is er een pijpleidingsopstelling, wordt de front-end ontwikkelaar bewaakt en heeft alle informatie zij nodig hebben, verschuift dit artikel perspectief van de beheerders en exclusief aan de front-end ontwikkelaarrol.

## Doelstelling {#objective}

In dit document wordt uitgelegd hoe u, in de rol van de front-end ontwikkelaar, toegang kunt krijgen tot Cloud Manager en toegangsreferenties kunt ophalen naar de AEM git-opslagplaats. Na het lezen zult u:

* Begrijp op een hoog niveau wat Cloud Manager is.
* Uw referenties zijn opgehaald voor toegang tot de AEM, zodat u uw aanpassingen kunt doorvoeren.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis geldt voor de front-end ontwikkelaar.

## Vereisten {#requirements}

Met het gereedschap Snel site maken kunnen ontwikkelaars aan de voorkant onafhankelijk werken zonder kennis van AEM of hoe ze zijn ingesteld. Nochtans, moet de beheerder van de Manager van de Wolk aan boord de front-end ontwikkelaar in het projectteam en de AEM beheerder u van wat vereiste informatie voorzien. Controleer of u de volgende informatie hebt voordat u doorgaat.

* Van de AEM beheerder:
   * Themabronbestanden om aan te passen
   * Pad naar een voorbeeldpagina die als basis voor verwijzing moet worden gebruikt
   * Proxy-gebruikersgegevens om uw aanpassingen te testen op live AEM-inhoud
   * Voorste ontwerpvereisten
* Via de beheerder van Cloud Manager:
   * Een welkomstbericht van Cloud Manager waarin u op de hoogte wordt gesteld van toegang
   * De naam van het programma of de URL in Cloud Manager

Neem contact op met de beheerder van de AEM of de beheerder van de cloud als u een van deze items ontbreekt.

Aangenomen wordt dat de front-end ontwikkelaar uitgebreide ervaring heeft met front-end ontwikkelingsworkflows en gangbare geïnstalleerde gereedschappen, waaronder:

* git
* npm
* webpack
* Een voorkeurseditor

## Werken met Cloud Manager {#understanding-cloud-manager}

Met Cloud Manager kunnen organisaties zelf AEM beheren in de cloud. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid.

Voor de front-end ontwikkelaar, is het de gateway aan:

* Toegang tot AEM informatie over de opslagplaats zodat u uw aanpassingen vooraf kunt doorvoeren.
* Begin de plaatsingspijpleiding om uw aanpassingen op te stellen.

De beheerder van Cloud Manager heeft u aangemeld als gebruiker van Cloud Manager. U zou een welkome e-mail gelijkend op het volgende moeten ontvangen hebben.

![Welkom-e-mail](assets/welcome-email.png)

Neem contact op met de beheerder van Cloud Manager als u deze e-mail niet hebt ontvangen.

## Cloud Manager openen {#access-cloud-manager}

1. Aanmelden bij Adobe Experience Cloud [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) of klik op de koppeling in de welkomstmail.

1. Cloud Manager geeft de verschillende beschikbare programma&#39;s weer. Selecteer het bestand dat u wilt openen, zoals opgegeven door de beheerder van Cloud Manager. Als dit uw eerste front-end project voor AEMaaCS is, hebt u waarschijnlijk slechts één programma beschikbaar.

   ![Een programma selecteren in Cloud Manager](assets/cloud-manager-select-program.png)

U ziet nu een overzicht van uw programma. De pagina ziet er anders uit, maar is vergelijkbaar met dit voorbeeld.

![Overzicht van Cloud Manager](assets/cloud-manager-overview.png)

## Toegang tot opslagplaats ophalen {#repo-access}

1. In de **Pijpleidingen** van de pagina Cloud Manager selecteert u de optie **Repo-info openen** knop.

   ![Pijpleidingen](assets/pipelines-repo-info.png)

1. De **Info opslagplaats** wordt geopend.

   ![Repo-info](assets/repo-info.png)

1. Selecteer de **Wachtwoord genereren** om een wachtwoord voor uzelf te maken.

1. Sla het gegenereerde wachtwoord op in een beveiligd wachtwoordbeheer. Het wachtwoord wordt nooit meer weergegeven.

1. Kopieer ook de **gebruikersnaam** en **Git, opdrachtregel** velden. U gebruikt deze gegevens later om toegang te krijgen tot het bericht.

1. Selecteren **Sluiten**.

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de AEM Quick Site Creation-reis hebt voltooid, moet u:

* Begrijp op een hoog niveau wat Cloud Manager is.
* Uw referenties zijn opgehaald voor toegang tot de AEM, zodat u uw aanpassingen kunt doorvoeren.

Gebaseerd op deze kennis en doorgaan met uw AEM snelle site-creatie door het document opnieuw te bekijken [Pas het thema Site aan,](customize-theme.md) Hier leert u hoe het thema van de site is opgebouwd, hoe u het kunt aanpassen en hoe u het gebruik van live AEM-inhoud kunt testen.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de reis Snel site maken te gaan door het document te bekijken [Pas het thema Site aan,](customize-theme.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [Documentatie Adobe Experience Manager Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) - Verken de documentatie van Cloud Manager voor meer informatie over de functies ervan.
