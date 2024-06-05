---
title: Demo-site maken
description: Maak een demosite in AEM op basis van een bibliotheek met vooraf geconfigureerde sjablonen.
exl-id: e76fd283-12b2-4139-9e71-2e145b9620b1
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# Demo-site maken {#creating-a-site}

Maak een demosite in AEM op basis van een bibliotheek met vooraf geconfigureerde sjablonen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Reference Demos Add-on trip, [Programma maken](create-program.md) u nam de eerste configuratiestap om een programma voor testende doeleinden tot stand te brengen en gebruikte een pijpleiding om toe:voegen-op inhoud op te stellen. Nu moet u:

* Begrijp hoe u met Cloud Manager een programma kunt maken.
* Zorg dat u weet hoe u de Add-on Reference Demos voor het nieuwe programma activeert.
* Kan een pijpleiding in werking stellen om toe:voegen-op inhoud op te stellen.

In dit artikel wordt de volgende stap van het proces beschreven door een site of AEM Screens-project te maken in AEM op basis van de sjablonen van de invoegtoepassing voor demo van referentie.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om een plaats tot stand te brengen die op de malplaatjes van de Toevoeging van de Demo van de Verwijzing wordt gebaseerd. Na het lezen moet u:

* Begrijp hoe te om tot het AEM auteursmilieu toegang te hebben.
* Weet hoe u een site kunt maken op basis van een sjabloon.
* Begrijp de grondbeginselen van het navigeren van de plaatsstructuur en het uitgeven van een pagina.

## Een demopsite of schermproject maken {#create-site}

Zodra de pijpleiding toe:voegen-aan van de Demo van de Verwijzing heeft opgesteld, kunt u tot het AEM auteursmilieu toegang hebben om demoplaatsen tot stand te brengen die op de toe:voegen-op inhoud worden gebaseerd.

1. Selecteer op de pagina met het programmaoverzicht in Cloud Manager de koppeling naar de AEM ontwerpomgeving.

   ![Toegang tot ontwerpomgeving](assets/access-author.png)

1. Selecteer in het hoofdmenu van AEM **Sites**.

   ![Toegang tot sites](assets/access-sites.png)

1. Selecteer in de siteconsole de optie **Maken** rechtsboven in het scherm en selecteert u **Site van sjabloon** in de vervolgkeuzelijst.

   ![Site maken van sjabloon](assets/create-site-from-template.png)

1. De wizard voor het maken van de site wordt gestart. In de linkerkolom kunt u de demo malplaatjes zien die de pijpleiding aan uw auteursinstantie opstelde. Selecteer een optie om deze te selecteren en geef details weer in de rechterkolom. Als u AEM Screens wilt testen of demo, moet u **We.Cafe-sitesjabloon**. Selecteren **Volgende**.

   ![Wizard Site maken](assets/site-creation-wizard.png)

1. Geef in het volgende scherm een titel op voor uw site of schermproject. U kunt een sitenaam opgeven of genereren op basis van de titel, als u deze weglaat. Selecteren **Maken**.

   * De titel van de site wordt weergegeven in de titelbalk van browsers.
   * De sitenaam wordt onderdeel van de URL.
   * De sitenaam moet voldoen aan AEM conventies voor paginanamen, waarvan de details beschikbaar zijn in het dialoogvenster [Aanvullende bronnen](#additional-resources) sectie.

   ![Sitegegevens](assets/site-details.png)

1. Het maken van de site wordt bevestigd door een dialoogvenster. Selecteren **Gereed**.

   ![Site maken voltooid](assets/site-creation-complete.png)

U hebt nu uw eigen demo-site gemaakt!

## Demo-site gebruiken {#use-site}

Nu uw demosite is gemaakt, kunt u deze op dezelfde manier gebruiken als elke andere site in AEM.

1. De site wordt nu weergegeven in de siteconsole.

   ![Nieuwe demosite in siteconsole](assets/new-demo-site.png)

1. Zorg ervoor dat in de rechterbovenhoek van het scherm de consoleweergave is ingesteld op **Kolomweergave**.

   ![Kolomweergave](assets/column-view.png)

1. Selecteer de site om de structuur en inhoud ervan te bekijken. De kolomweergave wordt voortdurend uitgebreid terwijl u door de inhoudsstructuur van de demosite navigeert.

   ![Sitestructuur](assets/site-structure.png)

1. Selecteer een pagina om deze te selecteren en selecteer vervolgens **Bewerken** in de werkbalk.

   ![Pagina selecteren](assets/select-page.png)

1. U kunt de pagina net als elke andere AEM inhoudspagina bewerken, zoals onderdelen of elementen toevoegen of bewerken en de functionaliteit van AEM testen.

   ![Pagina bewerken](assets/edit-page.png)

Gefeliciteerd! U kunt nu de inhoud van uw demo-site verder verkennen en alles ontdekken wat AEM te bieden heeft via de inhoud met best practices van de Add-on voor demo-weergave van verwijzingen.

Maak aanvullende sites op basis van andere sjablonen om meer AEM functionaliteit te verkennen.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Toelage van de Demo van de Verwijzing hebt voltooid zou u moeten:

* Begrijp hoe te om tot het AEM auteursmilieu toegang te hebben.
* Weet hoe u een site kunt maken op basis van een sjabloon.
* Begrijp de grondbeginselen van het navigeren van de plaatsstructuur en het uitgeven van een pagina.

U kunt nu de functies van AEM testen met add-on inhoud. U hebt twee opties om uw reis voort te zetten:

* Als u AEM Screens-inhoud volledig wilt demo- en testen, controleert u of u een site hebt geïmplementeerd op basis van de **We.Cafe-sitesjabloon** zoals hierboven beschreven en doorgaan [Schakel AEM Screens for Your Demo Site in.](screens.md)
* Als u alleen Sites-inhoud wilt demo, gaat u verder [Uw demosites beheren,](manage.md) waar u meer te weten komt over de gereedschappen die beschikbaar zijn om u te helpen uw demosites te beheren en hoe u deze kunt verwijderen.

## Aanvullende bronnen {#additional-resources}

* [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Als u meer informatie wilt over de functies van Cloud Manager, kunt u de diepgaande technische documenten direct raadplegen.
* [Site maken](/help/sites-cloud/administering/site-creation/create-site.md) - Leer hoe u AEM kunt gebruiken om een site te maken met behulp van sitesjablonen om de stijl en structuur van uw site te definiëren.
* [Naamconventies voor pagina&#39;s AEM](/help/sites-cloud/authoring/sites-console/organizing-pages.md#page-name-restrictions-and-best-practices). - Zie deze pagina voor meer informatie over de conventies voor het ordenen van AEM pagina&#39;s.
* [AEM basisverwerking](/help/sites-cloud/authoring/basic-handling.md) - Onderzoek dit document als u nieuw bent om basisconcepten zoals navigatie en consoleorganisatie AEM te begrijpen.
