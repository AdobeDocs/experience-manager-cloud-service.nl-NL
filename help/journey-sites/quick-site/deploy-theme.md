---
title: Uw aangepaste thema implementeren
description: Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding.
exl-id: fe065972-39db-4074-a802-85895c701efd
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 0%

---

# Uw aangepaste thema implementeren {#deploy-your-customized-theme}

Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de reis van de Aanmaak van de AEM Snelle Plaats, [ pas het Thema van de Plaats ](customize-theme.md) aan, leerde u hoe het thema wordt gebouwd, hoe te om het aan te passen, en hoe te om het te testen gebruikend levende AEM inhoud, en u zou nu moeten:

* Begrijp de basisstructuur van het sitethema en hoe u dit kunt bewerken.
* Zie hoe u themaaanpassingen kunt testen met echte AEM inhoud via lokale proxy.
* Weet hoe u uw wijzigingen in de AEM-git-opslagplaats kunt doorvoeren.

U kunt de definitieve stap nu nemen en de pijpleiding gebruiken om hen op te stellen.

## Doelstelling {#objective}

Dit document verklaart hoe te om het thema op te stellen gebruikend de pijpleiding. Na het lezen moet u:

* Weet hoe u een pijpleidingsplaatsing kunt teweegbrengen.
* Zie hoe u de implementatiestatus kunt controleren.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis geldt voor de front-end ontwikkelaar.

## De pijplijn starten {#start-pipeline}

Nadat u de veranderingen van de themaaanpassing in de AEM git bewaarplaats hebt begaan, kunt u [ de pijpleiding in werking stellen die de beheerder ](pipeline-setup.md) creeerde om de veranderingen op te stellen.

1. Teken in Cloud Manager [ aangezien u deed om uw informatie van de it toegang ](retrieve-access.md) terug te winnen en tot uw programma toegang te hebben. Op het **Overzicht** lusje, ziet u een kaart voor **Pijpleidingen**.

   ![ overzicht van Cloud Manager ](assets/cloud-manager-overview.png)

1. Selecteer de ellips naast de pijpleiding u moet beginnen. Van het drop-down menu, uitgezochte **Looppas**.

   ![ de pijpleiding van de Looppas ](assets/run-pipeline.png)

1. In de **bevestigingsdialoog van de Pijpleiding van de Looppas**, uitgezochte **ja**.

   ![ Bevestig pijpleidingslooppas ](assets/pipeline-confirm.png)

1. In de lijst van pijpleidingen, wijst de statuskolom erop dat uw pijpleiding nu loopt.

   ![ Pijpleiding die status ](assets/pipeline-running.png) in werking stelt

## Status pijplijn controleren {#pipeline-status}

U kunt de status van de pijpleiding controleren om de details van zijn vooruitgang op elk ogenblik te zien.

1. Selecteer de ellips naast uw pijpleiding.

   ![ de pijpleidingsdetails van de Mening ](assets/view-pipeline-details.png)

1. Het venster van het pijpleidingsdetail toont de onderbreking van de vooruitgang van de pijpleiding.

   ![ details van de Pijpleiding ](assets/pipeline-details.png)

>[!TIP]
>
>In het venster van pijpleidingsdetails, kunt u **Logboek van de Download** voor om het even welke stap van de pijpleiding voor het zuiveren doeleinden selecteren als om het even welke stap zou moeten ontbreken. Het zuiveren van de pijpleiding is voorbij het werkingsgebied van deze reis. Zie de technische documenten voor Cloud Manager in de [ Extra sectie van Middelen ](#additional-resources) van deze pagina.

## Valideer de Ingevoerde Aanpassingen {#view-customizations}

Zodra de pijpleiding volledig is, kunt u de beheerder informeren om de veranderingen te bevestigen. De beheerder zal dan:

1. Open de AEM ontwerpomgeving.
1. Navigeer aan [ de plaats de eerder gecreeerd beheerder ](create-site.md).
1. Bewerk een van de inhoudspagina&#39;s.
1. Zie de toegepaste wijzigingen.

![ toegepaste Veranderingen ](assets/changes-applied.png)

## Einde van de reis? {#end-of-journey}

Gefeliciteerd! U hebt de AEM Quick Site Creation-reis voltooid! Nu moet u:

* Begrijp hoe Cloud Manager en de front-end pijpleiding werken om front-end aanpassingen te beheren en op te stellen.
* Leer hoe u een AEM site maakt op basis van een sjabloon en hoe u het thema van de site downloadt.
* Hoe kan ik aan boord gaan van een front-end ontwikkelaar, zodat deze toegang heeft tot de AEM git-opslagplaats?
* Hoe te om een thema aan te passen en te testen gebruikend vooraf bepaalde AEM inhoud en die veranderingen in AEM greep te begaan.
* Hoe te om front-end aanpassing op te stellen gebruikend de pijpleiding.

U kunt nu de thema&#39;s van uw eigen AEM site aanpassen. Nochtans alvorens u begint verschillende het werkstromen te creëren gebruikend veelvoudige voorste pijpleidingen, herzie het document [ Ontwikkelend Plaatsen met de Voorste-Eind Pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md). Het kan u helpen optimaal uit uw front-end ontwikkeling door te halen:

* Behoud van één enkele bron van waarheid.
* Handhaving van een scheiding van zorgen.

AEM is een krachtig hulpmiddel en er zijn veel extra opties beschikbaar. Controle uit enkele extra middelen beschikbaar in de [ Extra sectie van Middelen ](#additional-resources) om meer over de eigenschappen te leren u in deze reis zag.

## Aanvullende bronnen {#additional-resources}

Hieronder vindt u een aantal aanvullende bronnen die dieper ingaan op bepaalde concepten die in dit document worden genoemd.

* [ Gebruikend het Spoorweg van de Plaats om Uw Thema van de Plaats te beheren ](/help/sites-cloud/administering/site-creation/site-rail.md) - leer de krachtige eigenschappen van het spoor van de Plaats om u te helpen uw plaatsthema met inbegrip van het downloaden van themabronnen en het beheren van themaversies gemakkelijk aanpassen en beheren.
* [ AEM as a Cloud Service technische documentatie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=nl-NL) - als u reeds een vast begrip van AEM hebt, kunt u de diepgaande technische documenten direct willen raadplegen.
* [ documentatie van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=nl-NL) - als u meer details over de eigenschappen van Cloud Manager zou willen, kunt u de diepgaande technische documenten direct willen raadplegen.
* [ Rol Gebaseerde Toestemmingen ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html?lang=nl-NL) - Cloud Manager heeft pre-gevormde rollen met aangewezen toestemmingen. Zie dit document voor details over deze rollen en hoe te om hen te beheren.
* [ Opslagplaatsen van Cloud Manager ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) - als u meer informatie over nodig hebt om git bewaarplaatsen voor uw project te vestigen en te beheren AEMaaCS, dit document zien.
* [ vorm CI/CD Pijpleiding - Cloud Servicen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) - leer meer details over vestiging pijpleidingen, zowel volledige stapel als vooreind, in dit document.
* [ AEM het StandaardMalplaatje van de Plaats ](https://github.com/adobe/aem-site-template-standard) - dit is de bewaarplaats GitHub van het AEM Standaardmalplaatje van de Plaats.
* [ AEM het Thema van de Plaats ](https://github.com/adobe/aem-site-template-standard-theme-e2e) - dit is de bewaarplaats GitHub van het Thema van de Plaats van de AEM.
* [ npm ](https://www.npmjs.com) - AEM thema&#39;s worden gebruikt om plaatsen snel te bouwen zijn gebaseerd op npm die.
* [ webpack ](https://webpack.js.org) - AEM thema&#39;s worden gebruikt om sites snel te bouwen baseren zich op webpack die.
* [ het Organiseren van Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/organizing-pages.md) - Deze gids bepaalt hoe te om pagina&#39;s van uw AEM plaats te organiseren.
* [ Creërend Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/creating-pages.md) - Deze gids bepaalt hoe te om nieuwe pagina&#39;s aan uw plaats toe te voegen.
* [ het Leiden Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/managing-pages.md) - Deze gids bepaalt hoe te om de pagina&#39;s van uw plaats te beheren met inbegrip van het bewegen, het kopiëren, en het schrappen.
* [ hoe te met Pakket ](/help/implementing/developing/tools/package-manager.md) te werken - de Pakketten laten het invoeren en het uitvoeren van bewaarplaatsinhoud toe. In dit document wordt uitgelegd hoe u met pakketten werkt in AEM 6.5. Dit geldt ook voor AEMaaCS.
* [ Onboarding Reis ](/help/journey-onboarding/overview.md) - Deze gids dient als uw uitgangspunt om ervoor te zorgen dat uw teams opstelling zijn en toegang tot AEM as a Cloud Service hebben.
* [ de Documentatie van Adobe Experience Manager Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=nl-NL) - Onderzoek de documentatie van Cloud Manager voor volledige details van zijn eigenschappen.
* [ Documentatie van het Beleid van de Plaats ](/help/sites-cloud/administering/site-creation/create-site.md) - Controle uit de technische documenten op plaatsverwezenlijking voor meer details op de Snelle eigenschappen van het hulpmiddel van de Aanmaak van de Plaats.
* [ het Ontwikkelen van Plaatsen met de Voorste-Eind Pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) - Dit document beschrijft sommige overwegingen om zich van bewust te zijn zodat kunt u het volledige potentieel uit het front-end ontwikkelingsproces krijgen gebruikend de front-end pijpleiding.
