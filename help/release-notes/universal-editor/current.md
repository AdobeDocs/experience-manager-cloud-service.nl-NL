---
title: Opmerkingen bij de release van Universal Editor 2024.11.12
description: Dit zijn de releaseopmerkingen voor de release 2024.11.12 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 03ccad00e689052ada8cca976d6c385be01d3cc9
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2024.11.12 {#release-notes}

Dit zijn de releaseopmerkingen voor de release van 12 november 2024 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nieuwe functies {#what-is-new}

* **probeer Optie op Onderbreking CORS opnieuw:** met [ versie 2024.09.26, ](/help/release-notes/universal-editor/2024/2024-09-26.md) werd een foutenpaneel geïntroduceerd toen de redacteur geen verbinding aan de geladen pagina kon vestigen, verhinderend eindeloze ladingsstaten.
   * Met deze versie blijft de editor het opnieuw proberen en zodra de verbinding tot stand is gebracht, kan het bewerken worden hervat.
   * Dit is vooral handig voor pagina&#39;s die langer kunnen duren dan de time-out van één minuut voor initialisatie.
* **de Verbeteringen van de Rekbaarheid voor Ontwikkelaars:** De Universele Redacteur steunt nu uitzendende gebeurtenissen aan uitbreidingen, toestaand uitbreidingsontwikkelaars om aan [ gebeurtenissen in te tekenen.](/help/implementing/universal-editor/events.md)
   * Dit laat ontwikkelaars toe om [ aan redacteursgebeurtenissen binnen hun douaneuitbreidingen te reageren.](/help/implementing/universal-editor/customizing.md#extending)
* **Blijvende Selectie van de Component:** Geselecteerde componenten in de redacteur zullen nu blijven zelfs na het verfrissen van browser.
   * Dit zorgt ervoor dat gebruikers kunnen blijven werken zonder hun context te verliezen wanneer ze de pagina opnieuw laden.
* **Gelokaliseerde Snelle Verbindingen:** de **Snelle sectie van Verbindingen** op het huisscherm verstrekt nu gelokaliseerde verbindingen aan documentatie, die gebruikers gemakkelijk tot relevante gidsen toegang helpen die op hun taalvoorkeur worden gebaseerd.
* **identiteitskaart van het Verzoek voor Geavanceerd het Zuiveren:** de berichten van de Fout omvatten nu identiteitskaart van het a **Verzoek** in de detailssectie, die met `x-request-id header` correleert.
   * Dit maakt het voor de ingenieursteams van de Adobe gemakkelijker om kwesties te vinden en te diagnostiseren door die fouten met interne logboeken aan te passen.

## Overige verbeteringen {#other-improvements}

* **Vaste Lange Etiketten van de Boom van de Inhoud:** loste een kwestie op waar de lange etiketten in het **paneel van de Boom van de Inhoud** weg werden geknipt
   * Zo zorgt u ervoor dat handgrepen voor slepen en neerzetten altijd zichtbaar zijn voor het opnieuw ordenen van inhoud.
* **Vaste Lange Etiketten van Eigenschappen:** geadresseerde een insect waar de lange gebiedslabels in het **paneel van Eigenschappen** met de informatie van de gebiedsbevestiging overlapten
* **Horizontaal Schuiven in het Comité van Eigenschappen:** Vaste een kwestie waar de brede elementen in het **paneel van Eigenschappen** horizontaal het scrollen veroorzaakten
* **Vaste Inactieve Toolbar tijdens Meldingen:** de hoogste **3} toolbar van Adobe Experience Cloud {is nu volledig functioneel wanneer [ toast ](https://spectrum.adobe.com/page/toast/) berichten worden getoond.**
* **Verbeterde Stabiliteit:** Toegevoegde foutengrenzen om onverwachte waarden te behandelen, verhinderend volledige UI te crashen wanneer één enkele renderer of validator ontbreekt, verbeterend robuustheid
