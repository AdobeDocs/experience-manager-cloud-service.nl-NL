---
title: Inhoud aanpassen in een voorbeeldprogramma Reageren
description: Gebruik een voorbeeld van een React-app om te leren hoe u inhoud kunt aanpassen met de functie zonder kop die in AEM as a Cloud Service is ingesteld.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1017'
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
>abstract="Laten we nu eens bekijken hoe creatie van inhoud zonder kop werkt. Uw proefversie zonder AEM is geïntegreerd met een voorbeeldtoepassing React, zodat u kunt zien hoe eenvoudig het voor iedereen is om inhoud onafhankelijk te beheren zonder ontwikkelingstijd.<br><br>Start deze module op een nieuw tabblad door hieronder te klikken en volg deze handleiding."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide_footer"
>title="In deze module hebt u geleerd hoe u een voorbeeld van een React-app kunt aanpassen.<br><br>Tijd naar markt: versneld!<br>Ontwikkelingscycli: gereduceerd!<br><br>Nu begrijpt u hoe eenvoudig het beheren van inhoud zonder kop is voor websites en toepassingen die worden aangedreven door AEM mogelijkheden zonder kop."
>abstract=""

## Voorvertoning van de app weergeven {#preview}

U start in de editor voor inhoudsfragmenten met de voorbeeldtoepassing die bij de proefversie zonder AEM is geleverd, al geladen. De voorbeeld-app wordt aangedreven door Content Fragments die via GraphQL worden geleverd. Gebruik de editor voor inhoudsfragmenten om de editor te leren kennen door een voorbeeld van de voorbeeld-app te bekijken.

1. Selecteer de **Voorvertoning** knop rechtsboven in het editorscherm.

1. De demo-app wordt op een nieuw tabblad geopend. De app is voor het fictieve WKND-merk voor outdoorlifestyle. Schuif omlaag op de pagina om door de voorbeeldinhoud te navigeren.

1. Ga terug naar het browsertabblad van de editor voor inhoudsfragmenten om door te gaan.

![Een voorvertoning van de app weergeven](assets/do-not-localize/preview-app-1.png)

## Een koptekst bewerken in de app {#edit-app}

In de editor voor inhoudsfragmenten wordt de basislay-out van de app weergegeven als een pagina-inhoudsfragment. De **Deelvensters** vertegenwoordigen verschillende pagina&#39;s van de app, die elk een eigen inhoudsfragment zijn. Door deze fragmenten te wijzigen, kunt u de inhoud van de app wijzigen.

1. Selecteren **Mtn Biker in Canyon** in de **Deelvensters** sectie.

   ![Tekstvenster selecteren](assets/do-not-localize/edit-header-1.png)

1. De redacteur opent omhoog het kopbalpaneel van app voor de bergbiker. Elk deelvenster bestaat uit lagen die verschillende afbeeldingen en tekst vertegenwoordigen die de ervaring bepalen.

1. Selecteer de tekstlaag **Mtn Biker in Canyon-tekstlaag** om de details van de laag in de redacteur te openen. De laag bestaat uit meerdere inhoudsfragmenten die de tekst bepalen die in dit deelvenster van de app wordt weergegeven.

1. Selecteer de **Mtn Biker in Canyon-titel** tekstitem. Hiermee opent u de editor voor inhoudsfragmenten waarin de inhoud van dit fragment wordt weergegeven en waarin u het fragment kunt wijzigen.

1. De tekst wijzigen vanuit `Your next great adventure is calling` tot `Choose your own adventure`. De wijziging wordt automatisch opgeslagen door de editor.

1. Selecteren **Voorvertoning** rechtsboven in het venster om de wijzigingen te zien. De voorvertoning van de demo-app wordt op een nieuw tabblad geopend.

   ![Voorvertoning van toepassing demo](assets/do-not-localize/edit-header-5-6.png)

Zo eenvoudig is het om inhoud in een React-app bij te werken wanneer deze is geïntegreerd in AEM CMS zonder kop.

## Een afbeelding wisselen in de app {#change-image}

Nu u een kopregel in de app hebt gewijzigd, kunt u proberen een afbeelding te wijzigen.

1. Ga vanuit de voorvertoning terug naar het browsertabblad van de editor voor inhoudsfragmenten.

1. U moet terugkeren naar de juiste plaats in de editor voor inhoudsfragmenten. De broodkruimels bij top-left van de redacteur tonen waar u in uw inhoudshiërarchie bent. Selecteren **Mtn Biker in Canyon** in de breadcrumbs om terug te keren naar die pagina.

   ![Broodkruimels](assets/do-not-localize/swap-image-2.png)

1. Selecteer de **Mtn Biking - Biker** afbeeldingslaag Hiermee opent u de editor voor inhoudsfragmenten

1. Selecteer de **X** om de fietsafbeelding te verwijderen. De afbeelding verdwijnt en in de editor wordt een fout weergegeven omdat de afbeelding vereiste gegevens is voor dit model van inhoudsfragment.

   ![Afbeelding verwijderen uit fragment](assets/do-not-localize/swap-image-4.png)

1. Selecteren **Element toevoegen** en vervolgens **Zoeken in middelen** in het pop-upmenu.

1. De **Element selecteren** wordt geopend en het pad **voorbeeldapp** > **en** > **afbeeldingsbestanden** wordt automatisch voor u geselecteerd.

1. Selecteer de afbeelding `biker-yellow.png` en selecteer vervolgens **Selecteren**.

1. De afbeelding van de fietser wordt vervangen door de geselecteerde afbeelding. De editor slaat de wijzigingen automatisch op.

1. Selecteren **Voorvertoning** rechtsboven in het venster om de wijzigingen te zien. De voorvertoning van de demo-app wordt op een nieuw tabblad geopend. Klik op Vernieuwen in de browser en u ziet de nieuwe fietsafbeelding met gele korte tekst in de app.

Het is zo eenvoudig om afbeeldingen en middelen in uw apps bij te werken met AEM CMS zonder kop.

## Een verwijzing toevoegen aan een nieuw inhoudsfragment in de app {#create-moment}

Nu u de afbeelding van de fietser hebt bijgewerkt, gaan we door hoe u nieuwe inhoud aan een app toevoegt door een nieuw inhoudsfragment te maken en ernaar te verwijzen. U voegt een productcall-out beheerd door een &quot;shoppable moment&quot; inhoudsfragment toe aan het tweede paneel van de app.

![Voorbeeld van een schokkend moment](assets/do-not-localize/example-shoppable-moment.png)

1. Keer terug naar het browserlusje van de redacteur van het Fragment van de Inhoud van het voorproeflusje.

1. U moet terugkeren naar de juiste plaats in de editor voor inhoudsfragmenten. De broodkruimels bij top-left van de redacteur tonen waar u in uw inhoudshiërarchie bent. Selecteren **WKND Home** in de breadcrumbs om terug te keren naar die pagina.

1. Selecteer de **Mtn Biker op WKND Yellow** deelvenster.

1. Selecteer de **Mtn Biking - Shopable** laag.

1. Als u een call-out wilt maken in dit deelvenster, maakt u een schokkend moment met een inhoudsfragment. Selecteer de **+ Nieuw fragment maken** knop.

   ![Een schokkend moment toevoegen](assets/do-not-localize/add-reference-1-5.png)

1. U moet eerst een model kiezen waarop u het nieuwe inhoudsfragment wilt baseren. Selecteer de **Opstuitbaar mompitem** model van het **Inhoudsfragmentmodel** vervolgkeuzelijst.

1. Geef het inhoudsfragment een naam. Voer bijvoorbeeld `Shorts` in de **Naam** veld.

1. Selecteren **Maken en openen**.

   ![Geef het onoverzichtelijke moment een naam](assets/do-not-localize/add-reference-6-7-8.png)

1. De editor wordt geopend voor het nieuwe inhoudsfragment.

1. Geef het schokbare moment een naam in de **Tekst** velden zoals `Yellow shorts`.

1. Waarden instellen voor **X** en **Y**. Dit is waar deze callout op het paneel zou moeten worden geregeld. Wijzigingen in het fragment worden automatisch opgeslagen door de editor

   * **X**: `-5`
   * **Y**: `-10`

1. Selecteren **Voorvertoning** rechtsboven in het venster om de wijzigingen te zien. De voorvertoning van de demo-app wordt op een nieuw tabblad geopend. Klik verfrissen zich op browser om het plaatsen te testen en aanpassingen aan te brengen zoals nodig in de redacteur.

   ![Voorvertoning](assets/do-not-localize/add-reference-10-11-12.png)

Nu begrijpt u hoe u nieuwe inhoud kunt maken en ernaar kunt verwijzen als een inhoudsfragment in uw app zonder ontwikkelingscycli.
