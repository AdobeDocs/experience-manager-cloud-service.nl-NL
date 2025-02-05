---
title: Aan de slag-handleiding voor ontwikkelaars voor WYSIWYG Authoring met Edge Delivery Services
description: Deze gids zal u aan de slag met een nieuwe plaats van Adobe Experience Manager gebruikend Edge Delivery Services en de Universele Redacteur voor de inhoud van WYSIWYG authoring krijgen.
feature: Edge Delivery Services
exl-id: a71184a7-c954-442e-b276-99edc6d2acd8
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 0%

---


# Aan de slag-handleiding voor ontwikkelaars voor WYSIWYG Authoring met Edge Delivery Services {#edge-dev-getting-started}

Deze gids zal u aan de slag met een nieuwe plaats van Adobe Experience Manager gebruikend Edge Delivery Services en de Universele Redacteur voor de inhoud van WYSIWYG authoring krijgen.

## Vereisten {#prerequisites}

Voordat u met deze handleiding begint, dient u al op de hoogte te zijn van de basisbeginselen van en toegang te hebben tot Edge Delivery Services, zoals:

* U hebt de [ zelfstudie van de Dienst van Edge Delivery ](/help/edge/developer/tutorial.md) voltooid.
* U hebt toegang tot een [ zandbak van AEM Cloud Service ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).
* U hebt [ de Universele Redacteur op het zelfde zandbakmilieu ](/help/implementing/universal-editor/getting-started.md) toegelaten.

## Basisconcepten bij het ontwikkelen voor Edge Delivery Services {#core-concepts}

Edge Delivery Services zijn gebaseerd op het concept van blokken. AEM wordt geleverd met een uitgebreide bibliotheek met vooraf gedefinieerde blokken, die kan worden uitgebreid om aan uw projectbehoeften te voldoen. De code voor de projecten van Edge Delivery Services wordt beheerd in GitHub.

### Blokken {#blocks}

Blokken zijn het meest fundamentele onderdeel van een pagina die door Edge Delivery Services wordt geleverd. Een blok omvat het stileren en de code die een logische component van een inhoudspagina drijft.

AEM biedt standaardblokken als onderdeel van het product binnen het bouwsteenbouwproject. Tot deze blokken behoren kop, tekst, afbeeldingen, koppelingen, lijsten, enzovoort.

>[!TIP]
>
>Gelieve te zien de [ sectie van de Bouwstijl ](/help/edge/developer/block-collection.md) van de documentatie van Edge Delivery Services voor meer details op blokken en hoe te zich voor de diensten van Edge Delivery ontwikkelen.

### Edge Delivery Services en GitHub {#github-edge}

Edge Delivery hefboomwerkingen GitHub zodat kunt u code van uw bewaarplaats beheren en opstellen GitHub.

Uw auteurs kunnen inhoud maken met gebruik van op documenten gebaseerde ontwerpen of met gebruik van inhoud in AEM met de Universal Editor. Ontwikkelaars kunnen de functionaliteit van uw site aanpassen door CSS en JavaScript in GitHub te gebruiken, ongeacht hoe de auteurs hun inhoud maken.

Er worden automatisch websites gemaakt voor elk van uw vertakkingen, van de voorvertoning van de inhoud tot de productie. Elk middel dat u in uw bewaarplaats GitHub zet is beschikbaar op uw website zonder een bouwstijlproces.

>[!TIP]
>
>Gelieve te zien de [ sectie van de Bouwstijl ](/help/edge/developer/block-collection.md) van de documentatie van Edge Delivery Services voor meer details op blokken en hoe te zich voor de diensten van Edge Delivery ontwikkelen.

## Aan de slag met WYSIWYG Authoring en Edge Delivery Services {#getting-started}

Zodra u [ aan de eerste vereisten ](#prerequisites) hebt voldaan en [ de keus gemaakt om de Universele Redacteur ](#editor-choice) te gebruiken, kunt u op uw eigen project beginnen.

### Uw GitHub-project maken {#create-github-project}

Eerst zult u een nieuw project op GitHub moeten tot stand brengen, dat op het malplaatje van de Adobe wordt gebaseerd.

1. Navigeer aan [`https://github.com/adobe-rnd/aem-boilerplate-xwalk` ](https://github.com/adobe-rnd/aem-boilerplate-xwalk) en klik op **Gebruik dit malplaatje** en selecteer **creeer een nieuwe bewaarplaats**.

   * U zult binnen aan GitHub moeten worden ondertekend om deze optie te zien.

   ![ project van de bewaarplaats van het Exemplaar ](assets/edge-dev-getting-started/use-template-project.png)

1. Standaard wordt de opslagplaats aan u toegewezen. Verander dit zonodig evenals verstrek een een bewaarplaatsnaam en een beschrijving en klik **creeer bewaarplaats**.

   ![ Creërend de bewaarplaats ](assets/edge-dev-getting-started/create-repo.png)

1. In een nieuw lusje in zelfde browser, navigeer aan [`https://github.com/apps/aem-code-sync` ](https://github.com/apps/aem-code-sync) en klik **vormen**.

   ![ de Synchronisatie van de Code ](assets/edge-dev-getting-started/configure-code-sync.png)

1. Klik **vormen** voor org waar u uw nieuwe bewaarplaats in de vorige stap creeerde.

   ![ het Kiezen van org voor codesynchronisatie ](assets/edge-dev-getting-started/code-sync-org.png)

1. Op de AEM pagina van GitHub van de Synchronisatie van de Code onder **Toegang van de Bewaarplaats**, selecteer **slechts bewaarplaatsen**, selecteer de bewaarplaats die u in de vorige stap creeerde, en klik dan **sparen**.

   ![ verlenen AEM de toegang van de Synchronisatie van de Code ](assets/edge-dev-getting-started/grant-code-sync-acces.png)

1. Nadat AEM Codesynchronisatie is geïnstalleerd, ontvangt u een bevestigingsscherm. Ga terug naar het browsertabblad van de nieuwe opslagplaats.

   ![ de installatiebevestiging van de Synchronisatie van de Code ](assets/edge-dev-getting-started/confirmation.png)

1. Klik het `fstab.yaml` dossier om het te openen en dan **dit dossier** pictogram uitgeven om het uit te geven.

   ![ fstab.yaml ](assets/edge-dev-getting-started/fstab.png)

1. Bewerk het `fstab.yaml` -bestand om het koppelingspunt van uw project bij te werken. Vervang het gebrek Google Docs URL met URL van uw het auteursrecht van AEM as a Cloud Service en klik dan **veranderingen vastleggen...**.

   * `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`
   * Als u het koppelingspunt wijzigt, weet u aan Edge Delivery Services waar ze de inhoud van de site moeten vinden.

   ![ Bijwerkend fstab ](assets/edge-dev-getting-started/fstab-update.png)

1. Voeg toe begaat bericht zoals gewenst en klik dan **veranderingen** begaan, die hen direct aan de `main` tak begaan.

   ![ het Aanwijzen veranderingen ](assets/edge-dev-getting-started/commit-fstab-changes.png)

1. Terugkeer naar de wortel van uw bewaarplaats en klik op `paths.json` en dan **geef dit dossier** pictogram uit.

   ![ paths.json ](assets/edge-dev-getting-started/paths.png)

1. Voor de standaardtoewijzing wordt de naam van de gegevensopslagruimte gebruikt. Werk de standaardafbeelding zoals vereist voor uw project met `/content/<site-name>/:/` bij en klik **verbindt veranderingen...**.

   * Geef uw eigen `<site-name>` op. U hebt het in een latere stap nodig.
   * De toewijzingen vertellen Edge Delivery Services hoe ze de inhoud in uw AEM opslagplaats moeten toewijzen aan de URL van de site.

   ![ Bijwerkend paths.json ](assets/edge-dev-getting-started/paths-update.png)

1. Voeg toe begaat bericht zoals gewenst en klik dan **veranderingen** begaan, die hen direct aan de `main` tak begaan.

   ![ het Aanwijzen veranderingen ](assets/edge-dev-getting-started/commit-paths-changes.png)

>[!TIP]
>
>Voor meer informatie over wegafbeeldingen, zie het document [ Toewijzing van de Weg voor Edge Delivery Services ](/help/edge/wysiwyg-authoring/path-mapping.md).

### Een nieuwe AEM-site maken en bewerken {#create-aem-site}

Nu u een project GitHub hebt, moet u een nieuwe AEM tot stand brengen plaats die het project kan gebruiken.

>[!NOTE]
>
>Als u uw site wilt bewerken met de Universal Editor, moet u een op chroom gebaseerde browser gebruiken.

1. Download het recentste WYSIWYG auteursrecht met het malplaatje van de Edge Delivery Services plaats van GitHub in [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases` ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases).

1. Teken binnen aan uw het auteursinstantie van AEM as a Cloud Service en navigeer aan de console van Plaatsen en klik **creeer** > **Plaats van malplaatje**.

   ![ creeer een nieuwe plaats van de console ](assets/edge-dev-getting-started/create-site-console.png)

1. Op **selecteer een plaatsmalplaatje** van creeer plaatstovenaar, klik de **Invoer** knoop om een nieuw malplaatje in te voeren.

   ![ het Invoeren malplaatjes ](assets/edge-dev-getting-started/site-templates.png)

1. Upload het WYSIWYG auteursrecht met het malplaatje van de Edge Delivery Services plaats dat u van GitHub downloadde.

   * De sjabloon mag slechts eenmaal worden geüpload. Na het uploaden kan het opnieuw worden gebruikt om extra sites te maken.

1. Zodra het malplaatje wordt ingevoerd, verschijnt het in de tovenaar. Klik om het te selecteren en dan **daarna** te klikken.

   ![ Uitgezochte malplaatje ](assets/edge-dev-getting-started/select-template.png)

1. Verstrek de volgende gebieden en de kraan of klik **creëren**.

   * **titel van de Plaats** - voeg een beschrijvende titel voor de plaats toe.
   * **titel van de Plaats** - gebruik `<site-name>` dat u in de [ vorige stap ](#create-github-project) bepaalde.
   * **GitHub URL** - gebruik URL van het project GitHub u in de vorige stap creeerde.

   ![ de details van de Plaats ](assets/edge-dev-getting-started/create-site-details.png)

1. AEM bevestigt het maken van de site met een dialoogvenster. Klik **O.K.** om te sluiten.

   ![ bevestiging van de creatie van de Plaats ](assets/edge-dev-getting-started/site-creation-confirmation.png)

1. Op de plaatsenconsole, navigeer aan `index.html` van de pas gecreëerde plaats en klik **uitgeven** in de toolbar.

   ![ Uitgevend de nieuwe plaats ](assets/edge-dev-getting-started/new-site.png)

1. De Universal Editor wordt op een nieuw tabblad geopend. U kunt moeten tikken of **binnen Teken met Adobe** klikken om uw pagina voor authentiek te verklaren uit te geven.

   ![ Universele Redacteur ](assets/edge-dev-getting-started/universal-editor.png)

U kunt uw site nu bewerken met de Universal Editor. Zie de [ Universele documentatie van de Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) voor meer informatie.

### Uw nieuwe site publiceren {#publishing}

Als u klaar bent met het bewerken van uw nieuwe site met de Universal Editor, kunt u uw inhoud publiceren.

1. Voor de plaatsenconsole, selecteer alle pagina&#39;s u voor uw nieuwe plaats creeerde en tikt of **klikt Snel publiceert** in de toolbar.

   ![ Selecterend pagina&#39;s om te publiceren ](assets/edge-dev-getting-started/publishing.png)

1. Tik of klik **Publish** in de bevestigingsdialoog om het proces te beginnen.

   ![ de dialoog van Publish ](assets/edge-dev-getting-started/publish-confirmation.png)

1. Open een nieuw tabblad in dezelfde browser en navigeer naar de URL van de nieuwe site.

   * `https://main--<repository-name>--<owner>.aem.page`

1. Bekijk de gepubliceerde inhoud.

   ![ Gepubliceerde inhoud ](assets/edge-dev-getting-started/published-site.png)

## Volgende stappen {#next-steps}

Nu u een werkend WYSIWYG creatie met het project van Edge Delivery Services hebt, kunt u beginnen creërend en uw eigen blokken.

Gelieve te zien de gids [ Creërend Blokken Instrumented voor gebruik met de Universele Redacteur ](/help/edge/wysiwyg-authoring/create-block.md) voor meer informatie.

>[!TIP]
>
>Voor een analyse van begin tot eind van het creëren van een nieuw project van Edge Delivery Services dat voor WYSIWYG creatie met AEM as a Cloud Service als inhoudsbron wordt toegelaten, gelieve te bekijken [ dit AEM webinar GEMs ](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery).
