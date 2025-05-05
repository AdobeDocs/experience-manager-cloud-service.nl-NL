---
title: Pagina's beheren
description: Leer hoe u de pagina's van uw website beheert in AEM, zoals verplaatsen, kopiëren en verwijderen.
exl-id: 355b60c5-a82e-4bbb-98ea-bfcc0126b7fd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# Pagina&#39;s beheren {#managing-pages}

Leer hoe u de pagina&#39;s van uw website beheert in AEM, zoals verplaatsen, kopiëren en verwijderen.

>[!TIP]
>
>Alvorens u begint uw pagina&#39;s te beheren, wordt vertrouwd met [ hoe uw pagina&#39;s in AEM ](/help/sites-cloud/authoring/sites-console/organizing-pages.md) worden georganiseerd.

>[!TIP]
>
>Er zijn verscheidene [ toetsenbordkortere weg ](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) die u van de Websiteconsole kunt gebruiken die het organiseren van uw pagina&#39;s efficiënter maken.

## Toegangsrechten {#access-privileges}

Uw account heeft de juiste toegangsrechten en machtigingen nodig om op pagina&#39;s te kunnen werken, zoals maken, kopiëren, verplaatsen, bewerken en verwijderen.

Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

## Een pagina openen voor bewerken {#opening-a-page-for-editing}

Na [ creërend een pagina ](/help/sites-cloud/authoring/sites-console/creating-pages.md) of het navigeren aan een bestaande pagina gebruikend [ de **console van Plaatsen** ](/help/sites-cloud/authoring/sites-console/introduction.md), kunt u het voor het uitgeven openen.

1. Open [ de **2&rbrace; console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md).**
1. Navigeer naar de pagina die u wilt bewerken.
1. Selecteer de pagina door een van de volgende twee methoden te gebruiken:

   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [ wijze van de Selectie ](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) en de toolbar

1. Tik of klik **uitgeven** pictogram.

   ![ geef knoop ](/help/sites-cloud/authoring/assets/edit.png) uit

1. De pagina wordt geopend en u kunt de pagina naar wens bewerken. Afhankelijk van hoe de geselecteerde pagina werd gecreeerd, **geeft** actie uit zal de aangewezen redacteur openen.
   * [ Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/introduction.md) - voor pagina&#39;s die met de Redacteur van de Pagina van de AEM worden gecreeerd
   * [ Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) - voor pagina&#39;s die met de Universele Redacteur worden gecreeerd

## Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

U kunt een pagina en alle subpagina&#39;s ervan naar een nieuwe locatie kopiëren:

1. Open [ de **2&rbrace; console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md).**
1. Navigeer naar de pagina die u wilt kopiëren.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [ wijze van de Selectie ](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) en de toolbar

1. Tik of klik het **1&rbrace; paginapictogram van het Exemplaar &lbrace;.**

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

## Een pagina verplaatsen of de naam ervan wijzigen {#moving-or-renaming-a-page}

De procedure voor het verplaatsen of wijzigen van de naam van een pagina is in feite hetzelfde en beide handelingen worden verwerkt door de wizard Pagina verplaatsen. Met deze wizard kunt u:

* Wijzig de naam van een pagina zonder deze te verplaatsen.
* Verplaats de pagina zonder de naam ervan te wijzigen.
* Tegelijkertijd verplaatsen en hernoemen.

AEM biedt u de functionaliteit om interne koppelingen bij te werken die verwijzen naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

1. Open [ de **2&rbrace; console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md).**
1. Navigeer naar de pagina die u wilt verplaatsen.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [ wijze van de Selectie ](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) en de toolbar

1. Tik of klik het **1&rbrace; paginapictogram van de Beweging &lbrace;om de tovenaar van de bewegingspagina te openen.**

   ![ knoop van de Beweging ](/help/sites-cloud/authoring/assets/move.png)

1. Van **noem** stap van de tovenaar anders u één van beide kunt:

   * Specificeer de naam u de pagina wilt hebben nadat het wordt bewogen, dan selecteer **daarna** te werk te gaan.
   * **annuleert** om het proces af te breken.

   ![ beweging en anders noemen pagina ](/help/sites-cloud/authoring/assets/move-page-rename.png)

   * De paginanaam kan hetzelfde blijven als u alleen de pagina verplaatst.

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `beach` bijvoorbeeld al bestaat, wordt een nieuwe pagina met de naam `beach` `beach1` .

1. Van de **Uitgezochte Stap van de Bestemming** van de tovenaar kunt u of:

   * Gebruik de [ kolommening ](/help/sites-cloud/authoring/basic-handling.md#column-view) om aan de nieuwe plaats voor de pagina te navigeren:

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

   * U kunt aangeven welke aanpassingen moeten worden aangebracht en/of opnieuw moeten worden gepubliceerd.

   >[!NOTE]
   >
   >Als er geen koppeling is naar de pagina en er niet naar wordt verwezen, is deze stap niet beschikbaar.

   ![ herpubliceer pagina op beweging ](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Tik of klik **Beweging** om te bepalen wanneer de bewegingsactie zou moeten voorkomen.

   * **nu** zal een [ asynchrone baan ](#asynchronous-actions) teweegbrengen om de pagina onmiddellijk te bewegen.
   * **later** zal u toestaan om een datum voor de beweging te plannen om worden verwerkt.

   ![ het bepalen wanneer zich ](assets/managing-pages-move-page-now-later.png) te bewegen

1. Tik of klik **ga** verder om de paginabeweging te voltooien.

>[!NOTE]
>
>Als de pagina al is gepubliceerd, wordt de publicatie ervan automatisch ongedaan gemaakt wanneer u de pagina verplaatst. Door gebrek, wordt het opnieuw gepubliceerd wanneer de beweging volledig is, maar dit kan veranderen door het **te controleren** gebied op **aanpassen/** stap opnieuw publiceren.

>[!NOTE]
>
>Het anders noemen van een pagina is ook onderworpen aan de [ Pagina noemende Conventies ](#page-naming-conventions) wanneer het specificeren van de nieuwe paginanaam.

>[!NOTE]
>
>Een pagina kan alleen worden verplaatst naar een locatie waar de sjabloon waarop de pagina is gebaseerd, is toegestaan. Zie [ Beschikbaarheid van het Malplaatje ](/help/implementing/developing/components/templates.md#template-availability) voor meer informatie.

### Asynchrone handelingen {#asynchronous-actions}

Handelingen voor het verplaatsen van pagina&#39;s worden altijd asynchroon verwerkt, zodat de gebruiker de bewerkingen in de gebruikersinterface ongehinderd kan voortzetten.

Het statuut van asynchrone banen kan in het **dashboard van de Banen van 0&rbrace; Async [&#128279;](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) bij** Globale Navigatie **worden gecontroleerd >** Hulpmiddelen **>** Verrichtingen **>** Banen **&#x200B;**

>[!TIP]
>
>Voor meer informatie over asynchrone baanverwerking en hoe te om de grens voor paginabeweging te vormen/acties anders te noemen, zie [ Asynchrone Jobs ](/help/operations/asynchronous-jobs.md) document in de de gebruikersgids van Verrichtingen.

### Een pagina verwijderen {#deleting-a-page}

1. Open [ de **2&rbrace; console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md).**
1. Navigeer naar de pagina die u wilt verwijderen.
1. Gebruik [ selectiemodus ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) om de vereiste pagina te selecteren, dan gebruik **Schrapping** van de toolbar:

   ![ knoop van de Schrapping ](/help/sites-cloud/authoring/assets/delete.png)

1. Een dialoogvenster zal om bevestiging vragen.

   ![ Schrapping dialoog ](/help/sites-cloud/authoring/assets/delete-page.png)

   * **wilt u pagina&#39;s vóór schrapping archiveren?** - Als deze optie is ingeschakeld, worden bij het verwijderen versies gemaakt van de pagina&#39;s die zijn geselecteerd om te worden verwijderd.
      * [ de Versies kunnen op een recentere datum ](/help/sites-cloud/authoring/sites-console/page-versions.md) worden hersteld.
      * Pagina&#39;s die zonder vorige versies zijn verwijderd, kunnen niet worden hersteld.
1. Tik of klik **annuleer** om de actie of **Schrapping** af te breken om de actie te bevestigen.
   * Als de pagina geen verwijzingen heeft, wordt de pagina geschrapt.
   * Als de pagina verwijzingen heeft, zal een berichtvakje u meedelen dat **Één of meerdere pagina&#39;s van verwijzingen worden voorzien.** u kunt **Schrapping** selecteren of **annuleren**.

>[!NOTE]
>
>Als een pagina al is gepubliceerd, wordt deze automatisch niet gepubliceerd voordat deze wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt [ vergrendelen/ontgrendelen een pagina ](/help/sites-cloud/authoring/page-editor/edit-content.md#locking-a-page) van of een console of wanneer het uitgeven van een individuele pagina. Informatie over het feit of een pagina is vergrendeld, wordt ook op beide locaties weergegeven.

![ knoop van het Slot ](/help/sites-cloud/authoring/assets/lock.png)
![ Ontgrendelingsknop ](/help/sites-cloud/authoring/assets/unlock.png)

### Een nieuwe map maken {#creating-a-new-folder}

U kunt mappen maken waarmee u uw bestanden en pagina&#39;s kunt ordenen.

1. Open [ de **2&rbrace; console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md).**
1. Navigeer naar de gewenste locatie.
1. Om de optielijst te openen, creeer **&#x200B;**&#x200B;van de toolbar
1. Selecteer **Omslag** om de dialoog te openen. Hier kunt u de **Naam** ingaan en **Titel**:

   ![ creeer omslag ](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Selecteer **creeer** om de omslag tot stand te brengen.

>[!NOTE]
>
>* De omslagen zijn ook onderworpen aan de [ Pagina noemende Conventies ](#page-naming-conventions) wanneer het specificeren van de nieuwe omslagnaam.
>* De omslagen kunnen slechts direct onder **Plaatsen** of onder andere omslagen worden gecreeerd. Ze kunnen niet onder een pagina worden gemaakt.
>* Met de standaardhandelingen kunt u eigenschappen verplaatsen, kopiëren, plakken, verwijderen, publiceren, verwijderen en weergeven/bewerken uitvoeren op een map.
>* Mappen zijn niet beschikbaar voor selectie in een live kopie.
