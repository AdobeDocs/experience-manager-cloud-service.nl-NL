---
title: Tips en trucs die u kunt onthouden bij het werken met AEM adaptieve formulieren.
description: Sommige aanbevolen procedures en belangrijke punten die u moet onthouden wanneer u werkt met componenten van een adaptief formulier.
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Aanbevolen procedures voor het werken met componenten{#best-practices-for-working-with-components}

U kunt de volgende tips en trucs gebruiken bij het werken met Aangepaste formuliercomponenten:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Om de eigenschappen van een component te vormen, selecteer de component en selecteer ![ eigenschappen ](assets/Smock_Wrench_18_N.svg) om de componenteneigenschappen in browser van Eigenschappen te openen.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u ![ eigenschappen ](assets/Smock_Wrench_18_N.svg) selecteert, kunt u de naam van de component veranderen door de **[!UICONTROL Element Name]** gebiedswaarde in eigenschappen browser te veranderen. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.

* U kunt de eigenschap Titel van een component Adaptief formulier inline wijzigen in de formuliereditor zonder de browser Eigenschappen te openen, zolang de titel maar zichtbaar is op het formulier. Daartoe:

   1. Selecteer deze optie om een component te selecteren die een eigenschap **[!UICONTROL Title]** heeft en waarvan de eigenschap **[!UICONTROL Hide title]** is uitgeschakeld.

   1. Selecteer ![ uitgeven pictogram ](assets/Smock_Edit_18_N.svg) om de titel editable te maken.

   1. Wijzig de titel en selecteer de Return-toets of selecteer een willekeurige locatie buiten de component om de wijzigingen op te slaan. Selecteer de sleutel van Esc om de veranderingen te verwerpen.

* Sommige componenten van Adaptief formulier, zoals E-mail en Telefoon, bevatten validatiepatronen die niet in de verpakking staan. U kunt echter aangepaste validatie opgeven door het veld **[!UICONTROL Validation Pattern]** onder de accordeon Patronen bij te werken in de componenteigenschappen. Zie de componentbeschrijvingen in de bovenstaande tabel voor meer informatie over standaardvalidaties.

* Adaptieve Forms-velden, zoals Numerieke vakken en E-mail, kunnen zo worden geconfigureerd dat ze speciale HTML-invoertypen bevatten. Wanneer deze velden de focus hebben op mobiele apparaten en tablets, worden op het toetsenblok specifieke alfabet, getallen en tekens vóór weergegeven die doorgaans worden gebruikt voor het invoeren van informatie in de velden. Het helpt gebruikers informatie snel ingaan zonder het moeten tussen karakterreeksen op het toetsenbord van een knevel voorzien. Als u gespecialiseerde invoer voor een component wilt toestaan, schakelt u het selectievakje **[!UICONTROL Use HTML Type Number]** in de componenteigenschappen in.

* U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Als u tekst met opmaak wilt inschakelen voor een tekstvak, schakelt u het selectievakje **[!UICONTROL Allow Rich Text]** in de eigenschappen van de component in.

* U kunt de componenten van het Doos van de Tekst, E-mail, en van de Telefoon aan autofill waarden voor gebieden zoals naam, adres, creditcard, telefoon, en e-mail van de informatie toelaten die in browser autofill montages wordt opgeslagen. Selecteer **[!UICONTROL Enable Autofill]** in de componenteigenschappen en selecteer een **[!UICONTROL Autofill Attribute]** om deze functie in te schakelen. Wanneer een gebruiker een adaptief formulier invult, worden de waarden voorgesteld vanuit het profiel voor automatisch invullen in de browser of op basis van de waarden die eerder door de gebruiker zijn ingevuld. Automatisch vullen werkt als de instellingen voor automatisch vullen in de browser van de gebruiker zijn ingeschakeld.

* Geef waarden op voor keuzerondjes en selectievakjes in de indeling `{value}={text}` in componenteigenschappen.
* Met de component Bestandsbijlage kan een gebruiker standaard slechts één bestand bijvoegen. U kunt de componenteigenschappen echter configureren om meerdere bijlagen te ondersteunen. Als een gebruiker meerdere bestanden met dezelfde bestandsnaam bijvoegt, kunnen er bovendien problemen optreden in de bijlagen. Daarom wordt aanbevolen een unieke id te koppelen voor elke verzonden bijlage bij het verzenden van het formulier. Daartoe:

   1. Navigeer op de [!DNL AEM Forms] -server naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** .
   1. Zoeken en selecteren **[!UICONTROL Adaptive Forms Configuration Service]** .
   1. Schakel **[!UICONTROL Make File Names Unique]** in het dialoogvenster Adaptive Forms Configuration Service in. Standaard is dit uitgeschakeld.

* Om gebruikers toe te laten om een PDF vast te maken gebruikend browser Safari, zorg ervoor dat **application/pdf** aan het Ondersteunde bezit van de Types van Dossier van de component van de gehechtheid van het Dossier wordt toegevoegd. De adaptieve Forms die met vorige [!DNL AEM Forms] versie wordt gecreeerd kan **.pdf** in plaats van **application/pdf** in het Ondersteunde bezit van de Types van Dossier bevatten.

>[!NOTE]
>
>Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (right to left). Bijvoorbeeld Hebreeuws.