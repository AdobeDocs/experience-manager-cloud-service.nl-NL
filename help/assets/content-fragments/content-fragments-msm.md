---
title: Inhoudsfragmenten opnieuw gebruiken met MSM en Actieve kopieën
description: Leer over het gebruiken van de Levende functionaliteit van het Exemplaar van MSM om de zelfde, of gelijkaardige, inhoud van het Fragment van de Inhoud op veelvoudige plaatsen te gebruiken, terwijl het synchroniseren met de broninhoud.
exl-id: f050b2d1-856c-4cdb-ac74-bc78016f144a
feature: Content Fragments
role: User
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
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

Voor een gedetailleerd overzicht van de concepten MSM zie [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>[MSM (Multi Site Manager)](/help/sites-cloud/administering/msm/overview.md) in Adobe Experience Manager kunnen gebruikers inhoud hergebruiken die eenmaal is ontworpen en vervolgens opnieuw wordt gebruikt op meerdere weblocaties.

Met MSM voor inhoudsfragmenten kunt u:

* Maak eenmaal inhoudsfragmenten en (gekoppelde) kopieën van deze fragmenten die u opnieuw kunt gebruiken in andere gebieden van de site of toepassing.
* Houd meerdere kopieën gesynchroniseerd door de bronkopie eenmaal bij te werken en de wijzigingen vervolgens door te voeren in de (actieve) kopieën.
* Breng lokale wijzigingen aan door de koppeling tussen bovenliggende en onderliggende fragmenten tijdelijk of permanent op te heffen. Dit kan volledig zijn of voor de variaties of velden van deze fragmenten.

Met MSM voor inhoudsfragmenten kunt u in combinatie met functionaliteit in de Inhoudsfragmenteditor overerving op veldniveau onderbreken en herstellen.

>[!CAUTION]
>
>MSM voor inhoudsfragmenten is alleen beschikbaar wanneer u Content Fragments gebruikt via de **Activa** console.
>
>MSM-functionaliteit is *niet* beschikbaar bij gebruik van de **Inhoudsfragmenten** console.

## Procedure {#how-to}

Zie de volgende documentatie voor details over het gebruik van MSM voor de Fragments van de Inhoud (ook toepasselijk op Activa):

* Hoe wordt het gebruikt [MSM voor inhoudsfragmenten (en elementen)](/help/assets/reuse-assets-using-msm.md)

* [Een actieve kopie maken](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >Als u MSM wilt gebruiken om exemplaren van Inhoudsfragmenten) tot stand te brengen, dan om het even welk **Uniek** de beperkingen moeten worden verwijderd uit alle gegevenstypen die in de respectieve [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md).

* [Eigenschappen en status van bron en Live kopie weergeven](/help/assets/reuse-assets-using-msm.md#properties)
* [Wijzigingen van bron naar Live kopie doorgeven](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* Overerving annuleren en opnieuw instellen voor:
   * velden en variaties in de [Inhoudsfragmenteditor](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [metagegevens van verwante elementen](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [De relatie onderbreken en hervatten](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [De live relatie verwijderen](/help/assets/reuse-assets-using-msm.md#detach)
* [Vergelijk MSM voor de Fragmenten van de Inhoud (en Middelen) met MSM voor Plaatsen](/help/assets/reuse-assets-using-msm.md#comparison)

## Beperkingen {#limitations}

* triggers voor on-modify en de bijbehorende rollout-configuratie bestaan niet voor Content Fragments.
