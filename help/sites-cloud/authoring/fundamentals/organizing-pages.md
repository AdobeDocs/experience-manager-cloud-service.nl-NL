---
title: Pagina's maken en indelen
description: Pagina's maken en ordenen met AEM
translation-type: tm+mt
source-git-commit: 86fa0de81e8398b5b74291840304a2254d1771f4

---


# Pagina&#39;s maken en indelen {#creating-and-organizing-pages}

In dit document wordt beschreven hoe u pagina&#39;s kunt maken en beheren met Adobe Experience Manager Cloud Service, zodat u vervolgens inhoud [op deze pagina&#39;s kunt](/help/sites-cloud/authoring/fundamentals/editing-content.md) maken.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten nodig] en machtigingen om actie te ondernemen op pagina&#39;s zoals maken, kopiëren, verplaatsen, bewerken en verwijderen.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to take action on pages such as create, copy, move, edit, and delete.
-->

>[!TIP]
>
>Er zijn een aantal [sneltoetsen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) die u vanuit de websiteconsole kunt gebruiken om uw pagina&#39;s efficiënter te ordenen.

## Uw website ordenen {#organizing-your-website}

Als auteur moet u uw website organiseren binnen AEM. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* U kunt deze gemakkelijk vinden in de ontwerpomgeving
* Bezoekers naar uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt ook [mappen](#creating-a-new-folder) gebruiken om uw inhoud te ordenen.

De structuur van een website kan worden beschouwd als een structuur die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titels worden getoond wanneer de paginainhoud wordt bekeken.

In het volgende voorbeeld ziet u een voorbeeld van de [WKND-zelfstudie](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) , waar een artikel over skateparks ( `la-skateparks`) wordt geopend:

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

Deze structuur kan worden weergegeven vanuit de **Sites** -console, waar u door de pagina&#39;s van uw website [kunt](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) navigeren en acties op de pagina&#39;s kunt uitvoeren. U kunt ook nieuwe sites en [nieuwe pagina&#39;s](#creating-a-new-page)maken.

Vanuit elk punt kunt u de vertakking naar boven zien vanuit de broodkruimels in de kopbalk:

![Door broodkruimels te navigeren](/help/sites-cloud/authoring/assets/organizing-breadcrumbs.png)

### Naamgevingsconventies voor pagina&#39;s {#page-naming-conventions}

Bij het maken van een nieuwe pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:

   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.

* **[Naam](#name)**:

   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel. Zie de volgende sectie Beperkingen van de Naam van de [Pagina en Beste praktijken](#page-name-restrictions-and-best-practices) voor details.

#### Beperkingen en aanbevolen procedures voor paginanamen {#page-name-restrictions-and-best-practices}

De **titel** en **naam** van de pagina kunnen afzonderlijk worden gemaakt, maar zijn aan elkaar gerelateerd:

* Wanneer u een pagina maakt, is alleen het veld **Titel** vereist. Als er bij het maken van de pagina geen **naam** is opgegeven, genereert AEM een naam uit de eerste 64 tekens van de titel (met inachtneming van de onderstaande validatie). Alleen de eerste 64 tekens worden gebruikt ter ondersteuning van de beste praktijken voor namen van korte pagina&#39;s.
* Als een paginanaam handmatig door de auteur wordt opgegeven, geldt de limiet van 64 tekens niet, maar kunnen andere technische beperkingen op de lengte van de paginanaam wel van toepassing zijn.

>[!TIP]
>
>Wanneer u een paginanaam definieert, is het verstandig de paginanaam zo kort maar expressief en zo gedenkwaardig mogelijk te houden, zodat de lezer deze goed begrijpt. Zie de [W3C-stijlhandleiding](https://www.w3.org/Provider/Style/TITLE.html) voor het `title` element voor meer informatie.
>
>Houd er ook rekening mee dat sommige browsers (bijvoorbeeld oudere versies van IE) URL&#39;s tot een bepaalde lengte alleen kunnen accepteren, dus er is ook een technische reden om paginanamen kort te houden.

Bij het maken van een nieuwe pagina valideert AEM de paginanaam volgens de conventies die door AEM en het JCR worden opgelegd. <!--When creating a new page, AEM will [validate the page name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and the JCR.-->

De minimaal toegestane tekens zijn:

* `a` doorheen `z`
* `A` doorheen `Z`
* `0` doorheen `9`
* `_` (onderstrepingsteken)
* `-` (afbreekstreepje/minteken)

Alle toegestane tekens worden in de naamgevingsconventies weergegeven. <!--Full details of all characters allowed can be found in [the naming conventions](/help/sites-developing/naming-conventions.md).-->

>[!NOTE]
>
>Paginanamen mogen maximaal 150 tekens bevatten.

#### Titel {#title}

Als u bij het maken van een nieuwe pagina alleen een **paginatitel** opgeeft, leidt AEM de **naam** van de pagina af van deze tekenreeks en valideert het de naam volgens de conventies die door AEM en JCR worden opgelegd. <!--If you supply only a page **Title** when creating a new page, AEM will derive the page **Name** from this string and [validate the name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and JCR.-->

Een veld **Titel** met ongeldige tekens wordt geaccepteerd, maar de ongeldige tekens worden vervangen door de afgeleide naam. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;*ç+ | `sc---c-.html` |

#### Naam {#name}

Wanneer u een **paginanaam** opgeeft wanneer u een nieuwe pagina maakt, valideert AEM de naam volgens de conventies die door AEM en JCR worden opgelegd. U kunt geen ongeldige tekens verzenden in het veld **Naam** . Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd. <!--When you supply a page **Name** when creating a new page, AEM will [validate the name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and JCR. You cannot submit invalid characters in the **Name** field. When AEM detects invalid characters the field will be highlighted with an explanatory message.-->

![Voorbeeld van het invoeren van een ongeldige paginanaam](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Gebruik geen code van twee letters, zoals gedefinieerd door ISO-639-1, als paginanaam, tenzij dit een hoofdtaalcode is.
>
>Zie Inhoud voorbereiden voor vertaling voor meer informatie.
<!--
>See [Preparing Content for Translation](/help/sites-administering/tc-prep.md) for more information.
-->

### Sjablonen {#templates}

In AEM, specificeert een malplaatje een gespecialiseerd type van pagina. Een sjabloon wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. Sjablonen bestaan uit [componenten](#components).

AEM wordt geleverd met verschillende sjablonen die u kunt vinden. Welke sjablonen beschikbaar zijn, is afhankelijk van de afzonderlijke website. De belangrijkste velden zijn:

* **Titel** De titel die op de resulterende webpagina wordt weergegeven.

* **Naam** die wordt gebruikt bij de naamgeving van de pagina.

* **Template** A lijst van malplaatjes beschikbaar voor gebruik wanneer het produceren van de nieuwe pagina.

>[!TIP]
>
>Als dit op uw exemplaar is geconfigureerd, kunnen [sjabloonauteurs sjablonen maken met de Sjablooneditor](/help/sites-cloud/authoring/features/templates.md).

### Onderdelen {#components}

Componenten zijn de elementen die door AEM worden geleverd, zodat u specifieke typen inhoud kunt toevoegen. AEM wordt geleverd met een reeks kant-en-klare componenten die uitgebreide functionaliteit bieden. Deze omvatten:

* Tekst
* Afbeelding
* Titel
* Carousel
* En nog veel meer

Nadat u een pagina hebt gemaakt en geopend, kunt u inhoud [toevoegen met de componenten](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component)die beschikbaar zijn in de [deelbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

>[!TIP]
>
>De [componentenconsole](/help/sites-cloud/authoring/features/components-console.md) geeft een overzicht van de componenten op uw instantie.

## Pagina&#39;s beheren {#managing-pages}

### Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s van tevoren voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Open de Sites-console (bijvoorbeeld `https://<host>:<port>/sites.html/content`.
1. Navigeer naar de locatie waar u de nieuwe pagina wilt maken.
1. Open de vervolgkeuzelijst met **Maken** op de werkbalk en selecteer vervolgens **Pagina** in de lijst:

   ![Een pagina maken](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Vanaf de eerste fase van de wizard kunt u:

   * Selecteer de sjabloon die u wilt gebruiken om de nieuwe pagina te maken en klik op **Volgende** of tik op Volgende om door te gaan.

   * **Annuleer** om het proces af te breken.
   ![Een sjabloon voor een nieuwe pagina selecteren](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Vanaf het laatste werkgebied van de wizard kunt u:

   * Gebruik de drie tabbladen om de [pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) in te voeren die u aan de nieuwe pagina wilt toewijzen. Klik vervolgens op **Maken** of tik op Maken om de pagina daadwerkelijk te maken.

   * Gebruik **Vorige** om terug te keren naar de sjabloonselectie.
   Hoofdvelden zijn:

   * **Titel**:

      * Dit wordt aan de gebruiker getoond en is verplicht.
   * **Naam**:

      * Hiermee wordt de URI gegenereerd. Indien niet opgegeven, wordt de naam afgeleid van de titel.
      * Als u bij het maken van een nieuwe pagina een **paginanaam** opgeeft, valideert AEM de naam volgens de conventies die door AEM en JCR worden opgelegd. <!--If you supply a page **Name** when creating a new page, AEM will [validate the name according to the conventions](/help/sites-developing/naming-conventions.md) imposed by AEM and JCR.-->
      * U **kunt geen ongeldige tekens** verzenden in het veld **Naam** . Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.
   >[!TIP]
   >
   >Zie conventies voor [paginanamen](#page-naming-conventions).

   De minimale informatie die nodig is om een nieuwe pagina te maken, is de **titel**.

   ![Paginatitel opgeven](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Gebruik **Maken** om het proces te voltooien en uw nieuwe pagina te maken. In het bevestigingsvenster wordt gevraagd of u de pagina direct wilt **openen** of wilt terugkeren naar de console (**Gereed**):

   ![Maken van pagina voltooid](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >Als u een pagina maakt met een naam die al op die locatie bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als er bijvoorbeeld `beach` al een nieuwe pagina bestaat, wordt deze `beach1`.

1. Als u terugkeert naar de console, zult u uw nieuwe pagina zien:

   ![Resulterende nieuwe pagina](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>Als een pagina eenmaal is gemaakt, kan de sjabloon ervan niet worden gewijzigd, tenzij u een [startpagina met een nieuwe sjabloon](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template)maakt, maar de bestaande inhoud verdwijnt.

### Een pagina openen voor bewerken {#opening-a-page-for-editing}

Nadat u een pagina hebt gemaakt of naar een bestaande pagina (in de console) hebt genavigeerd, kunt u deze openen om te bewerken:

1. Open de **Sites** -console.
1. Navigeer totdat u de pagina vindt die u wilt bewerken.
1. Selecteer de pagina door een van de volgende twee handelingen uit te voeren:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de werkbalk
   Selecteer vervolgens het pictogram **Bewerken** :

   ![Bewerken, knop](/help/sites-cloud/authoring/assets/edit.png)

1. De pagina wordt geopend en u kunt de pagina [naar wens](/help/sites-cloud/authoring/fundamentals/editing-content.md) bewerken.

>[!NOTE]
>
>U kunt vanuit de pagina-editor alleen naar andere pagina&#39;s navigeren in de modus Voorbeeld, omdat koppelingen niet actief zijn in de modus Bewerken.

### Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

U kunt een pagina en alle subpagina&#39;s ervan naar een nieuwe locatie kopiëren:

1. Navigeer in de **Sites** -console naar de pagina die u wilt kopiëren.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de werkbalk
   En dan het paginapictogram **Kopiëren** :

   ![Kopiëren](/help/sites-cloud/authoring/assets/copy.png)

   >[!NOTE]
   >
   >Als u in de selectiemodus werkt, wordt dit automatisch verlaten zodra de pagina wordt gekopieerd.

1. Navigeer naar de locatie voor de nieuwe kopie van de pagina.
1. Het pictogram **Plakken** is rechtstreeks naar rechts beschikbaar met een vervolgkeuzepijl:

   ![Plakken](/help/sites-cloud/authoring/assets/paste.png)

   U kunt:

   1. Selecteer het paginapictogram **Plakken** zelf: Op deze locatie worden een kopie van de originele pagina en eventuele onderliggende pagina&#39;s gemaakt.
   1. Selecteer de vervolgkeuzepijl om de optie **Plakken zonder onderliggende items** weer te geven. Op deze locatie wordt een kopie van de originele pagina gemaakt. onderliggende pagina&#39;s worden niet gekopieerd.
   >[!NOTE]
   >
   >Als u de pagina kopieert naar een locatie waar al een pagina met dezelfde naam als het origineel bestaat, genereert het systeem automatisch een variatie in de naam door een nummer toe te voegen. Als er bijvoorbeeld `beach` al een nieuwe pagina met deze naam bestaat, `beach` wordt deze gewijzigd `beach1`.

### Een pagina verplaatsen of de naam ervan wijzigen {#moving-or-renaming-a-page}

De procedure om een pagina te verplaatsen of anders te noemen is in wezen het zelfde en door de zelfde tovenaar behandeld. Met deze wizard kunt u:

* De naam van een pagina wijzigen zonder deze te verplaatsen
* De pagina verplaatsen zonder de naam ervan te wijzigen
* Tegelijkertijd verplaatsen en hernoemen

AEM biedt u de functionaliteit om interne koppelingen bij te werken die verwijzen naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

1. Navigeer totdat u de pagina vindt die u wilt verplaatsen.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) en de werkbalk
   Selecteer vervolgens het paginapictogram **Verplaatsen** :

   ![Knop Verplaatsen](/help/sites-cloud/authoring/assets/move.png)

   Hiermee wordt de wizard Verplaatsen van de pagina geopend.

1. In het werkgebied **Naam wijzigen** van de wizard kunt u:

   * Geef de naam op die de pagina moet hebben nadat deze is verplaatst en klik op **Volgende** of tik op Volgende om door te gaan.
   * **Annuleer** om het proces af te breken.
   ![Pagina verplaatsen en hernoemen](/help/sites-cloud/authoring/assets/move-page-rename.png)

   De paginanaam kan hetzelfde blijven als u alleen de pagina verplaatst.

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als er bijvoorbeeld `beach` al een nieuwe pagina met deze naam bestaat, `beach` wordt deze gewijzigd `beach1`.

1. Van het **Uitgezochte stadium van de Bestemming** van de tovenaar kunt u of:

   * Met de [kolomweergave](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) navigeert u naar de nieuwe locatie voor de pagina:

      * Selecteer de bestemming door de duimnagel van de bestemming te klikken.
      * Klik op **Volgende** om door te gaan.
   * Gebruik **Vorige** om terug te keren naar de specificatie van de paginanaam.
   >[!NOTE]
   >
   >Standaard wordt het bovenliggende element van de pagina waarvan u de naam verplaatst of wijzigt, geselecteerd als het doel.

   ![Doel pagina verplaatsen selecteren](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Bijvoorbeeld als `winter` reeds bestaat `winter` zal worden `winter1`.

1. Als de pagina is gekoppeld aan of waarnaar wordt verwezen, of is gepubliceerd, worden de details weergegeven in de stap **Aanpassen/Opnieuw** publiceren.

   U kunt aangeven welke aanpassingen moeten worden aangebracht en/of opnieuw moeten worden gepubliceerd.

   >[!NOTE]
   >
   >Als er geen koppeling is naar de pagina en er niet naar wordt verwezen, is deze stap niet beschikbaar.

   ![Pagina verplaatsen opnieuw publiceren](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Als u **Verplaatsen** selecteert, wordt het proces voltooid en wordt de pagina waar nodig verplaatst of hernoemd.

>[!NOTE]
>
>Als de pagina al is gepubliceerd, wordt de publicatie ervan automatisch ongedaan gemaakt wanneer u de pagina verplaatst. Deze wordt standaard opnieuw gepubliceerd wanneer de verplaatsing is voltooid, maar u kunt dit veranderen door het veld **Opnieuw publiceren** uit te schakelen in de stap **Aanpassen/opnieuw publiceren**.

>[!NOTE]
>
>Als er op geen enkele manier naar de pagina wordt verwezen, wordt de stap **Aanpassen/Opnieuw** publiceren overgeslagen.

>[!NOTE]
>
>Als u de naam van een pagina wijzigt, gelden de naamgevingsconventies [voor de](#page-naming-conventions) pagina ook voor het opgeven van de nieuwe paginanaam.

>[!NOTE]
>
>Een pagina kan alleen worden verplaatst naar een locatie waar de sjabloon waarop de pagina is gebaseerd, is toegestaan. Zie Sjabloonbeschikbaarheid voor meer informatie.
<!--
>A page can only be moved to a location where the template upon which the page is based is allowed. See [Template Availability](/help/sites-developing/templates.md#template-availability) for more information.
-->

### Een pagina verwijderen {#deleting-a-page}

1. Navigeer totdat u de pagina ziet die u wilt verwijderen.
1. Selecteer de gewenste pagina in de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) en gebruik vervolgens **Verwijderen** op de werkbalk:

   ![Knop Verwijderen](/help/sites-cloud/authoring/assets/delete.png)

   >[!NOTE]
   >
   >Uit veiligheidsoverwegingen is het pictogram op de pagina **Verwijderen** niet beschikbaar als een snelle actie.

1. Een dialoogvenster zal om bevestiging vragen.

   ![Dialoogvenster Verwijderen](/help/sites-cloud/authoring/assets/delete-page.png)

   * **Wilt u de pagina&#39;s archiveren voordat u ze verwijdert?** - Als deze optie is ingeschakeld, worden bij het verwijderen versies gemaakt van de pagina&#39;s die voor verwijdering zijn geselecteerd.
      * [Versies kunnen later worden hersteld.](/help/sites-cloud/authoring/features/page-versions.md)
      * Pagina&#39;s die zonder vorige versies zijn verwijderd, kunnen niet worden hersteld.
   * **Annuleren** om de handeling af te breken
   * **Verwijder** om de handeling te bevestigen:

      * Als de pagina geen verwijzingen bevat, wordt de pagina verwijderd.
      * Als de pagina verwijzingen heeft, zal een berichtvakje u meedelen dat **Één of meerdere pagina&#39;s van verwijzingen worden voorzien.** U kunt Verwijderen **forceren** of **Annuleren** selecteren.

>[!NOTE]
>
>Als een pagina al is gepubliceerd, wordt deze automatisch niet gepubliceerd voordat deze wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt een pagina [](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page) vergrendelen/ontgrendelen vanuit een console of wanneer u een afzonderlijke pagina bewerkt. Informatie over het feit of een pagina is vergrendeld, wordt ook op beide locaties weergegeven.

![Knop](/help/sites-cloud/authoring/assets/lock.png)![Ontgrendelen](/help/sites-cloud/authoring/assets/unlock.png)

### Nieuwe map maken {#creating-a-new-folder}

U kunt mappen maken waarmee u uw bestanden en pagina&#39;s kunt ordenen.

1. Open the **Sites** console and navigate to the required location.
1. Selecteer **Maken** in de werkbalk om de lijst met opties te openen
1. Selecteer **Map** om het dialoogvenster te openen. Hier kunt u de **naam** en de **titel** invoeren:

   ![Map maken](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Selecteer **Maken** om de map te maken.

>[!NOTE]
>
>Mappen zijn ook onderworpen aan de conventies voor [paginanamen](#page-naming-conventions) wanneer u de nieuwe mapnaam opgeeft.

>[!CAUTION]
>
>* Mappen kunnen alleen rechtstreeks onder **Sites** of onder andere mappen worden gemaakt. Ze kunnen niet onder een pagina worden gemaakt.
>* Met de standaardhandelingen kunt u eigenschappen verplaatsen, kopiëren, plakken, verwijderen, publiceren, verwijderen en weergeven/bewerken uitvoeren op een map.
>* Mappen zijn niet beschikbaar voor selectie in een live kopie.

