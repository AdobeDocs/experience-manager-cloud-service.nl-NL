---
title: Pagina's maken en ordenen
description: Leer hoe u uw website kunt ordenen door pagina's met AEM te maken en te beheren.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '2424'
ht-degree: 1%

---


# Pagina&#39;s maken en ordenen {#creating-and-organizing-pages}

In dit document wordt beschreven hoe u pagina&#39;s kunt maken en beheren met Adobe Experience Manager Cloud Service, zodat u [inhoud maken](/help/sites-cloud/authoring/fundamentals/editing-content.md) op die pagina&#39;s.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten en machtigingen nodig om op pagina&#39;s te kunnen werken, zoals maken, kopiëren, verplaatsen, bewerken en verwijderen.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to act on pages such as create, copy, move, edit, and delete.
-->

>[!TIP]
>
>Er zijn verschillende [sneltoetsen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) die u kunt gebruiken vanuit de websiteconsole om uw pagina&#39;s efficiënter te ordenen.

{{edge-delivery-authoring}}

## Uw website ordenen {#organizing-your-website}

Als auteur moet u uw website organiseren binnen AEM. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* U kunt deze gemakkelijk vinden in de ontwerpomgeving
* Bezoekers naar uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt ook [mappen](#creating-a-new-folder) om uw inhoud beter in te delen.

De structuur van een website kan worden beschouwd als een structuur die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titels worden getoond wanneer de paginainhoud wordt bekeken.

In het volgende voorbeeld wordt getoond [WKND-zelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) site, waar een artikel over skateparks ( `la-skateparks`) is geopend:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

```xml
 /content
 /wknd
  /en
   /music
    /...
   /sports
    /la-skateparks
    /five-gyms-la
    /mountain-bike-routes
   /shopping
    /...
   /art
    /...
   /...
```

Deze structuur kan worden weergegeven vanuit de **Sites** console, waar u kunt [door de pagina&#39;s van uw website navigeren](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en voert handelingen uit op de pagina&#39;s. U kunt ook nieuwe sites maken en [nieuwe pagina&#39;s](#creating-a-new-page).

Vanuit elk punt kunt u de vertakking naar boven zien vanuit de broodkruimels in de kopbalk:

![Door broodkruimels te navigeren](/help/sites-cloud/authoring/assets/organizing-breadcrumbs.png)

### Naamgevingsconventies voor pagina {#page-naming-conventions}

Bij het maken van een pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:

   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.

* **[Naam](#name)**:

   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel. Zie de volgende sectie [Beperkingen en aanbevolen procedures voor paginanamen](#page-name-restrictions-and-best-practices) voor meer informatie.

#### Beperkingen en aanbevolen procedures voor paginanamen {#page-name-restrictions-and-best-practices}

De **titel** en **naam** van de pagina kunnen afzonderlijk worden gemaakt, maar zijn aan elkaar gerelateerd:

* Bij het maken van een pagina worden alleen de **Titel** is vereist. Indien niet **Naam** wordt opgegeven bij het maken van de pagina. AEM genereert een naam uit de eerste 64 tekens van de titel (met inachtneming van de onderstaande validatie). Alleen de eerste 64 tekens worden gebruikt ter ondersteuning van de beste praktijken voor namen van korte pagina&#39;s.
* Als een paginanaam handmatig door de auteur wordt opgegeven, geldt de limiet van 64 tekens niet, maar kunnen andere technische beperkingen op de lengte van de paginanaam wel van toepassing zijn.

>[!TIP]
>
>Wanneer u een paginanaam definieert, is het verstandig de paginanaam zo kort maar expressief en zo gedenkwaardig mogelijk te houden, zodat de lezer deze goed begrijpt. Zie de [W3C-stijlhulplijn](https://www.w3.org/Provider/Style/TITLE.html) voor de `title` voor meer informatie.
>
>Houd er ook rekening mee dat sommige browsers (bijvoorbeeld oudere versies van IE) URL&#39;s tot een bepaalde lengte alleen kunnen accepteren, dus er is ook een technische reden om paginanamen kort te houden.

Wanneer u een pagina maakt, AEM [valideert de paginanaam volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en het GCO.

De minimaal toegestane tekens zijn:

* `a` doorheen `z`
* `A` doorheen `Z`
* `0` doorheen `9`
* `_` (onderstrepingsteken)
* `-` (afbreekstreepje/minteken)

Alle tekens die zijn toegestaan, zijn beschikbaar in [naamconventies](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Paginanamen mogen maximaal 150 tekens bevatten.

#### Titel {#title}

Als u alleen een pagina opgeeft **Titel** wanneer u een pagina maakt, wordt AEM de pagina afgeleid **Naam** van deze tekenreeks en [De naam valideren volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en JCR.

A **Titel** veld met ongeldige tekens wordt geaccepteerd, maar voor de afgeleide naam worden de ongeldige tekens vervangen. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

#### Naam {#name}

Wanneer u een pagina opgeeft **Naam** bij het maken van een pagina, AEM [valideert de naam volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en JCR. U kunt geen ongeldige tekens verzenden in het dialoogvenster **Naam** veld. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd met een uitleg.

![Voorbeeld van het invoeren van een ongeldige paginanaam](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Gebruik geen code van twee letters, zoals gedefinieerd door ISO-639-1, als paginanaam, tenzij dit een hoofdtaalcode is.
>
>Zie [Inhoud voorbereiden voor vertaling](/help/sites-cloud/administering/translation/preparation.md) voor meer informatie .

### Sjablonen {#templates}

In AEM geeft een sjabloon een speciaal type pagina op. Een sjabloon wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. Sjablonen bestaan uit [componenten](#components).

AEM wordt geleverd met verschillende sjablonen die buiten de box zijn geplaatst. Welke sjablonen beschikbaar zijn, is afhankelijk van de afzonderlijke website. De belangrijkste velden zijn:

* **Titel**
De titel die op de resulterende webpagina wordt weergegeven.

* **Naam**
Wordt gebruikt bij de naamgeving van de pagina.

* **Sjabloon**
Een lijst met sjablonen die u kunt gebruiken bij het genereren van de nieuwe pagina.

>[!TIP]
>
>Indien gevormd op uw instantie, [sjabloonauteurs kunnen sjablonen maken met de Sjablooneditor](/help/sites-cloud/authoring/features/templates.md).

### Onderdelen {#components}

Componenten zijn de elementen die worden verschaft door AEM, zodat u specifieke typen inhoud kunt toevoegen. AEM wordt geleverd met een reeks kant-en-klare componenten die uitgebreide functionaliteit bieden. Deze omvatten:

* Tekst
* Afbeelding
* Titel
* Carousel
* En nog veel meer

Als u eenmaal een pagina hebt gemaakt en geopend, kunt u [inhoud toevoegen met de componenten](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component), die beschikbaar zijn op [componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

>[!TIP]
>
>De [Componentenconsole](/help/sites-cloud/authoring/features/components-console.md) geef een overzicht van de componenten op uw instantie.

## Pagina&#39;s beheren {#managing-pages}

### Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s van tevoren voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Open de Sites-console (bijvoorbeeld `https://<host>:<port>/sites.html/content`.
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. De keuzelijst openen met **Maken** in de werkbalk selecteert u vervolgens **Pagina** in de lijst:

   ![Een pagina maken](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Vanaf de eerste fase van de wizard kunt u:

   * Selecteer de sjabloon die u wilt gebruiken om de nieuwe pagina te maken en selecteer vervolgens **Volgende** om verder te gaan.

   * **Annuleren** om het proces af te breken.

   ![Een sjabloon voor een nieuwe pagina selecteren](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Vanaf het laatste werkgebied van de wizard kunt u:

   * Gebruik de drie tabbladen om de [pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) u wilt toewijzen aan de nieuwe pagina en selecteert u vervolgens **Maken** om de pagina te maken.

   * Gebruiken **Vorige** om terug te keren naar de sjabloonselectie.

   Hoofdvelden zijn:

   * **Titel**:

      * Dit wordt aan de gebruiker getoond en is verplicht.

   * **Naam**:

      * Hiermee wordt de URI gegenereerd. Indien niet opgegeven, wordt de naam afgeleid van de titel.
      * Als u een pagina **Naam** bij het maken van een pagina, AEM [valideert de naam volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en JCR.
      * U **kan geen ongeldige tekens verzenden** in de **Naam** veld. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

   >[!TIP]
   >
   >Zie [Naamgevingsconventies voor pagina](#page-naming-conventions).

   De minimale informatie die nodig is om een pagina te maken, is de **Titel**.

   ![Paginatitel opgeven](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Gebruiken **Maken** om het proces te voltooien en uw nieuwe pagina te maken. In het bevestigingsvenster wordt u gevraagd of u **Openen** de pagina direct of terug naar de console (**Gereed**):

   ![Maken van pagina voltooid](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >Als u een pagina maakt met een naam die al op die locatie bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `beach` bestaat al, wordt een nieuwe pagina `beach1`.

1. Als u terugkeert naar de console kunt u uw nieuwe pagina zien:

   ![Resulterende nieuwe pagina](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>Nadat een pagina is gemaakt, kan de sjabloon ervan niet worden gewijzigd - tenzij u [een lancering met een nieuw malplaatje creëren](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), hoewel de bestaande inhoud hierdoor verloren zal gaan.

### Een pagina openen voor bewerken {#opening-a-page-for-editing}

Nadat u een pagina hebt gemaakt of naar een bestaande pagina (in de console) hebt genavigeerd, kunt u deze openen om te bewerken:

1. Open de **Sites** console.
1. Navigeer totdat u de pagina vindt die u wilt bewerken.
1. Selecteer de pagina door een van de volgende twee methoden te gebruiken:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de werkbalk

   Selecteer vervolgens de **Bewerken** pictogram:

   ![Bewerken, knop](/help/sites-cloud/authoring/assets/edit.png)

1. De pagina wordt geopend en u kunt [de pagina bewerken](/help/sites-cloud/authoring/fundamentals/editing-content.md) zoals vereist.

>[!NOTE]
>
>U kunt vanuit de pagina-editor alleen naar andere pagina&#39;s navigeren in de modus Voorbeeld, omdat koppelingen niet actief zijn in de modus Bewerken.

### Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

U kunt een pagina en alle subpagina&#39;s ervan naar een nieuwe locatie kopiëren:

1. In de **Sites** navigeren totdat u de pagina hebt gevonden die u wilt kopiëren.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de werkbalk

   En dan de **Kopiëren** pagina-pictogram:

   ![Kopiëren](/help/sites-cloud/authoring/assets/copy.png)

1. Navigeer naar de locatie voor de nieuwe kopie van de pagina.
1. Selecteer de **Plakken** pictogram dat beschikbaar kwam.

   ![Plakken](/help/sites-cloud/authoring/assets/paste.png)

1. Het dialoogvenster Plakken bevat een overzicht van de plaktransactie en de mogelijkheid om:
   * **Nieuwe sitenaam:** De naam van de geplakte pagina wijzigen
   * **Plakken zonder onderliggende elementen:** De onderliggende pagina&#39;s van de geselecteerde pagina weglaten tijdens het plakken (onderliggende pagina&#39;s worden standaard geplakt)

   ![Dialoogvenster Plakken](/help/sites-cloud/authoring/assets/paste-dialog.png)

1. Selecteer de **Plakken** om de plaktransactie te bevestigen en de nieuwe pagina(&#39;s) te maken.

>[!NOTE]
>
>Als u de pagina kopieert naar een locatie waar al een pagina met dezelfde naam als het origineel bestaat, genereert het systeem automatisch een variatie in de naam door een nummer toe te voegen. Als `beach` bestaat al, een nieuwe pagina met de naam `beach` wordt `beach1`.

>[!NOTE]
>
>Als u de plakactie in selectiemodus begint, wordt dit automatisch verlaten zodra de pagina wordt gekopieerd.

### Een pagina verplaatsen of de naam ervan wijzigen {#moving-or-renaming-a-page}

De procedure voor het verplaatsen of wijzigen van de naam van een pagina is in feite hetzelfde en beide handelingen worden verwerkt door de wizard Pagina verplaatsen. Met deze wizard kunt u:

* Naam van pagina wijzigen zonder deze te verplaatsen
* De pagina verplaatsen zonder de naam ervan te wijzigen
* Tegelijkertijd verplaatsen en hernoemen

AEM biedt u de functionaliteit om interne koppelingen bij te werken die verwijzen naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

1. Navigeer totdat u de pagina vindt die u wilt verplaatsen.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de werkbalk

   Selecteer vervolgens de **Verplaatsen** pagina-pictogram:

   ![Knop Verplaatsen](/help/sites-cloud/authoring/assets/move.png)

   Hiermee opent u de wizard Verplaatsen pagina.

1. Van de **Naam wijzigen** het werkgebied van de wizard dat u kunt instellen:

   * Geef de naam op die de pagina moet krijgen nadat deze is verplaatst en selecteer **Volgende** om verder te gaan.
   * **Annuleren** om het proces af te breken.

   ![Pagina verplaatsen en hernoemen](/help/sites-cloud/authoring/assets/move-page-rename.png)

   De paginanaam kan hetzelfde blijven als u alleen de pagina verplaatst.

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `beach` bestaat al, een nieuwe pagina met de naam `beach` wordt `beach1`.

1. Van de **Doel selecteren** het werkgebied van de wizard dat u kunt instellen:

   * Gebruik de [kolomweergave](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) om naar de nieuwe locatie voor de pagina te navigeren:

      * Selecteer de bestemming door de duimnagel van de bestemming te klikken.
      * Klikken **Volgende** om door te gaan.

   * Gebruiken **Vorige** om terug te keren naar de specificatie van de paginanaam.

   >[!NOTE]
   >
   >Standaard is het bovenliggende element van de pagina die u verplaatst of waarvan u de naam wijzigt, geselecteerd als het doel.

   ![Doel voor verplaatsen pagina selecteren](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `winter` bestaat al, `winter` wordt `winter1`.

1. Als de pagina is gekoppeld aan of waarnaar wordt verwezen, of is gepubliceerd, worden de details weergegeven in het dialoogvenster **Aanpassen/Opnieuw publiceren** stap.

   U kunt aangeven welke aanpassingen moeten worden aangebracht en/of opnieuw moeten worden gepubliceerd.

   >[!NOTE]
   >
   >Als er geen koppeling is naar de pagina en er niet naar wordt verwezen, is deze stap niet beschikbaar.

   ![Pagina verplaatsen opnieuw publiceren](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Selecteren **Verplaatsen** zal het proces voltooien en de pagina naar wens verplaatsen/hernoemen.

>[!NOTE]
>
>Als de pagina al is gepubliceerd, wordt de publicatie ervan automatisch ongedaan gemaakt wanneer u de pagina verplaatst. Standaard wordt de animatie opnieuw gepubliceerd wanneer de verplaatsing is voltooid, maar dit kan veranderen door de controle op de knop **Opnieuw publiceren** in het veld **Aanpassen/Opnieuw publiceren** stap.

>[!NOTE]
>
>Als er op geen enkele manier naar de pagina wordt verwezen, wordt de **Aanpassen/Opnieuw publiceren** stap wordt overgeslagen.

>[!NOTE]
>
>De naam van een pagina wijzigen is ook afhankelijk van de instelling [Naamgevingsconventies voor pagina](#page-naming-conventions) wanneer u de nieuwe paginanaam opgeeft.

>[!NOTE]
>
>Een pagina kan alleen worden verplaatst naar een locatie waar de sjabloon waarop de pagina is gebaseerd, is toegestaan. Zie [Beschikbaarheid sjabloon](/help/implementing/developing/components/templates.md#template-availability) voor meer informatie .

#### Asynchrone handelingen {#asynchronous-actions}

Handelingen voor het verplaatsen van pagina&#39;s worden altijd asynchroon verwerkt, zodat de gebruiker de bewerkingen in de gebruikersinterface ongehinderd kan voortzetten.

* De gebruiker moet definiëren wanneer de asynchrone bewerking moet worden uitgevoerd
   * **Nu** Hiermee wordt direct begonnen met de uitvoering van de asynchrone taak.
   * **Later** Hiermee kan de gebruiker definiëren wanneer de asynchrone taak wordt gestart.

<!--
  ![Asynchronous page move](assets/asynchronous-page-move.png)
-->

De status van asynchrone taken kan worden gecontroleerd in het dialoogvenster [**Async-taakstatus** dashboard](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) om **Algemene navigatie** > **Gereedschappen** > **Bewerkingen** > **Taken**

>[!NOTE]
>
>Voor meer informatie over asynchrone baanverwerking en hoe te om de grens voor de beweging van de pagina te vormen/acties anders te noemen, zie [Asynchrone taken](/help/operations/asynchronous-jobs.md) document in de gebruikershandleiding van Verrichtingen.

### Een pagina verwijderen {#deleting-a-page}

1. Navigeer totdat u de pagina ziet die u wilt verwijderen.
1. Gebruiken [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) om de vereiste pagina te selecteren, dan gebruik **Verwijderen** op de werkbalk:

   ![Knop Verwijderen](/help/sites-cloud/authoring/assets/delete.png)

   >[!NOTE]
   >
   >Uit veiligheidsoverwegingen is het pictogram op de pagina **Verwijderen** niet beschikbaar als een snelle actie.

1. Een dialoogvenster zal om bevestiging vragen.

   ![Dialoogvenster Verwijderen](/help/sites-cloud/authoring/assets/delete-page.png)

   * **Wilt u de pagina&#39;s archiveren voordat u ze verwijdert?** - Als deze optie is ingeschakeld, worden tijdens het verwijderen versies gemaakt van de pagina&#39;s die voor verwijdering zijn geselecteerd.
      * [Versies kunnen later worden hersteld](/help/sites-cloud/authoring/features/page-versions.md).
      * Pagina&#39;s die zonder vorige versies zijn verwijderd, kunnen niet worden hersteld.
   * **Annuleren** om de handeling af te breken
   * **Verwijderen** ter bevestiging van de actie :

      * Als de pagina geen verwijzingen heeft, wordt de pagina geschrapt.
      * Als de pagina verwijzingen heeft, zal een berichtvakje u meedelen dat **Naar een of meer pagina&#39;s wordt verwezen.** U kunt **Verwijderen forceren** of **Annuleren**.

>[!NOTE]
>
>Als een pagina al is gepubliceerd, wordt deze automatisch niet gepubliceerd voordat deze wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt [Een pagina vergrendelen/ontgrendelen](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page) vanuit een console of wanneer u een afzonderlijke pagina bewerkt. Informatie over het feit of een pagina is vergrendeld, wordt ook op beide locaties weergegeven.

![Knop Vergrendelen](/help/sites-cloud/authoring/assets/lock.png)
![Knop Ontgrendelen](/help/sites-cloud/authoring/assets/unlock.png)

### Een nieuwe map maken {#creating-a-new-folder}

U kunt mappen maken waarmee u uw bestanden en pagina&#39;s kunt ordenen.

1. Open de **Sites** en navigeer naar de gewenste locatie.
1. Selecteer **Maken** van de werkbalk
1. Selecteren **Map** het dialoogvenster openen. Hier kunt u de **Naam** en **Titel**:

   ![Map maken](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Selecteren **Maken** om de map te maken.

>[!NOTE]
>
>Mappen zijn ook onderworpen aan de [Naamgevingsconventies voor pagina](#page-naming-conventions) wanneer u de nieuwe mapnaam opgeeft.

>[!CAUTION]
>
>* Mappen kunnen alleen direct onder **Sites** of onder andere mappen. Ze kunnen niet onder een pagina worden gemaakt.
>* Met de standaardhandelingen kunt u eigenschappen verplaatsen, kopiëren, plakken, verwijderen, publiceren, verwijderen en weergeven/bewerken uitvoeren op een map.
>* Mappen zijn niet beschikbaar voor selectie in een live kopie.
