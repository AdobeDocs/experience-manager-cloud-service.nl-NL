---
title: XFA-ondersteuning in adaptieve Forms op basis van XDP
description: Hier worden ondersteunde XFA-gebeurtenissen, -eigenschappen, -scripts en -validatie weergegeven in Adaptive Forms.
uuid: 75d3c292-cfed-438f-afdb-4071d95a08b7
topic-tags: develop
discoiquuid: 05303b29-9058-4723-b134-4ba605fe40c7
feature: Adaptive Forms
role: User
hide: true
hidefromtoc: true
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---


# XFA-ondersteuning in adaptieve Forms op basis van XDP{#xfa-support-in-xdp-based-adaptive-forms}

## Inleiding {#introduction}

Adaptive Forms biedt ondersteuning voor verschillende XFA-gebeurtenissen, -eigenschappen, -scripts en -validaties die in een XDP-bestand zijn gedefinieerd, zoals:

* Uitvoering van scripts gedefinieerd voor gebeurtenissen in het XDP-bestand.
* Standaardwaarden en gedragseigenschappen vastleggen voor velden in het XDP-bestand.
* Uitvoering van validatiescripts die zijn gedefinieerd in het XDP-bestand.

Wanneer een adaptief formulier wordt gemaakt op basis van een XDP-bestand, worden de eigenschappen, gebeurtenissen en validaties automatisch ingevuld in de gebruikersinterface van het formulierontwerp. Auteurs van formulieren kunnen sommige van deze elementen echter overschrijven om een andere ervaring te creëren.

In dit artikel worden ondersteunde XFA-gebeurtenissen, -eigenschappen en -validaties weergegeven die in Adaptive Forms worden ondersteund en wordt uitgelegd hoe u deze kunt overschrijven in Adaptive Forms.

## Ondersteunde XFA-elementen en hun toewijzing in Adaptive Forms {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### Velden {#fields}

Wanneer een adaptief formulier wordt gemaakt met een XDP-bestand, kunt u een XFA-veld naar het adaptieve formulier slepen. In de volgende tabel wordt aangegeven hoe XFA-velden worden toegewezen aan velden voor adaptieve formulieren.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA veld of container</strong></p> </td>
   <td><p><strong>Overeenkomende adaptieve formuliercomponent</strong></p> </td>
  </tr>
  <tr>
   <td><p>Knop </p> </td>
   <td><p>Knop</p> </td>
  </tr>
  <tr>
   <td><p>Selectievakje </p> </td>
   <td><p>Selectievakje</p> </td>
  </tr>
  <tr>
   <td><p>Keuzelijst </p> </td>
   <td><p>Vervolgkeuzelijst</p> </td>
  </tr>
  <tr>
   <td><p>Datum-/tijdveld </p> </td>
   <td><p>Datumkiezer</p> </td>
  </tr>
  <tr>
   <td><p>Krabbelen op handtekening</p> </td>
   <td><p>Krabbelhandtekening</p> </td>
  </tr>
  <tr>
   <td><p>Numeriek veld </p> </td>
   <td><p>Numeriek vak</p> </td>
  </tr>
  <tr>
   <td><p>Decimaal veld</p> </td>
   <td><p>Numeriek vak</p> </td>
  </tr>
  <tr>
   <td><p>Tekstveld </p> </td>
   <td><p>Tekstvak</p> </td>
  </tr>
  <tr>
   <td><p>Wachtwoordveld </p> </td>
   <td><p>Wachtwoordvak</p> </td>
  </tr>
  <tr>
   <td><p>Afbeelding</p> </td>
   <td><p>Afbeelding</p> </td>
  </tr>
  <tr>
   <td><p>Tekst</p> </td>
   <td><p>Tekst</p> </td>
  </tr>
  <tr>
   <td><p>Subformulier </p> </td>
   <td><p>Deelvenster</p> </td>
  </tr>
  <tr>
   <td><p>Gebied (groep)</p> </td>
   <td><p>Deelvenster</p> </td>
  </tr>
  <tr>
   <td><p>Subformulierset </p> </td>
   <td><p>Deelvenster</p> </td>
  </tr>
 </tbody>
</table>

### Eigenschappen {#properties}

In de volgende tabel wordt vastgelegd hoe verschillende XFA-scripts die in de XDP-bestanden zijn gedefinieerd, zich gedragen in Adaptive Forms.

<table>
 <tbody>
  <tr>
   <td><p><strong>Eigenschappen van XFA-componenten</strong></p> </td>
   <td><p><strong>Corresponsief gedrag in Adaptive Forms</strong></p> </td>
  </tr>
  <tr>
   <td><p>somExpression </p> </td>
   <td><p>Toegewezen aan de Bind verwijzingsbezit (bindRef) in AanpassingsVorm.</p> </td>
  </tr>
  <tr>
   <td><p>aanwezigheid </p> </td>
   <td><p>Toegewezen aan de zichtbare eigenschap in Adaptief formulier. U kunt deze negeren met behulp van de zichtbaarheidsexpressie.</p> </td>
  </tr>
  <tr>
   <td><p>toegang </p> </td>
   <td><p>Toegewezen aan de toegelaten eigenschap in Aangepaste Vorm. U kunt het met de uitdrukking van de Toegang met voeten treden.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: rol </p> </td>
   <td><p>Toegewezen aan de rolineigenschap in Adaptief formulier.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: speakPriority </p> </td>
   <td><p>Toegewezen aan het speakPriority bezit in Aangepaste Vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: speakText</p> </td>
   <td><p>Toegewezen aan de aangepaste toegankelijkheidstekst in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: knopinfo </p> </td>
   <td><p>Toegewezen aan de korte beschrijvingsbezit in AanpassingsVorm.</p> </td>
  </tr>
  <tr>
   <td><p>caption <em> (alle types van Gebied) </em></p> </td>
   <td><p>Toegewezen aan de eigenschap Titel in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>displayFormat <em> (alle types van Gebied) </em></p> </td>
   <td><p>Toegewezen aan het weergavepatroon in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>rawValue <em> (alle types van Gebied) </em></p> </td>
   <td><p>Toegewezen aan waarde-eigenschap in adaptief formulier.</p> </td>
  </tr>
  <tr>
   <td><p>items <em> (Keuzelijst, Selectievakje) </em></p> </td>
   <td><p>Eigenschap toegewezen aan opties in adaptief formulier. U kunt deze negeren met de expressie Opties.</p> </td>
  </tr>
  <tr>
   <td><p>maxChar <em> (het Gebied van de Tekst) </em></p> </td>
   <td><p>Toegewezen aan de eigenschap Maximum aantal tekens toegestaan in Adaptief formulier.</p> </td>
  </tr>
  <tr>
   <td><p>multiline <em> (het Gebied van de Tekst) </em></p> </td>
   <td><p>Toegewezen aan de eigenschap Meerdere regels toestaan in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>fracDigit <em> (Numeriek Gebied, Decimaal Gebied) </em></p> </td>
   <td><p>Toegewezen aan de eigenschap Frac digits in Adaptief formulier.</p> </td>
  </tr>
  <tr>
   <td><p>leadDigit <em> (Numeriek Gebied, Decimaal Gebied) </em></p> </td>
   <td><p>Toegewezen aan de eigenschap Lead digits in Adaptive Form.</p> </td>
  </tr>
  <tr>
   <td><p>multiSelect <em> (Keuzelijst) </em></p> </td>
   <td><p>Toegewezen aan de eigenschap Meerdere selecties toestaan in adaptieve vorm.</p> </td>
  </tr>
 </tbody>
</table>

### Scripts {#scripts}

In de volgende tabel wordt vastgelegd hoe verschillende XFA-scripts die in het XDP-bestand zijn gedefinieerd, zich gedragen in Adaptive Forms.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-scriptgebeurtenissen</strong></p> </td>
   <td><p><strong>Corresponsief gedrag in Adaptive Forms</strong></p> </td>
  </tr>
  <tr>
   <td><p>initialiseren </p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>berekenen</p> </td>
   <td><p>Toegewezen aan de expressie Berekenen in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>validate </p> </td>
   <td><p>Toegewezen aan de uitdrukking van de Bevestiging in Adaptief Vorm.</p> </td>
  </tr>
  <tr>
   <td><p>validationState </p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in adaptieve vorm.<br /> </p> </td>
  </tr>
  <tr>
   <td><p>exit </p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>klikken (knopvelden)</p> </td>
   <td><p>Toegewezen aan de klikuitdrukking van de knoop.</p> </td>
  </tr>
  <tr>
   <td><p>Ondersteuning voor serverscripts</p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Ondersteuning voor webservices</p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Wijzigen (krabbelveld, keuzerondje, selectievakje)</p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in adaptieve vorm.</p> </td>
  </tr>
 </tbody>
</table>

### Validaties {#validations}

In de volgende tabel wordt vastgelegd hoe XFA-validaties worden toegewezen aan validaties in Adaptive Forms.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-validatie</strong></p> </td>
   <td><p><strong>Overeenkomende validatie in adaptief formulier</strong></p> </td>
  </tr>
  <tr>
   <td><p>Validatiepatroon (formatTest)</p> </td>
   <td><p>validatePictureClause</p> </td>
  </tr>
  <tr>
   <td><p>Bericht van validatiepatroon (formatTestMessage)</p> </td>
   <td><p>validatePictureMessage</p> </td>
  </tr>
  <tr>
   <td><p>Vereist (nullTest)</p> </td>
   <td><p>verplicht </p> </td>
  </tr>
  <tr>
   <td><p>Leeg bericht (nullTestMessage) </p> </td>
   <td><p>mandatoryMessage</p> </td>
  </tr>
  <tr>
   <td><p>Script valideren (scriptTest)</p> </td>
   <td><p>validateExp</p> </td>
  </tr>
  <tr>
   <td><p>Bericht van validatiescript (scriptTestMessage)</p> </td>
   <td><p>validateMessage</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt de verplichte eigenschap voor het keuzerondje Adaptief formulier en de groep selectievakjes die zijn gebonden aan XFA-knoppen, niet overschrijven.

