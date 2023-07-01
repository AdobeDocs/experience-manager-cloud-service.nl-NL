---
title: Koploze inhoud omzetten
description: Gebruik de vertaalaansluiting om uw inhoud zonder kop te vertalen.
exl-id: 3bfbf186-d684-4742-8c5c-34c34ff3adb5
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '2175'
ht-degree: 0%

---


# Koploze inhoud omzetten {#translate-content}

Gebruik de vertaalaansluiting om uw inhoud zonder kop te vertalen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM zonder kop [Vertaalaansluiting configureren](configure-connector.md) u leerde over het vertaalkader in AEM. Nu moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Nu de connector is ingesteld, gaat u met dit artikel door de volgende stap voor het vertalen van inhoud zonder kop.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om AEM vertaalprojecten samen met de schakelaar te gebruiken om inhoud te vertalen. Nadat u dit document hebt gelezen, moet u:

* Begrijp wat een vertaalproject is.
* Nieuwe vertaalprojecten kunnen maken.
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

1. Navigeren naar **Navigatie** -> **Activa** -> **Bestanden**. Onthoud dat inhoud zonder kop in AEM wordt opgeslagen als elementen die Content Fragments worden genoemd.
1. Selecteer de taalwortel van uw project. In dit geval hebben we `/content/dam/wknd/en`.
1. Tik of klik op de railkiezer en toon de **Verwijzingen** deelvenster.
1. Tik of klik op **Taalkopieën**.
1. Controleer de **Taalkopieën** selectievakje.
1. De sectie uitvouwen **Taalkopieën bijwerken** onder aan het venster Verwijzingen.
1. In de **Project** vervolgkeuzelijst, selecteren **Vertaalproject(en) maken**.
1. Geef een geschikte titel op voor uw vertaalproject.
1. Tik of klik op **Start**.

![Een vertaalproject maken](assets/create-translation-project.png)

U ontvangt een bericht dat het project werd gecreeerd.

>[!NOTE]
>
>Er wordt aangenomen dat de noodzakelijke taalstructuur voor de vertalingstalen reeds is gecreëerd als onderdeel van de [definitie van de inhoudsstructuur.](getting-started.md#content-structure) Dit moet gebeuren in samenwerking met de inhoudarchitect.
>
>Als de taalmappen niet van tevoren worden gemaakt, kunt u geen taalkopieën maken zoals beschreven in de vorige stappen.

### Handmatig een vertaalproject maken door uw inhoud te selecteren {#manually-creating}

Voor managers van vertaalprojecten, is het vaak noodzakelijk om specifieke inhoud manueel te selecteren om in een vertaalproject te omvatten. Als u een dergelijk handmatig vertaalproject wilt maken, moet u eerst een leeg project maken en vervolgens de inhoud selecteren die u aan het project wilt toevoegen.

1. Navigeren naar **Navigatie** -> **Projecten**.
1. Tik of klik op **Maken** -> **Map** om een map voor uw projecten te maken.
   * Dit is optioneel, maar handig om uw vertaalwerkzaamheden te organiseren.
1. In de **Project maken** venster, een **Titel** voor de map en tik of klik op **Maken**.

   ![Projectmap maken](assets/create-project-folder.png)

1. Tik of klik op de map om de map te openen.
1. Tik of klik op **Maken** -> **Project**.
1. Projecten zijn gebaseerd op sjablonen. Tik of klik op de knop **Omzettingsproject** sjabloon om het te selecteren en vervolgens te tikken of te klikken **Volgende**.

   ![Sjabloon voor vertaalproject selecteren](assets/select-translation-project-template.png)

1. Op de **Basis** voert u een naam in voor uw nieuwe project.

   ![Tabblad Projectbasis](assets/project-basic-tab.png)

1. Op de **Geavanceerd** gebruiken **Doeltaal** vervolgkeuzelijst om de taal of talen te selecteren waarin de inhoud moet worden vertaald. Tik of klik op **Maken**.

   ![Tabblad Project geavanceerd](assets/project-advanced-tab.png)

1. Tik of klik op **Openen** in het bevestigingsdialoogvenster.

   ![Dialoogvenster Projectbevestiging](assets/project-confirmation-dialog.png)

Het project is gemaakt, maar bevat geen inhoud om te vertalen. In de volgende sectie wordt beschreven hoe het project is gestructureerd en hoe u inhoud kunt toevoegen.

## Een vertaalproject gebruiken {#using-translation-project}

Vertaalprojecten zijn ontworpen om alle inhoud en taken in verband met een vertaalinspanning op één plaats te verzamelen, zodat uw vertaling eenvoudig en eenvoudig te beheren is.

Het vertaalproject weergeven:

1. Navigeren naar **Navigatie** -> **Projecten**.
1. Tik of klik op het project dat in de vorige sectie is gemaakt.

![Vertaalproject](assets/translation-project.png)

Het project is verdeeld in meerdere kaarten.

* **Samenvatting** - Deze kaart bevat de basiskoptekstinformatie van het project, waaronder de eigenaar, de taal en de vertaalprovider.
* **Vertaaltaak** - Op deze kaart of op deze kaarten is (zijn) een overzicht te zien van de werkelijke vertaalbaan, met inbegrip van de status, het aantal activa, enz. Over het algemeen is er één taak per taal waarbij de ISO-2-taalcode aan de taaknaam wordt toegevoegd.
* **Team** - Deze kaart toont de gebruikers die aan dit vertaalproject samenwerken. Deze reis gaat niet over dit onderwerp.
* **Taken** - Aanvullende taken die samenhangen met het vertalen van de inhoud, zoals het uitvoeren van items of workflowitems. Deze reis gaat niet over dit onderwerp.

Hoe u een vertaalproject gebruikt, hangt af van de manier waarop het is gemaakt: automatisch door AEM of handmatig.

### Een automatisch gemaakt vertaalproject gebruiken {#using-automatic-project}

Wanneer u het vertaalproject automatisch maakt, beoordeelt AEM de inhoud zonder kop onder het pad dat u hebt geselecteerd. Op basis van die evaluatie extraheert het de inhoud die vertaald moet worden naar een nieuw vertaalproject. Ik weet welke velden moeten worden vertaald op basis van de velden die worden gemarkeerd als **Vertaalbaar** door de inhoudarchitect.

U kunt als volgt de details van de inhoud zonder kop in dit project bekijken:

1. Tik of klik op de knop voor de ovaal onder aan het dialoogvenster **Vertaaltaak** kaart.
1. De **Vertaaltaak** worden alle items in de taak weergegeven.
   ![Taakdetails voor vertaling](assets/translation-job-detail.png)
1. Tik of klik op een regel om de details van die regel weer te geven. Houd er rekening mee dat één regel meerdere inhoudsitems kan vertegenwoordigen die moeten worden vertaald.
1. Tik of klik op het selectiekader voor een regelitem om andere opties weer te geven, zoals de optie om het item uit de taak te verwijderen of in de consoles Inhoudsfragmenten of Elementen weer te geven.

![Opties voor vertaaltaken](assets/translation-job-options.png)

De inhoud van de vertaaltaak wordt meestal gestart in het dialoogvenster **Concept** staat zoals aangegeven door de **Staat** in de **Vertaaltaak** venster.

Als u de vertaaltaak wilt starten, gaat u terug naar het overzicht van het vertaalproject en tikt u op de knop chevron boven aan het dialoogvenster **Vertaaltaak** kaart en selecteer **Start**.

![Vertaaltaak starten](assets/start-translation-job.png)

AEM communiceert nu met uw vertaalconfiguratie en -connector om de inhoud naar de vertaalservice te verzenden. U kunt de voortgang van de vertaling bekijken door terug te keren naar de **Vertaaltaak** venster en de **Staat** kolom van de vermeldingen.

![Vertaaltaak goedgekeurd](assets/translation-job-approved.png)

De vertalingen van de machine keren automatisch met een staat van terug **Goedgekeurd**. Menselijke vertaling maakt meer interactie mogelijk, maar valt buiten het bereik van deze reis.

### Een handmatig gemaakt vertaalproject gebruiken {#using-manual-project}

Als u handmatig een vertaalproject maakt, AEM de benodigde taken, maar selecteert u niet automatisch de inhoud die u wilt opnemen. Hierdoor kan de projectbeheerder van de vertaling kiezen welke inhoud moet worden vertaald.

Inhoud toevoegen aan een vertaaltaak:

1. Tik of klik op de ovaalknop onder aan een van de **Vertaaltaak** kaarten.
1. Controleer of de taak geen inhoud bevat. Tik of klik op de knop **Toevoegen** boven aan het venster en vervolgens **Middelen/Pagina&#39;s** in de vervolgkeuzelijst.

   ![Lege vertaaltaak](assets/empty-translation-job.png)

1. Er wordt een padbrowser geopend waarin u specifiek kunt selecteren welke inhoud u wilt toevoegen. Zoek de inhoud en tik of klik om deze te selecteren.

   ![Padbrowser](assets/path-browser.png)

1. Tik of klik op **Selecteren** om de geselecteerde inhoud aan de baan toe te voegen.
1. In de **Vertalen** , geeft u aan dat u **Taalkopie maken**.

   ![Taalkopie maken](assets/translate-copy-master.png)

1. De inhoud wordt nu opgenomen in de taak.

   ![Inhoud toegevoegd aan vertaaltaak](assets/content-added.png)

1. Tik of klik op het selectiekader voor een regelitem om andere opties weer te geven, zoals de optie om het item uit de taak te verwijderen of in de consoles Inhoudsfragmenten of Elementen weer te geven.

![Opties voor vertaaltaken](assets/translation-job-options.png)

1. Herhaal deze stappen om alle vereiste inhoud in de taak op te nemen.

>[!TIP]
>
>De padbrowser is een krachtig hulpmiddel waarmee u uw inhoud kunt zoeken, filteren en doorbladeren. Tik of klik op de knop **Alleen inhoud/filters** om het zijpaneel in en uit te schakelen en geavanceerde filters zoals **Wijzigingsdatum** of **Vertaalstatus**.
>
>Meer informatie over de padbrowser vindt u in het dialoogvenster [sectie aanvullende bronnen.](#additional-resources)

U kunt de voorafgaande stappen gebruiken om de noodzakelijke inhoud aan alle talen (banen) voor het project toe te voegen. Nadat u alle inhoud hebt geselecteerd, kunt u de vertaling starten.

De inhoud van de vertaaltaak wordt meestal gestart in het dialoogvenster **Concept** staat zoals aangegeven door de **Staat** in de **Vertaaltaak** venster.

Als u de vertaaltaak wilt starten, gaat u terug naar het overzicht van het vertaalproject en tikt u op de knop chevron boven aan het dialoogvenster **Vertaaltaak** kaart en selecteer **Start**.

![Vertaaltaak starten](assets/start-translation-job.png)

AEM communiceert nu met uw vertaalconfiguratie en -connector om de inhoud naar de vertaalservice te verzenden. U kunt de voortgang van de vertaling bekijken door terug te keren naar de **Vertaaltaak** venster en de **Staat** kolom van de vermeldingen.

![Vertaaltaak goedgekeurd](assets/translation-job-approved.png)

De vertalingen van de machine keren automatisch met een staat van terug **Goedgekeurd**. Menselijke vertaling maakt meer interactie mogelijk, maar valt buiten het bereik van deze reis.

## Vertaalde inhoud controleren {#reviewing}

[Zoals eerder waargenomen,](#using-translation-project) door de computer vertaalde inhoud gaat terug naar AEM met de status **Goedgekeurd** aangezien ervan wordt uitgegaan dat er geen menselijk ingrijpen vereist is omdat er machinevertaling wordt gebruikt . Het is natuurlijk nog steeds mogelijk om de vertaalde inhoud te beoordelen.

Ga eenvoudig naar de voltooide vertaalbaan en selecteer een lijnpunt door te tikken of checkbox te klikken. Het pictogram **Tonen in inhoudsfragment** wordt weergegeven in de werkbalk.

![Tonen in inhoudsfragment](assets/reveal-in-content-fragment.png)

Tik of klik op dat pictogram om het vertaalde inhoudsfragment in de editorconsole te openen en de details van de vertaalde inhoud weer te geven.

![Een vertaald inhoudsfragment](assets/translated-content-fragment.png)

U kunt het inhoudsfragment desgewenst verder wijzigen, op voorwaarde dat u de juiste machtigingen hebt, maar dat het bewerken van inhoudsfragmenten buiten het bereik van deze rit valt. Zie de [Aanvullende bronnen](#additional-resources) voor meer informatie over dit onderwerp.

Het doel van het project is om alle middelen in verband met een vertaling op één plaats te verzamelen, zodat u gemakkelijk toegang hebt en een duidelijk overzicht krijgt. Zoals u echter kunt zien door de details van een vertaald item weer te geven, vloeien de vertalingen zelf terug naar de map met middelen van de vertaaltaal. In dit voorbeeld is de map

```text
/content/dam/wknd/es
```

Als u via **Navigatie** -> **Bestanden** -> **Activa**, ziet u de vertaalde inhoud.

![Omslagstructuur voor vertaalde inhoud](assets/translated-file-content.png)

AEM vertaalkader ontvangt de vertalingen van de vertaalschakelaar en leidt dan automatisch tot de inhoudsstructuur die op de taalwortel wordt gebaseerd en gebruikend de vertalingen die door de schakelaar worden verstrekt.

Het is belangrijk om te begrijpen dat deze inhoud niet wordt gepubliceerd en daarom niet beschikbaar voor uw headless diensten. We zullen meer leren over deze publicatiestructuur van auteurs en zien hoe we onze vertaalde inhoud in de volgende stap van de vertaalreis kunnen publiceren.

## Menselijke vertaling {#human-translation}

Als uw vertaalservice voorziet in menselijke vertaling, biedt het revisieproces meer opties. Bijvoorbeeld, komen de vertalingen terug in het project met de status **Concept** en moet met de hand worden herzien en goedgekeurd of geweigerd.

Menselijke vertaling valt buiten het bereik van deze lokalisatietraject. Zie de [Aanvullende bronnen](#additional-resources) voor meer informatie over dit onderwerp. Naast de aanvullende goedkeuringsopties is het werkschema voor menselijke vertalingen echter hetzelfde als voor machinevertalingen die in deze reis worden beschreven.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp wat een vertaalproject is.
* Nieuwe vertaalprojecten kunnen maken.
* Gebruik vertaalprojecten om uw inhoud zonder kop te vertalen.

Gebaseerd op deze kennis en doorgaan met uw AEM doorlopende vertaaltocht door het document opnieuw te bekijken [Vertaalde inhoud publiceren](publish-content.md) waar u leert hoe u uw vertaalde inhoud publiceert en hoe u deze vertalingen bijwerkt wanneer de inhoud van de hoofdtaal verandert.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de reis zonder kop gaan door het document te bekijken [Vertaalde inhoud publiceren,](publish-content.md) hieronder volgen enkele aanvullende , optionele bronnen die dieper ingaan op bepaalde in dit document genoemde concepten , maar die niet nodig zijn om verder te gaan op de weg zonder kop .

* [Vertaalprojecten beheren](/help/sites-cloud/administering/translation/managing-projects.md) - Leer de details van vertaalprojecten en aanvullende functies zoals workflows voor menselijke vertaling en meertalige projecten.
* [Ontwerpomgeving en -gereedschappen](/help/sites-cloud/authoring/fundamentals/environment-tools.md##path-selection) - AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud, waaronder een robuuste padbrowser.
