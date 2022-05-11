---
title: AEM Headless Developer Journey
description: 'Begin hier voor een geleide reis door Adobe Experience Manager (AEM) as a Cloud Service wanneer het als Zwaardeloos Systeem van het Inhoudsbeheer (CMS) wordt gebruikt. Leer over de krachtige en flexibele functies zonder koppen, hun mogelijkheden en hoe u deze kunt gebruiken voor uw eerste project voor ontwikkeling zonder koppen. Deze reis verstrekt u van alle informatie u uw eerste headless toepassing moet ontwikkelen. '
landing-page-description: 'Krijg inzicht in de levering en implementatie van inhoud zonder kop. Meer weten over het ontwikkelen van uw strategie binnen uw bedrijf? '
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: 2ec6b29800867462bbc2e88048c583d4e5eefa57
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 1%

---

# AEM Headless Developer Journey {#aem-headless-developer-journey}

Hier beginnen voor een geleide reis door [!DNL Adobe Experience Manager as a Cloud Service] (AEM) wanneer het wordt gebruikt als een CMS (Headless Content Management System). Leer over de krachtige en flexibele functies zonder koppen, hun mogelijkheden en hoe u deze kunt gebruiken voor uw eerste project voor ontwikkeling zonder koppen. Deze reis verstrekt u van alle informatie u uw eerste headless toepassing moet ontwikkelen.

## Inleiding {#introduction}

Bij de headless-implementatie van AEM wordt gebruikgemaakt van Content Fragments Models en Content Fragments om de nadruk te leggen op het maken van gestructureerde, kanaalneutrale en herbruikbare fragmenten van inhoud en hun doorvoerkanalen. Hiervoor gaat het pagina- en componentbeheer verloren, zoals dat gebruikelijk is in volledige stapeloplossingen. Het is een modern en dynamisch ontwikkelingspatroon voor de implementatie van digitale ervaringen.

Deze gids leidt u door de belangrijkste implementatieonderwerpen in AEM zodat u na voltooiing:

* U moet goed begrijpen wat de inhoud zonder kop levert en wat de voordelen ervan zijn.
* Begrijp AEM functies zonder kop en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Heb de capaciteit om de eerste stappen uit te voeren die uw eerste AEM hoofdloze project uitvoeren.

## AEM Documentenreizen {#documentation-journeys}

[Een documentatiereis](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen met elkaar door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn ontworpen op basis van de beginselen van best practices, gebaseerd op de meest recente onderzoeken, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

Als u wilt weten hoe Adobe adviseert hoe te om hoofdloze zaken met AEM op te lossen, [Reizen zonder kop AEM](/help/journey-documentation/documentation-journeys.md) zijn waar te beginnen.

>[!TIP]
>
> Als u liever **leren door** en technisch gezien zijn, gaat u naar de AEM headless lesbestanden, die zijn georganiseerd door API en framework en beschikbaar zijn in het [Sectie Aanvullende bronnen](#additional-resources) aan het einde van dit document.

## Publiek {#audience}

Deze reis wordt ontworpen voor de ontwikkelaar persoonlijkheid, die de vereisten, de stappen, en de benadering van een AEM Zwaardeloos project vanuit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisopstelling en configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

Informatie op deze reis kan natuurlijk nuttig zijn voor iedereen, maar sommige informatie kan voor bepaalde rollen overbodig zijn. Blijf op de hoogte voor [komende reizen die bijkomende rollen bestrijken.](/help/journey-documentation/documentation-journeys.md#journeys)

## De headless Developer Journey {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. In de volgende artikelen wordt u op basis van uw kennis van de kop in AEM en een link naar gedetailleerde technische documentatie weergegeven.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom adviseren wij als u in AEM nieuw bent om zonder kop te beginnen, dat u aan het begin begint en opeenvolgend vordert.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [Meer informatie over CMS Headless Development](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [Aan de slag met AEM headless as a Cloud Service](getting-started.md) | Meer informatie over AEM vereisten voor headless |
| 3 | [Pad naar uw eerste ervaring met AEM zonder kop](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [Hoe te om uw inhoud te modelleren](model-your-content.md) | Leer hoe u uw inhoudsstructuur kunt modelleren. Dan realiseer die structuur voor Adobe Experience Manager (AEM) gebruikend de Modellen van de Fragmenten van de Inhoud en de Fragmenten van de Inhoud, voor hergebruik over kanalen. |
| 5 | [Toegang krijgen tot uw inhoud via AEM API&#39;s voor levering](access-your-content.md) | Leer hoe te om vragen te gebruiken GraphQL om tot uw inhoud van de Fragmenten van de Inhoud toegang te hebben. |
| 6 | [Inhoud bijwerken via AEM Assets API&#39;s](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [Alles bij elkaar zetten - uw app en uw inhoud in AEM headless](put-it-all-together.md) | Leer hoe u uw AEM Project neemt en voorbereidt voor live gaan met de AEM Headless SDK. |
| 8 | [Live gaan met uw toepassing zonder kop](go-live.md) | Leer hoe u de toepassing live kunt implementeren en uw lokale code in Git kunt plaatsen en deze kunt verplaatsen naar Cloud Manager Git voor CI/CD-pijplijn. |
| 9 | [Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met AEM](create-spa.md) | Als u AEM functies zonder kop begrijpt, kunt u experimenteren met een combinatie van een krachtige en koploze levering en leren hoe u bewerkbare SPA kunt maken met AEM SPA Editor-framework. |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan op uw Adobe Headless reis. We raden u aan door te gaan naar het volgende deel van de reis en het artikel te lezen [Meer informatie over CMS Headless Development.](learn-about.md)

### Kies uw eigen avontuur {#choose-your-path}

Nochtans, wil Adobe u slagen aangezien u met uw AEM Headless project, ongeacht uw het leren stijl begint. Overweeg deze twee opties alstublieft.

* Als u liever wilt doorgaan **meer informatie over headless-concepten en AEM headless-technologieën**, moet u doorgaan met uw AEM zonder kop, zoals wordt aanbevolen door het document opnieuw te bekijken [Hoe te om Uw Inhoud als Modellen van de Inhoud te modelleren AEM](model-your-content.md) waar u leert hoe u de inhoudsstructuur in AEM modelleert.
* Als u liever **leren door**, kunt u naar de [Aan de slag met AEM praktische zelfstudie zonder hoofd](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u rechtstreeks in AEM Zwaardeloze ontwikkeling door een eenvoudig project zult springen om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te verstrekken dat u door complexe, onderling samenhangende processen en eigenschappen begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn de trajecten bedoeld om zelfstandig te staan. Een aantal ervan kan echter met elkaar verwant zijn. Bekijk deze extra reizen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [Zelfstudies zonder koppen AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - Als u liever wilt leren door te doen en technisch georiënteerd bent, neemt u onze praktische zelfstudies die zijn georganiseerd door API en framework, die het maken en gebruiken van toepassingen die zijn gebaseerd op AEM Headless onderzoeken.
* [AEM doorlopende vertaalreis](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een ruim inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient en hoe u deze kunt vertalen.
* [Papierreis zonder koppen](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [Architect zonder hoofd](/help/journey-headless/architect/overview.md) - Begin hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager as a Cloud Service en hoe u inhoud voor uw project kunt modelleren.
* [as a Cloud Service technische documentatie AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - Als u al een duidelijk inzicht hebt in AEM en technologieën zonder kop, kunt u onze diepgaande technische documenten direct raadplegen.
