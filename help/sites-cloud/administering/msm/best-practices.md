---
title: Aanbevolen MSM-procedures
description: Leer de beste praktijken die door Adobe engineering en raadplegende teams worden gecompileerd helpen om met de AEM MultiManager van de Plaats aan de slag te gaan.
feature: Multi Site Manager
role: Admin
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 0%

---

# Aanbevolen MSM-procedures {#msm-best-practices}

## Algemeen {#general}

MSM is een configureerbaar framework voor het automatiseren van de implementatie van inhoud. Bij implementaties gaat het vaak om grote delen van een website en meerdere organisaties en geografische gebieden. Daarom wordt u ten zeerste aangeraden MSM-implementaties net zo zorgvuldig te plannen als uw website:

* Zorgvuldig **planstructuur en inhoudsstromen** alvorens implementatie te beginnen.
* **pas zo veel zoals nodig aan, maar zo weinig mogelijk.** Hoewel MSM een hoge mate van aanpassing ondersteunt (bijvoorbeeld rollout-configuraties), is het minimaliseren van aanpassingen doorgaans de beste manier om de prestaties, betrouwbaarheid en upgradebaarheid van uw website te minimaliseren.
* Vestig a **governance** model vroeg, en treed gebruikers dienovereenkomstig, om succes te verzekeren. Een beste praktijk van een governance standpunt moet **minimaliseren het gezag dat de lokale inhoudsproducenten** hebben om inhoud aan andere lokale gebruikers en hun respectieve Levende Kopieën toe te wijzen/te verbinden. Dit komt omdat onbestuurde, geketende overerving de complexiteit van een MSM-structuur aanzienlijk kan verhogen en de prestaties en betrouwbaarheid ervan in gevaar kan brengen.
* Zodra een plan voor uw structuur, inhoudsstromen, automatisering, en bestuur bestaat, **prototype en test grondig uw systeem** alvorens een levende implementatie te beginnen.
* Houd in mening dat **Adobe Consulting en de belangrijke Integrators van het Systeem** diepe ervaring planning en het uitvoeren van inhoudsautomatisering met MSM hebben, zodat kunnen zij u zowel helpen met uw project MSM en door zijn volledige implementatie begonnen worden.

## Live Copy-bronnen en configuraties voor blauwdrukken {#live-copy-sources-and-blueprint-configurations}

Houd in mening dat een Levend Exemplaar kan worden gecreeerd gebruikend of [ regelmatige pagina&#39;s ](creating-live-copies.md#creating-a-live-copy-of-a-page) of a [ blauwdrukconfiguratie ](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Beide zijn geldige gebruiksgevallen.

De extra voordelen van het gebruiken van een blauwdrukconfiguratie zijn dat zij:

* Sta de auteur toe om de **optie van de Uitvoer** op een blauwdruk te gebruiken om wijzigingen aan Levende Exemplaren uitdrukkelijk te duwen die van dit blauwdruk erven.
* Sta de auteur toe om **te gebruiken creeer Plaats** om talen gemakkelijk te selecteren en de structuur van Levend Exemplaar te vormen.
* Definieer een standaardconfiguratie voor rollout voor actieve kopieën die een relatie hebben met de blauwdruk.

Als er niet naar een blauwdrukconfiguratie wordt verwezen, kunnen rollouts alleen worden geïnitieerd vanuit de live kopieën zelf, waarbij inhoud van de bron wordt opgehaald.

Wanneer u een site maakt met Live Copy, is het handig om blauwdrukconfiguraties te maken om ervoor te zorgen dat de volledige MSM-functieset beschikbaar is.

>[!NOTE]
>
>CUG&#39;s op het tabblad Machtigingen kunnen niet worden geïmplementeerd voor actieve kopieën van blauwdrukken. Plan deze regel bij het configureren van Live Copy.

## Componenten en containersynchronisatie {#components-and-container-synchronization}

In het algemeen, is de rollout regel in MSM betreffende de synchronisatie van componenten:

* Componenten worden gesynchroniseerd met alle bronnen in de blauwdruk.
* Containers synchroniseren alleen de huidige bron.

Dit betekent dat componenten als aggregaat worden behandeld, en in een rollout worden de component zelf en al zijn kinderen vervangen met die in de blauwdrukken. Dit betekent dat als een bron lokaal aan een dergelijke component wordt toegevoegd, deze bij rollout verloren gaat aan de inhoud van de blauwdruk.

Om het nesten van componenten te steunen zodat de plaatselijk toegevoegde componenten in een rollout worden gehandhaafd, moet de component als container worden verklaard.

>[!NOTE]
>
>Voeg de eigenschap `cq:isContainer` toe aan de component om deze aan te wijzen als een container.

## Site maken {#create-site}

U ziet dat AEM twee hoofdbenaderingen heeft voor het maken van actieve kopieën:

* Wanneer [ creërend een Levend Exemplaar ](creating-live-copies.md#creating-a-live-copy-of-a-page) - dit kan als generischere benadering worden beschouwd, toestaand u om Levende Kopieën van om het even welke pagina tot stand te brengen. De inhoudsstructuur van een Live Copy komt exact overeen met de bron.

* Wanneer [ creërend een Plaats ](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) - dit is een meer gespecialiseerde benadering, hoofdzakelijk voor het creëren van websites met een meertalige structuur.

Houd rekening met het volgende wanneer u een site maakt:

* Om een plaats tot stand te brengen, hebt u de configuratie van de a [ blauwdruk ](creating-live-copies.md#managing-blueprint-configurations) nodig.
* Als u wilt dat de taalpaden op een nieuwe site kunnen worden geselecteerd, moeten de overeenkomstige taalwortels in de blauwdruk (bron) aanwezig zijn.
* Zodra a [ nieuwe plaats is gecreeerd als Levend Exemplaar ](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (gebruikend **creeer**, dan **Plaats**), zijn de eerste twee niveaus van dit Levende Exemplaar *ondiep*. Onderliggende items van de pagina behoren niet tot de live-relatie, maar de rollout neemt wel af als een live-relatie wordt gevonden die overeenkomt met de trigger.

Het is nuttig om te vermijden:

* Talen handmatig toevoegen in de blauwdruk (onder het eerste niveau).
* Inhoud handmatig direct onder de hoofdmap van de taal toevoegen, omdat dit er niet toe leidt dat deze nieuwe inhoud automatisch bij de rollout naar Live Copy wordt overgebracht.

## MSM- en meertalige websites {#msm-and-multilingual-websites}

MSM kan op twee manieren helpen bij het maken van meertalige websites:

Houd bij het maken van taalstramienen rekening met het volgende:

* Terwijl MSM zelf **geen inhoudsomzetting** verstrekt, kan het met derdevertaalschakelaars worden geïntegreerd die doen. Let op het volgende:
   * Met MSM kunt u overname op pagina- en/of componentniveau annuleren. Zo voorkomt u bij de volgende rollout dat u vertaalde inhoud overschrijft (van een Live Copy met nog niet-vertaalde inhoud van een blauwdruk).
      * Sommige vertalingsconnectors van derden automatiseren dit beheer van MSM-overerving.
      * Vraag uw vertaalservicebureau om meer informatie.
      * Een alternatieve benadering voor het maken en vertalen van taalmeesters is het gebruik van taalkopieën in combinatie met AEM niet-elektronische vertaalintegratiekader.

Voor meer informatie zie [ Vertaal Inhoud voor Meertalige Plaatsen ](/help/sites-cloud/administering/translation/overview.md) en [ de Beste praktijken van de Vertaling ](/help/sites-cloud/administering/translation/best-practices.md).

## Structuurwijzigingen en rollouts {#structure-changes-and-rollouts}

Wijzigingen in de inhoudsstructuur in een blauwdruk-/bronstructuur worden anders weerspiegeld in een actieve kopie. Dit is afhankelijk van het wijzigingstype:

* **Creërend** nieuwe pagina&#39;s in een blauwdruk zullen in overeenkomstige pagina&#39;s resulteren die in Levende Kopieën na rollout met de standaardrollout configuratie worden gecreeerd.
* **het Schrappen van** pagina&#39;s in een blauwdruk zal in overeenkomstige pagina&#39;s resulteren die van Levende Kopieën na rollout met standaard rollout configuratie worden geschrapt.
* **het bewegen** pagina&#39;s in een blauwdruk zal **** niet in overeenkomstige pagina&#39;s resulteren die in Levende Kopieën na rollout met standaard rollout configuratie worden bewogen:
   * De reden voor dit gedrag is dat een paginabeweging impliciet een pagina-verwijdering bevat. Dit kan mogelijk leiden tot onverwacht gedrag bij het publiceren, omdat bij het verwijderen van pagina&#39;s bij de auteur de bijbehorende inhoud bij het publiceren automatisch wordt gedeactiveerd. Dit kan ook een aanvullend effect hebben op verwante items, zoals koppelingen, bladwijzers en andere.
      * Inhoudsovererving op de respectievelijke Live Copy-pagina&#39;s wordt bijgewerkt met de nieuwe locatie van de bronnen in de blauwdruk.
      * Om volledig te realiseren een paginabeweging van een blauwdruk aan Levende Exemplaren, overweeg de [ beste praktijken van de paginageverplaatsing ].(#page-move)

### Aanbevolen werkwijzen voor verplaatsen pagina {#page-move}

Houd rekening met de volgende aanbevolen procedures wanneer u overweegt pagina&#39;s te verplaatsen in een Live kopie.

>[!NOTE]
>
>Het volgende zal slechts met [ werken bij de trekker van de Uitvoer ](live-copy-sync-config.md#rollout-triggers).

1. Maak een aangepaste rollout-configuratie.
   * Deze nieuwe configuratie moet de handeling `PageMoveAction` bevatten.
   * Voeg geen andere acties aan deze configuratie toe.
1. Plaats de nieuwe configuratie.
   * Als u de pagina volledig wilt uitrollen, verplaatst u de pagina terwijl u de desbetreffende pagina&#39;s op hun oude locatie in Live Copy verwijdert:
      * Plaats de gecreeerde configuratie vóór de standaardrollout configuratie. De standaardrollout configuratie zal ervoor zorgen om de pagina&#39;s in hun oude plaatsen te schrappen.
      * Als u de pagina wilt uitrollen, verplaatst u de pagina terwijl de respectievelijke pagina&#39;s op hun oude locatie in Live kopieën blijven staan (de inhoud wordt in feite gedupliceerd):
         * Plaats de gecreeerde configuratie na de standaardrollout configuratie. Zo voorkomt u dat inhoud wordt verwijderd uit Live kopie of gedeactiveerd uit publicatie.

## Rollen aanpassen {#customizing-rollouts}

MSM-rollout-configuraties zijn in hoge mate aanpasbaar. Het automatiseren van rollouts kan verreikende gevolgen hebben. Als beste praktijken, zou u zeer zorgvuldig moeten plannen alvorens aan de volgende activiteiten deel te nemen:

* Het automatiseren rollouts zoals met [ onModify trekkers ](#onmodify)
* Het aanpassen [ knooptypes/eigenschappen ](#node-types-properties)
* Volgende workflows starten
* Inhoud activeren als onderdeel van rollouts

### onModify {#onmodify}

Wanneer het gebruiken van de [ rollout trekker ](live-copy-sync-config.md#rollout-triggers) `onModify` zou u moeten overwegen:

* Het automatiseren van rollouts met `onModify` triggers kan een negatief effect hebben op de ontwerpprestaties, aangezien deze rollouts activeren na elke wijziging van de pagina.
* Het rollout-resultaat kan afwijken van het verwachte resultaat:
   * U kunt de volgorde van de resulterende wijzigingsgebeurtenissen niet opgeven.
   * De op gebeurtenis-gebaseerde architectuur kan niet de opeenvolging van de gebeurtenissen waarborgen die tot de Manager van de Uitvoer worden overgegaan.
* Het gebruiken van zulk een rollout configuratie kon tot conflicten leiden als de gezamenlijke updates van het zelfde middel voorkomen.

Daarom wordt u aangeraden alleen triggers van het type `onModify` te gebruiken als de voordelen van automatische rollout opwegen tegen mogelijke prestatieproblemen.

### Knooppunttypen/eigenschappen {#node-types-properties}

Naast het aanpassen van rollout acties, laat MSM u knoopeigenschappen ook aanpassen die worden opgesteld. De [ configuratie MSM OSGi laat u knooptypes ](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) van het worden gekopieerd uit de bron aan Levend Exemplaar uitsluiten.

## Aanvullende informatie {#further-information}

Raadpleeg de volgende artikelen voor meer informatie over MSM en Live Copy.

* [Actieve kopieën maken en synchroniseren](creating-live-copies.md)
* [Console voor live kopiëren](live-copy-overview.md)
* [Synchronisatie van actieve kopie configureren](live-copy-sync-config.md)
* [Conflicten MSM-rollout](rollout-conflicts.md)
