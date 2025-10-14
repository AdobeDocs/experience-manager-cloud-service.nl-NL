---
title: Hoe kunnen we metagegevens voor AEM Forms beheren?
description: Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.
feature: Adaptive Forms, Foundation Components
exl-id: 8527246a-37f0-4d43-a49e-1c76c265514e
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 0%

---

# Metagegevens van een adaptief formulier toevoegen, verwijderen of bewerken {#manage-form-metadata}

>[!NOTE]
>
> De Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/creating-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/manage-form-metadata.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.

[!DNL AEM Forms] biedt standaard een gedefinieerde set metagegevens voor elk elementtype. Naast de standaardmetagegevens kunt u ook aangepaste metagegevens toevoegen aan elk elementtype. [!DNL AEM Forms] biedt u ook de juiste middelen om al deze metagegevens efficiënt voor uw formulieren te maken, beheren en uit te wisselen.

<!-- If you are a developer or a site owner, you can customize Forms Portal, the end-user interface for [!DNL AEM Forms] to reflect the metadata you are using in your organization. For more information abouts Forms Portal, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md). -->

## Metagegevens in [!DNL AEM Forms] {#metadata-in-aem-forms}

In [!DNL AEM Forms] hangt de lijst met metagegevenseigenschappen die aan een element zijn gekoppeld af van het type. Als u bovendien een aangepaste eigenschap voor metagegevens toevoegt, wordt deze toegevoegd aan alle elementen van het type waarop de aangepaste metagegevens zijn toegevoegd.

### Elementen {#asset-types}

De volgende elementtypen worden ondersteund in [!DNL AEM Forms] :

* Formuliersjablonen (XFA-formulieren)
* PDF forms
* Document (platte PDF)
* Adaptieve Forms
* Forms-gegevensmodel
* XFS

#### Uitgebreide lijst met metagegevens {#extensive-list-of-metadata}

Hieronder volgt een uitgebreide lijst met metagegevenseigenschappen die worden ondersteund in [!DNL AEM Forms] :

<table>
 <tbody> 
  <tr> 
   <td><strong>Eigenschapnaam</strong></td> 
   <td><strong>Type element</strong></td> 
   <td><strong> Beschrijving </strong><br /> </td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Alles behalve bron</td> 
   <td>De naam van de vertoning van de activa.<br /> </td> 
  </tr> 
  <tr> 
   <td>Beschrijving</td> 
   <td>Alles behalve bron</td> 
   <td>Beschrijving van het actief. De gebruiker kan deze waarde specificeren.<br /> </td> 
  </tr> 
  <tr> 
   <td>Type</td> 
   <td>Alles</td> 
   <td><p>Een alleen-lezen waarde die het type element aangeeft. Deze kan een van de volgende waarden hebben:</p> 
    <ul> 
     <li>Formuliersjabloon</li> 
     <li>PDF-formulier, PDF-formulier (Acrobat) of PDF-formulier (ondertekend)</li> 
     <li>Document, document (ondertekend)</li> 
     <li>Adaptief formulier</li> 
     <li>Formuliergegevensmodel (FDM)</li>
     <li>Bron</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Gemaakt</td> 
   <td>Alles</td> 
   <td>Een alleen-lezen waarde die de tijd van het maken van het element aangeeft.</td> 
  </tr> 
  <tr> 
   <td>Laatste wijzigingsdatum</td> 
   <td>Alles</td> 
   <td>Een alleen-lezen waarde die de tijd aangeeft waarop het element voor het laatst is gewijzigd.</td> 
  </tr> 
  <tr> 
   <td>Auteur</td> 
   <td>Alles behalve bron</td> 
   <td><p>Een alleen-lezen waarde die automatisch wordt berekend op basis van het formuliertype.</p> 
    <ul> 
     <li>PDF/Formuliersjabloon/Document - opgehaald uit het geüploade binaire bestand.</li> 
     <li>Adaptief formulier - Wordt bij het maken van het formulier aangemeld bij de gebruiker.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Alles behalve bron</td> 
   <td><p> Een alleen-lezen waarde die een van de volgende statussen van een formulier definieert:</p> 
    <ul> 
     <li>Geen waarde: als een formulier nog nooit is gepubliceerd.</li> 
     <li>Gepubliceerd: wanneer een formulier wordt gepubliceerd.</li> 
     <li>Gewijzigd: wanneer een formulier is gewijzigd nadat het eenmaal is gepubliceerd.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Laatste publicatiedatum</td> 
   <td>Alles behalve bron</td> 
   <td>Een alleen-lezen waarde die aangeeft op welk tijdstip het formulier het laatst is gepubliceerd.</td> 
  </tr> 
  <tr> 
   <td>Publish aan/uit-tijd</td> 
   <td>Alles behalve bron</td> 
   <td><p>Tijdstip waarop het formulier volgens de planning automatisch moet worden gepubliceerd/gepubliceerd. De gebruiker stelt deze waarde in bij het bewerken van metagegevens.</p> 
    <ul> 
     <li>Zowel Publish Aan als Uit moet langer zijn dan de huidige datum. </li> 
     <li>Publish Off time dient na publicatie On time te zijn. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>URL verzenden</td> 
   <td><p>Formuliersjabloon</p> <p>PDF-formulier</p> </td> 
   <td><p>Een door de gebruiker opgegeven URL configureren voor het verzenden van formuliergegevens naar een servlet.</p> <p>Verzenden van URL kan worden geconfigureerd met een van de volgende methoden, vermeld in volgorde van prioriteit:</p> 
    <ul> 
     <li>Geef een verzend-URL rechtstreeks op in een formuliersjabloon met de knop HTTP verzenden tijdens het maken van een XFA-formulier in AEM Forms Designer.</li> 
     <li>Selecteer in de gebruikersinterface van AEM Forms een formulier en geef een verzendURL op bij het bewerken van de eigenschappen van metagegevens.</li> 
     <!-- <li>In Forms Portal, edit the Search &amp; Lister component and specify a submit URL under the Form Link tab.</li> -->
    </ul> </td> 
  </tr> 
  <tr> 
   <td>HTML-renderprofiel</td> 
   <td>Formuliersjabloon</td> 
   <td>Het HTML-renderprofiel dat wordt gebruikt bij het renderen van een formuliersjabloon in HTML-indeling.</td> 
  </tr> 
  <tr> 
   <td>Renderindeling</td> 
   <td><p>Formuliersjabloon</p> <p>Adaptief formulier</p> </td> 
   <td><p>Met deze optie kan de gebruiker de renderindeling van het formulier opgeven wanneer de formulieren worden gepubliceerd:</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>Beide</li> 
    </ul> <p>Deze optie wordt gebruikt om de weergave-indeling van de formulieren alleen te beperken op de portal Formulieren waar ze zichtbaar zijn voor de gebruiker.</p> </td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>Alles behalve bron</td> 
   <td>Labels die aan het formulier zijn gekoppeld, zodat u snel en gemakkelijk kunt zoeken.</td> 
  </tr> 
  <tr> 
   <td>Verwijzingen</td> 
   <td><p>Adaptief formulier</p> <p>Formuliersjabloon</p> <p>Bron</p> </td> 
   <td><p>Lijst met elementen (andere formulieren of bronnen) waarmee dit formulier is gerelateerd. Deze activa kunnen in de volgende twee categorieën vallen:</p> 
    <ul> 
     <li>Zie: Assets waarnaar het huidige formulier verwijst.</li> 
     <li>Verwezen door: Assets die naar het huidige element verwijzen.</li> 
    </ul> <p>Deze activa worden getoond als verbindingen en hun meta-gegevens kunnen direct worden betreden door hen te klikken.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Selectie van formuliermodel (XDP/XSD)</td> 
   <td>Adaptief formulier</td> 
   <td><p>Hiermee geeft u aan welk formuliermodel wordt gebruikt bij het ontwerpen van het adaptieve formulier. Deze eigenschap kan de volgende waarden hebben:</p> 
    <ul> 
      <li>Formuliergegevensmodel (FDM)</li>
      <li>Schema: een XML van het JSON-schema</li>
     <!-- <li>Form template: A form template is selected from the ones existing in the repository. This value can be updated.</li> 
     <li>XML schema: An XSD file is uploaded. This value can be updated.</li> -->
     <li>Geen</li> 
    </ul> 
    <div>
      Een formuliermodel dat is geselecteerd, kan worden bijgewerkt, maar niet worden verwijderd. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Metagegevens van formulieren weergeven {#view-form-metadata}

Assets heeft bestaande eigenschapswaarden die kunnen worden weergegeven in de alleen-lezen modus. Deze metagegevens zijn afkomstig bij het uploaden van het formulier of het maken van het formulier.

1. Navigeer naar de locatie van het element waarvan u de metagegevens wilt weergeven.

1. Open de eigenschappenpagina op een van de volgende manieren:

   * Klik het **[!UICONTROL Properties]** ![&#x200B; pictogram van Eigenschappen &#x200B;](assets/Smock_Info_18_N.svg) van Snelle Acties.

     >[!NOTE]
     >
     >Snelle acties zijn de actiepunten die over een duimnagel worden getoond wanneer de muiswijzer.

   * Selecteer de vorm en klik het **[!UICONTROL Properties]** ![&#x200B; Eigenschappen &#x200B;](assets/Smock_Info_18_N.svg) pictogram dat in de toolbar verschijnt.
   * Navigeer naar de pagina met formulierdetails door op de miniatuur van het formulier te klikken wanneer u niet in de selectiemodus werkt. Nu, klik het ![&#128279;](assets/Smock_Info_18_N.svg) oogpictogram van Eigenschappen 0&rbrace; &lbrace;op het hogere recht, en klik dan Eigenschappen in de lijst onder het.

1. De bezitspagina die opent toont een schema dat slechts die meta-gegevenseigenschappen bevat die één of andere waarde houden.

   <!-- The properties page has a toolbar containing two action icons:

    * Edit: ![Edit](assets/Smock_Edit_18_N.svg) Edit the metadata property values
    * View: ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) Navigate to the form details page, which opens the form in the preview mode. -->

   Het inhoudgedeelte wordt in twee delen verdeeld:

   * Het linkerdeelvenster bevat een miniatuur van het formulier
   * Het rechterdeelvenster bevat eigenschappen van metagegevens in de alleen-lezen modus, verdeeld over verschillende tabbladen.

## Waarden van metagegevens van formulieren toevoegen/bijwerken {#add-update-form-metadata-values}

U kunt de waarde van bestaande eigenschappen van metagegevens bewerken of nieuwe waarden toevoegen aan een bestaand veld voor eigenschappen van metagegevens (bijvoorbeeld wanneer een metagegevensveld leeg is).

<!-- ### Update metadata property values {#update-metadata-property-values}

1. Follow the steps mentioned in the previous section to open the properties page where existing metadata of the selected form can be viewed.  

1. From the toolbar, click the Edit icon ![Edit](assets/Smock_Edit_18_N.svg) to change the mode of the page from read-only to read/write.  

1. The properties page that opens holds a schema that contains a mix of editable input fields and static text.  

1. The properties displayed in static text are the ones that you cannot edit.  

1. You can navigate to other tabs to find input fields for metadata properties placed under them.

   This page has a toolbar containing two action icons different from those in view mode:

    * Cancel: ![aem6forms_close](assets/aem6forms_close.svg_w24.png) Cancel any changes made to metadata property values so far
    * Done: ![aem6forms_check](assets/aem6forms_check.png) Save all the changes made to metadata property values so far

   Both these actions direct the user back to read-only mode of the properties page containing the updated values.-->

### De miniatuur van het formulier bijwerken {#update-the-form-thumbnail}

In het linkerdeelvenster op de pagina Eigenschappen wordt de miniatuur van het formulier weergegeven. Standaard wordt de miniatuur weergegeven die wordt gegenereerd bij het maken van het formulier (adaptief formulier) of bij het uploaden van het formulier.

Voor alle formuliertypen kunt u een afbeelding uploaden door op **[!UICONTROL Upload Image]** te klikken en naar een afbeeldingsbestand in de lokale map te bladeren. De geselecteerde afbeelding wordt gebruikt als een miniatuur in plaats van de standaardafbeelding.

Voor Adaptive Forms is een extra functionaliteit beschikbaar waarmee de gebruiker een miniatuur kan genereren als momentopname van de huidige adaptieve voorvertoning van formulieren. Aangezien [!DNL AEM Forms] ook ondersteuning biedt voor het ontwerpen van Adaptief Forms, kan het voorbeeld van het Adaptief formulier elke keer dat u het Adaptief formulier wijzigt, veranderen. Met deze functie voor het genereren van een miniatuur krijgt u een nieuwe miniatuur voor het adaptieve formulier op basis van de huidige voorbeeldstatus. Klik op **[!UICONTROL Generate Preview]** om deze handeling uit te voeren.

>[!NOTE]
>
>* Gebruik een vierkante afbeelding voor de miniatuur. Wanneer u een niet-vierkante afbeelding gebruikt en de miniatuur in de lijstweergave weergeeft, wordt de miniatuur afgekapt weergegeven.
>* Nadat een nieuwe afbeelding is geüpload of gegenereerd, wordt de miniatuur vervangen door deze afbeelding en kan deze niet opnieuw worden ingesteld op de vorige afbeelding.
>

## Aangepaste metagegevens toevoegen {#add-custom-metadata}

Naast de metagegevens die in het vak worden weergegeven, ondersteunt [!DNL AEM Forms] nieuwe aangepaste metagegevens.

Er is een hulpprogramma (de Editor voor metagegevensschema&#39;s) beschikbaar waarmee u het schema voor de indeling van metagegevens kunt definiëren. Dit is de indeling van wat wordt weergegeven op de pagina **[!UICONTROL Properties]** van een formulier. Met de Metagegevensschemaeditor kunt u een aangepast schema voor uw elementen toevoegen of wijzigen.

[!DNL AEM Forms] geeft informatie over de metagegevensschema&#39;s van de ondersteunde formuliertypen in dit gereedschap. Op deze manier hebt u toegang tot deze schema&#39;s en kunt u aangepaste eigenschappen toevoegen met gebruik van de functionaliteit in de editor voor het metagegevensschema.

### Navigeren door de editor voor het metagegevensschema {#navigate-the-metadata-schema-editor}

1. Navigeer naar **[!UICONTROL Tools > Assets > Metadata Schemas]** .

1. Klik op **[!UICONTROL forms]** in de lijst met schemaformulieren.

1. Klik in de lijst die wordt geopend op het elementtype waarvoor u aangepaste metagegevens wilt toevoegen.

   >[!NOTE]
   >
   >Deze schema&#39;s bevatten eigenschappen van meta-gegevens die buiten doos worden verstrekt en moeten niet worden veranderd/worden uitgegeven (het selecteren van controledoos en het klikken geeft van toolbar uit) om functionele kwesties te vermijden.

1. Elk type element waarop u klikt, opent een lijst met de optie `extendedmetadata` . Bewerk dit schema.

1. Selecteer checkbox naast `extendedmetadata` en klik dan uitgeven ![&#x200B; &#x200B;](assets/Smock_Edit_18_N.svg) pictogram dat in de toolbar verschijnt.

1. [!DNL AEM Forms] opent de editor/formulierbuilder voor het metagegevensschema van het geselecteerde elementtype (in dit geval Adaptief formulier).

   Metagegevenseditor

   1. Het linkerdeelvenster bevat secties met tabbladen waarin de velden zijn geplaatst en in het rechterdeelvenster worden alle beschikbare UI-componenten en de eigenschappen van het veld weergegeven die in het linkerdeelvenster zijn geselecteerd.

   1. De vergrendelde sectie kan niet worden bewerkt en bevat velden voor alle metagegevenseigenschappen die in het vak worden opgegeven.

   1. U kunt extra tabbladen toevoegen door op het plus-symbool te klikken.

   1. U kunt een aangepast veld van het gewenste type toevoegen door de veldcomponent van de sectie **[!UICONTROL Build Form]** naar de schemapagina te slepen.
   1. U kunt de specificaties voor dit veld opgeven in de sectie **[!UICONTROL Settings]** nadat u op het veld hebt geklikt.

### Aangepaste metagegevenseigenschap toevoegen in schema-editor {#add-custom-metadata-property-in-schema-editor}

1. Navigeer naar het tabblad (bestaand of nieuw) waar u de aangepaste eigenschap wilt toevoegen.

1. Sleep een component van het gewenste type van de **[!UICONTROL Build Form]** sectie aan linkerpaneel en plaats bij een geschikte plaats.

   >[!NOTE]
   >
   >U kunt de vergrendelde secties niet verplaatsen, maar u kunt de component in een van de lege ruimten plaatsen.

1. Klik op een component die u net hebt gesleept. Vul op het tabblad Instellingen dat in het rechterdeelvenster wordt geopend de gegevens in voor de volgende velden:

   1. Geef een veldlabel op dat als een weergavenaam boven het veld in het schema moet worden gebruikt (bijvoorbeeld: Department)
   1. Onder Kaart aan bezitsgebied, kunt u een vooraf ingevulde waarde zien **&#39;./jcr:content/metadata/default&#39;**. Verander het &quot;**gebrek**&quot;in een gewenste bezitsnaam, die wordt gebruikt om het bezit in crx bewaarplaats (bijvoorbeeld: &quot;./jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >Wijzig het voorvoegsel &#39; niet./jcr:content/metadata/&#39; zoals deze het pad definieert waar de eigenschap wordt opgeslagen.
      >
      >De eigenschapsnaam moet ook uniek zijn om te voorkomen dat waarden worden geschreven voor twee of meer eigenschappen op dezelfde locatie in de opslagplaats. Het wordt daarom aanbevolen de waarde &#39;default&#39; te wijzigen.

   1. Vul andere instellingen in op basis van vereisten. Selecteer bijvoorbeeld de optie Vereist als u het veld verplicht wilt maken.
   1. Om een gebied te schrappen u toevoegde, selecteer het gebied en klik dan schrapping ![&#x200B; schrap &#x200B;](assets/Smock_Delete_18_N.svg) pictogram.

1. Voer indien nodig stap 1-3 uit om een andere eigenschap toe te voegen.
1. Klik op **[!UICONTROL Save]** nadat u alle wijzigingen hebt aangebracht.

   U hebt een aangepaste eigenschap voor metagegevens toegevoegd.

Alle Adaptive Forms in [!DNL AEM Forms] bevatten nu deze extra eigenschap voor metagegevens. U kunt het van de eigenschappen pagina uitgeven.


## Zie ook {#see-also}

{{see-also}}