---
title: Koploze inhoud omzetten
description: Gebruik de vertaalaansluiting om uw inhoud zonder kop te vertalen.
exl-id: 3bfbf186-d684-4742-8c5c-34c34ff3adb5
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 0%

---


# Koploze inhoud omzetten {#translate-content}

Met de vertaalintegratie kunt u uw inhoud zonder kop vertalen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze vertaalreis, [ vorm de Schakelaar van de Vertaling ](configure-connector.md) u over het vertaalkader in AEM leerde. Nu moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Nu de connector is ingesteld, gaat u met dit artikel door de volgende stap voor het vertalen van inhoud zonder kop.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om AEM vertaalprojecten samen met de schakelaar te gebruiken om inhoud te vertalen. Nadat u dit document hebt gelezen, moet u:

* Begrijp wat een vertaalproject is.
* U kunt nieuwe vertaalprojecten maken.
* Gebruik vertaalprojecten om uw inhoud zonder kop te vertalen.

## Een vertaalproject maken {#creating-translation-project}

Met vertaalprojecten kunt u de vertaling van inhoud zonder kop AEM. In een vertaalproject wordt de inhoud verzameld die op één locatie in andere talen moet worden vertaald voor een centrale weergave van de vertaalwerkzaamheden.

Wanneer inhoud aan een vertaalproject wordt toegevoegd, wordt een vertaalbaan gecreeerd voor het. Taken bieden opdrachten en statusinformatie die u gebruikt om de workflows voor het vertalen van mensen en computers die op de bronnen worden uitgevoerd, te beheren.

Vertaalprojecten kunnen op twee manieren worden gemaakt:

1. Selecteer de taalwortel van de inhoud en hebben AEM automatisch tot het vertaalproject leiden dat op de inhoudspad wordt gebaseerd.
1. Maak een leeg project en selecteer handmatig de inhoud die u aan het vertaalproject wilt toevoegen

Beide zijn geldige benaderingen die doorgaans alleen verschillen op basis van de persoon die de vertaling uitvoert:

* De TPM (vertaalprojectmanager) heeft vaak de flexibiliteit nodig om de inhoud handmatig te selecteren voor het vertaalproject.
* Als de eigenaar van de inhoud ook verantwoordelijk is voor de vertaling, is het vaak gemakkelijker AEM het project automatisch te maken op basis van het geselecteerde inhoudspad.

Beide benaderingen worden in de volgende secties verkend.

### Automatisch een vertaalproject maken op basis van het inhoudspad {#automatically-creating}

Voor eigenaars van inhoud die ook verantwoordelijk zijn voor vertaling, is het vaak gemakkelijker om het vertaalproject automatisch AEM maken. AEM automatisch een vertaalproject maken op basis van het inhoudspad:

1. Navigeer aan **Navigatie** > **Assets** > **Dossiers**. Onthoud dat inhoud zonder kop in AEM wordt opgeslagen als elementen die Content Fragments worden genoemd.
1. Selecteer de taalwortel van uw project. In dit geval hebben we `/content/dam/wknd/en` geselecteerd.
1. Selecteer de spoorselecteur en toon het **paneel van Verwijzingen**.
1. Selecteer **Exemplaren van de Taal**.
1. Controleer het **checkbox van de Kopieën van de Taal 0&rbrace;.**
1. Breid de sectie **Exemplaren van de Taal van de Update** bij de bodem van het verwijzingenpaneel uit.
1. In de **drop-down lijst van het Project**, uitgezocht **creeer Vertaal Project(en)**.
1. Geef een geschikte titel op voor uw vertaalproject.
1. Selecteer **Begin**.

![ creeer een vertaalproject ](assets/create-translation-project.png)

U ontvangt een bericht dat het project werd gecreeerd.

>[!NOTE]
>
>Men veronderstelt dat de noodzakelijke taalstructuur voor de vertalingen talen reeds als deel van de [ definitie van uw inhoudsstructuur ](getting-started.md#content-structure) is gecreeerd. Dit moet gebeuren in samenwerking met de inhoudarchitect.
>
>Als de taalmappen niet van tevoren worden gemaakt, kunt u geen taalkopieën maken zoals beschreven in de vorige stappen.

### Handmatig een vertaalproject maken door uw inhoud te selecteren {#manually-creating}

Voor managers van vertaalprojecten, is het vaak noodzakelijk om specifieke inhoud manueel te selecteren om in een vertaalproject te omvatten. Als u een dergelijk handmatig vertaalproject wilt maken, moet u eerst een leeg project maken en vervolgens de inhoud selecteren die u aan het project wilt toevoegen.

1. Navigeer aan **Navigatie** > **Projecten**.
1. Selecteer **creeer** > **Omslag** om een omslag voor uw projecten tot stand te brengen.
   * Dit is optioneel, maar handig om uw vertaalwerkzaamheden te organiseren.
1. In **creeer het venster van het Project**, voeg a **Titel** voor de omslag toe en selecteer dan **creeer**.

   ![ creeer projectomslag ](assets/create-project-folder.png)

1. Selecteer de map om de map te openen.
1. In uw nieuwe projectomslag, creeer **&#x200B;**&#x200B;> **Project**.
1. Projecten zijn gebaseerd op sjablonen. Selecteer het **malplaatje van het Project van de Vertaling** om het te selecteren en dan **daarna** te selecteren.

   ![ Uitgezochte malplaatje van het vertaalproject ](assets/select-translation-project-template.png)

1. Op het **Basis** lusje, ga een naam voor uw nieuw project in.

   ![ Basis tabel van het Project ](assets/project-basic-tab.png)

1. Op het **Geavanceerde** lusje, gebruik de **drop-down Taal van het Doel** om de talen te selecteren waarin uw inhoud zou moeten worden vertaald. Selecteer **creeer**.

   ![ Project geavanceerd lusje ](assets/project-advanced-tab.png)

1. Selecteer **Open** in de bevestigingsdialoog.

   ![ de bevestigingsdialoog van het Project ](assets/project-confirmation-dialog.png)

Het project is gemaakt, maar bevat geen inhoud om te vertalen. In de volgende sectie wordt beschreven hoe het project is gestructureerd en hoe u inhoud kunt toevoegen.

## Een vertaalproject gebruiken {#using-translation-project}

Vertaalprojecten zijn ontworpen om de inhoud en taken in verband met een vertaalinspanning op één plaats te verzamelen om uw vertaling eenvoudig en eenvoudig te beheren.

Het vertaalproject weergeven:

1. Navigeer aan **Navigatie** > **Projecten**.
1. Selecteer het project dat in de vorige sectie is gemaakt.

![ Vertaal project ](assets/translation-project.png)

Het project is verdeeld in meerdere kaarten.

* **Samenvatting** - Deze kaart toont de basiskopbalinformatie van het project met inbegrip van de eigenaar, de taal, en de vertaalleverancier.
* **VertaalBaan** - Deze kaart of deze kaarten tonen (tonen) een overzicht van de daadwerkelijke vertaalbaan met inbegrip van de status, het aantal activa, etc. Over het algemeen is er één taak per taal, waarbij de ISO-2-taalcode aan de taaknaam wordt toegevoegd.
* **Team** - Deze kaart toont de gebruikers die aan dit vertaalproject samenwerken. Deze reis gaat niet over dit onderwerp.
* **Taken** - de Extra taken verbonden aan het vertalen van de inhoud zoals om punten of werkschemapunten te doen. Deze reis gaat niet over dit onderwerp.

Hoe u een vertaalproject gebruikt, hangt af van de manier waarop het is gemaakt: automatisch door AEM of handmatig.

### Een automatisch gemaakt vertaalproject gebruiken {#using-automatic-project}

Wanneer u het vertaalproject automatisch maakt, beoordeelt AEM de inhoud zonder kop onder het pad dat u hebt geselecteerd. Op basis van die evaluatie extraheert het de inhoud die vertaald moet worden naar een nieuw vertaalproject. Ik weet welke gebieden die op de gebieden worden gebaseerd die als **Vertaalbaar** door de inhoudarchitect worden gemarkeerd te vertalen.

U kunt als volgt de details van de inhoud zonder kop in dit project bekijken:

1. Selecteer de ellipsis knoop bij de bodem van de **kaart van de Taak van de Vertaling**.
1. Het **venster van de Baan van de Vertaling** maakt een lijst van alle punten in de baan.
   ![ het detail van de Baan van de Vertaling ](assets/translation-job-detail.png)
1. Selecteer een regel om de details van die regel weer te geven. Houd er rekening mee dat één regel meerdere inhoudsitems kan vertegenwoordigen om te vertalen.
1. Schakel het selectievakje voor een regelitem in om andere opties weer te geven, zoals de optie om het item uit de taak te verwijderen of om het item weer te geven in de inhoudsfragmenten of in de Assets-consoles.

![ de opties van de Taak van de Vertaling ](assets/translation-job-options.png)

Typisch begint de inhoud voor de vertaalbaan in de **staat van het Ontwerp** zoals die door de **wordt vermeld 3&rbrace; kolom van de Staat &lbrace;in het** venster van de Baan van de Vertaling **.**

Om de vertaalbaan te beginnen, ga aan het overzicht van het vertaalproject terug en selecteer de kantorknoop bij de bovenkant van de **kaart van de VertaalBaan** en selecteer **Begin**.

![ de vertaalbaan van het Begin ](assets/start-translation-job.png)

AEM communiceert nu met uw vertaalconfiguratie en -connector om de inhoud naar de vertaalservice te verzenden. U kunt de vooruitgang van de vertaling bekijken door aan het **venster van de VertaalBaan** terug te keren en de **3&rbrace; kolom van de Staat &lbrace;van de ingangen te bekijken.**

![ Goedgekeurde Taak van de Vertaling ](assets/translation-job-approved.png)

De vertalingen van de machine keren automatisch met een staat van **Goedgekeurd** terug. Menselijke vertaling maakt meer interactie mogelijk, maar valt buiten het bereik van deze reis.

### Een handmatig gemaakt vertaalproject gebruiken {#using-manual-project}

Als u handmatig een vertaalproject maakt, AEM de benodigde taken, maar selecteert u niet automatisch de inhoud die u wilt opnemen. Hierdoor kan de projectbeheerder van de vertaling kiezen welke inhoud moet worden vertaald.

Inhoud toevoegen aan een vertaaltaak:

1. Selecteer de ellipsknoop bij de bodem van één van de **kaarten van de Taak van de Vertaling**.
1. Controleer of de taak geen inhoud bevat. Selecteer **toevoegen** knoop bij bovenkant van het venster en dan **Assets/Pagina&#39;s** van drop-down.

   ![ Lege vertaalbaan ](assets/empty-translation-job.png)

1. Er wordt een padbrowser geopend waarin u specifiek kunt selecteren welke inhoud u wilt toevoegen. Zoek de inhoud en selecteer deze.

   ![ browser van de Weg ](assets/path-browser.png)

1. Selecteer **Uitgezocht** om de geselecteerde inhoud aan de baan toe te voegen.
1. In de **Vertaal** dialoog, specificeer dat u **het Exemplaar van de Taal** wilt creëren.

   ![ creeer taalexemplaar ](assets/translate-copy-master.png)

1. De inhoud wordt nu opgenomen in de taak.

   ![ Inhoud die aan vertaalbaan ](assets/content-added.png) wordt toegevoegd

1. Schakel het selectievakje voor een regelitem in om andere opties weer te geven, zoals de optie om het item uit de taak te verwijderen of om het item weer te geven in de inhoudsfragmenten of in de Assets-consoles.

![ de opties van de Taak van de Vertaling ](assets/translation-job-options.png)

1. Herhaal deze stappen om alle vereiste inhoud in de taak op te nemen.

>[!TIP]
>
>De padbrowser is een krachtig hulpmiddel waarmee u uw inhoud kunt zoeken, filteren en doorbladeren. Selecteer de **Inhoud slechts/Filters** knoop om het zijpaneel van een knevel te voorzien en geavanceerde filters zoals **Gewijzigde Datum** of **Vertaalstatus** te tonen.
>
>U kunt meer over wegbrowser in de [ extra middelensectie ](#additional-resources) leren.

U kunt de voorafgaande stappen gebruiken om de noodzakelijke inhoud aan alle talen (banen) voor het project toe te voegen. Nadat u alle inhoud hebt geselecteerd, kunt u de vertaling starten.

Typisch begint de inhoud voor de vertaalbaan in de **staat van het Ontwerp** zoals die door de **wordt vermeld 3&rbrace; kolom van de Staat &lbrace;in het** venster van de Baan van de Vertaling **.**

Om de vertaalbaan te beginnen, ga aan het overzicht van het vertaalproject terug en selecteer de kantorknoop bij de bovenkant van de **kaart van de VertaalBaan** en selecteer **Begin**.

![ de vertaalbaan van het Begin ](assets/start-translation-job.png)

AEM communiceert nu met uw vertaalconfiguratie en -connector om de inhoud naar de vertaalservice te verzenden. U kunt de vooruitgang van de vertaling bekijken door aan het **venster van de VertaalBaan** terug te keren en de **3&rbrace; kolom van de Staat &lbrace;van de ingangen te bekijken.**

![ Goedgekeurde Taak van de Vertaling ](assets/translation-job-approved.png)

De vertalingen van de machine keren automatisch met een staat van **Goedgekeurd** terug. Menselijke vertaling maakt meer interactie mogelijk, maar valt buiten het bereik van deze reis.

## Vertaalde inhoud controleren {#reviewing}

[ zoals eerder gezien ](#using-translation-project), de machine vertaalde inhoud vloeit terug in AEM met het statuut van **Goedgekeurd** aangezien de veronderstelling is dat omdat de machinevertaling wordt gebruikt, geen menselijke interventie wordt vereist. Het is echter nog steeds mogelijk om de vertaalde inhoud te beoordelen.

Ga eenvoudig naar de voltooide vertaalbaan en selecteer een lijnpunt door te tikken of checkbox te klikken. Het pictogram **openbaart in het Fragment van de Inhoud** wordt getoond in de hulpmiddelbar.

![ onthullen in inhoudsfragment ](assets/reveal-in-content-fragment.png)

Selecteer dat pictogram om het vertaalde inhoudsfragment in zijn redacteursconsole te openen om de details van de vertaalde inhoud te zien.

![ A vertaald inhoudsfragment ](assets/translated-content-fragment.png)

U kunt het inhoudsfragment desgewenst verder wijzigen, op voorwaarde dat u de juiste machtigingen hebt, maar dat het bewerken van inhoudsfragmenten buiten het bereik van deze rit valt. Zie de [ Extra sectie van Middelen ](#additional-resources) aan het eind van dit document voor meer informatie over dit onderwerp.

Het doel van het project is om alle middelen in verband met een vertaling op één plaats te verzamelen, zodat u gemakkelijk toegang hebt en een duidelijk overzicht krijgt. Zoals u echter kunt zien door de details van een vertaald item weer te geven, vloeien de vertalingen zelf terug naar de map met middelen van de vertaaltaal. In dit voorbeeld is de map

```text
/content/dam/wknd/es
```

Als u aan deze omslag als **Navigatie** > **Dossiers** > **Assets** navigeert, ziet u de vertaalde inhoud.

![ Vertaalde structuur van de inhoudsomslag ](assets/translated-file-content.png)

AEM vertaalkader ontvangt de vertalingen van de vertaalschakelaar en leidt dan automatisch tot de inhoudsstructuur die op de taalwortel wordt gebaseerd en gebruikend de vertalingen die door de schakelaar worden verstrekt.

Het is belangrijk om te begrijpen dat deze inhoud niet wordt gepubliceerd en daarom niet beschikbaar voor uw headless diensten. U leert over deze auteur-publicatiestructuur en ziet hoe u vertaalde inhoud kunt publiceren in de volgende stap van de vertaalreis.

## Menselijke vertaling {#human-translation}

Als uw vertaalservice voorziet in menselijke vertaling, biedt het revisieproces meer opties. Bijvoorbeeld, komen de vertalingen terug in het project met het status **Ontwerp** aan en moeten worden herzien en manueel worden goedgekeurd of verworpen.

Menselijke vertaling valt buiten het bereik van deze lokalisatietraject. Zie de [ Extra sectie van Middelen ](#additional-resources) aan het eind van dit document voor meer informatie over dit onderwerp. Naast de aanvullende goedkeuringsopties is het werkschema voor menselijke vertalingen echter hetzelfde als voor machinevertalingen die in deze reis worden beschreven.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp wat een vertaalproject is.
* U kunt nieuwe vertaalprojecten maken.
* Gebruik vertaalprojecten om uw inhoud zonder kop te vertalen.

Bouw op deze kennis voort en zet uw AEM hoofdloze vertaalreis door het document [ te herzien Publish vertaalde inhoud ](publish-content.md) waar u leert hoe te om uw vertaalde inhoud te publiceren en hoe te om die vertalingen bij te werken aangezien uw inhoud van de taalwortel verandert.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de hoofdloze vertaalreis door het document [ Publish vertaalde inhoud ](publish-content.md) te herzien beweegt, zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document worden vermeld doen, maar zij worden niet vereist om op de headless reis verder te gaan.

* [ het Leiden de Projecten van de Vertaling ](/help/sites-cloud/administering/translation/managing-projects.md) - leer de details van vertaalprojecten en extra eigenschappen zoals menselijke vertaalwerkschema&#39;s en meertalige projecten.
* [ Authoring Milieu en Hulpmiddelen ](/help/sites-cloud/authoring/path-selection.md#path-selection) - AEM verstrekt diverse mechanismen om uw inhoud met inbegrip van robuuste wegbrowser te organiseren en uit te geven.
