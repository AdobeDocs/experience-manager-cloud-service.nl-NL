---
title: Modellen van contentfragmenten
description: Inhoudsfragmentmodellen worden gebruikt om inhoudsfragmenten met gestructureerde inhoud te maken.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 21%

---


# Modellen van contentfragmenten{#content-fragment-models}

Met Content Fragment Models wordt de structuur van de inhoud voor [inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)gedefinieerd.

## Enable Content Fragment Models {#enable-content-fragment-models}

>[!CAUTION]
>
>Als u Modellen van **inhoudsfragmenten** niet inschakelt, is de optie **Maken** niet beschikbaar voor het maken van nieuwe modellen.

Als u modellen van inhoudsfragmenten wilt inschakelen, moet u:

* Het gebruik van modellen van inhoudsfragmenten inschakelen in configuratiebeheer
* De configuratie toepassen op de map Middelen

### Modellen van inhoudsfragmenten inschakelen in Configuratiebeheer {#enable-content-fragment-models-in-configuration-manager}

Om een nieuw Model [van het Fragment van de Inhoud te](#creating-a-content-fragment-model) creëren **moet** u hen eerst toelaten gebruikend de Manager van de Configuratie:

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.
2. Selecteer de locatie die geschikt is voor uw website.
3. Gebruik **Maken** om het dialoogvenster te openen waarin u:

   1. Geef een **titel** op.
   2. Selecteer Modellen van **inhoudsfragmenten** om het gebruik ervan in te schakelen.
   ![configuratie](assets/cfm-models-01.png)

4. Selecteer **Maken** om de definitie op te slaan.

### De configuratie toepassen op de middelenmap {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **globaal** is ingeschakeld voor modellen van inhoudsfragmenten, kunnen alle modellen die gebruikers maken, worden gebruikt in elke map Middelen.

Als u andere configuraties (dat wil zeggen exclusief globaal) wilt gebruiken met een vergelijkbare map met assets, moet u de verbinding definiëren. U doet dit door de juiste **Configuratie** te selecteren op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

## Een inhoudsfragmentmodel maken {#creating-a-content-fragment-model}

1. Navigeer naar **Gereedschappen**, **Elementen** en open vervolgens Modellen **inhoudsfragmenten**.
1. Navigeer naar de map die geschikt is voor uw [configuratie](#enable-content-fragment-models).
1. Gebruik **Maken** om de wizard te openen.

   >[!CAUTION]
   >
   >Als het [gebruik van inhoudsfragmentmodellen niet is ingeschakeld](#enable-content-fragment-models), is de optie **Maken** niet beschikbaar.

1. Geef de **modeltitel** op. U kunt desgewenst ook een **beschrijving** toevoegen.

   ![titel en beschrijving](assets/cfm-models-02.png)

1. Gebruik **Maken** om het lege model op te slaan. Een bericht zal op het succes van de actie wijzen, kunt u **Open** selecteren om het model onmiddellijk uit te geven, of **Gedaan** om aan de console terug te keren.

## Het model van het inhoudsfragment definiëren {#defining-your-content-fragment-model}

Het inhoudsfragmentmodel definieert in feite de structuur van de resulterende inhoudsfragmenten. Gebruikend de modelredacteur kunt u, de vereiste gebieden toevoegen en vormen:

>[!CAUTION]
>
>Het bewerken van een bestaand inhoudsfragmentmodel kan invloed hebben op afhankelijke fragmenten.

1. Navigeer naar **Gereedschappen**, **Elementen** en open vervolgens Modellen **inhoudsfragmenten**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Open het vereiste model voor **Bewerken**; gebruik de snelle actie of selecteer het model en de actie op de werkbalk.

   Zodra open de modelredacteur toont:

   * links: velden al gedefinieerd
   * rechts: **datatypen** voor het maken van velden (en **eigenschappen** voor gebruik als er velden zijn gemaakt)
   >[!NOTE]
   >
   >Als een veld **Vereist** is, wordt het **label** in het linkerdeelvenster gemarkeerd met een sterretje (*****).

   ![eigenschappen](assets/cfm-models-03.png)

1. **Een veld toevoegen**

   * Sleep een vereist gegevenstype naar de vereiste locatie voor een veld:
   ![gegevenstype naar veld](assets/cfm-models-04.png)

   * Nadat een veld aan het model is toegevoegd, worden in het rechterdeelvenster de **eigenschappen** weergegeven die voor dat specifieke gegevenstype kunnen worden gedefinieerd. Hier kunt u definiëren wat voor dat veld is vereist. Bijvoorbeeld:
   ![veldeigenschappen](assets/cfm-models-05.png)

   >[!NOTE]
   >
   >Voor het datatype **Tekst met meerdere regels** is het mogelijk het **standaardtype** als volgt te definiëren:
   >* **RTF**
   >* **Markering**
   >* **Onbewerkte tekst**
   >Als er geen waarde wordt opgegeven, wordt de standaardwaarde voor **RTF** gebruikt voor dit veld.
   >Het wijzigen van het **standaardtype** in een contentfragmentmodel heeft alleen effect op een bestaand, gerelateerd contentfragment nadat dat fragment is geopend in de editor en opgeslagen.

1. **Een veld verwijderen**

   Selecteer het vereiste veld en klik op het pictogram met de prullenbak of tik erop. U wordt gevraagd de actie te bevestigen.

   ![remove](assets/cfm-models-06.png)

1. Nadat u alle vereiste velden hebt toegevoegd en de eigenschappen hebt gedefinieerd, gebruikt u **Opslaan** om de definitie te behouden. Bijvoorbeeld:

   ![save](assets/cfm-models-07.png)

## Een inhoudsfragmentmodel verwijderen {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>Het verwijderen van een inhoudsfragmentmodel kan invloed hebben op afhankelijke fragmenten.

Een inhoudsfragmentmodel verwijderen:

1. Navigeer naar **Gereedschappen**, **Elementen** en open vervolgens Modellen **inhoudsfragmenten**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer het model, gevolgd door **Verwijderen** op de werkbalk.

   >[!NOTE]
   >
   >Als naar het model wordt verwezen, wordt een waarschuwing gegeven. Voer de juiste actie uit.

## Een inhoudsfragmentmodel publiceren {#publishing-a-content-fragment-model}

Inhoudsfragmentmodellen moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

Een fragmentmodel voor inhoud publiceren:

1. Navigeer naar **Gereedschappen**, **Elementen** en open vervolgens Modellen **inhoudsfragmenten**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer het model, gevolgd door **Publiceren** op de werkbalk.

   >[!NOTE]
   >
   >Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, wordt dit in een selectielijst aangegeven en wordt het model met het fragment gepubliceerd.
