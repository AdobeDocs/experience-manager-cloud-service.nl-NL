---
title: Auto-markering activa met  [!DNL Adobe AI]  slimme dienst
description: Voorzie assets van tags met een AI-service die contextuele en beschrijvende bedrijfstags toepast.
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1465'
ht-degree: 5%

---


# Training voor slimme tags

Met training voor slimme tags kunt u tags trainen, zodat u de gegevens kunt opgeven als de relevante tags niet aanwezig zijn. Het gebruikt een kunstmatig intelligent kader van [&#x200B; Adobe AI &#x200B;](https://business.adobe.com/ai/adobe-genai.html) om zijn algoritme van de beelderkenning op uw markeringsstructuur en bedrijfstaxonomie te trainen. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. [!DNL Experience Manager Assets] past standaard automatisch slimme tags toe op geüploade elementen.

## Bepalen van de vereiste van training voor slimme tags {#smart-tag-training-requirement}

Slimme tags training is vereist in de volgende scenario&#39;s:

* Een automatische labelfunctie toevoegen om telkens wanneer u hetzelfde element uploadt herhalingen van het toevoegen van labels op te slaan.
* Verbetering van de mogelijkheid voor elementen om relevante codes toe te passen.
* De nauwkeurigheid van de tags die worden weergegeven voor een element vergroten.
* Niet-beschikbare of ontbrekende labels toevoegen.


>[!NOTE]
>
>De opleiding slimme markeringen is toepasselijk in een ***beeld-type*** van activa slechts.

## Stappen voor training voor slimme tags

[!DNL Experience Manager] als [!DNL Cloud Service] automatisch de slimme tags genereren voor de op tekst gebaseerde elementen en voor video&#39;s. Als u slimme tags wilt trainen in afbeeldingen, voert u de volgende taken uit:

* [Leer labelmodellen en -richtlijnen](#understand-tag-models-guidelines)
* [Het model trainen](#train-model)
* [Tags toewijzen aan digitale elementen](#tag-assets)
* [Tags en zoekopdrachten beheren](#manage-smart-tags-and-searches)

## Leer labelmodellen en -richtlijnen {#understand-tag-models-guidelines}

Een labelmodel is een groep gerelateerde tags die zijn gekoppeld aan verschillende visuele aspecten van afbeeldingen die worden gecodeerd. Tags hebben betrekking op de duidelijk verschillende visuele aspecten van afbeeldingen, zodat de tags, wanneer deze worden toegepast, helpen bij het zoeken naar specifieke typen afbeeldingen. Een schoenenverzameling kan bijvoorbeeld verschillende tags hebben, maar alle tags zijn gerelateerd aan schoenen en kunnen tot hetzelfde tagmodel behoren. Wanneer de labels worden toegepast, kunt u verschillende soorten schoenen vinden, bijvoorbeeld op basis van ontwerp of gebruik.

Voordat u een tagmodel maakt en de service traint, moet u een set unieke tags identificeren die de objecten in de afbeeldingen het beste beschrijven in de context van uw bedrijf. Zorg ervoor dat de activa in uw gekrulde reeks aan [&#x200B; de opleidingsrichtlijnen &#x200B;](#training-guidelines) bevestigen.

### Richtlijnen voor training {#training-guidelines}

Zorg ervoor dat de afbeeldingen in de trainingsset voldoen aan de volgende richtlijnen:

<table>
   <tr>
      <th> Metrisch </th>
      <th> Beschrijving </th>
   </tr>
   <tr>
      <td> <b> Hoeveelheid en grootte </b></td>
      <td> Minimaal 10 en maximaal 50 afbeeldingen per tag. </td>
   </tr>
   <tr>
      <td> <b> Coherence </b> </td>
      <td> Zorg ervoor dat de afbeeldingen voor een tag visueel op elkaar lijken. U kunt de tags met betrekking tot dezelfde visuele aspecten (zoals hetzelfde type objecten in een afbeelding) het beste aan één tagmodel toevoegen. Bijvoorbeeld, is het geen goed idee om elk van deze beelden als <i> mijn-partij </i> (voor opleiding) te etiketteren omdat zij niet visueel gelijkaardig zijn. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/coherence.png"><br><i> Cijfer: Illustratieve beelden van Coherence om de richtlijnen voor opleiding </i> te illustreren
      </td>
   </tr>
   <tr>
      <td> <b> Coverage </b></td>
      <td> De beelden in de training moeten voldoende uiteenlopend zijn. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat de lessen zich kunnen richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen. Bijvoorbeeld, voor de markering <i> model-onderstel </i>, omvat meer opleidingsbeelden gelijkend op het benadrukte beeld hieronder voor de dienst om gelijkaardige beelden nauwkeuriger tijdens het etiketteren te identificeren.</td>
   </tr>
   <tr>
   <td colspan="2"> <img src="assets/do-not-localize/coverage_1.png"><br><i> Cijfer: Illustratieve beelden van Dekking om de richtlijnen voor opleiding </i> te illustreren
   </td>
   </tr>
   <tr>
      <td><b> Vervorming/belemmering </b> </td>
      <td> De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp). Bijvoorbeeld, voor de markering <i> casual-shoe </i>, is het tweede beeld geen goede opleidingskandidaat. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/distraction.png"><br><i> Cijfer: Illustratieve beelden van Vervorming/belemmering om de richtlijnen voor opleiding </i> uit te breiden
      </td>
   </tr>
   <tr>
      <td> <b> Voltooiing </b> </td>
      <td> Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Als het bijvoorbeeld gaat om tags zoals <i>regenjas</i> en <i>modelweergave</i>, voegt u beide tags toe aan de desbetreffende asset voordat u dit opneemt voor training. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/completeness.png"><br><i> Cijfer: Illustratieve beelden van Volledigheid om de richtlijnen voor opleiding </i> uit te breiden
      </td>
   </tr>
   <tr>
      <td> <b> Aantal markeringen </b> </td>
      <td> Adobe raadt u aan een model op te leiden met ten minste twee verschillende tags en ten minste tien verschillende afbeeldingen voor elke tag. Voeg in één tagmodel niet meer dan 50 tags toe. </td>
   </tr>
   <tr>
      <td> <b> Aantal voorbeelden </b> </td>
      <td> Voeg voor elke tag ten minste tien voorbeelden toe. Adobe beveelt echter ongeveer 30 voorbeelden aan. Er worden maximaal 50 voorbeelden per tag ondersteund. </td>
   </tr>
   <tr>
      <td> <b> Prevent valse positieven en conflicten </b> </td>
      <td> Adobe raadt u aan één tagmodel te maken voor één visueel aspect. Structuur de labelmodellen zodanig dat overlappende codes tussen de modellen worden voorkomen. Bijvoorbeeld, gebruik geen gemeenschappelijke markeringen zoals <i> sneakers </i> in twee verschillende namen van markeringsmodellen <i> schoenen </i> en <i> schoeisel </i>. Het trainingsproces overschrijft het ene getrainde tagmodel met het andere voor een algemeen trefwoord. </td>
   </tr>
</table>

**Voorbeelden**: Sommige meer voorbeelden voor begeleiding zijn:

* Maak een tagmodel dat alleen het volgende bevat:

   * De labels die betrekking hebben op automodellen.
   * De labels hadden betrekking op hoesjes voor volwassenen en kinderen.

* Niet maken,

   * Een labelmodel dat automodellen bevat die in 2019 en 2020 zijn uitgebracht.
   * Meerdere labelmodellen met dezelfde paar automodellen.

>[!NOTE]
>
>U kunt dezelfde afbeeldingen gebruiken om verschillende tagmodellen te trainen. Koppel een afbeelding echter niet aan meerdere tags in een labelmodel. U kunt dezelfde afbeelding labelen met verschillende tags die bij verschillende labelmodellen horen.
>U kunt de training niet ongedaan maken. Aan de hand van de bovenstaande richtlijnen kunt u goede afbeeldingen kiezen om te trainen.

## Het model trainen voor uw douanetags {#train-model}

Voer de volgende stappen uit om een model voor uw bedrijfsspecifieke tags te maken en op te leiden:

1. Maak de benodigde labels en de juiste codestructuur. Upload de relevante afbeeldingen in de DAM-opslagplaats.
1. Open [!DNL Experience Manager Cloud Service] > **[!UICONTROL Assets]** in de **[!UICONTROL Smart Tag Training]** -gebruikersinterface.
1. Klik op **[!UICONTROL Create]**. Geef een waarde op **[!UICONTROL Title]** , **[!UICONTROL Description]** .
1. Klik op het mappictogram in het veld **[!UICONTROL Tags]** . Er wordt een pop-upvenster geopend.
1. Zoek of selecteer de juiste tags van de bestaande tags in `cq-tags` die u aan het model wilt toevoegen. Klik op **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >U kunt de codestructuur in oplopende of aflopende volgorde sorteren op basis van de datum **[!UICONTROL Name]** (alfabetische volgorde), **[!UICONTROL Created]** date of **[!UICONTROL Modified]** .


1. Klik in het dialoogvenster **[!UICONTROL Select Assets]** op **[!UICONTROL Add Assets]** voor elke tag. Zoek in de DAM-opslagplaats of blader door de opslagplaats om ten minste 10 en ten hoogste 50 afbeeldingen te selecteren. Selecteer elementen en niet de map. Als u de afbeeldingen hebt geselecteerd, klikt u op **[!UICONTROL Select]** .

   ![&#x200B; de opleidingsstatus van de Mening &#x200B;](assets/smart-tags-training-status.png)

1. Als u een voorvertoning van de miniaturen van de geselecteerde afbeeldingen wilt weergeven, klikt u op de accordeon vóór een tag. U kunt de selectie wijzigen door op **[!UICONTROL Add Assets]** te klikken. Klik op **[!UICONTROL Submit]** als u tevreden bent met de selectie. In de gebruikersinterface wordt onder aan de pagina een melding weergegeven dat de training wordt gestart.
1. Controleer de status van de training in de kolom **[!UICONTROL Status]** voor elk tagmodel. Mogelijke statussen zijn [!UICONTROL Pending] , [!UICONTROL Trained] en [!UICONTROL Failed] .

![&#x200B; Werkschema om het etiketteren model voor Slimme Markeringen te trainen &#x200B;](assets/smart-tag-model-training-flow.png)

*Cijfer: Stappen van het opleidingswerkschema om het etiketteren model te trainen.*

### Trainingsstatus en rapport weergeven {#training-status}

Als u wilt controleren of de service Slimme tags is opgeleid voor uw tags in de trainingsset met elementen, raadpleegt u het workflowrapport voor training in de rapportconsole.

1. Ga in de [!DNL Experience Manager Cloud Service] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]** .
1. Klik op **[!UICONTROL Asset Reports]** op de pagina **[!UICONTROL Create]** .
1. Selecteer het rapport **[!UICONTROL Smart Tags Training]** en klik vervolgens op **[!UICONTROL Next]** op de werkbalk.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk om het rapport weer te geven.
1. Bekijk de details van het rapport. Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de service Slimme tags is getraind voor de tag. Gele kleur geeft aan dat de service gedeeltelijk is opgeleid voor een bepaalde tag. Als u de service volledig wilt trainen voor een tag, voegt u meer afbeeldingen met de desbetreffende tag toe en voert u de trainingsworkflow uit. Als dit rapport uw tags niet bevat, voert u de trainingsworkflow opnieuw uit voor deze tags.Tags
1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een spreadsheet.

>[!NOTE]
>
>Wat gebeurt er als ik de training Slimme tags van de ene instantie naar de andere wil overbrengen via een exportbewerking?
>U hoeft de training Slimme tags niet te exporteren als de omgeving tot dezelfde IMS org behoort. Deze wordt automatisch gedeeld. Als de omgeving zich in verschillende IMS-organisaties bevindt, is het niet mogelijk om training voor slimme tags te delen of te exporteren.

## Beperkingen en aanbevolen procedures met betrekking tot slimme tags {#limitations-smart-tags-training}

* Gebruik de meest geschikte afbeeldingen om het model op te leiden. De training kan niet worden teruggezet of het trainingsmodel kan niet worden verwijderd. De nauwkeurigheid van de tags is afhankelijk van de huidige training, dus doe dit zorgvuldig.
* U kunt de service die slimme tags toepast op video&#39;s niet trainen met behulp van specifieke video&#39;s. Dit werkt met de standaardinstellingen van [!DNL Adobe AI] .


>[!NOTE]
>
>Of u met slimme tags op uw tags kunt trainen en deze kunt toepassen op andere afbeeldingen, is afhankelijk van de kwaliteit van de afbeeldingen die u gebruikt voor training.
>Voor de beste resultaten raadt Adobe aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.
