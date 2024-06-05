---
title: Inhoud vertalen
description: Gebruik de vertaalaansluiting en de regels om uw inhoud te vertalen.
index: true
hide: false
hidefromtoc: false
exl-id: b8ab2525-3f15-4844-866c-da47bfc7518c
solution: Experience Manager Sites
feature: Translation
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 0%

---

# Inhoud vertalen {#translate-content}

Gebruik de vertaalaansluiting en de regels om uw inhoud te vertalen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Sites-vertaalreis: [Vertaalregels configureren](translation-rules.md) u hebt geleerd hoe u AEM vertaalregels kunt gebruiken om uw vertaalinhoud te identificeren. Nu moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

Nu de verbindingsregels en vertaalregels zijn ingesteld, gaat dit artikel door de volgende stap voor het vertalen van uw AEM Sites-inhoud.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om AEM vertaalprojecten samen met de schakelaar en uw vertaalregels te gebruiken om inhoud te vertalen. Nadat u dit document hebt gelezen, moet u:

* Begrijp wat een vertaalproject is.
* U kunt nieuwe vertaalprojecten maken.
* Gebruik vertaalprojecten om uw AEM Sites-inhoud te vertalen.

## Een vertaalproject maken {#creating-translation-project}

Met vertaalprojecten kunt u de vertaling van AEM inhoud beheren. Een vertaalproject verzamelt de inhoud die op één locatie moet worden vertaald voor een centrale weergave van de vertaalwerkzaamheden.

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

1. Navigeren naar **Navigatie** > **Sites** en selecteer uw project.
1. Zoek de taalhoofdmap van uw project. Als de hoofdtaal bijvoorbeeld Engels is, `/content/<your-project>/en`.
   * Vóór de eerste vertaling is dat de andere taalomslagen lege placeholders zijn. Deze worden gewoonlijk gemaakt door de inhoudarchitect.
1. Zoek de taalhoofdmap van uw project.
1. Selecteer de spoorkiezer en geef de **Verwijzingen** deelvenster.
1. Selecteren **Taalkopieën**.
1. Controleer de **Taalkopieën** selectievakje.
1. De sectie uitbreiden **Taalkopieën bijwerken** onder aan het venster Verwijzingen.
1. In de **Project** vervolgkeuzelijst, selecteert u **Vertaalproject(en) maken**.
1. Geef een geschikte titel op voor uw vertaalproject.
1. Selecteren **Bijwerken**.

![Een vertaalproject maken](assets/create-translation-project.png)

U ontvangt een bericht dat het project werd gecreeerd.

>[!NOTE]
>
>Er wordt aangenomen dat de noodzakelijke taalstructuur voor de vertalingstalen reeds is gecreëerd als onderdeel van de [definitie van de inhoudsstructuur.](getting-started.md#content-structure) Dit moet gebeuren in samenwerking met de inhoudarchitect.
>
>Als de taalmappen niet van tevoren worden gemaakt, kunt u geen taalkopieën maken zoals beschreven in de vorige stappen.

### Handmatig een vertaalproject maken door uw inhoud te selecteren {#manually-creating}

Voor managers van vertaalprojecten, is het vaak noodzakelijk om specifieke inhoud manueel te selecteren om in een vertaalproject te omvatten. Als u een dergelijk handmatig vertaalproject wilt maken, moet u eerst een leeg project maken en vervolgens de inhoud selecteren die u aan het project wilt toevoegen.

1. Navigeren naar **Navigatie** > **Projecten**.
1. Selecteren **Maken** > **Map** om een map voor uw projecten te maken.
   * Dit is optioneel, maar handig om uw vertaalwerkzaamheden te organiseren.
1. In de **Project maken** venster, een **Titel** voor de map en selecteer **Maken**.

   ![Projectmap maken](assets/create-project-folder.png)

1. Selecteer de map om de map te openen.
1. Selecteer in de nieuwe projectmap de optie **Maken** > **Project**.
1. Projecten zijn gebaseerd op sjablonen. Selecteer de **Omzettingsproject** te selecteren sjabloon en vervolgens te selecteren **Volgende**.

   ![Sjabloon voor vertaalproject selecteren](assets/select-translation-project-template.png)

1. Op de **Basis** voert u een naam in voor uw nieuwe project.

   ![Tabblad Projectbasis](assets/project-basic-tab.png)

1. Op de **Geavanceerd** gebruiken **Doeltaal** om de talen te selecteren waarin de inhoud moet worden vertaald. Selecteren **Maken**.

   ![Tabblad Project geavanceerd](assets/project-advanced-tab.png)

1. Selecteren **Openen** in het bevestigingsdialoogvenster.

   ![Dialoogvenster Projectbevestiging](assets/project-confirmation-dialog.png)

Het project is gemaakt, maar bevat geen inhoud om te vertalen. In de volgende sectie wordt beschreven hoe het project is gestructureerd en hoe u inhoud kunt toevoegen.

## Een vertaalproject gebruiken {#using-translation-project}

Vertaalprojecten zijn ontworpen om alle inhoud en taken in verband met een vertaalinspanning op één plaats te verzamelen, zodat uw vertaling eenvoudig en eenvoudig te beheren is.

Het vertaalproject weergeven:

1. Navigeren naar **Navigatie** > **Projecten**.
1. Selecteer het project dat in de vorige sectie werd gecreeerd (of [Automatisch een vertaalproject maken op basis van het inhoudspad](#automatically-creating) of [Handmatig een vertaalproject maken door uw inhoud te selecteren](#manually-creating) afhankelijk van uw situatie).

![Vertaalproject](assets/translation-project.png)

Het project is verdeeld in meerdere kaarten.

* **Samenvatting** - Deze kaart bevat de basiskoptekstinformatie van het project, waaronder de eigenaar, de taal en de vertaalprovider.
* **Vertaaltaak** - Op deze kaart of op deze kaarten wordt (worden) een overzicht gegeven van de werkelijke vertaalbaan, met inbegrip van de status, het aantal activa, enzovoort. Over het algemeen is er één taak per taal, waarbij de ISO-2-taalcode aan de taaknaam wordt toegevoegd.
   * Wanneer [automatisch vertaalbanen creëren,](#automatically-creating) AEM leidt tot de banen asynchroon en zij kunnen niet onmiddellijk binnen het project verschijnen.
* **Team** - Deze kaart toont de gebruikers die aan dit vertaalproject samenwerken. Deze reis gaat niet over dit onderwerp.
* **Taken** - Aanvullende taken die samenhangen met het vertalen van de inhoud, zoals het uitvoeren van items of workflowitems. Deze reis gaat niet over dit onderwerp.

Om de vertaalstroom in AEM beter te begrijpen, is één verandering in de projectmontages nuttig. Deze stap is niet vereist voor productievertalingen, maar voor een beter begrip van het proces.

1. Op de **Samenvatting** -kaart, selecteert u de knop voor ovaal onder aan de kaart.
1. Op de **Geavanceerd** tabblad, schakelt u de optie uit **Starten na aanbieding verwijderen**.

   ![Starten na promotieoptie verwijderen](assets/delete-launch-option.png)

1. Selecteren **Opslaan en sluiten**.

Nu kunt u uw vertaalproject gebruiken. Hoe u een vertaalproject gebruikt, hangt af van de manier waarop het is gemaakt: automatisch door AEM of handmatig.

### Een automatisch gemaakt vertaalproject gebruiken {#using-automatic-project}

Wanneer het automatisch tot stand brengen van het vertaalproject, evalueert AEM de inhoud onder de weg u selecteerde gebaseerd op de vertaalregels die u eerder bepaalde. Op basis van die evaluatie extraheert het de inhoud die vertaald moet worden naar een nieuw vertaalproject.

U kunt als volgt de details van de inhoud in dit project bekijken:

1. Selecteer de knop voor ovaal onder aan het dialoogvenster **Vertaaltaak** kaart.
1. De **Vertaaltaak** worden alle items in de taak weergegeven.

   ![Taakdetails voor vertaling](assets/translation-job-detail.png)

1. Selecteer een regel om de details van die regel weer te geven. Houd er rekening mee dat één regel meerdere inhoudsitems kan vertegenwoordigen om te vertalen.
1. Schakel het selectievakje voor een regelitem in om andere opties weer te geven, zoals de optie om het item uit de taak te verwijderen of in de siteconsole weer te geven.

   ![Opties voor vertaaltaken](assets/translation-job-options.png)

De inhoud van de vertaaltaak wordt meestal gestart in het dialoogvenster **Concept** staat zoals aangegeven door **Staat** in de **Vertaaltaak** venster.

Als u de vertaaltaak wilt starten, gaat u terug naar het overzicht van het vertaalproject en selecteert u de knop chevron boven aan het dialoogvenster **Vertaaltaak** kaart en selecteer **Start**.

![Vertaaltaak starten](assets/start-translation-job.png)

AEM communiceert nu met uw vertaalconfiguratie en -connector om de inhoud naar de vertaalservice te verzenden. U kunt de voortgang van de vertaling bekijken door terug te keren naar de **Vertaaltaak** venster en de **Staat** kolom van de vermeldingen.

![Vertaaltaak goedgekeurd](assets/translation-job-approved.png)

De vertalingen van de machine keren automatisch met een staat van terug **Goedgekeurd**. Menselijke vertaling maakt meer interactie mogelijk, maar valt buiten het bereik van deze reis.

>[!TIP]
>
>Het kan enige tijd duren om een vertaaltaak te verwerken en het kan zijn dat uw vertaalitems van de status **Concept** tot **Bezig met omzetten** tot **Gereed voor revisie** voordat ze bij **Goedgekeurd** status. Dat is te verwachten.

>[!NOTE]
>
>Als u de projectoptie niet hebt gedeactiveerd **Starten na aanbieding verwijderen** als [beschreven in het vorige punt,](#using-translation-project) vertaalde items worden weergegeven bij de **Verwijderd** status. Dit is normaal, omdat AEM de vertaalverslagen automatisch verwijdert zodra de vertaalde punten aankomen. De vertaalde items zijn geïmporteerd als taalkopieën, alleen de vertaalrecords zijn verwijderd omdat ze niet meer nodig zijn.
>
>Maak je geen zorgen als dit onduidelijk is. Dit zijn diepgaande details van hoe AEM werkt en niet uw begrip van de reis beïnvloedt. Als u dieper wilt duiken op hoe AEM vertalingen verwerkt, zie [extra middelen](#additional-resources) aan het einde van dit artikel.

### Een handmatig gemaakt vertaalproject gebruiken {#using-manual-project}

Als u handmatig een vertaalproject maakt, AEM de benodigde taken, maar selecteert u niet automatisch de inhoud die u in die taken wilt opnemen. Hierdoor kan de projectbeheerder van de vertaling kiezen welke inhoud moet worden vertaald.

Inhoud toevoegen aan een vertaaltaak:

1. Selecteer de knop voor ovaal onder aan een van de opties **Vertaaltaak** kaarten.
1. Controleer of de taak geen inhoud bevat. Selecteer de **Toevoegen** boven aan het venster en vervolgens **Middelen/Pagina&#39;s** in de vervolgkeuzelijst.

   ![Lege vertaaltaak](assets/empty-translation-job.png)

1. Er wordt een padbrowser geopend waarin u specifiek kunt selecteren welke inhoud u wilt toevoegen. Zoek de inhoud en selecteer deze.

   ![Padbrowser](assets/path-browser.png)

1. Selecteren **Selecteren** om de geselecteerde inhoud aan de baan toe te voegen.
1. In de **Vertalen** , geeft u op dat u **Taalkopie maken**.

   ![Taalkopie maken](assets/translate-copy-master.png)

1. De inhoud wordt nu opgenomen in de taak.

   ![Inhoud toegevoegd aan vertaaltaak](assets/content-added.png)

1. Schakel het selectievakje voor een regelitem in om andere opties weer te geven, zoals de optie om het item uit de taak te verwijderen of in de siteconsole weer te geven.

   ![Opties voor vertaaltaken](assets/translation-job-options.png)

1. Herhaal deze stappen om alle vereiste inhoud in de taak op te nemen.

>[!TIP]
>
>De padbrowser is een krachtig hulpmiddel waarmee u uw inhoud kunt zoeken, filteren en doorbladeren. Selecteer de **Alleen inhoud/filters** om het zijpaneel in en uit te schakelen en geavanceerde filters zoals **Wijzigingsdatum** of **Vertaalstatus**.
>
>Meer informatie over de padbrowser vindt u in het dialoogvenster [sectie aanvullende bronnen.](#additional-resources)

U kunt de voorafgaande stappen gebruiken om de noodzakelijke inhoud aan alle talen (banen) voor het project toe te voegen. Nadat u alle inhoud hebt geselecteerd, kunt u de vertaling starten.

De inhoud van de vertaaltaak wordt meestal gestart in het dialoogvenster **Concept** staat zoals aangegeven door **Staat** in de **Vertaaltaak** venster.

Als u de vertaaltaak wilt starten, gaat u terug naar het overzicht van het vertaalproject en selecteert u de knop chevron boven aan het dialoogvenster **Vertaaltaak** kaart en selecteer **Start**.

![Vertaaltaak starten](assets/start-translation-job.png)

AEM communiceert nu met uw vertaalconfiguratie en -connector om de inhoud naar de vertaalservice te verzenden. U kunt de voortgang van de vertaling bekijken door terug te keren naar de **Vertaaltaak** venster en de **Staat** kolom van de vermeldingen.

![Vertaaltaak goedgekeurd](assets/translation-job-approved.png)

De vertalingen van de machine keren automatisch met een staat van terug **Goedgekeurd**. Menselijke vertaling maakt meer interactie mogelijk, maar valt buiten het bereik van deze reis.

>[!TIP]
>
>Het kan enige tijd duren om een vertaaltaak te verwerken en het kan zijn dat uw vertaalitems van de status **Concept** tot **Bezig met omzetten** tot **Gereed voor revisie** voordat ze bij **Goedgekeurd** status. Dat is te verwachten.

>[!NOTE]
>
>Als u de projectoptie niet hebt gedeactiveerd **Starten na aanbieding verwijderen** als [beschreven in het vorige punt,](#using-translation-project) vertaalde items worden weergegeven bij de **Verwijderd** status. Dit is normaal, omdat AEM de vertaalverslagen automatisch verwijdert zodra de vertaalde punten aankomen. De vertaalde items zijn geïmporteerd als taalkopieën, alleen de vertaalrecords zijn verwijderd omdat ze niet meer nodig zijn.
>
>Maak je geen zorgen als dit onduidelijk is. Dit zijn diepgaande details van hoe AEM werkt en niet uw begrip van de reis beïnvloedt. Als u dieper wilt duiken op hoe AEM vertalingen verwerkt, zie [extra middelen](#additional-resources) aan het einde van dit artikel.

## Vertaalde inhoud controleren {#reviewing}

[Zoals eerder waargenomen,](#using-translation-project) door de computer vertaalde inhoud gaat terug naar AEM met de status **Goedgekeurd** aangezien ervan wordt uitgegaan dat er geen menselijk ingrijpen vereist is omdat er machinevertaling wordt gebruikt . Het is echter nog steeds mogelijk om de vertaalde inhoud te beoordelen.

Ga eenvoudig naar de voltooide vertaalbaan en selecteer een lijnpunt door te tikken of checkbox te klikken. Het pictogram **Voorvertoning in sites** wordt weergegeven in de werkbalk.

![Tonen op sites](assets/reveal-in-sites.png)

Selecteer dat pictogram om de vertaalde inhoud in zijn console te openen om de details van de vertaalde inhoud te zien.

![Een vertaalde pagina](assets/translated-page.png)

U kunt de vertaalde inhoud verder aanpassen, op voorwaarde dat u de juiste toestemming hebt, maar het bewerken van inhoud valt buiten het bereik van deze reis. Zie de [Aanvullende bronnen](#additional-resources) voor meer informatie over dit onderwerp.

Het doel van het project is om alle middelen in verband met een vertaling op één plaats te verzamelen, zodat u gemakkelijk toegang hebt en een duidelijk overzicht krijgt. Zoals u echter kunt zien door de details van een vertaald item weer te geven, vloeien de vertalingen zelf terug naar de map sites van de vertaaltaal. In dit voorbeeld is de map

```text
/content/<your-project>/es
```

Als u via **Navigatie** > **Sites**, ziet u de vertaalde inhoud.

![Omslagstructuur voor vertaalde inhoud](assets/translated-sites-content.png)

AEM vertaalkader ontvangt de vertalingen van de vertaalschakelaar en leidt dan automatisch tot de inhoudsstructuur die op de taalwortel wordt gebaseerd en gebruikend de vertalingen die door de schakelaar worden verstrekt.

Het is belangrijk te begrijpen dat deze inhoud niet wordt gepubliceerd en dus niet beschikbaar is voor consumptie. U leert over deze auteur-publicatiestructuur en ziet hoe u onze vertaalde inhoud kunt publiceren in de volgende stap van de vertaalreis.

## Menselijke vertaling {#human-translation}

Als uw vertaalservice voorziet in menselijke vertaling, biedt het revisieproces meer opties. Bijvoorbeeld, komen de vertalingen terug in het project met de status **Concept** en moet met de hand worden herzien en goedgekeurd of geweigerd.

Menselijke vertaling valt buiten het bereik van deze lokalisatietraject. Zie de [Aanvullende bronnen](#additional-resources) voor meer informatie over dit onderwerp. Naast de aanvullende goedkeuringsopties is het werkschema voor menselijke vertalingen echter hetzelfde als voor machinevertalingen die in deze reis worden beschreven.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Sites-vertaalreis hebt voltooid, moet u:

* Begrijp wat een vertaalproject is.
* U kunt nieuwe vertaalprojecten maken.
* Gebruik vertaalprojecten om uw inhoud te vertalen.

Gebaseerd op deze kennis en uw AEM Sites-vertaalreis voortzetten door het document opnieuw te bekijken [Vertaalde inhoud publiceren](publish-content.md) waar u leert hoe u uw vertaalde inhoud publiceert en hoe te om die vertalingen bij te werken aangezien uw inhoud van de taalwortel verandert.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de vertaalreis gaan door het document te bekijken [Vertaalde inhoud publiceren,](publish-content.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [Vertaalprojecten beheren](/help/sites-cloud/administering/translation/managing-projects.md) - Leer de details van vertaalprojecten en aanvullende functies zoals workflows voor menselijke vertaling en meertalige projecten.
* [Ontwerpomgeving en -gereedschappen](/help/sites-cloud/authoring/path-selection.md#path-selection) - AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud, waaronder een robuuste padbrowser.
