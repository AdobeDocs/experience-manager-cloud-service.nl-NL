---
title: Assets-mappen maken - headless Setup
description: Met Modellen AEM inhoudsfragmenten kunt u de structuur van inhoudsfragmenten definiëren als de basis voor inhoud zonder kop.
exl-id: 9a156a17-8403-40fc-9bd0-dd82fb7b2235
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Assets-mappen maken - headless Setup {#creating-an-assets-folder}

Met Modellen AEM inhoudsfragmenten kunt u de structuur van inhoudsfragmenten definiëren als de basis voor inhoud zonder kop. Inhoudsfragmenten worden vervolgens in mappen met elementen opgeslagen.

## Wat is een Assets-map? {#what-is-an-assets-folder}

[&#x200B; nu u de Modellen van het Fragment van de Inhoud &#x200B;](create-content-model.md) hebt gecreeerd die de structuur bepalen die u voor uw toekomstige Fragmenten van de Inhoud wilt, bent u waarschijnlijk opgewekt om sommige fragmenten tot stand te brengen.

U moet echter eerst een map met middelen maken waarin u deze wilt opslaan.

De omslagen van Assets worden gebruikt om [&#x200B; traditionele inhoudsactiva &#x200B;](/help/assets/manage-digital-assets.md) zoals beelden en video&#39;s, samen met de Fragmenten van de Inhoud te organiseren.

## Een Assets-map maken {#how-to-create-an-assets-folder}

Een beheerder hoeft alleen maar af en toe mappen te maken om de inhoud te ordenen terwijl deze wordt gemaakt. Voor deze gids Aan de slag hoeven we slechts één map te maken.

1. Logboek in AEM as a Cloud Service en van het belangrijkste menu selecteert **Navigatie > Assets > Dossiers**.
1. Selecteer **creeer > Omslag**.
1. Verstrek a **Titel** en a **Naam** voor uw omslag.
   * De **Titel** zou beschrijvend moeten zijn.
   * De **Naam** wordt de knoopnaam in de bewaarplaats.
      * Het wordt automatisch geproduceerd gebaseerd op de titel en aangepast volgens [&#x200B; AEM noemende overeenkomsten &#x200B;](/help/implementing/developing/introduction/naming-conventions.md).
      * Deze kan zo nodig worden aangepast.

   ![&#x200B; creeer omslag &#x200B;](../assets/assets-folder-create.png)
1. Selecteer de map die u hebt gemaakt door op het vinkje te tikken en erop te klikken. Dan selecteer **Eigenschappen** van de toolbar (of gebruik `p` [&#x200B; toetsenbordkortere weg &#x200B;](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md)).
1. In het **venster van Eigenschappen**, selecteer de **Cloud Servicen** tabel.
1. Voor de **Configuratie van de Wolk** selecteer de [&#x200B; configuratie u eerder &#x200B;](create-configuration.md) creeerde.
   ![&#x200B; vorm activa omslag &#x200B;](../assets/assets-folder-configure.png)
1. Selecteer **sparen &amp; Sluiten**.
1. Selecteer **O.K.** in het bevestigingsvenster.

   ![&#x200B; Bevestigingsvenster &#x200B;](../assets/assets-folder-confirmation.png)

U kunt aanvullende submappen maken in de map die u hebt gemaakt. De subfolders zullen de **Configuratie van de Wolk** van de ouderomslag erven. Dit kan worden met voeten getreden echter als u modellen van een andere configuratie wilt gebruiken.

Als u een gelokaliseerde plaatsstructuur gebruikt, kunt u [&#x200B; tot een taalwortel &#x200B;](/help/assets/translate-assets.md) onder uw nieuwe omslag leiden.

## Volgende stappen {#next-steps}

Nu u een omslag voor uw Fragmenten van de Inhoud hebt gecreeerd, kunt u zich op het vierde deel van begonnen gids bewegen en [&#x200B; creeer inhoudsfragmenten &#x200B;](create-content-fragment.md).

>[!TIP]
>
>Voor volledige details over het beheren van de Fragmenten van de Inhoud, zie de [&#x200B; documentatie van de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md)
