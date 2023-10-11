---
title: Tips en trucs die u kunt onthouden bij het werken met AEM adaptieve formulieren.
description: Sommige aanbevolen procedures en belangrijke punten die u moet onthouden wanneer u werkt met componenten van een adaptief formulier.
source-git-commit: d33c7278d16a8cce76c87b606ca09aa91f1c3563
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# Aanbevolen procedures voor het werken met componenten{#best-practices-for-working-with-components}

U kunt de volgende tips en trucs gebruiken bij het werken met Aangepaste formuliercomponenten:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Tik op de component en tik om de eigenschappen van een component te configureren ![eigenschappen](assets/Smock_Wrench_18_N.svg) om de componenteigenschappen in de browser van Eigenschappen te openen.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u tikt ![eigenschappen](assets/Smock_Wrench_18_N.svg)kunt u de naam van de component wijzigen door de **[!UICONTROL Element Name]** in de eigenschappenbrowser. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.

* U kunt de eigenschap Titel van een component Adaptief formulier inline wijzigen in de formuliereditor zonder de browser Eigenschappen te openen, zolang de titel maar zichtbaar is op het formulier. Daartoe:

   1. Tik om een component te selecteren die een **[!UICONTROL Title]** eigendom en waarvan **[!UICONTROL Hide title]** eigenschap is uitgeschakeld.

   1. Tikken ![Pictogram Bewerken](assets/Smock_Edit_18_N.svg) om de titel bewerkbaar te maken.

   1. Wijzig de titel en tik op de Return-toets of tik ergens buiten de component om de wijzigingen op te slaan. Tik op de toets Esc om de wijzigingen te verwijderen.

* Sommige componenten van Adaptief formulier, zoals E-mail en Telefoon, bevatten validatiepatronen die niet in de verpakking staan. U kunt echter aangepaste validatie opgeven door het dialoogvenster **[!UICONTROL Validation Pattern]** onder de accordeon Patronen in de eigenschappen van de component. Zie de componentbeschrijvingen in de bovenstaande tabel voor meer informatie over standaardvalidaties.

* Adaptieve Forms-velden, zoals Numerieke vakken en E-mail, kunnen zo worden geconfigureerd dat ze speciale HTML-invoertypen bevatten. Wanneer deze velden de focus hebben op mobiele apparaten en tablets, worden op het toetsenblok specifieke alfabet, getallen en tekens vóór weergegeven die doorgaans worden gebruikt voor het invoeren van informatie in de velden. Het helpt gebruikers informatie snel ingaan zonder het moeten tussen karakterreeksen op het toetsenbord van een knevel voorzien. Als u gespecialiseerde invoer voor een component wilt toestaan, schakelt u de optie **[!UICONTROL Use HTML Type Number]** in de componenteigenschappen.

* U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Als u RTF-tekst wilt inschakelen voor een tekstvak, schakelt u de optie **[!UICONTROL Allow Rich Text]** in de componenteigenschappen.

* U kunt de componenten van het Doos van de Tekst, E-mail, en van de Telefoon aan autofill waarden voor gebieden zoals naam, adres, creditcard, telefoon, en e-mail van de informatie toelaten die in browser autofill montages wordt opgeslagen. Selecteer **[!UICONTROL Enable Autofill]** in de componenteigenschappen en selecteer een **[!UICONTROL Autofill Attribute]**. Wanneer een gebruiker een adaptief formulier invult, worden de waarden voorgesteld vanuit het profiel voor automatisch invullen in de browser of op basis van de waarden die eerder door de gebruiker zijn ingevuld. Automatisch vullen werkt alleen als de instellingen voor automatisch vullen in de browser van de gebruiker zijn ingeschakeld.

* Geef waarden op voor de items Keuzerondje en Selectievakje in `{value}={text}` in componenteigenschappen.
* Met de component Bestandsbijlage kan een gebruiker standaard slechts één bestand bijvoegen. U kunt de componenteigenschappen echter configureren om meerdere bijlagen te ondersteunen. Als een gebruiker meerdere bestanden met dezelfde bestandsnaam bijvoegt, kunnen er bovendien problemen optreden in de bijlagen. Daarom wordt aanbevolen een unieke id te koppelen voor elke verzonden bijlage bij het verzenden van het formulier. Daartoe:

   1. Op uw [!DNL AEM Forms] server, navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
   1. Zoeken en tikken **[!UICONTROL Adaptive Forms Configuration Service]**.
   1. Schakel in het dialoogvenster Adaptive Forms Configuration Service de optie **[!UICONTROL Make File Names Unique]**. Standaard is dit uitgeschakeld.

* Om gebruikers in staat te stellen een PDF vast te maken gebruikend browser Safari, zorg ervoor dat **application/pdf** wordt toegevoegd aan de eigenschap Ondersteunde bestandstypen van de component Bestandsbijlage. Adaptieve Forms gemaakt met vorige [!DNL AEM Forms] versie kan bevatten **.pdf** in plaats van **application/pdf** in de eigenschap Ondersteunde bestandstypen.

>[!NOTE]
>
>Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (right to left). Bijvoorbeeld Hebreeuws.