---
title: Inhoud zoeken en indexeren
description: Inhoud zoeken en indexeren
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 2%

---


# Inhoud zoeken en indexeren {#indexing}

## Changes in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Met AEM als Cloud Service, beweegt Adobe zich van een AEM instantie centric model aan een de dienst gebaseerde mening met n-x AEM Containers, aangedreven door CI/CD pijpleidingen in de Manager van de Wolk. In plaats van het vormen van en het handhaven van Indexen op enige instanties AEM, moet de configuratie van de Index vóór een plaatsing worden gespecificeerd. De veranderingen van de configuratie in productie zijn duidelijk het beleid van CI/CD breken. Hetzelfde geldt voor indexwijzigingen, aangezien dit van invloed kan zijn op de stabiliteit en de prestaties van het systeem als dit niet wordt gespecificeerd en getest en opnieuw geïndexeerd voordat deze in productie worden genomen.

Hieronder volgt een lijst met de belangrijkste wijzigingen ten opzichte van AEM 6.5 en eerdere versies:

1. De gebruikers zullen geen toegang tot de Manager van de Index van één enkele instantie AEM hebben om het indexeren te zuiveren, te vormen of te handhaven. Het wordt alleen gebruikt voor lokale ontwikkeling en on-prem-implementaties.

1. De gebruikers zullen geen indexen op één enkel Instantie veranderen AEM noch zullen zij zich over consistentiecontroles of het opnieuw indexeren moeten meer ongerust maken.

1. Over het algemeen worden indexwijzigingen doorgevoerd voordat naar de productie wordt gegaan om kwaliteitsgateways in de CBI/CD-leidingen van de Cloud Manager niet te omzeilen en geen invloed te hebben op de KPI&#39;s van de Business.

1. Alle verwante metriek met inbegrip van onderzoeksprestaties in productie zal voor klanten bij runtime beschikbaar zijn om de holistische mening over de onderwerpen van Onderzoek en het Indexeren te verstrekken.

1. Klanten kunnen waarschuwingen instellen op basis van hun behoeften.

1. SRE&#39;s bewaken de systeemgezondheid 24/7 en zullen zo nodig en zo vroeg mogelijk actie ondernemen.

1. Indexconfiguratie wordt gewijzigd via implementaties. Wijzigingen in indexdefinities worden net als andere wijzigingen in de inhoud geconfigureerd.

1. Op een hoog niveau voor AEM als Cloud Service, met de introductie van het [blauw-Groene plaatsingsmodel](#index-management-using-blue-green-deployments) zullen twee reeksen indexen bestaan: één set voor de oude versie (blauw) en één set voor de nieuwe versie (groen).

1. Klanten kunnen zien of de indexeertaak is voltooid op de pagina voor het samenstellen van de cloud Manager en ontvangen een melding wanneer de nieuwe versie gereed is voor verkeer.

1. Beperkingen: momenteel wordt indexbeheer op AEM als Cloud Service alleen ondersteund voor indexen van het type lucene.

<!-- ## Sizing Considerations {#sizing-considerations}

AEM as a Cloud Service comes with a default capacity model to provide sufficient performance for average web applications. This "average" measure relates to the repository size and even more relevant to the indexing size. If we have reasons to believe that we need extended capacity for a specific customer project, an evaluation with SREs and Engineering will take place to determine the required capacity settings.

AS NOTE: the above is internal for now.

-->

## Het gebruik {#how-to-use}

De volgende drie gebruiksgevallen kunnen in indexen worden gedefinieerd:

1. Een nieuwe klantindexdefinitie toevoegen
1. Een bestaande indexdefinitie bijwerken. Dit betekent in feite dat een nieuwe versie van een bestaande indexdefinitie moet worden toegevoegd
1. Verwijderen van een bestaande index die overbodig of verouderd is.

Voor zowel de punten 1 als 2 hierboven moet u een nieuwe indexdefinitie maken als onderdeel van uw aangepaste codebasis in het respectievelijke releaseprogramma voor Cloud Manager. Voor meer informatie, zie het [Opstellen aan AEM als documentatie](/help/implementing/deploying/overview.md)van de Cloud Service.

### De nieuwe indexdefinitie voorbereiden {#preparing-the-new-index-definition}

U moet een nieuw indexdefinitiepakket voorbereiden dat de daadwerkelijke indexdefinitie bevat, die dit noemingspatroon volgt:

`<indexName>[-<productVersion>]-custom-<customVersion>`

en dat moet dan nog onderuit `ui.apps/src/main/content/jcr_root`. Subhoofdmappen worden op dit moment niet ondersteund.

<!-- need to review and link info on naming convention from https://wiki.corp.adobe.com/display/WEM/Merging+Customer+and+OOTB+Index+Changes?focusedCommentId=1784917629#comment-1784917629 -->

Het pakket van het bovenstaande voorbeeld is samengesteld als `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`volgt.

### Indexdefinities implementeren {#deploying-index-definitions}

>[!NOTE]
>
>Er is een bekend probleem met Jackrabbit FileVult Maven Package Plugin versie **1.1.0** die u niet toestaat om `oak:index` aan modules van toe te voegen `<packageType>application</packageType>`. Gebruik versie **1.0.4** om dit probleem op te lossen.

Indexdefinities zijn nu gemarkeerd als aangepast en versieingesteld:

* De indexdefinitie zelf (bijvoorbeeld `/oak:index/ntBaseLucene-custom-1`)

Om een index te kunnen implementeren, moet de indexdefinitie (`/oak:index/definitionname``ui.apps` ) daarom via Git en het implementatieproces van Cloud Manager worden geleverd.

Nadat de nieuwe indexdefinitie is toegevoegd, moet de nieuwe toepassing worden geïmplementeerd via Cloud Manager. Na de implementatie worden twee taken gestart, die verantwoordelijk zijn voor het toevoegen (en indien nodig samenvoegen) van de indexdefinities aan respectievelijk MongoDB en Azure Segment Store voor auteur en publicatie. De onderliggende repository&#39;s worden opnieuw gedestilleerd met de nieuwe indexdefinities, voordat de Blauw-Groen omschakeling plaatsvindt.

>[!TIP]
>
>Zie het document [AEM Project Structure voor meer informatie over de vereiste pakketstructuur voor AEM als Cloud Service.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## Indexbeheer met Blauw-groene implementaties {#index-management-using-blue-green-deployments}

### Wat is indexbeheer {#what-is-index-management}

Indexbeheer gaat over het toevoegen, verwijderen en wijzigen van indexen. Het wijzigen van de *definitie* van een index is snel, maar het toepassen van de wijziging (vaak &#39;een index maken&#39; genoemd, of, voor bestaande indexen, &#39;opnieuw indexeren&#39;) kost tijd. Het is niet onmiddellijk: de gegevensopslagruimte moet worden gescand om de gegevens te indexeren.

### Wat is een blauw-groene implementatie {#what-is-blue-green-deployment}

Blauw-groene implementatie kan downtime verminderen. Het staat ook voor nul downtime verbeteringen toe en verstrekt snelle terugdraaiversies. De oude versie van de toepassing (blauw) wordt tegelijk met de nieuwe versie van de toepassing uitgevoerd (groen).

### Alleen-lezen en Gebieden lezen/schrijven {#read-only-and-read-write-areas}

Bepaalde delen van de opslagplaats (alleen-lezen onderdelen van de opslagplaats) kunnen verschillend zijn in de oude (blauwe) en de nieuwe (groene) versie van de toepassing. De gebieden met het kenmerk Alleen-lezen van de gegevensopslagruimte zijn doorgaans &quot;`/app`&quot; en &quot;`/libs`&quot;. In het volgende voorbeeld wordt cursief gebruikt voor het markeren van alleen-lezen gebieden, terwijl vet wordt gebruikt voor lezen-schrijven gebieden.

* **/**
* */apps (alleen-lezen)*
* **/content**
* */libs (alleen-lezen)*
* **/oak:index**
* **/oak:index/acme**
* **/jcr:system**
* **/system**
* **/var**

De lees-schrijf gebieden van de bewaarplaats worden gedeeld tussen alle versies van de toepassing, terwijl voor elke versie van de toepassing, er een specifieke reeks van `/apps` en `/libs`is.

### Indexbeheer zonder blauw-groene implementatie {#index-management-without-blue-green-deployment}

Tijdens de ontwikkeling, of wanneer het gebruiken op gebouwinstallaties, kunnen indexen worden toegevoegd, worden verwijderd, of bij runtime worden veranderd. Indexen worden gebruikt zodra ze beschikbaar zijn. Als een index nog niet in de oude versie van de toepassing moet worden gebruikt, dan wordt de index typisch gebouwd tijdens een geplande onderbreking. Hetzelfde geldt wanneer u een index verwijdert of een bestaande index wijzigt. Wanneer u een index verwijdert, wordt deze niet meer beschikbaar zodra deze wordt verwijderd.

### Indexbeheer met blauw-groene implementatie {#index-management-with-blue-green-deployment}

Met blauwgroene implementaties is er geen downtime. Voor indexbeheer is het echter vereist dat indexen alleen door bepaalde versies van de toepassing worden gebruikt. Als u bijvoorbeeld een index toevoegt in versie 2 van de toepassing, wilt u deze nog niet gebruiken in versie 1 van de toepassing. Het omgekeerde is het geval wanneer een index wordt verwijderd: een in versie 2 verwijderde index is nog steeds nodig in versie 1. Als u een indexdefinitie wijzigt, willen we dat de oude versie van de index alleen wordt gebruikt voor versie 1 en dat de nieuwe versie van de index alleen wordt gebruikt voor versie 2.

In de volgende tabel worden vijf indexdefinities weergegeven: index `cqPageLucene` wordt in beide versies gebruikt, terwijl index alleen in versie 2 `damAssetLucene-custom-1` wordt gebruikt.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` AEM is nodig als Cloud Service om dit te markeren als een vervanging voor een bestaande index.

| Index | Index van out-of-the-box | Gebruiken in versie 1 | Gebruiken in versie 2 |
|---|---|---|---|
| /eak:index/damAssetLucene | Ja | Ja | Nee |
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Nee | Ja |
| /ak:index/acmeProduct-custom-1 | Nee | Ja | Nee |
| /ak:index/acmeProduct-custom-2 | Nee | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Het versienummer wordt telkens verhoogd wanneer de index wordt gewijzigd. Als u wilt voorkomen dat aangepaste indexnamen botsen met indexnamen van het product zelf, moeten aangepaste indexen en wijzigingen in indexen uit het vak eindigen met `-custom-<number>`.

### Wijzigingen in indexen buiten de box {#changes-to-out-of-the-box-indexes}

Zodra Adobe een uit-van-de-doos index zoals &quot;damAssetLucene&quot;of &quot;cqPageLucene&quot;verandert, wordt een nieuwe genoemde index genoemd `damAssetLucene-2` of `cqPageLucene-2` gecreeerd, of, als de index reeds werd aangepast, wordt de aangepaste indexdefinitie samengevoegd met de veranderingen in de uit-van-de-doos index, zoals hieronder getoond. Wijzigingen worden automatisch samengevoegd. Dat betekent dat u niets hoeft te doen als een index buiten de doos verandert. Het is echter mogelijk de index later opnieuw aan te passen.

| Index | Index van out-of-the-box | Gebruiken in versie 2 | Gebruiken in versie 3 |
|---|---|---|---|
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Ja | Nee |
| /eak:index/damAssetLucene-2-custom-1 | Ja (automatisch samengevoegd van damAssetLucene-custom-1 en damAssetLucene-2) | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nee |
| /oak:index/cqPageLucene-2 | Ja | Nee | Ja |

### Beperkingen {#limitations}

Indexbeheer wordt momenteel alleen ondersteund voor indexen van het type `lucene`.

### Een index verwijderen {#removing-an-index}

Als een index in een recentere versie van de toepassing moet worden verwijderd, kunt u een lege index (een index zonder gegevens aan index), met een nieuwe naam bepalen. U kunt deze bijvoorbeeld een naam geven `/oak:index/acmeProduct-custom-3`. Hiermee vervangt u de index `/oak:index/acmeProduct-custom-2`. Nadat de lege index door het systeem `/oak:index/acmeProduct-custom-2` is verwijderd, `/oak:index/acmeProduct-custom-3` kan deze ook worden verwijderd.

### Een index toevoegen {#adding-an-index}

Als u een index met de naam &quot;/oak:index/acmeProduct-custom-1&quot; wilt toevoegen die moet worden gebruikt in een nieuwe versie van de toepassing en hoger, moet de index als volgt worden geconfigureerd:

`*mk.*assetLuceneIndex-1-custom-1`

Dit werkt door een aangepaste id vooraf op de indexnaam in te stellen, gevolgd door een punt (**.**). De id moet tussen 1 en 4 tekens lang zijn.

Zoals hierboven, verzekert dit dat de index slechts door de nieuwe versie van de toepassing wordt gebruikt.

### Index wijzigen {#changing-an-index}

Wanneer een bestaande index wordt gewijzigd, moet een nieuwe index met de gewijzigde indexdefinitie worden toegevoegd. Stel dat de bestaande index &quot;/oak:index/acmeProduct-custom-1&quot; is gewijzigd. De oude index wordt opgeslagen onder `/oak:index/acmeProduct-custom-1`en de nieuwe index wordt opgeslagen onder `/oak:index/acmeProduct-custom-2`.

De oude versie van de toepassing gebruikt de volgende configuratie:

`/oak:index/acmeProduct-custom-1`

De nieuwe versie van de toepassing gebruikt de volgende (veranderde) configuratie:

`/oak:index/acmeProduct-custom-2`