---
title: Invoegtoepassing demodemodus begrijpen
description: Meer informatie over Cloud Manager en hoe de invoegtoepassing wordt geïnstalleerd.
exl-id: 9418aac6-a8c4-43f7-b329-b02149fe2d53
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---

# Invoegtoepassing demodemodus begrijpen {#understand-installation}

Meer informatie over Cloud Manager en hoe de invoegtoepassing wordt geïnstalleerd.

>[!TIP]
>
>Als u met Cloud Manager wordt ervaren of rechtstreeks aan configuratie en gebruik van toe:voegen-op wilt springen, overslaan aan [ creeer een Programma en een Pijpleiding ](create-program.md)
>
>Als u wilt leren hoe Cloud Manager en AEM samenwerken om uw demo-omgevingen te maken en hoe u uw eigen omgevingen kunt instellen en gebruiken, blijft u het huidige document lezen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe het installatieproces van de Add-on van de Demo van de Verwijzing werkt, die hoe de verschillende stukken samenwerken. Na het lezen moet u:

* Een basisbegrip hebben van Cloud Manager.
* Begrijp hoe de pijpleidingen inhoud en configuratie aan AEM leveren.
* Bekijk hoe sjablonen met slechts een paar klikken sites kunnen maken die vooraf zijn gevuld met demo-inhoud.

Dit document richt zich op het begrijpen van deze fundamentele stukken van de AEM Toeslag van de Demo van de Verwijzing alvorens tot de volgende stap van de reis over te gaan waar u met installatie begint.

Hoewel het wordt geadviseerd om door deze reis te werk te gaan, als u met Cloud Manager wordt ervaren, of rechtstreeks aan configuratie en gebruik van toe:voegen-op wilt springen, overslaan aan [ creeer een Programma en een Pijpleiding ](create-program.md).

## Verantwoordelijke rol {#responsible-role}

Deze reis is op een systeembeheerder van toepassing die een lid van de **rol van de BedrijfsEigenaar** in Cloud Manager voor uw organisatie is.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn minimale vereisten om over te leren en te beginnen gebruiken de Add-on van de Demo van de Verwijzing.

### Kennis {#knowledge}

* Basiskennis van Cloud Manager

### Gereedschappen {#tools}

* Ben een lid van **BedrijfsEigenaar** rol in Cloud Manager voor uw organisatie

## Cloud Manager begrijpen {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als enig toegangspunt voor het platform.

Cloud Manager wordt gebruikt voor het beheer van de cloudbronnen die uw AEM Projecten ondersteunen, inclusief de benodigde omgevingen en tools. Voor deze reis is een volledig begrip van Cloud Manager niet nodig. Nochtans, moet u met sommige basisconcepten vertrouwd zijn.

>[!TIP]
>
>Als u over Cloud Manager in detail wilt leren, zie ](#additional-resources) sectie van de Middelen van 0} Extra van Middelen {voor verbindingen aan meer informatie.[

### Programma&#39;s {#programs}

Wanneer u in Cloud Manager ondertekent, hebt u toegang tot één of meerdere **programma&#39;s**. Een programma kan op verschillende manieren worden gedefinieerd, maar het is het eenvoudigst om eraan te denken dat het verband houdt met de sites en ervaringen die verband houden met één merkidentiteit.

Als u in Cloud Manager ondertekent die **WKND Reizen en de Onderneming van het Avontuur vertegenwoordigt**, zou u a **WKND 3} programma en a** WKND achtertuinProjecten **programma kunnen tot stand brengen.** Beide programma&#39;s zouden AEM omgevingen hebben voor het beheer van de bijbehorende sites.

### Sandboxen {#sandboxes}

De programma&#39;s kunnen of productieprogramma&#39;s of zandbakprogramma&#39;s zijn.

* **A productieprogramma** wordt gecreeerd om levend verkeer uiteindelijk toe te staan wanneer uw programma klaar is om te leven.
* **het zandbakprogramma van A** wordt gecreeerd voor opleiding, lopende demo&#39;s, enablement, POCs, etc., en is niet bedoeld voor levend verkeer.

Maak een sandboxprogramma om de AEM Reference Demos Add-on te installeren.

>[!NOTE]
>
>De invoegtoepassing AEM Reference Demos is alleen beschikbaar in sandboxprogramma&#39;s.

## Installatie- en gebruiksstroom {#installation-flow}

Nu u sommige fundamentele concepten van Cloud Manager begrijpt, is de installatie van AEM Invoegtoepassing van de Demos van de Verwijzing conceptueel eenvoudig.

1. Log in bij Cloud Manager.
1. Maak een AEM van een sandbox en activeer de optie Demo&#39;s van AEM referentie toevoegen als optie voor het programma.
1. De demo-inhoud en -configuratie worden geïmplementeerd in het programma. De demo-inhoud bevat:
   * Sitesjablonen die worden gebruikt om verschillende AEM sites te maken met behulp van functies van AEM, die vooraf zijn gevuld met voorbeelden van best practices.
   * De hulpmiddelen van de configuratie om uw demo inhoud te beheren.
1. Meld u aan bij AEM in uw nieuwe sandboxprogramma en gebruik het gereedschap Snel site maken en maak demosites op basis van de sjablonen.
1. Gebruik de configuratiehulpmiddelen om die demoplaatsen en malplaatje met inbegrip van het schrappen van hen te beheren wanneer niet meer nodig.

## Sitesjablonen AEM {#site-templates}

AEM Sitesjablonen zijn pakketten met vooraf gedefinieerde inhoud en structuur voor een site. De malplaatjes van de plaats kunnen worden aangepast om aan de behoeften van specifieke projecten te voldoen zodat wanneer AEM beheerders plaatsen creëren, kunnen zij van malplaatjes kiezen die op hun bedrijfsgevallen van toepassing zijn.

De AEM Add-on voor demo&#39;s bevat meerdere sjablonen voor verschillende test- en demonstratiebehoeften. Zodra u uw programma hebt gecreeerd en de pijpleiding opgesteld om toe:voegen-aan te installeren, kunt u login AEM en plaatsen tot stand brengen die op vele demo malplaatjes worden gebaseerd

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Toestemmingsreis van de Demos van de Verwijzing hebt voltooid, zou u moeten:

* Een basisbegrip hebben van Cloud Manager.
* Begrijp hoe de pijpleidingen inhoud en configuratie aan AEM leveren.
* Bekijk hoe sjablonen met slechts een paar klikken sites kunnen maken die vooraf zijn gevuld met demo-inhoud.

Bouw op deze kennis voort en ga uw AEM Snelle reis van de Aanmaak van de Plaats door te herzien [ creeer een Programma en een Pijpleiding ](create-program.md), waar u leert hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich naar het volgende deel van de Snelle reis van de Verwezenlijking van de Plaats door te herzien [ creeert een Programma en een Pijpleiding ](create-program.md), zijn het volgende wat extra, facultatieve middelen. Deze middelen nemen een diepere duik in concepten in dit document worden vermeld. Zij zijn echter niet verplicht de reis voort te zetten.

* [ Begrip Programma&#39;s en de Types van Programma ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/program-types.html) - Begin hier om de verschillen tussen levende en zandbakprogramma&#39;s te begrijpen.
* [ Malplaatjes van de Plaats ](/help/sites-cloud/administering/site-creation/site-templates.md) - als u meer over de structuur van plaatssjablonen zou willen weten en hoe zij worden gebruikt om plaatsen tot stand te brengen, verwijs naar dit document.
* [ documentatie van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html) - als u meer details over de eigenschappen van Cloud Manager zou willen, kunt u de diepgaande technische documenten direct willen raadplegen.
