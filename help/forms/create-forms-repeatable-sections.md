---
title: Hoe te om herhaalbare panelen in de Aangepaste Componenten van de Kern van de Vorm te creëren?
description: Leer herhaalbare secties of velden maken in een adaptief formulier.
role: Architect, Developer, Admin, User
feature: Adaptive Forms, Core Components
exl-id: 02521bf3-83c1-40a0-8fe6-23af240727e9
source-git-commit: f28f212574dda0ece2cedb56a714d381e5bd7d3c
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 0%

---

# Formulieren maken met herhaalbare secties (kerncomponenten) {#repeat-panel}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-forms-repeatable-sections.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Een herhaalbare sectie verwijst naar een deel van een formulier dat meerdere keren kan worden gedupliceerd of herhaald om informatie te verzamelen voor meerdere exemplaren van dezelfde gegevens.

Neem bijvoorbeeld een formulier dat wordt gebruikt om informatie over iemands werkervaring te verzamelen. U hebt mogelijk een herhaalbare sectie voor het vastleggen van details van elke vorige taak. De herhaalbare sectie zou doorgaans velden bevatten zoals de naam van het bedrijf, de functie, de datum van tewerkstelling en de verantwoordelijkheden op het gebied van de functie. De gebruiker kan veelvoudige instanties van de herhaalbare sectie toevoegen om informatie over elke baan in te gaan zij hebben gehouden.

![Herhaalbaarheid](/help/forms/assets/repeatable-adaptive-form-example.gif)

Aan het einde van dit artikel leert u:

* Een herhaalbare sectie maken in een adaptief formulier
* Minimum- of maximumaantal herhalingen instellen voor een adaptieve formuliercomponent
* De regelredacteur van het gebruik om toevoeging of schrappingsacties voor herhaalbare secties te vormen

U kunt de [Deelvenster](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), [Accordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Horizontale tabs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html), [Verticale tabs](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) of [Wizard](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) componenten om secties van een adaptief formulier herhaalbaar te maken. U kunt onderliggende componenten aan deze componenten toevoegen om een herhaalbare sectie in een formulier te maken.


Voorbeelden in dit document zijn gebaseerd op de [Deelvenster](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) component. U kunt identieke stappen uitvoeren om [Deelvenster](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), [Accordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Horizontale tabs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html), [Verticale tabs](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) of [Wizard](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) componenten herhaalbaar.

## Herhaalbare secties in een formulier toevoegen of verwijderen {#add-or-delete-repeatable-section-in-panel-container}

Als u een deelvenster in het formulier wilt herhalen of herhaalbare deelvensters wilt verwijderen, gebruikt de auteur van het formulier een knopcomponent om een exemplaar van het deelvenster toe te voegen of te verwijderen. Om herhaalbare secties (deelvensters) in een formulier toe te voegen of te verwijderen:

* [Deelvenstercontainer herhaalbaar maken](#make-panel-container-repeatable)
* [herhaalbare sectie toevoegen](#add-repeatable-section-using-instance-manager-via-scripts)
* [Herhaalbare secties verwijderen](#delete-repeatable-section-using-instance-manager-via-scripts)

### Deelvenstercontainer herhaalbaar maken {#make-panel-container-repeatable}

![Toegankelijkheid, tabblad](/help/forms/assets/repeat-panel.png)

Voer de volgende stappen uit om een deelvenster herhaalbaar te maken:
1. Selecteer een deelvenstercontainer en selecteer ![cmppr](/help/forms/assets/cmppr.png).
1. Klik op de knop **deelvenster herhalen** en schakel de schakeloptie in op **deelvenster herhaalbaar maken**.
1. Set **minimale herhalingen** zoals vereist voor minimale herhaalbare secties, kunt u instellen **minimale herhalingen** op nul zetten om deelvensters niet te vervangen of om de herhaalde deelvensters te verwijderen. De standaardwaarde voor minimale herhaling is nul.
1. Set **maximale herhalingen** om het paneel te herhalen vereist aantal tijden, door gebrek is de waarde oneindig.

   >[!NOTE]
   >
   > 
   > * Minimale herhaling kan geen waarde -ve zijn.
   > * Als u een niet-herhaalbaar deelvenster wilt maken, stelt u de waarde van het maximum- en minimumveld in op 1.

### herhaalbare sectie toevoegen met Instance Manager (via scripts) {#add-repeatable-section-using-instance-manager-via-scripts}

Het bovenliggende element van het deelvenster dat moet worden herhaald, moet een knop voor het toevoegen van knoppen bevatten om herhalende instanties van het deelvenster te beheren. Voer de volgende stappen uit om knoppen in te voegen in het bovenliggende element en om scripts in de knoppen in te schakelen:

1. Voeg een **knopcomponent** aan het bovenliggende element van het deelvenster. In de onderstaande voorbeeldvideo ziet u een knopcomponent met de labelnaam **Toevoegen** en veldnaam **AddPanel**, wordt gebruikt. Selecteer de component en selecteer ![bewerkingsregels](/help/forms/assets/edit-rules.png). De regels van de knoopcomponent open in de regelredacteur.
1. Klik in het venster Regeleditor op **Maken**.

   Selecteren **Visuele editor** in de rij Formulierobjecten en -functies.

   1. Selecteer in het regelgebied, onder WHEN, de status **is aangeklikt**.
   1. Selecteer onder VERVOLGENS **Instantie toevoegen** en sleep het deelvenster met slepen ![schakelen tussen zijpaneel](/help/forms/assets/toggle-side-panel.png) of selecteer het met **Object neerzetten of hier selecteren.**

   Selecteren **Code-editor** in de rij Formulierobjecten en -functies. Klikken **Regels bewerken** en in het codegebied:

   * Als u een knop in het deelvenster Toevoegen wilt maken, geeft u `this.panel.instanceManager.addInstance()`

   Klikken **Gereed**.

>[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)


### herhaalbare secties verwijderen met Instance Manager (via scripts) {#delete-repeatable-section-using-instance-manager-via-scripts}

Het bovenliggende element van het deelvenster moet een verwijderknop bevatten om een exemplaar van de herhaalbare deelvensters te verwijderen. Voer de volgende stappen uit om knopen aan de ouder op te nemen en manuscripten op de knopen toe te laten om herhaalbare panelen te schrappen:

1. Voeg een **knopcomponent** aan het bovenliggende element van het deelvenster: in de video hieronder, een knopcomponent met de labelnaam **delete** en veldnaam **DeletePanel** wordt gebruikt. Selecteer de component en selecteer ![bewerkingsregels](/help/forms/assets/edit-rules.png). De regels van de knoopcomponent open in de regelredacteur.
1. Klik in het venster Regeleditor op **Maken**.

   Selecteren **Visuele editor** in de rij Formulierobjecten en -functies.

   1. In het regelgebied, onder WHEN **DeletePanel**, status selecteren **is aangeklikt**.
   1. Selecteer onder VERVOLGENS **Instantie verwijderen** en sleep het deelvenster met slepen ![schakelen tussen zijpaneel](/help/forms/assets/toggle-side-panel.png) of selecteer het met **Object neerzetten of hier selecteren.**

   Selecteren **Code-editor** in de rij Formulierobjecten en -functies. Klikken **Regels bewerken** en in het codegebied:

   * Als u een knop in het deelvenster Verwijderen wilt maken, geeft u `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`

   Klikken **Gereed**.
>[!VIDEO](https://video.tv.adobe.com/v/3421620/adaptive-forms-repeatable-sections)

>[!NOTE]
>
>Als een veld tot een herhaalbaar deelvenster behoort, kunt u het veld niet rechtstreeks openen met de naam ervan in uw scripts. Als u toegang wilt krijgen tot het veld, geeft u met de `instances` API in `InstanceManager`. De syntaxis die moet worden gebruikt voor de `instances` API in `InstanceManager` is:
>
>
>`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
>
>
>U maakt bijvoorbeeld een adaptief formulier met een herhaalbaar deelvenster met een tekstvak. Wanneer u het formulier vooraf invult met drie herhaalbare tekstvakken, hebt u de xml hieronder nodig:
>
>
>`<panel1><textbox1>AA1</panel1></textbox1>`
>
>
>`<panel1><textbox1>AA2</panel1></textbox1>`
>
>
>`<panel1><textbox1>AA3</panel1></textbox1>`
>
>
>Als u AA1-gegevens wilt lezen, geeft u:
>
>
>`Panel1.instanceManager.instances[0].textbox.value`
>
>
>Als u AA2-gegevens wilt lezen, geeft u:
>
>
>`Panel1.instanceManager.instances[1].textbox.value`
>
>
>

<!-- 
>For more information, see: Class: InstanceManager#instances in [AEM Forms Java API reference](https://adobe.com/go/learn_aemforms_documentation_63).      
-->

>[!NOTE]
>
> Wanneer alle instanties van een deelvenster uit een adaptief formulier zijn verwijderd en u een instantie van het verwijderde deelvenster wilt toevoegen, gebruikt u de syntaxis _panelName om het Instance Manager van het deelvenster vast te leggen en gebruikt u de API van Instance Manager addInstance om de verwijderde instantie toe te voegen. Bijvoorbeeld _panelName.addInstance(). Er wordt een instantie van het verwijderde deelvenster toegevoegd.

<!--
![panel-repeatability-video](/help/adaptive-forms/assets/panel-repeatability-video.mp4)
-->

<!--

## Using the accordion layout for the parent panel &nbsp; {#using-the-accordion-layout-for-the-parent-panel-nbsp}

A panel has various layouts options. The Layout for accordian design option has out of the box support for repeatable panels. Perform the following steps to repeatable panel with Layout for accordian design option:

1. On the parent of panel to be repeated, select ![cmppr](assets/cmppr.png). You can see the properties in the sidebar. In the **Layout** drop-down, select **Accordion**.
1. On a panel, which is to be repeated, select ![cmppr](assets/cmppr.png). You can see the panel properties in the sidebar. Enable the **Make Panel Repeatable** tab, and specify value for the **Maximum** and **Minimum** fields.

   Now, you can use the plus (+) and delete ( ![delete-panel](assets/delete-panel.png)) buttons to add and remove the panels.

-->

## Herhalende subformulieren gebruiken vanuit formuliersjabloon (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Herhalbaar subformulier is vergelijkbaar met de herhaalbare deelvensters in Adaptief Forms. Voer in AEM Forms Designer de volgende stappen uit om een herhalend subformulier te maken:

1. Selecteer in het palet Hiërarchie het bovenliggende subformulier van het subformulier dat u wilt herhalen.
1. Klik in het palet Object op het tabblad Subformulier en selecteer Overlopen in de lijst Inhoud.
1. Selecteer het subformulier dat u wilt herhalen.
1. Klik in het palet Object op het tabblad Subformulier en selecteer Geplaatst of Overlopen in de lijst Inhoud.
1. Klik op het tabblad Binding en selecteer Subformulier herhalen voor elk gegevensitem.
1. Als u het minimale aantal herhalingen wilt opgeven, selecteert u Min. aantal en typt u een getal in het bijbehorende vak. Als deze optie is ingesteld op 0 en er geen gegevens zijn opgegeven voor de objecten in het subformulier bij het samenvoegen van gegevens, wordt het subformulier niet geplaatst wanneer het formulier wordt gegenereerd.
1. Als u het maximale aantal herhalingen van subformulieren wilt opgeven, selecteert u Max en typt u een getal in het bijbehorende vak. Als u geen waarde opgeeft in het vak Max, is het aantal herhalingen van het subformulier onbeperkt.
1. Als u een ingesteld aantal herhalingen van subformulieren wilt opgeven, ongeacht de hoeveelheid gegevens, selecteert u Eerste telling en typt u een getal in het bijbehorende vak. Als u deze optie selecteert en er geen gegevens beschikbaar zijn of er minder gegevensitems zijn dan de opgegeven waarde bij Eerste telling, worden lege exemplaren van het subformulier nog steeds op het formulier geplaatst.
1. Voeg twee knoppen toe aan het bovenliggende subformulier: een voor het toevoegen van een exemplaar en een andere voor het verwijderen van exemplaren van herhaalbare subformulieren. Zie voor meer informatie [Een handeling maken](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Koppel nu de formuliersjabloon aan het adaptieve formulier. Zie voor meer informatie [Een adaptief formulier maken op basis van een sjabloon](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=en#create-an-adaptive-form-based-on-an-xfa-form-template).
1. Gebruik de knoppen die u in stap 9 hebt gemaakt om subformulieren toe te voegen en te verwijderen.

ZIP-bestand dat is gekoppeld, bevat een voorbeeld van een herhaalbaar subformulier.

[Bestand ophalen](/help/forms/assets/samplerepeatablesubform.zip)

## Herhalingsinstellingen van een XML-schema (XSD) gebruiken {#using-repeat-settings-of-an-xml-schema-xsd-br}

U kunt herhaalbare panelen van een Schema van XML en van het minOccurs &amp; maxOccurs bezit van om het even welk complex typeelement tot stand brengen. Voor gedetailleerde informatie over het Schema van XML, zie [Aangepaste formulieren maken met XML-schema als formuliermodel](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-xml-schema-form-model.html).

In de volgende code worden de `SampleType`gebruikt de eigenschap minOccurs &amp; maxOccurs.

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>

        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartDate" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails"
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```


## Zie ook {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Create an Adaptive Form](creating-adaptive-form-core-components.md)
>* [Create style or themes for your forms](using-themes-in-core-components.md)
>* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
>* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/features/console-layout.md)

-->