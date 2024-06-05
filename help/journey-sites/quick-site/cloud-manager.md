---
title: Inzicht krijgen in Cloud Manager en de workflow voor snel maken van sites
description: Leer meer over Cloud Manager en hoe dit het nieuwe proces voor het maken van de Snelle site samenbrengt.
exl-id: 5d264078-e552-48ca-8d82-294a646e6b1f
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 0%

---

# Inzicht krijgen in Cloud Manager en de workflow voor snel maken van sites {#understand-cloud-manager}

Leer meer over Cloud Manager en hoe dit het nieuwe proces voor het maken van de Snelle site samenbrengt.

>[!TIP]
>
>Als uw rol exclusief front-end ontwikkeling is, kunt u aan het artikel overslaan [Toegangsgegevens van de opslagplaats ophalen](retrieve-access.md) tijdens deze reis.
>
>Als u een AEM beheerder bent, is een beheerder van de Manager van de Wolk, verantwoordelijk voor zowel front-end ontwikkeling als beheerderstaken, of eenvoudig het proces van begin tot eind in AEM voor front-end ontwikkeling wilt begrijpen, blijven lezend het huidige document en ga op deze reis verder.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe het AEM Snelle hulpmiddel van de Plaats werkt en geeft u een overzicht van de stroom van begin tot eind. Na het lezen moet u:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om de ontwikkeling op de voorgrond te vergemakkelijken
* Ontdek hoe de stap voor aanpassing volledig losgekoppeld is van AEM en geen AEM kennis vereist.

Dit document richt zich op het begrijpen van deze fundamentele stukken van de Snelle oplossing van de Plaats alvorens zich aan de volgende stap van de reis te bewegen waar u configuratie begint.

Hoewel het aangeraden is stap voor stap door te gaan met deze reis, kunt u als u al begrijpt dat AEM Sites en Cloud Manager samenwerken en rechtstreeks met de configuratie willen beginnen [Ga verder met de volgende stap van de reis.](create-site.md)

## Verantwoordelijke rol {#responsible-role}

Dit gedeelte van de reis is van toepassing op zowel de beheerder van de AEM als de beheerder van de Manager van de Wolk.

## Eisen en voorwaarden {#requirements-prerequisites}

U hebt verschillende vereisten nodig voordat u sites gaat maken en aanpassen met het gereedschap Snel site maken.

Omdat deze reis voor zowel front-end ontwikkelaars, beheerders, als combinaties van alle rollen is bestemd, zijn de vereisten voor allebei hier vermeld.

Het is belangrijk te begrijpen dat voor de front-end ontwikkelaar geen AEM toegang of kennis noodzakelijk is.

### Kennis {#knowledge}

| Kennis | Rol |
|---|---|
| Inzicht in de standaardinstrumenten en -processen van front-end ontwikkeling | Front-endontwikkelaar |
| Basiskennis van het maken en beheren van sites in AEM | AEM-beheerder |
| Basiskennis van Cloud Manager | Cloud Manager-beheerder |

Voor de front-end ontwikkelaar is geen AEM kennis nodig.

### Gereedschappen {#tools}

| Gereedschap | Rol |
|---|---|
| Voorkeursontwikkelomgeving | Front-endontwikkelaar |
| npm | Front-endontwikkelaar |
| webpack | Front-endontwikkelaar |
| Toegang tot Cloud Manager | Cloud Manager-beheerder |
| Lid zijn van **Zakelijke eigenaar** rol in Cloud Manager | Cloud Manager-beheerder |
| Sys Admin in Cloud Manager zijn | Cloud Manager-beheerder |
| Toegang tot Admin Console | Cloud Manager-beheerder |
| Lid zijn van de **Implementatiebeheer** rol in Cloud Manager | Cloud Manager-beheerder |
| Lid zijn van de **Implementatiebeheer** rol in Cloud Manager | Front-endontwikkelaar |

Voor de front-end ontwikkelaar, is geen gebruik van AEM noodzakelijk.

>[!TIP]
>
>Als u niet bekend bent met de rollen en het rolbeheer van Cloud Manager, raadpleegt u het document Rolgebaseerde machtigingen in het dialoogvenster [Aanvullende bronnen](#additional-resources) sectie.

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één ingangspunt voor het platform.

Om klanten met de montages van de ondernemingsontwikkeling te steunen, AEM as a Cloud Service volledig integreert met de Manager van de Wolk en zijn doel-gebouwde CI/CD pijpleidingen. Met het gereedschap Snel site maken kunt u deze functies uitbreiden voor ondersteuning van speciale front-end ontwikkelingspijplijnen.

Voor deze reis is een volledig begrip van Cloud Manager niet nodig. Op hoog niveau bestaat Cloud Manager uit verschillende structuurniveaus.

![Cloud Manager-structuur](assets/cloud-manager-structure.png)

* **TENANT** - Elke klant wordt voorzien van een huurder.
* **PROGRAMMA&#39;S** - Elke huurder heeft één of meerdere programma&#39;s, die vaak de gelicentieerde oplossingen van de klant weerspiegelen.
* **OMGEVINGEN** - Elk programma heeft meerdere omgevingen, zoals productie voor live-inhoud, één voor staging en één voor ontwikkelingsdoeleinden.
* **BEVESTIGING** - De omgevingen beschikken over git-opslagruimten waar de toepassing en front-end code worden onderhouden.
* **GEREEDSCHAPPEN EN WORKFLOWS** - De pijpleidingen beheren de implementatie van code van de gegevensbanken aan de milieu&#39;s.

Een voorbeeld is vaak handig bij het contextualiseren van deze hiërarchie.

* WKND Travel and Adventure Enterprises zou een **huurder** die zich richt op reisgerelateerde media.
* De huurder van WKND Reizen en Adventure Enterprises zou twee kunnen hebben **programma&#39;s**: één Sites-programma voor WKND Magazine en één Assets-programma voor WKND Media.
* De programma&#39;s WKND Magazine en WKND Media zouden zowel dev, stadium, als productie hebben **omgevingen**.

## De snelle ontwikkeling van de Site Creation Front-End-ontwikkelingsstroom {#flow}

De algehele flow is eenvoudig en intuïtief, zelfs als u nog geen uitgebreide ervaring hebt met Cloud Manager.

1. De AEM beheerder ondertekent in een AEM milieu, en leidt tot een nieuwe plaats gebruikend een plaatssjabloon.
1. De beheerder van de Manager van de Wolk leidt tot een front-end pijpleiding in de Manager van de Wolk. De pijpleiding organiseert de plaatsing van code van een git bewaarplaats aan een AEM milieu.
1. De AEM beheerder voert het plaatsthema van de AEM instantie van het programma uit en verstrekt het aan de front-end ontwikkelaar.
1. De beheerder van de Manager van de Wolk verleent de front-end ontwikkelaar toegang tot de AEM git bewaarplaats waar de aanpassingen kunnen worden begaan.
1. De voorste eindontwikkelaar wint toegangsgeloofsbrieven aan toegangskit en de pijpleiding terug.
1. De front-end ontwikkelaar past het thema aan, test het het gebruikend daadwerkelijke inhoud van de plaats gebruikend een volmacht en begaat dan de veranderingen in de git bewaarplaats.
1. De front-end ontwikkelaar voert de pijpleiding uit om de themaaanpassingen aan het productiemilieu van het programma op te stellen.

![Snelle workflow voor het maken van sites](assets/qsc-flow.png)

Het belangrijkste voordeel van het gebruik van het gereedschap Snel maken is dat de zuivere front-end ontwikkelaar alleen verantwoordelijk is voor de werkelijke aanpassing. De front-end ontwikkelaar heeft geen interactie met AEM of heeft enige kennis van AEM nodig.

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de AEM Quick Site Creation-reis hebt voltooid, moet u:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om de ontwikkeling op de voorgrond te vergemakkelijken
* Ontdek hoe de stap voor aanpassing volledig losgekoppeld is van AEM en geen AEM kennis vereist.

Gebaseerd op deze kennis en doorgaan met uw AEM snelle site-creatie door het document opnieuw te bekijken [Site maken van sjabloon,](create-site.md) Hier leert u hoe u snel een nieuwe AEM-site kunt maken met een sjabloon.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de reis Snel site maken te gaan door het document te bekijken [Site maken van sjabloon,](create-site.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Als u meer informatie wilt over de functies van Cloud Manager, kunt u de diepgaande technische documenten direct raadplegen.
* [Op rollen gebaseerde machtigingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager heeft vooraf geconfigureerde rollen met de juiste machtigingen. Zie dit document voor details over deze rollen en hoe te om hen te beheren.
* [npm](https://www.npmjs.com) - AEM thema&#39;s die worden gebruikt om sites snel te bouwen, zijn gebaseerd op npm.
* [webpack](https://webpack.js.org) - AEM thema&#39;s die worden gebruikt om sites snel op te bouwen, zijn gebaseerd op webpack.
