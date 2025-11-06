---
title: Kanalen maken en beheren in Screens as a Cloud Service
description: Op deze pagina wordt beschreven hoe u kanalen kunt maken en beheren in Screens as a Cloud Service.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 1%

---

# Een kanaal maken en beheren in Screens as a Cloud Service {#creating-channels-screens-cloud}

Nadat u een AEM Screens-project hebt gemaakt, moet u kanalen maken.
***Kanalen***, toon een opeenvolging van inhoud (beelden en video&#39;s), een website, of een enig-paginatoepassing.

## Doelstelling {#objective}

Met dit document krijgt u meer inzicht in het maken en beheren van kanalen voor uw AEM Screens-project in de Screens Content Provider. Na het lezen moet u:

* begrijpen hoe kanalen naar Screens Content Provider kunnen worden gemaakt
* inhoud in uw kanalen beheren en bewerken
* beheer taak en activeringsprogramma voor uw kanalen in [ de Dienstverlener van Screens ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=en)

## Stappen voor het maken van een nieuw sequentiekanaal in Screens as a Cloud Service {#create-new-channel}

>[!NOTE]
>**Eerste vereisten**
>Alvorens deze sectie van de Gids te beginnen, herzie [ Creërend en het Leiden Projecten in Screens as a Cloud Service ](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Ga als volgt te werk om een volgnummer te maken in Screens as a Cloud Service:

1. Navigeer naar de Screens Content Provider.

1. Navigeer aan uw project van AEM Screens, zoals *FirstDigitalExperience*.

1. Selecteer de **omslag van Kanalen** van uw project, zoals **FirstDigitalExperience** -> **Kanalen** en klik **creeer** van de actiebar.

   ![ kanaal-create1 ](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Selecteer het malplaatje, zoals, **Kanaal van de Opeenvolging** van **creeer** tovenaar en klik **daarna**.

   ![ kanaal-create2 ](/help/screens-cloud/assets/create-content/channel-create2.png)

   >[!NOTE]
   > **creeer** tovenaar verstrekt verschillende soorten malplaatjes terwijl het creëren van een kanaal. Zie [ Beschikbare Malplaatjes ](#available-templates) in Create Tovenaar voor meer details.

1. Ga de naam van uw opeenvolgingskanaal, zoals in, **LoopingChannelOne** en klik **creeer**.

   ![ kanaal-create3 ](/help/screens-cloud/assets/create-content/channel-create3.png)

   U zult nu a **LoopingChannelOne** in uw omslag van Kanalen in uw project van AEM Screens zien.

   Nadat u het kanaal hebt gemaakt, kunt u nu inhoud aan het kanaal toevoegen. Zie [ Toevoegend Inhoud aan een Kanaal ](#add-content) om te leren hoe te om activa (beelden/video&#39;s) aan uw kanaal toe te voegen.

## Een kanaal beheren {#managing-channels}

U kunt een kanaal bewerken, weergeven, eigenschappen en dashboard, kopiëren, voorvertonen en verwijderen.

Navigeer naar het kanaal vanuit uw project en selecteer het kanaal, zoals in de onderstaande afbeelding wordt getoond. U kunt nu opties selecteren, zoals het bewerken van het kanaal, het weergeven van eigenschappen, het voorvertonen van inhoud, het beheren van publicatie of het verwijderen van het kanaal uit de actiebalk.

![ channelprop1 ](/help/screens-cloud/assets/create-content/channelprop1.png)

### Inhoud toevoegen aan een kanaal {#add-content}

Ga als volgt te werk om inhoud aan een kanaal toe te voegen of te bewerken:

1. Selecteer het kanaal dat u wilt bewerken, zoals in de onderstaande afbeelding wordt getoond. Klik **uitgeven** van de hoogste linkerhoek van de actiebar om de redacteur te openen.

   ![ geef-channel1 uit ](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. In de editor kunt u elementen/componenten aan uw kanaal toevoegen die u wilt publiceren.

1. Sleep de elementen vanuit het linkerdeelvenster en voeg deze toe aan de editor.

   ![ uitgeven-channel2 ](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Klik **Voorproef** aan voorproef de inhoud van uw kanaal.
   >![ geef-kanaalvoorproef uit ](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Beschikbare sjablonen in wizard Maken {#available-templates}

De volgende malplaatjes zijn beschikbaar terwijl het gebruiken van **creeer** kanaaltovenaar:

| Beschikbare sjablonen | Beschrijving |
|--- |--- |
| Map Kanalen | Hiermee kunt u een map maken waarin de verzameling kanalen wordt opgeslagen. |
| Volgekanaal | Hiermee kunt u een kanaal maken waarmee de componenten opeenvolgend worden afgespeeld (een voor een in een presentatie). |
| Linker- of rechterL-balkgesplitste schermkanaal | Hiermee kunnen auteurs van inhoud verschillende typen elementen weergeven in zones met de juiste grootte. |

## Standaardtoewijzingsdetails gebruiken voor kanalen {#default-channels}

Met deze functie kunt u een standaard activeringsschema voor een kanaal definiëren en dit standaard gebruiken voor elke toewijzing voor een weergave. Dit verstrekt een methode zodat de lastige programmadefinitie niet te hoeven worden herhaald.

1. Navigeer aan de [ Leverancier van de Diensten van Screens ](https://experience.adobe.com/screens).

### Standaardtoewijzingsdetails maken voor een kanaal {#create-default}

1. Navigeer naar de detailspagina voor het kanaal u wilt vormen.
1. Bepaal de plaats van de **Standaard toewijzingsdetails** tegel op de pagina.

   ![afbeelding](/help/screens-cloud/assets/display/Assignment1.png)

1. Klik **Vastgestelde standaarddetails**.
1. Vorm de standaardtoewijzingsdetails, met inbegrip van prioriteit, begin &amp; einddata, en terugkerende patronen voor het kanaal, en klik **toewijzen**.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments2.png)

1. Merk op de details van de taak in de **Standaard toewijzingsdetails** tegel worden getoond:

   ![afbeelding](/help/screens-cloud/assets/display/Assignments3.png)

In deze tegel wordt de volgende informatie weergegeven:

* Standaardprioriteit van het kanaal in de weergave.
* De begin- en einddatum van de activering wanneer het kanaal volgens de planning moet worden afgespeeld.
* Synthetisch overzicht van de herhaling (Uur/Daily/Weekly/Maandelijks/Jaarlijks en naam die aan die herhaling wordt gegeven).

### De standaardtoewijzingsdetails gebruiken bij het toewijzen aan een weergave {#default-display}

Kanalen met standaardtoewijzingsdetails kunnen op dezelfde manier worden weergegeven als gewone kanalen, met de toegevoegde optie om de standaardtoewijzingsdetails te gebruiken in plaats van telkens handmatig aangepaste details te definiëren.

1. Navigeer aan de pagina van vertoningsdetails u het kanaal aan wilt toewijzen en **klikken wijst kanaal** toe.
Alternatief, selecteer de gewenste vertoning in de [ inventaris ](https://experience.adobe.com/screens/displays) mening en klik **toewijzen kanaal**.
1. Het dialoogvenster Kanaaltoewijzing wordt geopend.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments4.png)

1. Selecteer in de kanaalkiezer het gewenste kanaal met de standaardtoewijzingsdetails.
1. U ziet dat het dialoogvenster voor kanaaltoewijzing is gewijzigd, zodat u de standaardtoewijzingsdetails kunt kiezen of aangepaste toewijzingsdetails kunt selecteren:

   ![afbeelding](/help/screens-cloud/assets/display/Assignments5.png)

1. Klik **toewijzen** om de taak te voltooien, of **plaats de details van de douanetoewijzing** als u verkiest met sommige andere waarden in de context van die bepaalde vertoning met voeten te treden.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments6.png)

1. Merk op de **Toegewezen kanalen** tegel wordt bijgewerkt met de nieuwe taak:

   ![afbeelding](/help/screens-cloud/assets/display/Assignments7.png)

1. U ziet dat de kanalen een ander pictogram hebben, afhankelijk van het feit of ze aangepaste programma&#39;s (het pictogram Klok) gebruiken of de standaarddetails (het pictogram voor de klok van de Wereld) overnemen. Als u op deze kanalen klikt, worden de planningsdetails weergegeven.
1. U ziet ook dat de beschikbare acties voor elk type verschillen.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments8.png)

**Nota:** de kanaaltaak van A die de standaardtoewijzingsdetails gebruikt zal niet in de context van de vertoning editable zijn.

* Als u het in een douanetoewijzing moet veranderen, verwijder eerst het en voeg het dan opnieuw toe gebruikend de **Reeks de details van de douanetoewijzing** optie.
* Als u de eigenschappen van de standaardtoewijzingsdetails moet wijzigen, doet u dit rechtstreeks vanaf de pagina met kanaaldetails.

### Standaardtoewijzingsgegevens uit een kanaal verwijderen {#remove-display}

1. Navigeer naar de detailpagina voor het kanaal u de standaardtoewijzingsdetails wilt verwijderen.
1. Bepaal de plaats van de **Standaard toewijzingsdetails** tegel in de pagina
1. Klik **verwijderen gebrek**.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments9.png)

1. Er wordt een bevestigingsdialoogvenster weergegeven en de details komen overeen met een van de volgende voorwaarden:
   **a.** het Kanaal wordt niet gebruikt in om het even welke vertoning.

   ![afbeelding](/help/screens-cloud/assets/display/Assignments10.png)

**b.** Kanaal wordt gebruikt in één enkele vertoning.

![afbeelding](/help/screens-cloud/assets/display/Assignment11.png)

**c.** Kanaal wordt gebruikt in verscheidene vertoningen.

![afbeelding](/help/screens-cloud/assets/display/Assignments12.png)

1. Klik *verwijderen* om de verandering te bevestigen.

**Nota:** het verwijderen van de standaardtoewijzingsdetails uit een kanaal zal de passende taken op alle vertoningen verwijderen die het gebruikten.
Dit kan dan ook leiden tot lege schermen als er geen alternatieve inhoud op die schermen moet worden afgespeeld.

## Volgende functies {#whats-next}

Nu u een AEM Screens-kanaal hebt ingesteld in uw project, moet u uw kanaal publiceren. Zie [ het Publiceren Kanalen in Screens as a Cloud Service ](manage-publish.md) alvorens uw spelers van de Leverancier van de Diensten van Screens te beheren.
