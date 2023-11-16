---
title: Taken van ontwikkelaar- en implementatiebeheer
description: Zodra zij de systeembeheerder opstelling de noodzakelijke wolkenmiddelen hebben, leer hoe de ontwikkelaars en plaatsingsmanagers toegang kunnen hebben om toepassingen te ontwikkelen en pijpleidingen te gebruiken om hen op te stellen.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1411'
ht-degree: 0%

---


# Taken van ontwikkelaar- en implementatiebeheer {#developer-deployment-manager}

In dit facultatieve deel van [aan boord gaan,](overview.md) u leert hoe de ontwikkelaars en plaatsingsmanagers tot git kunnen toegang hebben om toepassingen te ontwikkelen en pijpleidingen te gebruiken om hen op te stellen.

## Het verhaal tot nu toe {#story-so-far}

Je hebt een lange weg afgelegd op je instapreis! Gefeliciteerd! De systeembeheerder heeft de instapreis voltooid door de benodigde cloudbronnen in te stellen en toegang te verlenen in het document [AEM productprofielen toewijzen.](assign-profiles-aem.md)

Op dit punt kunnen uw ontwikkelaars en implementatiemanagers beginnen met het maken van uw eigen toepassingen, terwijl uw AEM gebruikers kunnen beginnen met het maken van inhoud. In die zin is uw instapsysteem voltooid en nu is het tijd om uw nieuwe AEM as a Cloud Service systeem te gebruiken, wat dit document zal illustreren.

## Publiek {#audience}

Dit document is daarom geschreven vanuit het perspectief van de **ontwikkelaar** en **implementatiebeheer**.

De systeembeheerder kan deze zelfde taken ook uitvoeren, maar over het algemeen worden deze rollen gehouden door verschillende gebruikers.

## Doelstelling {#objective}

Dit document is een aanvulling op de instapreis om de basistaken van een ontwikkelaar en plaatsingsmanager te tonen zodra de systeembeheerder alle gebruikers heeft gecontroleerd en de noodzakelijke wolkenmiddelen gecreeerd.

Nadat u dit document hebt gelezen, moet u:

* Als ontwikkelaar dient u te begrijpen hoe u toegang kunt krijgen tot en beheer kunt maken van uw cloudbeheeropslagruimten.
* Als implementatiebeheerder kunt u pijpleidingen instellen en uw code implementeren in Cloud Manager.

## Ontwikkelaars en implementatiemanagers {#roles}

Zodra de systeembeheerder de belangrijkste onboarding taken van het creëren van gebruikers en het opzetten van wolkenmiddelen heeft voltooid, zijn de gebruikers over het algemeen het meest benieuwd om tot het systeem toegang te hebben de ontwikkelaars en plaatsingsmanagers. Dit komt omdat zij de gebruikers verantwoordelijk zijn voor de bouw van uw douanetoepassingen bovenop AEM as a Cloud Service.

* **Ontwikkelaars** - Deze gebruikers hebben toegang tot de Git-opslagruimten van Cloud Manager, waar ze de code voor uw AEM aangepaste toepassingen zullen beheren.
* **Implementatiebeheerders** - Deze gebruikers gebruiken Cloud Manager om pijpleidingen te maken en uit te voeren die de code van de git-opslagplaatsen aan uw lopende AEM milieu&#39;s opstellen.

Afhankelijk van uw organisatorische behoeften kunnen dezelfde gebruikers beide rollen hebben.

## Vereisten {#prerequisites}

Voordat u begint met de taken die in dit document worden beschreven als ontwikkelaar of implementatiebeheerder, moet u controleren of uw systeembeheerder alle stappen in deze instapreis heeft uitgevoerd. Dit betekent dat:

* Uw systeembeheerder heeft ontwikkelaars en plaatsingsmanagers aan hun respectieve productprofielen toegewezen.
* Ontwikkelaars moeten ook worden toegewezen aan **AEM** of **AEM** ook de productprofielen gebruiken AEM.
* Er zijn bronnen voor de cloud ingesteld.

## Toegang tot it {#accessing-git}

U kunt toegang krijgen tot en beheer van uw git-opslagruimten via het beheer van uw eigen git-account vanuit Cloud Manager.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Navigeren naar **Pijpleidingen** kaart van uw **Programmaoverzicht** pagina en zoek de **Repo-info openen** om toegang te krijgen tot uw Git Repository en deze te beheren.

   ![De knop Repo-info openen op de milieucokaart](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klik op de knop **Repo-info weergeven** om een dialoogvenster te openen dat wordt weergegeven:

   * De URL naar de gegevensopslagruimte van Cloud Manager.
   * De git-gebruikersnaam.
   * Het wachtwoord voor de it, waarvan de waarde wordt weergegeven wanneer de optie **Wachtwoord genereren** wordt geklikt.

   ![Informatie over opslagplaats](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Met behulp van deze referenties kan de gebruiker een lokale kopie van de opslagplaats klonen en wijzigingen aanbrengen in die lokale opslagplaats, en wanneer hij klaar is, alle wijzigingen in de code terugsturen naar de externe opslagplaats voor code in Cloud Manager.

## Instellingen pijpleiding {#setup-pipeline}

Zodra de ontwikkelaars hun douanecode aan uw gokbewaarplaatsen hebben toegevoegd, kan de plaatsingsmanager pijpleidingen tot stand brengen en uitvoeren om die code aan uw AEM milieu&#39;s op te stellen.

Voer de volgende stappen uit om uw eerste niet-productie implementatiepijplijn te maken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Toegang krijgen tot de **Pijpleidingen** kaart van het startscherm van Cloud Manager. Klikken **+Toevoegen** en selecteert u **Niet-productiepijpleiding toevoegen**.

   ![Niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Op de **Configuratie** tabblad van het **Niet-productiepijpleiding toevoegen** selecteert u het type niet-productiepijplijn dat u wilt toevoegen. In dit voorbeeld selecteert u **Implementatiepijp**.

   ![Dialoogvenster Niet-productiepijplijn toevoegen](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geef een **Naam niet-productiepijpleiding** om uw pijpleiding samen met de volgende extra informatie te identificeren.

1. Voor de **Implementatieactivering** selecteren **Handmatig** zodat de pijpleiding slechts loopt wanneer u het begint.

1. Klikken **Doorgaan**.

1. Op de **Broncode** tabblad van het **Niet-productiepijpleiding toevoegen** moet u selecteren welk type code de pijplijn moet verwerken. In dit voorbeeld selecteert u **Volledige stapelcode**.

1. Op de **Broncode** moet u de volgende opties definiëren.

   * **In aanmerking komende implementatieomgevingen** - U moet kiezen welk milieu waarop de pijpleiding zou moeten opstellen.
   * **Bewaarplaats** - Deze opties bepalen waarvan git de pijpleiding de code zou moeten terugwinnen.
   * **Git Branch** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.

   ![Volledige pijplijn](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klikken **Opslaan**.

U hebt nu uw eerste pijpleiding gecreeerd! Gebruikers met de rol van implementatiebeheer kunnen de pijpleiding nu starten vanuit de interface van Cloud Manager.

## Implementeren {#deploy}

Nu de ontwikkelaars hun douanecode aan de gokbewaarplaatsen hebben toegevoegd en u een pijpleiding hebt die wordt gecreeerd om die code op te stellen, is het tijd om de pijpleiding uit te voeren om die code van git aan uw milieu eigenlijk te bewegen.

![Pipelinekaart in Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op de ovaalknop naast de pijplijn die u in de vorige sectie hebt gemaakt en selecteer **Uitvoeren** in het menu.

1. De pijpleidingslooppas begint en door **Status** kolom.

U kunt de details van de run zien door nogmaals op de knop voor ovaal te klikken en vervolgens **Details weergeven**.

Gefeliciteerd! U hebt nu code van uw git bewaarplaats aan een non-production milieu opgesteld!

## Volgende functies {#whats-next}

Nu u dit document hebt gelezen, moet u:

* Als ontwikkelaar dient u te begrijpen hoe u toegang kunt krijgen tot en beheer kunt maken van uw cloudbeheeropslagruimten.
* Als implementatiebeheerder kunt u pijpleidingen instellen en uw code implementeren in Cloud Manager.

U hebt de grond geraakt die als ontwikkelaar of plaatsingsmanager met niet alleen het werken kennis van de Manager van de Wolk maar ook het werk milieu&#39;s, bewaarplaatsen en pijpleidingen loopt! Maar er is meer te leren over de krachtige CI/CD-tools van AEM as a Cloud Service. Kijk uit de [Aanvullende bronnen](#additional-resources) voor meer informatie.

Als u geïnteresseerd bent in de manier waarop auteurs van inhoud toegang krijgen tot en AEM gebruiken als Cloud-service, gaat u verder naar het laatste gedeelte van de instapreis. [AEM gebruikerstaken.](aem-users.md)

>[!TIP]
>
>Nu je aan boord bent, kun je [Leer hoe te om de AEMInvoegtoepassing van de Demo van de Verwijzing gemakkelijk toe te voegen](/help/journey-sites/demos-add-on/overview.md) in een sandbox-omgeving met minimale AEM configuratie en de krachtige functies van AEM kunnen testen met uitgebreide voorbeelden op basis van best practices.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Toegang tot opslagplaatsen](/help/implementing/cloud-manager/managing-code/accessing-repos.md) - Leer hoe u uw git-opslagplaats kunt openen en beheren met behulp van het beheer van de git-account voor zelfbediening vanuit Cloud Manager.
* [Git gebruiken met Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - Leer hoe u de git-opslagruimten van Cloud Manager kunt gebruiken en hoe u uw eigen, door de klant beheerde git-opslagplaats op locatie kunt integreren met Cloud Manager.
* [Lokale ontwikkelomgeving instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) - Deze zelfstudie begeleidt u bij het instellen van een lokale ontwikkelomgeving voor Adobe Experience Manager (AEM) met behulp van de AEM as a Cloud Service SDK.
* [Aan de slag met AEM Sites - WKND-zelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) - Deze meerdelige zelfstudie is ontworpen voor ontwikkelaars die nog geen ervaring hebben met Adobe Experience Manager (AEM). In deze zelfstudie wordt de implementatie besproken van een AEM site voor een fictieve levensstijl, de WKND. De zelfstudie behandelt fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, Bewerkbare Malplaatjes, cliënt-zijbibliotheken, en componentenontwikkeling met Adobe Experience Manager Sites.
* [Aan de slag met SPA in AEM Reageren gebruiken](/help/implementing/developing/hybrid/getting-started-react.md) - Dit artikel bevat een voorbeeld SPA toepassing, legt uit hoe deze is samengesteld en laat u snel aan de slag met uw eigen SPA met behulp van het React-framework.
* [Aan de slag met SPA in AEM Angular gebruiken](/help/implementing/developing/hybrid/getting-started-angular.md) - In dit artikel wordt een voorbeeld SPA toepassing gepresenteerd, wordt uitgelegd hoe deze wordt samengesteld en kunt u snel met uw eigen SPA aan de slag met het raamwerk voor Angulars.
* [Headless Developer Journey](/help/journey-headless/developer/overview.md) - Begin hier voor een geleide cursus voor het ontwikkelen van toepassingen zonder kop met AEM.
