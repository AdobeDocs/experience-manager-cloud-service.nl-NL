---
title: Pagina-eigenschappen bewerken
description: De vereiste eigenschappen voor een pagina definiëren
translation-type: tm+mt
source-git-commit: c3fd7b5a6311eded51b13ab9fea1ca6af4a050eb
workflow-type: tm+mt
source-wordcount: '1894'
ht-degree: 5%

---


# Pagina-eigenschappen bewerken {#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is beschikbaar, indien van toepassing.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Standaard {#basic}

* **Titel en tags**

   * **Titel**  - De titel van de pagina wordt op verschillende plaatsen getoond. Bijvoorbeeld de **Tablijst Websites** en de **Kaart/lijstweergaven van** Sites.
      * Dit is een verplicht veld.
   * **Tags**  - Hier kunt u codes aan de pagina toevoegen of eruit verwijderen door de lijst in het selectievak bij te werken.
      * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
      * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.
         * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
         * De nieuwe tag wordt dan weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.
      * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
      * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.
      * Zie [Codes gebruiken](/help/sites-cloud/authoring/features/tags.md) voor meer informatie over tags.
   * **Verbergen in navigatie**  - Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site.

* **Branding**

   Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Voor deze functionaliteit is het gebruik van de paginacomponent vanaf versie 2.14.0 of hoger van de [kerncomponenten vereist.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

   * **Overschrijven**  - Schakel deze optie in om de witruimte op deze pagina te definiëren.
      * De waarde wordt overgeërfd door onderliggende pagina&#39;s, tenzij de waarden **Override** zijn ingesteld.
   * **Waarde**  overschrijven - De tekst van de gloedmarkering die aan de paginatitel moet worden toegevoegd.
      * De waarde wordt toegevoegd aan de paginatitel na een pipe-teken, zoals &quot;Cycling Tuscany&quot; | Altijd klaar voor de WKND&quot;

* **HTML-id**

   * **ID**  - HTML-id die moet worden toegepast op de component.

* **Meer titels en beschrijving**

   * **Paginatitel**  - Een titel die op de pagina moet worden gebruikt. Wordt meestal gebruikt door titelcomponenten. Als de **Titel** leeg is, wordt deze gebruikt.
   * **Navigatitel**  - U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Als dit leeg is, wordt **Title** gebruikt.
   * **Ondertitel**  - Een ondertitel voor gebruik op de pagina.
   * **Beschrijving**  - Uw beschrijving van de pagina, het doel of andere details die u wilt toevoegen.

* **Aan/Uit-tijd**

   * **Op tijd**  - De datum en het tijdstip waarop de gepubliceerde pagina zichtbaar wordt gemaakt (weergegeven) in de publicatieomgeving. De pagina moet, of manueel of door pre-gevormde auto-replicatie worden gepubliceerd.

      >[!NOTE]
      >
      > Zie [On and Off Times - Trigger Configuration](/help/operations/replication.md#on-and-off-times-trigger-configuration) voor details van hoe te om de verwante automatische replicatie te vormen.

      * Als deze pagina al [gepubliceerd (handmatig)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) is, blijft deze slapend (verborgen) totdat deze op het opgegeven tijdstip wordt weergegeven.
      * Als niet gepubliceerd, en gevormd voor auto-replicatie, zal de pagina automatisch worden gepubliceerd, dan, op de gespecificeerde tijd teruggegeven.
      * Als niet gepubliceerd, en niet gevormd voor auto-replicatie, zal de pagina niet automatisch gepubliceerd worden, zodat zal 404 worden gezien wanneer een poging om tot de pagina toegang te hebben wordt gemaakt.
   * **Off Time**  - Net als en vaak gebruikt in combinatie met  **On Time**, bepaalt dit de tijd waarop de gepubliceerde pagina wordt verborgen in de publicatieomgeving.

   * Laat deze velden (**On Time** en **Off Time**) leeg voor pagina&#39;s die u direct wilt publiceren en die beschikbaar zijn in de publicatieomgeving totdat ze zijn gedeactiveerd (het normale scenario).


* **Vanity URL**

   * Hiermee kunt u een vanity-URL voor deze pagina invoeren, waarmee u een kortere en/of expressieve URL kunt hebben.
   * Als de URL vanity bijvoorbeeld is ingesteld op `welcome` op de pagina die wordt aangegeven door het pad `/v1.0/startpage` voor de website `http://example.com`, is `http://example.com/welcome` de vanity URL van `http://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Vanity-URL&#39;s:
   >
   >* Dit moet uniek zijn, dus zorg ervoor dat de waarde niet al door een andere pagina wordt gebruikt.
   >* Geen ondersteuning voor regex-patronen.
   >* Deze mag niet op een bestaande pagina worden ingesteld.


   * **Voeg toe**  - Tik of klik om een gebied te tonen om een vanity URL voor de pagina te bepalen.
      * Tik of klik nogmaals om meerdere items toe te voegen.
      * Tik of klik op het pictogram **Verwijderen** om de vanity URL te verwijderen.
   * **Redirect Vanity URL**  - Geeft aan of de pagina de vanity URL moet gebruiken.




### Geavanceerd {#advanced}

* **Instellingen**

   * **Taal**  - De paginataal
   * **Hoofdmap**  van taal - Moet worden gecontroleerd als de pagina de basis is van een taalkopie
   * **Omleiden**  - Geeft de pagina aan waarnaar deze pagina automatisch moet worden omgeleid
   * **Ontwerp**  - Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site
   * **Alias**  - Geeft een alias op die voor deze pagina moet worden gebruikt

   >[!NOTE]
   >
   >Alias plaatst het `sling:alias` bezit om een alias naam voor het middel te bepalen (dit beïnvloedt slechts het middel, niet de weg).
   >
   >Bijvoorbeeld: als u een alias van `latin-lang` voor de knoop `/content/we-retail/spanish` bepaalt, dan kan deze pagina via `/content/we-retail/latin-language` worden betreden
   >
   >Zie Gelokaliseerde paginanamen onder SEO en URL Management Best Practices voor meer informatie.

   <!--
  >For further details see [Localized page names under SEO and URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names).
  -->

* **Configuratie**

   * **Cloudconfiguratie** : het pad naar de configuratie

* **Sjablooninstellingen**

   * **Toegestane Malplaatjes**  -  [bepaalt de lijst van malplaatjes die binnen deze subtak ](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) beschikbaar zullen zijn

* **Verificatievereiste**

   * **Inschakelen**  - Het gebruik van verificatie inschakelen voor toegang tot de pagina

      >[!NOTE]
      >
      >Gesloten gebruikersgroepen voor de pagina worden gedefinieerd op het tabblad **[Machtigingen](#permissions)**.

   * **Aanmeldingspagina**  - De pagina die moet worden gebruikt voor aanmelding

* **Exporteren**

   * **Configuratie**  exporteren - Geeft een exportconfiguratie op

### Miniatuur {#thumbnail}

De paginaminiatuur configureren

* **Voorvertoning**  genereren - Een voorbeeld van de pagina genereren om als miniatuur te gebruiken
* **Afbeelding**  uploaden - Een afbeelding uploaden om als miniatuur te gebruiken
* **Afbeelding**  selecteren - Selecteer een bestaand element dat u als miniatuur wilt gebruiken
* **Vorige versie**  - Deze optie wordt beschikbaar nadat u de miniatuur hebt gewijzigd. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Sociale media {#social-media}

* **Delen via sociale media**

   Definieert de opties voor delen die beschikbaar zijn op de pagina. Hiermee geeft u de opties weer die beschikbaar zijn voor [De kerncomponent delen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/sharing.html).

   * **Delen door gebruikers voor Facebook inschakelen**
   * **Gebruikersdeling inschakelen voor Pinterest**
   * **Voorkeurswijziging XF**
      * De fragmentvariatie definiëren die wordt gebruikt voor het genereren van metagegevens voor de pagina

### Cloud Services {#cloud-services}

* **Configuraties**  van Cloud Servicen - Eigenschappen voor cloudservices definiëren

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### Personalisatie {#personalization}

* **ContextHub-configuraties**

   * **ContextHub Path**  - bepaal de configuratie  [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Segmentpad**  - Het pad  [Segmenten definiëren](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Doelconfiguratie**

   * **Merk**  - bepaalt een  [Merk om een werkingsgebied voor het richten](/help/sites-cloud/authoring/personalization/targeted-content.md) te specificeren.
   >[!NOTE]
   >Voor deze optie moet de gebruikersaccount deel uitmaken van de `Target Administrators`groep.

### Machtigingen {#permissions}

* **Machtigingen**

   * Machtigingen toevoegen
   * Gesloten gebruikersgroep bewerken
   * Effectieve machtigingen weergeven

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### Blauwdruk {#blueprint}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die als blauwdrukken fungeren.

* **Huidige actieve kopieën**  - Hiermee geeft u pagina&#39;s weer die op deze blauwdrukpagina zijn gebaseerd (dat wil zeggen, Live kopieën van deze pagina zijn)

   <!--Define properties for a Blueprint page within [multi-site management](/help/sites-administering/msm.md).-->
* **De Vormen**  van de rollout - controleert de omstandigheden waaronder de wijzigingen aan Levende Exemplaar zullen worden verspreid

### Live kopie {#live-copy}

* **Synchroniseren**  - Actieve kopie synchroniseren met vervagen, lokale wijzigingen behouden
* **Herstellen**  - Actieve kopie opnieuw instellen op de status Vervagen, lokale wijzigingen verwijderen
* **Onderbreken**  - Live kopie onderbreken bij verdere rollout-wijzigingen
* **Loskoppelen**  - Live kopie loskoppelen van vervaging

* **Bron**

   * Hiermee geeft u het pad van de blauwdruk voor deze actieve kopie weer

* **Status**

   * Hiermee geeft u de huidige status van Live kopie van de pagina weer

* **Configuratie**

   * **Overerving**  van Actieve kopie - Als deze optie is ingeschakeld, is de configuratie van Live Copy effectief voor alle onderliggende elementen
   * **Als dit selectievakje is ingeschakeld, worden de rollout-configuratie overgenomen van het bovenliggende element** .
   * **Kies Rollout Config**  - bepaalt de omstandigheden waaronder de wijzigingen van de Vervaging en slechts beschikbaar zullen worden verspreid wanneer de  **Inherit Uitvoer van** Parentis niet wordt geselecteerd

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

* Vanuit de **Sites**-console:
   * [Een nieuwe pagina](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page)  maken (een subset van de eigenschappen)
   * **Eigenschappen** klikken of tikken
      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)
* Vanuit de pagina-editor:
   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Uit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Klik op **Eigenschappen** of tikken om de pagina-eigenschappen te definiëren:

1. Navigeer met de console **Sites** naar de locatie van de pagina waarvoor u eigenschappen wilt weergeven en bewerken.
1. Selecteer de optie **Eigenschappen** voor de vereiste pagina met behulp van:
   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * De pagina-eigenschappen worden weergegeven met de juiste tabbladen.
1. Bekijk of bewerk de eigenschappen naar wens.
1. Gebruik vervolgens **Opslaan** om uw updates op te slaan, gevolgd door **Close** om terug te keren naar de console.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer u een pagina bewerkt, kunt u **Pagina-informatie** gebruiken om de pagina-eigenschappen te definiëren:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.
1. Selecteer het pictogram **Pagina-informatie** om het selectiemenu te openen:
1. Selecteer **Eigenschappen openen** en er wordt een dialoogvenster geopend waarin u de eigenschappen kunt bewerken, gesorteerd op het juiste tabblad. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:
   * **Annuleren**
   * **Opslaan en sluiten**
1. Met de knop **Opslaan en sluiten** kunt u de wijzigingen opslaan.

### Uit de siteconsole - Meerdere pagina&#39;s {#from-the-sites-console-multiple-pages}

Vanuit de **Sites**-console kunt u meerdere pagina&#39;s selecteren en vervolgens **Eigenschappen weergeven** gebruiken om de pagina-eigenschappen te bekijken en/of te bewerken. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

>[!NOTE]
>
>Bulkbewerking van eigenschappen is ook beschikbaar voor Elementen. Het is erg vergelijkbaar, maar op een paar punten verschilt het. Zie Eigenschappen van meerdere elementen bewerken voor meer informatie.
>
>Er is ook de Bulk Editor, waarmee u met GQL (Google Query Language) naar inhoud op meerdere pagina&#39;s kunt zoeken en de inhoud vervolgens rechtstreeks in de bulkeditor kunt bewerken voordat u de wijzigingen op de pagina&#39;s die beginnen opslaat.

<!--
>Bulk editing of properties is also available for Assets. It is very similar, but differs in a few points. See [Editing Properties of Multiple Assets](/help/assets/managing-multiple-assets.md) for details.
>
>There is also the [Bulk Editor](/help/sites-administering/bulk-editor.md), which allows you to search for content from multiple pages using GQL (Google Query Language) and then edit the content directly in the bulk editor before saving your changes to the originating pages.
-->

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Tijdens het bladeren door de **Sites** console
* Nadat u **Zoeken** hebt gebruikt om een set pagina&#39;s te zoeken

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
      * Als het veld meerdere waarden heeft (bijvoorbeeld Tags), worden waarden alleen weergegeven als *all* algemeen zijn. Als slechts enkele van deze voorbeelden algemeen zijn, worden deze alleen weergegeven tijdens het bewerken.
      * Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **Bewerken**

   * U kunt de waarden in de beschikbare velden bijwerken.
      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Done** selecteert.
      * Wanneer het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.
   * Velden die algemeen zijn, maar verschillende waarden hebben op de verschillende pagina&#39;s, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>`. Bij het bewerken van dergelijke velden moet de nodige aandacht worden besteed om gegevensverlies te voorkomen.

>[!NOTE]
>
>De paginacomponent kan worden gevormd om de gebieden te specificeren beschikbaar voor bulkbewerking. Zie Uw pagina configureren voor bulkbewerking van pagina-eigenschappen.

<!--
>The page component can be configured to specify the fields available for bulk editing. See [Configuring your page for bulk editing of page properties](/help/sites-developing/bulk-editing.md).
-->
