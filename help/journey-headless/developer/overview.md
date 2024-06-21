---
title: AEM Headless CMS Developer Reis
description: Meer informatie over ontwikkeling zonder kop met Adobe Experience Manager (AEM) als een headless CMS. Leer hoe u functies als Content Models, Content Fragments en een GraphQL API kunt gebruiken voor het leveren van inhoud zonder kop.
landing-page-description: Krijg inzicht in de levering en implementatie van inhoud zonder kop. Meer weten over het ontwikkelen van uw strategie binnen uw bedrijf?
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 1%

---

# AEM Headless CMS Developer Reis {#aem-headless-developer-journey}

Welkom bij de documentatie voor ontwikkelaars die nog niet bekend zijn met Adobe Experience Manager CMS zonder kop!

Leer over de krachtige en flexibele functies zonder koppen, hun mogelijkheden en hoe u deze kunt gebruiken voor uw eerste project voor ontwikkeling zonder koppen. Deze reis verstrekt u van alle informatie u uw eerste headless toepassing moet ontwikkelen.

{{headless-trials-promotion}}

>[!CONTEXTUALHELP]
>id="aemcloud_headless_developer_resources"
>title="Bronnen voor ontwikkelaars zonder hoofd AEM en geavanceerde documentatie"
>abstract="Alles wat u nodig hebt om meer te leren over AEM CMS zonder kop en om betere toepassingen en snellere ervaringen te maken en te verzenden."
>additional-url="https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html" text="Bronnen voor ontwikkelaars zonder koppen AEM"

## Inleiding {#introduction}

Bij de headless-implementatie van AEM wordt gebruikgemaakt van Content Fragments Models en Content Fragments om de nadruk te leggen op het maken van gestructureerde, kanaalneutrale en herbruikbare fragmenten van inhoud en hun doorvoerkanalen. Hiervoor gaat het pagina- en componentbeheer verloren, zoals dat gebruikelijk is in volledige stapeloplossingen. Het is een modern en dynamisch ontwikkelingspatroon voor de implementatie van digitale ervaringen.

Deze gids leidt u door hoofdloze implementatieonderwerpen in AEM zodat wanneer u doet kunt u:

* U moet goed begrijpen wat de inhoud zonder kop levert en wat de voordelen ervan zijn.
* Begrijp AEM functies zonder kop en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Voer de eerste stappen uit die uw eerste AEM project zonder kop uitvoeren.

>[!TIP]
>
> Als u liever **leren door te doen** en beschikken over bestaande kennis van AEM, bezoek de AEM headless lesbestanden, die zijn georganiseerd door API en framework en beschikbaar zijn in de [Sectie Aanvullende bronnen](#additional-resources) aan het einde van dit document.

## Publiek {#audience}

Deze reis wordt ontworpen voor de ontwikkelaar persoonlijkheid, die de vereisten, de stappen, en de benadering van een AEM Zwaardeloos project vanuit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisopstelling en configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

## De headless Developer Journey {#the-journey}

Wij zullen veel onderwerpen op deze reis behandelen, die u van de stichtende kennis van hoofdloze in AEM zal voorzien.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, zijn veel concepten gebaseerd op die in vorige artikelen. Adobe raadt u aan aan aan het begin te beginnen en de stappen opeenvolgend te maken.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [Meer informatie over CMS Headless Development](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [Aan de slag met AEM headless as a Cloud Service](getting-started.md) | Meer informatie over AEM vereisten voor headless |
| 3 | [Pad naar uw eerste ervaring met AEM zonder kop](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [Uw inhoud modelleren](model-your-content.md) | Leer hoe u uw inhoudsstructuur kunt modelleren. |
| 5 | [Toegang krijgen tot uw inhoud via AEM API&#39;s voor levering](access-your-content.md) | Leer hoe u GraphQL-query&#39;s gebruikt om toegang te krijgen tot inhoud van Content Fragments. |
| 6 | [Inhoud bijwerken via AEM Assets API&#39;s](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [Alles bij elkaar zetten - uw app en uw inhoud in AEM headless](put-it-all-together.md) | Leer hoe u uw AEM Project neemt en voorbereidt voor live gaan met de AEM Headless SDK. |
| 8 | [Live gaan met uw toepassing zonder kop](go-live.md) | Leer hoe u de toepassing live kunt implementeren en uw lokale code in Git kunt plaatsen en deze kunt verplaatsen naar Cloud Manager Git voor CI/CD-pijplijn. |
| 9 | [Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met AEM](create-spa.md) | Ontdek hoe u krachtige en koploze SPA kunt combineren en hoe u bewerkbare SPA kunt maken met AEM Editor-framework. |

{style="table-layout:auto"}

## Volgende functies {#what-is-next}

Ga aan de slag met het volgende artikel: [Meer informatie over CMS Headless Development.](learn-about.md)

### Kies uw eigen avontuur {#choose-your-path}

Wil je in je eigen tempo leren? Bekijk de volgende opties:

* Als u liever wilt doorgaan **meer informatie over concepten zonder kop en AEM technologieën zonder kop**, moet u doorgaan met uw AEM zonder kop, zoals wordt aanbevolen door het document opnieuw te bekijken [Hoe te om Uw Inhoud als Modellen van de Inhoud te modelleren AEM](model-your-content.md) waar u leert hoe u de inhoudsstructuur in AEM modelleert.
* Als u liever **leren door te doen**, kunt u naar de [Aan de slag met AEM praktische zelfstudie zonder hoofd](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u rechtstreeks in AEM Zwaardeloze ontwikkeling door een eenvoudig project zult springen om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te verstrekken dat u door verwante processen en eigenschappen begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Bekijk deze extra reizen voor meer informatie over hoe AEM krachtige functies samenwerken.

* De [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [Zelfstudies zonder koppen AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - Als u liever wilt leren door te werken en bestaande kennis van AEM hebt, neemt u onze praktische zelfstudies die zijn georganiseerd door API en framework, die het maken en gebruiken van toepassingen die zijn gebaseerd op AEM Headless onderzoeken.
* [AEM doorsnedenloze vertaalreis](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een ruim inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient en hoe u deze kunt vertalen.
* [Papierreis zonder koppen](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [Architect zonder hoofd](/help/journey-headless/architect/overview.md) - Begin hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager as a Cloud Service en hoe u inhoud voor uw project kunt modelleren.
* [as a Cloud Service technische documentatie AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - Als u al een goed inzicht hebt in AEM en technologieën zonder kop, bekijkt u onze diepgaande technische documenten.
   * [Inleiding tot AEM als een headless CMS](/help/headless/introduction.md)
