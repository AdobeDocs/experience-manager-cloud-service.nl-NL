---
title: Tags beheren
description: Leer hoe u tags kunt beheren in AEM om uw inhoud te ordenen.
exl-id: 42480699-b7a7-4678-a763-569a9b7573e2
solution: Experience Manager Sites
feature: Workflow
role: Admin
source-git-commit: d46678e999889934631bd0c678de5b060bc38f44
workflow-type: tm+mt
source-wordcount: '2200'
ht-degree: 0%

---

# Tags beheren {#administering-tags}

Tags zijn een intuïtieve methode om uw inhoud te classificeren. U kunt ze beschouwen als trefwoorden of labels (metagegevens) waarmee inhoud sneller kan worden gevonden.

In Adobe Experience Manager (AEM) kan een tag een eigenschap zijn van:

* Een inhoudsknooppunt voor een pagina
   * Zie het document [ Gebruikend Markeringen ](/help/sites-cloud/authoring/sites-console/tags.md) voor meer informatie.
* Een metagegevensknooppunt voor een element
   * Zie het document [ Beheerde Meta-gegevens voor Digitale Assets ](/help/assets/manage-metadata.md) voor meer informatie.

>[!TIP]
>
>Het is aan te raden het aantal labels dat betrekking heeft op dezelfde ideeën tot een minimum te beperken. Bijvoorbeeld, als u inhoud voor een outdoorleveringsopslag beheert, hebt u waarschijnlijk geen markering voor zowel **schoeisel** en **schoenen** waarschijnlijk nodig.

## Functies voor tags {#tag-features}

Tags bieden robuuste functies voor het ordenen en beheren van inhoud.

* Tags kunnen in verschillende naamruimten worden gegroepeerd.
   * Naamruimten kunnen worden beschouwd als hiërarchieën waarmee taxonomieën kunnen worden gemaakt.
   * Deze taxonomieën zijn wereldwijd in AEM.
* Tags kunnen door auteurs worden toegepast en door sitebezoekers worden gebruikt.
* Ongeacht de maker van de tags worden alle typen tags beschikbaar gemaakt voor selectie, zowel bij het toewijzen aan een pagina als bij het zoeken.
* De markeringen worden gebruikt door de [ Component van de Lijst ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html) om dynamische lijsten te produceren die op de geselecteerde markeringen worden gebaseerd.

## Tagvereisten {#requirements}

Er zijn een paar technische details om in mening te houden wanneer het creëren van en het leiden van markeringen.

* Tags moeten uniek zijn binnen een specifieke naamruimte.
* De naam van een tag mag geen scheidingstekens voor tags bevatten:
   * Colon (`:`) - Hiermee wordt de naamruimtetag gescheiden
   * Snede (`/`) - Hiermee worden subtags gescheiden
* Als de titel van een tag labelscheidingstekens bevat, worden deze in de gebruikersinterface onderdrukt.
* Tags kunnen worden gemaakt en de bijbehorende taxonomie kan worden gewijzigd door leden van de groep `tag-administrators` en leden die wijzigingsrechten hebben op `/content/cq:tags` .
   * Een tag die onderliggende tags bevat, wordt een containertag genoemd.
   * Een tag die geen containertag is, wordt een bladtag genoemd.
   * Een naamruimte van een tag kan een blad- of containertag zijn.

Voor meer technische details op hoe de markeringen werken, zie [ AEM het Etiketteren Kader ](/help/implementing/developing/introduction/tagging-framework.md).

## Tagingsconsole {#tagging-console}

De coderingsconsole wordt gebruikt om labels en hun taxonomieën te maken en te beheren. U kunt de tagconsole gebruiken om uw tags te beheren door:

* Groeperen in naamruimten.
* Het gebruik van bestaande tags controleren voordat u nieuwe maakt.
* Tags opnieuw ordenen zonder de tag los te koppelen van de inhoud waarnaar momenteel wordt verwezen.

De tagconsole openen:

1. Meld u aan bij een ontwerpomgeving met beheerdersrechten.
1. Selecteer **`Tools`** > **`General`** >
   **`Tagging`**.

![ de het etiketteren console in AEM ](/help/sites-cloud/administering/assets/tagging-console.png)

## Nieuwe tags maken {#creating-new-tags}

Er zijn verschillende stappen om tags te maken en te gebruiken om uw inhoud te ordenen.

1. [ creeer een namespace voor uw markeringen ](#creating-namespaces) (of kies bestaande te hergebruiken).
1. [Maak een nieuwe tag.](#creating-tags)
1. [Publish the tag.](#publishing-tags)

### Naamruimten maken {#creating-namespaces}

Een naamruimte wordt gebruikt om andere tags te ordenen. Het kan worden beschouwd als de laag-vlakke markering en typisch gebruikt om andere markeringen te groeperen.

1. Om een namespace tot stand te brengen, open de [ etiketterende console ](#tagging-console) en selecteer **creeer** knoop in de toolbar en dan **creeer Namespace**.

   ![ voeg de dialoog van Namespace ](/help/sites-cloud/administering/assets/add-namespace.png) toe

1. Verstrek de noodzakelijke informatie.

   * **Titel** - een titel voor namespace die aan de gebruiker in (facultatieve) UI wordt getoond
   * **Naam** - als een naam niet wordt gespecificeerd, wordt een geldige knoopnaam gecreeerd van de **Titel**. Zie het document [ AEM het Etiketteren Kader ](/help/implementing/developing/introduction/tagging-framework.md#tagid) voor meer informatie.
   * **Beschrijving** - een beschrijving van namespace (facultatief)

1. Zodra de vereiste informatie is ingegaan uitgezocht **creeer**.

De naamruimte wordt gemaakt. In de coderingsconsole bevinden de naamruimten zich op het laagste niveau (helemaal links in de console) en worden deze weergegeven door mappictogrammen, die hun aard weerspiegelen als een &#39;container&#39; of groepering van andere tags.

U kunt [ nieuwe markeringen ](#creating-tags) in dit namespace nu tot stand brengen of [ bestaande markeringen beheren.](#managing-tags)

Een naamruimte hoeft geen subtags te bevatten. Omdat een naamruimte zelf een tag is, kan deze worden gebruikt om de inhoud te ordenen zoals elke andere tag. Nochtans, om een gestructureerde het etiketteren taxonomie te blijven creëren, kunt u [ subtags ](#creating-tags) binnen tot stand brengen die namespace op uw projectvereisten wordt gebaseerd.

### Tags maken {#creating-tags}

Tags worden over het algemeen toegevoegd aan naamruimten.

1. Om een markering tot stand te brengen, open de [ etiketterende console.](#tagging-console)

1. Selecteer de naamruimte waar u de tag wilt maken. Of selecteer een andere tag om een subtag eronder te maken.

1. Selecteer **creeer** knoop op de toolbar en dan **creeer Markering**.

1. Het **creeer de dialoog van de Markering** opent. Geef de vereiste informatie voor de nieuwe tag op.

   * **Titel** - een vertoningstitel voor de (vereiste) markering
   * **Naam** - een naam voor de (vereiste) markering. Als gespecificeerd niet, wordt een geldige knoopnaam gecreeerd van de **Titel**. Zie [ TagID ](/help/implementing/developing/introduction/tagging-framework.md#tagid).
   * **Beschrijving** - een beschrijving van de markering
   * **Weg van de Markering** - Gebreken aan namespace (of markering) u in de het etiketteren console selecteerde. U kunt deze functie handmatig bijwerken door op het pictogram van de padkiezer te tikken of te klikken.

   ![ creeer markeringsdialoog ](assets/create-tag.png)

1. Selecteer **voorleggen**.

De tag wordt gemaakt en de console wordt bijgewerkt om de nieuwe tag weer te geven.

Met tags kunt u op basis van uw organisatorische behoeften uw eigen taxonomie op flexibele wijze maken.

* U kunt onderliggende tags van bestaande tags maken door de bovenliggende tag in de console te selecteren voordat u de nieuwe tag maakt.
* Als u een tag maakt zonder een naamruimte of een andere tag te selecteren, maakt u in feite een naamruimte.

### Codes publiceren {#publishing-tags}

Net als bij het maken van andere inhoud in AEM, bestaat een tag (of naamruimte) alleen in de ontwerpomgeving nadat u een tag hebt gemaakt. De tags zijn alleen beschikbaar voor gebruikers als u deze publiceert.

1. Om een markering te publiceren, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering of de markeringen u en in de toolbar wilt publiceren, uitgezochte **Publish**.

   ![ Selecterend markeringen in de console ](assets/select-tags.png)

1. De **de markering van Publish** dialoog vraagt om een bevestiging om de geselecteerde markeringen te publiceren. Selecteer **Publish**.

   ![ de bevestiging van de Publish markering modaal ](assets/publish-tag.png)

1. De publicatieactie wordt bevestigd met de dialoog van het Succes van a ****.

   ![ de dialoog van het markeringssucces van Publish ](assets/publish-tag-success.png)

De geselecteerde labels worden in de wachtrij voor publicatie geplaatst. Net als bij pagina-inhoud wordt (worden) alleen de geselecteerde tag(s) gepubliceerd, ongeacht of deze subtags bevat of niet.

Om een volledige taxonomie (a namespace en sub-markeringen) te publiceren, moet de beste praktijk a [ pakket ](/help/implementing/developing/tools/package-manager.md) van namespace (zie [ Knoop van de Hoofdmap van de Taxonomie ](/help/implementing/developing/introduction/tagging-framework.md#taxonomy-root-node)) tot stand brengen.

<!--
Be sure to [apply permissions](#setting-tag-permissions) to the namespace before creating the package.
-->

## Tags beheren {#managing-tags}

Er zijn verschillende acties die u kunt uitvoeren op bestaande tags en naamruimten om deze te beheren en te ordenen. Selecteer eenvoudig een markering of namespace in de [ etiketterende console ](#tagging-console) om in de toolbar de beschikbare acties te openbaren.

* [Eigenschappen weergeven](#viewing-tag-properties)
* [Bewerken](#editing-tags)
* [Publiceren ongedaan maken](#unpublishing-tags)
* [Verwijzingen](#viewing-tag-references)
* [Verplaatsen](#moving-tags)
* [Samenvoegen](#merging-tags)
* [Verwijderen](#deleting-tags)

Als er voldoende notitie beschikbaar is op de werkbalk, zijn er extra opties beschikbaar achter het ellipspictogram.

### Tageigenschappen weergeven {#viewing-tag-properties}

Wanneer één enkele markering, namespace of andere markering in de etiketterende console wordt geselecteerd, worden de basisdetails van de geselecteerde markering zoals tijd van laatste uitgeeft en laatste publicatie getoond in de kolom links van de markeringskolom.

![ de detailkolom van de Markering ](assets/tag-details-column.png)

U kunt meer details over de markering bekijken met inbegrip van wie het het laatst publiceerde en wanneer door de console aan de **mening van Eigenschappen** te schakelen.

1. Om de eigenschappen van een markering te bekijken, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering de waarvan eigenschappen u en in de linkerspooruitgezochte **Eigenschappen** wilt bekijken.

   ![ het Selecteren eigenschappen mening ](assets/view-tag-properties.png)

1. De gedetailleerde eigenschappen van de geselecteerde tag worden weergegeven in de linkerspoorstaaf.

   ![ het Bekijken van markeringseigenschappen ](assets/tag-properties.png)

Voor meer details bij het selecteren van het bekijken wijzen en spoorstaaf, zie [ Basis Behandelend ](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

### Tags bewerken {#editing-tags}

Tags en naamruimten kunnen na het maken worden bewerkt.

1. Om een markering uit te geven, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering u wilt uitgeven en in de toolbar, uitgezocht **** uitgeven.

1. Breng de gewenste wijzigingen aan. Het is mogelijk de volgende wijzigingen aan te brengen:

   * **Titel**
   * **Beschrijving**
   * [**Lokalisatie**](#managing-tags-in-different-languages)

1. Nadat wordt uitgegeven, uitgezochte **voorleggen**.

Voor details over het toevoegen van taalvertalingen, zie de sectie over [ het Leiden Markeringen in Verschillende Talen ](#managing-tags-in-different-languages).

Als de veranderingen u aanbracht aan een reeds gepubliceerde markering waren, kunt u het [ willen opnieuw publiceren.](#publishing-tags)

### Publicatie van labels ongedaan maken {#unpublishing-tags}

Als u de tag op de instantie van de auteur wilt deactiveren en deze uit uw publicatie-instantie wilt verwijderen, kunt u de publicatie ervan ongedaan maken.

1. Om een markering ongedaan te maken, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering of de markeringen u wilt unpublish en in de toolbar, uitgezocht **unpublish**.

   ![ Selecterend markeringen in de console ](assets/select-tags.png)

1. De **Unublish dialoog van de Markering** vraagt om een bevestiging om de geselecteerde markeringen te publiceren. Selecteer **Publish**.

   ![ de bevestiging van de Publish markering modaal ](assets/unpublish-tag.png)

1. De unpublish actie wordt bevestigd met de dialoog van het Succes van a ****.

   ![ de dialoog van het markeringssucces van Publish ](assets/unpublish-tag-success.png)

De geselecteerde tag(s) worden in de wachtrij geplaatst voor publicatie. Als de geselecteerde tag een containertag is, worden alle onderliggende tags gedeactiveerd in de auteursomgeving en verwijderd uit de publicatieomgeving.

### Tagverwijzingen weergeven {#viewing-tag-references}

Het kan handig zijn om te zien op welke inhoud een bepaalde tag wordt toegepast. U kunt dit doen door de **mening van Verwijzingen** in de het etiketteren console te gebruiken.

1. Om de verwijzingen van een markering te bekijken, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering de waarvan verwijzingen u wilt bekijken en in de linkerspooruitgezochte **Verwijzingen**.

   ![ het Selecteren eigenschappen mening ](assets/view-tag-references.png)

1. Het totale aantal verwijzingen voor de geselecteerde markering wordt getoond in het linkerspoor.

   ![ het Bekijken van markeringsverwijzingen ](assets/tag-references.png)

1. Selecteer het aantal tagverwijzingen om de gedetailleerde lijst weer te geven met inhoud die aan de tag is toegewezen.

   ![ het Bekijken van het detail van de verwijzingen van de markering ](assets/tag-references-detail.png)

Houd de muis boven een verwijzing of selecteer een inhoud in de lijst om het volledige pad van de inhoud weer te geven.

Voor meer details bij het selecteren van het bekijken wijzen en spoorstaaf, zie [ Basis Behandelend ](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

### Labels verplaatsen {#moving-tags}

Het kan nodig zijn om de tagtaxonomie op een andere manier op te schonen of te reorganiseren door een tag naar een nieuwe locatie te verplaatsen of de naam ervan te wijzigen.

>[!TIP]
>
>Het wordt aanbevolen dat alleen beheerders tags mogen verplaatsen en hernoemen.

1. Om een markering te bewegen of anders te noemen, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering die u wilt bewegen of anders noemen en **Beweging** in de toolbar selecteren.

1. In de **dialoog van de Markering van de Beweging**, specificeer welk bezit u wilt veranderen.

   * **hernoemt aan** - de nieuwe naam u de markering wilt geven
      * Dit veld wordt vooraf gevuld met de huidige naam van de tag.
      * Laat het veld ongewijzigd als u alleen de code wilt verplaatsen en de naam ervan niet wilt wijzigen.
   * **Beweging aan** - waar u de markering wilt bewegen
      * Dit veld wordt vooraf gevuld met de huidige locatie van de tag.
      * Laat het veld ongewijzigd als u alleen de naam van de tag wilt wijzigen en deze niet wilt verplaatsen.

   ![ Markering van de Beweging ](assets/move-tag.png)

1. Selecteer **voorleggen**.

De naam van de tag wordt gewijzigd en/of naar de nieuwe locatie verplaatst. Wanneer de geselecteerde tag een containertag is, worden bij het verplaatsen van de tag ook alle onderliggende tags verplaatst.

### Tags samenvoegen {#merging-tags}

Als de codeertaxonomie gelijksoortige duplicaten of tags bevat, kan het handig zijn deze tags samen te voegen. Wanneer tag `A` wordt samengevoegd met tag `B` , worden alle pagina&#39;s met tag `A` gecodeerd met tag `B` en is tag `A` niet meer beschikbaar voor auteurs.

1. Om twee markeringen samen te voegen, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering die u in een andere markering wilt samenvoegen en dan **** in de toolbar selecteren samenvoegen.

1. In de **dialoog van de Markering van de Fusie**, selecteer **doorbladert** pictogram van de **Fusie in** gebied om te specificeren waarin de markering u de geselecteerde markering wilt samenvoegen.

   ![ de dialoog van de Markering van de Fusie ](assets/merge-tag.png)

1. Selecteer **voorleggen**.

De tag die in de console is geselecteerd, wordt samengevoegd met de tag die in het dialoogvenster is opgegeven. Wanneer een tag waarnaar wordt verwezen wordt verplaatst of samengevoegd, wordt de tag niet fysiek verwijderd, zodat verwijzingen behouden kunnen blijven. Zie [ AEM het Etiketteren Kader ](/help/implementing/developing/introduction/tagging-framework.md#moving-and-merging-tags) voor meer informatie.

### Tags verwijderen {#deleting-tags}

Als de codeertaxonomie verandert en een tag of naamruimte onnodig maakt, kan deze worden verwijderd.

1. Om een markering te schrappen, open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering die u wilt schrappen en dan **Schrapping** in de toolbar selecteren.

1. De **dialoog van de Markering van de Schrapping** vraagt om een bevestiging om de geselecteerde markering(en) te schrappen. Selecteer **Schrapping**.

   ![ de bevestiging van de Markering van de Schrapping modaal ](assets/delete-tag.png)

1. AEM controleert of er niet naar de tag wordt verwezen.

   1. Als er geen verwijzingen worden gevonden, AEM vraagt om definitieve bevestiging om te schrappen. Selecteer **Schrapping**

      ![ Geen gevonden verwijzingen ](assets/no-references-found.png)

   1. Als verwijzingen worden gevonden, presenteert AEM hen en vraagt om definitieve bevestiging om te schrappen.

      ![ Gevonden Verwijzingen ](assets/references-found.png)

De geselecteerde tag(s) wordt verwijderd en definitief verwijderd uit de auteursomgeving. Als de tag is gepubliceerd, wordt deze ook verwijderd uit de publicatieomgeving. Als de geselecteerde tag een containertag is, worden ook alle onderliggende tags verwijderd.

<!--

## Setting Tag Permissions {#setting-tag-permissions}

Tag permissions are ['secure (by default)'](/help/sites-administering/production-ready.md); a best practice for the publish environment that requires read permission to be explicitly allowed for tags. Bascially, this is done by creating a package of the Tag Namespace after permissions have been set on author, and installing the package on all publish instances.

* on author instance

    * sign in with administrative privileges
    * access the [Security Console](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console),

        * for example, browse to http://localhost:4502/useradmin

    * in the left pane, select the group (or user) for which [read permission](/help/sites-administering/security.md#permissions) is to be granted
    * in the right pane, locate the **Path **to the Tag Namespace

        * for example, `/content/cq:tags/mycommunity`

    * select the `checkbox`in the **Read** column
    * select **Save**

![chlimage_1-204](assets/chlimage_1-204.png)

* ensure all publish instances have same permissions

    * one approach is to [create a package](/help/sites-administering/package-manager.md#package-manager) of the namespace on author

        * on `Advanced` tab, for `AC Handling` select `Overwrite`

    * replicate the package

        * choose `Replicate` from package manager

-->

## Tags beheren in verschillende talen {#managing-tags-in-different-languages}

De eigenschap `title` van een tag kan in meerdere talen worden vertaald. Nadat de code is vertaald, kan de juiste tagtitel worden weergegeven op basis van de taal van de gebruiker of inhoud.

Laten we ervan uitgaan dat we een tag met de naam `Animals` hebben die we in het Duits en Frans willen vertalen.

1. Open de [ etiketterende console.](#tagging-console)

1. Selecteer de markering die u wilt vertalen en dan selecteren **uitgeven** in de toolbar.

1. In **geef de dialoog van de Markering** uit, in de **3} kolom van de Localisatie {, selecteer de doeltaal, bijvoorbeeld, Duits.**

1. Op het **Duitse** gebied dat verschijnt, verstrek de vertaalde titel.

1. Herhaal de vorige twee stappen voor het Frans.

   ![ Vertaal markeringstitels ](assets/translate-tag.png)

1. Selecteer **voorleggen**.

Voor inhoudspagina&#39;s, wordt de taal gekozen voor de markering genomen van de paginalaal, indien beschikbaar.

In de ontwerpomgeving gebruikt AEM echter de taalinstelling van de gebruiker. In de coderingsconsole wordt voor de tag `Animals` `Animaux` dus weergegeven voor een gebruiker die de taal in zijn gebruikerseigenschappen instelt op Frans.

Om een nieuwe taal aan de dialoog toe te voegen, zie het document [ Bouwend Tags in AEM Toepassingen ](/help/implementing/developing/introduction/tagging-applications.md#adding-a-new-language-to-the-edit-tag-dialog)

>[!TIP]
>
>Als u meer over AEM localisatieeigenschappen wilt leren, zie [ Vertaal Uw Inhoud voor Meertalige Plaatsen ](/help/sites-cloud/administering/translation/overview.md).
