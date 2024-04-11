---
title: Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services
description: Deze gids zal u aan de slag met een nieuwe plaats van Adobe Experience Manager gebruikend Edge Delivery Services en de Universele Redacteur voor inhoud creatie krijgen.
feature: Edge Delivery Services
exl-id: a71184a7-c954-442e-b276-99edc6d2acd8
source-git-commit: 11f721b4a617c99e30329d7196f42d7b48067f1b
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---


# Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services {#edge-dev-getting-started}

Deze gids zal u aan de slag met een nieuwe plaats van Adobe Experience Manager gebruikend Edge Delivery Services en de Universele Redacteur voor inhoud creatie krijgen.

## Vereisten {#prerequisites}

Voordat u met deze handleiding begint, dient u al op de hoogte te zijn van de basisbeginselen van en toegang te hebben tot Edge Delivery Services, zoals:

* U hebt de [Zelfstudie over Edge Delivery Service.](/help/edge/developer/tutorial.md)
* U hebt toegang tot [AEM Cloud Service-sandbox.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)
* U hebt [heeft de Universal Editor ingeschakeld in dezelfde sandboxomgeving.](/help/implementing/universal-editor/getting-started.md)

## Kies de rechtereditor {#editor-choice}

AEM biedt twee verschillende inhoudeditors en de keuze van wie u wilt gebruiken hangt af van uw situatie.

* **Universele editor** - Dit zou de standaardkeus voor nieuwe plaatsen moeten zijn.
* **Pagina-editor AEM** - Dit moet worden gekozen voor een bestaande migratie van AEM Sites naar Edge Delivery Services.

Deze gids concentreert zich op AEM projecten op Edge Delivery Services gebruikend de Universele Redacteur. Zie het document [Edge Delivery Services met AEM gebruiken](/help/edge/using.md) voor meer informatie over het kiezen van de juiste redacteur en de migratie van bestaande AEM plaatsen aan Edge Delivery Services.

## Basisconcepten bij het ontwikkelen voor Edge Delivery Services {#core-concepts}

Edge Delivery Services zijn gebaseerd op het concept van blokken. AEM wordt geleverd met een uitgebreide bibliotheek met vooraf gedefinieerde blokken, die kan worden uitgebreid om aan uw projectbehoeften te voldoen. De code voor de projecten van Edge Delivery Services wordt beheerd in GitHub.

### Blokken {#blocks}

Blokken zijn het meest fundamentele onderdeel van een pagina die door Edge Delivery Services wordt geleverd. Een blok omvat het stileren en de code die een logische component van een inhoudspagina drijft.

AEM biedt standaardblokken als onderdeel van het product binnen het bouwsteenbouwproject. Tot deze blokken behoren kop, tekst, afbeeldingen, koppelingen, lijsten, enzovoort.

>[!TIP]
>
>Zie de [Sectie Samenstellen](/help/edge/developer/block-collection.md) van de documentatie van Edge Delivery Services voor meer informatie over blokken en hoe te om voor de diensten van de Levering van de Rand te ontwikkelen.

### Edge Delivery Services en GitHub {#github-edge}

De hefboomwerkingen van de Levering van de rand GitHub zodat kunt u code direct van uw bewaarplaats beheren en opstellen GitHub.

Uw auteurs kunnen inhoud maken met gebruik van op documenten gebaseerde ontwerpen of met gebruik van inhoud in AEM met de Universal Editor. Ontwikkelaars kunnen de functionaliteit van uw site aanpassen met CSS en JavaScript in GitHub, ongeacht hoe de auteurs hun inhoud maken.

Er worden automatisch websites gemaakt voor elk van uw vertakkingen, van de voorvertoning van de inhoud tot de productie. Elk middel dat u in uw bewaarplaats GitHub zet is beschikbaar op uw website zonder een bouwstijlproces.

>[!TIP]
>
>Zie de [Sectie Samenstellen](/help/edge/developer/block-collection.md) van de documentatie van Edge Delivery Services voor meer informatie over blokken en hoe te om voor de diensten van de Levering van de Rand te ontwikkelen.

## Aan de slag met AEM Authoring en Edge Delivery Services {#getting-started}

Zodra u hebt voldaan [de voorwaarden](#prerequisites) en [de keuze om de Universal Editor te gebruiken;](#editor-choice) u kunt aan de slag gaan met uw eigen project.

### Uw GitHub-project maken {#create-github-project}

Eerst zult u een nieuw project op GitHub moeten tot stand brengen, dat op het malplaatje van de Adobe wordt gebaseerd.

1. Navigeren naar [`https://github.com/adobe-rnd/aem-boilerplate-xwalk`](https://github.com/adobe-rnd/aem-boilerplate-xwalk) en klik op **Deze sjabloon gebruiken** en selecteert u **Een nieuwe opslagplaats maken**.

   * U zult binnen aan GitHub moeten worden ondertekend om deze optie te zien.

   ![Opslagproject kopiëren](assets/edge-dev-getting-started/use-template-project.png)

1. Standaard wordt de opslagplaats aan u toegewezen. Wijzig dit zo nodig en geef een naam en beschrijving voor de gegevensopslagplaats op en klik op **Opslagplaats maken**.

   ![De opslagplaats maken](assets/edge-dev-getting-started/create-repo.png)

1. Ga in een nieuw tabblad in dezelfde browser naar [`https://github.com/apps/aem-code-sync`](https://github.com/apps/aem-code-sync) en klik op **Configureren**.

   ![Codesync](assets/edge-dev-getting-started/configure-code-sync.png)

1. Klikken **Configureren** voor de org waar u in de vorige stap uw nieuwe opslagplaats creeerde.

   ![De org kiezen voor codesynchronisatie](assets/edge-dev-getting-started/code-sync-org.png)

1. Op de AEM pagina GitHub van de Synchronisatie van de Code onder **Toegang tot opslagplaats**, selecteert u **Alleen repositories selecteren** selecteert u de opslagplaats die u in de vorige stap hebt gemaakt en klikt u vervolgens op **Opslaan**.

   ![Toegang tot AEM codesynchronisatie verlenen](assets/edge-dev-getting-started/grant-code-sync-acces.png)

1. Nadat AEM Codesynchronisatie is geïnstalleerd, ontvangt u een bevestigingsscherm. Ga terug naar het browsertabblad van de nieuwe opslagplaats.

   ![Bevestiging van installatie van codesynchronisatie](assets/edge-dev-getting-started/confirmation.png)

1. Klik op de knop `fstab.yaml` te openen en vervolgens **Dit bestand bewerken** pictogram om het te bewerken.

   ![fstab.yaml](assets/edge-dev-getting-started/fstab.png)

1. Bewerk de `fstab.yaml` bestand om het koppelingspunt van uw project bij te werken. Vervang de standaard Google Docs URL met URL van uw AEM as a Cloud Service ontwerpinstantie en klik dan **Wijzigingen vastleggen...**.

   * `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`
   * Als u het koppelingspunt wijzigt, weet u aan Edge Delivery Services waar ze de inhoud van de site moeten vinden.

   ![Fstab bijwerken](assets/edge-dev-getting-started/fstab-update.png)

1. Voeg naar wens een commit message toe en klik vervolgens op **Wijzigingen vastleggen**, die rechtstreeks bij de `main` vertakking.

   ![Wijzigingen vastleggen](assets/edge-dev-getting-started/commit-fstab-changes.png)

1. Ga terug naar de hoofdmap van uw opslagplaats en klik op `paths.json` en vervolgens de **Dit bestand bewerken** pictogram.

   ![paths.json](assets/edge-dev-getting-started/paths.png)

1. Voor de standaardtoewijzing wordt de naam van de gegevensopslagruimte gebruikt. Werk de standaardafbeelding zoals vereist voor uw project bij met `/content/<site-name>/:/` en klik op **Wijzigingen vastleggen...**.

   * Geef uw eigen `<site-name>`. U hebt het in een latere stap nodig.
   * De toewijzingen vertellen Edge Delivery Services hoe ze de inhoud in uw AEM opslagplaats moeten toewijzen aan de URL van de site.

   ![Paden.json bijwerken](assets/edge-dev-getting-started/paths-update.png)

1. Voeg naar wens een commit message toe en klik vervolgens op **Wijzigingen vastleggen**, die rechtstreeks bij de `main` vertakking.

   ![Wijzigingen vastleggen](assets/edge-dev-getting-started/commit-paths-changes.png)

### Een nieuwe AEM-site maken en bewerken {#create-aem-site}

Nu u een project GitHub hebt, moet u een nieuwe AEM tot stand brengen plaats die het project kan gebruiken.

>[!NOTE]
>
>Als u uw site wilt bewerken met de Universal Editor, moet u een op chroom gebaseerde browser gebruiken.

1. Vraag het recentste AEM Authoring met de plaatssjabloon van Edge Delivery Services van de Techniek van de Adobe via uw [Slack-kanaal van project.](/help/edge/docs/slack.md)

1. Meld u aan bij uw AEM as a Cloud Service ontwerpinstantie en navigeer naar de Sites-console en tik of klik op **Maken** -> **Site van sjabloon**.

   ![Een nieuwe site maken vanaf de console](assets/edge-dev-getting-started/create-site-console.png)

1. Op de **Een sitesjabloon selecteren** klikt u op de knop **Importeren** om een nieuwe sjabloon te importeren.

   ![Sjablonen importeren](assets/edge-dev-getting-started/site-templates.png)

1. Upload de AEM Authoring met de sitesjabloon van Edge Delivery Services die u van de Adobe Engineering ontvangt.

1. Zodra het malplaatje wordt ingevoerd, verschijnt het in de tovenaar. Tik of klik om het te selecteren en tik of klik vervolgens op **Volgende**.

   ![Sjabloon selecteren](assets/edge-dev-getting-started/select-template.png)

1. Geef de volgende velden op en tik of klik op **Maken**.

   * **Titel van site** - Voeg een beschrijvende titel toe aan de site.
   * **Titel van site** - Gebruik de `<site-name>` die u in [vorige stap.](#create-github-project)
   * **GitHub-URL** - Gebruik URL van het project GitHub u in de vorige stap creeerde.

   ![Sitegegevens](assets/edge-dev-getting-started/create-site-details.png)

1. AEM bevestigt het maken van de site met een dialoogvenster. Tik of klik op **OK** om te worden ontslagen.

   ![Bevestiging van site](assets/edge-dev-getting-started/site-creation-confirmation.png)

1. Navigeer op de siteconsole naar de `index.html` van de nieuwe site en tik of klik op **Bewerken** in de werkbalk.

   ![De nieuwe site bewerken](assets/edge-dev-getting-started/new-site.png)

1. De Universal Editor wordt op een nieuw tabblad geopend. Mogelijk moet u tikken of op **Aanmelden met Adobe** om te verifiëren om uw pagina te bewerken.

   ![Universele editor](assets/edge-dev-getting-started/universal-editor.png)

U kunt uw site nu bewerken met de Universal Editor. Zie de [Universal Editor-documentatie](/help/sites-cloud/authoring/universal-editor/authoring.md) voor meer informatie .

### Uw nieuwe site publiceren {#publishing}

Als u klaar bent met het bewerken van uw nieuwe site met de Universal Editor, kunt u uw inhoud publiceren.

1. Selecteer in de siteconsole alle pagina&#39;s die u voor uw nieuwe site hebt gemaakt en tik of klik op **Snel publiceren** in de werkbalk.

   ![Te publiceren pagina&#39;s selecteren](assets/edge-dev-getting-started/publishing.png)

1. Tik of klik op **Publiceren** in het bevestigingsdialoogvenster om het proces te starten.

   ![Het dialoogvenster Publiceren](assets/edge-dev-getting-started/publish-confirmation.png)

1. Open een nieuw tabblad in dezelfde browser en navigeer naar de URL van de nieuwe site.

   * `https://main--<site-name>--<owner>.hlx.page`

1. Bekijk de gepubliceerde inhoud.

   ![Gepubliceerde inhoud](assets/edge-dev-getting-started/published-site.png)

## Volgende stappen {#next-steps}

Nu u een werkend AEM creatie met het project van Edge Delivery Services hebt, kunt u beginnen creërend en uw eigen blokken.

Zie de handleiding [Blokken maken met een instrument voor gebruik met de universele editor](/help/edge/aem-authoring/create-block.md) voor meer informatie .

>[!TIP]
>
>Voor een analyse van begin tot eind van het creëren van een nieuw project van Edge Delivery Services dat voor AEM creatie met AEM as a Cloud Service als inhoudsbron wordt toegelaten, gelieve te bekijken [deze AEM GEM&#39;s webinar.](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery)

