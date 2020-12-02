---
title: Deelnemen aan workflows
description: Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 1%

---


# Deelnemen aan workflows {#participating-in-workflows}

Workflows bevatten doorgaans stappen die vereisen dat een persoon een activiteit op een pagina of element uitvoert. De werkstroom selecteert een gebruiker of groep om de activiteit uit te voeren en wijst een het werkpunt aan die persoon of groep toe. De gebruiker ontvangt een melding en kan vervolgens de juiste actie ondernemen:

* [Meldingen weergeven](#notifications-of-available-workflow-actions)
* [Een deelnemersstap voltooien](#completing-a-participant-step)
* [Een deelnemersstap delegeren](#delegating-a-participant-step)
* [Stap terug op een Stap van de Deelnemer uitvoeren](#performing-step-back-on-a-participant-step)
* [Open een workflowitem om details weer te geven (en om handelingen uit te voeren)](#opening-a-workflow-item-to-view-details-and-take-actions)
* [Bekijk de Werkstroom Payload (Meerdere Middelen)](#viewing-the-workflow-payload-multiple-resources)

## Meldingen van beschikbare workflowacties {#notifications-of-available-workflow-actions}

Wanneer u een werkitem wordt toegewezen (bijvoorbeeld **Inhoud goedkeuren**), worden verschillende waarschuwingen en/of meldingen weergegeven:

* Uw [meldingsindicator](/help/sites-cloud/authoring/getting-started/inbox.md) (werkbalk) wordt verhoogd:

   ![Berichtwerkbalk](/help/sites-cloud/authoring/assets/workflows-notifications.png)

* Het item wordt vermeld in uw melding [Inbox](/help/sites-cloud/authoring/getting-started/inbox.md):

   ![Meldingen in Postvak IN](/help/sites-cloud/authoring/assets/workflows-inbox.png)

* Wanneer u de pagina-editor gebruikt, wordt de statusbalk weergegeven:
   * de naam van de workflow(en) die op de pagina wordt toegepast; bijvoorbeeld Verzoek om activering.
   * Alle handelingen die beschikbaar zijn voor de huidige gebruiker voor de huidige stap van de workflow. bijvoorbeeld Voltooid, Delegeren, Details weergeven.
   * Het aantal werkstromen dat op de pagina van toepassing is. U kunt:
      * Gebruik de pijlen links/rechts om door de statusinformatie van de verschillende workflows te navigeren.
      * Klik/tik op het daadwerkelijke aantal om een drop-down lijst van alle toepasselijke werkschema&#39;s te openen, dan selecteer het werkschema u in de statusbar wilt tonen.

   ![Pagina met meerdere workflows](/help/sites-cloud/authoring/assets/workflows-multiple.png)

   >[!NOTE]
   >
   >De statusbalk is alleen zichtbaar voor gebruikers met workflowbevoegdheden. bijvoorbeeld leden van de groep `workflow-users`.
   >
   >
   >Handelingen worden weergegeven wanneer de huidige gebruiker rechtstreeks betrokken is bij de huidige stap van de workflow.

* Wanneer **Timeline** open is voor de resource, wordt de workflowstap weergegeven. Wanneer u op de waarschuwingsbanner klikt of tikt, worden ook de beschikbare acties weergegeven:

   ![Workflow in de tijdlijn](/help/sites-cloud/authoring/assets/workflows-timeline.png)

### Een deelnemersstap {#completing-a-participant-step} voltooien

U kunt een item voltooien zodat de workflow naar de volgende stap kan gaan.

Op deze actie kunt u aangeven:

* **Volgende stap**: de volgende te nemen stap; u kunt uit een lijst selecteren die wordt verstrekt
* **Opmerking**: indien vereist

U kunt een deelnemersstap uitvoeren vanuit:

* [Inbox](#completing-a-participant-step-inbox)
* [De pagina-editor](#completing-a-participant-step-page-editor)
* [De tijdlijn](#completing-a-participant-step-timeline)
* Wanneer [een werkschemapunt openen om details](#opening-a-workflow-item-to-view-details-and-take-actions) te bekijken.

#### Een deelnemersstap invullen - Postvak {#completing-a-participant-step-inbox}

Voer de volgende procedure uit om het werkitem te voltooien:

1. Open **[AEM Inbox](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Volledig** van de toolbar.
1. Het dialoogvenster **Werkitem voltooien** wordt geopend. Selecteer **Volgende Stap** van de drop-down selecteur en voeg **Commentaar** indien nodig toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap voltooien - Pagina-editor {#completing-a-participant-step-page-editor}

Voer de volgende procedure uit om het werkitem te voltooien:

1. Open de [pagina voor het uitgeven](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Selecteer **Volledig** in de statusbalk boven in het scherm.
1. Het dialoogvenster **Werkitem voltooien** wordt geopend. Selecteer **Volgende Stap** van de drop-down selecteur en voeg **Commentaar** indien nodig toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap voltooien - tijdlijn {#completing-a-participant-step-timeline}

U kunt ook de tijdlijn gebruiken om een stap te voltooien en uit te voeren:

1. Selecteer de vereiste pagina en open **Timeline** (of open **Timeline** en selecteer de pagina):

   ![Een stap voltooien](/help/sites-cloud/authoring/assets/workflows-timeline-completing.png)

1. Klik of tik op de waarschuwingsbanner om beschikbare handelingen weer te geven. Selecteer **Geavanceerd**:

   ![De stap vooruit](/help/sites-cloud/authoring/assets/workflows-timeline-advance.png)

1. Afhankelijk van de workflow kunt u de volgende stap selecteren:

   ![Volgende stap selecteren](/help/sites-cloud/authoring/assets/workflows-next-step.png)

1. Selecteer **Geavanceerd** om de handeling te bevestigen.

### Een deelnemersstap {#delegating-a-participant-step} delegeren

Als een stap aan u is toegewezen, maar om het even welke reden u geen actie kunt ondernemen, kunt u de stap aan een andere gebruiker of een groep delegeren.

De gebruikers die voor delegatie beschikbaar zijn hangen af van wie het het werkpunt werd toegewezen:

* Als het het werkpunt aan een groep werd toegewezen, zijn de groepsleden beschikbaar.
* Als het het werkpunt aan een groep werd toegewezen en dan aan een gebruiker werd gedelegeerd, zijn de groepsleden en de groep beschikbaar.
* Als het het werkpunt aan één enkele gebruiker werd toegewezen, kan het het werkpunt niet worden afgevaardigd.

Op deze actie kunt u aangeven:

* **Gebruiker**: de gebruiker u aan wilt delegeren; u kunt uit een lijst selecteren die wordt verstrekt
* **Opmerking**: indien vereist

U kunt een deelnemersstap delegeren vanuit:

* [Inbox](#delegating-a-participant-step-inbox)
* [De pagina-editor](#delegating-a-participant-step-page-editor)
* [De tijdlijn](#delegating-a-participant-step-timeline)
* Wanneer [een werkschemapunt openen om details](#opening-a-workflow-item-to-view-details-and-take-actions) te bekijken.

#### Een deelnemersstap delegeren - Postvak {#delegating-a-participant-step-inbox}

Gebruik de volgende procedure om een het werkpunt te delegeren:

1. Open **[AEM Inbox](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Delegeren** van de toolbar.
1. Het dialoogvenster wordt geopend. Geef de **Gebruiker** op in de keuzelijst (dit kan ook een groep zijn) en voeg indien nodig een **Opmerking** toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap delegeren - Pagina-editor {#delegating-a-participant-step-page-editor}

Gebruik de volgende procedure om een het werkpunt te delegeren:

1. Open de [pagina voor het uitgeven](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Selecteer **Delegeren** van de statusbar bij de bovenkant.
1. Het dialoogvenster wordt geopend. Geef de **Gebruiker** op in de keuzelijst (dit kan ook een groep zijn) en voeg indien nodig een **Opmerking** toe.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Een deelnemersstap delegeren - tijdlijn {#delegating-a-participant-step-timeline}

U kunt de tijdlijn ook gebruiken om een stap te delegeren en/of toe te wijzen:

1. Selecteer de vereiste pagina en open **Timeline** (of open **Timeline** en selecteer de pagina).
1. Klik of tik op de waarschuwingsbanner om beschikbare handelingen weer te geven. Selecteer **Toegewezen wijzigen**:

   ![Stap delegeren](/help/sites-cloud/authoring/assets/workflows-delegate.png)

1. Geef een nieuwe ontvanger op:

   ![Toewijzing wijzigen](/help/sites-cloud/authoring/assets/workflows-assignee.png)

1. Selecteer **Toewijzen** om de handeling te bevestigen.

### Stap terug op een Stap van de Deelnemer {#performing-step-back-on-a-participant-step} uitvoeren

Als u ontdekt dat een stap, of een reeks stappen, moet worden herhaald kunt u achteruit stappen. Op deze manier kunt u een stap selecteren die eerder in de workflow is opgetreden voor opwerking. De werkstroom keert aan de stap terug u specificeert, dan gaat van daar te werk.

Op deze actie kunt u aangeven:

* **Vorige stap**: de stap waarop moet worden teruggezet; u kunt uit een lijst selecteren die wordt verstrekt
* **Opmerking**: indien vereist

U kunt stap terug op een deelnemersstap van één van beiden uitvoeren:

* [Inbox](#performing-step-back-on-a-participant-step-inbox)
* [De pagina-editor](#performing-step-back-on-a-participant-step-page-editor)
* [De tijdlijn](#performing-step-back-on-a-participant-step-timeline)
* Wanneer [een werkschemapunt openen om details](#opening-a-workflow-item-to-view-details-and-take-actions) te bekijken.

#### Het uitvoeren van Stap terug op een Stap van de Deelnemer - Inbox {#performing-step-back-on-a-participant-step-inbox}

Gebruik de volgende procedure om terug te gaan:

1. Open **[AEM Inbox](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Stap terug** om het dialoogvenster te openen.
1. Geef de **Vorige stap** op en voeg een **opmerking** toe, indien nodig.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Stap terug op een Stap van de Deelnemer uitvoeren - de Redacteur van de Pagina {#performing-step-back-on-a-participant-step-page-editor}

Gebruik de volgende procedure om terug te gaan:

1. Open de [pagina voor het uitgeven](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Selecteer **Stap terug** van de statusbar bij de bovenkant.
1. Geef de **Vorige stap** op en voeg een **opmerking** toe, indien nodig.
1. Gebruik **OK** om de stap te voltooien (of **Annuleren** om de handeling af te breken).

#### Stap terug op een Stap van de Deelnemer uitvoeren - Chronologie {#performing-step-back-on-a-participant-step-timeline}

U kunt de tijdlijn ook gebruiken om terug te gaan (stap) naar een vorige stap:

1. Selecteer de vereiste pagina en open **Timeline** (of open **Timeline** en selecteer de pagina).
1. Klik of tik op de waarschuwingsbanner om beschikbare handelingen weer te geven. Selecteer **Terugdraaien**:

   ![Een stap terugdraaien](/help/sites-cloud/authoring/assets/workflows-roll-back.png)

1. Geef de stap op waarnaar de workflow moet terugkeren:

   ![Stap opgeven](/help/sites-cloud/authoring/assets/workflows-roll-back-step.png)

1. Selecteer **Terugdraaien** om de handeling te bevestigen.

### Het openen van een Punt van het Werkschema om Details (en Acties te bekijken) {#opening-a-workflow-item-to-view-details-and-take-actions}

Bekijk details van het werkstroomonderdeel en voer de juiste handelingen uit.

De workflowdetails worden weergegeven op tabbladen en de juiste acties zijn beschikbaar op de werkbalk:

* **** WORKITEMtab:

   ![Tabblad WORKITEM](/help/sites-cloud/authoring/assets/workflows-work-item.png)

* **WORKFLOW** INFOtab:

   ![WORKFLOW, tabblad](/help/sites-cloud/authoring/assets/workflows-workflow-info.png)

   Als de Stages van het Werkschema voor het model zijn gevormd, kunt u de vooruitgang volgens deze bekijken: <!--If [Workflow Stages](/help/sites-developing/workflows.md#workflow-stages) have been configured for the model, you can view the progress according to these:-->

   ![Workflowfasen](/help/sites-cloud/authoring/assets/workflows-workflow-stages.png)

* **** COMMENTStab:

   ![Tabblad Opmerkingen](/help/sites-cloud/authoring/assets/workflows-comments.png)

U kunt de details van het werkitem openen vanuit:

* [Inbox](#performing-step-back-on-a-participant-step-inbox)
* [De pagina-editor](#performing-step-back-on-a-participant-step-page-editor)

#### Workflow Details openen - Postvak {#opening-workflow-details-inbox}

U opent als volgt een workflowitem en bekijkt de details:

1. Open **[AEM Inbox](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Openen** om de informatietabbladen te openen.
1. Selecteer zo nodig de gewenste actie, geef details op en bevestig de **OK** (of **Annuleren**).
1. Gebruik **Save** of **Cancel** om af te sluiten.

#### Workflow Details openen - Pagina-editor {#opening-workflow-details-page-editor}

U opent als volgt een workflowitem en bekijkt de details:

1. Open de [pagina voor het uitgeven](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Selecteer **Details weergeven** in de statusbalk om de informatietabbladen te openen.
1. Selecteer zo nodig de gewenste actie, geef details op en bevestig de **OK** (of **Annuleren**).
1. Gebruik **Save** of **Cancel** om af te sluiten.

### Het bekijken van de Payload van het Werkschema (Veelvoudige Middelen) {#viewing-the-workflow-payload-multiple-resources}

U kunt details van de lading bekijken verbonden aan de werkschemainstantie. In eerste instantie worden de bronnen in het pakket weergegeven, waarna u de afzonderlijke pagina&#39;s kunt weergeven.

Om de lading, en middelen, van de werkschemainstantie te bekijken:

1. Open **[AEM Inbox](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Selecteer het werkstroomitem waarop u actie wilt uitvoeren (tik op de miniatuur of klik erop).
1. Selecteer **Payload weergeven** op de werkbalk om het dialoogvenster te openen.
   * Aangezien een workflowpakket slechts een verzameling aanwijzers naar paden in de repository is, kunt u de items hier toevoegen/verwijderen/wijzigen om aan te passen wat er in het workflowpakket naar wordt verwezen. Met de component **Brondefinitie** kunt u nieuwe items toevoegen.
1. U kunt de koppelingen gebruiken om de afzonderlijke pagina&#39;s te openen.
