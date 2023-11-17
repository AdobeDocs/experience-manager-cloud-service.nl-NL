---
title: Invoegtoepassing demodemodus begrijpen
description: Leer meer over Cloud Manager en hoe deze wordt gebruikt om de invoegtoepassing te installeren.
exl-id: 9418aac6-a8c4-43f7-b329-b02149fe2d53
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 0%

---

# Invoegtoepassing demodemodus begrijpen {#understand-installation}

Leer meer over Cloud Manager en hoe deze wordt gebruikt om de invoegtoepassing te installeren.

>[!TIP]
>
>Als u ervaring hebt met Cloud Manager of als u rechtstreeks naar de configuratie en het gebruik van de invoegtoepassing wilt gaan, gaat u verder [Een programma en een pijplijn maken](create-program.md)
>
>Als u wilt leren hoe Cloud Manager en AEM samenwerken om uw demo-omgevingen te maken en hoe u uw eigen omgevingen kunt instellen en gebruiken, blijft u het huidige document lezen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe het installatieproces van de Add-on van de Demo van de Verwijzing werkt, die hoe de verschillende stukken samenwerken. Na het lezen moet u:

* U hebt een basiskennis van Cloud Manager.
* Begrijp hoe de pijpleidingen inhoud en configuratie aan AEM leveren.
* Bekijk hoe sjablonen met slechts een paar klikken sites kunnen maken die vooraf zijn gevuld met demo-inhoud.

Dit document richt zich op het begrijpen van deze fundamentele stukken van de AEM Toeslag van de Demo van de Verwijzing alvorens tot de volgende stap van de reis over te gaan waar u met installatie begint.

Hoewel het wordt geadviseerd om door deze reis te werk te gaan, als u met de Manager van de Wolk ervaring hebt, of aan configuratie en gebruik van toe:voegen-aan direct wilt springen, overslaan aan [Een programma en een pijplijn maken](create-program.md).

## Verantwoordelijke rol {#responsible-role}

Deze reis is op een systeembeheerder van toepassing die een lid van is **Zakelijke eigenaar** rol in Cloud Manager voor uw organisatie.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn minimale vereisten om over te leren en te beginnen gebruiken de Add-on van de Demo van de Verwijzing.

### Kennis {#knowledge}

* Basiskennis van Cloud Manager

### Gereedschappen {#tools}

* Lid zijn van **Zakelijke eigenaar** rol in Cloud Manager voor uw organisatie

## Werken met Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één ingangspunt voor het platform.

Cloud Manager wordt gebruikt voor het beheer van de cloudbronnen die uw AEM projecten ondersteunen, inclusief de omgevingen en tools die nodig zijn. Voor deze reis is een volledig begrip van Cloud Manager niet nodig. Nochtans, moet u met sommige basisconcepten vertrouwd zijn.

>[!TIP]
>
>Ga voor meer informatie over Cloud Manager naar [Aanvullende bronnen](#additional-resources) in dit artikel voor koppelingen naar meer informatie.

### Programma&#39;s {#programs}

Als u zich aanmeldt bij Cloud Manager, hebt u toegang tot een of meer **programma&#39;s**. Een programma kan op verschillende manieren worden gedefinieerd, maar het is het eenvoudigst om eraan te denken dat het verband houdt met de sites en ervaringen die verband houden met één merkidentiteit.

Als u zich aanmeldt bij Cloud Manager die **WKND Reizen- en avontuurbedrijven** kunt u een **WKND Nightlife** programma en **WKND-projecten** programma. Beide programma&#39;s zouden AEM omgevingen hebben voor het beheer van de bijbehorende sites.

### Sandboxen {#sandboxes}

De programma&#39;s kunnen of productieprogramma&#39;s of zandbakprogramma&#39;s zijn.

* **Een productieprogramma** wordt gecreeerd om levend verkeer uiteindelijk toe te staan wanneer uw programma klaar is om te leven.
* **Een sandboxprogramma** wordt gecreeerd voor opleiding, lopende demo&#39;s, enablement, POCs, etc., en is niet bedoeld voor levend verkeer.

Maak een sandboxprogramma om de AEM Reference Demos Add-on te installeren.

>[!NOTE]
>
>De invoegtoepassing AEM Reference Demos is alleen beschikbaar in sandboxprogramma&#39;s.

## Installatie- en gebruiksstroom {#installation-flow}

Nu u sommige fundamentele concepten van de Manager van de Wolk begrijpt, is de installatie van AEM Invoegsel van de Demo van de Verwijzing conceptueel eenvoudig.

1. Meld u aan bij Cloud Manager.
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

* U hebt een basiskennis van Cloud Manager.
* Begrijp hoe de pijpleidingen inhoud en configuratie aan AEM leveren.
* Bekijk hoe sjablonen met slechts een paar klikken sites kunnen maken die vooraf zijn gevuld met demo-inhoud.

Bouw op deze kennis voort en zet uw AEM snelle reis van de Plaats door te herzien [Een programma en een pijpleiding maken,](create-program.md) waar u leert hoe te opstelling een nieuw programma en een pijpleiding om toe:voegen-op op te stellen.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de reis Snel site maken te gaan door het volgende gedeelte te bekijken [Een programma en een pijplijn maken](create-program.md)Hieronder volgen enkele aanvullende, optionele bronnen. Deze middelen nemen een diepere duik in concepten in dit document worden vermeld. Zij zijn echter niet verplicht de reis voort te zetten.

* [Programma&#39;s en programmatypen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/program-types.html) - Begin hier om de verschillen tussen live- en sandboxprogramma&#39;s te begrijpen.
* [Sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md) - Raadpleeg dit document als u meer wilt weten over de structuur van sitesjablonen en hoe u deze gebruikt om sites te maken.
* [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Als u meer informatie wilt over de functies van Cloud Manager, kunt u de diepgaande technische documenten direct raadplegen.
