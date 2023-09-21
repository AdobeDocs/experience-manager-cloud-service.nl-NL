---
title: Adaptieve formulierfragmenten
description: Adaptive Forms biedt een mechanisme om een formuliersegment te maken, zoals een deelvenster of een groep velden, zoals het in elk adaptief formulier wordt gebruikt. U kunt een bestaand deelvenster ook opslaan als fragment.
topic-tags: author
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: b3aac0cb7682f66c72c32ebf706f5db4067b12ed
workflow-type: tm+mt
source-wordcount: '1673'
ht-degree: 0%

---


# Adaptieve formulierfragmenten {#adaptive-form-fragments}

<span class="preview"> Dit is een pre-release functie die toegankelijk is via onze [pre-releasekanaal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails en inkomstengegevens. Formulierontwikkelaars moeten deze algemene segmenten telkens maken wanneer een nieuw formulier wordt gemaakt.

Adaptive Forms biedt een handig mechanisme om slechts eenmaal een formuliersegment als een deelvenster of een groep velden te maken en deze opnieuw te gebruiken in Adaptive Forms. Deze herbruikbare en standalone segmenten worden Adaptieve formulierfragmenten genoemd.

Formulierfragmenten worden naadloos geïntegreerd in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

U kunt een fragment meerdere keren aan een document toevoegen en eigenschappen voor gegevensbinding van de componenten gebruiken om het aan verschillende gegevensbronnen of schema te koppelen. U kunt bijvoorbeeld hetzelfde adresfragment gebruiken voor een vast adres, communicatie en factureringsadres en dit koppelen aan verschillende velden van een gegevensbron of schema.

## Een formulierfragment maken {#create-a-fragment}

U kunt een adaptief formulierfragment helemaal zelf maken of een deelvenster in een bestaand adaptief formulier opslaan als fragment. Een formulierfragment maken:

1. Meld u aan bij uw AEM Forms-exemplaar op https://[*hostnaam*]:[*poort*]/aem/forms.html.
1. Klikken **Maken > Adaptief formulierfragment**.
1. Geef een titel, naam, beschrijving en tags voor het fragment op. Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er al een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.
1. Selecteer een formuliersjabloon. U kunt een formulierfragment maken voor Core Components (Basiscomponenten) op basis van adaptieve Forms of Foundation Components (Basiscomponenten) op basis van adaptieve Forms.
   * Als u formulierfragment wilt maken voor formulieren op basis van kerncomponenten, selecteert u een sjabloon op basis van kerncomponenten.
   * Als u formulierfragment wilt maken voor op Foundation Components gebaseerde formulieren, selecteert u een sjabloon voor elementcomponenten. Bijvoorbeeld /libs/fd/af/templateForFragment/defaultFragmentTemplate.

   Wanneer u formulierfragment maakt voor formulieren op basis van kerncomponenten, gebruikt u de optie Formulierthema selecteren om een thema op basis van kerncomponenten te selecteren.

1. Klik om het dialoogvenster **Formuliermodel** en van de **Selecteren uit** selecteert u een van de volgende modellen voor het fragment:

   ![Hiermee geeft u het modeltype weer op het tabblad Formuliermodel](assets/create-af-1-1.png)

   * **Geen**: hiermee geeft u op dat het fragment helemaal opnieuw moet worden gemaakt zonder een formuliermodel te gebruiken.

     >[!NOTE]
     >
     >Een voordeel van op kerncomponenten gebaseerde fragmenten ten opzichte van op stichtingscomponenten gebaseerde fragmenten is de mogelijkheid om meerdere op kerncomponenten gebaseerde fragmenten te gebruiken die niet aan een formuliermodel in één adaptieve vorm zijn gekoppeld.

   * **Schema**: Geeft op om het fragment te maken met een XML- of JSON-schema dat naar AEM Forms is geüpload. U kunt vanuit de beschikbare XML- of JSON-schema&#39;s het formuliermodel voor het fragment uploaden of selecteren. Wanneer u een XML-schema selecteert, kunt u ook een adaptief formulierfragment maken door in het geselecteerde schema een complexType te selecteren in het **[!UICONTROL XML Schema Complex Type]** vervolgkeuzelijst. Wanneer u een JSON-schema selecteert, kunt u ook een adaptief formulierfragment maken door in het geselecteerde schema een schemadefinitie te selecteren in het **[!UICONTROL JSON Schema Definitions]** vervolgkeuzelijst.
   * **Formuliergegevensmodel**: geeft op het fragment te maken met behulp van een formuliergegevensmodel. U kunt een adaptief formulierfragment maken op basis van slechts één gegevensmodelobject in een formuliergegevensmodel. Vervolgkeuzelijst Formuliergegevensmodeldefinities uitvouwen. Hiermee worden alle gegevensmodelobjecten in het opgegeven formuliergegevensmodel weergegeven. Selecteer een gegevensmodelobject in de lijst.

   ![Formuliergegevensmodel](assets/create-af-3.png)



1. Klikken **Maken** en klik vervolgens op **Openen** om het fragment met een standaardsjabloon te openen in de bewerkingsmodus. In de bewerkingsmodus kunt u elke component Adaptief formulier aan het fragment toevoegen.

<!-- For information about Adaptive Form components, see [Introduction to authoring Adaptive Forms](../../forms/using/introduction-forms-authoring.md). --> Als u bovendien een XML-schema of XDP-formuliersjabloon hebt geselecteerd als het formuliermodel voor uw fragment, wordt een nieuw tabblad met de hiërarchie van het formuliermodel weergegeven in de zoeker naar inhoud. Hiermee kunt u formuliermodelelementen naar het fragment slepen en neerzetten. De toegevoegde formuliermodelelementen worden geconverteerd naar formuliercomponenten, terwijl de oorspronkelijke eigenschappen van de gekoppelde XDP of XSD behouden blijven.

Nadat het fragment van het adaptieve formulier is gebaseerd op een schema of formuliergegevensmodel, worden formuliergegevensmodel of schema-elementen weergegeven op het tabblad Gegevensbronnen van de browser Inhoud in de Adaptive Form-editor. U kunt formuliermodelelementen naar de fragment slepen. De toegevoegde formuliermodelelementen worden geconverteerd naar formuliercomponenten met behoud van de oorspronkelijke eigenschappen van het bijbehorende schema.


## Een fragment toevoegen aan een adaptief formulier {#insert-a-fragment-in-an-adaptive-form}

Een fragment van een adaptief formulier toevoegen aan een adaptief formulier:

1. Open het adaptieve formulier in de bewerkingsmodus.
1. Voeg de **component Adaptief formulierfragment** toe aan het formulier.
1. Klik op de knop **Activa** de inhoudbrowser van de zijbalk. Selecteer in de middelenbrowser onder de paden de optie **Adaptieve formulierfragmenten** -optie. Alle Adaptieve Forms-fragmenten die beschikbaar zijn voor uw formulier, worden weergegeven, afhankelijk van het formuliermodel.

   ![Selecteer de optie Aangepaste formulierfragmenten](assets/adaptive-forms-fragments.png)

1. Sleep een adaptief formulierfragment naar de **Adaptief formulierfragment** op uw adaptieve formulier.

   >[!NOTE]
   >
   >Het fragment Adaptief formulier is niet ingeschakeld voor ontwerpen vanuit het adaptieve formulier. Bovendien kunt u een XSD-fragment niet gebruiken in een op JSON gebaseerde adaptieve vorm en omgekeerd.

Het fragment adaptief formulier wordt toegevoegd als verwijzing naar het adaptieve formulier en blijft gesynchroniseerd met het op zichzelf staande fragment van de adaptieve vorm. Dit houdt in dat alle wijzigingen die in het adaptieve formulierfragment worden aangebracht, worden weerspiegeld in alle gevallen waarin het fragment is opgenomen in Adaptief Forms.

### Een fragment insluiten in adaptieve vorm {#embed-a-fragment-in-adaptive-form}

U kunt een adaptief formulierfragment insluiten in een adaptief formulier door te klikken op de knop ![Insluiten](assets/Smock_Import_18_N.svg) pictogram de paneeltoolbar van het toegevoegde fragment

Het ingesloten fragment is niet meer gekoppeld aan het zelfstandige fragment. U kunt de componenten in het ingesloten fragment bewerken vanuit het adaptieve formulier.

<!-- 
## Configure fragment appearance {#configure-fragment-appearance}

Any fragment you insert in Adaptive Forms appears as a placeholder image. The placeholder displays titles of up to a maximum of ten child panels in the fragment. You can configure AEM Forms to show the complete fragment instead of the placeholder image.

Perform the following steps to show complete fragments in forms:

1. Go to AEM web console configuration page at https:[*host*]:[*port*]/system/console/configMgr.

1. Search and click **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** to open it in edit mode.
1. Disable **[!UICONTROL Enable Placeholder in place of Fragment]** checkbox to show complete fragments rather than the placeholder image.

-->

### Fragmenten binnen fragmenten gebruiken {#using-fragments-within-fragments}

U kunt geneste fragmenten van adaptieve vormen maken. Dit betekent dat u een fragment naar een ander fragment kunt slepen en neerzetten en een geneste fragmentstructuur kunt hebben.



## Automatische toewijzing van fragmenten voor gegevensbinding {#auto-mapping-of-fragments-for-data-binding}

Wanneer u een fragment van een adaptieve vorm maakt met een XFA-formuliersjabloon of een XSD-complex type en het fragment naar een Adaptief formulier sleept, wordt het XFA-fragment of het XSD-complexe type automatisch vervangen door het overeenkomstige adaptieve formulierfragment waarvan de basis van het fragmentmodel is toegewezen aan het XFA-fragment of het XSD-complexe type.

U kunt het fragmentmiddel en de bindingen ervan wijzigen in het dialoogvenster Component bewerken.

U kunt ook een gebonden fragment van de adaptieve vorm uit de bibliotheek Adaptief formulierfragment in AEM content finder slepen en de juiste bindverwijzing weergeven in het dialoogvenster Component bewerken van het fragmentdeelvenster Adaptief formulier.

## Fragmenten beheren {#manage-fragments}

U kunt verschillende bewerkingen uitvoeren op Adaptief-formulierfragmenten met de gebruikersinterface van AEM Forms.

1. Ga naar `https://[hostname]/aem/forms.html`.

1. Klikken **Selecteren** in de gebruikersinterface van AEM Forms en selecteer een adaptief formulierfragment. De werkbalk bevat de volgende bewerkingen die u kunt uitvoeren op het geselecteerde adaptieve formulierfragment.

<table>
 <tbody>
  <tr>
   <td><p><strong>Bewerking</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bewerken</p> </td>
   <td><p>Hiermee opent u het geselecteerde adaptieve formulierfragment in de bewerkingsmodus.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Eigenschappen</p> </td>
   <td><p>Hiermee opent u het deelvenster Eigenschappen. In het deelvenster Eigenschappen kunt u eigenschappen weergeven en bewerken, een voorvertoning genereren en een miniatuurafbeelding voor het geselecteerde fragment uploaden. Zie voor meer informatie <a>Metagegevens beheren</a>.<br /> <br /> </p> </td>
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
   <td><p>Hiermee kunt u een voorbeeld van het fragment weergeven als een HTML of aangepaste voorvertoning door gegevens uit een XML-bestand samen te voegen met het fragment. Zie voor meer informatie <a>Een voorbeeld van een formulier bekijken</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Revisie starten/Revisie beheren</p> </td>
   <td><p>Hiermee kunt u een revisie van het geselecteerde fragment starten en beheren. Zie voor meer informatie <a>Revisies maken en beheren</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Woordenboek toevoegen</p> </td>
   <td><p>Genereert een woordenboek voor het lokaliseren van het geselecteerde fragment. Zie voor meer informatie <a>Adaptieve Forms lokaliseren</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publiceren/Publiceren ongedaan maken</p> </td>
   <td><p>Hiermee maakt u het geselecteerde fragment ongedaan.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Belangrijke punten die u moet onthouden wanneer u werkt met fragmenten {#key-points-to-remember-when-working-with-fragments}

* Zorg ervoor dat de fragmentnaam uniek is. Het fragment kan niet worden gemaakt als er een bestaand fragment met dezelfde naam bestaat.
* Als u in een op XDP gebaseerd adaptief formulier een deelvenster opslaat als fragment dat een ander XDP-fragment bevat, wordt het resulterende fragment automatisch gebonden aan het onderliggende XDP-fragment. In het geval van een op XSD gebaseerde adaptieve vorm, zal het resulterende fragment aan de schemawortel worden gebonden.
* Wanneer u een adaptief fragment van de Vorm creeert, wordt een fragmentknoop gecreeerd, die aan de guideContainer knoop voor een Adaptief Vorm, in CRXDe Lite gelijkaardig is.
* Een fragment in een adaptief formulier dat een ander formuliergegevensmodel gebruikt, wordt niet ondersteund. Een fragment op basis van XDP wordt bijvoorbeeld niet ondersteund in een op XSD gebaseerd adaptief formulier en andersom.
* Adaptieve formulierfragmenten zijn beschikbaar voor gebruik via het tabblad Adaptieve formulierfragmenten in AEM zoekfunctie.
* Expressies, scripts of stijlen in een zelfstandig adaptief formulierfragment blijven behouden wanneer deze via verwijzing worden ingevoegd of in een adaptief formulier worden ingesloten.
* U kunt een adaptief formulierfragment, dat via verwijzing wordt ingevoegd, niet bewerken vanuit een adaptief formulier. Als u het fragment wilt bewerken, bewerkt u het zelfstandige adaptieve formulierfragment of sluit u het fragment in het adaptieve formulier in.
* Wanneer u een adaptief formulier publiceert, moet u de stand-alone adaptieve formulierfragmenten publiceren die door verwijzing zijn ingevoegd in het adaptieve formulier.
* Wanneer u een bijgewerkt fragment van het adaptief formulier opnieuw publiceert, worden de wijzigingen doorgevoerd in de gepubliceerde exemplaren van de adaptieve vorm waarin het fragment wordt gebruikt.
* Het adaptieve formulier met de component Verify ondersteunt geen anonieme gebruikers. Het wordt ook niet aangeraden de component Verify te gebruiken in een adaptief formulierfragment.
* (**Alleen** Mac) Voeg het volgende item toe aan het bestand /private/etc/hosts om ervoor te zorgen dat de functionaliteit van formulierfragmenten in alle scenario&#39;s perfect werkt:
  `127.0.0.1 <Host machine>`**Hostcomputer**: de Apple Mac-computer waarop AEM Forms is gedistribueerd.

## Referentiefragmenten {#reference-fragments}

Er zijn referentiefragmenten beschikbaar voor adaptieve formulieren die u kunt gebruiken om uw formulier te maken.
<!-- For more information, see [Reference Fragments](../../forms/using/reference-adaptive-form-fragments.md). -->
