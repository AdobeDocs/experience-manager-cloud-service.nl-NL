---
title: Cloud Manager en de workflow voor snel maken van sites begrijpen
description: Meer informatie over Cloud Manager en hoe het nieuwe proces voor het maken van de Snelle site samenbrengt.
exl-id: 5d264078-e552-48ca-8d82-294a646e6b1f
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
recommendations: noDisplay, noCatalog
source-git-commit: 8c4b34a77ef85869048fae254728c58cf0d99b66
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 0%

---


# Cloud Manager en de workflow voor snel maken van sites begrijpen {#understand-cloud-manager}

{{traditional-aem}}

Meer informatie over Cloud Manager en hoe het nieuwe proces voor het maken van de Snelle site samenbrengt.

>[!TIP]
>
>Als uw rol exclusief front-end ontwikkeling is, kunt u aan het artikel [ overslaan terugwinnen de toegangsinformatie van de git bewaarplaats ](retrieve-access.md) in deze reis.
>
>Als u een beheerder van AEM, een beheerder van Cloud Manager bent, voor zowel front-end ontwikkeling als beheerderstaken verantwoordelijk, of eenvoudig het proces van begin tot eind in AEM voor front-end ontwikkeling wilt begrijpen, blijven lezend het huidige document en ga op deze reis verder.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe het gereedschap AEM Quick Site Creation werkt en geeft u een overzicht van de end-to-end flow. Na het lezen moet u:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om front-end ontwikkeling te vergemakkelijken
* Ontdek hoe de stap voor aanpassing aan de voorkant volledig losgekoppeld is van AEM en geen AEM-kennis vereist.

Dit document richt zich op het begrijpen van deze fundamentele stukken van de Snelle oplossing van de Plaats alvorens zich aan de volgende stap van de reis te bewegen waar u configuratie begint.

Hoewel het wordt geadviseerd om door deze reis stap voor stap te werk te gaan, als u reeds AEM Sites en Cloud Manager samen begrijpt en direct met configuratie wilt beginnen, kunt u [ aan de volgende stap van de reis ](create-site.md) overslaan.

## Verantwoordelijke rol {#responsible-role}

Dit deel van de reis is zowel op de beheerder van AEM als op de beheerder van Cloud Manager van toepassing.

## Eisen en voorwaarden {#requirements-prerequisites}

U hebt verschillende vereisten nodig voordat u sites gaat maken en aanpassen met het gereedschap Snel site maken.

Omdat deze reis voor zowel front-end ontwikkelaars, beheerders, als combinaties van alle rollen is bestemd, zijn de vereisten voor allebei hier vermeld.

Het is belangrijk te begrijpen dat voor de front-end ontwikkelaar geen toegang of kennis van AEM nodig is.

### Kennis {#knowledge}

| Kennis | Rol |
|---|---|
| Inzicht in de standaardinstrumenten en -processen van front-end ontwikkeling | Front-endontwikkelaar |
| Basiskennis van het maken en beheren van sites in AEM | AEM-beheerder |
| Basiskennis van Cloud Manager | Cloud Manager-beheerder |

Voor de front-end ontwikkelaar is AEM-kennis niet nodig.

### Gereedschappen {#tools}

| Gereedschap | Rol |
|---|---|
| Voorkeursontwikkelomgeving | Front-endontwikkelaar |
| npm | Front-endontwikkelaar |
| webpack | Front-endontwikkelaar |
| Toegang tot Cloud Manager | Cloud Manager-beheerder |
| Ben een lid van **BedrijfsEigenaar** rol in Cloud Manager | Cloud Manager-beheerder |
| Sys Admin in Cloud Manager zijn | Cloud Manager-beheerder |
| Toegang tot Admin Console | Cloud Manager-beheerder |
| Ben een lid van de **rol van de Manager van de Plaatsing** in Cloud Manager | Cloud Manager-beheerder |
| Ben een lid van de **rol van de Manager van de Plaatsing** in Cloud Manager | Front-endontwikkelaar |

Voor de front-end ontwikkelaar is geen gebruik van AEM nodig.

>[!TIP]
>
>Als u niet vertrouwd met de rollen en rolbeheer van Cloud Manager bent, zie het Rol Gebaseerde document van Toestemmingen in de [ Extra sectie van Middelen ](#additional-resources).

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als enig toegangspunt voor het platform.

Om klanten met de montages van de ondernemingsontwikkeling te steunen, integreert AEM as a Cloud Service volledig met Cloud Manager en zijn doel-gebouwde CI/CD pijpleidingen. Met het gereedschap Snel site maken kunt u deze functies uitbreiden voor ondersteuning van speciale front-end ontwikkelingspijplijnen.

Voor deze reis is een volledig begrip van Cloud Manager niet nodig. Op hoog niveau bestaat Cloud Manager uit verschillende structuurniveaus.

![ structuur van Cloud Manager ](assets/cloud-manager-structure.png)

* **TENANT** - elke klant wordt provisioned met een huurder.
* **PROGRAMMA&#39;S** - elke huurder heeft één of meerdere programma&#39;s, die vaak op de gelicentieerde oplossingen van de klant wijzen.
* **OMGEVINGEN** - Elk programma heeft veelvoudige milieu&#39;s zoals productie voor levende inhoud, voor het opvoeren, en voor ontwikkelingsdoeleinden.
* **REPOSITORY** - de milieu&#39;s hebben git bewaarplaatsen waar toepassing en front-end code wordt gehandhaafd.
* **TOOLS &amp; WORKFLOWS** - de Pijpleidingen beheren de plaatsing van code van de bewaarplaatsen aan de milieu&#39;s.

Een voorbeeld is vaak handig bij het contextualiseren van deze hiërarchie.

* De Onderneming van het Reizen van WKND en van het Avontuur zou a **huurder** kunnen zijn die zich op op reis betrekking hebbende media concentreert.
* De huurder van de Onderneming van het WKND Reizen en van het Avontuur zou twee **programma&#39;s** kunnen hebben: één programma van Plaatsen voor het Tijdschrift van WKND en één programma van Assets voor Media WKND.
* De programma&#39;s van het Tijdschrift WKND en van Media WKND zouden zowel dev, stadium, als productie **milieu&#39;s** hebben.

## De snelle ontwikkeling van de Site Creation Front-End-ontwikkelingsstroom {#flow}

De algehele stroom is eenvoudig en intuïtief, zelfs als u nog geen uitgebreide ervaring hebt met Cloud Manager.

1. De AEM-beheerder ondertekent in een AEM-omgeving en maakt een nieuwe site met een sitesjabloon.
1. De beheerder van Cloud Manager leidt tot een front-end pijpleiding in Cloud Manager. De pijpleiding organiseert de plaatsing van code van een git bewaarplaats aan een milieu van AEM.
1. De AEM-beheerder exporteert het sitethema uit het AEM-exemplaar van het programma en levert het aan de front-end ontwikkelaar.
1. De Cloud Manager-beheerder verleent de front-end ontwikkelaar toegang tot de AEM git-opslagplaats waar aanpassingen kunnen worden doorgevoerd.
1. De voorste eindontwikkelaar wint toegangsgeloofsbrieven aan toegangskit en de pijpleiding terug.
1. De front-end ontwikkelaar past het thema aan, test het het gebruikend daadwerkelijke inhoud van de plaats gebruikend een volmacht en begaat dan de veranderingen in de git bewaarplaats.
1. De front-end ontwikkelaar voert de pijpleiding uit om de themaaanpassingen aan het productiemilieu van het programma op te stellen.

![ Snelle stroom van de Verwezenlijking van de Plaats ](assets/qsc-flow.png)

Het belangrijkste voordeel van het gebruik van het gereedschap Snel maken is dat de zuivere front-end ontwikkelaar alleen verantwoordelijk is voor de werkelijke aanpassing. De front-end ontwikkelaar heeft geen interactie met AEM of heeft enige kennis van AEM nodig.

{{add-cm-allowlist-frontend-pipeline}}

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Quick Site Creation-reis hebt voltooid, kunt u het volgende doen:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om front-end ontwikkeling te vergemakkelijken
* Ontdek hoe de stap voor aanpassing aan de voorkant volledig losgekoppeld is van AEM en geen AEM-kennis vereist.

Bouw op deze kennis voort en ga uw reis van de Gemaakt van de Plaats van AEM Snelle door het document te herzien [ creeer Plaats van Malplaatje ](create-site.md), waar u leert hoe te om snel een nieuwe plaats van AEM tot stand te brengen gebruikend een malplaatje.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de Snelle reis van de Verwezenlijking van de Plaats door het document te herzien [ creeert Plaats van Malplaatje ](create-site.md) beweegt, zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de reis verder te gaan.

* [ documentatie van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - als u meer details over de eigenschappen van Cloud Manager zou willen, kunt u de diepgaande technische documenten direct willen raadplegen.
* [ Rol Gebaseerde Toestemmingen ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager heeft pre-gevormde rollen met aangewezen toestemmingen. Zie dit document voor details over deze rollen en hoe te om hen te beheren.
* [ npm ](https://www.npmjs.com) - de thema&#39;s van AEM die worden gebruikt om plaatsen snel te bouwen zijn gebaseerd op npm.
* [ webpack ](https://webpack.js.org) - de thema&#39;s van AEM die worden gebruikt om sites snel te bouwen baseren zich op webpack.
