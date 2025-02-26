---
title: AEM AS A CLOUD SERVICE DEVELOPER CONSOLE - BETA
description: Meer weten over CRXDE Lite en AEM as a Cloud Service Developer Console?
feature: Developing
role: Admin, Architect, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: 11c52f6782df3b608bedd4b120c145a7a80a0702
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 0%

---

# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

>[!NOTE]
>
>In dit artikel wordt een vernieuwde ervaring beschreven voor de AEM Cloud Service Developer Console, die nu bètaversie is. Sommige klanten kunnen tot het toegang hebben door een knoop bij de klassieke bovenkant van UI te klikken. Adobe verwelkomt eventuele feedback van u door deze naar `aemcs-new-devconsole-ui-beta@adobe.com` te verzenden. Voor informatie over de klassieke AEM Developer Console, zie [ dit artikel ](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

De AEM as a Cloud Service Developer Console bevat een set gereedschappen voor foutopsporing in Cloud-omgevingen. Het kan door een per-milieu verbinding in Cloud Manager worden betreden.

>[!NOTE]
>AEM as a Cloud Service Developer Console zou niet met zo ook genoemde [*Adobe Developer Console* ](https://developer.adobe.com/developer-console/) moeten worden verward.
>


<!--
There are multiple ways of accessing it:

1. Launch from Cloud Manager  

1. Type a url that can be determined by adjusting the Author or Publish service urls as follows:
   ```  
   https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com
   ```  

1. As a shortcut, the following Cloud Manager CLI command can be used to launch the AEM as a Cloud Service Developer Console based on an environment parameter described below:    
   ```
   aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>
   ```
-->

Ontwikkelaars hebben toegang tot de functies die hieronder worden beschreven:

## OSGi-bundels {#osgi-bundles}

![ Nieuw scherm van Bundles OSGi in Console Dev ](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Een overzicht van de pakketten OSGI die in het geselecteerde omgevingstype worden opgesteld. Hiermee wordt een zoekopdracht in volledige tekst ingeschakeld.
* Het is nuttig om informatie over de daadwerkelijke staat van bundels in het milieu te krijgen. U kunt informatie ophalen zoals geëxporteerde pakketten, geïmporteerde pakketten, gebruikte services en meer.
* Ontwikkelaars willen de werkelijke omgeving controleren en controleren of de bundel doet wat ze verwachten.
* **gebruik-geval van het voorbeeld:** Een versiewaaier van een gebiedsdeel wordt gespecificeerd in uw bundel. Er gaat iets mis in de afhankelijkheid. U wilt controleren welke versie van het gebiedsdeel in uw bundel wordt getelegrafeerd. Als u dit wilt controleren, gaat u naar de bundeldetails en gebruikt u bundels/pakketten importeren om te controleren welke bundelversie of pakketversie tijdens runtime wordt gebruikt. Met deze informatie, kunt u uw bepaalde waaier van de gebiedsdeelversie aanpassen of uw code aanpassen.

## Java-pakketten {#java-packages}

![ het lusje van de Pakketten van Java in Dev Console UI ](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Een zoekprompt die u kunt gebruiken om te zoeken in pakketten die actief zijn in het OSGI-systeem van de omgeving. Op deze locatie kunt u zien welke bundel het pakket exporteert (of levert) en u kunt zien welke bundel het pakket importeert (of gebruikt). U kunt ook controleren op dubbele pakketten (hetzelfde pakket, verschillende versies), wat in sommige gevallen problemen kan veroorzaken.
* **gebruik-geval van het voorbeeld:** De douanedienst die de [ dynamische klassenloader ](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) gebruikt laadt een klasse zonder een versie te specificeren. Aangezien meerdere bundels verschillende versies exporteren, varieert de implementatie en dit leidt tot gedragswijzigingen. De ontwikkelaar wil controleren welke pakketten in het milieu zonder het eigenschapmodel te analyseren zijn. Ze zoeken naar het pakket en bekijken alle geëxporteerde versies. Deze mogelijkheid geeft hen de informatie om een betere versiewaaier in te gaan.

## Servlets {#servlets}

![ Servlets lusje in de Dev Console UI ](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Een zoekprompt waarin u een pad met kiezers en een extensie met GET of POST kunt opgeven. Het verstrekt dan de resultaten van servlets in orde van voorkeur die het verzoek in Sling behandelt.
* **het gebruiksgeval van het Voorbeeld:** u hebt servlet OSGI die op een verzoek en drukoutput aan de reactie zou moeten activeren. In plaats van de verwachte uitvoer wordt de reactie echter leeg geretourneerd. U moet controleren of een andere servlet voorrang heeft op uw servlet vanwege specifiekere kiezers, `resourceType` , uitbreidingen of rangschikkingen. U zoekt naar het verwachte pad en zoekt of een andere servlet actief is met een hogere rang. Vervolgens bepaalt u of u uw servlet boven in de rij kunt zetten door bijvoorbeeld kiezers toe te voegen.

## Services {#services}

![ het lusje van de Diensten in Dev Console UI ](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Gelijkaardig aan de mening van Componenten OSGI, maar gebaseerd op de diensten. U kunt snel zoeken in welke services bepaalde eigenschappen worden aangeboden.

## OSGi-componenten {#osgi-components}

![ het Lusje van Componenten OSGi in Dev Console UI ](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Een overzicht van de componenten OSGI die in het geselecteerde omgevingstype aanwezig zijn. Hiermee wordt een zoekopdracht in volledige tekst ingeschakeld.
* Je krijgt de live status van OSGI componenten in de omgeving. U kunt zien aan welke services het voldoet, de bundel die het levert en het activeringstype (onmiddellijk of vertraagd).
* **het gebruiksgeval 1 van het Voorbeeld:** als ontwikkelaar, moet u controleren of een component die met een configuratie wordt geactiveerd actief in een specifiek milieu is. De reden is dat het verwachte gedrag niet optreedt. U kijkt eenvoudig omhoog de component in het onderzoek en controle om te zien of is de component actief of niet.
* **het gebruiksgeval 2 van het Voorbeeld:** u wilt zien welke uit-van-de-dooscomponenten in het milieu beschikbaar zijn en de diensten identificeren zij steunen. Op deze manier kun je meer leren over Adobe Experience Manager as a Cloud Service. U kunt ze uitchecken in de lijst met componenten.

## Integrations {#integrations}

![ het lusje van Integraties in de Dev Console UI ](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Beheerders kunnen tokens voor services en ontwikkelaars genereren, hernoemen en verwijderen.

## Bewaarplaats {#repository}

* Opent [ browser van de Bewaarplaats ](/help/implementing/developing/tools/repository-browser.md).

## Statusfouten/query&#39;s {#status-dumps-queries}

![ de Fouten/het lusje van Vragen van de Status in Dev Console UI ](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Een volledige tekst of JSON-stortplaats van de huidige staat van bundels, pakketten, configuraties, de diensten, componenten, sling banen of de definities van Oak.
* Dit is vooral nuttig als de ontwikkelaar een onverwachte status heeft ontdekt en deze status voor andere ontwikkelaars wil communiceren of documenteren. Het downloaden van de stortplaats geeft u een momentopname van de staat voor recentere verwijzing.

## Configuraties {#configurations}

![ het lusje van Configuraties in Dev Console UI ](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Een doorzoekbare lijst met configuraties die actief zijn in de omgeving. U kunt zien welke eigenschappen door de configuraties worden verstrekt door de detailspagina uit te checken.
* **het gebruiksgeval van het Voorbeeld:** De ontwikkelaar van A wil ervoor zorgen dat de configuraties die zij hebben gespecificeerd eigenlijk in het milieu aanwezig zijn. Als de configuratie ontbreekt, kunnen zij het eigenschapmodel of de wijze of de omslag van de configuratielooppas controleren.

Voor productieprogramma&#39;s wordt met de &quot;Cloud Manager - Developer Role&quot; in Adobe Admin Console de toegang tot de AEM as a Cloud Service Developer Console gecontroleerd. Voor sandboxprogramma&#39;s kan elke gebruiker met een productprofiel dat AEM toegang biedt, de Developer Console gebruiken. Voor alle programma&#39;s is de &quot;Cloud Manager - Developer Role&quot; vereist voor statusdumps en toegang tot de browser van de repository. Als u gegevens van zowel auteur- als publicatieservices wilt weergeven, moeten gebruikers ook zijn toegewezen aan het productprofiel van AEM-gebruikers of AEM-beheerders op beide services.

Voor meer informatie over vestiging gebruikerstoestemmingen, zie [ Documentatie van Cloud Manager ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/users-and-roles).

