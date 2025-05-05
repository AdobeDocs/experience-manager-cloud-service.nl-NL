---
title: Taken van ontwikkelaar- en implementatiebeheer
description: Zodra zij de systeembeheerder opstelling de noodzakelijke wolkenmiddelen hebben, leer hoe de ontwikkelaars en plaatsingsmanagers toegang kunnen hebben om toepassingen te ontwikkelen en pijpleidingen te gebruiken om hen op te stellen.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1397'
ht-degree: 0%

---


# Taken van ontwikkelaar- en implementatiebeheer {#developer-deployment-manager}

In dit facultatieve deel van de [ onboarding reis ](overview.md), leert u hoe de ontwikkelaars en plaatsingsmanagers tot git kunnen toegang hebben om toepassingen te ontwikkelen en pijpleidingen te gebruiken om hen op te stellen.

## Het verhaal tot nu toe {#story-so-far}

Je hebt een lange weg afgelegd op je instapreis! Gefeliciteerd! De systeembeheerder heeft de onboarding reis door vestiging de noodzakelijke wolkenmiddelen en het verlenen van toegang in het document [ voltooid Toewijzend AEM de Profielen van het Product ](assign-profiles-aem.md).

Op dit punt kunnen uw ontwikkelaars en implementatiemanagers beginnen met het maken van uw eigen toepassingen, terwijl uw AEM gebruikers kunnen beginnen met het maken van inhoud. In die zin is uw instapweigering voltooid en nu is het tijd om uw nieuwe AEM as a Cloud Service-systeem te gebruiken, wat dit document zal illustreren.

## Publiek {#audience}

Dit document wordt daarom geschreven vanuit het perspectief van de **ontwikkelaar** en **plaatsingsmanager**.

De systeembeheerder kan deze zelfde taken ook uitvoeren, maar over het algemeen worden deze rollen gehouden door verschillende gebruikers.

## Doelstelling {#objective}

Dit document is een aanvulling op de instapreis om de basistaken van een ontwikkelaar en plaatsingsmanager te tonen zodra de systeembeheerder alle gebruikers heeft gecontroleerd en de noodzakelijke wolkenmiddelen gecreeerd.

Nadat u dit document hebt gelezen, moet u:

* Als ontwikkelaar dient u te begrijpen hoe u uw Cloud Manager git-opslagruimten kunt openen en beheren.
* Als plaatsingsmanager, kan opstellings pijpleidingen en uw code in Cloud Manager opstellen.

## Ontwikkelaars en implementatiemanagers {#roles}

Zodra de systeembeheerder de belangrijkste onboarding taken van het creëren van gebruikers en het opzetten van wolkenmiddelen heeft voltooid, zijn de gebruikers over het algemeen het meest benieuwd om tot het systeem toegang te hebben de ontwikkelaars en plaatsingsmanagers. De reden hiervoor is dat zij de gebruikers zijn die verantwoordelijk zijn voor het bouwen van uw aangepaste toepassingen boven op AEM as a Cloud Service.

* **Ontwikkelaars** - Deze gebruikers hebben toegang tot de greet van Cloud Manager bewaarplaatsen waar zij de code voor uw AEM douanetoepassingen zullen beheren.
* **Managers van de Plaatsing** - Deze gebruikers gebruiken Cloud Manager om pijpleidingen tot stand te brengen en in werking te stellen die de code van de gokbewaarplaatsen aan uw lopende AEM milieu&#39;s opstellen.

Afhankelijk van uw organisatorische behoeften kunnen dezelfde gebruikers beide rollen hebben.

## Vereisten {#prerequisites}

Voordat u begint met de taken die in dit document worden beschreven als ontwikkelaar of implementatiebeheerder, moet u controleren of uw systeembeheerder alle stappen in deze instapreis heeft uitgevoerd. Dit betekent dat:

* Uw systeembeheerder heeft ontwikkelaars en plaatsingsmanagers aan hun respectieve productprofielen toegewezen.
* De ontwikkelaars moeten ook aan **worden toegewezen AEM Gebruikers** of **AEM Beheerders** productprofielen ook AEM gebruiken.
* Er zijn bronnen voor de cloud ingesteld.

## Toegang tot it {#accessing-git}

U kunt uw git-opslagruimten openen en beheren met behulp van het beheer van een git-account van Cloud Manager.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan **Pijpleidingen** kaart van uw **pagina van het Overzicht van het Programma** en vind de **Info van de Reparatie van de Toegang** knoop om tot uw Bewaarplaats van de it toegang te hebben en te beheren.

   ![ de knoop van Info van de Reparatie van de Toegang op de kaart van Milieu ](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klik de **knoop van Info van de Reactie van de Mening** om een dialoog aan mening te openen:

   * De URL naar de Cloud Manager-it-opslagplaats.
   * De git-gebruikersnaam.
   * Het wachtwoord van de it, waarvan de waarde wordt getoond wanneer **het Wachtwoord** knoop van het Kiezen wordt geklikt.

   ![ informatie van de Bewaarplaats ](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Met behulp van deze referenties kan de gebruiker een lokale kopie van de opslagplaats klonen en wijzigingen aanbrengen in die lokale opslagplaats, en wanneer hij klaar is, alle wijzigingen in de code terugsturen naar de externe gegevensopslagruimte in Cloud Manager.

## Instellingen pijpleiding {#setup-pipeline}

Zodra de ontwikkelaars hun douanecode aan uw gokbewaarplaatsen hebben toegevoegd, kan de plaatsingsmanager pijpleidingen tot stand brengen en uitvoeren om die code aan uw AEM milieu&#39;s op te stellen.

Voer de volgende stappen uit om uw eerste niet-productie implementatiepijplijn te maken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Heb toegang tot **Pijpleidingen** kaart van het het huisscherm van Cloud Manager. Klik **+ voeg** toe en selecteer **toevoegen niet-Productiepijpleiding**.

   ![ voeg niet-productiepijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png) toe

1. Op het **lusje van de Configuratie** van **voeg de dialoog van de Pijl van de Niet-Productie** toe, selecteer het type van niet-productiepijplijn u met toe te voegen. Voor dit voorbeeld, uitgezochte **Pijpleiding van de Plaatsing**.

   ![ toevoegen de pijpleidingsdialoog van de Niet-Productie ](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Verstrek de Naam van de Pijpleiding van de a **Niet-Productie** om uw pijpleiding samen met de volgende extra informatie te identificeren.

1. Voor de **Trigger van de Plaatsing** uitgezochte **Handboek** zodat de pijpleiding slechts loopt wanneer u het begint.

1. Klik **verdergaan**.

1. Op het **lusje van de Code van Source** van **voeg niet-Productie pijplijn** dialoog toe, moet u selecteren welk type van code de pijpleiding zou moeten verwerken. Voor dit voorbeeld, uitgezochte **Volledige Code van de Stapel**.

1. Op het **lusje van de Code van Source**, moet u de volgende opties bepalen.

   * **In aanmerking komende Milieu&#39;s van de Plaatsing** - u moet kiezen welk milieu waaraan de pijpleiding zou moeten opstellen.
   * **Bewaarplaats** - Deze opties bepalen waarvan git repo de pijpleiding de code zou moeten terugwinnen.
   * **Tak van het Git** - Deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * Voer de eerste paar tekens van de naam van de vertakking in en met de functie voor automatisch aanvullen van dit veld kunt u de overeenkomende vertakkingen vinden om u te helpen selecteren.

   ![ volledig-stapelpijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klik **sparen**.

U hebt nu uw eerste pijpleiding gecreeerd! De gebruikers met de rol van de plaatsingsmanager kunnen de pijpleiding van Cloud Manager nu beginnen UI.

## Implementeren {#deploy}

Nu de ontwikkelaars hun douanecode aan de gokbewaarplaatsen hebben toegevoegd en u een pijpleiding hebt die wordt gecreeerd om die code op te stellen, is het tijd om de pijpleiding uit te voeren om die code van git aan uw milieu eigenlijk te bewegen.

![ de kaart van Pijpleidingen in Cloud Manager ](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsis knoop naast de pijpleiding u in de vorige sectie creeerde en **looppas** van het menu selecteert.

1. De pijpleidingslooppas begint en door de **Status** kolom wordt vermeld.

U kunt de details van de looppas zien door de ellipsknoop opnieuw te klikken en **details van de Mening** te selecteren.

Gefeliciteerd! U hebt nu code van uw git bewaarplaats aan een non-production milieu opgesteld!

## Volgende functies {#whats-next}

Nu u dit document hebt gelezen, moet u:

* Als ontwikkelaar dient u te begrijpen hoe u uw Cloud Manager git-opslagruimten kunt openen en beheren.
* Als plaatsingsmanager, kan opstellings pijpleidingen en uw code in Cloud Manager opstellen.

U hebt de grond geraakt die als ontwikkelaar of plaatsingsmanager met niet alleen werkende kennis van Cloud Manager maar ook werkende milieu&#39;s, bewaarplaatsen en pijpleidingen loopt! Maar er is meer te leren over AEM as a Cloud Service die krachtige CI/CD hulpmiddelen. Controle uit de [ Extra sectie van Middelen ](#additional-resources) voor meer details.

Als u in bent geinteresseerd hoe de inhoudsauteurs toegang hebben en AEM als dienst van de Wolk gebruiken, ga op het definitieve deel van de onboarding reis voort, [ AEM de Taken van de Gebruiker ](aem-users.md).

>[!TIP]
>
>Nu u wordt betreden, kunt u [ leren hoe te om AEM toe:voegen-aan de Demo&#39;s van de Verwijzing ](/help/journey-sites/demos-add-on/overview.md) aan een zandbakmilieu met minimale AEM configuratie gemakkelijk toe te voegen en de krachtige eigenschappen van AEM met rijke die voorbeelden te kunnen testen op best-praktijken worden gebaseerd.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ die tot Opslagplaatsen ](/help/implementing/cloud-manager/managing-code/accessing-repos.md) toegang hebben - leer hoe te om tot uw git bewaarplaats toegang te hebben en te beheren gebruikend het de rekeningsbeheer van de zelfbediening git van Cloud Manager.
* [ Gebruikend git met Cloud Manager ](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - leer hoe te om Cloud Manager te gebruiken git bewaarplaatsen en hoe te om uw eigen op-gebouw klant-beheerde git bewaarplaats met Cloud Manager te integreren.
* [ de Lokale Opstelling van het Milieu van de Ontwikkeling ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=nl-NL) - Dit leerprogramma begeleidt u door vestiging een lokale ontwikkelomgeving voor Adobe Experience Manager (AEM) gebruikend AEM as a Cloud Service SDK.
* [ Begonnen Wend met AEM Sites - WKND Leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=nl-NL) - Dit meerdelige leerprogramma wordt ontworpen voor ontwikkelaars nieuw aan Adobe Experience Manager (AEM). In deze zelfstudie wordt de implementatie besproken van een AEM site voor een fictieve levensstijl, de WKND. De zelfstudie behandelt fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, Bewerkbare Malplaatjes, cliënt-zijbibliotheken, en componentenontwikkeling met Adobe Experience Manager Sites.
* [ Begonnen het Worden met SPA in AEM Gebruikend Reageren ](/help/implementing/developing/hybrid/getting-started-react.md) - Dit artikel stelt een steekproef SPA toepassing voor, verklaart hoe het wordt samengebracht, en laat u omhoog-en-lopende met uw eigen SPA snel gebruikend het Reageren kader worden.
* [ Begonnen het Worden met SPA in AEM Gebruikend Angular ](/help/implementing/developing/hybrid/getting-started-angular.md) - Dit artikel stelt een steekproef SPA toepassing voor, verklaart hoe het wordt samengebracht, en laat u omhoog-en-lopende met uw eigen SPA snel gebruikend het kader van de Angular worden.
* [ Zwaardeloze Reis van de Ontwikkelaar ](/help/journey-headless/developer/overview.md) - Begin hier voor een geleide cursus voor het ontwikkelen van headless toepassingen met AEM.
