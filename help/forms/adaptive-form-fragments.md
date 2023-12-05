---
title: Hoe te om Aangepaste Fragmenten van de Vorm tot stand te brengen en te gebruiken?
description: Formulierfragment is een modulair en herbruikbaar onderdeel van een formulier. Leer formulierfragmenten te maken en deze in verschillende formulieren opnieuw te gebruiken voor een efficiënte formulierverzameling.
uuid: bb4830b5-82a0-4026-9dae-542daed10e6f
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 1a32eb24-db3b-4fad-b1c7-6326b5af4e5e
docset: aem65
exl-id: e4d8bcb9-ce1f-425e-b35c-d0a79fa771f3
source-git-commit: abe5f8a4b19473c3dddfb79674fb5f5ab7e52fbf
workflow-type: tm+mt
source-wordcount: '2122'
ht-degree: 0%

---

# Aangepaste Forms-fragmenten maken en gebruiken in een adaptief formulier  {#adaptive-form-fragments}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails, inkomstengegevens enzovoort. Formulierontwikkelaars moeten deze algemene segmenten telkens maken wanneer een nieuw formulier wordt gemaakt. Adaptive Forms biedt een handig mechanisme om slechts eenmaal een formuliersegment als een deelvenster of een groep velden te maken en deze opnieuw te gebruiken in Adaptive Forms. Deze herbruikbare en standalone segmenten worden de Adaptieve Fragmenten van de Vorm genoemd.


## Een fragment maken {#create-a-fragment}

U kunt een adaptief formulierfragment helemaal opnieuw maken of een deelvenster in een bestaand adaptief formulier opslaan als fragment.

### Geheel fragment maken {#create-fragment-from-scratch}

1. Aanmelden [!DNL AEM Forms] auteur-instantie op https://[*hostnaam*]:[*poort*]/aem/forms.html.
1. Klikken **Maken > Adaptief formulierfragment**.
1. Geef een titel, naam, beschrijving en tags voor het fragment op.

   >[!NOTE]
   >
   >Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er al een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.

1. Klik om het dialoogvenster **Formuliermodel** en van de **Selecteren uit** selecteert u een van de volgende modellen voor het fragment:

   * **Geen**: Hiermee geeft u op het fragment helemaal opnieuw te maken zonder een formuliermodel te gebruiken.

     >[!NOTE]
     >
     > In Adaptive Forms kunt u één formulierfragment (op basis van kerncomponenten) meerdere keren gebruiken in een formulier. Dit biedt ondersteuning voor formulierfragmenten die zijn gebaseerd op geen en op schema&#39;s gebaseerde fragmenten.

   * **Formuliersjabloon**: geeft aan dat het fragment moet worden gemaakt met behulp van een XDP-sjabloon die is geüpload naar [!DNL AEM Forms]. Selecteer de juiste XDP-sjabloon als het formuliermodel voor het fragment.

   ![Een adaptief formulier maken met de formuliersjabloon als model](assets/form-template-model.png)

   De subformulieren die als fragmenten zijn gemarkeerd in de geselecteerde formuliersjabloon, worden ook weergegeven. U kunt een subformulier voor Adaptief formulierfragment selecteren in de vervolgkeuzelijst.

   ![Subformulieren selecteren uit de opgegeven formuliersjabloon](assets/fragment-subform.png)

   Daarnaast kunt u een adaptief formulierfragment maken met subformulieren die niet zijn gemarkeerd als fragmenten in de formuliersjabloon door de SOM-expressie voor het subformulier op te geven in de vervolgkeuzelijst.

   * **XML-schema**: Geeft op om het fragment te maken met een XML-schema dat is geüpload naar [!DNL AEM Forms]. U kunt een van de beschikbare XML-schema&#39;s uploaden of selecteren als het formuliermodel voor het fragment.

   ![Een adaptief formulierfragment maken op basis van een XML-schema als model](assets/xml-schema-model.png)

   U kunt ook een adaptief formulierfragment maken door in de vervolgkeuzelijst een complexType te selecteren dat aanwezig is in het geselecteerde schema.

   ![Selecteer een complex type van het gespecificeerde het schemamodel van XML](assets/complex-type.png)

1. Klikken **Maken** en klik vervolgens op **Openen** om het fragment met een standaardsjabloon te openen in de bewerkingsmodus.

In de bewerkingsmodus kunt u elke adaptieve formuliercomponent van de AEM naar het fragment slepen en neerzetten. <!-- For information about Adaptive Form components, see Introduction to authoring Adaptive Forms. -->

Als u bovendien een XML-schema of XDP-formuliersjabloon hebt geselecteerd als het formuliermodel voor uw fragment, wordt een nieuw tabblad met de hiërarchie van het formuliermodel weergegeven in de zoeker naar inhoud. Hiermee kunt u formuliermodelelementen naar het fragment slepen en neerzetten. De toegevoegde formuliermodelelementen worden omgezet in formuliercomponenten waarbij de oorspronkelijke eigenschappen van de bijbehorende XDP of XSD behouden blijven.

### Deelvenster opslaan als een fragment {#save-panel-as-a-fragment}

1. Open een adaptief formulier dat het deelvenster bevat dat u wilt opslaan als adaptief formulierfragment.
1. Klik op de werkbalk van het deelvenster op **[!UICONTROL Save as Fragment]**. Het dialoogvenster Opslaan als fragment wordt geopend.

   >[!NOTE]
   >
   >Als het deelvenster dat u opslaat als fragment een onderliggend deelvenster bevat, worden deze opgenomen in het resulterende fragment.

1. Geef in het dialoogvenster Fragment maken de volgende informatie op:

   * **Naam**: Naam van het fragment. De standaardwaarde is de elementnaam van het deelvenster. Het is een verplicht veld.

     >[!NOTE]
     >
     >Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er al een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.

   * **Titel**: Titel van het fragment. De standaardwaarde is de titel van het deelvenster.

   * **Beschrijving**: Beschrijving van het fragment.

   * **Tags**: Hiermee worden metagegevens voor het fragment gecodeerd.

   * **Doelpad**: Pad naar opslagplaats waar het fragment wordt opgeslagen. Als u geen pad opgeeft, wordt een knooppunt met dezelfde naam als het fragment gemaakt naast het knooppunt dat het adaptieve formulier bevat. Het fragment wordt opgeslagen in dit knooppunt.

   * **Formuliermodel**: Afhankelijk van het formuliermodel voor het adaptieve formulier wordt in dit veld het dialoogvenster **XML-schema**, **Formuliersjabloon**, of **Geen**. Het is een niet-bewerkbaar veld.

   * **Hoofdmap** fragmentmodel: verschijnt alleen in op XSD gebaseerde adaptieve vormen. Hiermee geeft u de basis voor het fragmentmodel op. U kunt het XSD-complextype kiezen **** in de vervolgkeuzelijst. U kunt het fragment alleen opnieuw gebruiken in een ander adaptief formulier als u het complexe type selecteert als hoofdknooppunt van het fragmentmodel.
Als u **/** Als hoofdmap van het fragmentmodel is de volledige XSD-structuur van het basismodel zichtbaar op het tabblad Adaptief formuliergegevensmodel. Voor een complexe hoofdmap van een fragmentmodel zijn alleen de onderliggende elementen van het geselecteerde complexe type zichtbaar op het tabblad Adaptief formuliergegevensmodel.

   * **XSD Ref**: wordt alleen weergegeven in adaptieve Forms op basis van XSD. De locatie van het XML-schema wordt weergegeven.

   * **XDP Ref**: wordt alleen weergegeven in adaptieve Forms op basis van XDP. De locatie van de XDP-formuliersjabloon wordt weergegeven.

   ![save-fragment](assets/save-fragment.png)

   Dialoogvenster Opslaan als fragment

1. Klikken **OK**.

   Het deelvenster wordt opgeslagen op de opgegeven of standaardlocatie in de opslagplaats. In het adaptieve formulier wordt het deelvenster vervangen door een opname van het fragment. Zoals hieronder wordt weergegeven, worden het deelvenster Algemene informatie en de onderliggende deelvensters Persoonlijke gegevens en Adres als een fragment opgeslagen.

   Klik op **[!UICONTROL Edit Asset]** in de paneelwerkbalk. Het fragment wordt in de bewerkingsmodus op een nieuw tabblad of in een nieuw venster geopend.

   ![Fragment bewerken](assets/edit-fragment.png)

## Werken met fragmenten {#working-with-fragments}

### Fragmentweergave configureren {#configure-fragment-appearance}

Elk fragment dat u invoegt in Adaptief Forms, wordt weergegeven als een voorlopige afbeelding. De plaatsaanduiding bevat titels van maximaal tien onderliggende deelvensters in het fragment. U kunt [!DNL AEM Forms] om het volledige fragment weer te geven in plaats van de voorlopige afbeelding.

Voer de volgende stappen uit om volledige fragmenten in formulieren weer te geven:

1. Ga naar AEM webconsoleconfiguratiepagina op https:[*host*]:[*poort*]/system/console/configMgr.

1. Zoeken en klikken **[!UICONTROL Adaptive Form Configuration Service]** openen in bewerkingsmodus.
1. Uitschakelen **[!UICONTROL Enable Placeholder in place of Fragment]** Schakel dit selectievakje in om volledige fragmenten te tonen in plaats van de voorlopige afbeelding.

### Een fragment invoegen in een adaptief formulier {#insert-a-fragment-in-an-adaptive-form}

De adaptieve formulierfragmenten die u maakt, worden weergegeven op het tabblad Adaptieve formulierfragmenten van de zoeker AEM inhoud. Een adaptief formulierfragment invoegen in een adaptief formulier:

1. Open het adaptieve formulier in de bewerkingsmodus waarin u een adaptief formulierfragment wilt invoegen.
1. Klikken **Activa** ![assets-browser](assets/assets-browser.png) in de zijbalk. Selecteer in de middelenbrowser de optie **Adaptieve formulierfragmenten** in de vervolgkeuzelijst.

   U kunt er ook voor kiezen om alle adaptieve formulierfragmenten of filters weer te geven op basis van het formuliermodel (Formuliersjabloon, XML-schema of Standaard).

1. Sleep een adaptief formulierfragment naar de adaptieve vorm.

   >[!NOTE]
   >
   >Het adaptieve formulierfragment is niet ingeschakeld voor ontwerpen vanuit het Adaptieve formulier. Bovendien kunt u een op XSD gebaseerde fragment niet gebruiken in een op JSON gebaseerde adaptieve vorm en omgekeerd.

Het adaptieve formulierfragment wordt als referentie ingevoegd in het adaptieve formulier en wordt gesynchroniseerd met het op zichzelf staande adaptieve formulierfragment. Dit betekent dat wanneer u het adaptieve formulierfragment bijwerkt, de wijzigingen worden doorgevoerd in alle adaptieve vormen waar het fragment wordt gebruikt.

### Een fragment insluiten in Adaptieve vorm {#embed-a-fragment-in-adaptive-form}

U kunt een adaptief formulierfragment insluiten in een adaptief formulier door op **Element insluiten: &lt;*fragmentName*>** op de paneelwerkbalk van het toegevoegde fragment, zoals in de volgende voorbeeldafbeelding wordt getoond.

![Een formulierfragment insluiten in adaptieve vorm](assets/embed-fragment.png)

>[!NOTE]
>
>Het ingesloten fragment is niet meer gekoppeld aan het zelfstandige fragment. U kunt de componenten in het ingesloten fragment bewerken vanuit het adaptieve formulier.

### Fragmenten in fragmenten gebruiken {#using-fragments-within-fragments}

U kunt geneste adaptieve formulierfragmenten maken, wat betekent dat u een fragment naar een ander fragment kunt slepen en neerzetten en dat u een geneste fragmentstructuur kunt hebben.

### Fragmenten wijzigen {#change-fragments}

U kunt een adaptief formulierfragment vervangen of wijzigen door een ander fragment met de opdracht **Fragmentelement selecteren** in het dialoogvenster Component bewerken voor een deelvenster Adaptief formulierfragment.

### Een formulierfragment meerdere keren gebruiken in een adaptief formulier {#using-form-fragment-mutiple-times-in-af}

U kunt een formulierfragment op basis van een schema meerdere keren gebruiken in een adaptief formulier om gegevens uniek op te slaan voor elk formulierfragmentveld. U kunt bijvoorbeeld een fragment van een adresformulier gebruiken om adresgegevens te verzamelen voor permanente communicatie en het weergeven van levende adressen in een aanvraagformulier voor een lening.

![meerdere fragmenten gebruiken in adaptieve vorm](/help/forms/assets/using-multiple-fragment-af.gif)

>[!NOTE]
>
> Als u op geen gebaseerde formulierfragmenten meerdere keren in een adaptief formulier gebruikt, treedt er een probleem op met gegevenssynchronisatie tussen de velden van de fragmenten. U kunt een op een [kerncomponent gebaseerde formulierfragment](/help/forms/adaptive-form-fragments-core-components.md) dat niet is gekoppeld aan een formuliergegevensmodel, meerdere keren in een formulier gebruiken zonder problemen met gegevenssynchronisatie te ondervinden.

## Automatische toewijzing van fragmenten voor gegevensbinding {#auto-mapping-of-fragments-for-data-binding}

Wanneer u een adaptief formulierfragment maakt met een XFA-formuliersjabloon of een XSD-complex type en het fragment naar een Adaptief formulier sleept, wordt het XFA-fragment of het XSD-complexe type automatisch vervangen door het overeenkomstige Adaptieve formulierfragment waarvan de basis van het fragmentmodel is toegewezen aan het XFA-fragment of het XSD-complexe type.

U kunt het fragmentmiddel en de bindingen ervan wijzigen in het dialoogvenster Component bewerken.

>[!NOTE]
>
>U kunt ook een gebonden adaptief formulierfragment uit de bibliotheek Adaptief formulierfragment in AEM Content Finder slepen en de juiste bindverwijzing weergeven vanuit het dialoogvenster Component bewerken van het deelvenster Fragment van adaptieve vorm.

## Fragmenten beheren {#manage-fragments}

U kunt verschillende bewerkingen uitvoeren op adaptieve formulierfragmenten met de opdracht [!DNL AEM Forms] UI.

1. Ga naar `https://[hostname]:'port'/aem/forms.html`.

1. Klikken **Selecteren** in de [!DNL AEM Forms] UI-werkbalk en selecteer een adaptief formulierfragment. De werkbalk bevat de volgende bewerkingen die u kunt uitvoeren op het geselecteerde adaptieve formulierfragment.

<table>
 <tbody>
  <tr>
   <td><p><strong>Bewerking</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Openen</p> </td>
   <td><p>Hiermee opent u het geselecteerde adaptieve formulierfragment in de bewerkingsmodus.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Eigenschappen weergeven</p> </td>
   <td><p>Hiermee opent u het deelvenster Eigenschappen. In het deelvenster Eigenschappen kunt u eigenschappen weergeven en bewerken, een voorvertoning genereren en een miniatuurafbeelding voor het geselecteerde fragment uploaden. Zie <a href="manage-form-metadata.md" target="_blank">Metagegevens</a> beheren voor meer informatie.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Kopiëren</p> </td>
   <td><p>Hiermee kopieert u het geselecteerde fragment. De knop Plakken wordt op de werkbalk weergegeven.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Downloaden</p> </td>
   <td><p>Het geselecteerde fragment downloaden.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Voorvertoning</p> </td>
   <td><p>Hiermee kunt u een voorbeeld van het fragment weergeven als een HTML of aangepaste voorvertoning door gegevens uit een XML-bestand samen te voegen met het fragment. <!-- For more information, see <a href="previewing-forms.md" target="_blank">Previewing a form</a>.<br /> <br /> --></p> </td>
  </tr>
  <tr>
   <td><p>Revisie starten/Revisie beheren</p> </td>
   <td><p>Hiermee kunt u een revisie van het geselecteerde fragment starten en beheren. <!-- For more information, see <a href="create-reviews-forms.md" target="_blank">Creating and managing reviews</a>.<br /> <br /> </p> --> </td>
  </tr>
  <tr>
   <td><p>Woordenboek maken</p> </td>
   <td><p>Genereert een woordenboek voor het lokaliseren van het geselecteerde fragment. <!-- For more information, see <a href="lazy-loading-adaptive-forms.md" target="_blank">Localizing Adaptive Forms</a>.<br /> <br /> --> </p> </td>
  </tr>
  <tr>
   <td><p>Publiceren/Publiceren ongedaan maken</p> </td>
   <td><p>Hiermee publiceert u het geselecteerde fragment of maakt u de publicatie ervan ongedaan.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Adaptief formulier met fragmenten lokaliseren {#localizing-adaptive-form-containing-fragments}

Als u een adaptief formulier met adaptieve formulierfragmenten wilt lokaliseren, moet u het fragment en het formulier afzonderlijk lokaliseren. U kunt een fragment één keer lokaliseren en opnieuw gebruiken in meerdere Adaptieve Forms.

>[!NOTE]
>
>De lokalisatietoetsen in het fragment worden niet weergegeven in het XLIFF-bestand voor een adaptief formulier.

## Belangrijke punten die u moet onthouden wanneer u werkt met fragmenten {#key-points-to-remember-when-working-with-fragments}

* Zorg ervoor dat de fragmentnaam uniek is. Het fragment kan niet worden gemaakt als er een bestaand fragment met dezelfde naam bestaat.
* Als u in een op XDP gebaseerd adaptief formulier een deelvenster opslaat als fragment dat een ander XDP-fragment bevat, wordt het resulterende fragment automatisch gebonden aan het onderliggende XDP-fragment. In het geval van een op XSD gebaseerde adaptieve vorm, wordt het resulterende fragment gebonden aan de schemawortel.
* Wanneer u een adaptief formulierfragment maakt, wordt in CRXDe Lite een fragmentknooppunt gemaakt, dat vergelijkbaar is met het knooppunt guideContainer voor een adaptief formulier.
* Een fragment in een adaptief formulier dat een ander formuliergegevensmodel gebruikt, wordt niet ondersteund. Een XDP-fragment wordt bijvoorbeeld niet ondersteund in een XSD-gebaseerd adaptief formulier en omgekeerd.
* Adaptieve formulierfragmenten zijn beschikbaar voor gebruik via het tabblad Adaptieve formulierfragmenten in AEM zoekfunctie.
* Expressies, scripts of stijlen in een zelfstandig adaptief formulierfragment blijven behouden wanneer deze via verwijzing worden ingevoegd of in een adaptief formulier worden ingesloten.
* U kunt een adaptief formulierfragment, dat via verwijzing wordt ingevoegd, niet bewerken vanuit een adaptief formulier. Als u het fragment wilt bewerken, bewerkt u het zelfstandige adaptieve formulierfragment of sluit u het fragment in het adaptieve formulier in.
* Wanneer u een adaptief formulier publiceert, moet u de op zichzelf staande Fragmenten van het adaptieve formulier publiceren die met behulp van een verwijzing zijn ingevoegd in het Adaptieve formulier.
* Wanneer u een bijgewerkt fragment van een adaptieve formulier opnieuw publiceert, worden de wijzigingen doorgevoerd in de gepubliceerde exemplaren van de adaptieve vorm waarin het fragment wordt gebruikt.
* Adaptief formulier dat de component Verifiëren bevat, biedt geen ondersteuning voor anonieme gebruikers. Ook wordt het niet opnieuw aangeraden om de component Verifiëren in een adaptief formulierfragment te gebruiken.
* (**Alleen** Mac) Voeg het volgende item toe aan het bestand /private/etc/hosts om ervoor te zorgen dat de functionaliteit van formulierfragmenten in alle scenario&#39;s perfect werkt:
  `127.0.0.1 <Host machine>` **Hostmachine**: De Apple Mac-machine waarop [!DNL AEM Forms] wordt geïmplementeerd.

<!--
## Reference Fragments {#reference-fragments}

Reference Adaptive Form Fragments that you can use to create your form are available. For more information, see [Reference Fragments](reference-adaptive-form-fragments.md).
-->

>[!MORELIKETHIS]
>
>* [Adaptieve formulierfragmenten in kerncomponenten](/help/forms/adaptive-form-fragments-core-components.md)
