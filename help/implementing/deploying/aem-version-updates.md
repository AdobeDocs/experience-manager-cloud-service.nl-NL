---
title: Updates van AEM-versie
description: Leer hoe Adobe Experience Manager (AEM) as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
role: Admin
source-git-commit: 01de7b0c4e0408a3bbc5322e37db5075d43c4c5f
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---


# Updates van AEM-versie {#aem-version-updates}

Leer hoe Adobe Experience Manager (AEM) as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.

## CI/CD {#ci-cd}

AEM as a Cloud Service maakt gebruik van continue integratie en doorlopende levering (CI/CD) om ervoor te zorgen dat uw projecten de meest actuele AEM-versie hebben. Met dit proces worden uw productie-, staging- en ontwikkelingsinstanties naadloos bijgewerkt, zonder dat dit uw gebruikers verstoort.

>[!NOTE]
> Aangezien de ontwikkelingsinstanties reeds automatisch worden bijgewerkt, zouden de handupdates voor ontwikkelingsinstanties niet aan _kunnen beschikbaar zijn wat_ van uw programma&#39;s. Deze functie wordt overgebracht naar automatische updates.

Voordat uw exemplaren automatisch worden bijgewerkt, wordt 3-5 dagen van tevoren een nieuwe AEM Maintenance-release gepubliceerd. Tijdens deze periode, zou uw ontwikkelingsinstantie automatisch kunnen worden bijgewerkt of in het geval dat het beschikbaar is kunt u naar keuze [ de update voor uw ontwikkelingsinstanties ](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) teweegbrengen. De updates van de versie worden automatisch toegepast op uw ontwikkelomgevingen eerst. Als de update succesvol is, gaat het updateproces naar uw werkgebied en productieinstanties. De ontwikkelings- en staging-instanties fungeren als een geautomatiseerde kwaliteitspoort, waar uw op maat geschreven tests worden uitgevoerd voordat de update wordt toegepast op uw productieomgeving.

### NIMU (Non-Intrusive Maintenance Updates) {#nimu}

Niet-opdringerige onderhoudsupdates zijn automatische updates die worden toegepast zonder de klantenpijpleidingen erbij te betrekken.
Via NIMU kan de klant de pijplijn op elk moment gebruiken, zelfs als een AEM-versie-update gepland is of in uitvoering is en onderhoudsupdates niet meer worden weergegeven in de implementatiegeschiedenis van de Klantpijpleiding, waardoor het eenvoudiger wordt om de geschiedenis van code-implementaties te volgen.

#### Activiteiten bijwerken

De huidige AEM-versie kan nog steeds voor elke omgeving worden gecontroleerd, zoals voorheen, via het deelvenster Cloud Manager UI-omgevingen. De zelfde kwaliteitsspoorten die in de pijpleiding worden gebruikt worden door de Updates van het Onderhoud van het Non-Intrusive, met inbegrip van de klant geschreven tests.
A [ het bericht van Cloud Manager UI ](/help/implementing/cloud-manager/notifications.md) zal worden verzonden wanneer een Niet-Intrusieve Update van het Onderhoud wordt toegepast op de milieu&#39;s van uw programma. U kunt instellen dat deze ook naar uw e-mail wordt verzonden.

>[!NOTE]
>
> Opmerking: in 2024 zullen de updates voor niet-indringend onderhoud geleidelijk aan voor alle klanten worden ingeschakeld.

## Type updates {#update-types}

Er zijn twee typen updates voor AEM-versies:

* [**AEM-onderhoudsupdates**](/help/release-notes/maintenance/latest.md)

   * Ze zijn vooral bedoeld voor onderhoudsdoeleinden, inclusief de nieuwste oplossingen voor problemen en beveiligingsupdates.
   * Het heeft minimale gevolgen, omdat de wijzigingen regelmatig worden toegepast.

* [**AEM-functie activeren**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * Ze worden op een voorspelbaar maandelijks schema vrijgegeven.

>[!NOTE]
>
> De zeer belangrijke data van de controle voor maandelijkse versies op [ Experience Manager geeft roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL#aem-as-cloud-service) vrij en merken uw kalenders om zich voor te bereiden op de belangrijkste activiteiten om voor de versie klaar te worden.

## Update mislukt {#update-failure}

De updates van AEM gaan door een intensieve en volledig geautomatiseerde productbevestigingspijplijn die veelvoudige stappen omvat, die geen verstoring van de dienst voor om het even welke systemen in productie verzekeren. Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles tijdens een update van AEM as a Cloud Service mislukken, gaat de versie niet verder en Adobe onderzoekt waarom de update dit onverwachte gedrag veroorzaakte.

Wanneer u een nieuwe versie van douanecode op uw milieu opstelt, [ product en de functionele tests van de Douane ](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) spelen een cruciale rol. Zij zorgen ervoor dat de productiesystemen stabiel en functioneel blijven, zelfs nadat een wijziging is aangebracht. Deze tests worden ook toegepast in het updateproces van de Versie van AEM.

Als de update naar de productieomgeving mislukt, draait Cloud Manager automatisch de testomgeving terug. Dit wordt automatisch gedaan om ervoor te zorgen dat zowel de het opvoeren als productiemilieu&#39;s na een update voltooit op de zelfde versie van AEM zijn.
En als een geautomatiseerde update van een ontwikkelomgeving mislukt, worden de faserings- en productieomgevingen niet bijgewerkt.

>[!NOTE]
>
>Als de aangepaste code naar de testfase is geduwd en niet naar de productie, verwijdert de volgende AEM-update deze wijzigingen om de tag it van de laatste geslaagde release van de klant naar de productie te weerspiegelen. Daarom moet de douanecode die slechts op het opvoeren beschikbaar was opnieuw worden opgesteld.

## Aanbevolen procedures {#best-practices}

* **Gebruik van het Milieu van het Stadium**
   * Gebruik een andere omgeving (geen werkgebied) voor lange QA/UAT-cycli.
   * Nadat het testen van de hygiëne in het werkgebied is voltooid, gaat u naar Verifiëren bij Productie.

* **de Pijpleiding van de Productie**
   * Pauze voordat u gaat implementeren naar productie.
   * Het annuleren van de pijpleiding na een Stadium stelt erop dat de code &quot;een wegbaan&quot;en geen geldige kandidaat voor Productie is, verwijs [ het Vormen van een Pijpleiding van de Productie ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **niet-Productie Pijpleiding**
   * Vorm a [ niet-Productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Versnelt leversnelheid/frequentie voor mislukte productiepijplijnen. Identificeer kwesties in niet-prod pijpleidingen door het Functionele Testen van het Product, het Aangepast Functioneren Testen, en het Testen van de UI van de Douane toe te laten.

* **Exemplaar van de Inhoud**
   * Het Exemplaar van de Inhoud van het gebruik [ om gelijkaardige inhoudssets aan een niet-prod milieu te bewegen.](/help/implementing/developing/tools/content-copy.md)

* **Geautomatiseerd Functioneel het Testen**
   * Neem de automatische test op in de pijplijn, zodat u kritieke functionaliteit kunt testen.
   * [ Functionele Testen van de Klant ](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) en [ het Testen van UI van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) blokkeren, als zij de versie van AEM ontbreken wordt niet opgesteld.

## Regressie {#regression}

Als u een probleem tegenkomt dat te maken heeft met regressie, kunt u een ondersteuningszaak indienen via de Admin Console. Als de kwestie een blokker is en de invloed ervan op de productie, moet een P1 worden opgeworpen. Geef alle gegevens op die nodig zijn om het regressieprobleem te reproduceren.

## Composite Node Store {#composite-node-store}

Meestal worden updates zonder downtime uitgevoerd, inclusief voor de ontwerpinstantie, die een cluster met knooppunten is. Het rollen updates zijn mogelijk toe te schrijven aan [ de samengestelde eigenschap van de knoopopslag in Oak ](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html).

Met deze functie kan AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In a [ het rollen plaatsing ](/help/implementing/deploying/overview.md#how-rolling-deployments-work), bevat de nieuwe versie van AEM zijn eigen `/libs` (de op TarMK gebaseerde onveranderlijke bewaarplaats). Deze gegevensopslagruimte verschilt van de oudere AEM-versie, hoewel beide verwijzen naar een gezamenlijke, op DocumentMK gebaseerde variabele gegevensopslagruimte die gebieden als `/content` , `/conf` , `/etc` en andere bevat.

Omdat zowel de oude als de nieuwe versie een eigen versie van `/libs` hebben, kunnen beide actief zijn tijdens de actieve update. En, kunnen beide verkeer nemen tot de oude volledig door nieuwe wordt vervangen.

## Aanvullende informatie {#further-information}

Voor meer informatie over verwante thema&#39;s:

* [Cloud Manager CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)
* [Cloud Manager UI-melding](/help/implementing/cloud-manager/notifications.md)
* [de Architectuur van Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md)
