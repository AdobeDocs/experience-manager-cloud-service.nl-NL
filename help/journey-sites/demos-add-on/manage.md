---
title: Uw demo-sites beheren
description: Leer meer over de gereedschappen die beschikbaar zijn om u te helpen uw demosites te beheren en hoe u deze kunt verwijderen.
exl-id: 988c6e09-c43e-415f-8d61-998c294c5a11
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# Uw demo-sites beheren {#manage-demo-sites}

Leer meer over de gereedschappen die beschikbaar zijn om u te helpen uw demosites te beheren en hoe u deze kunt verwijderen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Reference Demos Add-on trip, [Site maken,](create-site.md) u creeerde een nieuwe demoplaats die op de malplaatjes van de Toevoeging van de Demo van de Verwijzing wordt gebaseerd. Nu moet u:

* Begrijp hoe te om tot het AEM auteursmilieu toegang te hebben.
* Weet hoe u een site kunt maken op basis van een sjabloon.
* Begrijp de grondbeginselen van het navigeren van de plaatsstructuur en het uitgeven van een pagina.

Als u ook [AEM Screens ingeschakeld voor uw demo-site,](screens.md) u zou ook moeten:

* De basisbeginselen van AEM Screens kennen.
* Begrijp de Web.Cafe demo-inhoud.
* Weet hoe u AEM Screens for We.Cafe kunt configureren.

Nu u uw eigen demosite hebt om te verkennen, worden in dit artikel de gereedschappen beschreven die beschikbaar zijn om u te helpen uw demosites te beheren en hoe u deze kunt verwijderen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe u de demosites kunt beheren die u hebt gemaakt. Na het lezen moet u:

* Begrijp hoe te om tot de Hulpmiddelen van de Demo van de Zelfbediening toegang te hebben.
* Weet welke hulpprogramma&#39;s voor u beschikbaar zijn.
* Hoe te om een bestaande demoplaats of malplaatje te schrappen.

## Toegang tot de Hulpprogramma&#39;s van de Demo van de Zelfbediening {#accessing-utilities}

Nu u uw eigen demosites hebt, wilt u waarschijnlijk weten hoe u deze kunt beheren. De pijpleiding stelde niet alleen de plaatsmalplaatjes op om uw inhoud van demoplaatsen te geven, zette het ook een reeks nut op om die plaatsen te beheren.

1. Selecteer in de AEM algemene navigatiebalk de optie **Gereedschappen** > **Demo van referenties** > **Referentie-demo-hulpprogramma**.

   ![Self-Service Demo-hulpprogramma&#39;s](assets/demo-utilities.png)

1. De Hulpprogramma&#39;s van de Demo van de verwijzing zijn een inzameling van nuttige functionaliteit die opstelling en controle uw milieu van Adobe Experience Manager zal helpen. De eerste weergave is de **Dashboard**, die dient als een statuscontrole van de omgeving en de demofunctionaliteit ervan.

   ![Dashboard](assets/dashboard.png)

De Hulpprogramma&#39;s van de Demo van de zelfbediening verstrekken verscheidene hulpmiddelen.

* **Sites verwijderen** - Selecteer de site die u wilt verwijderen in dit Adobe Experience Manager-exemplaar. Onthoud dat dit een destructieve actie is en dat deze actie niet ongedaan kan worden gemaakt als de actie eenmaal is gestart.
* **Sitesjablonen verwijderen** - Selecteer de Sjabloon site die u in dit Adobe Experience Manager-exemplaar wilt verwijderen. Voordat u een Sjabloon site verwijdert, moet u ervoor zorgen dat alle sites die verwijzen naar de sjabloon, ook worden verwijderd. Onthoud dat dit een destructieve actie is en dat deze actie niet ongedaan kan worden gemaakt als de actie eenmaal is gestart.
* **Cache primaire auteur** - Hiermee worden verschillende bronnen opgehaald in het Adobe Experience Manager-exemplaar, waardoor de ophaaltijden worden verkort. Het kan enkele seconden duren.
* **Android-toepassing** - Gereedschappen voor het installeren en starten van de Android-demonstratieapp. Een site maken op basis van de **WKND App met één pagina** deze pagina vullen. Gebruiken vanaf een Android-apparaat, emulator of Bluestacks.
* **Gebruikersvoorkeuren** - Pop-updialoogvensters met zelfstudies uitschakelen.
* **GraphQL instellen** - Het algemene GraphQL-eindpunt snel instellen.

## Demosites en sjablonen verwijderen {#deleting}

Nadat u een set AEM hebt getest, hebt u mogelijk niet langer uw demosite of zelfs de sjabloon waarop deze is gebaseerd nodig. Het is gemakkelijk om zowel demo plaatsen als plaatsmalplaatjes te schrappen.

1. Toegang krijgen tot de **Referentie-demo-hulpprogramma** en selecteert u **Sites verwijderen**.

   ![Sites verwijderen](assets/delete-sites.png)

1. De beschikbare sites worden in een lijst weergegeven. Controleer de site of sites die u wilt verwijderen en selecteer **Verwijderen**.

   >[!CAUTION]
   >
   >De plaats en malplaatjeschrapping is een destructieve actie en kan niet ongedaan worden gemaakt zodra in werking gesteld.

1. Bevestig het verwijderen van de site in het dialoogvenster.

   ![Verwijderen van site bevestigen](assets/confirm-site-delete.png)

1. AEM verwijdert de geselecteerde site of sites en toont de voortgang van de geselecteerde sites **Verwijderen** knoop was eerder.

   ![Voortgang verwijderen](assets/delete-progress.png)

De site wordt nu verwijderd.

U kunt sjablonen op dezelfde manier verwijderen onder de kop **Sitesjablonen verwijderen** in de **Referentie-demo-hulpprogramma**.

>[!CAUTION]
>
>Voordat u een Sjabloon site verwijdert, moet u ervoor zorgen dat alle sites die verwijzen naar de sjabloon, ook worden verwijderd.

## Einde van de reis? {#end-of-journey}

Gefeliciteerd! U hebt de reis AEM de Toelage van de Demos van de Verwijzing voltooid! Nu moet u:

* U hebt een basiskennis van Cloud Manager en begrijpt hoe pijpleidingen inhoud en configuratie leveren aan AEM.
* Begrijp hoe u met Cloud Manager een programma kunt maken.
* Weet hoe te om toe:voegen-aan van de Demos van de Verwijzing voor het nieuwe programma te activeren en een pijpleiding in werking te stellen om toe:voegen-op inhoud op te stellen.
* Begrijp hoe te om tot het AEM auteursmilieu toegang te hebben om een plaats tot stand te brengen die op een malplaatje wordt gebaseerd.
* Begrijp hoe te om tot de Hulpmiddelen van de Demo van de Zelfbediening toegang te hebben.
* Weet hoe u een bestaande demosite of sjabloon kunt verwijderen.

U bent nu klaar om de mogelijkheden van AEM te onderzoeken gebruikend uw eigen demo plaatsen. AEM is echter een krachtig hulpmiddel en er zijn veel aanvullende opties beschikbaar. Bekijk enkele aanvullende bronnen die beschikbaar zijn in het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources) voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

* [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Als u meer informatie wilt over de functies van Cloud Manager, kunt u de diepgaande technische documenten direct raadplegen.
* [Site maken](/help/sites-cloud/administering/site-creation/create-site.md) - Leer hoe u AEM kunt gebruiken om een site te maken met behulp van sitesjablonen om de stijl en structuur van uw site te definiëren.
* [Naamconventies voor pagina&#39;s AEM](/help/sites-cloud/authoring/sites-console/organizing-pages.md#page-name-restrictions-and-best-practices). - Zie deze pagina voor meer informatie over de conventies voor het ordenen van AEM pagina&#39;s.
* [AEM basisverwerking](/help/sites-cloud/authoring/basic-handling.md) - Onderzoek dit document als u nieuw bent om basisconcepten zoals navigatie en consoleorganisatie AEM te begrijpen.
* [as a Cloud Service technische documentatie AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - Als u al een duidelijk inzicht hebt in AEM, kunt u de diepgaande technische documenten direct raadplegen.
* [Sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md) - Raadpleeg dit document als u meer wilt weten over de structuur van sitesjablonen en hoe u deze gebruikt om sites te maken.
