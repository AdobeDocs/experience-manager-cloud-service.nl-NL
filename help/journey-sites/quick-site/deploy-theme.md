---
title: Uw aangepaste thema implementeren
description: Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding.
source-git-commit: f8695dd8fdc9ffb203bab943c335ab2957df6251
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---


# Uw aangepaste thema implementeren {#deploy-your-customized-theme}

Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding.

>[!CAUTION]
>
>Het gereedschap Snel site maken is momenteel een technische voorvertoning. Het wordt ter beschikking gesteld voor test- en evaluatiedoeleinden en is niet bestemd voor gebruik in de productie, tenzij overeengekomen met Adobe Support.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Snelle reis van de Plaats, [Pas het thema Site aan,](customize-theme.md) u hebt geleerd hoe het thema is opgebouwd, hoe u het kunt aanpassen en hoe u het kunt testen met live AEM-inhoud. Nu moet u:

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

Als u de wijzigingen in de themaaanpassing hebt toegewezen aan de AEM-git-opslagplaats, kunt u [de pijpleiding die de beheerder creeerde](pipeline-setup.md) om de wijzigingen te implementeren.

1. Cloud Manager openen [zoals u deed om uw toegangsinformatie van de it terug te winnen.](retrieve-access.md) Op de **Overzicht** tabblad ziet u een kaart voor **Pijpleidingen**.

   ![Overzicht van Cloud Manager](assets/cloud-manager-overview.png)

1. Tik of klik op de ellips naast de pijplijn die u moet starten. Selecteer in het keuzemenu de optie **Uitvoeren**.

   ![Gasleiding uitvoeren](assets/run-pipeline.png)

1. In de **Pipet uitvoeren** bevestigingsvenster, tik of klik **Ja**.

   ![Uitvoeren pijpleiding bevestigen](assets/pipeline-confirm.png)

1. In de lijst van pijpleidingen, wijst de statuskolom erop dat uw pijpleiding nu loopt.

   ![Status van pijpleiding](assets/pipeline-running.png)

## Status pijplijn controleren {#pipeline-status}

U kunt de status van de pijpleiding controleren om de details van zijn vooruitgang op elk ogenblik te zien.

1. Tik of klik op de ellips naast de pijplijn.

   ![Details van pijpleiding weergeven](assets/view-pipeline-details.png)

1. Het venster van het pijpleidingsdetail toont de onderbreking van de vooruitgang van de pijpleiding.

   ![Details pijpleiding](assets/pipeline-details.png)

>[!TIP]
>
>In het venster van pijpleidingsdetails, kunt u tikken of klikken **Logbestand downloaden** voor om het even welke stap van de pijpleiding voor het zuiveren doeleinden als om het even welke stap zou moeten ontbreken. Het zuiveren van de pijpleiding valt buiten het bereik van deze reis. Raadpleeg de technische documentatie voor Cloud Manager in het dialoogvenster [Aanvullende bronnen](#additional-resources) van deze pagina.

## Valideer de Ingevoerde Aanpassingen {#view-customizations}

Zodra de pijpleiding volledig is, kunt u de beheerder informeren om de veranderingen te bevestigen. De beheerder zal dan:

1. Open de AEM ontwerpomgeving.
1. Navigeren naar [de site die de beheerder eerder heeft gemaakt.](create-site.md)
1. Bewerk een van de inhoudspagina&#39;s.
1. Zie de toegepaste wijzigingen.

![Toegepaste wijzigingen](assets/changes-applied.png)

## Einde van de reis? {#end-of-journey}

Gefeliciteerd! U hebt de AEM Quick Site Creation-reis voltooid! Nu moet u:

* Begrijp hoe de Manager van de Wolk en de front-end pijpleiding werken om front-end aanpassingen te beheren en op te stellen.
* Leer hoe u een AEM site maakt op basis van een sjabloon en hoe u het thema van de site downloadt.
* Hoe kan ik aan boord gaan van een front-end ontwikkelaar, zodat deze toegang heeft tot de AEM git-opslagplaats?
* Hoe te om een thema aan te passen en te testen gebruikend vooraf bepaalde AEM inhoud en die veranderingen in AEM greep te begaan.
* Hoe te om front-end aanpassing op te stellen gebruikend de pijpleiding.

U kunt nu de thema&#39;s van uw eigen AEM site aanpassen. AEM is echter een krachtig hulpmiddel en er zijn veel aanvullende opties beschikbaar. Bekijk enkele aanvullende bronnen die beschikbaar zijn in het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources) voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de reis Snel site maken te gaan door het document te bekijken [Uw aangepast thema implementeren,](deploy-theme.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [as a Cloud Service technische documentatie AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - Als u al een duidelijk inzicht hebt in AEM, kunt u de diepgaande technische documenten direct raadplegen.
* [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Als u meer informatie wilt over de functies van Cloud Manager, kunt u de diepgaande technische documenten direct raadplegen.
* [Op rollen gebaseerde machtigingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager heeft vooraf geconfigureerde rollen met de juiste machtigingen. Raadpleeg dit document voor meer informatie over deze rollen en hoe u deze kunt beheren.
* [Opslagplaatsen voor Cloud Manager](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) - Raadpleeg dit document als u meer informatie nodig hebt over het instellen en beheren van git-opslagruimten voor uw AEMaaCS-project.
* [CI/CD-pijpleiding configureren - Cloud Services](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) - Meer informatie over het instellen van pijpleidingen, zowel volledige stapel als front-end, vindt u in dit document.
* [Standaardsitemplate AEM](https://github.com/adobe/aem-site-template-standard) - Dit is de bewaarplaats GitHub van het AEM Standaardmalplaatje van de Plaats.
* [Sitethema AEM](https://github.com/adobe/aem-site-template-standard-theme-e2e) - Dit is de bewaarplaats GitHub van het Thema van de Plaats van de AEM.
* [npm](https://www.npmjs.com) - AEM thema&#39;s die worden gebruikt om sites snel te bouwen, zijn gebaseerd op npm.
* [webpack](https://webpack.js.org) - AEM thema&#39;s die worden gebruikt om sites snel op te bouwen, zijn gebaseerd op webpack.
* [Pagina&#39;s maken en ordenen](/help/sites-cloud/authoring/fundamentals/organizing-pages.md) - In deze handleiding wordt beschreven hoe u pagina&#39;s van uw AEM Site kunt beheren als u deze verder wilt aanpassen nadat u deze vanuit de sjabloon hebt gemaakt.
* [Hoe te met Pakket werken](/help/implementing/developing/tools/package-manager.md) - Pakketten maken het importeren en exporteren van inhoud in de opslagplaats mogelijk. In dit document wordt uitgelegd hoe u met pakketten werkt in AEM 6.5. Dit geldt ook voor AEMaaCS.
* [Onboarding Journaal](/help/journey-onboarding/home.md) - Deze gids dient als uitgangspunt om ervoor te zorgen dat uw teams opstelling zijn en toegang tot AEM as a Cloud Service hebben.
* [Documentatie Adobe Experience Manager Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) - Raadpleeg de documentatie van Cloud Manager voor meer informatie over de functies ervan.
* [Documentatie voor sitebeheer](/help/sites-cloud/administering/site-creation/create-site.md) - Ontdek de technische documentatie bij het maken van de site voor meer informatie over de functies van het gereedschap Snel maken.
