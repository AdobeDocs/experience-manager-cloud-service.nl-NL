---
title: Inhoud aanpassen in een voorbeeldprogramma Reageren
description: Gebruik een voorbeeld van een React-app om te leren hoe u inhoud kunt aanpassen met de functie zonder kop die in AEM as a Cloud Service is ingesteld.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 0%

---


# Inhoud aanpassen in een voorbeeldprogramma Reageren {#customize-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app"
>title="Inhoud aanpassen in een voorbeeld van een React-app"
>abstract="Uw proefversie zonder AEM is geïntegreerd met een voorbeeld van een React-app die u kunt aanpassen."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide"
>title="De editor voor inhoudsfragmenten starten"
>abstract="Uw proefversie zonder AEM is geïntegreerd met een voorbeeldtoepassing React, zodat u kunt zien hoe eenvoudig het voor iedereen is om inhoud onafhankelijk te beheren zonder ontwikkelingstijd.<br><br>Start deze module op een nieuw tabblad door hieronder te klikken en volg deze handleiding."
>additional-url="https://video.tv.adobe.com/v/328618" text="Video over app-intro aanpassen"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide_footer"
>title="In deze module hebt u geleerd hoe u een voorbeeld van een React-app kunt aanpassen.<br><br>Tijd tot de markt: Versneld!<br>Ontwikkelingscycli: Verlaagd!<br><br>Nu begrijpt u hoe eenvoudig het beheren van inhoud zonder kop is voor websites en toepassingen die worden aangedreven door AEM mogelijkheden zonder kop."
>abstract=""

## Voorvertoning van de app weergeven {#preview}

Klik op de knop **De editor voor inhoudsfragmenten starten** opent de editor voor het inhoudsfragment op een nieuw tabblad.

![Inhoudsfragmenteditor](assets/customize-app/content-fragment-editor.png)

De voorbeeldapp die bij de proefversie zonder titel wordt geleverd, wordt geleverd door Content Fragments via GraphQL. Gebruik de editor voor inhoudsfragmenten om de inhoud vertrouwd te maken door een voorvertoning van het voorbeeld weer te geven.

1. Tik of klik op de knop **Voorvertoning** knop rechtsboven in het editorscherm.

1. De demo-app wordt op een nieuw tabblad geopend. De app is voor het fictieve WKND-merk voor outdoorlifestyle. Klik rond om door de voorbeeldinhoud te navigeren.

   ![Voorvertoning van toepassing demo](assets/customize-app/preview-demo-app.png)

1. Ga terug naar het browsertabblad van de editor voor inhoudsfragmenten om door te gaan.

## Een koptekst in de app bewerken {#edit-app}

In de editor voor inhoudsfragmenten wordt de basislay-out van de app weergegeven als een pagina-inhoudsfragment. De **Deelvensters** vertegenwoordigen verschillende pagina&#39;s van de app, die elk een eigen inhoudsfragment zijn. Door deze fragmenten te wijzigen, kunt u de inhoud van de app wijzigen.

1. Tik of klik op **Mtn Biker in Canyon** in de **Deelvensters** sectie.

   ![Tik op Mtn Biker in Canyon-fragment](assets/customize-app/mtn-biker-in-canyon.png)

1. De redacteur opent omhoog het kopbalpaneel van app voor de bergbiker. Elk deelvenster bestaat uit lagen die verschillende afbeeldingen en tekst vertegenwoordigen die de ervaring bepalen.

   ![Deelvensters](assets/customize-app/panels.png)

1. Selecteer de tekstlaag **Mtn Biker in Canyon-tekstlaag**. Hiermee opent u de details van de laag in de editor. De laag bestaat uit meerdere inhoudsfragmenten die de tekst bepalen die in dit deelvenster van de app wordt weergegeven.

   ![Selecteer de motorfiets in Canyon-titel](assets/customize-app/mtn-biker-in-canyon-text-layer.png)

1. Selecteer **Mtn Biker in Canyon-titel** tekstitem. Hiermee opent u de editor voor inhoudsfragmenten.

   ![De koppelingskiezer selecteren in het tekstitem Canyon-titel](assets/customize-app/mtn-biker-in-canyon-title.png)

1. De tekst wijzigen vanuit `Your next great adventure is calling` tot `Choose your own adventure`. De wijziging wordt automatisch opgeslagen door de editor.

1. Tik of klik op **Voorvertoning** rechtsboven in het venster om de wijzigingen te zien. De voorvertoning van de demo-app wordt op een nieuw tabblad geopend.

   ![Voorvertoning van toepassing demo](assets/customize-app/preview-demo-app-text.png)

Zo eenvoudig is het om inhoud in een React-app bij te werken wanneer deze is geïntegreerd in AEM CMS zonder kop.

## Een afbeelding in de app wisselen {#change-image}

Nu u een kopregel in de app hebt gewijzigd, kunt u proberen een afbeelding te wijzigen.

1. Keer terug naar het browserlusje van de redacteur van het Fragment van de Inhoud.

1. U moet terugkeren naar de juiste plaats in de editor voor inhoudsfragmenten. De broodkruimels bij top-left van de redacteur tonen waar u in uw inhoudshiërarchie bent. Tik of klik op **Mtn Biker in Canyon** in de breadcrumbs om terug te keren naar die pagina.

   ![Broodkruimels](assets/customize-app/breadcrumbs.png)

1. Selecteer **Mtn Biking - Biker** afbeeldingslaag. Hiermee opent u de editor voor inhoudsfragmenten

   ![Afbeeldingsfragment bewerken](assets/customize-app/mtn-biking-biker.png)

1. Tik of klik op de knop **X** om de fietsafbeelding te verwijderen. De afbeelding verdwijnt en in de editor wordt een fout weergegeven omdat de afbeelding vereiste gegevens is voor dit model van inhoudsfragment.

   ![Afbeelding verwijderd uit fragment](assets/customize-app/mtn-biking-biker-no-image.png)

1. Tik of klik op **Element toevoegen**.

1. De **Element selecteren** wordt geopend en het pad **voorbeeldapp** > **en** > **afbeeldingsbestanden** wordt automatisch voor u geselecteerd.

1. Selecteer de afbeelding `biker-yellow.png` tikken of klikken **Selecteren**.

   ![Element selecteren](assets/customize-app/select-asset.png)

1. De afbeelding van de fietser wordt vervangen door de geselecteerde afbeelding. De editor slaat de wijzigingen automatisch op.

   ![Bewerkt fragment van hypersterafbeelding](assets/customize-app/mtn-biking-biker-edited.png)

1. Tik of klik op **Voorvertoning** rechtsboven in het venster om de wijzigingen te zien. De voorvertoning van de demo-app wordt op een nieuw tabblad geopend. Klik op Vernieuwen in de browser en u ziet de nieuwe fietsafbeelding met gele korte tekst in de app.

Het is zo eenvoudig om afbeeldingen en middelen in uw apps bij te werken met AEM CMS zonder kop.

## Een verwijzing toevoegen aan een nieuw inhoudsfragment in de app {#create-moment}

Nu u de afbeelding van de fietser hebt bijgewerkt, gaan we door hoe u nieuwe inhoud aan een app toevoegt door een nieuw inhoudsfragment te maken en ernaar te verwijzen. U voegt een productcall-out beheerd door een &quot;shoppable moment&quot; inhoudsfragment toe aan het tweede paneel van de app.

![Voorbeeld van een schokkend moment](assets/customize-app/example-shoppable-moment.png)

1. Keer terug naar het browserlusje van de redacteur van het Fragment van de Inhoud.

1. U moet terugkeren naar de juiste plaats in de editor voor inhoudsfragmenten. De broodkruimels bij top-left van de redacteur tonen waar u in uw inhoudshiërarchie bent. Tik of klik op **WKND Home** in de breadcrumbs om terug te keren naar die pagina.

   ![Teruggaan naar het layoutscherm](assets/customize-app/breadcrumbs-2.png)

1. Selecteer **Mtn Biker op WKND Yellow** deelvenster.

   ![Maak een schokkend moment](assets/customize-app/mtn-biker-on-wknd-yellow.png)

1. Selecteer **Mtn Biking - Shopable** laag.

   ![Schorpbare tijdlaag selecteren](assets/customize-app/mtn-biking-shoppable.png)

1. Als u een nieuwe call-out wilt maken in dit deelvenster, moet u een nieuw, verwisselbaar moment maken met een inhoudsfragment. Tik of klik op de knop **+ Nieuw fragment maken** knop.

   ![Een schokkend moment toevoegen](assets/customize-app/create-new-fragment.png)

1. U moet eerst een model kiezen waarop u het nieuwe inhoudsfragment wilt baseren. Selecteer **Opstuitbaar mompitem** model van het **Inhoudsfragmentmodel** vervolgkeuzelijst.

1. Geef het inhoudsfragment een naam. Voer bijvoorbeeld `Shorts` in de **Naam** veld.

   ![Geef het onoverzichtelijke moment een naam](assets/customize-app/new-content-fragment.png)

1. Tik of klik op **Maken en openen**.

1. De editor wordt geopend voor het nieuwe inhoudsfragment.

1. Geef het schokbare moment een naam in de **Tekst** velden zoals `Yellow shorts`.

1. Waarden instellen voor **X** en **Y**. Dit is waar deze callout op het paneel zou moeten worden geregeld. Wijzigingen in het fragment worden automatisch opgeslagen door de editor
   * **X**: `-18`
   * **Y**: `-28`

   ![Het schokkende moment bewerken](assets/customize-app/edit-shoppable-moment.png)

1. Tik of klik op **Voorvertoning** rechtsboven in het venster om de wijzigingen te zien. De voorvertoning van de demo-app wordt op een nieuw tabblad geopend. Klik verfrissen zich op browser om het plaatsen te testen en aanpassingen aan te brengen zoals nodig in de redacteur.

Nu begrijpt u hoe u nieuwe inhoud kunt maken en ernaar kunt verwijzen als een inhoudsfragment in uw app zonder ontwikkelingscycli.
