---
title: Aan de slag met de Experience Modernization Agent
description: Leer de eerste stappen om snel productief te worden met de Agent van de Modernisering van de Ervaring gebruikend de Console van de Modernisering van de Ervaring.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: c80ce5a9fc5f208fd910d5cef72225085248fb4d
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 0%

---


# Aan de slag met de Experience Modernization Agent {#getting-started}

Leer de eerste stappen om snel productief te worden met de Agent van de Modernisering van de Ervaring gebruikend de Console van de Modernisering van de Ervaring.

>[!NOTE]
>
>Als u geïnteresseerd bent in het gebruik van de Experience Modernization Console, kunt u toegang aanvragen voor een vloeiende instapervaring.

## Een Edge Delivery GitHub-opslagplaats voorbereiden {#prepare-repo}

1. Selecteer een [&#x200B; plaats van Edge Delivery Services &#x200B;](/help/edge/overview.md) voor gebruik met de Console van de Modernisering van de Ervaring.
   * Dit kan een bestaand project van Edge Delivery Services zijn of u kunt nieuwe tot stand brengen na het [&#x200B; ontwikkelaarsleerprogramma &#x200B;](https://www.aem.live/developer/tutorial) gebruikend de [&#x200B; boilerplate bewaarplaats.](https://github.com/adobe/aem-boilerplate)
1. Zorg ervoor dat [&#x200B; AEMY GitHub app &#x200B;](https://github.com/apps/aem-aemy) in de bewaarplaats geïnstalleerd is.
   * Hierdoor kan de console uw code inspecteren.
1. Zorg ervoor dat de [&#x200B; app van GitHub van de Synchronisatie van de Code van AEM &#x200B;](https://github.com/apps/aem-code-sync) in de bewaarplaats geïnstalleerd is.
   * Zo kan Edge Delivery Services uw code synchroniseren.
   * Als uw repo is gebaseerd op de zelfstudie, is deze stap al voltooid.

## Open de Experience Moderation Console {#open-console}

1. Ga naar [`aemcoder.adobe.io`.](https://aemcoder.adobe.io)
1. Meld u aan bij uw Adobe ID.

## Sluit uw GitHub-opslagplaats aan {#connect-repo}

De console vraagt u om een repository wanneer u zich voor het eerst aanmeldt.

![&#x200B; eerste teken binnen het scherm van de console &#x200B;](assets/first-sign-on.png)

1. Klik **verbinden bewaarplaats**.
1. Hierdoor wordt de AEMY-app op een nieuw browsertabblad geopend. Klik **autoriseer AEM AEMY**.
1. Terug in de console, uitgezochte **Eigenaar**, **Bewaarplaats**, en **de selectie van de Tak** en klik **Controle aan werkruimte**.
   ![&#x200B; het Verbinden met het project GitHub &#x200B;](assets/connect-to-github-project.png)
1. Wanneer ertoe aangezet om **bestaande werkruimte** te vervangen, klik **vervangen werkruimte**.
   ![&#x200B; vervangt bestaande werkruimte &#x200B;](assets/replace-existing-workspace.png)

Uw project GitHub wordt nu verbonden met de console en u bent op het huisscherm.

![&#x200B; Het huis van de Console &#x200B;](assets/console-home.png)

## Vragen starten {#start-prompting}

Nu uw console tot uw code kan toegang hebben, bent u klaar beginnen het vragen.

1. Om aan de slag te gaan, kunt u de inhoud van een site importeren:
   * &quot;Migreer de pagina `https://wknd-trendsetters.site`.&quot;
1. Hiermee importeert u de inhoud van de site.
   * De console neemt onderscheid van zorgen waar en behandelt inhoud en presentatie afzonderlijk.
   * De eerste import van de inhoud van een site kan enkele minuten in beslag nemen.
   * De console stelt u met aan de gang zijnde terugkoppelt aangezien het zijn werk, met inbegrip van een overzicht van zijn geplande stappen begint.
     ![&#x200B; de invoer van de Inhoud &#x200B;](assets/content-import.png)
1. Zodra de plaats wordt ingevoerd, toont het **Workspace** paneel de pagina&#39;s. Selecteer een pagina waarvan u een voorvertoning wilt weergeven in het rechterdeelvenster.
   ![&#x200B; ingevoerde Inhoud &#x200B;](assets/content-imported.png)
1. Nu u inhoud hebt, kunt u vragen of u de stijlen uit dezelfde bron wilt importeren.
   * &quot;Importeer de algemene stijlen uit `https://wknd-trendsetters.site`.&quot;
1. Net als bij het importeren van de eerste inhoud kan het importeren enkele minuten duren en geeft de console feedback tijdens het verwerken van uw verzoek en het importeren van de stijlen. Zodra de taak volledig is, klik **verfrissen voorproef** in het juiste paneel om de gestileerde inhoud te bekijken.
   ![&#x200B; Geïmporteerde Stijlen &#x200B;](assets/styles-imported.png)

Nu worden zowel de inhoud als de stijlen in de console geïmporteerd.

## Inhoud uploaden {#upload-content}

Om uw inhoud aan [&#x200B; Document Authoring &#x200B;](https://da.live) te uploaden:

1. Zorg ervoor u in de **mening van de Inhoud** bent en klik dan de **uploadt inhoud** knoop op top-right.
   * Door gebrek bent u in **Inhoud** mening wanneer het ingaan van de console.
   * Uw weergave wordt aangegeven met het gemarkeerde pictogram in het zijpaneel links in de console.
1. **uploadt inhoud** dialoog opent met bestemmingsorg en repo vooraf gevuld van uw `fstab.yaml`.
   * Als een `fstab.yaml` niet aanwezig in uw verbonden bewaarplaats is, zult u uw **Organisatie** en **Bewaarplaats** manueel moeten ingaan.
   * Als u de tekstbouwsteen hebt gebruikt, wordt een `fstab.yaml` weergegeven.
1. Selecteer de dossiers u wilt uploaden en **klikken uploadt**.
   ![&#x200B; uploadt inhoudsdialoog &#x200B;](assets/upload-content.png)
1. De console wijst op uploadproces door **te graaien uploadt** knoop.
   ![&#x200B; Uploading &#x200B;](assets/uploading.png)
1. Zodra volledig, verschijnt een bericht bij de bodem van de console.
   ![&#x200B; Mening in AEM &#x200B;](assets/view-in-aem.png)

Om tot de geuploade inhoud in Document Authoring toegang te hebben, klikt u naar keuze **Mening in AEM** in het bericht wanneer uploaden voltooit, of navigeert aan `https://da.live/#/{organization}/{repository}`.

![&#x200B; Inhoud in Document Authoring &#x200B;](assets/content-in-document-authoring.png)

De geïmporteerde inhoud bevindt zich nu in Document Authoring.

## Wijzigingen in code duwen {#push-code-changes}

Zodra u met de veranderingen tevreden bent u aan uw code hebt aangebracht, kunt u hen aan uw bewaarplaats duwen GitHub.

1. De schakelaar aan **mening van de Code** (`</>` pictogram in linkerzijbalk) en toen **Veranderingen van de it** lusje (takpictogram bij top-right).
   ![&#x200B; mening van de Code &#x200B;](assets/code-view-git-changes.png)
1. Als sommige bestanden in de gewijzigde lijst niet worden bijgehouden, klikt u op de knop `+` om ze te plaatsen.
1. Klik de **GitHub acties** knoop bij top-right en selecteer dan **Duw** van drop-down.
1. In de **Duw verandert** dialoog, verkies om veranderingen in nieuwe PR (gebrek) of de huidige tak te duwen en **te klikken bevestigt** om te duwen.
   * Bij twijfel kunt u naar de huidige vertakking duwen om de zaken eenvoudig te houden.
1. Zodra volledig, verschijnt een bericht bij de bodem van de console.
   ![&#x200B; PR van de Mening &#x200B;](assets/view-pr.png)

Als u wenst om tot de geduwde veranderingen in GitHub direct toegang te hebben, klik **PR van de Mening** in het bericht wanneer de duw voltooit.

![&#x200B; Code in GitHub &#x200B;](assets/code-in-github.png)

Uw code is nu in GitHub.

## Site voorvertonen {#preview-site}

De wijzigingen in de voorvertoningsomgeving weergeven:

1. Ga terug naar Document Authoring.
   * Het kan nog in een browser lusje open zijn u na het klikken van **Mening in AEM** na het uploaden van de inhoud opende.
   * Of ga naar `https://da.live/#/{organization}/{repository}`
1. Open een van de pagina&#39;s die u eerder naar AEM hebt geüpload.
1. Klik het pictogram van het papiervliegtuig (hoogste recht) en selecteer **Voorproef**.
   ![&#x200B; publiceer aan voorproef &#x200B;](assets/publish-to-preview.png)

Gefeliciteerd! De gemigreerde inhoud en stijlen zijn nu live in de AEM-voorvertoningsomgeving.

![&#x200B; Gepubliceerde voorproefinhoud &#x200B;](assets/published-preview.png)

Als u uw code naar een andere vertakking dan `main` hebt geduwd, zal de voorproef die van de Authoring van het Document wordt geopend de stijlen niet tonen. Wijzig de vertakking door de URL van de voorvertoning bij te werken. De stijlen worden dan weergegeven.

## Aanvullende bronnen {#additional-resources}

De volgende documenten kunnen nuttig zijn aangezien u de Agent van de Modernisering van de Ervaring en zijn console blijft onderzoeken.

* [&#x200B; Console van de Modernisering van de Ervaring &#x200B;](/help/ai-in-aem/agents/modernization/console.md) - Details op de console, zijn meningen, opties, en mogelijkheden
* [&#x200B; de ontwikkelaarsleerprogramma van Edge Delivery Services &#x200B;](https://www.aem.live/developer/tutorial) - Nuttig als u aan de projecten van AEM en van Edge Delivery Services nieuw bent
* [&#x200B; Authoring van het Document &#x200B;](https://da.live) - Nuttig als u aan Document Authoring voor inhoudsbeheer nieuw bent
