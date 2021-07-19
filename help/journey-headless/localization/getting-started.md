---
title: Aan de slag met AEM headless localisatie
description: Leer hoe u uw inhoud zonder kop kunt ordenen en hoe AEM lokalisatieprogramma's werken.
source-git-commit: 22ca7c01bfddb407c119de7d9a4d105941772664
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Aan de slag met AEM headless Localization {#getting-started}

Leer hoe u uw inhoud zonder kop kunt ordenen en hoe AEM lokalisatieprogramma&#39;s werken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless localisatietraject, [Leer over inhoud zonder kop en hoe u zich in AEM](learn-about.md) kunt lokaliseren, leerde u de basistheorie van wat een headless CMS is en u zou nu moeten:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM ondersteuning biedt voor headless en lokalisatie.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe AEM inhoud zonder kop opslaat en beheert en hoe u AEM lokalisatiehulpmiddelen kunt gebruiken om die inhoud te vertalen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe u inhoud zonder kop in AEM kunt gaan lokaliseren. Na het lezen moet u:

* Begrijp het belang van inhoudsstructuur voor localisatie.
* Begrijp hoe AEM inhoud zonder kop opslaat.
* Wees vertrouwd met AEM lokalisatieprogramma&#39;s.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn een aantal vereisten voordat u inhoud zonder kop gaat lokaliseren AEM inhoud.

### Kennis {#knowledge}

* Ervaar het lokaliseren van inhoud voor een CMS
* Ervaar het gebruiken van de basiseigenschappen van grootschalig CMS
* Werken met AEM basisverwerking
* Kennis van de vertaalservice die u gebruikt
* Basiskennis hebben van de inhoud die u wilt vertalen

>[!TIP]
>
>Als u niet vertrouwd bent met het gebruiken van grote CMS als AEM, overweeg het herzien van [Basisbehandeling](/help/sites-cloud/authoring/getting-started/basic-handling.md) documentatie alvorens te werk te gaan. De documentatie voor basisverwerking maakt geen deel uit van de reis. Ga daarom na voltooiing terug naar deze pagina.

### Opties {#tools}

* Sandbox-toegang voor het testen van het vertalen van uw inhoud
* Credentials om verbinding te maken met uw voorkeursvertaalservice
* Lid zijn van de `project-administrators` groep in AEM

## Structuur is sleutel {#content-structure}

AEM inhoud, of het nu kranteloze of traditionele webpagina&#39;s zijn, wordt aangedreven door de structuur ervan. AEM stelt weinig vereisten aan de inhoudsstructuur op, maar een zorgvuldige afweging van uw inhoudshiërarchie als onderdeel van de projectplanning kan de lokalisatie veel eenvoudiger maken.

>[!TIP]
>
>Plan voor vertaling en localisatie bij het allereerste begin van het hoofdloze project. Werk vroeg nauw samen met de projectmanager en de inhoudarchitecten.
>
>Een &quot;projectmanager voor internationalisering&quot; kan worden verlangd als een aparte persoon die tot taak heeft te bepalen welke inhoud moet worden vertaald en wat niet, en welke vertaalde inhoud door regionale of lokale inhoudproducenten kan worden gewijzigd.

Maak een plan voor de lokalisatie van de inhoud die u nodig hebt.

* Hebt u alleen maar verschillende talen of ook taal nodig om zich aan te passen aan regionale bijzonderheden?
* Hebt u rijke media-inhoud zoals afbeeldingen of video&#39;s nodig om voor verschillende landinstellingen te kunnen verschillen?

## Hoe AEM inhoud zonder kop opslaat {#headless-content-in-aem}

Voor de lokalisatiespecialist is het niet belangrijk om diepgaand te begrijpen hoe AEM inhoud zonder kop beheert. Het is echter heel handig om de basisbeginselen en -terminologie te kennen, aangezien u later AEM lokalisatieprogramma&#39;s gebruikt. Het belangrijkste is dat u uw eigen inhoud begrijpt en hoe deze is gestructureerd om deze effectief te kunnen lokaliseren.

### Inhoudsmodellen {#content-models}

Om ervoor te zorgen dat inhoud zonder kop consistent wordt geleverd tussen kanalen, regio&#39;s en talen, moet de inhoud zeer gestructureerd zijn. AEM gebruikt Content Models om deze structuur af te dwingen. U kunt Content Models zien als een soort sjabloon of patroon voor het maken van inhoud zonder kop. Omdat elk project zijn eigen behoeften heeft, bepaalt elk project zijn eigen Modellen van het Fragment van de Inhoud. AEM heeft geen vaste eisen of structuur voor dergelijke modellen.

De inhoudarchitect werkt in een vroeg stadium van het project om deze structuur te definiëren. Zoals eerder aanbevolen, dient u als lokalisatiespecialist nauw samen te werken met de inhoudarchitect om de inhoud te begrijpen en te ordenen.

Omdat de inhoudsmodellen de structuur van uw inhoud bepalen, zult u moeten weten welke gebieden van uw modellen moeten worden vertaald. In het algemeen werkt u met de inhoudarchitect om dit te definiëren. Volg onderstaande stappen om door de velden van uw inhoudsmodellen te bladeren.

1. Navigeer naar **Tools** -> **Assets** -> **Content Fragment Models**.
1. Modellen van inhoudsfragmenten worden over het algemeen opgeslagen in een mapstructuur. Tik of klik op de map voor uw project.
1. De modellen worden vermeld. Tik of klik op het model om de details weer te geven.
   ![Modellen van contentfragmenten](assets/content-fragment-models.png)
1. De **Inhoudsfragmentmodeleditor** wordt geopend.
   1. De linkerkolom bevat de velden van het model. Deze kolom interesseert ons.
   1. De rechterkolom bevat de velden die aan het model kunnen worden toegevoegd. Deze kolom kunnen wij negeren.
      ![Inhoudsfragmentmodeleditor](assets/content-fragment-model-editor.png)
1. Tik of klik op een van de velden van het model. AEM worden het en de details van dat gebied getoond in de juiste kolom.
   ![Details van de Editor van het inhoudsfragmentmodel](assets/content-fragment-model-editor-detail.png)

Neem nota van het gebied **de Naam van het Bezit** voor alle gebieden die moeten worden vertaald. U hebt deze informatie nodig voor de volgende stap in de reis.

### Contentfragmenten {#content-fragments}

Inhoudsmodellen worden door de auteurs van de inhoud gebruikt om de inhoud zonder kop te maken. Inhoudsauteurs selecteren op welk model ze hun inhoud willen baseren en maken vervolgens Inhoudsfragmenten. Inhoudsfragmenten zijn exemplaren van de modellen en vertegenwoordigen feitelijke inhoud die zonder kop moet worden geleverd.

Als Content Models de patronen voor de inhoud zijn, is de inhoud van de fragmenten de werkelijke inhoud op basis van die patronen.

Inhoudsfragmenten worden als elementen in AEM beheerd als onderdeel van DAM (Digital Asset Management). Dit is belangrijk aangezien zij allen onder de weg `/content/dam` zullen worden gevestigd.

## Aanbevolen inhoudsstructuur {#recommended-structure}

Zoals eerder geadviseerd, werk met uw inhoudarchitect om de aangewezen inhoudsstructuur voor uw eigen project te bepalen. Het volgende is echter een bewezen, eenvoudige en intuïtieve structuur die heel effectief is.

Definieer een basismap voor uw project onder `/content/dam`.

```text
/content/dam/<your-project>
```

De taal waarin uw inhoud wordt geschreven wordt genoemd de taalwortel. In ons voorbeeld is het Engels en moet het onder dit pad liggen.

```text
/content/dam/<your-project>/en
```

Alle projectinhoud die eventueel moet worden gelokaliseerd, moet worden geplaatst onder de master taal.

```text
/content/dam/<your-project>/en/<your-project-content>
```

Localisaties moeten samen met de hoofdmap van de taal worden gemaakt als op hetzelfde niveau geplaatste mappen. Duits zou bijvoorbeeld het volgende pad hebben.

```text
/content/dam/<your-project>/de
```

De uiteindelijke structuur kan er ongeveer als volgt uitzien.

```text
/content
    |- dam
        |- your-project
            |- en
                |- some
                |- exciting
                |- headless
                |- content
            |- de
            |- fr
            |- it
            |- ...
        |- another-project
        |- ...
```

## AEM lokalisatieprogramma&#39;s {#localization-tools}

Nu u begrijpt wat Content Fragments zijn en hoe belangrijk de inhoudsstructuur is, kunnen we bekijken hoe u deze inhoud kunt lokaliseren. De lokalisatieprogramma&#39;s in AEM zijn tamelijk krachtig, maar eenvoudig te begrijpen op een hoog niveau.

* **Vertaalaansluiting**  - De aansluiting is de koppeling tussen AEM en de vertaalservice die u gebruikt.
* **Vertaalregels**  - Regels bepalen welke inhoud onder bepaalde paden moet worden vertaald.
* **Vertaalprojecten**  - Vertaalprojecten bevatten inhoud die als één enkele vertaalinspanning zou moeten worden behandeld en de vooruitgang van de vertaling volgen, die met de schakelaar in aanraking komt om de te vertalen inhoud over te brengen en het terug van de vertaaldienst te ontvangen.

Over het algemeen hoeft u uw connector slechts eenmaal in te stellen voor uw instantie en regels per project zonder kop. Vervolgens gebruikt u vertaalprojecten om uw inhoud te lokaliseren en de vertalingen voortdurend bij te werken.

## Volgende functies {#what-is-next}

Nu u dit gedeelte van de reis zonder kop hebt voltooid, moet u:

* Begrijp het belang van inhoudsstructuur voor localisatie.
* Begrijp hoe AEM inhoud zonder kop opslaat.
* Wees vertrouwd met AEM lokalisatieprogramma&#39;s.

Voortbouwen op deze kennis en doorgaan met uw AEM tocht naar een hoofdloze lokalisatie door het document [Configureer de vertaalconnector](configure-connector.md) waar u leert hoe u AEM kunt verbinden met een vertaalservice.|

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u op het volgende deel van de hoofdloze lokalisatietraject door het document [te herzien de vertaalschakelaar ](configure-connector.md) vormt zijn het volgende enkele extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document worden vermeld, maar zij worden vereist niet om op de headless reis voort te zetten.

* [AEM Basic Handling](/help/sites-cloud/authoring/getting-started/basic-handling.md)  - Leer de grondbeginselen van de AEM UI om comfortabel te kunnen navigeren en essentiële taken uit te voeren zoals het vinden van uw inhoud.
* [Inhoud identificeren voor vertaling](/help/sites-cloud/administering/translation/rules.md)  - Leer hoe vertaalregels inhoud identificeren die moet worden vertaald.
* [Het Vormen van het Kader](/help/sites-cloud/administering/translation/integration-framework.md)  van de Integratie van de Vertaling - leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met de diensten van de derdevertaling te integreren.
* [Vertaalprojecten](/help/sites-cloud/administering/translation/managing-projects.md)  beheren - Leer hoe u zowel machine- als menselijke vertaalprojecten in AEM kunt maken en beheren.
