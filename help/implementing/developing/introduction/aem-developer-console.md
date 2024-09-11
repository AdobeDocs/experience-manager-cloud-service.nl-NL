---
title: AEM as a Cloud Service Developer Console (Beta)
description: Meer informatie over CRX/DE Lite en AEM as a Cloud Service Developer Console
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 16379d9cb7cdf876502205c12a233a95b410a67a
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

>[!NOTE]
>
>In dit artikel wordt een vernieuwde ervaring beschreven voor de AEM Cloud Service Developer Console, die nu in bèta beschikbaar is, en die beschikbaar is voor sommige klanten door op een knop boven aan de klassieke gebruikersinterface te klikken. We stellen eventuele feedback op prijs die u naar `aemcs-new-devconsole-ui-beta@adobe.com` kunt verzenden. Voor informatie over de klassieke AEM Developer Console, zie [ dit artikel ](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

## AEM as a Cloud Service-ontwikkelingstools {#aem-as-a-cloud-service-development-tools}

>[!NOTE]
>AEM as a Cloud Service Developer Console zou niet met zo ook genoemde [*Adobe Developer Console* ](https://developer.adobe.com/developer-console/) moeten worden verward.
>

Klanten hebben toegang tot de CRXDE-lijst in de ontwikkelomgeving van de auteur, maar niet in het stadium of de productie. Er kan niet bij uitvoering naar de onveranderlijke opslagplaats (`/libs`, `/apps` ) worden geschreven, zodat dit tot fouten leidt.

In plaats daarvan kan de Repository Browser worden gestart vanuit de AEM as a Cloud Service Developer Console, waarmee een alleen-lezen weergave in de opslagplaats wordt geboden voor alle omgevingen op auteur-, publicatie- en voorvertoningslagen. Voor meer informatie zie [ Browser van de Bewaarplaats ](/help/implementing/developing/tools/repository-browser.md).

Er is een set tools beschikbaar voor foutopsporing in AEM as a Cloud Service-ontwikkelomgevingen in de AEM as a Cloud Service Developer Console for RDE-, Dev-, stage- en productieomgevingen. De URL kan worden bepaald door de URL van de Auteur of Publish-service als volgt aan te passen:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als sneltoets kunt u de volgende Cloud Manager CLI-opdracht gebruiken om de AEM as a Cloud Service Developer Console te starten op basis van een omgevingsparameter die hieronder wordt beschreven:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Zie [ de Informatie van de Versie ](/help/release-notes/home.md) voor meer informatie.

Ontwikkelaars kunnen statusinformatie genereren en diverse bronnen oplossen.

Zoals hieronder wordt geïllustreerd, omvat de beschikbare statusinformatie de staat van bundels, componenten, configuraties OSGI, eikenindexen, diensten OSGI, en het Sling banen.

### OSGi-bundels {#osgi-bundles}

![ Nieuw scherm van Bundles OSGi in Console Dev ](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Dit levert een overzicht op van de OSGI-bundels die op het geselecteerde omgevingstype worden geïmplementeerd. Hiermee wordt een zoekopdracht in volledige tekst ingeschakeld.
* Het is nuttig om informatie over de daadwerkelijke staat van bundels in het milieu te krijgen. U kunt informatie ophalen zoals geëxporteerde pakketten, geïmporteerde pakketten, gebruikte services en meer.
* Ontwikkelaars willen de werkelijke omgeving controleren en controleren of de bundel doet wat ze verwachten.
* **gebruik-geval van het voorbeeld:** Een versiewaaier van een gebiedsdeel wordt gespecificeerd in uw bundel. Er gaat iets mis in de afhankelijkheid. U wilt controleren welke versie van het gebiedsdeel in uw bundel wordt getelegrafeerd. Om dit te controleren, gaat u naar de bundeldetails, en gebruikt het invoeren bundels/pakketten om te controleren welke bundelversie of pakketversie bij runtime wordt gebruikt om te weten te komen. Met deze informatie kunt u uw bepaalde waaier van de gebiedsdeelversie aanpassen of uw code aanpassen.

### Java-pakketten {#java-packages}

![ het lusje van de Pakketten van Java in Dev Console UI ](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Dit verstrekt een onderzoeksherinnering u aan onderzoekspakketten kunt gebruiken die in het systeem van OSGI van het milieu actief zijn. Op deze locatie kunt u zien welke bundel het pakket exporteert (of levert) en u kunt zien welke bundel het pakket importeert (of gebruikt). U kunt ook controleren op dubbele pakketten (hetzelfde pakket, verschillende versies), wat in sommige gevallen problemen kan veroorzaken.
* **het gebruik-geval van het Voorbeeld:** De douanedienst die de [ dynamische klassenloader ](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) gebruikt laadt een klasse zonder een versie te specificeren, die door veelvoudige bundels met verschillende versies wordt uitgevoerd, die de implementatie veroorzaken om verschillend te zijn en het gedrag om te veranderen. De ontwikkelaar wil zien welke pakketten zich in de omgeving bevinden zonder het eigenschapmodel te analyseren, zodat ze naar dit pakket zoeken en alle versies zien die worden geëxporteerd. Dit geeft hen de informatie om een betere versiewaaier in te gaan.

### Servlets {#servlets}

![ Servlets lusje in de Dev Console UI ](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Dit verstrekt een onderzoeksherinnering waarop u een weg met selecteurs en een uitbreiding met of GET of POST kunt specificeren. Het verstrekt dan resultaten van servlets in orde van voorkeur die het verzoek in Sling zal behandelen.
* **het gebruiksgeval van het Voorbeeld:** u hebt servlet OSGI die op een verzoek zou moeten worden geactiveerd en iets aan de reactie zou moeten drukken, maar u krijgt in plaats daarvan een lege reactie terug. U moet controleren of een andere servlet voorrang heeft op uw servlet vanwege specifiekere kiezers, `resourceType` , uitbreidingen of rangschikkingen. U zoekt naar het verwachte pad en zoekt of een andere servlet actief is met een hogere rang. Vervolgens bepaalt u of u uw servlet boven in de rij kunt zetten door bijvoorbeeld kiezers toe te voegen.

### Services {#services}

![ het lusje van de Diensten in Dev Console UI ](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Gelijkaardig aan de mening van Componenten OSGI, maar gebaseerd op de diensten. U kunt snel zoeken in welke services bepaalde eigenschappen worden aangeboden.

### OSGi-componenten {#osgi-components}

![ het Lusje van Componenten OSGi in Dev Console UI ](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Dit geeft een overzicht van de OSGI-componenten in het geselecteerde omgevingstype. Hiermee wordt een zoekopdracht in volledige tekst ingeschakeld.
* Je krijgt de live status van OSGI componenten in de omgeving. U kunt zien aan welke services het voldoet, de bundel die het levert en het activeringstype (onmiddellijk of vertraagd).
* **gebruik-geval 1 van het Voorbeeld:** als ontwikkelaar, wilt u verifiëren als een component die met een configuratie wordt geactiveerd actief of niet op een bepaald milieu is, omdat u niet het gedrag krijgt dat u verwacht. U zoekt eenvoudig de component in het onderzoek en controleert om te zien of is de component actief of niet.
* **gebruik-geval 2 van het voorbeeld:** u geinteresseerd bent om te zien welke uit de dooscomponenten op het milieu aanwezig zijn, en welke diensten zij tevredenstellen, om meer over Adobe Experience Manager as a Cloud Service te leren. U kunt ze uitchecken in de lijst met componenten.

### Integrations {#integrations}

![ het lusje van Integraties in de Dev Console UI ](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Biedt beheerders de capaciteit om dienst-geloofsbrieven en ontwikkelaartokens te produceren, anders te noemen en te schrappen.

### Bewaarplaats {#repository}

* Opent [ browser van de Bewaarplaats ](/help/implementing/developing/tools/repository-browser.md).

### Statuspompen/query&#39;s {#status-dumps-queries}

![ de Fouten/het lusje van Vragen van de Status in Dev Console UI ](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Geeft een volledige tekst of JSON-stortplaats van de huidige staat van bundels, pakketten, configuraties, de diensten, componenten, sling banen of eikendefinities.
* Dit is vooral handig als de ontwikkelaar een onverwachte status heeft ontdekt en dit voor andere ontwikkelaars wil communiceren of documenteren. Het downloaden van de stortplaats geeft u een momentopname van de staat voor recentere verwijzing.

### Configuraties {#configurations}

![ het lusje van Configuraties in Dev Console UI ](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Dit geeft u een doorzoekbare lijst van configuraties die op het milieu actief zijn. U kunt zien welke eigenschappen door de configuraties worden verstrekt door de detailspagina uit te checken.
* **het gebruiksgeval van het Voorbeeld:** De ontwikkelaar van A wil ervoor zorgen dat de configuraties die zij hebben gespecificeerd eigenlijk op het milieu aanwezig zijn. Als de configuratie ontbreekt, kunnen zij het eigenschapmodel of de configuratie runmode of omslag controleren.

Voor productieprogramma&#39;s wordt de toegang tot de AEM as a Cloud Service Developer Console gedefinieerd door de &quot;Cloud Manager - Developer Role&quot; in de Adobe Admin Console, terwijl voor sandboxprogramma&#39;s de AEM as a Cloud Service Developer Console beschikbaar is voor gebruikers met een productprofiel dat hen toegang geeft tot AEM as a Cloud Service. Voor alle programma&#39;s is &quot;Cloud Manager - Developer Role&quot; nodig voor statusdumps en moeten de browser van de opslagplaats en gebruikers ook worden gedefinieerd in het productprofiel van AEM gebruikers of AEM beheerders voor zowel auteur- als publicatieservices om gegevens van beide services te bekijken. Voor meer informatie over vestiging gebruikerstoestemmingen, zie [ Documentatie van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).