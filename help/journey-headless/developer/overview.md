---
title: AEM Headless CMS Developer Journey
description: Meer informatie over ontwikkeling zonder kop met Adobe Experience Manager (AEM) als een Headless CMS. Leer hoe u functies als Content Models, Content Fragments en een GraphQL API kunt gebruiken voor het leveren van inhoud zonder kop.
landing-page-description: Krijg inzicht in de levering en implementatie van inhoud zonder kop. Meer weten over het ontwikkelen van uw strategie binnen uw bedrijf?
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 1%

---

# AEM Headless CMS Developer Journey {#aem-headless-developer-journey}

Welkom bij de documentatie voor nieuwe ontwikkelaars van Adobe Experience Manager, CMS zonder kop!

Leer over de krachtige en flexibele functies zonder koppen, hun mogelijkheden en hoe u deze kunt gebruiken voor uw eerste project voor ontwikkeling zonder koppen. Deze reis verstrekt u van alle informatie u uw eerste headless toepassing moet ontwikkelen.

>[!CONTEXTUALHELP]
>id="aemcloud_headless_developer_resources"
>title="AEM Headless-ontwikkelaarsbronnen en geavanceerde documentatie"
>abstract="Alles wat u nodig hebt om meer te leren over CMS zonder kop en betere toepassingen en snellere ervaringen te maken en te verzenden."
>additional-url="https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html" text="AEM Headless developer-bronnen"


## Inleiding {#introduction}

Bij de headless-implementatie van AEM worden Content Fragments Models en Content Fragments gebruikt om de nadruk te leggen op het maken van gestructureerde, kanaalneutrale en herbruikbare fragmenten van inhoud en de levering van deze fragmenten tussen kanalen. Hiervoor gaat het pagina- en componentbeheer verloren, zoals dat gebruikelijk is in volledige stapeloplossingen. Het is een modern en dynamisch ontwikkelingspatroon voor de implementatie van digitale ervaringen.

Deze gids leidt u door hoofdloze implementatieonderwerpen in AEM zodat wanneer u klaar bent u kunt:

* U moet goed begrijpen wat de inhoud zonder kop levert en wat de voordelen ervan zijn.
* Begrijp de baanloze AEM-functies en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Voer de eerste stappen uit om uw eerste AEM-project zonder kop uit te voeren.

## Publiek {#audience}

Deze reis is ontworpen voor de ontwikkelaar persona, die de vereisten, de stappen, en de benadering van een AEM Headless project uit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisconfiguratie en -configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

## De headless Developer Journey {#the-journey}

Wij zullen veel onderwerpen op deze reis behandelen, die u van de stichtende kennis van krantenkoppen in AEM zal voorzien.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, zijn veel concepten gebaseerd op die in vorige artikelen. Adobe raadt u aan om aan het begin te beginnen en op volgorde verder te gaan.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [ Leer over de Hoofdloze Ontwikkeling van CMS ](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [ Begonnen het Worden met AEM Headless as a Cloud Service ](getting-started.md) | Meer informatie over AEM Headless-vereisten |
| 3 | [ Weg aan uw eerste ervaring gebruikend de Zetel van AEM ](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [ hoe te om uw inhoud ](model-your-content.md) te modelleren | Leer hoe u uw inhoudsstructuur kunt modelleren. |
| 5 | [ hoe te om tot uw inhoud via levering APIs van AEM toegang te hebben ](access-your-content.md) | Leer hoe u GraphQL-query&#39;s gebruikt om toegang te krijgen tot inhoud van Content Fragments. |
| 6 | [ hoe te om uw inhoud via AEM Assets APIs bij te werken ](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [ hoe te om het allen samen te zetten - uw app en uw inhoud in AEM Headless ](put-it-all-together.md) | Leer hoe u uw AEM-project kunt nemen en voorbereiden op live gaan met de AEM Headless SDK. |
| 8 | [ hoe te om met uw headless toepassing te gaan ](go-live.md) | Leer hoe u de toepassing live kunt implementeren en uw lokale code in Git kunt plaatsen en naar Cloud Manager Git voor CI/CD-pijpleiding kunt verplaatsen. |
| 9 | [ Facultatief - hoe te om enige paginatoepassingen (SPAs) met AEM ](create-spa.md) tot stand te brengen | Onderzoek hoe te om krachtige en zonder kop levering te combineren en te leren hoe u editable SPAs kunt tot stand brengen gebruikend het kader van de Redacteur van het KUUROORD van AEM. |

{style="table-layout:auto"}

## Volgende functies {#what-is-next}

Ga aan de slag door het volgende artikel uit te checken: [ Leer meer over CMS Headless Development ](learn-about.md) ,

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te bieden dat u door verwante processen en functies begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als u liever wilt leren door AEM te doen en er al kennis van hebt, neemt u onze praktische zelfstudies die zijn georganiseerd door API en framework, die het maken en gebruiken van toepassingen die zijn gebaseerd op AEM Headless onderzoeken. Zie [ Leerprogramma&#39;s voor Hoofdtelefoon in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html).

Bekijk deze extra ritten voor meer informatie over hoe de krachtige functies van AEM samenwerken.

* Het [ Portaal van de Ontwikkelaar van AEM ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ de Vertaalreis van 0} AEM Headless ](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een breed inzicht in headless technologie, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.
* [ Koploze het Authoring Reis ](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [ Eis van de Architect zonder hoofd ](/help/journey-headless/architect/overview.md) - Begin hier voor een inleiding aan de krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager as a Cloud Service, en hoe te om inhoud voor uw project te modelleren.
* [ de technische documentatie van AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - als u reeds een stevig inzicht in AEM en headless technologieën hebt, controleer onze diepgaande technische documenten.
   * [Inleiding tot AEM als een CMS zonder kop](/help/headless/introduction.md)
