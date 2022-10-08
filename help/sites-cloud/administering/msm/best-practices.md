---
title: Aanbevolen MSM-procedures
description: Leer de beste praktijken die door Adobe engineering en raadplegende teams worden samengesteld helpen om met de AEM MultiManager van de Plaats in gebruik te worden.
feature: Multi Site Manager
role: Admin
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '1434'
ht-degree: 0%

---

# Aanbevolen MSM-procedures {#msm-best-practices}

## Algemeen {#general}

MSM is een configureerbaar framework voor het automatiseren van de implementatie van inhoud. Bij implementaties gaat het vaak om grote delen van een website en meerdere organisaties en geografische gebieden. Daarom wordt u ten zeerste aangeraden MSM-implementaties net zo zorgvuldig te plannen als uw website:

* zorgvuldig **planstructuur en inhoudsstromen** voordat de implementatie wordt gestart.
* **Pas de aanpassingen zoveel als nodig is, maar zo weinig mogelijk.** Hoewel MSM een hoge mate van aanpassing (bijvoorbeeld, rollout configuraties) steunt, typisch is de beste praktijken voor de prestaties, de betrouwbaarheid en de upgradeability van uw website aanpassing minimaliseren.
* Een **bestuur** model in een vroeg stadium, en de gebruikers dienovereenkomstig trainen, om succes te verzekeren. Een goede praktijk vanuit bestuurlijk oogpunt is: **de autoriteit die producenten van lokale inhoud hebben** om inhoud toe te wijzen/te verbinden aan andere lokale gebruikers en hun respectieve Levende Exemplaren. Dit komt omdat onbestuurde, geketende overerving de complexiteit van een MSM-structuur aanzienlijk kan verhogen en de prestaties en betrouwbaarheid ervan in gevaar kan brengen.
* Zodra er een plan voor uw structuur, inhoudsstromen, automatisering, en bestuur bestaat, **prototype maken en uw systeem grondig testen** voordat een live implementatie wordt gestart.
* Houd er rekening mee dat **Adobe Consulting en toonaangevende systeemintegrators** hebben diepe ervaring planning en het uitvoeren van inhoudautomatisering met MSM, zodat kunnen zij u zowel beginnen met uw project MSM als door zijn volledige implementatie helpen.

## Live Copy-bronnen en configuraties voor blauwdrukken {#live-copy-sources-and-blueprint-configurations}

Houd er rekening mee dat een Live kopie kan worden gemaakt met [gewone pagina&#39;s](creating-live-copies.md#creating-a-live-copy-of-a-page) of [blauwdrukconfiguratie](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Beide zijn geldige gebruiksgevallen.

De extra voordelen van het gebruiken van een blauwdrukconfiguratie zijn dat zij:

* Laat de auteur het **Uitrol** op een blauwdruk om expliciet wijzigingen door te voeren in Actieve kopieën die van deze blauwdruk overerven.
* Laat de auteur gebruiken **Site maken** om eenvoudig talen te selecteren en de structuur van de Live Copy te configureren.
* Definieer een standaardconfiguratie voor rollout voor actieve kopieën die een relatie hebben met de blauwdruk.

Als er niet naar een blauwdrukconfiguratie wordt verwezen, kunnen rollouts alleen worden geïnitieerd vanuit de live kopieën zelf, waarbij inhoud van de bron wordt opgehaald.

Wanneer u een nieuwe site maakt met Live Copy, is het handig om blauwdrukconfiguraties te maken om ervoor te zorgen dat de volledige MSM-functieset beschikbaar is.

>[!NOTE]
>
> CUG&#39;s op het tabblad Machtigingen kunnen niet worden geïmplementeerd voor actieve kopieën van blauwdrukken. Plan dit probleem bij het configureren van Live Copy.

## Componenten en containersynchronisatie {#components-and-container-synchronization}

In het algemeen, is de rollout regel in MSM betreffende de synchronisatie van componenten:

* Componenten worden gesynchroniseerd met alle bronnen in de blauwdruk.
* Containers synchroniseren alleen de huidige bron.

Dit betekent dat componenten als aggregaat worden behandeld, en in een rollout worden de component zelf en al zijn kinderen vervangen met die in de blauwdrukken. Dit betekent dat als een bron lokaal aan een dergelijke component wordt toegevoegd, deze bij rollout verloren gaat aan de inhoud van de blauwdruk.

Om het nesten van componenten te steunen zodat de plaatselijk toegevoegde componenten in een rollout worden gehandhaafd, moet de component als container worden verklaard.

>[!NOTE]
>
>De eigenschap toevoegen `cq:isContainer` aan de component om het als container aan te wijzen.

## Site maken {#create-site}

U ziet dat AEM twee hoofdbenaderingen heeft voor het maken van actieve kopieën:

* Wanneer [een actieve kopie maken](creating-live-copies.md#creating-a-live-copy-of-a-page) - Dit kan worden beschouwd als de meer algemene aanpak, zodat u Live-kopieën kunt maken van elke pagina. De inhoudsstructuur van een Live Copy komt exact overeen met de bron.

* Wanneer [een site maken](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) - Dit is een meer gespecialiseerde aanpak, vooral voor het maken van websites met een meertalige structuur.

Houd rekening met het volgende wanneer u een site maakt:

* Als u een nieuwe site wilt maken, hebt u een [blauwdrukconfiguratie](creating-live-copies.md#managing-blueprint-configurations).
* Als u wilt dat de taalpaden op een nieuwe site kunnen worden geselecteerd, moeten de overeenkomstige taalwortels in de blauwdruk (bron) aanwezig zijn.
* Eenmaal [nieuwe site is gemaakt als een live kopie](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (gebruiken **Maken** vervolgens **Site**), zijn de eerste twee niveaus van deze Live Copy *ondiep*. Onderliggende items van de pagina behoren niet tot de live-relatie, maar de rollout neemt wel af als een live-relatie wordt gevonden die overeenkomt met de trigger.

Het is nuttig om te vermijden:

* Talen handmatig toevoegen in de blauwdruk (onder het eerste niveau).
* Inhoud handmatig direct onder de hoofdmap van de taal toevoegen, omdat dit er niet toe leidt dat deze nieuwe inhoud automatisch bij de rollout naar Live Copy wordt overgebracht.

## MSM- en meertalige websites {#msm-and-multilingual-websites}

MSM kan op twee manieren helpen bij het maken van meertalige websites:

Houd bij het maken van taalstramienen rekening met het volgende:

* Terwijl MSM zelf **biedt geen vertaling van inhoud**, kan het met derde vertaalschakelaars worden geïntegreerd die doen. Houd er rekening mee dat:
   * Met MSM kunt u overerving op pagina- en/of componentniveau annuleren. Zo voorkomt u bij de volgende rollout dat u vertaalde inhoud overschrijft (van een Live Copy met nog niet-vertaalde inhoud van een blauwdruk).
      * Sommige vertalingsconnectors van derden automatiseren dit beheer van MSM-overerving.
      * Neem contact op met uw vertaalserviceprovider voor meer informatie.
      * Een alternatieve benadering voor het maken en vertalen van taalmeesters is het gebruik van taalkopieën in combinatie met AEM kader voor vertaalintegratie buiten de doos.

Zie voor meer informatie [Inhoud vertalen voor meertalige sites](/help/sites-cloud/administering/translation/overview.md) en de [Aanbevolen procedures voor vertaling.](/help/sites-cloud/administering/translation/best-practices.md)

## Structuurwijzigingen en rollouts {#structure-changes-and-rollouts}

Wijzigingen in de inhoudsstructuur in een blauwdruk-/bronstructuur worden anders weerspiegeld in een actieve kopie. Dit is afhankelijk van het wijzigingstype:

* **Maken** Als u nieuwe pagina&#39;s in een blauwdruk maakt, worden de bijbehorende pagina&#39;s na de uitrol met de standaardconfiguratie voor uitrollout gemaakt in Live kopieën.
* **Verwijderen** De pagina&#39;s in een blauwdruk zullen ertoe leiden dat de overeenkomstige pagina&#39;s van Levende Exemplaren na rollout met de standaardrollout configuratie worden geschrapt.
* **Verplaatsen** pagina&#39;s in een blauwdruk **niet** resulterend in het verplaatsen van de overeenkomstige pagina&#39;s in Actieve Exemplaren na rollout met standaard rollout configuratie:
   * De reden voor dit gedrag is dat een paginabeweging impliciet een pagina-verwijdering bevat. Dit kan mogelijk leiden tot onverwacht gedrag bij het publiceren, omdat bij het verwijderen van pagina&#39;s bij de auteur de bijbehorende inhoud bij het publiceren automatisch wordt gedeactiveerd. Dit kan ook een aanvullend effect hebben op verwante items, zoals koppelingen, bladwijzers en andere.
      * Inhoudsovererving op de respectievelijke Live Copy-pagina&#39;s wordt bijgewerkt met de nieuwe locatie van de bronnen in de blauwdruk.
      * Als u volledig wilt weten dat een pagina van een blauwdruk naar Actieve kopieën wordt verplaatst, moet u rekening houden met de [beste werkwijzen verplaatsen.](#page-move)

### Aanbevolen werkwijzen voor verplaatsen pagina {#page-move}

Houd rekening met de volgende aanbevolen procedures wanneer u overweegt pagina&#39;s te verplaatsen in een Live kopie.

>[!NOTE]
>
>Het volgende werkt alleen met de [Bij rollout-trigger](live-copy-sync-config.md#rollout-triggers).

1. Maak een aangepaste rollout-configuratie.
   * Deze nieuwe configuratie moet de handeling bevatten `PageMoveAction`.
   * Voeg geen andere acties aan deze configuratie toe.
1. Plaats de nieuwe configuratie.
   * Als u de pagina volledig wilt uitrollen, verplaatst u de pagina terwijl u de desbetreffende pagina&#39;s op hun oude locatie in Live Copy verwijdert:
      * Plaats de nieuw gecreëerde configuratie vóór de standaardrollout configuratie. De standaardrollout configuratie zal ervoor zorgen om de pagina&#39;s in hun oude plaatsen te schrappen.
      * Als u de pagina wilt uitrollen, verplaatst u de pagina terwijl de respectievelijke pagina&#39;s op hun oude locatie in Live kopieën blijven staan (de inhoud wordt in feite gedupliceerd):
         * Plaats de nieuw gecreëerde configuratie na de standaardrollout configuratie. Zo voorkomt u dat inhoud wordt verwijderd uit Live kopie of gedeactiveerd uit publicatie.

## Rollen aanpassen {#customizing-rollouts}

MSM-rollout-configuraties zijn in hoge mate aanpasbaar. Het automatiseren van rollouts kan verstrekkende gevolgen hebben. Als beste praktijken, zou u zeer zorgvuldig moeten plannen alvorens aan de volgende activiteiten deel te nemen:

* Rolouts automatiseren, zoals met [onModify-triggers](#onmodify)
* Aanpassen [knooppunttypen/eigenschappen](#node-types-properties)
* Volgende workflows starten
* Inhoud activeren als onderdeel van rollouts

### onModify {#onmodify}

Wanneer u de [rollout trigger](live-copy-sync-config.md#rollout-triggers) `onModify` u dient in overweging te nemen dat :

* Rolouts automatiseren met `onModify` triggers kunnen een negatief effect hebben op de ontwerpprestaties omdat ze rollouts activeren na elke wijziging van de pagina.
* Het rollout-resultaat kan afwijken van het verwachte resultaat:
   * U kunt de volgorde van de resulterende wijzigingsgebeurtenissen niet opgeven.
   * De op gebeurtenis-gebaseerde architectuur kan niet de opeenvolging van de gebeurtenissen waarborgen die tot de Manager van de Uitvoer worden overgegaan.
* Het gebruiken van zulk een rollout configuratie kon tot conflicten leiden als de gezamenlijke updates van het zelfde middel voorkomen.

Daarom wordt aangeraden dat u alleen `onModify` veroorzaakt als de voordelen van automatische rollout initialisering om het even welke potentiële prestatieskwesties opwegen.

### Knooppunttypen/eigenschappen {#node-types-properties}

Naast het aanpassen van rollout acties, staat MSM u ook toe om knoopeigenschappen aan te passen die worden uitgerold. De [MSM OSGi configuratie staat u toe om knooptypes uit te sluiten](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) van de bron naar de Live kopie worden gekopieerd.

## Aanvullende informatie {#further-information}

Raadpleeg de volgende artikelen voor meer informatie over MSM en Live Copy.

* [Actieve kopieën maken en synchroniseren](creating-live-copies.md)
* [Console voor live kopiëren](live-copy-overview.md)
* [Synchronisatie van actieve kopie configureren](live-copy-sync-config.md)
* [Conflicten MSM-rollout](rollout-conflicts.md)
