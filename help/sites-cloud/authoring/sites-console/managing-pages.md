---
title: Pagina's beheren
description: Leer hoe u de pagina's van uw website beheert in AEM, zoals verplaatsen, kopiëren en verwijderen.
exl-id: 355b60c5-a82e-4bbb-98ea-bfcc0126b7fd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# Pagina&#39;s beheren {#managing-pages}

Leer hoe u de pagina&#39;s van uw website beheert in AEM, zoals verplaatsen, kopiëren en verwijderen.

>[!TIP]
>
>Voordat u begint met het beheren van uw pagina&#39;s, dient u vertrouwd te raken met [hoe uw pagina&#39;s in AEM worden ingedeeld.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

>[!TIP]
>
>Er zijn verschillende [sneltoetsen](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) die u kunt gebruiken vanuit de websiteconsole om uw pagina&#39;s efficiënter te ordenen.

## Toegangsrechten {#access-privileges}

Uw account heeft de juiste toegangsrechten en machtigingen nodig om op pagina&#39;s te kunnen werken, zoals maken, kopiëren, verplaatsen, bewerken en verwijderen.

Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

## Een pagina openen voor bewerken {#opening-a-page-for-editing}

Na [een pagina maken](/help/sites-cloud/authoring/sites-console/creating-pages.md) of naar een bestaande pagina navigeren met [de **Sites** console,](/help/sites-cloud/authoring/sites-console/introduction.md) u kunt het openen om te bewerken.

1. Openen [de **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigeer naar de pagina die u wilt bewerken.
1. Selecteer de pagina door een van de volgende twee methoden te gebruiken:

   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) en de werkbalk

1. Tik of klik op de knop **Bewerken** pictogram.

   ![Bewerken, knop](/help/sites-cloud/authoring/assets/edit.png)

1. De pagina wordt geopend en u kunt de pagina naar wens bewerken. Afhankelijk van de manier waarop de geselecteerde pagina is gemaakt, wordt **Bewerken** de actie zal de aangewezen redacteur openen.
   * [Pagina-editor](/help/sites-cloud/authoring/page-editor/introduction.md) - Voor pagina&#39;s die zijn gemaakt met de AEM Pagina-editor
   * [Universele editor](/help/sites-cloud/authoring/universal-editor/authoring.md) - Voor pagina&#39;s die zijn gemaakt met de Universal Editor

## Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

U kunt een pagina en alle subpagina&#39;s ervan naar een nieuwe locatie kopiëren:

1. Openen [de **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigeer naar de pagina die u wilt kopiëren.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) en de werkbalk

1. Tik of klik op de knop **Kopiëren** paginapictogram

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

## Een pagina verplaatsen of de naam ervan wijzigen {#moving-or-renaming-a-page}

De procedure voor het verplaatsen of wijzigen van de naam van een pagina is in feite hetzelfde en beide handelingen worden verwerkt door de wizard Pagina verplaatsen. Met deze wizard kunt u:

* Wijzig de naam van een pagina zonder deze te verplaatsen.
* Verplaats de pagina zonder de naam ervan te wijzigen.
* Tegelijkertijd verplaatsen en hernoemen.

AEM biedt u de functionaliteit om interne koppelingen bij te werken die verwijzen naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

1. Openen [de **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigeer naar de pagina die u wilt verplaatsen.
1. Selecteer de pagina met behulp van:

   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/basic-handling.md#selecting-resources) en de werkbalk

1. Tik of klik op de knop **Verplaatsen** paginapictogram om de wizard Verplaatsen te openen.

   ![Knop Verplaatsen](/help/sites-cloud/authoring/assets/move.png)

1. Van de **Naam wijzigen** stap van de wizard:

   * Geef de naam op die de pagina moet krijgen nadat deze is verplaatst en selecteer **Volgende** om verder te gaan.
   * **Annuleren** om het proces af te breken.

   ![Pagina verplaatsen en hernoemen](/help/sites-cloud/authoring/assets/move-page-rename.png)

   * De paginanaam kan hetzelfde blijven als u alleen de pagina verplaatst.

   >[!NOTE]
   >
   >Als u een pagina verplaatst naar een locatie waar al een pagina met dezelfde naam bestaat, genereert het systeem automatisch een variatie in de naam door een getal toe te voegen. Als `beach` bestaat al, een nieuwe pagina met de naam `beach` wordt `beach1`.

1. Van de **Doel selecteren** stap van de wizard:

   * Gebruik de [kolomweergave](/help/sites-cloud/authoring/basic-handling.md#column-view) om naar de nieuwe locatie voor de pagina te navigeren:

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

   * U kunt aangeven welke aanpassingen moeten worden aangebracht en/of opnieuw moeten worden gepubliceerd.

   >[!NOTE]
   >
   >Als er geen koppeling is naar de pagina en er niet naar wordt verwezen, is deze stap niet beschikbaar.

   ![Pagina verplaatsen opnieuw publiceren](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. Tik of klik op **Verplaatsen** om te bepalen wanneer de bewegingsactie zou moeten voorkomen.

   * **Nu** zal een [asynchrone taak](#asynchronous-actions) om de pagina direct te verplaatsen.
   * **Later** Hiermee kunt u een datum voor de verwerking van de verplaatsing plannen.

   ![De datum van verplaatsing definiëren](assets/managing-pages-move-page-now-later.png)

1. Tik of klik op **Doorgaan** om het verplaatsen van de pagina te voltooien.

>[!NOTE]
>
>Als de pagina al is gepubliceerd, wordt de publicatie ervan automatisch ongedaan gemaakt wanneer u de pagina verplaatst. Standaard wordt de animatie opnieuw gepubliceerd wanneer de verplaatsing is voltooid, maar dit kan veranderen door de controle op de knop **Opnieuw publiceren** in het veld **Aanpassen/Opnieuw publiceren** stap.

>[!NOTE]
>
>De naam van een pagina wijzigen is ook afhankelijk van de instelling [Naamgevingsconventies voor pagina](#page-naming-conventions) wanneer u de nieuwe paginanaam opgeeft.

>[!NOTE]
>
>Een pagina kan alleen worden verplaatst naar een locatie waar de sjabloon waarop de pagina is gebaseerd, is toegestaan. Zie [Beschikbaarheid sjabloon](/help/implementing/developing/components/templates.md#template-availability) voor meer informatie .

### Asynchrone handelingen {#asynchronous-actions}

Handelingen voor het verplaatsen van pagina&#39;s worden altijd asynchroon verwerkt, zodat de gebruiker de bewerkingen in de gebruikersinterface ongehinderd kan voortzetten.

De status van asynchrone taken kan worden gecontroleerd in het dialoogvenster [**Async-taakstatus** dashboard](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) om **Algemene navigatie** > **Gereedschappen** > **Bewerkingen** > **Taken**

>[!TIP]
>
>Voor meer informatie over asynchrone baanverwerking en hoe te om de grens voor de beweging van de pagina te vormen/acties anders te noemen, zie [Asynchrone taken](/help/operations/asynchronous-jobs.md) document in de gebruikershandleiding van Verrichtingen.

### Een pagina verwijderen {#deleting-a-page}

1. Openen [de **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigeer naar de pagina die u wilt verwijderen.
1. Gebruiken [selectiemodus](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) om de vereiste pagina te selecteren, dan gebruik **Verwijderen** op de werkbalk:

   ![Knop Verwijderen](/help/sites-cloud/authoring/assets/delete.png)

1. Een dialoogvenster zal om bevestiging vragen.

   ![Dialoogvenster Verwijderen](/help/sites-cloud/authoring/assets/delete-page.png)

   * **Wilt u de pagina&#39;s archiveren voordat u ze verwijdert?** - Als deze optie is ingeschakeld, worden tijdens het verwijderen versies gemaakt van de pagina&#39;s die voor verwijdering zijn geselecteerd.
      * [Versies kunnen later worden hersteld](/help/sites-cloud/authoring/sites-console/page-versions.md).
      * Pagina&#39;s die zonder vorige versies zijn verwijderd, kunnen niet worden hersteld.
1. Tik of klik op **Annuleren** om de handeling of **Verwijderen** om de actie te bevestigen.
   * Als de pagina geen verwijzingen heeft, wordt de pagina geschrapt.
   * Als de pagina verwijzingen heeft, zal een berichtvakje u meedelen dat **Naar een of meer pagina&#39;s wordt verwezen.** U kunt **Verwijderen forceren** of **Annuleren**.

>[!NOTE]
>
>Als een pagina al is gepubliceerd, wordt deze automatisch niet gepubliceerd voordat deze wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt [Een pagina vergrendelen/ontgrendelen](/help/sites-cloud/authoring/page-editor/edit-content.md#locking-a-page) vanuit een console of wanneer u een afzonderlijke pagina bewerkt. Informatie over het feit of een pagina is vergrendeld, wordt ook op beide locaties weergegeven.

![Knop Vergrendelen](/help/sites-cloud/authoring/assets/lock.png)
![Knop Ontgrendelen](/help/sites-cloud/authoring/assets/unlock.png)

### Een nieuwe map maken {#creating-a-new-folder}

U kunt mappen maken waarmee u uw bestanden en pagina&#39;s kunt ordenen.

1. Openen [de **Sites** console.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigeer naar de gewenste locatie.
1. Selecteer **Maken** van de werkbalk
1. Selecteren **Map** het dialoogvenster openen. Hier kunt u de **Naam** en **Titel**:

   ![Map maken](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. Selecteren **Maken** om de map te maken.

>[!NOTE]
>
>* Mappen zijn ook onderworpen aan de [Naamgevingsconventies voor pagina](#page-naming-conventions) wanneer u de nieuwe mapnaam opgeeft.
>* Mappen kunnen alleen direct onder **Sites** of onder andere mappen. Ze kunnen niet onder een pagina worden gemaakt.
>* Met de standaardhandelingen kunt u eigenschappen verplaatsen, kopiëren, plakken, verwijderen, publiceren, verwijderen en weergeven/bewerken uitvoeren op een map.
>* Mappen zijn niet beschikbaar voor selectie in een live kopie.
