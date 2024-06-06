---
title: Wat zijn adaptieve formulierfragmenten?
description: Adaptive Forms biedt een mechanisme om een formuliersegment te maken, zoals een deelvenster of een groep velden, zoals het in elk adaptief formulier wordt gebruikt. U kunt een bestaand deelvenster ook opslaan als fragment.
topic-tags: author
keywords: Adaptieve formulierfragmenten toevoegen, Adaptieve formulierfragmenten maken, een formulierfragment maken, een fragment toevoegen aan een adaptief formulier, Fragmenten beheren
feature: Adaptive Forms, Core Components
exl-id: 3a9ad1b7-2f6f-4ca9-a1c9-549c4238c59e
source-git-commit: 46cd7d689c6cbc453720b5798ffb552da58f66e7
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---

# Adaptieve Forms-fragmenten maken en gebruiken in een adaptief formulier op basis van kerncomponenten {#adaptive-form-fragments}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service (kerncomponenten) | Dit artikel |
| AEM as a Cloud Service (stichtingscomponenten) | [Klik hier](/help/forms/adaptive-form-fragments.md) |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html) |

Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails en inkomstengegevens. Formulierontwikkelaars moeten deze algemene segmenten telkens maken wanneer een nieuw formulier wordt gemaakt.

Adaptive Forms biedt een handig mechanisme om slechts eenmaal een formuliersegment als een deelvenster of een groep velden te maken en deze opnieuw te gebruiken in Adaptive Forms. Deze herbruikbare en standalone segmenten worden Adaptieve formulierfragmenten genoemd.

Formulierfragmenten worden naadloos geïntegreerd in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

U kunt een fragment meerdere keren aan een document toevoegen en eigenschappen voor gegevensbinding van de componenten gebruiken om het aan verschillende gegevensbronnen of schema te koppelen. U kunt bijvoorbeeld hetzelfde adresfragment gebruiken voor een vast adres, communicatie en factureringsadres en dit koppelen aan verschillende velden van een gegevensbron of schema.

>[!NOTE]
>
> U kunt uw fragmentervaring eenvoudig aanpassen voor gebruikers met de [Dialoogvenster Formulierfragment configureren en ontwerpen](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/adaptive-form-fragment).

## Een adaptief formulierfragment maken {#create-a-fragment}

U kunt een adaptief formulierfragment helemaal opnieuw maken of een deelvenster in een bestaand adaptief formulier opslaan als fragment. Een formulierfragment maken:

1. Meld u aan bij uw AEM Forms-exemplaar op https://[*hostnaam*]:[*poort*]/aem/forms.html.
1. Klikken **Maken > Adaptief formulierfragment**.

   ![Adaptief formulierfragment maken](/help/forms/assets/adaptive-form-fragment.png)

1. Geef een titel, naam, beschrijving en tags voor het fragment op. Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.
1. Selecteer een formuliersjabloon. U kunt een formulierfragment maken voor Core Components (Basiscomponenten) op basis van adaptieve Forms of Foundation Components (Basiscomponenten) op basis van adaptieve Forms. Als u formulierfragment wilt maken voor formulieren op basis van kerncomponenten, selecteert u een sjabloon op basis van kerncomponenten.

   Wanneer u formulierfragment maakt voor formulieren op basis van kerncomponenten, gebruikt u de optie Formulierthema selecteren om een thema op basis van kerncomponenten te selecteren.

1. Klik om het dialoogvenster **Formuliermodel** en van de **Selecteren uit** selecteert u een van de volgende modellen voor het fragment:

   ![Hiermee geeft u het modeltype weer op het tabblad Formuliermodel](assets/create-af-1-1.png)

   * **Geen**: Hiermee geeft u op het fragment helemaal opnieuw te maken zonder een formuliermodel te gebruiken.

     >[!NOTE]
     >
     > In Adaptive Forms kunt u één formulierfragment (op basis van kerncomponenten) meerdere keren gebruiken. Deze ondersteunt zowel op geen gebaseerde als op schema gebaseerde formulierfragmenten.

   * **Schema**: Geeft op om het fragment te maken met een XML- of JSON-schema dat naar AEM Forms is geüpload. U kunt vanuit de beschikbare XML- of JSON-schema&#39;s het formuliermodel voor het fragment uploaden of selecteren. Wanneer u een XML-schema selecteert, kunt u ook een adaptief formulierfragment maken door in het geselecteerde schema een complexType te selecteren in het **[!UICONTROL XML Schema Complex Type]** vervolgkeuzelijst. Wanneer u een JSON-schema selecteert, kunt u ook een adaptief formulierfragment maken door in het geselecteerde schema een schemadefinitie te selecteren in het **[!UICONTROL JSON Schema Definitions]** vervolgkeuzelijst.
   * **Formuliergegevensmodel**: Geeft op om het fragment te maken met een formuliergegevensmodel (FDM). U kunt een adaptief formulierfragment maken op basis van slechts één gegevensmodelobject in een formuliergegevensmodel (FDM). Vervolgkeuzelijst Formuliergegevensmodel (FDM)-definities uitvouwen. Hiermee worden alle gegevensmodelobjecten in het opgegeven formuliergegevensmodel (FDM) weergegeven. Selecteer een gegevensmodelobject in de lijst.

   ![Formuliergegevensmodel (FDM)](assets/create-af-3.png)

1. Klikken **Maken** en klik vervolgens op **Openen** om het fragment met een standaardsjabloon te openen in de bewerkingsmodus. In de bewerkingsmodus kunt u elke component Adaptief formulier aan het fragment toevoegen.

<!-- For information about Adaptive Form components, see [Introduction to authoring Adaptive Forms](../../forms/using/introduction-forms-authoring.md). --> Als u bovendien een XML-schema hebt geselecteerd als het formuliermodel voor uw fragment, wordt een nieuw tabblad met de hiërarchie van het formuliermodel weergegeven in de zoeker naar inhoud. Hiermee kunt u formuliermodelelementen naar het fragment slepen en neerzetten. <!--The added form-model elements get converted into form components while retaining the original properties from the associated XDP or XSD. -->

Zodra het adaptieve fragment van de Vorm dat op een schema of een model van vormgegevens (FDM) wordt gebaseerd wordt gecreeerd, verschijnen het model van vormgegevens (FDM) of schemaelementen op het lusje van Gegevensbronnen van browser van de Inhoud in de Adaptieve redacteur van de Vorm. U kunt formuliermodelelementen naar het fragment slepen en neerzetten. De toegevoegde formuliermodelelementen worden geconverteerd naar formuliercomponenten terwijl de oorspronkelijke eigenschappen van het gekoppelde schema behouden blijven.


## Een fragment toevoegen aan een adaptief formulier {#insert-a-fragment-in-an-adaptive-form}

Een adaptief formulierfragment toevoegen aan een adaptief formulier:

1. Open het adaptieve formulier in de bewerkingsmodus.
1. Voeg de **Adaptief formulierfragment** aan het formulier.
1. Het dialoogvenster Configuratie openen van **Adaptief formulierfragment** component.
1. Selecteer de **Fragmentverwijzing** in de **Basis** tab. Alle Adaptieve Forms-fragmenten die beschikbaar zijn voor uw formulier, worden weergegeven, afhankelijk van het formuliermodel.

1. Selecteer een adaptief formulierfragment op het tabblad **Adaptief formulierfragment** op uw adaptieve formulier.

   ![Selecteer de optie Aangepaste formulierfragmenten](/help/forms/assets/adaptive-form-fragment-basic.png)

<!-- >[!NOTE]
   >
   >The Adaptive Form fragment is not enabled for authoring from within the Adaptive Form. Moreover, you cannot use an XSD-based fragment in a JSON-based Adaptive Form and the opposite way. -->

Het fragment Adaptief formulier wordt toegevoegd met verwijzing naar het adaptieve formulier en blijft gesynchroniseerd met het standalone adaptieve formulierfragment. Dit houdt in dat alle wijzigingen die in het adaptieve formulierfragment worden aangebracht, worden weerspiegeld in alle gevallen waarin het fragment is opgenomen in Adaptief Forms.

<!--### Embed a fragment in Adaptive Form {#embed-a-fragment-in-adaptive-form}

You can choose to embed an Adaptive Form fragment in an Adaptive Form by clicking the ![Embed](assets/Smock_Import_18_N.svg) icon the panel toolbar of the added fragment

The embedded fragment is no longer linked with the standalone fragment. You can edit the components in the embedded fragment from within the Adaptive Form.-->

<!-- 
## Configure fragment appearance {#configure-fragment-appearance}

Any fragment you insert in Adaptive Forms appears as a placeholder image. The placeholder displays titles of up to a maximum of ten child panels in the fragment. You can configure AEM Forms to show the complete fragment instead of the placeholder image.

Perform the following steps to show complete fragments in forms:

1. Go to AEM web console configuration page at https:[*host*]:[*port*]/system/console/configMgr.

1. Search and click **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** to open it in edit mode.
1. Disable **[!UICONTROL Enable Placeholder in place of Fragment]** checkbox to show complete fragments rather than the placeholder image.

-->

### Fragmenten in fragmenten gebruiken {#using-fragments-within-fragments}

U kunt geneste adaptieve formulierfragmenten maken, wat betekent dat u een fragment kunt toevoegen aan een ander fragment en dat u een geneste fragmentstructuur kunt hebben.

### Een formulierfragment meerdere keren gebruiken in een adaptief formulier {#using-form-fragment-mutiple-times-in-af}

U kunt een formulierfragment op basis van geen en schema meerdere keren gebruiken in een adaptief formulier om gegevens uniek op te slaan voor elk veld met formulierfragmenten. U kunt bijvoorbeeld een fragment van een adresformulier gebruiken om adresgegevens te verzamelen voor permanente communicatie en het weergeven van levende adressen in een aanvraagformulier voor een lening.

![meerdere fragmenten gebruiken in adaptieve vorm](/help/forms/assets/using-multiple-fragment-af.gif)

<!--

## Auto mapping of fragments for data binding {#auto-mapping-of-fragments-for-data-binding}

When you create an Adaptive Form fragment using an XFA form template or XSD complex type and drag-drop the fragment to an Adaptive Form, the XFA fragment or the XSD complex type is automatically replaced by the corresponding Adaptive Form fragment whose fragment model root is mapped to the XFA fragment or XSD complex Type.

You can change the fragment asset and its bindings from the Edit component dialog.

You can also drag-drop a bound Adaptive Form fragment from Adaptive Form Fragment library in AEM content finder and provide the correct bind reference from the Edit component dialog of the Adaptive Form fragment panel. -->

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
   <td><p>Voorvertoning</p> </td>
   <td><p>Hiermee kunt u een voorbeeld van het fragment weergeven als een HTML of aangepaste voorvertoning door gegevens uit een XML-bestand samen te voegen met het fragment. Zie voor meer informatie <a>Een voorbeeld van een formulier bekijken</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Downloaden</p> </td>
   <td><p>Het geselecteerde fragment downloaden.<br /> <br /> </p> </td>
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
   <td><p>Hiermee publiceert u het geselecteerde fragment of maakt u de publicatie ervan ongedaan.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Belangrijke punten die u moet onthouden wanneer u werkt met fragmenten {#key-points-to-remember-when-working-with-fragments}

* Zorg ervoor dat de fragmentnaam uniek is. Het fragment kan niet worden gemaakt als er een bestaand fragment met dezelfde naam bestaat.
* Expressies, scripts of stijlen in een zelfstandig adaptief formulierfragment blijven behouden wanneer deze via verwijzing worden ingevoegd of in een adaptief formulier worden ingesloten.
* U kunt een adaptief formulierfragment, dat via verwijzing wordt ingevoegd, niet bewerken vanuit een adaptief formulier. Als u wilt bewerken, wijzigt u het zelfstandige adaptieve formulierfragment.
* Wanneer u een adaptief formulier publiceert, moet u de stand-alone adaptieve formulierfragmenten publiceren die door verwijzing zijn ingevoegd in het adaptieve formulier.
* Wanneer u een bijgewerkt adaptief formulierfragment opnieuw publiceert, worden de wijzigingen doorgevoerd in de gepubliceerde exemplaren van het adaptieve formulier waarin het fragment wordt gebruikt.
* Het adaptieve formulier met de component Verify ondersteunt geen anonieme gebruikers. Het wordt ook niet aangeraden de component Verify te gebruiken in een adaptief formulierfragment.

## Referentiekaders {#reference-fragments}

Er zijn referentiefragmenten beschikbaar voor adaptieve formulieren die u kunt gebruiken om uw formulier te maken.
<!-- For more information, see [Reference Fragments](../../forms/using/reference-adaptive-form-fragments.md). -->



## Zie ook {#see-also}

{{see-also}}