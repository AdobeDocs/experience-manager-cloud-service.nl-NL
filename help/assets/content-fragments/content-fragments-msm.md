---
title: Inhoudsfragmenten opnieuw gebruiken met MSM en Actieve kopieën
description: Leer over het gebruiken van de Levende functionaliteit van het Exemplaar van MSM om de zelfde, of gelijkaardige, inhoud van het Fragment van de Inhoud op veelvoudige plaatsen te gebruiken, terwijl het synchroniseren met de broninhoud.
exl-id: f050b2d1-856c-4cdb-ac74-bc78016f144a
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Inhoudsfragmenten opnieuw gebruiken met MSM {#reuse-content-fragments-using-msm}

Met MSM (Multi Site Manager) en de functie Live Copy kunt u dezelfde inhoud op meerdere locaties gebruiken terwijl u synchroniseert met de broninhoud.

* Met Live MSM-kopieën kunt u:
   * Inhoud eenmaal maken en vervolgens
   * U kunt deze inhoud opnieuw gebruiken in andere gebieden van dezelfde of andere sites of toepassingen.
* MSM onderhoudt dan de levende verhoudingen tussen uw broninhoud en zijn Levende Kopieën zodat:
   * Wanneer u de broninhoud wijzigt, worden de bron en Live kopieën gesynchroniseerd.
   * U kunt alleen de inhoud van de actieve kopieën aanpassen door de live relatie voor afzonderlijke subpagina&#39;s en/of componenten te verbreken.

Voor een gedetailleerd overzicht van de concepten MSM zie [&#x200B; Hergebruikende Inhoud: De Manager van de MultiPlaats en Levende Kopie van het Exemplaar &#x200B;](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>[&#x200B; Multisite Manager (MSM) &#x200B;](/help/sites-cloud/administering/msm/overview.md) functionaliteit in Adobe Experience Manager laat gebruikers toe om inhoud opnieuw te gebruiken die eens en dan over veelvoudige Web-plaatsen wordt ontworpen opnieuw gebruikt.

Met MSM voor inhoudsfragmenten kunt u:

* Maak eenmaal inhoudsfragmenten en (gekoppelde) kopieën van deze fragmenten die u opnieuw kunt gebruiken in andere gebieden van de site of toepassing.
* Houd meerdere kopieën gesynchroniseerd door de bronkopie eenmaal bij te werken en de wijzigingen vervolgens door te voeren in de (actieve) kopieën.
* Breng lokale wijzigingen aan door de koppeling tussen bovenliggende en onderliggende fragmenten tijdelijk of permanent op te heffen. Dit kan volledig zijn of voor de variaties of velden van deze fragmenten.

Met MSM voor inhoudsfragmenten kunt u in combinatie met functionaliteit in de Inhoudsfragmenteditor overerving op veldniveau onderbreken en herstellen.

>[!CAUTION]
>
>MSM voor de Fragmenten van de Inhoud is slechts beschikbaar wanneer het gebruiken van de Fragmenten van de Inhoud via de **Assets** console.
>
>De functionaliteit MSM is *niet* beschikbaar wanneer het gebruiken van de **console van de Fragmenten van de Inhoud**.

## Procedure {#how-to}

Zie de volgende documentatie voor details over het gebruik van MSM voor de Fragments van de Inhoud (ook toepasselijk op Assets):

* Hoe te om [&#x200B; MSM voor de Fragmenten van de Inhoud (en Assets) te gebruiken &#x200B;](/help/assets/reuse-assets-using-msm.md)

* [Een actieve kopie maken](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >Als u MSM wilt gebruiken om exemplaren van Inhoudsfragmenten) tot stand te brengen, dan zouden om het even welke **Unieke** beperkingen uit om het even welke Types moeten worden verwijderd van Gegevens die in de respectieve [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-models.md) worden gebruikt.

* [Eigenschappen en status van bron en Live kopie weergeven](/help/assets/reuse-assets-using-msm.md#properties)
* [Wijzigingen van bron naar Live kopie doorgeven](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* Overerving annuleren en opnieuw instellen voor:
   * gebieden en variaties in de [&#x200B; redacteur van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [metagegevens van verwante elementen](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [De relatie onderbreken en hervatten](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [De live relatie verwijderen](/help/assets/reuse-assets-using-msm.md#detach)
* [Vergelijk MSM voor de Fragmenten van de Inhoud (en Assets) met MSM voor Plaatsen](/help/assets/reuse-assets-using-msm.md#comparison)

## Beperkingen {#limitations}

* triggers voor on-modify en de bijbehorende rollout-configuratie bestaan niet voor Content Fragments.
