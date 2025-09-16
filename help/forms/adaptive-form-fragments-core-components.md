---
title: Wat zijn adaptieve formulierfragmenten?
description: Adaptive Forms biedt een mechanisme om een formuliersegment te maken, zoals een deelvenster of een groep velden, zoals het in elk adaptief formulier wordt gebruikt. U kunt een bestaand deelvenster ook opslaan als fragment.
topic-tags: author
keywords: Adaptieve formulierfragmenten toevoegen, Adaptieve formulierfragmenten maken, een formulierfragment maken, een fragment toevoegen aan een adaptief formulier, Fragmenten beheren
feature: Adaptive Forms, Core Components
exl-id: 3a9ad1b7-2f6f-4ca9-a1c9-549c4238c59e
role: User, Developer
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 0%

---

# Adaptieve Forms-fragmenten maken en gebruiken in een adaptief formulier op basis van kerncomponenten {#adaptive-form-fragments}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Core Components) | Dit artikel |
| AEM as a Cloud Service (Foundation Components) | [ klik hier ](/help/forms/adaptive-form-fragments.md) |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html?lang=nl-NL) |

Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails en inkomstengegevens. Formulierontwikkelaars moeten deze algemene segmenten telkens maken wanneer een nieuw formulier wordt gemaakt.

Adaptive Forms biedt een handig mechanisme om slechts eenmaal een formuliersegment als een deelvenster of een groep velden te maken en deze opnieuw te gebruiken in Adaptive Forms. Deze herbruikbare en standalone segmenten worden Adaptieve formulierfragmenten genoemd.

Formulierfragmenten worden naadloos geïntegreerd in meerdere formulieren, waardoor het maken van consistente en professioneel ogende formulieren wordt gestroomlijnd. Formulierfragmenten zorgen voor herbruikbaarheid, standaardisering en consistentie van merken via de functie &#39;Eenmaal wijzigen en overal weerspiegelen&#39;. Ervaar meer onderhoudsgemak en efficiëntie, aangezien updates die op één plaats worden gemaakt, automatisch worden verspreid over alle vormen die deze fragmenten gebruiken.

U kunt een fragment meerdere keren aan een document toevoegen en eigenschappen voor gegevensbinding van de componenten gebruiken om het aan verschillende gegevensbronnen of schema te koppelen. U kunt bijvoorbeeld hetzelfde adresfragment gebruiken voor een vast adres, communicatie en factureringsadres en dit koppelen aan verschillende velden van een gegevensbron of schema.

>[!NOTE]
>
> U kunt uw fragmentervaring voor gebruikers met [ gemakkelijk aanpassen vormt dialoog en de dialoog van het Ontwerp van de component van het Fragment van de Vorm ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/adaptive-form-fragment).

## Een adaptief formulierfragment maken {#create-a-fragment}

U kunt een adaptief formulierfragment helemaal opnieuw maken of een deelvenster in een bestaand adaptief formulier opslaan als fragment. Een formulierfragment maken:

1. Login aan uw instantie van AEM Forms in https:// [*hostname*]:[*haven*] /aem/forms.html.
1. Klik **creëren > het AanpassingsFragment van de Vorm**.

   ![ creeer Aangepast Fragment van de Vorm ](/help/forms/assets/adaptive-form-fragment.png)

1. Geef een titel, naam, beschrijving en tags voor het fragment op. Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.
1. Selecteer een formuliersjabloon. U kunt een formulierfragment maken voor Core Components (Basiscomponenten) op basis van adaptieve Forms of Foundation Components (Basiscomponenten) op basis van adaptieve Forms. Als u formulierfragment wilt maken voor formulieren op basis van kerncomponenten, selecteert u een sjabloon op basis van kerncomponenten.

   Wanneer u formulierfragment maakt voor formulieren op basis van kerncomponenten, gebruikt u de optie Formulierthema selecteren om een thema op basis van kerncomponenten te selecteren.

1. Klik om het **Model van de Vorm** lusje te openen, en van **Uitgezocht van** drop-down menu, selecteer één van de volgende modellen voor het fragment:

   ![ modeltype van vertoningen in het Modellusje van de Vorm ](assets/create-af-1-1.png)

   * **niets**: Specificeert om het fragment van kras tot stand te brengen zonder enig vormmodel te gebruiken.

     >[!NOTE]
     >
     > In Adaptive Forms kunt u één formulierfragment (op basis van kerncomponenten) meerdere keren gebruiken. Deze ondersteunt zowel op geen gebaseerde als op schema gebaseerde formulierfragmenten.

   * **Schema**: Specificeert om het fragment tot stand te brengen gebruikend een schema van XML of van JSON dat aan AEM Forms wordt geupload. U kunt vanuit de beschikbare XML- of JSON-schema&#39;s het formuliermodel voor het fragment uploaden of selecteren. Wanneer u een XML-schema selecteert, kunt u ook een adaptief formulierfragment maken door in het keuzemenu **[!UICONTROL XML Schema Complex Type]** een complexType te selecteren dat aanwezig is in het geselecteerde schema. Wanneer u een JSON-schema selecteert, kunt u ook een adaptief formulierfragment maken door in het keuzemenu **[!UICONTROL JSON Schema Definitions]** een schemadefinitie te selecteren die aanwezig is in het geselecteerde schema.
   * **Model van de Gegevens van de Vorm**: Specificeert om het fragment tot stand te brengen gebruikend een model van vormgegevens (FDM). U kunt een adaptief formulierfragment maken op basis van slechts één gegevensmodelobject in een formuliergegevensmodel (FDM). Vervolgkeuzelijst Formuliergegevensmodel (FDM)-definities uitvouwen. Hiermee worden alle gegevensmodelobjecten in het opgegeven formuliergegevensmodel (FDM) weergegeven. Selecteer een gegevensmodelobject in de lijst.

   ![ Model van de Gegevens van de Vorm (FDM) ](assets/create-af-3.png)

1. Klik **creëren** en klik dan **Open** om het fragment, met een standaardmalplaatje, op uit te geven wijze te openen. In de bewerkingsmodus kunt u elke component Adaptief formulier aan het fragment toevoegen.

<!-- For information about Adaptive Form components, see [Introduction to authoring Adaptive Forms](../../forms/using/introduction-forms-authoring.md). --> Als u bovendien een XML-schema hebt geselecteerd als het formuliermodel voor uw fragment, wordt een nieuw tabblad met de hiërarchie van het formuliermodel weergegeven in de zoeker naar inhoud. Hiermee kunt u formuliermodelelementen naar het fragment slepen en neerzetten. <!--The added form-model elements get converted into form components while retaining the original properties from the associated XDP or XSD. -->

Zodra het adaptieve fragment van de Vorm dat op een schema of model van vormgegevens (FDM) wordt gebaseerd wordt gecreeerd, verschijnen het model van vormgegevens (FDM) of schemaelementen op het lusje van Gegevensbronnen van browser van de Inhoud in de Adaptieve Bouwer van de Vorm. U kunt formuliermodelelementen naar het fragment slepen en neerzetten. De toegevoegde formuliermodelelementen worden geconverteerd naar formuliercomponenten terwijl de oorspronkelijke eigenschappen van het gekoppelde schema behouden blijven.


## Een fragment toevoegen aan een adaptief formulier {#insert-a-fragment-in-an-adaptive-form}

Een adaptief formulierfragment toevoegen aan een adaptief formulier:

1. Open het adaptieve formulier in de bewerkingsmodus.
1. Voeg de **Aangepaste component van het Fragment van de Vorm** aan de vorm toe.
1. Open de dialoog van de Configuratie van **AanpassingsFragment van de Vorm** component.
1. Selecteer de **verwijzing van het Fragment** in **Basis** tabel. Alle Adaptieve Forms-fragmenten die beschikbaar zijn voor uw formulier, worden weergegeven, afhankelijk van het formuliermodel.

1. Selecteer een Adaptief fragment van de Vorm op de **Adaptieve component van het Fragment van de Vorm** op uw AanpassingsVorm.

   ![ selecteer de Aangepaste optie van de Fragmenten van de Vorm ](/help/forms/assets/adaptive-form-fragment-basic.png)

<!-- 
   >[!NOTE]
   >
   >The Adaptive Form fragment is not enabled for authoring from within the Adaptive Form. Moreover, you cannot use an XSD-based fragment in a JSON-based Adaptive Form and the opposite way. 
-->

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

![ gebruikend veelvoudige fragment in adaptieve vorm ](/help/forms/assets/using-multiple-fragment-af.gif)

## Ondersteuning voor automatische toewijzing van fragmenten in een adaptief formulier

Wanneer u een adaptief formulierfragment maakt op basis van een JSON-schemadefinitie, kan dit automatisch opnieuw worden gebruikt in formulieren die met hetzelfde schema zijn gemaakt.
Als u een schemaobject of geneste objecten sleept die overeenkomen met de JSON-schemadefinitietoewijzing van een adaptief formulierfragment, wordt het object vervangen door het overeenkomende adaptieve formulierfragment. In plaats van een deelvenster met afzonderlijke velden toe te voegen, voegt het formulier het toegewezen adaptieve formulierfragment in.

![ belemmering en laat vallen een fragment ](/help/forms/assets/fragment.png)

U kunt een gebonden adaptief formulierfragment ook slepen en neerzetten vanuit de bibliotheek met adaptief formulierfragment in de zoekfunctie voor AEM-inhoud en de juiste bindingsverwijzing opgeven in het dialoogvenster Component bewerken van het deelvenster Adaptief formulierfragment.

## Fragmenten beheren {#manage-fragments}

U kunt verschillende bewerkingen uitvoeren op Adaptief-formulierfragmenten met de gebruikersinterface van AEM Forms.

1. Ga naar `https://[hostname]/aem/forms.html` .

1. Klik **Uitgezocht** in de toolbar van UI van AEM Forms en selecteer een Adaptief Fragment van de Vorm. De werkbalk bevat de volgende bewerkingen die u kunt uitvoeren op het geselecteerde adaptieve formulierfragment.

<table>
 <tbody>
  <tr>
   <td><p><strong>Bewerking</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bewerken</p> </td>
   <td><p>Hiermee opent u het geselecteerde adaptieve formulierfragment in de bewerkingsmodus. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Voorvertoning</p> </td>
   <td><p>Hiermee kunt u een voorvertoning van het fragment weergeven als een HTML of een aangepaste voorvertoning door gegevens uit een XML-bestand samen te voegen met het fragment. Voor meer informatie, zie <a> Previewing een vorm </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Downloaden</p> </td>
   <td><p>Hiermee downloadt u het geselecteerde fragment. <br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Revisie starten/Revisie beheren</p> </td>
   <td><p>Hiermee kunt u een revisie van het geselecteerde fragment starten en beheren. Voor meer informatie, zie <a> Creërend en het leiden overzichten </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Woordenboek toevoegen</p> </td>
   <td><p>Genereert een woordenboek voor het lokaliseren van het geselecteerde fragment. Voor meer informatie, zie <a> Localizing Adaptive Forms </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publiceren/Publiceren ongedaan maken</p> </td>
   <td><p>Hiermee publiceert u het geselecteerde fragment of maakt u de publicatie ervan ongedaan. <br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment. <br /> <br /> </p> </td>
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
