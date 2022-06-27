---
title: Pagina-eigenschappen bewerken
description: De vereiste eigenschappen voor een pagina definiëren
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: 73adc2a9cad7f3e5dde723d1b3d695f8cec3ca69
workflow-type: tm+mt
source-wordcount: '1987'
ht-degree: 5%

---

# Pagina-eigenschappen bewerken {#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is beschikbaar, indien van toepassing.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Basis {#basic}

* **Titel en tags**

   * **Titel** - De titel van de pagina wordt op verschillende plaatsen weergegeven. De **Websites** en de **Sites** kaart-/lijstweergaven.
      * Dit is een verplicht veld.
   * **Tags** - Hier kunt u codes aan de pagina toevoegen of eruit verwijderen door de lijst in het selectievak bij te werken.
      * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
      * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.
         * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
         * De nieuwe tag wordt dan weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.
      * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
      * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.
      * Zie voor meer informatie over tags [Tags gebruiken](/help/sites-cloud/authoring/features/tags.md).
   * **Verbergen in navigatie** - Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site.

* **Branding**

   Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Voor deze functionaliteit is het gebruik van de component Pagina vanaf versie 2.14.0 of hoger van het dialoogvenster [Core Components.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

   * **Negeren** - Schakel dit selectievakje in om de merkwitruimte op deze pagina te definiëren.
      * De waarde wordt overgeërfd door onderliggende pagina&#39;s, tenzij deze ook hun **Negeren** ingestelde waarden.
   * **Waarde overschrijven** - De tekst van de merkmarkering die aan de paginatitel moet worden toegevoegd.
      * De waarde wordt toegevoegd aan de paginatitel na een pipe-teken, zoals &quot;Cycling Tuscany&quot; | Altijd klaar voor de WKND&quot;

* **HTML-id**

   * **ID** - HTML-id die moet worden toegepast op de component.

* **Meer titels en beschrijving**

   * **Paginatitel** - Een titel die op de pagina moet worden gebruikt. Wordt meestal gebruikt door titelcomponenten. Als de **Titel** wordt gebruikt.
   * **Navigatietitel** - U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Indien leeg, **Titel** wordt gebruikt.
   * **Ondertitel** - Een ondertitel voor gebruik op de pagina.
   * **Beschrijving** - Uw beschrijving van de pagina, het doel of andere details die u wilt toevoegen.

* **Aan/Uit-tijd**

   >[!NOTE]
   >
   > Zie [Aan- en uittijden - Configuratie activeren](/help/operations/replication.md#on-and-off-times-trigger-configuration) voor details van hoe te om de verwante automatische replicatie te vormen.

   >[!NOTE]
   >Indien **Op tijd** of **Uit-tijd** is in het verleden, en de automatische replicatie wordt gevormd, dan zal de relevante actie onmiddellijk teweeggebracht worden.

   * **Op tijd** - De datum en het tijdstip waarop de gepubliceerde pagina zichtbaar (weergegeven) wordt gemaakt in de publicatieomgeving. De pagina moet, of manueel of door pre-gevormde auto-replicatie worden gepubliceerd.

      * Indien al [gepubliceerd (handmatig)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) deze pagina wordt slapend (verborgen) gehouden totdat deze op het opgegeven tijdstip wordt weergegeven.
      * Als niet gepubliceerd, en gevormd voor auto-replicatie, zal de pagina automatisch worden gepubliceerd, dan, op de gespecificeerde tijd teruggegeven.
      * Als niet gepubliceerd, en niet gevormd voor auto-replicatie, zal de pagina niet automatisch gepubliceerd worden, zodat zal 404 worden gezien wanneer een poging om tot de pagina toegang te hebben wordt gemaakt.
   * **Uit-tijd** - Vergelijkbaar met en vaak gebruikt in combinatie met **Op tijd** Hiermee bepaalt u de tijd waarop de gepubliceerde pagina wordt verborgen in de publicatieomgeving.

   * Deze velden behouden (**Op tijd** en **Uit-tijd**) is leeg voor pagina&#39;s die u direct wilt publiceren en die beschikbaar zijn in de publicatieomgeving totdat ze zijn gedeactiveerd (het normale scenario).


* **Vanity URL**

   * Hiermee kunt u een vanity-URL voor deze pagina invoeren, waarmee u een kortere en/of expressieve URL kunt hebben.
   * Als bijvoorbeeld de URL voor Vanity is ingesteld op `welcome` naar de pagina die wordt aangeduid door het pad `/v1.0/startpage` voor de website `http://example.com`vervolgens `http://example.com/welcome` zou de vanzelf-URL zijn van `http://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Vanity-URL&#39;s:
   >
   >* Dit moet uniek zijn, dus zorg ervoor dat de waarde niet al door een andere pagina wordt gebruikt.
   >* Geen ondersteuning voor regex-patronen.
   >* Deze mag niet op een bestaande pagina worden ingesteld.


   * **Toevoegen** - Tik of klik om een veld weer te geven waarin een vanity-URL voor de pagina wordt gedefinieerd.
      * Tik of klik nogmaals om meerdere items toe te voegen.
      * Tik of klik op de knop **Verwijderen** pictogram om de vanity URL te verwijderen.
   * **Redirect Vanity URL** - Geeft aan of de pagina de vanity-URL moet gebruiken.


### Geavanceerd {#advanced}

* **Instellingen**

   * **Taal** - De paginataal
   * **Taalbasis** - Moet worden gecontroleerd als de pagina de basis van een taalkopie is
   * **Omleiden** - Geeft de pagina aan waarnaar deze pagina automatisch moet worden omgeleid met een HTML `302 Found` status.
      * **Permanent omleiden** - Als deze optie is ingeschakeld, wordt de pagina omgeleid naar het doelpad dat samen met een HTML wordt geleverd `301 Moved Permanently` status.
   * **Ontwerp** - Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site
   * **Alias** - Hiermee wordt een alias opgegeven die met deze pagina moet worden gebruikt
      * Als u bijvoorbeeld een alias definieert van `private` voor de pagina `/content/wknd/us/en/magazine/members-only`, kan deze pagina ook worden geopend via `/content/wknd/us/en/magazine/private`
      * Het creëren van een aliasreeksen `sling:alias` eigenschap op het paginaknooppunt, die alleen invloed heeft op de bron, niet op het pad naar de opslagplaats.
      * Pagina&#39;s die door aliassen in de editor worden benaderd, kunnen niet worden gepubliceerd. [Publicatieopties](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.

   <!--
  >For further details see [Localized page names under SEO and URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names).
  -->

* **Configuratie**

   * **Cloud Configuration** - Het pad naar de configuratie

* **Sjablooninstellingen**

   * **Toegestane sjablonen** - [Hiermee definieert u de lijst met sjablonen die beschikbaar zijn](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) binnen dit subbijkantoor

* **Verificatievereiste**

   * **Inschakelen** - Gebruik van verificatie toestaan om toegang te krijgen tot de pagina

      >[!NOTE]
      >
      >Gesloten gebruikersgroepen voor de pagina worden gedefinieerd op de **[Machtigingen](#permissions)** tab.

   * **Aanmeldingspagina** - De pagina die moet worden gebruikt voor aanmelding

* **Exporteren**

   * **Configuratie exporteren** - Geeft een exportconfiguratie op

### Miniatuur {#thumbnail}

De paginaminiatuur configureren

* **Voorvertoning genereren** - Genereer een voorvertoning van de pagina die u als miniatuur wilt gebruiken
* **Afbeelding uploaden** - Upload een afbeelding die u als miniatuur wilt gebruiken
* **Afbeelding selecteren** - Selecteer een bestaand element dat u als miniatuur wilt gebruiken
* **Vorige versie** - Deze optie wordt beschikbaar nadat u een wijziging in de miniatuur hebt aangebracht. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Sociale media {#social-media}

* **Delen via sociale media**

   Definieert de opties voor delen die beschikbaar zijn op de pagina. Hiermee geeft u de opties weer die beschikbaar zijn voor de [De kerncomponent delen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/sharing.html).

   * **Delen door gebruikers voor Facebook inschakelen**
   * **Delen door gebruikers voor Pinterest inschakelen**
   * **Voorkeurswijziging XF**
      * De fragmentvariatie definiëren die wordt gebruikt voor het genereren van metagegevens voor de pagina

### Cloud Services {#cloud-services}

* **Configuraties van Cloud Servicen** - Eigenschappen definiëren voor cloudservices

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### Personalisatie {#personalization}

* **ContextHub-configuraties**

   * **ContextHub-pad** - Definieer de [ContextHub-configuratie](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Segmentpad** - Definieer de [Segmentpad](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Doelconfiguratie**

   * **Merk** - Definieert een [Merk om een werkingsgebied voor het richten te specificeren](/help/sites-cloud/authoring/personalization/targeted-content.md).
   >[!NOTE]
   >Deze optie vereist dat de gebruikersaccount zich in de `Target Administrators`groep.

### Machtigingen {#permissions}

* **Machtigingen**

   * Machtigingen toevoegen
   * Gesloten gebruikersgroep bewerken
   * Effectieve machtigingen weergeven

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### Blauwdruk {#blueprint}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die als blauwdrukken fungeren. Blauwdrukken dienen als basis voor Actieve kopieën maken deel uit van [Beheer van meerdere sites.](/help/sites-cloud/administering/msm/overview.md)

* **Huidige actieve kopieën** - Hiermee geeft u pagina&#39;s weer die op deze blauwdrukpagina zijn gebaseerd (dat wil zeggen: Live kopieën van deze pagina zijn)

* **Rollout Configs** - Controleert de omstandigheden waaronder de wijzigingen aan Levende Exemplaar zullen worden verspreid

### Live kopie {#live-copy}

* **Synchroniseren** - Actieve kopie synchroniseren met vervagen, lokale wijzigingen behouden
* **Herstellen** - Actieve kopie opnieuw instellen op de status Vervagen, lokale wijzigingen verwijderen
* **Onderbreken** - Live kopie van verdere rollout-wijzigingen onderbreken
* **Loskoppelen** - Actieve kopie loskoppelen van vervaging

* **Bron**

   * Hiermee geeft u het pad van de blauwdruk voor deze actieve kopie weer

* **Status**

   * Hiermee geeft u de huidige status van Live kopie van de pagina weer

* **Configuratie**

   * **Overerving van Actieve kopie** - Als deze optie is ingeschakeld, is de Live Copy-configuratie effectief voor alle onderliggende toepassingen
   * **Inherit Rollout Configs from Parent** - Als deze optie is ingeschakeld, wordt de rollout-configuratie overgenomen van het bovenliggende item van de pagina
   * **Uitrolconfiguratie kiezen** - Definieert de omstandigheden waaronder wijzigingen via het blauwdruk worden doorgegeven en alleen beschikbaar zijn wanneer **Inherit Rollout Configs from Parent** is niet geselecteerd

### Voorvertoning {#preview}

Wanneer een voorvertoningsomgeving is ingeschakeld, ziet u:

* Voorbeeld-URL - de URL die wordt gebruikt voor toegang tot de inhoud in de voorvertoningsomgeving

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

* Van de **Sites** console:
   * [Een nieuwe pagina maken](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (een subset van de eigenschappen)
   * Klikken of tikken **Eigenschappen**
      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)
* Vanuit de pagina-editor:
   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Vanuit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Klikken of tikken **Eigenschappen** om de pagina-eigenschappen te definiëren:

1. Met de **Sites** navigeer naar de locatie van de pagina waarvan u de eigenschappen wilt weergeven en bewerken.
1. Selecteer **Eigenschappen** optie voor de vereiste pagina met behulp van:
   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * De pagina-eigenschappen worden weergegeven met de juiste tabbladen.
1. Bekijk of bewerk de eigenschappen naar wens.
1. Gebruik vervolgens **Opslaan** om uw updates op te slaan, gevolgd door **Sluiten** om naar de console terug te keren.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer u een pagina bewerkt, kunt u **Pagina-informatie** om de pagina-eigenschappen te definiëren:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.
1. Selecteer **Pagina-informatie** pictogram om het selectiemenu te openen:
1. Selecteer **Eigenschappen openen** en er wordt een dialoogvenster geopend waarin u de eigenschappen kunt bewerken, gesorteerd op het juiste tabblad. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:
   * **Annuleren**
   * **Opslaan en sluiten**
1. Gebruik de **Opslaan en sluiten** om de wijzigingen op te slaan.

### Van de Console van Plaatsen - Meerdere Pagina&#39;s {#from-the-sites-console-multiple-pages}

Vanuit de **Sites**-console kunt u meerdere pagina&#39;s selecteren en vervolgens **Eigenschappen weergeven** gebruiken om de pagina-eigenschappen te bekijken en/of te bewerken. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

>[!NOTE]
>
>Bulkbewerking van eigenschappen is ook beschikbaar voor Elementen. Het is erg vergelijkbaar, maar op een paar punten verschilt het. Zie Eigenschappen van meerdere elementen bewerken voor meer informatie.
>
>Er is ook de Bulk Editor, waarmee u met GQL (Google Query Language) naar inhoud van meerdere pagina&#39;s kunt zoeken en de inhoud vervolgens rechtstreeks in de grote editor kunt bewerken voordat u de wijzigingen opslaat in de oorspronkelijke pagina&#39;s.

<!--
>Bulk editing of properties is also available for Assets. It is very similar, but differs in a few points. See [Editing Properties of Multiple Assets](/help/assets/managing-multiple-assets.md) for details.
>
>There is also the [Bulk Editor](/help/sites-administering/bulk-editor.md), which allows you to search for content from multiple pages using GQL (Google Query Language) and then edit the content directly in the bulk editor before saving your changes to the originating pages.
-->

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Wanneer u door de **Sites** console
* Na gebruik van **Zoeken** om een set pagina&#39;s te zoeken

Nadat u de pagina&#39;s hebt geselecteerd en op de optie **Eigenschappen** hebt geklikt of getikt, worden de bulkeigenschappen weergegeven:

![Pagina-eigenschappen voor bulkbewerking](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* Maakt geen deel uit van een livecopy
   * Als een van de pagina&#39;s zich in een live kopie bevindt, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Nadat u de optie Bulk bewerken hebt ingevoerd, kunt u:

* **Weergave**

   * Een lijst met de betrokken pagina&#39;s
      * U kunt desgewenst selecteren/deselecteren
      * Tabs
         * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.
   * Een subset van eigenschappen
      * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
      * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.
   * Algemene eigenschappen met een gemeenschappelijke waarde
      * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven in de weergavemodus.
      * Als het veld meerdere waarden heeft (bijvoorbeeld Codes), worden waarden alleen weergegeven als *alles* vaak voorkomen. Als slechts enkele van deze voorbeelden algemeen zijn, worden deze alleen weergegeven tijdens het bewerken.
      * Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **Bewerken**

   * U kunt de waarden in de beschikbare velden bijwerken.
      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed**.
      * Wanneer het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.
   * Velden die veel voorkomen, maar verschillende waarden op de verschillende pagina&#39;s hebben, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>`. Bij het bewerken van dergelijke velden moet de nodige aandacht worden besteed om gegevensverlies te voorkomen.

>[!NOTE]
>
>De paginacomponent kan worden gevormd om de gebieden te specificeren beschikbaar voor bulkbewerking. Zie Uw pagina configureren voor bulkbewerking van pagina-eigenschappen.

<!--
>The page component can be configured to specify the fields available for bulk editing. See [Configuring your page for bulk editing of page properties](/help/sites-developing/bulk-editing.md).
-->
