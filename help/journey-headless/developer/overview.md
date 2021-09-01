---
title: AEM Headless Developer Journey
description: Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste ontwikkelingsproject te gebruiken.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: 387e75faeccb0671a32a54ff0c12f05219844311
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 1%

---

# AEM Headless Developer Journey {#aem-headless-developer-journey}

Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste project zonder titel te gebruiken.

## Inleiding {#introduction}

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels. De implementatie is gericht op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering ervan via meerdere kanalen. Het is een modern en dynamisch ontwikkelingspatroon voor de implementatie van digitale ervaringen.

Deze gids leidt u door de belangrijkste implementatieonderwerpen in AEM zodat u na voltooiing:

* U moet goed begrijpen wat de inhoud zonder kop levert en wat de voordelen ervan zijn.
* Begrijp AEM functies zonder kop en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Heb de capaciteit om de eerste stappen uit te voeren die uw eerste AEM hoofdloze project uitvoeren.

## AEM Documentenreizen {#documentation-journeys}

[Een Documentation ](/help/journey-documentation/home.md) Journeyties verenigt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn ontworpen op basis van de beginselen van best practices, gebaseerd op de meest recente onderzoeken, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

Als u wilt weten hoe Adobe adviseert om zaken zonder kop met AEM op te lossen, [AEM zijn de Transparanten zonder Zetel](/help/journey-headless/home.md) waar te beginnen.

>[!TIP]
>
> Als u liever **leert door te doen** en technisch gezien zijn, gaat u naar de AEM zelfstudies zonder koppen, die zijn georganiseerd door API en framework en beschikbaar zijn in de [Aanvullende bronnen sectie](#additional-resources) aan het einde van dit document.

## Publiek {#audience}

Deze reis wordt ontworpen voor de ontwikkelaar persoonlijkheid, die de vereisten, de stappen, en de benadering van een AEM Zwaardeloos project vanuit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisopstelling en configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

Informatie op deze reis kan natuurlijk nuttig zijn voor iedereen, maar sommige informatie kan voor bepaalde rollen overbodig zijn. Blijf op de hoogte voor [komende reizen die extra rollen behandelen.](/help/journey-documentation/home.md#journeys)

## De headless Developer Journey {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. In de volgende artikelen wordt u op basis van uw kennis van de kop in AEM en een link naar gedetailleerde technische documentatie weergegeven.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom adviseren wij als u in AEM nieuw bent om zonder kop te beginnen, dat u aan het begin begint en opeenvolgend vordert.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [Meer informatie over CMS Headless Development](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [Aan de slag met AEM Headless als Cloud Service](getting-started.md) | Meer informatie over AEM vereisten voor headless |
| 3 | [Pad naar uw eerste ervaring met AEM zonder kop](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [Hoe te om uw inhoud te modelleren](model-your-content.md) | Leer hoe u uw inhoudsstructuur kunt modelleren. Dan realiseer die structuur voor Adobe Experience Manager (AEM) gebruikend de Modellen van de Fragmenten van de Inhoud en de Fragmenten van de Inhoud, voor hergebruik over kanalen. |
| 5 | [Toegang krijgen tot uw inhoud via AEM API&#39;s voor levering](access-your-content.md) | Leer hoe te om vragen te gebruiken GraphQL om tot uw inhoud van de Fragmenten van de Inhoud toegang te hebben. |
| 6 | [Inhoud bijwerken via AEM Assets API&#39;s](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [Alles bij elkaar zetten - uw app en uw inhoud in AEM headless](put-it-all-together.md) | Leer hoe u uw AEM Project neemt en voorbereidt voor live gaan met de AEM Headless SDK. |
| 8 | [Live gaan met uw toepassing zonder kop](go-live.md) | Leer hoe u de toepassing live kunt implementeren en uw lokale code in Git kunt plaatsen en deze kunt verplaatsen naar Cloud Manager Git voor CI/CD-pijplijn. |
| 9 | [Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met AEM](create-spa.md) | Als u AEM functies zonder kop begrijpt, kunt u experimenteren met een combinatie van een krachtige en koploze levering en leren hoe u bewerkbare SPA kunt maken met AEM SPA Editor-framework. |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan op uw Adobe Headless reis. We raden u aan door te gaan met het volgende gedeelte van de reis en het artikel [Meer informatie over CMS Headless Development te lezen.](learn-about.md)

### Kies uw eigen avontuur {#choose-your-path}

Nochtans, wil Adobe u slagen aangezien u met uw AEM Headless project, ongeacht uw het leren stijl begint. Overweeg deze twee opties alstublieft.

* Als u liever **meer wilt leren over concepten zonder kop en AEM technologieën zonder kop**, kunt u de AEM doorlopen zoals aanbevolen door het document [How to Model Your Content as AEM Content Models](model-your-content.md) te bekijken, waarin u leert hoe u de inhoudstructuur in AEM modelleert.
* Als u verkiest om **te leren door te doen**, kunt u aan [Aan de slag met AEM Hoofdloze hands-on leerprogramma](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) springen waar u direct in AEM Ontwikkelt zonder Titel door een eenvoudig project uit te voeren om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te verstrekken dat u door complexe, onderling samenhangende processen en eigenschappen begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn de trajecten bedoeld om zelfstandig te staan. Een aantal ervan kan echter met elkaar verwant zijn. Bekijk deze extra reizen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [AEM zelfstudies](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)  zonder koppen - Als u liever wilt leren door te doen en technisch georiënteerd bent, neemt u onze praktische zelfstudies die zijn georganiseerd door API en framework, die het maken en gebruiken van toepassingen die zijn gebaseerd op AEM Headless onderzoeken.
* [AEM Headless Translation Journey](/help/journey-headless/translation/overview.md)  - Deze documentatietraject geeft u een ruim inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient en hoe u deze kunt vertalen.
* [Headless Authoring Journey](/help/journey-headless/author/overview.md)  - Begin hier voor een begeleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden en hoe u uw inhoud kunt modelleren op uw eerste project zonder kop.
* [Headless Architect Journey](/help/journey-headless/architect/overview.md)  - Begin hier voor een introductie van de krachtige, flexibele, ongekende functies van Adobe Experience Manager als Cloud Service en hoe u inhoud voor uw project kunt modelleren.
* [AEM als technische documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html)  van de Cloud Service - Als u reeds een stevig inzicht in AEM en headless technologieën hebt, kunt u onze diepgaande technische documenten direct willen raadplegen.
