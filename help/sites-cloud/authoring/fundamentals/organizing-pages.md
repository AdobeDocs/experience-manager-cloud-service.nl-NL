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

Dit document beschrijft om pagina&#39;s met de Cloud Service van Adobe Experience Manager tot stand te brengen en te beheren zodat u inhoud ](/help/sites-cloud/authoring/fundamentals/editing-content.md) op die pagina&#39;s kunt dan [ tot stand brengen.

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
>Er zijn verscheidene [ toetsenbordkortere weg ](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) die u van de Websiteconsole kunt gebruiken die het organiseren van uw pagina&#39;s efficiënter maken.

{{edge-delivery-authoring}}

## Uw website ordenen {#organizing-your-website}

Als auteur moet u uw website organiseren binnen AEM. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* U kunt deze gemakkelijk vinden in de ontwerpomgeving
* Bezoekers naar uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt [ omslagen ](#creating-a-new-folder) ook gebruiken helpen uw inhoud organiseren.

De structuur van een website kan worden beschouwd als een structuur die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titels worden getoond wanneer de paginainhoud wordt bekeken.

Het volgende toont een voorbeeld van de [ plaats van het Leerprogramma WKND ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html), waar een artikel over skateparks ( `la-skateparks`) wordt betreden:

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

Deze structuur kan van de **console van Plaatsen** worden bekeken, waar u [ door de pagina&#39;s van uw website ](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) kunt navigeren en acties op de pagina&#39;s uitvoeren. U kunt nieuwe plaatsen en [ nieuwe pagina&#39;s ](#creating-a-new-page) ook tot stand brengen.

Vanuit elk punt kunt u de vertakking naar boven zien vanuit de broodkruimels in de kopbalk:

![ Gebruikend broodkruimels ](/help/sites-cloud/authoring/assets/organizing-breadcrumbs.png)

### Naamgevingsconventies voor pagina {#page-naming-conventions}

Bij het maken van een pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:

   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.

* **[Naam](#name)**:

   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel. Zie de volgende sectie [ Beperkingen van de Naam van de Pagina en Beste praktijken ](#page-name-restrictions-and-best-practices) voor details.

#### Beperkingen en aanbevolen procedures voor paginanamen {#page-name-restrictions-and-best-practices}

De **titel** en **naam** van de pagina kunnen afzonderlijk worden gemaakt, maar zijn aan elkaar gerelateerd:

* Wanneer het creëren van een pagina, slechts wordt het **gebied van de Titel** vereist. Als geen **Naam** bij paginaverwezenlijking wordt verstrekt, zal AEM een naam van de eerste 64 karakters van de titel (het observeren van de hieronder vermelde bevestiging) produceren. Alleen de eerste 64 tekens worden gebruikt ter ondersteuning van de beste praktijken voor namen van korte pagina&#39;s.
* Als een paginanaam handmatig door de auteur wordt opgegeven, geldt de limiet van 64 tekens niet, maar kunnen andere technische beperkingen op de lengte van de paginanaam wel van toepassing zijn.

>[!TIP]
>
>Wanneer u een paginanaam definieert, is het verstandig de paginanaam zo kort maar expressief en zo gedenkwaardig mogelijk te houden, zodat de lezer deze goed begrijpt. Zie de [ W3C stijlgids ](https://www.w3.org/Provider/Style/TITLE.html) voor het `title` element voor meer informatie.
>
>Houd er ook rekening mee dat sommige browsers (bijvoorbeeld oudere versies van IE) URL&#39;s tot een bepaalde lengte alleen kunnen accepteren, dus er is ook een technische reden om paginanamen kort te houden.

Wanneer het creëren van een pagina, AEM [ bevestigt de paginanaam volgens de overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd.

De minimaal toegestane tekens zijn:

* `a` tot en met `z`
* `A` tot en met `Z`
* `0` tot en met `9`
* `_` (underscore)
* `-` (afbreekstreepje/minteken)

De volledige details van alle toegestane karakters kunnen in [ worden gevonden de noemende overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Paginanamen mogen maximaal 150 tekens bevatten.

#### Titel {#title}

Als u slechts een pagina **Titel** wanneer het creëren van een pagina verstrekt, AEM leidt de pagina **Naam** van dit koord af en [ bevestigt de naam volgens de overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd.

Het gebied van de Titel van A **** dat ongeldige karakters bevat wordt goedgekeurd, maar de afgeleide naam heeft de ongeldige karakters vervangen. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | `schoen.html` |
| SC% &amp;&#42; ç+ | `sc---c-.html` |

#### Naam {#name}

Wanneer u een pagina **Naam** wanneer het creëren van een pagina levert, AEM [ bevestigt de naam volgens de overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd. U kunt geen ongeldige karakters op het **gebied van de Naam** voorleggen. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd met een uitleg.

![ Voorbeeld van het ingaan van een ongeldige paginanaam ](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Gebruik geen code van twee letters, zoals gedefinieerd door ISO-639-1, als paginanaam, tenzij dit een hoofdtaalcode is.
>
>Zie [ Voorbereidend Inhoud voor Vertaling ](/help/sites-cloud/administering/translation/preparation.md) voor meer informatie.

### Sjablonen {#templates}

In AEM geeft een sjabloon een speciaal type pagina op. Een sjabloon wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. De malplaatjes worden samengesteld uit [ componenten ](#components).

AEM wordt geleverd met verschillende sjablonen die buiten de box zijn geplaatst. Welke sjablonen beschikbaar zijn, is afhankelijk van de afzonderlijke website. De belangrijkste velden zijn:

* **Titel**
De titel die op de resulterende webpagina wordt weergegeven.

* **Naam**
Wordt gebruikt bij de naamgeving van de pagina.

* **Malplaatje**
Een lijst met sjablonen die u kunt gebruiken bij het genereren van de nieuwe pagina.

>[!TIP]
>
>Als gevormd op uw instantie, [ malplaatjeauteurs sjablonen met de Redacteur van het Malplaatje ](/help/sites-cloud/authoring/features/templates.md) kunnen tot stand brengen.

### Onderdelen {#components}

Componenten zijn de elementen die worden verschaft door AEM, zodat u specifieke typen inhoud kunt toevoegen. AEM wordt geleverd met een reeks kant-en-klare componenten die uitgebreide functionaliteit bieden. Deze omvatten:

* Tekst
* Afbeelding
* Titel
* Carousel
* En nog veel meer

Zodra u hebt gecreeerd en een pagina geopend kunt u [ inhoud toevoegen gebruikend de componenten ](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component), die van [ componentenbrowser ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) beschikbaar zijn.

>[!TIP]
>
>De [ Console van Componenten ](/help/sites-cloud/authoring/features/components-console.md) geeft een overzicht van de componenten op uw instantie.

## Pagina&#39;s beheren {#managing-pages}

### Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s van tevoren voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Open de Sites-console (bijvoorbeeld `https://<host>:<port>/sites.html/content` .
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. Open de drop-down selecteur gebruikend **creeer** in de toolbar, dan selecteer **Pagina** van de lijst:

   ![ Creërend een pagina ](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Vanaf de eerste fase van de wizard kunt u:

   * Selecteer het malplaatje u wilt gebruiken om de nieuwe pagina tot stand te brengen, dan selecteren **daarna** te werk te gaan.

   * **annuleert** om het proces af te breken.

   ![ Selecterend een malplaatje voor een nieuwe pagina ](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Vanaf het laatste werkgebied van de wizard kunt u:

   * Gebruik de drie lusjes om de [ paginaeigenschappen ](/help/sites-cloud/authoring/fundamentals/page-properties.md) in te gaan u aan de nieuwe pagina wilt worden toegewezen, dan **creeer** om de pagina eigenlijk tot stand te brengen.

   * Het gebruik **terug** om op malplaatjeselectie terug te keren.

   Hoofdvelden zijn:

   * **Titel**:

      * Dit wordt aan de gebruiker getoond en is verplicht.

   * **Naam**:

      * Hiermee wordt de URI gegenereerd. Indien niet opgegeven, wordt de naam afgeleid van de titel.
      * Als u een pagina **Naam** wanneer het creëren van een pagina levert, AEM [ bevestigt de naam volgens de overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd.
      * U **kunt geen ongeldige karakters** op het **gebied van de Naam** voorleggen. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

   >[!TIP]
   >
   >Zie [ Pagina noemende Conventies ](#page-naming-conventions).

   De minimuminformatie die wordt vereist om een pagina tot stand te brengen is de **Titel**.

   ![ Verstrekkend paginatitel ](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Het gebruik **creeert** om het proces te voltooien en uw nieuwe pagina tot stand te brengen. De bevestigingsdialoog zal vragen of u **** de pagina onmiddellijk wilt openen of aan de console terugkeren (**Gedaan**):

   ![ de aanmaaksucces van de pagina ](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >Als u een pagina maakt met een naam die al op die locatie bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `beach` bijvoorbeeld al bestaat, wordt een nieuwe pagina `beach1` .

1. Als u terugkeert naar de console kunt u uw nieuwe pagina zien:

   ![ Resulterend nieuwe pagina ](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>Zodra een pagina is gecreeerd kan zijn malplaatje niet worden veranderd - tenzij u [ creeert een lancering met een nieuw malplaatje ](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), hoewel dit om het even welke bestaande inhoud zal verliezen.

### Een pagina openen voor bewerken {#opening-a-page-for-editing}

Nadat u een pagina hebt gemaakt of naar een bestaande pagina (in de console) hebt genavigeerd, kunt u deze openen om te bewerken:

1. Open de **console van Plaatsen**.
1. Navigeer totdat u de pagina vindt die u wilt bewerken.
1. Selecteer de pagina door een van de volgende twee methoden te gebruiken:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [ wijze van de Selectie ](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de toolbar

   En selecteer dan **uitgeven** pictogram:

   ![ geef knoop ](/help/sites-cloud/authoring/assets/edit.png) uit

1. De pagina wordt geopend en u kunt [ de pagina ](/help/sites-cloud/authoring/fundamentals/editing-content.md) zoals vereist uitgeven.

>[!NOTE]
>
>U kunt vanuit de pagina-editor alleen naar andere pagina&#39;s navigeren in de modus Voorbeeld, omdat koppelingen niet actief zijn in de modus Bewerken.

### Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

U kunt een pagina en alle subpagina&#39;s ervan naar een nieuwe locatie kopiëren:

1. In de **console van Plaatsen**, navigeer tot u de pagina vindt die u wilt kopiëren.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [ wijze van de Selectie ](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de toolbar

   En toen het **1} paginapictogram van het Exemplaar {:**

   ![ Exemplaar ](/help/sites-cloud/authoring/assets/copy.png)

1. Navigeer naar de locatie voor de nieuwe kopie van de pagina.
1. Selecteer het **pictogram van het Deeg** dat beschikbaar werd.

   ![ Deeg ](/help/sites-cloud/authoring/assets/paste.png)

1. Het dialoogvenster Plakken bevat een overzicht van de plaktransactie en de mogelijkheid om:
   * **Nieuwe Naam van de Plaats:** verander de geplakte naam van de pagina
   * **Deeg zonder Kinderen:** laat de kindpagina&#39;s van de geselecteerde pagina weg wanneer het kleven (door gebrek worden de kindpagina&#39;s gekleefd)

   ![ Deeg dialoog ](/help/sites-cloud/authoring/assets/paste-dialog.png)

1. Selecteer de **knoop van het Deeg** om de deegtransactie te bevestigen en de nieuwe pagina(s) tot stand te brengen.

>[!NOTE]
>
>Als u de pagina kopieert naar een locatie waar al een pagina met dezelfde naam als het origineel bestaat, genereert het systeem automatisch een variatie in de naam door een nummer toe te voegen. Als `beach` bijvoorbeeld al bestaat, wordt een nieuwe pagina met de naam `beach` `beach1` .

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
   * [ wijze van de Selectie ](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de toolbar

   En selecteer dan het **1} paginapictogram van de Beweging {:**

   ![ knoop van de Beweging ](/help/sites-cloud/authoring/assets/move.png)

   Hiermee opent u de wizard Verplaatsen pagina.

1. Van **anders noem** stadium van de tovenaar u één van beide kunt:

   * Specificeer de naam u de pagina wilt hebben nadat het wordt bewogen, dan selecteer **daarna** te werk te gaan.
   * **annuleert** om het proces af te breken.

   ![ beweging en anders noemen pagina ](/help/sites-cloud/authoring/assets/move-page-rename.png)

   De paginanaam kan hetzelfde blijven als u alleen de pagina verplaatst.

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `beach` bijvoorbeeld al bestaat, wordt een nieuwe pagina met de naam `beach` `beach1` .

1. Van het **Uitgezochte stadium van de Bestemming** van de tovenaar kunt u of:

   * Gebruik de [ kolommening ](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) om aan de nieuwe plaats voor de pagina te navigeren:

      * Selecteer de bestemming door de duimnagel van de bestemming te klikken.
      * Klik **daarna** om verder te gaan.

   * Het gebruik **terug** om op de specificatie van de paginanaam terug te keren.

   >[!NOTE]
   >
   >Standaard is het bovenliggende element van de pagina die u verplaatst of waarvan u de naam wijzigt, geselecteerd als het doel.

   ![ Uitgezochte paginabewegingsbestemming ](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `winter` bijvoorbeeld al bestaat, wordt `winter` wordt `winter1` .

1. Als de pagina met wordt verbonden of van verwijzingen voorzien, of gepubliceerd is, dan zijn de details vermeld in **aanpassen/** stap opnieuw publiceren.

   U kunt aangeven welke aanpassingen moeten worden aangebracht en/of opnieuw moeten worden gepubliceerd.

   >[!NOTE]
   >
   >Als er geen koppeling is naar de pagina en er niet naar wordt verwezen, is deze stap niet beschikbaar.

   ![ herpubliceer pagina op beweging ](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Het selecteren van **Beweging** zal het proces voltooien en zal/zal uw pagina zoals aangewezen bewegen anders noemen.

>[!NOTE]
>
>Als de pagina al is gepubliceerd, wordt de publicatie ervan automatisch ongedaan gemaakt wanneer u de pagina verplaatst. Door gebrek, wordt het opnieuw gepubliceerd wanneer de beweging volledig is, maar dit kan veranderen door het **te controleren** gebied op **aanpassen/** stap opnieuw publiceren.

>[!NOTE]
>
>Als de pagina niet op om het even welke manier van verwijzingen wordt voorzien, dan wordt de **Adjust/Republish** stap overgeslagen.

>[!NOTE]
>
>Het anders noemen van een pagina is ook onderworpen aan de [ Pagina noemende Conventies ](#page-naming-conventions) wanneer het specificeren van de nieuwe paginanaam.

>[!NOTE]
>
>Een pagina kan alleen worden verplaatst naar een locatie waar de sjabloon waarop de pagina is gebaseerd, is toegestaan. Zie [ Beschikbaarheid van het Malplaatje ](/help/implementing/developing/components/templates.md#template-availability) voor meer informatie.

#### Asynchrone handelingen {#asynchronous-actions}

Handelingen voor het verplaatsen van pagina&#39;s worden altijd asynchroon verwerkt, zodat de gebruiker de bewerkingen in de gebruikersinterface ongehinderd kan voortzetten.

* De gebruiker moet definiëren wanneer de asynchrone bewerking moet worden uitgevoerd
   * **** begint nu de uitvoering van de asynchrone baan onmiddellijk.
   * **later** staat de gebruiker toe om te bepalen wanneer de asynchrone baan zal beginnen.

<!--
  ![Asynchronous page move](assets/asynchronous-page-move.png)
-->

Het statuut van asynchrone banen kan in het **dashboard van de Banen van 0} Async ](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) bij** Globale Navigatie **worden gecontroleerd >** Hulpmiddelen **>** Verrichtingen **>** Banen **[**

>[!NOTE]
>
>Voor meer informatie over asynchrone baanverwerking en hoe te om de grens voor paginabeweging te vormen/acties anders te noemen, zie [ Asynchrone Jobs ](/help/operations/asynchronous-jobs.md) document in de de gebruikersgids van Verrichtingen.

### Een pagina verwijderen {#deleting-a-page}

1. Navigeer totdat u de pagina ziet die u wilt verwijderen.
1. Gebruik [ selectiemodus ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) om de vereiste pagina te selecteren, dan gebruik **Schrapping** van de toolbar:

   ![ knoop van de Schrapping ](/help/sites-cloud/authoring/assets/delete.png)

   >[!NOTE]
   >
   >Uit veiligheidsoverwegingen is het pictogram op de pagina **Verwijderen** niet beschikbaar als een snelle actie.

1. Een dialoogvenster zal om bevestiging vragen.

   ![ Schrapping dialoog ](/help/sites-cloud/authoring/assets/delete-page.png)

   * **wilt u pagina&#39;s vóór schrapping archiveren?** - Als deze optie is ingeschakeld, worden bij het verwijderen versies gemaakt van de pagina&#39;s die zijn geselecteerd om te worden verwijderd.
      * [ de Versies kunnen op een recentere datum ](/help/sites-cloud/authoring/features/page-versions.md) worden hersteld.
      * Pagina&#39;s die zonder vorige versies zijn verwijderd, kunnen niet worden hersteld.
   * **annuleert** om de actie af te breken
   * **Schrapping** om de actie te bevestigen:

      * Als de pagina geen verwijzingen heeft, wordt de pagina geschrapt.
      * Als de pagina verwijzingen heeft, zal een berichtvakje u meedelen dat **Één of meerdere pagina&#39;s van verwijzingen worden voorzien.** u kunt **Schrapping** selecteren of **annuleren**.

>[!NOTE]
>
>Als een pagina al is gepubliceerd, wordt deze automatisch niet gepubliceerd voordat deze wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt [ vergrendelen/ontgrendelen een pagina ](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page) van of een console of wanneer het uitgeven van een individuele pagina. Informatie over het feit of een pagina is vergrendeld, wordt ook op beide locaties weergegeven.

![ knoop van het Slot ](/help/sites-cloud/authoring/assets/lock.png)
![ Ontgrendelingsknop ](/help/sites-cloud/authoring/assets/unlock.png)

### Een nieuwe map maken {#creating-a-new-folder}

U kunt mappen maken waarmee u uw bestanden en pagina&#39;s kunt ordenen.

1. Open de **console van Plaatsen** en navigeer aan de vereiste plaats.
1. Om de optielijst te openen, creeer **** van de toolbar
1. Selecteer **Omslag** om de dialoog te openen. Hier kunt u de **Naam** ingaan en **Titel**:

   ![ creeer omslag ](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Selecteer **creeer** om de omslag tot stand te brengen.

>[!NOTE]
>
>De omslagen zijn ook onderworpen aan de [ Pagina noemende Conventies ](#page-naming-conventions) wanneer het specificeren van de nieuwe omslagnaam.

>[!CAUTION]
>
>* De omslagen kunnen slechts direct onder **Plaatsen** of onder andere omslagen worden gecreeerd. Ze kunnen niet onder een pagina worden gemaakt.
>* Met de standaardhandelingen kunt u eigenschappen verplaatsen, kopiëren, plakken, verwijderen, publiceren, verwijderen en weergeven/bewerken uitvoeren op een map.
>* Mappen zijn niet beschikbaar voor selectie in een live kopie.
