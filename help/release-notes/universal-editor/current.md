---
title: Opmerkingen bij de release van Universal Editor 2024.08.13
description: Dit zijn de releaseopmerkingen voor de release 2024.08.13 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: aad4d0353fb5e2eacb518b72e935def931d0798a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2024.08.13 {#release-notes}

Dit zijn de opmerkingen bij de release van 13 augustus 2024 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nieuwe functies {#what-is-new}

* **de Types van Gegevens van de Douane**: Tailor de redacteur aan uw unieke gegevensbehoeften met de capaciteit om douanegebieden binnen het eigenschappen paneel tot stand te brengen.
   * Of u nu een aangepaste productkiezer ontwikkelt voor gebruik in handelsversies of een vervolgkeuzelijst vult met waarden uit uw achtergronden, deze functie geeft u de controle die u nodig hebt over de gegevens die auteurs gebruiken om inhoud samen te stellen.
* **de Belemmering &amp; Daling van 0} dwars-Container: Geniet van grotere flexibiliteit in lay-outsamenstelling met de capaciteit om componenten over verschillende containers te bewegen via belemmering en daling ](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) binnen het [ paneel van de Boom van de Inhoud.](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode)**[
* **Geoptimaliseerde Integratie GitHub**: Het coderen voor reacties GitHub is geïntroduceerd, beduidend sneller terugwinning van markeringen en `universal-editor-cors-library`, resulterend in een snellere en vlottere gebruikerservaring.
* **Managed Services RPM Pakket**: De Adobe biedt nu een pakket van RPM aan om de plaatsing en het beheer van de Universele Dienst van de Redacteur te stroomlijnen, die onderhoud vereenvoudigen en operationele overheadkosten voor de beheerde diensten verminderen.
* **configureerbare IMS Symbolische Bevestiging**: Om flexibiliteit in symbolisch beheer te verhogen, is IMS symbolische bevestiging nu facultatief.
   * Met deze configuratieoptie kunt u validatie desgewenst uitschakelen en de instellingen van uw cloudgateway vereenvoudigen.
* **de Integratie van het Splunk**: Het registreren van het spleet is geïntegreerd in de [ Universele Dienst van de Redacteur voor lokale ontwikkeling, ](/help/implementing/universal-editor/local-dev.md) verbeterend toezicht en diagnostiek.
   * Deze integratie zorgt voor een efficiënte logboekregistratie, vloeiendere bewerkingen en snellere probleemoplossing.

## Opgeloste problemen {#bug-fixes}

* **Verbeterde het Publiceren Terugkoppeling**: Als de publicatie wegens ontoereikende toestemmingen ontbreekt, terugkoppel aan de gebruiker tijdens het publiceren is verbeterd om een duidelijke waarschuwing te tonen in plaats van eenvoudig op een mislukking te wijzen.
* **Verbeterde behandeling URL**: De kwesties met onjuiste het coderen URL/decoderen die het publiceren mislukkingen veroorzaakten werden opgelost.
* **Accurate Gegevens die** behandelen: Een kwestie waar de vlotteraantallen verkeerd werden opgeslagen aangezien de gehelen zijn gericht, die nauwkeurige gegevens behandelen over uw inhoud verzekeren.
* **Veiligheid en Stabiliteit**: De kwetsbaarheid van de veiligheid in de beelden van het Docker is bevestigd en de testdekking voor kritieke componenten zoals de Plukker van de Component en Breadcrumbs zijn uitgevoerd, leidend tot een veiligere, stabielere, en betrouwbare redactervaring.
