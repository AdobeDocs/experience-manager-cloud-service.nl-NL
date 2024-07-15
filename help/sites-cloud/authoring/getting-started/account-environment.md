---
title: Uw accountomgeving configureren
description: Adobe Experience Manager (AEM) biedt u de mogelijkheid om uw account en bepaalde aspecten van de auteursomgeving te configureren.
exl-id: 1b948f0b-85b9-478a-8b7e-61495c1d57b6
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 4%

---

# Uw accountomgeving configureren {#configuring-your-account-environment}

Adobe Experience Manager (AEM) biedt u de mogelijkheid om uw account en bepaalde aspecten van de auteursomgeving te configureren.

Met de optie [Gebruiker](#user-settings) in de [koptekst](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header) en het bijbehorende dialoogvenster [Mijn voorkeuren](#my-preferences) kunt u uw gebruikersopties wijzigen, zoals

Begin door tot de [ optie van de Gebruiker ](#user-settings) in de kopbal toegang te hebben.

## Gebruikersinstellingen {#user-settings}

Het **de montagedialoog van de Gebruiker** geeft u toegang tot:

* Imiteren als
   * Met Impersonate als functionaliteit, kan een gebruiker namens een andere gebruiker werken. <!--With the [Impersonate as](/help/sites-administering/security.md#impersonating-another-user) functionality, a user can work on behalf of another user.-->
* Profiel
   * Het biedt een handige koppeling naar uw gebruikersinstellingen <!--Offers a convenient link to your [user settings](/help/sites-administering/security.md))-->
* [Mijn voorkeuren](#my-preferences)
   * Verschillende voorkeursinstellingen opgeven die uniek zijn voor uw gebruiker

![ montages van de Gebruiker ](/help/sites-cloud/authoring/assets/user-settings.png)

### Mijn voorkeuren {#my-preferences}

Het **Mijn de dialoogvakje van de Voorkeur** wordt betreden als [ gebruiker ](#user-settings) optie in de kopbal.

Elke gebruiker kan zijn eigen voorkeurseigenschappen instellen.

![ Mijn Voorkeur ](/help/sites-cloud/authoring/assets/user-preferences.png)

* **Taal**

  Dit bepaalt de taal voor UI van het auteursmilieu te gebruiken. Selecteer de gewenste taal in de beschikbare lijst.

* **Beheer van het Venster**

  Hiermee definieert u het gedrag voor het openen van vensters. Selecteer een van de volgende opties:

   * **Veelvoudige Vensters** (Gebrek)

      * Pagina&#39;s worden geopend in een nieuw venster.

   * **Enig Venster**

      * Pagina&#39;s worden geopend in het huidige venster.

* **toon Desktopacties voor Assets**

  Voor deze optie moet de AEM-bureaubladtoepassing worden gebruikt.

* **Kleur van de Annotatie**

  Hiermee definieert u de standaardkleur die wordt gebruikt bij het maken van annotaties.

   * Klik op het kleurblok, zodat u de staalkiezer kunt openen en een kleur kunt selecteren.
   * U kunt ook de hexadecimale code voor de gewenste kleur in het veld invoeren.

* **Relatieve Presentatie van de Datum**

  Om de leesbaarheid te verbeteren, worden AEM datums binnen de laatste zeven dagen weergegeven als relatieve datums (bijvoorbeeld drie dagen geleden) en als oudere datums als exacte datums (bijvoorbeeld 20 maart 2017).

  Met deze optie bepaalt u hoe datums in het systeem worden weergegeven. De volgende opties zijn beschikbaar:

   * **toont altijd nauwkeurige datum**: De nauwkeurige datum wordt altijd getoond (nooit een relatieve datum).
   * **1 Dag**: De relatieve datum wordt getoond voor data binnen één dag, anders wordt een nauwkeurige datum getoond.
   * **7 Dagen (gebrek)**: De relatieve datum wordt getoond voor data binnen zeven dagen, anders wordt een nauwkeurige datum getoond.
   * **1 Maand**: De relatieve datum wordt getoond voor data binnen één maand, anders wordt een nauwkeurige datum getoond.
   * **1 Jaar**: De relatieve datum wordt getoond voor data binnen één jaar, anders wordt een nauwkeurige datum getoond.
   * **toont altijd relatieve datum**: De nauwkeurige data worden nooit getoond en slechts relatieve data worden getoond.

* **laat Kortere weg** toe

  AEM ondersteunt verschillende sneltoetsen die het ontwerpen efficiënter maken.

   * [Sneltoetsen voor het bewerken van pagina&#39;s](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md)
   * [Sneltoetsen voor consoles](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)

  Met deze optie schakelt u sneltoetsen in. Deze worden standaard ingeschakeld, maar kunnen worden uitgeschakeld, bijvoorbeeld als een gebruiker bepaalde toegankelijkheidsvereisten heeft.

* **laat de Homepage van Assets** toe

  Deze optie is alleen beschikbaar als uw systeembeheerder de Assets Home Page-ervaring voor de hele organisatie heeft ingeschakeld.

* **Configuratie van de Beeld**

  Deze optie laat u de aangewezen configuratie van Adobe Stock specificeren en is slechts beschikbaar als uw systeembeheerder [ integratie van Adobe Stock ](/help/assets/aem-assets-adobe-stock.md) heeft toegelaten.
