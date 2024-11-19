---
title: Werkbladen gebruiken om tabelgegevens te beheren
description: Leer hoe u met werkbladen tabelgegevens kunt beheren voor verschillende waarden, zoals metagegevens en omleidingen voor uw AEM naar de site Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 26d4db90-3e4b-4957-bf21-343c76322cdc
role: Admin, Architect, Developer
source-git-commit: 4e4234c1aaf0a410cb419140e9e353348ce118c1
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---


# Werkbladen gebruiken om tabelgegevens te beheren {#tabular-data}

Leer hoe u met werkbladen tabelgegevens kunt beheren voor verschillende waarden, zoals metagegevens en omleidingen voor uw AEM naar de site Edge Delivery Services.

## Gevallen gebruiken {#use-cases}

Voor om het even welke AEM met de plaats van Edge Delivery Services, is er een behoefte om lijsten van tabelgegevens zoals voor sleutel-waarde afbeeldingen te handhaven. Dit kunnen lijsten van vele verschillende waarden zoals meta-gegevens en omleiding zijn. Met Edge Deliver Services kunt u dergelijke tabellijsten bijhouden met behulp van een intuïtief hulpprogramma: de spreadsheet. AEM zet deze spreadsheets om in JSON-bestanden die eenvoudig door uw website of webtoepassing kunnen worden gebruikt.

Vaak voorkomende gevallen van gebruik zijn:

* [Plaatsaanduidingen](/help/edge/docs/placeholders.md)
* [Metagegevens](/help/edge/docs/bulk-metadata.md)
* [Kopteksten](/help/edge/docs/custom-headers.md)
* [Omleiding](/help/edge/docs/redirects.md)
* [ Configuraties ](/help/edge/docs/setup-byo-cdn-push-invalidation.md) zoals voor montages CND

Bovendien kunt u uw spreadsheets ](#own-spreadsheet) van om het even welke structuur tot stand brengen om afbeeldingen voor uw eigen doeleinden op te slaan.[

Dit document gebruikt het voorbeeld van omleidingen om te illustreren hoe u dergelijke spreadsheets kunt maken. Zie de eerder-verbonden onderwerpen in de documentatie van Edge Delivery Services voor details van elk gebruiksgeval.

>[!TIP]
>
>Voor meer informatie over hoe spreadsheets in het algemeen met Edge Delivery Services werken, zie gelieve het document [ Spreadsheets en JSON.](/help/edge/developer/spreadsheets.md)

>[!TIP]
>
>Spreadsheets mogen alleen worden gebruikt om tabelgegevens te onderhouden. Voor het opslaan van gestructureerde gegevens, [ controle uit AEM het installeren van headless eigenschappen.](/help/headless/introduction.md)

## Vereisten {#prerequisites}

Als u toewijzingen wilt maken met behulp van spreadsheets in uw AEM met Edge Delivery Services-project, moet u uw site hebben gemaakt met de nieuwste sitesjabloon.

Gelieve te zien de document [ Begonnen Gids van de Ontwikkelaar Begonnen voor het schrijven van WYSIWYG met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) voor meer informatie.

## Een werkblad maken {#spreadsheet}

In dit voorbeeld maakt u een spreadsheet voor het beheren van omleidingen voor uw AEM met de site Edge Delivery Services. De zelfde stappen zijn op [ andere spreadsheettypes ](#other) van toepassing die u wenst te creëren.

1. Teken binnen aan uw het auteursinstantie van AEM as a Cloud Service, ga naar de **console van Plaatsen**, en navigeer aan de wortel van de plaats die een spreadsheet vereist. Tik of klik **creeer** -> **Pagina**.

   ![ creeer pagina ](assets/tabular-data/tabular-data-create-page.png)

1. Op het **Malplaatje** lusje van creeer paginatovenaar, ontvang of klik **richt** malplaatje opnieuw om het te selecteren en dan te onttikken of **daarna** te klikken.

   ![ Uitgezochte malplaatje ](assets/tabular-data/tabular-data-create-page-teamplate-redirects.png)

1. Het **lusje van Eigenschappen** van de tovenaar stelt de standaardwaarden voor opnieuw richt spreadsheet voor. Tik of klik **creeer**.

   * **Titel** - verlaat deze waarde zoals-is.
   * **Kolommen** - de minimumkolommen nodig voor redirects zijn prepopulated.
      * **bron** - de pagina die moet worden opnieuw gericht
      * **bestemming** - de pagina aan redirect aan

   ![ Eigenschappen van spreadsheet ](assets/tabular-data/tabular-data-create-page-properties-redirects.png)

1. In de **dialoog van het Succes**, tik of klik **Open**.

   ![ de dialoog van het Succes ](assets/tabular-data/tabular-data-success.png)

1. Een nieuw lusje opent met spreadsheet die in een redacteur met vooraf bepaalde **wordt geladen bron** en **bestemmings** kolommen. Om uw redirects te bepalen, tik of klik de lege rij van de **bron** kolom. Wijzigingen worden automatisch opgeslagen wanneer u het werkblad bewerkt.

   ![ geef spreadsheet ](assets/tabular-data/tabular-data-edit-redirects.png) uit

   * De **bron** is met betrekking tot het domein van uw website, zodat bevat het slechts de relatieve weg.
   * De **bestemming** kan of volledig - gekwalificeerde URL zijn als u aan een verschillende website opnieuw richt, of het kan een relatieve weg zijn als u binnen uw eigen website opnieuw richt.
   * Gebruik de Tab-toets om de focus naar de volgende cel te verplaatsen.
   * De redacteur voegt nieuwe rijen aan spreadsheet toe zonodig.
   * Om een rij te schrappen of te bewegen, gebruik het **1} pictogram van de Schrapping aan het eind van elke rij en de belemmeringshandvatten aan het begin van elke rij, respectievelijk.**

## Werkbladgegevens importeren {#importing}

Naast het bewerken van spreadsheets in de AEM Pagina-editor kunt u ook gegevens uit een CSV-bestand importeren.

1. Wanneer het uitgeven van uw spreadsheet in AEM, tik of klik **uploadt** knoop bij top-left van het scherm.
1. Selecteer in de vervolgkeuzelijst hoe u de gegevens wilt importeren.
   * **vervangt Doc** om de inhoud van volledige spreadsheet met de inhoud van het Csv- dossier te vervangen u zult uploaden.
   * **voeg aan Doc** toe om de gegevens van het Csv- dossier toe u aan de bestaande spreadsheetinhoud zult uploaden.
1. In de dialoog die opent, selecteer uw Csv- dossier en dan ontleend of klik **Open**.

Er wordt een dialoogvenster geopend wanneer het importeren wordt verwerkt. Wanneer de gegevens in het CSV-bestand zijn voltooid, worden deze toegevoegd aan of vervangen door de inhoud van het spreadsheet. Als er fouten optreden, zoals een fout in de kolomverhoudingen, worden deze gemeld zodat u het CSV-bestand kunt corrigeren.

>[!NOTE]
>
>* De koppen in het CSV-bestand moeten exact overeenkomen met de kolommen in het werkblad.
>* Als u de volledige CSV importeert, worden de kolomkoppen niet gewijzigd, alleen de inhoudsrijen.
>* Als u de kolommen moet bijwerken, moet u dat doen in de AEM Pagina-editor voordat u de CSV-bestanden kunt importeren.
>* Een CSV-bestand kan niet groter zijn dan 10 MB voor importeren.

Afhankelijk van de selectie van `mode` kunt u ook `create` , `replace` of `append` naar spreadsheets gaan met een opdracht CSV en cURL, vergelijkbaar met de volgende.

```text
curl --request POST \
  --url http://<aem-instance>/bin/asynccommand \
  --header 'content-type: multipart/form-data' \
  --form file=@/path/to/your.csv \
  --form spreadsheetPath=/content/<your-site>/<your-spreadsheet> \
  --form 'spreadsheetTitle=Your Spreadsheet' \
  --form cmd=spreadsheetImport \
  --form operation=asyncSpreadsheetImport \
  --form _charset_=utf-8 \
  --form mode=append
```

De aanroep retourneert een HTML-pagina met informatie over de taak-id.

```text
Message | Job(Id:2024/9/18/15/27/5cb0cacc-585d-4176-b018-b684ad2dfd02_90) created successfully. Please check status at Async Job Status Navigation.
```

[ u kunt de **2} console van Banen ](/help/operations/asynchronous-jobs.md) gebruiken om het statuut van de baan te bekijken of identiteitskaart te gebruiken die aan vraag het is teruggekeerd.**

```text
https://<aem-instance>/bin/asynccommand?optype=JOBINF&jobid=2024/10/24/14/1/8da63f9e-066b-4134-95c9-21a9c57836a5_1
```

## Een spreadsheetpad.json publiceren {#paths-json}

Als AEM de gegevens in uw spreadsheet wilt publiceren, moet u het `paths.json` -bestand van uw project bovendien bijwerken.

1. Open de wortel van uw project in GitHub.

1. Tik of klik het `paths.json` dossier om zijn details te openen en dan **geef** pictogram uit.

   ![ paths.json- dossier ](assets/tabular-data/tabular-data-paths-json.png)

1. Voeg een lijn toe om uw nieuwe spreadsheet aan een `redirects.json` middel in kaart te brengen.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/redirects:/redirects.json"
     ]
   }
   ```

   >[!NOTE]
   >
   >Dit `paths.json` -item is gebaseerd op het voorbeeld van het maken van omleidingen met behulp van tabelgegevens. Zorg ervoor om de weg aangewezen aan het [ type van spreadsheet bij te werken u creeert.](#other)

1. Klik **Veranderingen vastleggen...** om de veranderingen in `main` te bewaren.

   * Leg dit vast aan `main` of maak een pull-aanvraag volgens uw proces.

1. Wanneer u klaar bent het bepalen van uw omleidingen en u de wegafbeelding bijwerkte, terugkeer aan de **Sites** console.

1. Tik of klik om het opnieuw richt spreadsheet te selecteren dat u in de console creeerde en dan **Snelle Publish** in de actiebar tikt of klikt om spreadsheet te publiceren.

   ![ selecteer spreadsheet in de console van Plaatsen ](assets/tabular-data/tabular-data-select-publish.png)

1. In de **dialoog van 30} Snelle Publish {, tik of klik** Publish **.**

   ![ bevestigt publiceren ](assets/tabular-data/tabular-data-quick-publish.png)

1. Een banner bevestigt de publicatie.

   ![ bevestiging van de Banner van publicatie ](assets/tabular-data/tabular-data-publish-banner.png)

Het spreadsheet voor omleiding wordt nu gepubliceerd en openbaar gemaakt.

>[!TIP]
>
>Voor meer informatie over wegafbeeldingen, te zien gelieve het document [ Toewijzing van de Weg voor Edge Delivery Services.](/help/edge/wysiwyg-authoring/path-mapping.md)

## Andere spreadsheettypen {#other}

Nu u weet hoe u een spreadsheet voor omleidingen kunt maken, kunt u elk ander standaardspreadsheettype maken:

* Plaatsaanduidingen
* Metagegevens
* Kopteksten
* Configuratie
* [Taxonomie](/help/edge/wysiwyg-authoring/taxonomy.md)

Volg eenvoudig de zelfde stappen in de secties [ creëren Spreadsheet ](#spreadsheet) en [ Update paths.json ](#paths-json) en kies het aangewezen malplaatje en werk het `paths.json` dossier dienovereenkomstig bij.

Voor [ Configuratie ](https://www.aem.live/docs/configuration), [ Kopballen ](https://www.aem.live/docs/custom-headers) en [ Meta-gegevens ](https://www.aem.live/docs/bulk-metadata) zorgen ervoor om een afbeelding toe te voegen om hen aan hun standaardplaatsen te publiceren:

* Configuratie: `/.helix/config.json`
* Kopteksten: `/.helix/headers.json`
* Metagegevens: `/metadata.json`
* Taxonomie: Gelieve te zien het document [ Leiden Gegevens van de Taxonomie ](/help/edge/wysiwyg-authoring/taxonomy.md) voor meer informatie.

Bovendien, kunt u [ uw eigen spreadsheet ](#own-spreadsheet) met willekeurige kolommen voor uw eigen gebruik tot stand brengen.

>[!NOTE]
>
>U hoeft geen spreadsheet te maken om indexering voor AEM as a Cloud Service met projecten van Edge Delivery Services te beheren.
>
>Als u wenst om uw eigen indexen tot stand te brengen, [ te volgen gelieve deze documentatie ](https://www.aem.live/developer/indexing#setting-up-more-index-configurations) om uw eigen `helix-query.yaml` dossier tot stand te brengen.

## Uw eigen spreadsheet maken {#own-spreadsheet}

1. Volg de zelfde stappen in de sectie [ creëren Spreadsheet.](#spreadsheet)

1. Wanneer het selecteren van het malplaatje, kies **Spreadsheet**.

1. In het **lusje van Eigenschappen** van de tovenaar, kunt u uw eigen kolommen toevoegen.

   ![ voeg uw eigen kolommen ](assets/tabular-data/tabular-data-own-spreadsheet.png) toe

   * In de **sectie van Kolommen**, onttikt of klikt **** toevoegt om een nieuwe kolom toe te voegen.
   * Geef een naam op voor de kolom.
   * Verwijder of reorganiseer de kolommen gebruikend **Schrapping** en belemmering handvatpictogrammen, respectievelijk.

1. Maak het spreadsheet en publiceer dit volgens de instructies voor het spreadsheet omleiden.

1. Voeg een toewijzing aan het `paths.json` dossier volgens de instructies voor het herleidingsspreadsheet toe.

