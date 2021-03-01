---
title: Problemen met MSM en veelgestelde vragen oplossen
description: Kom te weten hoe te om de gemeenschappelijkste MSM-verwante kwesties problemen op te lossen en antwoorden te krijgen de gemeenschappelijkste MSM-verwante vragen.
translation-type: tm+mt
source-git-commit: b33e13814403af1383b46b1f34737e8aa75d8213
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---


# Problemen met MSM oplossen en veelgestelde vragen {#troubleshooting-msm}

## Problemen in eerste stappen oplossen {#first-steps}

Als u ervaart wat u denkt is onjuist gedrag of een fout in MSM, alvorens en het gedetailleerde oplossen van problemen zeker te zijn:

* Controleer [Veelgestelde vragen MSM](#faq) aangezien uw problemen of vragen daar reeds kunnen worden opgelost.
* Controleer [MSM best practices article](best-practices.md) aangezien een aantal tips daar wordt aangeboden samen met verduidelijkingen van een aantal misconcepties.

## Geavanceerde informatie over uw blauwdruk en status van Live kopie {#advanced-info} zoeken

MSM registreert verscheidene servers die met selecteurs op middel URLs kunnen worden gevraagd. Deze worden gebruikt door UI maar kunnen ook direct worden gevraagd om direct extra gecomputeriseerde MSM statussen voor uw pagina&#39;s te zien:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Gebruik deze optie op een blauwdrukpagina om de lijst op te halen met alle Live-kopieën die eraan zijn gekoppeld, met extra statusinformatie voor Live Copy.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Gebruik deze optie op Live Copy-pagina&#39;s om geavanceerde informatie op te halen over de verbinding met de bijbehorende pagina&#39;s. Als de pagina geen live kopie is, wordt er niets geretourneerd.

Die servlets produceren de berichten van het Logboek van de FOUTOPSPORING door het `com.day.cq.wcm.msm` registreerapparaat dat ook nuttig kan zijn.

## MSM-specifieke informatie controleren in de dataopslag {#checking-repo}

De vroegere servlets teruggekeerde gegevens verwerkte die informatie op de MSM-specifieke knopen en de mixins wordt gebaseerd. De informatie wordt op de volgende manier in de opslagplaats opgeslagen.

* `cq:LiveSync` mixintype
   * Deze wordt ingesteld op `jcr:content`-knooppunten en definieert Live Copy-basispagina&#39;s.
   * Deze pagina&#39;s hebben een `cq:LiveSyncConfig` onderliggende node van het type `cq:LiveCopy` die standaard en verplichte informatie over Live Copy zal bevatten via de volgende eigenschappen:
      * `cq:master` verwijst naar de pagina met de blauwdruk van de Live kopie.
      * `cq:rolloutConfigs` Hiermee worden actieve rollout-configuraties aangegeven die zijn toegepast op Live Copy.
      * `cq:isDeep` is true als de onderliggende pagina&#39;s van deze hoofdpagina van Live Copy zijn opgenomen in de Live Copy.
* `cq:LiveRelationship` mixintype
   * Elke Live Copy-pagina heeft een dergelijk mixintype op het `jcr:content`-knooppunt.
   * Als dit niet het geval is, is de pagina op een bepaald punt losgekoppeld of handmatig gemaakt via de ontwerpinterface buiten een actie Live Copy (maken of rollout).
* `cq:LiveSyncCancelled` mixintype
   * Toegevoegd aan `jcr:content` knooppunten van Live Copy-pagina&#39;s die zijn opgeschort.
   * Als de opschorting ook van toepassing is op onderliggende pagina&#39;s, wordt een eigenschap `cq:isCancelledForChildren` ingesteld op true op hetzelfde knooppunt.

De informatie aanwezig in deze eigenschappen zou in UI moeten worden weerspiegeld, nochtans wanneer het oplossen van problemen het kan nuttig zijn om gedrag MSM direct in de bewaarplaats waar te nemen aangezien de acties MSM voorkomen.

Kennis van die eigenschappen kan ook nuttig zijn om een query uit te voeren op uw opslagplaats en om te kijken welke paginasets zich in bepaalde staten bevinden. Bijvoorbeeld:

* `select * from cq:LiveSync` Hiermee worden alle hoofdpagina&#39;s van Live Copy geretourneerd.

## Veelgestelde vragen {#faq}

Hier volgen enkele veelgestelde vragen over MSM en Live Copy.

### Waarom worden sommige eigenschappen (bijvoorbeeld titel, annotaties) niet bijgewerkt tijdens een MSM-rollout? {#missing-properties}

De acties van de synchronisatie MSM zijn hoogst configureerbaar. Welke eigenschappen of componenten tijdens rollouts worden gewijzigd hangt direct van eigenschappen van die configuraties af.

Zie [dit artikel](best-practices.md) voor meer informatie over dit onderwerp.

### Hoe kan ik rollout toestemmingen voor een groep auteurs verwijderen? {#remove-rollout-permissions}

Er is geen **rollout** voorrecht dat voor AEM hoofden (gebruikers of groepen) kan worden geplaatst of worden verwijderd.

Als alternatief kunt u:

* Pas het product UI aan om de acties van de Output voor een bepaalde principal te verbergen.
* Verwijder schrijfrechten uit de Live Copy-structuur voor auteurs die niet mogen uitrollen.

### Waarom zie ik Live Copy-pagina&#39;s met het achtervoegsel &quot;_msm_moving&quot;? {#moved-pages}

Als een blauwdrukpagina wordt uitgevouwen, wordt de pagina Live kopie bijgewerkt of wordt er een nieuwe pagina Live kopie gemaakt als deze nog niet bestond (bijvoorbeeld wanneer de pagina voor de eerste keer wordt uitgevouwen of wanneer de pagina Live kopie handmatig is verwijderd).

In dit laatste geval echter, als een pagina zonder een `cq:LiveRelationship` bezit met de zelfde naam bestaat, zal deze pagina dienovereenkomstig worden anders genoemd, alvorens de Levende pagina van het Exemplaar wordt gecreeerd.

Standaard wordt bij de rollout een gekoppelde Live Copy-pagina verwacht, waarop de updates van de blauwdrukken worden uitgevoerd, of geen pagina bij, wanneer een Live Copy-pagina wordt gemaakt.

Als er een &quot;zelfstandige&quot; pagina wordt gevonden, kiest MSM ervoor de naam van deze pagina te wijzigen en een aparte, gekoppelde Live Copy-pagina te maken.

Een dergelijke zelfstandige pagina in een substructuur van Live Copy is doorgaans het resultaat van een bewerking **Detach**, of de vorige pagina Live Copy is handmatig verwijderd door een auteur en vervolgens opnieuw gemaakt met dezelfde naam.

Om dit te vermijden gebruikt u de functie Live kopie **Suspend** in plaats van **Detach**. Meer informatie over de **actie** in [dit artikel.](creating-live-copies.md)
