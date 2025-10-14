---
title: Pagina-eigenschappen bewerken
description: Leer hoe u de eigenschappen van een pagina bewerkt en het gedrag van de pagina wijzigt en hoe u deze beheert.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 83e61ae4af3dcd76ad51722decd0032cceb737a5
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 1%

---


# Pagina-eigenschappen bewerken {#page-properties}

Leer hoe te om [&#x200B; de eigenschappen van een pagina &#x200B;](/help/sites-cloud/authoring/sites-console/page-properties.md) uit te geven en gedrag van de pagina te veranderen en hoe het wordt geleid.

>[!TIP]
>
>Voor details op de individuele beschikbare paginaeigenschappen, te zien gelieve het document [&#x200B; Eigenschappen van de Pagina.](/help/sites-cloud/authoring/sites-console/page-properties.md)

## Pagina-eigenschappen bewerken {#where}

U kunt pagina-eigenschappen op een aantal plaatsen in AEM bewerken.

* [Van de &#x200B;](#from-the-sites-console)
* [Uit de pagina-editor](#from-the-page-editor)
* [Van de universele editor](#from-the-universal-editor)

Gebruikend de Console van Plaatsen kunt u ook [&#x200B; de eigenschappen van veelvoudige pagina&#39;s in één keer uitgeven.](#editing-multiple-pages)

### Van de Siteconsole {#from-the-sites-console}

Wanneer het doorbladeren van uw inhoud in de **console van de Plaatsen**, kunt u de **Eigenschappen** knoop in de toolbar gebruiken om paginaeigenschappen uit te geven:

1. Gebruikend de [**console van Plaatsen**, &#x200B;](/help/sites-cloud/authoring/sites-console/introduction.md) navigeer aan de plaats van de pagina waarvoor u eigenschappen bekijken en wilt uitgeven.
1. Selecteer de **optie van Eigenschappen** voor de vereiste pagina die of gebruikt:
   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/basic-handling.md#selecting-resources)
   * De pagina-eigenschappen worden weergegeven met de juiste tabbladen.
1. Bekijk of bewerk de eigenschappen naar wens.
1. Dan gebruik **sparen** om uw updates te bewaren die door **worden gevolgd dicht** om aan de console terug te keren.

### Uit de pagina-editor {#from-the-page-editor}

Wanneer het uitgeven van een pagina gebruikend de Redacteur van de Pagina, kunt u {de Informatie van de Pagina van 0} gebruiken **om de pagina-eigenschappen te bepalen:**

1. In de [&#x200B; Redacteur van de Pagina &#x200B;](/help/sites-cloud/authoring/page-editor/introduction.md), open de pagina waarvoor u eigenschappen wilt uitgeven.
1. Selecteer het **pictogram van de Informatie van de Pagina** om het selectiemenu te openen:
1. Selecteer **Open Eigenschappen** en een dialoog opent die u de eigenschappen laat uitgeven, die door het aangewezen lusje worden gesorteerd. De volgende knoppen zijn beschikbaar aan de rechterkant van de werkbalk:
   * **annuleert**
   * **sparen &amp; Sluiten**
1. Gebruik **sparen &amp; sluit** knoop om de veranderingen te bewaren.

## Van de universele editor {#from-the-universal-editor}

Wanneer het uitgeven van een pagina gebruikend de Universele Redacteur, kunt u het **pictogram van Eigenschappen van de Pagina gebruiken 0&rbrace; om de eigenschappen uit te geven:**

1. In de [&#x200B; Universele Redacteur &#x200B;](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties), open de pagina waarvoor u eigenschappen wilt uitgeven.
1. Selecteer het **pictogram van de Eigenschappen van de Pagina** in de toolbar.
1. Het venster van de pagina eigenschappen van AEM opent in een nieuw browser lusje enkel alsof u pagina-eigenschappen van de [&#x200B; Redacteur van de Pagina uitgeeft.](#from-the-page-editor) De volgende knoppen zijn beschikbaar aan de rechterkant van de werkbalk:
   * **annuleert**
   * **sparen &amp; Sluiten**
1. Gebruik **sparen &amp; sluit** knoop om de veranderingen te bewaren.
1. Ga terug naar het browsertabblad van de Universal Editor.

## De eigenschappen van meerdere pagina&#39;s bewerken {#editing-multiple-pages}

Van de **console van de Plaatsen[*&#128279;*](/help/sites-cloud/authoring/sites-console/introduction.md) u kunt verscheidene pagina&#39;s dan gebruiken &#x200B;** Eigenschappen van de Mening** om de pagina eigenschappen te bekijken en/of uit te geven. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Wanneer het doorbladeren van de **console van Plaatsen**
* Na het gebruiken van **Onderzoek** om van een reeks pagina&#39;s de plaats te bepalen

Na het selecteren van de pagina&#39;s en dan het klikken of het tikken van de **optie van Eigenschappen**, worden de bulkeigenschappen getoond:

![&#x200B; Bulk het uitgeven paginaeigenschappen &#x200B;](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* maakt geen deel uit van een live kopie
   * Als een van de geselecteerde pagina&#39;s deel uitmaakt van een live kopie, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Het venster voor bulkbewerking wordt verticaal in tweeën gedeeld:

* De linkerkant is een lijst met de pagina&#39;s die u hebt geselecteerd voor bulkbewerking.
   * U kunt de pagina&#39;s desgewenst selecteren of deselecteren.
   * Standaard zijn alle opties geselecteerd.
* Het recht is een lijst van [&#x200B; eigenschappen beschikbaar voor bulk het uitgeven.](/help/implementing/developing/extending/bulk-editor.md)
   * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.
   * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
   * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.
   * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven.
   * Wanneer het gebied multi-waarde (bijvoorbeeld, Markeringen) is, zullen de waarden slechts worden getoond wanneer *allen* gemeenschappelijk zijn. Als slechts enkele van de algemene voorbeelden worden weergegeven, worden deze alleen weergegeven tijdens het bewerken.
* Velden die veel voorkomen, maar die verschillende waarden hebben op de verschillende pagina&#39;s, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>` .

U kunt de waarden bijwerken in de velden die beschikbaar zijn op de pagina&#39;s die u selecteert. De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed** selecteert. Als het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.

## Overerving van eigenschappen {#inheritance}

Als de pagina op een blauwdruk gebaseerd is of anders inhoud van een andere pagina erft, wordt de overerving weerspiegeld in het **venster van de Eigenschappen van de 1&rbrace; pagina** voor het individuele gebied.

![&#x200B; Overgenomen eigenschappen &#x200B;](assets/property-inhertiance.png)

Overerfde eigenschappen kunnen niet worden bewerkt. Tik of klik **annuleer overerving** pictogram naast een bepaald gebied om zijn overerving te breken.

![&#x200B; annuleert overerving &#x200B;](assets/cancel-inheritance.png)

Bevestig de annulering in **annuleert overerving** modaal.

![&#x200B; annuleert overervingsbevestiging modaal &#x200B;](assets/cancel-inheriance-confirmation.png)

Nadat de overerving voor een veld is geannuleerd, wordt het veld bewerkbaar.

![&#x200B; Geannuleerde overerving &#x200B;](assets/property-inheritance-broken.png)

Om overerving opnieuw op te nemen, ontweek of klik **terugkeren overerving** pictogram naast het gebied.

![&#x200B; keert overerving &#x200B;](assets/revert-inheritance.png) terug

Bevestig de terugkeer in **terugkeren overerving** modaal.

![&#x200B; keert overervingsbevestiging modaal terug &#x200B;](assets/revert-inhertiance-confirmation.png)

Selecteer **Synchronize Pagina na het terugkeren van overerving** om het gebied met de recentste waarden in de blauwdruk bij te werken. Als u dat niet doet, worden de waarden bijgewerkt wanneer LiveCopy opnieuw wordt gesynchroniseerd.

>[!TIP]
>
>Voor meer informatie over overerving, gelieve te zien het document [&#x200B; Meerdere Manager van de Plaats en Vertaling &#x200B;](/help/sites-cloud/administering/msm-and-translation.md)
