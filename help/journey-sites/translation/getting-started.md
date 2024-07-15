---
title: Aan de slag met AEM Sites-vertaling
description: Leer hoe u uw AEM Sites-inhoud kunt ordenen en hoe AEM vertaalhulpmiddelen werken.
index: true
hide: false
hidefromtoc: false
exl-id: 9bfc3995-ac8e-488e-b68f-9e1b5b4a3176
solution: Experience Manager Sites
feature: Translation
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 0%

---

# Aan de slag met AEM Sites Translation {#getting-started}

Leer hoe u uw AEM Sites-inhoud kunt ordenen en hoe AEM vertaalhulpmiddelen werken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de de vertaalreis van AEM Sites, [ Leer over de inhoud van AEM Sites en hoe te in AEM ](learn-about.md) te vertalen u de basistheorie van AEM Sites leerde en u zou nu moeten:

* Begrijp de basisbeginselen van het maken van AEM Sites-inhoud.
* Zorg dat u weet hoe AEM vertaling ondersteunt.

Dit artikel bouwt verder op die grondbeginselen zodat u begrijpt hoe AEM inhoud opslaat en beheert en hoe u AEM vertaalhulpmiddelen kunt gebruiken om die inhoud te vertalen.

## Doelstelling {#objective}

Met dit document kunt u begrijpen hoe u de inhoud van sites in AEM kunt gaan vertalen. Na het lezen moet u:

* Begrijp het belang van inhoudsstructuur voor vertaling.
* Begrijp hoe AEM inhoud opslaat.
* Wees vertrouwd met AEM vertaalhulpmiddelen.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verschillende vereisten voordat u begint met het vertalen van AEM inhoud.

### Kennis {#knowledge}

* Ervaar het vertalen van inhoud in een CMS
* Ervaar het gebruiken van de basiseigenschappen van grootschalig CMS
* Werken met AEM basisverwerking
* Kennis van de vertaalservice die u gebruikt
* Basiskennis hebben van de inhoud die u wilt vertalen

>[!TIP]
>
>Als u niet vertrouwd bent met het gebruiken van grote CMS als AEM, overweeg het herzien van de [ Basis Behandelende ](/help/sites-cloud/authoring/basic-handling.md) documentatie alvorens te werk te gaan. De documentatie van de Basisbehandeling maakt geen deel uit van de reis. Ga daarom terug naar deze pagina wanneer u klaar bent.

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van het vertalen van uw inhoud
* Credentials om verbinding te maken met uw voorkeursvertaalservice
* Lid zijn van de `project-administrators` -groep in AEM

## Inhoud AEM opslaan {#content-in-aem}

Voor de vertaalspecialist is het niet belangrijk om diepgaand te begrijpen hoe AEM inhoud beheert. Het is echter nuttig bekend te zijn met de basisbeginselen en -terminologie, aangezien u later AEM vertaalhulpmiddelen gebruikt. Het belangrijkste is dat u uw eigen inhoud begrijpt en hoe deze gestructureerd is om deze effectief te vertalen.

### Sites-console {#sites-console}

De siteconsole biedt een overzicht van de structuur van uw inhoud waardoor u eenvoudig door uw inhoud kunt navigeren en deze kunt beheren door nieuwe pagina&#39;s te maken, pagina&#39;s te verplaatsen en te kopiëren en inhoud te publiceren.

Toegang tot de siteconsole:

1. In het globale navigatiemenu, uitgezochte **Navigatie** > **Plaatsen**.
1. De siteconsole wordt geopend op het hoogste niveau van uw inhoud.
1. Zorg ervoor dat de **Mening van de Kolom** gebruikend de meningsselecteur bij het top-right van het venster wordt geselecteerd.

   ![ Selecterend kolommening ](assets/selecting-column-view.png)

1. Als u op een item in een kolom tikt of erop klikt, wordt de onderliggende inhoud weergegeven in de hiërarchie in de kolom rechts.

   ![ de hiërarchie van de Inhoud ](assets/sites-console-hierarchy.png)

1. Door op het selectievakje van een item in een kolom te tikken of erop te klikken, wordt dat item geselecteerd en worden de details van het geselecteerde item in de kolom rechts weergegeven, zodat verschillende beschikbare acties voor het geselecteerde item op de bovenstaande werkbalk zichtbaar worden.

   ![ selectie van de Inhoud ](assets/sites-console-selection.png)

1. Door op de spoorselecteur bij hoogste linkerzijde te tikken of te klikken, kunt u de **mening van de Boom van de Inhoud** voor een boomstructuuroverzicht van uw inhoud ook tonen.

   ![ de boommening van de Inhoud ](assets/sites-console-content-tree.png)

Met deze eenvoudige gereedschappen kunt u op intuïtieve wijze door de inhoudsstructuur navigeren.

>[!NOTE]
>
>De inhoudarchitect definieert doorgaans de inhoudsstructuur terwijl de inhoudsauteurs de inhoud binnen die structuur maken.
>
>Als vertaalspecialist is het belangrijk om eenvoudig te begrijpen hoe te om die structuur te navigeren en te begrijpen waar de inhoud wordt gevestigd.

### Pagina-editor {#page-editor}

Met de siteconsole kunt u door de inhoud navigeren en krijgt u een overzicht van de structuur. Als u de details van een afzonderlijke pagina wilt zien, moet u de site-editor gebruiken.

Een pagina bewerken:

1. Gebruik de siteconsole om een pagina te zoeken en te selecteren. U moet het selectievakje van een afzonderlijke pagina inschakelen om deze te selecteren.

   ![ Selecterend een pagina om uit te geven ](assets/sites-editor-select-page.png)

1. Selecteer **uitgeven** optie in de toolbar.
1. De site-editor wordt geopend en de geselecteerde pagina wordt geladen voor bewerking in een nieuw browsertabblad.
1. Wanneer u de muis over inhoud beweegt of hierop tikt, worden kiezers voor afzonderlijke componenten weergegeven. Componenten zijn de bouwstenen voor slepen en neerzetten die de pagina vormen.

   ![ Uitgevend een pagina ](assets/sites-editor-title.png)

U kunt naar de plaatsenconsole terugkeren door terug naar dat lusje in uw browser op elk ogenblik te schakelen. Met de site-editor kunt u de inhoud van de pagina snel weergeven als de auteurs van de inhoud en uw publiek deze kunnen zien.

>[!NOTE]
>
>De auteurs van de inhoud maken uw site-inhoud met de siteeditor.
>
>Als vertaalspecialist is het belangrijk om eenvoudig te begrijpen hoe te om de details van die inhoud te bekijken gebruikend de plaatshedacteur.

## Structuur is sleutel {#content-structure}

AEM inhoud wordt aangestuurd door de structuur. AEM stelt weinig vereisten aan de inhoudsstructuur op, maar een zorgvuldige overweging van uw inhoudshiërarchie als onderdeel van de projectplanning kan vertaling veel eenvoudiger maken.

>[!TIP]
>
>Plan voor vertaling bij het allereerste begin van uw AEM project. Werk vroeg nauw samen met de projectmanager en de inhoudarchitecten.
>
>Een projectmanager voor internationalisatie kan worden verlangd als een aparte persoon die tot taak heeft te bepalen welke inhoud moet worden vertaald en wat niet, en welke vertaalde inhoud door regionale of lokale inhoudproducenten kan worden gewijzigd.

## Aanbevolen inhoudsstructuur {#recommended-structure}

Zoals eerder geadviseerd, werk met uw inhoudarchitect om de aangewezen inhoudsstructuur voor uw eigen project te bepalen. Het volgende is echter een bewezen, eenvoudige en intuïtieve structuur die heel effectief is.

Definieer een basismap voor uw project onder `/content` .

```text
/content/<your-project>
```

De taal waarin uw inhoud wordt geschreven wordt genoemd de taalwortel. In ons voorbeeld is het Engels en moet het onder dit pad liggen.

```text
/content/<your-project>/en
```

Alle projectinhoud die mogelijk moet worden gelokaliseerd, moet onder de hoofdmap van de taal worden geplaatst.

```text
/content/<your-project>/en/<your-project-content>
```

De vertalingen zouden als sibling omslagen naast de taalwortel met hun omslagnaam moeten worden gecreeerd die ISO-2 taalcode van de taal vertegenwoordigt. Duits zou bijvoorbeeld het volgende pad hebben.

```text
/content/<your-project>/de
```

>[!NOTE]
>
>Over het algemeen is de inhoudsarchitect verantwoordelijk voor het maken van deze taalmappen. Als ze niet worden gecreëerd, kunnen AEM later geen vertaalbanen creëren.

De uiteindelijke structuur kan er ongeveer als volgt uitzien.

```text
/content
    |- your-project
        |- en
            |- some
            |- exciting
            |- sites
            |- content
        |- de
        |- fr
        |- it
        |- ...
    |- another-project
    |- ...
```

Let op het specifieke pad van uw inhoud, omdat dit later nodig is om uw vertaling te configureren.

>[!NOTE]
>
>Het is in het algemeen de verantwoordelijkheid van de inhoudarchitect om de inhoudstructuur te definiëren, vaak in samenwerking met de vertaalspecialist.
>
>Het wordt hier nader toegelicht om de volledigheid te waarborgen.

## AEM vertaalgereedschappen {#translation-tools}

Nu u de de plaatsenconsole en redacteur en het belang van inhoudsstructuur begrijpt, kunnen wij bekijken hoe te om inhoud te vertalen. De vertaalhulpmiddelen in AEM zijn vrij krachtig, maar eenvoudig te begrijpen op hoog niveau.

* **Schakelaar van de Vertaling** - de schakelaar is het verband tussen AEM en de vertaaldienst die u gebruikt.
* **de Regels van de Vertaling** - bepaalt welke inhoud onder bijzondere wegen zou moeten worden vertaald.
* **de Projecten van de Vertaling** - De vertaalprojecten verzamelen inhoud die als één enkele vertaalinspanning zou moeten worden gericht en de vooruitgang van de vertaling volgen, die met de schakelaar omzet om de te vertalen inhoud over te brengen en het terug van de vertaaldienst te ontvangen.

U plaatst over het algemeen slechts eens uw schakelaar voor uw instantie en regels per project. Vervolgens gebruikt u vertaalprojecten om uw inhoud te vertalen en de vertalingen voortdurend bij te werken.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Sites-vertaalreis hebt voltooid, moet u:

* Begrijp het belang van inhoudsstructuur voor vertaling.
* Begrijp hoe AEM inhoud opslaat.
* Wees vertrouwd met AEM vertaalhulpmiddelen.

Bouw op deze kennis voort en ga uw de vertaalreis van AEM Sites door het document [ opnieuw te bekijken vormt de vertaalschakelaar ](configure-connector.md) waar u leert hoe te om AEM met de vertaaldienst te verbinden.|

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van de vertaalreis door het document [ te herzien de vertaalschakelaar ](configure-connector.md) beweegt is het volgende wat extra, facultatieve middelen die een diepere duik op sommige die concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de reis verder te gaan.

* [ AEM Basisbehandeling ](/help/sites-cloud/authoring/basic-handling.md) - leer de grondbeginselen van AEM UI om essentiële taken gemakkelijk te kunnen navigeren en uitvoeren zoals het vinden van uw inhoud.
* [ identificerend Inhoud om ](/help/sites-cloud/administering/translation/rules.md) te vertalen - leer hoe de vertaalregels inhoud identificeren die moet vertalen.
* [ Vormend het Kader van de Integratie van de Vertaling ](/help/sites-cloud/administering/translation/integration-framework.md) - leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met de diensten van de derdevertaling te integreren.
* [ het Leiden de Projecten van de Vertaling ](/help/sites-cloud/administering/translation/managing-projects.md) - leer hoe te om zowel machine als menselijke vertaalprojecten in AEM tot stand te brengen en te leiden.
