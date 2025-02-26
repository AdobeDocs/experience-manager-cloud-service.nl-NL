---
title: Universal Editor - Zelfstudie voor ontwikkelaars
description: Deze zelfstudie helpt u om aan de slag te gaan met de Universal Editor-interface. Het helpt u bij het begrijpen van de gebruikersinterface om uw eigen Edge Delivery Services-formulieren te maken in de Universal Editor.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 0%

---

# De interface van de Universal Editor (WYSIWYG) verkennen

De [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) biedt een eenvoudige, visuele, en intuïtieve interface van What You See Is What You Get (WYSIWYG) voor de Diensten van de Levering van de Rand van Adobe (EDS) Forms aan. Het biedt een moderne interface met functionaliteit voor slepen en neerzetten voor efficiënt ontwerpen van formulieren.

![ Universele Gebruikersinterface van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Universal Editor Interface

Wanneer de auteur van het formulier het formulier bewerkt met de Universal Editor, opent de console een interactieve WYSIWYG-interface waarmee de gebruiker het formulier kan bewerken.

>[!NOTE]
>
> Leren hoe te om vormen te schrijven gebruikend de Universele Redacteur, zie het artikel [ Begonnen Worden met Edge Delivery Services voor AEM Forms gebruikend Universele Redacteur (WYSIWYG) ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![ Universele Gebruikersinterface van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

De interface van de Universal Editor bestaat uit vier delen:

* **[A: De Kopbal van Experience Cloud](#experience-cloud-header)**
* **[B: Universele Toolbar van de Redacteur](#universal-editor-toolbar)**
* **[C: Het Comité van Eigenschappen](#properties-panel)**
* **[D: Redacteur](#editor)**

### Experience Cloud-koptekst

De Experience Cloud-header bevindt zich boven aan de console. Deze biedt informatie over de huidige locatie in Experience Cloud. U kunt ook naar andere Experience Cloud-toepassingen navigeren.

![ Universal Editor Experience Cloud Header ](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)


Laten we elk van zijn componenten begrijpen.

* **Adobe Experience Cloud**

  U kunt de **verbinding van Adobe Experience Cloud** op de linkerkant van het scherm klikken om aan de wortel van de oplossing van Experience Manager en toegangshulpmiddelen zoals Experience Manager Sites, Experience Manager Assets, en Experience Manager Guides te navigeren.

  ![ Adobe Experience Manager ](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png) {width=50%, height=50%}

* **naam van de Organisatie**

  De **naam van de Organisatie** toont de naam van de organisatie IMS u momenteel wordt ondertekend in. U kunt naar een andere organisatie overschakelen IMS, als zij toegang tot andere organisaties hebben, door van de drop-down lijst te selecteren. De momenteel geselecteerde IMS-organisatienaam is bijvoorbeeld `AEM Forms Internal01` .

  ![ Organisatie ](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png) {width=50%, height=50%}


* **Hulp**

  Met het Help-pictogram hebt u snel toegang tot leermiddelen en ondersteuningsbronnen. De vormauteur kan ook toevoegen terugkoppelt in de **sectie van de Hulp**.
  ![ Hulp ](/help/edge/docs/forms/universal-editor/assets/ue-help.png) {width=50%, height=50%}


* **Meldingen**

  De **sectie van het Bericht** toont het aantal momenteel toegewezen onvolledige berichten, de verzoeken en, huidige taken in de organisatie IMS.

  ![ Bericht ](/help/edge/docs/forms/universal-editor/assets/ue-notification.png) {width=50%, height=50%}


* **Oplossingen**

  U kunt aan andere oplossingen van Experience Cloud schakelen gebruikend de **verbinding van Oplossingen**.
  ![ Oplossingen ](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png) {width=50%, height=50%}


* **Auteur**
Het pictogram geeft de details van de auteur van het formulier weer, samen met de naam van de IMS-organisatie waarin de auteur momenteel is aangemeld.
  ![ Auteur ](/help/edge/docs/forms/universal-editor/assets/ue-author.png) {width=50%, height=50%}

### Werkbalk Universele editor

Met de werkbalk kunt u naar andere formulieren navigeren en deze bewerken. Hiermee kunnen ze ook het formulier publiceren of de publicatie ervan ongedaan maken, de eigenschappen van het formulier bewerken en toegang krijgen tot de regeleditor.
![ Universele Toolbar van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Laten we elk van zijn componenten begrijpen.

* **Knop van het Huis**
Met de knop Home kunt u naar de startpagina van de Universal Editor navigeren. U kunt ook rechtstreeks de URL invoeren van het formulier dat u wilt bewerken met de universele editor.
  ![ Universeel Huis van de Redacteur ](/help/edge/docs/forms/universal-editor/assets/ue-home.png)



* **de Bar van de Plaats**
De **plaatsbar** toont het adres van de vorm die de auteur uitgeeft. U kunt ook een andere formulier-URL invoeren door op de locatiebalk te klikken. De sneltoets om de locatiebalk te openen, is toets `l` .
  ![ de Bar van de Plaats ](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png) {width=50%, height=50%}



* **Redacteur van de Regel**

  De **Redacteur van de Regel** biedt een intuïtieve visuele interface voor het creëren van en het leiden van regels aan. U kunt dynamisch formuliergedrag toevoegen met de regeleditor.

  ![ Redacteur van de Regel ](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > * In Universele Redacteur, wordt de uitbreiding van de Redacteur van de Regel niet toegelaten door gebrek. Om de uitbreiding van de Redacteur van de Regel toe te laten schrijven aan ons in [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) van uw officiële e-mailidentiteitskaart
  > * Leren hoe te om regels tot stand te brengen, verwijs naar de artikel [ Inleiding aan de Redacteur van de Regel in de Authoring van WYSIWYG ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

* **geef de Eigenschappen van de Vorm uit**
U kunt de vormeigenschappen, zoals het model van vormgegevens uitgeven en datum publiceren, door de **te klikken geeft de optie van de Eigenschappen van de Vorm** uit.
  ![ geef de Eigenschappen van de Vorm uit ](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)



* **Montages van de Kopbal van de Authentificatie**
De **montages van de authentificatiekop** staat de auteur toe om een kopbal van de douaneauthentificatie voor lokale ontwikkelingsdoeleinden te plaatsen.
  ![ authentificatiekopbal ](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png) {width=50%, height=50%}



* **Responsieve Wijze**
  **optie van de Wijze van 0} de Responsieve** staat u toe om te bepalen hoe de Universele Redacteur de vorm teruggeeft. Standaard wordt de editor geopend in een computerlay-out, waarbij de hoogte en breedte automatisch worden bepaald door de browser. U kunt ook een mobiel apparaat emuleren en controleren hoe het formulier op mobiele apparaten wordt weergegeven.

  ![ Responsieve wijze ](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png) {width=50%, height=50%}


* **Modus van de Voorproef 0}
In de voorbeeldmodus wordt het formulier precies zo weergegeven in de editor als het wordt gepubliceerd.** Op deze manier kan de auteur in het formulier navigeren door op koppelingen en knoppen te klikken. Als de auteur tevreden is met de bewerkingen, kan hij het formulier publiceren voor live gebruikers. De sneltoets voor het schakelen tussen de modus Bewerken en Voorvertoning is `p` .
  ![ Voorproef ](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

* **Open Pagina**
De **Open optie van de Pagina** opent de vorm in een nieuw lusje voor voorproef. De sneltoets voor het openen van het formulier in de voorbeeldmodus op een nieuw tabblad is `o` .
  ![ Open Pagina ](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

* **publiceer**

  U kunt de vorm ter beschikking stellen om gebruikers te leven gebruikend **publiceer** knoop.
  ![ publiceer ](/help/edge/docs/forms/universal-editor/assets/ue-publish.png) {width=50%, height=50%}

* **Ellipsis**
Wanneer de auteur de (...) ellipseoptie klikt, verschijnt **unpublish** optie. U kunt een vorm ongedaan maken door **te gebruiken unpublish** optie.
  ![ Ellipse ](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png) {width=50%, height=50%}

### Deelvenster Eigenschappen

Het **Comité van Eigenschappen** wordt gevestigd op de rechterkant van de redacteur. Hierin worden de details weergegeven van de component die is geselecteerd in de hiërarchie van het formulier. Dit is de standaardstructuur wanneer geen component is geselecteerd.
![ gebruik-eigenschappen paneel ](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png) {width=50%,height=50%}


Laten we elk van zijn componenten begrijpen.


* **de Wijze van Eigenschappen**
In **Eigenschappen** toont de optie de eigenschappen van de geselecteerde component in de redacteur. In de afbeelding worden bijvoorbeeld de eigenschappen van de geselecteerde invoercomponent voor nummers weergegeven. U kunt de eigenschappen van de component wijzigen met deze optie. De sneltoets voor het openen van eigenschappen van de component is `d` .

  ![ gebruik-eigenschappen ](/help/edge/docs/forms/universal-editor/assets/ue-properties.png) {width=50%,height=50%}


* **de Boom van de Inhoud**
De **optie van de Boom van de Inhoud** toont de hiërarchie van de vorm. Wanneer de auteur op een punt in de inhoudsboom klikt, selecteert de redacteur het en scrolt aan die component. De sneltoets voor het schakelen tussen de weergave van de inhoudsstructuur is sleutel `f` .

  ![ de boom van de Inhoud ](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png) {width=50%, height=50%}


* **produceer Variaties**
  **produceer Variaties** gebruik kunstmatige intelligentie om verschillende versies van vormen te produceren die op specifieke herinneringen worden gebaseerd. Deze aanwijzingen kunnen worden verschaft door Adobe of worden gemaakt en beheerd door de auteur van het formulier.

  ![ variatie ](/help/edge/docs/forms/universal-editor/assets/ue-variations.png) {width=50%, height=50%}


  >[!NOTE]
  >
  > Voor instructies bij het gebruiken produceer Variaties voor vormen, verwijs naar [ produceer Artikel van Variaties ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/generative-ai/generate-variations)

* **Experimentatie**:

  **de Experimentatie** verwijst naar technieken die worden gebruikt om verschillende variaties van vormen en lay-out te testen om gebruikerservaring en prestaties te optimaliseren.
  ![ experimenteren ](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png) {width=50%, height=50%}


* **Personalization**
De **Personalization** optie vormt de montages om een verbinding tussen de vormen en Adobe Experience Platform (AEP) te vestigen die deel van het ecosysteem van Adobe of externe toepassingen uitmaken.
  ![ Personalization ](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png) {width=50%, height=50%}


* **het Testen A/B**:
  **het Testen A/B** verwijst naar technieken die worden gebruikt om verschillende variaties van vormen en lay-out te testen om gebruikerservaring en prestaties te optimaliseren.
  ![ het Testen A/B ](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png) {width=50%,height=50%}



* **het Beheer van de Taak**:
De **eigenschap van het Beheer van de Taak** laat u toe om werkschema&#39;s te stroomlijnen en samenwerking te verbeteren door teams toe te staan om, taken met betrekking tot de aanpassing en optimalisering van vormen te beheren te volgen en uit te voeren
  ![ taakbeheer ](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png) {width=50%, height=50%}

.
* **Inhoudsconcepten**

  De **Inhoud stelt** optie toe u om concepten voor rijke tekstelementen tot stand te brengen. Concepten kunnen worden gemaakt met bestaande formuliertekst of helemaal zelf. Desgewenst kunt u concepten bewerken of verwijderen. Door gebrek, slechts zijn drie concepten zichtbaar, maar het klikken **toont allen** toont de rest.

  ![ taakbeheer ](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png) {width=50%, height=50%}


* **Gegevens Source**

  De **optie van Gegevens Source** staat u toe om gegevensbronnen te vormen en hen te selecteren wanneer het creëren van een Model van de Gegevens van de Vorm (FDM). Hiermee worden alle gegevensmodelobjecten, eigenschappen en services van de geselecteerde gegevensbronnen beschikbaar gemaakt voor gebruik in het formuliergegevensmodel.
  ![ Gegevens Source ](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png) {width=50%, height=50%}

* **voeg toe**

  De **voegt** optie toe opent een drop-down lijst van componenten die aan de geselecteerde container kunnen worden toegevoegd. In een sectie Adaptief formulier worden bijvoorbeeld de beschikbare componenten weergegeven die aan een formulier kunnen worden toegevoegd. De sneltoets voor het openen van de lijst met componenten is `a` .
  ![ voeg pictogram ](/help/edge/docs/forms/universal-editor/assets/ue-add.png) {width=50%, height=50% toe}

* **Dupliceren**

  De **Dubbele** optie leidt tot een exemplaar van de component, die of in de inhoudsboom of de redacteur wordt geselecteerd.
  ![ Dupliceer pictogram ](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png) {width=50%, height=50%}


* **Schrapping**
De **schrapping** optie schrapt een component, die of in de inhoudsboom of de redacteur wordt geselecteerd.

  ![ Schrapping ](/help/edge/docs/forms/universal-editor/assets/ue-delete.png) {width=50%, height=50%}

### Editor

Met de editor kunt u het formulier bewerken. Het formulier dat u opgeeft op de locatiebalk, wordt weergegeven in het bewerkingsgebied. In de voorbeeldmodus van de editor kunt u met de beschikbare knoppen en koppelingen in het formulier navigeren.
![ Redacteur ](/help/edge/docs/forms/universal-editor/assets/ue-editor.png) {width=50%, height=50%}

## Zie ook

{{universal-editor-see-also}}
