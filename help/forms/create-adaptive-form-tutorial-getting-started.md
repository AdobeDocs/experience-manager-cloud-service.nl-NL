---
title: Aan de slag met Adaptive Forms.
description: Leer hoe u Adaptieve Forms met responsieve mobiele apparaten kunt maken met onze stapsgewijze zelfstudie. Deze formulieren worden naadloos aangepast op verschillende apparaten, zodat u een vloeiende ervaring hebt.
keywords: Adaptive Forms, responsieve Forms, HTML5 Forms
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
exl-id: b59cb56c-9629-48e4-b5c9-a861013a1360
source-git-commit: af58a784f24f212962ad73f11015fb788493d8b5
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---

# Een adaptief formulier maken (kerncomponenten) - zelfstudie

Op deze dag en deze leeftijd verwachten gebruikers een mobiele ervaring in al hun interacties, en formulieren vormen hierop geen uitzondering. Met adaptieve formulieren kunt u formulieren maken die niet alleen gebruiksvriendelijk zijn, maar ook de betrokkenheid van gebruikers verbeteren en de tijd die nodig is om deze formulieren in te vullen verminderen.

Deze zelfstudie biedt een stapsgewijze gids voor het maken van een adaptief formulier. Het is opgedeeld in een gebruikscase en diverse hulplijnen, die u elk leren hoe u een nieuwe functie aan het aangepaste formulier kunt toevoegen.

Aan het einde van de zelfstudie kunt u het volgende doen:

* Een adaptief formulier en het bijbehorende gegevensmodel maken
* Stijl uw adaptieve formulier
* Bedrijfsregels maken met de editor voor aangepaste formulierregels
* Aangepaste formuliervelden vooraf invullen
* E-handtekeningen toevoegen aan uw formulier
* Protect uw formulier van bots met Google reCAPTCHA
* Het aangepaste formulier lokaliseren voor verschillende talen
* Uw formulier configureren om gestructureerde gegevens te produceren
* Stel uw formulier in om gegevens naar een REST-eindpunt te verzenden
* Publish uw adaptieve formulier


## Waarom een formulier maken dat is gebaseerd op kerncomponenten?

AEM Forms biedt Foundation Components en Core Components (Basiscomponenten) voor het maken van formulieren. Core Components is de moderne en aanbevolen methode om nieuwe formulieren te maken. Waarom Core Components gebruiken? Deze componenten zijn lichtgewicht, opensource (beschikbaar op github), bieden een geweldige Google Lighthouse- en web vitals score, voldoen aan toegankelijkheidsvereisten en bieden alle vertrouwde functies van AEM Sites (zoals versioning en lokalisatie). Bovendien zijn deze componenten gemakkelijker te maken, kunt u hun verschijning gemakkelijk aanpassen volgens de branding richtlijnen van uw organisatie. Deze zijn niet afhankelijk van derden. Ontwikkelaars met kennis van JavaScript en CSS kunnen deze componenten eenvoudig aanpassen.

![ waarom creeer de Componenten van de Kern gebaseerd Adaptief Forms? Deze componenten zijn lichtgewicht, gemakkelijker om te vormen, bieden hoge vuurthouse score, steunen toegankelijkheidsnormen, gemakkelijk aanpasbaar, open-bronnen, beschikbaar op github, geen afhankelijkheid van derdebibliotheken, en hebben bijna geen het leren kromme voor AEM ontwikkelaars en AEM Auteurs bovenop het AEM Forms Core Components alle eigenschappen van AEM WCM Core Componenten.](/help/forms/assets/cc-core-components-benefits.png){width="50%"}

## Gebruiksscenario: gestroomlijnde voorkwalificatie voor thuislening met Adaptive Forms

In deze zelfstudie bouwt u een adaptief formulier voor een grote bank. Het gebruiksgeval is:

Potentiële kopers bezoeken de website of de afdeling van de bank om opties voor woningkredieten te verkennen. Het traditionele toepassingsproces is lang en overweldigend en vereist vaak vooraf documentatie. Hierdoor worden sommige kopers ervan weerhouden het proces te starten, waardoor zowel de leidende generatie van de bank als het vermogen van de koper om met vertrouwen naar hun droomhuis te zoeken, worden belemmerd.

U bent belast met het ontwikkelen van een interactief formulier voor de voorkwalificatie van woningkredieten. Dit formulier zou basisinformatie verzamelen, de kredietnemer vooraf kwalificeren op basis van hun input, geschatte bedragen van de leningen, potentiële betalingsbehoeften voor neerwaartse betalingen en rentetarieven op basis van verschillende soorten leningen aanbieden. Voorgekwalificeerde gebruikers zouden rechtstreeks via het voorkwalificatieformulier een volledige leningaanvraag kunnen starten.

Het formulier wordt samengesteld met behulp van adaptieve formulieren. Dit maakt een persoonlijke ervaring mogelijk en verzamelt tegelijkertijd de nodige financiële gegevens voor een nauwkeurige voorkwalificatie van woningkredieten.

Nadat u de zelfstudie hebt voltooid, ziet het formulier er als volgt uit en werkt het als volgt:

![ voeg hier een het werk vorm toe ](/help/forms/assets/cc-tutorial-final-form.png)

## Ontwikkelomgeving instellen

U kunt het Adaptief formulier rechtstreeks op uw lokale computer maken en testen voordat u het implementeert in een Cloud Service-omgeving. Adobe biedt een AEM SDK voor lokale ontwikkeling waarmee u

* Formulieren lokaal maken, aanpassen en testen.
* Formulierthema&#39;s ontwerpen en configuraties lokaal samenstellen,
* Implementeer uw voltooide middelen eenvoudig in de cloud.

Lokale ontwikkeling met AEM SDK bespaart u tijd en vereenvoudigt het ontwikkelingsproces


**klaar om te beginnen?**

1. [ de ontwikkelingshulpmiddelen van de opstelling voor AEM Projecten ](/help/forms/setup-local-development-environment.md#set-up-development-tools-for-aem-projects): Download en installeer de recentste versie van [ Java 11™ ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#local-development-environment-set-up), [ Git ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-git), [ Node.js (npm) ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#node-js), en [ Gemaakt ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-maven). Installeer ook een duidelijk-tekstredacteur, zijn de voorbeelden in dit leerprogramma gebaseerd op de Code van Visual Studio.

1. [ installeer de AEM SDK ](/help/forms/setup-local-development-environment.md#set-up-local-experience-manager-environment-for-development): Download en installeer de recentste versie van AEM SDK. Dit biedt de essentiële instrumenten voor AEM ontwikkeling. Noteer de versie van AEM SDK.

   ![ software-Distributie ](/help/forms/assets/software-distribution.png)

   ![ installeer AEM SDK ](/help/forms/assets/start-aem-sdk.png)

1. [ voeg toe:voegen-op van AEM Forms ](/help/forms/setup-local-development-environment.md#add-forms-archive-to-local-author-and-publish-instances-and-configure-forms-specific-users) toe: Download en installeer toe:voegen-op aanpassing van AEM Forms aan de versie van uw AEM SDK van het [ Portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads).
   ![ install-name-forms-add-on ](/help/forms/assets/install-aem-forms-add-on.png)

   +++ AEM Forms-invoegtoepassing installeren:

   AEM Forms-invoegtoepassing installeren:

   1. Stop AEM SDK.
   1. Voeg het add-on (.far)-bestand van AEM Forms toe aan de map `AEM SDK/crx-quickstart/install` ,
   1. Start AEM SDK opnieuw.

   +++

1. [ vorm gebruikerstoestemmingen ](/help/forms/setup-local-development-environment.md#configure-users-and-permissions): Creeer gebruikers met ontwikkeling, auteursrecht, en andere toestemmingen en voeg deze gebruikers aan vooraf bepaalde vormgroepen toe.


1. [ voegt de Aangepaste malplaatjes van Forms ](/help/forms/setup-local-development-environment.md#set-up-a-development-project-for-forms-based-on-experience-manager-archetype) toe: Gebruik AEM Archetypes 48 of later om een nieuw AEM project tot stand te brengen en het op uw AEM SDK op te stellen. Het project voegt adaptieve Forms-sjablonen toe aan uw AEM SDK.

   ![ Aangepaste Malplaatjes van de Vorm ](/help/forms/assets/adaptive-forms-templates.png)

   +++ Voeg Aangepaste Forms-sjablonen toe aan uw AEM SDK:

   1. Voer de onderstaande opdracht uit om een AEM project te maken.

      ```
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="48" -D appTitle=securbank -D appId=securbank -D groupId=com.securbank -D includeFormsenrollment="y" -D aemVersion="cloud"
      ```

      ![ AEM-Archetyoe-Project ](/help/forms/assets/aem-archetype-project.png)

   1. Implementeer het project in uw lokale ontwikkelomgeving. U kunt het volgende bevel gebruiken om aan uw lokale ontwikkelomgeving op te stellen

      ```
      cd securbank
      
      mvn -PautoInstallPackage clean install
      ```

   Nadat u het AEM project hebt geïmplementeerd, kunt u Adaptieve Forms-sjablonen in uw omgeving zien.

   +++


Voor gedetailleerde instructies en geleidelijke gids bij vestiging uw lokale de ontwikkelomgeving van AEM Forms, verwijs het [ opstelling lokale ontwikkelomgeving voor AEM Forms ](/help/forms/setup-local-development-environment.md) artikel.



## Volgende stap

Nadat u de ontwikkelomgeving hebt geconfigureerd, kunt u een adaptief formulier maken. In het volgende artikel leert u om

* Een adaptief formulier maken op basis van de lege sjabloon
* Indelingsvelden die u wilt weergeven en waarop u eenvoudig gegevens wilt accepteren.
* Bekijk een voorbeeld van het formulier.

<!-- 

### Step 2: Create Form Data Model

A form data model lets you connect an adaptive form to disparate data sources. For example, AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. You can use the form data model with an adaptive form to retrieve, update, delete, and add data to connected data sources.

Goals of article:

* Create the form data model using Rest endpoint.
* Add data model objects so you can form the data model.
* Configure read and write services for the form data model.
* Test form data model and configured services with test data.

### Step 4: Apply rules to adaptive form fields

AEM Forms provide an editor to write rules on adaptive form objects. These rules define actions to trigger on form objects based on preset conditions, user inputs, and user actions on the form. It helps ensure accuracy and speeds up the form-filling experience.

Goals:

* Create and apply rules to adaptive form fields.
* Use rules to trigger form data model services to update the data to database.

### Step 5: Style your adaptive form

Adaptive forms provide OOTB themes and allows you to customize an existing theme to make a brand specific theme. 


A theme contains styling details for components and panels, and you can reuse a theme in different forms. Styles include properties such as background colors, state colors, transparency, alignment, and size. When you apply the theme to your form, the specified style reflects on corresponding components of your form.

Goals:

* Apply an out of the box theme to an adaptive form.
* Create your brand specific theme.


### Step 6: Publish your adaptive form

You can publish adaptive forms as a stand-alone form (single page application), include in AEM Sites page, or include in a non-AEM Sites page.

Goals:

* Publish the adaptive form as an AEM Page.
* Embed the adaptive form in an AEM Sites Page.
* Embed the adaptive form in an external webpage (a non-AEM webpage hosted outside AEM).

-->
