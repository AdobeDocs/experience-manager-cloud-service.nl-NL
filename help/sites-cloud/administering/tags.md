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
   * Zie het document [Tags gebruiken](/help/sites-cloud/authoring/sites-console/tags.md) voor meer informatie .
* Een metagegevensknooppunt voor een element
   * Zie het document [Metagegevens voor digitale elementen beheren](/help/assets/manage-metadata.md) voor meer informatie .

>[!TIP]
>
>Het is aan te raden het aantal labels dat betrekking heeft op dezelfde ideeën tot een minimum te beperken. Bijvoorbeeld, als u inhoud voor een outdoorleveringsopslag beheert, hebt u waarschijnlijk geen markering voor allebei nodig **schoeisel** en **schoenen**.

## Functies voor tags {#tag-features}

Tags bieden robuuste functies voor het ordenen en beheren van inhoud.

* Tags kunnen in verschillende naamruimten worden gegroepeerd.
   * Naamruimten kunnen worden beschouwd als hiërarchieën waarmee taxonomieën kunnen worden gemaakt.
   * Deze taxonomieën zijn wereldwijd in AEM.
* Tags kunnen door auteurs worden toegepast en door sitebezoekers worden gebruikt.
* Ongeacht de maker van de tags worden alle typen tags beschikbaar gemaakt voor selectie, zowel bij het toewijzen aan een pagina als bij het zoeken.
* Tags worden gebruikt door de [Component List](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html) om dynamische lijsten te produceren die op de geselecteerde markeringen worden gebaseerd.

## Tagvereisten {#requirements}

Er zijn een paar technische details om in mening te houden wanneer het creëren van en het leiden van markeringen.

* Tags moeten uniek zijn binnen een specifieke naamruimte.
* De naam van een tag mag geen scheidingstekens voor tags bevatten:
   * Colon (`:`) - Hiermee wordt de naamruimtetag gescheiden
   * Slash (`/`) - Subtags verwijderen
* Als de titel van een tag labelscheidingstekens bevat, worden deze in de gebruikersinterface onderdrukt.
* Tags kunnen worden gemaakt en hun taxonomie kan worden gewijzigd door leden van de `tag-administrators` groep en leden die wijzigingsrechten hebben op `/content/cq:tags`.
   * Een tag die onderliggende tags bevat, wordt een containertag genoemd.
   * Een tag die geen containertag is, wordt een bladtag genoemd.
   * Een naamruimte van een tag kan een blad- of containertag zijn.

Voor meer technische details over hoe markeringen werken, zie [Kader voor tags AEM](/help/implementing/developing/introduction/tagging-framework.md).

## Tagingsconsole {#tagging-console}

De coderingsconsole wordt gebruikt om labels en hun taxonomieën te maken en te beheren. U kunt de tagconsole gebruiken om uw tags te beheren door:

* Groeperen in naamruimten.
* Het gebruik van bestaande tags controleren voordat u nieuwe maakt.
* Tags opnieuw ordenen zonder de tag los te koppelen van de inhoud waarnaar momenteel wordt verwezen.

De tagconsole openen:

1. Meld u aan bij een ontwerpomgeving met beheerdersrechten.
1. Selecteer in het algemene navigatiemenu de optie **`Tools`** > **`General`** >
   **`Tagging`**.

![De tagconsole in AEM](/help/sites-cloud/administering/assets/tagging-console.png)

## Nieuwe tags maken {#creating-new-tags}

Er zijn verschillende stappen om tags te maken en te gebruiken om uw inhoud te ordenen.

1. [Een naamruimte maken voor uw tags](#creating-namespaces) (of kies een bestaande die u wilt hergebruiken).
1. [Maak een nieuwe tag.](#creating-tags)
1. [Publiceer de tag.](#publishing-tags)

### Naamruimten maken {#creating-namespaces}

Een naamruimte wordt gebruikt om andere tags te ordenen. Het kan worden beschouwd als de laag-vlakke markering en typisch gebruikt om andere markeringen te groeperen.

1. Als u een naamruimte wilt maken, opent u de [tagconsole](#tagging-console) en selecteert u de **Maken** in de werkbalk en vervolgens **Naamruimte maken**.

   ![Het dialoogvenster Namespace toevoegen](/help/sites-cloud/administering/assets/add-namespace.png)

1. Verstrek de noodzakelijke informatie.

   * **Titel** - Een titel voor de naamruimte die aan de gebruiker wordt weergegeven in de gebruikersinterface (optioneel)
   * **Naam** - Als er geen naam is opgegeven, wordt een geldige knooppuntnaam gemaakt op basis van de **Titel**. Zie het document [Kader voor tags AEM](/help/implementing/developing/introduction/tagging-framework.md#tagid) voor meer informatie .
   * **Beschrijving** - Een beschrijving van de naamruimte (optioneel)

1. Nadat de vereiste informatie is ingevoerd, selecteert u **Maken**.

De naamruimte wordt gemaakt. In de coderingsconsole bevinden de naamruimten zich op het laagste niveau (helemaal links in de console) en worden deze weergegeven door mappictogrammen, die hun aard weerspiegelen als een &#39;container&#39; of groepering van andere tags.

U kunt nu [nieuwe tags maken](#creating-tags) in deze naamruimte of [bestaande tags beheren.](#managing-tags)

Een naamruimte hoeft geen subtags te bevatten. Omdat een naamruimte zelf een tag is, kan deze worden gebruikt om de inhoud te ordenen zoals elke andere tag. Als u echter een gestructureerde tagingtaxonomie wilt blijven maken, kunt u [subtags maken](#creating-tags) binnen die namespace die op uw projectvereisten wordt gebaseerd.

### Tags maken {#creating-tags}

Tags worden over het algemeen toegevoegd aan naamruimten.

1. Als u een tag wilt maken, opent u de [taggen-console.](#tagging-console)

1. Selecteer de naamruimte waar u de tag wilt maken. Of selecteer een andere tag om een subtag eronder te maken.

1. Selecteer de **Maken** op de werkbalk **Tag maken**.

1. De **Tag maken** wordt geopend. Geef de vereiste informatie voor de nieuwe tag op.

   * **Titel** - Een titel voor weergave van de tag (vereist)
   * **Naam** - Een naam voor de tag (vereist). Indien niet opgegeven, wordt een geldige knooppuntnaam gemaakt op basis van de **Titel**. Zie [TagID](/help/implementing/developing/introduction/tagging-framework.md#tagid).
   * **Beschrijving** - Een beschrijving van de tag
   * **Labelpad** - Wordt standaard ingesteld op de naamruimte (of tag) die u hebt geselecteerd in de tagconsole. U kunt deze functie handmatig bijwerken door op het pictogram van de padkiezer te tikken of te klikken.

   ![Tagdialoogvenster maken](assets/create-tag.png)

1. Selecteren **Verzenden**.

De tag wordt gemaakt en de console wordt bijgewerkt om de nieuwe tag weer te geven.

Met tags kunt u op basis van uw organisatorische behoeften uw eigen taxonomie op flexibele wijze maken.

* U kunt onderliggende tags van bestaande tags maken door de bovenliggende tag in de console te selecteren voordat u de nieuwe tag maakt.
* Als u een tag maakt zonder een naamruimte of een andere tag te selecteren, maakt u in feite een naamruimte.

### Codes publiceren {#publishing-tags}

Net als bij het maken van andere inhoud in AEM, bestaat een tag (of naamruimte) alleen in de ontwerpomgeving nadat u een tag hebt gemaakt. De tags zijn alleen beschikbaar voor gebruikers als u deze publiceert.

1. Als u een tag wilt publiceren, opent u de [taggen-console.](#tagging-console)

1. Selecteer de tag of tags die u wilt publiceren en selecteer in de werkbalk de optie **Publiceren**.

   ![Tags selecteren in de console](assets/select-tags.png)

1. De **Tag publiceren** vraagt om een bevestiging om de geselecteerde tags te publiceren. Selecteren **Publiceren**.

   ![De bevestigingsmodus van de publicatiemarkering](assets/publish-tag.png)

1. De publicatieactie wordt bevestigd met een **Succes** in.

   ![Dialoogvenster Tagsucces publiceren](assets/publish-tag-success.png)

De geselecteerde labels worden in de wachtrij voor publicatie geplaatst. Net als bij pagina-inhoud wordt (worden) alleen de geselecteerde tag(s) gepubliceerd, ongeacht of deze subtags bevat of niet.

Als u een volledige taxonomie (een naamruimte en subtags) wilt publiceren, kunt u het beste een [package](/help/implementing/developing/tools/package-manager.md) van de naamruimte (zie [Taxonomy Root Node](/help/implementing/developing/introduction/tagging-framework.md#taxonomy-root-node)).

<!--
Be sure to [apply permissions](#setting-tag-permissions) to the namespace before creating the package.
-->

## Tags beheren {#managing-tags}

Er zijn verschillende acties die u kunt uitvoeren op bestaande tags en naamruimten om deze te beheren en te ordenen. Selecteer gewoon een tag of naamruimte in het dialoogvenster [tagconsole](#tagging-console) om de beschikbare acties op de werkbalk weer te geven.

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

![Kolom met tagdetails](assets/tag-details-column.png)

U kunt meer details over de markering bekijken met inbegrip van wie het laatst publiceerde en wanneer door de console aan te schakelen **Eigenschappen** weergeven.

1. Als u de eigenschappen van een tag wilt weergeven, opent u het dialoogvenster [taggen-console.](#tagging-console)

1. Selecteer de tag waarvan u de eigenschappen wilt weergeven en selecteer in de linkertrack **Eigenschappen**.

   ![Weergave Eigenschappen selecteren](assets/view-tag-properties.png)

1. De gedetailleerde eigenschappen van de geselecteerde tag worden weergegeven in de linkerspoorstaaf.

   ![Tageigenschappen weergeven](assets/tag-properties.png)

Zie voor meer informatie over het selecteren van weergavemodi en de spoorstaaf [Basisverwerking](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

### Tags bewerken {#editing-tags}

Tags en naamruimten kunnen na het maken worden bewerkt.

1. Als u een tag wilt bewerken, opent u het dialoogvenster [taggen-console.](#tagging-console)

1. Selecteer het label dat u wilt bewerken en selecteer in de werkbalk de optie **Bewerken**.

1. Breng de gewenste wijzigingen aan. Het is mogelijk de volgende wijzigingen aan te brengen:

   * **Titel**
   * **Beschrijving**
   * [**Lokalisatie**](#managing-tags-in-different-languages)

1. Nadat de bewerkingen zijn aangebracht, selecteert u **Verzenden**.

Zie de sectie over het toevoegen van taalvertalingen voor meer informatie over het toevoegen van taalvertalingen [Tags beheren in verschillende talen](#managing-tags-in-different-languages).

Als de wijzigingen die u hebt aangebracht, een reeds gepubliceerde tag zijn, kunt u [deze opnieuw publiceren.](#publishing-tags)

### Publicatie van labels ongedaan maken {#unpublishing-tags}

Als u de tag op de instantie van de auteur wilt deactiveren en deze uit uw publicatie-instantie wilt verwijderen, kunt u de publicatie ervan ongedaan maken.

1. Als u de publicatie van een tag ongedaan wilt maken, opent u het dialoogvenster [taggen-console.](#tagging-console)

1. Selecteer de tag of tags waarvan u de publicatie ongedaan wilt maken en selecteer in de werkbalk de optie **Publiceren ongedaan maken**.

   ![Tags selecteren in de console](assets/select-tags.png)

1. De **Label onbekend** vraagt om een bevestiging om de geselecteerde tags te publiceren. Selecteren **Publiceren**.

   ![De bevestigingsmodus van de publicatiemarkering](assets/unpublish-tag.png)

1. De actie Unpublish wordt bevestigd met een **Succes** in.

   ![Dialoogvenster Tagsucces publiceren](assets/unpublish-tag-success.png)

De geselecteerde tag(s) worden in de wachtrij geplaatst voor publicatie. Als de geselecteerde tag een containertag is, worden alle onderliggende tags gedeactiveerd in de auteursomgeving en verwijderd uit de publicatieomgeving.

### Tagverwijzingen weergeven {#viewing-tag-references}

Het kan handig zijn om te zien op welke inhoud een bepaalde tag wordt toegepast. U kunt dit doen door **Verwijzingen** in de coderingsconsole.

1. Als u de referenties van een tag wilt weergeven, opent u de [taggen-console.](#tagging-console)

1. Selecteer het label waarvan u de referenties wilt weergeven en selecteer in de linkertrack **Verwijzingen**.

   ![Weergave Eigenschappen selecteren](assets/view-tag-references.png)

1. Het totale aantal verwijzingen voor de geselecteerde markering wordt getoond in het linkerspoor.

   ![Tagverwijzingen weergeven](assets/tag-references.png)

1. Selecteer het aantal tagverwijzingen om de gedetailleerde lijst weer te geven met inhoud die aan de tag is toegewezen.

   ![De details van de verwijzingen van de tag weergeven](assets/tag-references-detail.png)

Houd de muis boven een verwijzing of selecteer een inhoud in de lijst om het volledige pad van de inhoud weer te geven.

Zie voor meer informatie over het selecteren van weergavemodi en de spoorstaaf [Basisverwerking](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

### Labels verplaatsen {#moving-tags}

Het kan nodig zijn om de tagtaxonomie op een andere manier op te schonen of te reorganiseren door een tag naar een nieuwe locatie te verplaatsen of de naam ervan te wijzigen.

>[!TIP]
>
>Het wordt aanbevolen dat alleen beheerders tags mogen verplaatsen en hernoemen.

1. Als u een tag wilt verplaatsen of de naam ervan wilt wijzigen, opent u het dialoogvenster [taggen-console.](#tagging-console)

1. Selecteer de tag die u wilt verplaatsen of wijzig de naam en selecteer **Verplaatsen** in de werkbalk.

1. In de **Tag verplaatsen** geeft u op welke eigenschap u wilt wijzigen.

   * **Naam wijzigen in** - De nieuwe naam die u de tag wilt geven
      * Dit veld wordt vooraf gevuld met de huidige naam van de tag.
      * Laat het veld ongewijzigd als u alleen de code wilt verplaatsen en de naam ervan niet wilt wijzigen.
   * **Verplaatsen naar** - Waar u de tag wilt verplaatsen
      * Dit veld wordt vooraf gevuld met de huidige locatie van de tag.
      * Laat het veld ongewijzigd als u alleen de naam van de tag wilt wijzigen en deze niet wilt verplaatsen.

   ![Tag verplaatsen](assets/move-tag.png)

1. Selecteren **Verzenden**.

De naam van de tag wordt gewijzigd en/of naar de nieuwe locatie verplaatst. Wanneer de geselecteerde tag een containertag is, worden bij het verplaatsen van de tag ook alle onderliggende tags verplaatst.

### Tags samenvoegen {#merging-tags}

Als de codeertaxonomie gelijksoortige duplicaten of tags bevat, kan het handig zijn deze tags samen te voegen. Wanneer label `A` wordt samengevoegd met de tag `B`, alle pagina&#39;s met code `A` worden getagd met tag `B` en -tag `A` is niet meer beschikbaar voor auteurs.

1. Als u twee tags wilt samenvoegen, opent u het dialoogvenster [taggen-console.](#tagging-console)

1. Selecteer de tag die u in een andere tag wilt samenvoegen en selecteer vervolgens **Samenvoegen** in de werkbalk.

1. In de **Tag samenvoegen** selecteert u de **Bladeren** pictogram van de **Samenvoegen in** veld waarin u wilt opgeven in welk label u de geselecteerde tag wilt samenvoegen.

   ![Het dialoogvenster Code samenvoegen](assets/merge-tag.png)

1. Selecteren **Verzenden**.

De tag die in de console is geselecteerd, wordt samengevoegd met de tag die in het dialoogvenster is opgegeven. Wanneer een tag waarnaar wordt verwezen wordt verplaatst of samengevoegd, wordt de tag niet fysiek verwijderd, zodat verwijzingen behouden kunnen blijven. Zie [Kader voor tags AEM](/help/implementing/developing/introduction/tagging-framework.md#moving-and-merging-tags) voor meer informatie .

### Tags verwijderen {#deleting-tags}

Als de codeertaxonomie verandert en een tag of naamruimte onnodig maakt, kan deze worden verwijderd.

1. Als u een tag wilt verwijderen, opent u het dialoogvenster [taggen-console.](#tagging-console)

1. Selecteer het label dat u wilt verwijderen en selecteer vervolgens **Verwijderen** in de werkbalk.

1. De **Label verwijderen** vraagt om een bevestiging om de geselecteerde tag(s) te verwijderen. Selecteren **Verwijderen**.

   ![De bevestigingsmodus van de tag verwijderen](assets/delete-tag.png)

1. AEM controleert of er niet naar de tag wordt verwezen.

   1. Als er geen verwijzingen worden gevonden, AEM vraagt om definitieve bevestiging om te schrappen. Selecteren **Verwijderen**

      ![Geen verwijzingen gevonden](assets/no-references-found.png)

   1. Als verwijzingen worden gevonden, presenteert AEM hen en vraagt om definitieve bevestiging om te schrappen.

      ![Referenties gevonden](assets/references-found.png)

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

De `title` De eigenschap van een tag kan in meerdere talen worden vertaald. Nadat de code is vertaald, kan de juiste tagtitel worden weergegeven op basis van de taal van de gebruiker of inhoud.

Laten we aannemen dat we een tag hebben met de naam `Animals` dat we in het Duits en Frans willen vertalen.

1. Open de [taggen-console.](#tagging-console)

1. Selecteer de tag die u wilt vertalen en selecteer vervolgens **Bewerken** in de werkbalk.

1. In de **Tag bewerken** in het dialoogvenster **Lokalisatie** , selecteert u de doeltaal, bijvoorbeeld Duits.

1. In de **Duits** Geef de vertaalde titel op in het veld dat wordt weergegeven.

1. Herhaal de vorige twee stappen voor het Frans.

   ![Tagtitels omzetten](assets/translate-tag.png)

1. Selecteren **Verzenden**.

Voor inhoudspagina&#39;s, wordt de taal gekozen voor de markering genomen van de paginalaal, indien beschikbaar.

In de ontwerpomgeving gebruikt AEM echter de taalinstelling van de gebruiker. Dus in de tagconsole, voor de `Animals` -tag, `Animaux` wordt weergegeven voor een gebruiker die de taal in zijn gebruikerseigenschappen instelt op Frans.

Zie het document als u een nieuwe taal wilt toevoegen aan het dialoogvenster [Tags samenstellen in AEM toepassingen](/help/implementing/developing/introduction/tagging-applications.md#adding-a-new-language-to-the-edit-tag-dialog)

>[!TIP]
>
>Ga voor meer informatie over AEM lokalisatiefuncties naar [Inhoud vertalen voor meertalige sites](/help/sites-cloud/administering/translation/overview.md).
