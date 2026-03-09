---
title: Aan de slag met de Experience Modernization Agent for AEM Authoring Projecten
description: Leer de specifieke opstellingsstappen die voor de auteursprojecten van AEM worden vereist wanneer het worden begonnen met de Agent van de Modernisering van de Ervaring gebruikend de Console van de Modernisering van de Ervaring.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: a1b2c3d4-e5f6-4789-a012-3456789abcde
source-git-commit: df23c3a4c497943135f8719425225526ae14aa92
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Aan de slag met de Experience Modernization Agent for AEM Authoring Projecten {#getting-started-aem-authoring}

Voor AEM-ontwerpprojecten die gebruikmaken van de Universal Editor, verschilt de voorbereiding van de Experience Modernization Agent van de standaard Edge Delivery-flow. In dit document worden deze instellingsverschillen behandeld. Zodra de stappen hieronder volledig zijn, volg het belangrijkste [ Begonnen Worden met de gids van de Agent van de Modernisering van de Ervaring ](getting-started.md).

## Uw Edge Delivery Services-projectrepo maken {#create-repo}

1. Gebruik de [`aem-block-collection-xwalk` ](https://github.com/adobe-rnd/aem-block-collection-xwalk) bewaarplaats als uw malplaatje (niet het standaardEdge Delivery Services boilerplate).
1. Volg het [ Universele leerprogramma van de Redacteur ](https://www.aem.live/developer/ue-tutorial) aan opstelling uw repo.
   * Stop wanneer u wordt gevraagd een site te maken in AEM.
1. Verwijder `paths.json` en wijs deze wijziging toe aan `main` .
1. Voeg [ toe de Schakelaar van de Code van AEM ](https://github.com/apps/aem-code-connector/installations/select_target) app aan uw reactie.
   * Hierdoor kan de console uw code inspecteren.

## Een nieuwe site maken in AEM {#create-site}

1. In de console van AEM Sites, creeert de uitgezochte **** > **Plaats van malplaatje**.
1. Selecteer de **Plaats van AEM met het Malplaatje van Edge Delivery Services**.
   * Zie je het niet in de lijst? [ installeer het malplaatje.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)
1. Houd de **naam** van de plaats (niet de titel) zoals verstrekt.
   * De sitenaam wordt gebruikt als de unieke id.
   * De titel kan worden gewijzigd voor weergave.
1. Klik **creëren**.
   * U wordt omgeleid naar de pagina van Plaatsen.
   * Vernieuw de pagina als de nieuwe site niet meteen wordt weergegeven.
1. Als u het nog niet hebt gedaan wanneer [ vestiging uw repo, ](#create-repo) update `fstab.yaml` zodat richt het aan uw gastheer van AEM, git eigenaar, en git revisie en begaat die veranderingen aan `main`.
   * Zie [ inhoudsbron ](/help/implementing/cloud-manager/edge-delivery/configure-content-source.md) voor instructies vormen.

## Ga verder met de standaard Aan de slag-stappen {#continue}

Zodra de bovenstaande stappen zijn voltooid, kunt u doorgaan met de standaardgids Aan de slag om uw inhoud te migreren.

![ de invoer van de Inhoud ](assets/content-import.png)

Voer de volgende stappen uit in de standaardhandleiding.

1. [Een Edge Delivery GitHub-opslagplaats voorbereiden](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#prepare-repo)
1. [Open de Experience Moderation Console](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#open-console)
1. [Sluit uw GitHub-opslagplaats aan](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#connect-repo)
1. [Vragen starten](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#start-prompting)

![ ingevoerde Inhoud ](assets/content-imported-aem-authoring.png)

Als u deze stappen hebt uitgevoerd om de inhoud te migreren, gaat u verder met de volgende stappen.

## Inhoud valideren {#validate-content}

Valideer de inhoud van de geselecteerde pagina in het voorvertoningsvenster. Om het even welke fouten zullen worden getoond door de **knoop van Fouten** te klikken.
Ga uw praatjegesprek met de agent voort om de fouten te bevestigen. Gebruik **toevoegen aan praatje{** eigenschap om moeilijke situaties aan specifieke elementen van de pagina, parserdossiers, of transformatordossiers te richten.

![ Contextual praatje ](assets/contextual-chat.png)

## Inhoud uploaden {#upload-content}

Ga als volgt te werk om uw inhoud te uploaden naar AEM:

1. Zorg ervoor u in de **mening van de Inhoud** bent en klik **uploadt inhoud** knoop op top-right.
1. In **creeer inhoudspakket** dialoog, kies de pagina&#39;s in het pakket te omvatten.
   * Naar keuze ga a **Naam van het Pakket** in (gebreken aan de plaatsnaam als verlaten leeg).
   * Het gebruik **selecteert allen**, **Duidelijke selectie**, **breidt allen** uit, of **vouwt allen** samen om de lijst te beheren.
1. Klik **creeer pakket**.

   ![ creeer inhoudspakket - kies pagina&#39;s en creeer ](assets/content-package.png)

1. Nadat het pakket wordt gecreeerd, toont de **Upload inhoudspakket** dialoog dat het pakket klaar is.
   1. U kunt **pakket van de Download** {om het plaatselijk te bewaren, of te werk te gaan om te uploaden.
   1. Onder **uploadt aan AEM**, bevestig de **plaats van AEM** en **gastheer van AEM** (vooraf ingevuld van uw projectmontages).
      * Verlaat naar keuze **uploadbeelden** gecontroleerd om beelden te omvatten.
   1. Klik **uploaden aan AEM**.

   ![ Pakket klaar om aan AEM te uploaden of te downloaden ](assets/upload-package-start.png)

1. In het dialoogvenster wordt de voortgang van het uploaden weergegeven terwijl pagina&#39;s en elementen naar AEM worden verzonden. Wanneer het uploaden is voltooid, worden een succesbericht en het uploadlogboek weergegeven. Klik **dicht** om de dialoog te sluiten.

   ![ upload vooruitgang en voltooiing in AEM ](assets/upload-package-complete.png)

De geïmporteerde inhoud bevindt zich nu in AEM. Ga met [ de Veranderingen van de Code van de Duw ](getting-started.md#push-code-changes) in het belangrijkste begonnen gids verder.

## Aanvullende bronnen {#additional-resources}

* [ Begonnen het Worden met de Agent van de Modernisering van de Ervaring ](getting-started.md) - Volledig werkschema met inbegrip van console, het ertoe aanzetten, uploaden, en voorproef
* [ Console van de Modernisering van de Ervaring ](console.md) - de verwijzing van de Console
* [ Universeel leerprogramma van de Redacteur ](https://www.aem.live/developer/ue-tutorial) - Opstelling een het auteurswerk van AEM en Universeel project van de Redacteur
* [`aem-block-collection-xwalk` ](https://github.com/adobe-rnd/aem-block-collection-xwalk) - Sjabloonopslagplaats voor AEM-ontwerpprojecten en Universal Editor-projecten
