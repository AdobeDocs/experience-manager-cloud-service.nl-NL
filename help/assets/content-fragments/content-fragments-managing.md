---
title: Inhoudsfragmenten beheren (Assets - Inhoudsfragmenten)
description: Leer hoe u de Assets-console gebruikt om uw AEM Content Fragments te beheren, als de basis van uw inhoud zonder kop of voor het ontwerpen van pagina's.
exl-id: 333ad877-db2f-454a-a3e5-59a936455932
feature: Content Fragments
role: User, Admin
solution: Experience Manager Sites
source-git-commit: 74e2f015d6bcb36505c2dc6471bb68d69d98db99
workflow-type: tm+mt
source-wordcount: '1925'
ht-degree: 4%

---

# Inhoudsfragmenten beheren {#managing-content-fragments}

Leer hoe u de Assets-console gebruikt om uw AEM Content Fragments te beheren, als de basis van uw inhoud zonder kop of voor het ontwerpen van pagina&#39;s.

Na het bepalen van uw [ Modellen van het Fragment van de Inhoud ](#creating-a-content-model) kunt u deze gebruiken om [ uw Fragmenten van de Inhoud ](#creating-a-content-fragment) tot stand te brengen.

De [ Redacteur van het Fragment van de Inhoud ](#opening-the-fragment-editor) verstrekt diverse [ wijzen ](#modes-in-the-content-fragment-editor) om u toe te laten:

* [ geeft de inhoud ](#editing-the-content-of-your-fragment) uit en [ leidt Variaties ](#creating-and-managing-variations-within-your-fragment)
* [Uw fragment notities aanbrengen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Inhoud koppelen aan uw fragment](#associating-content-with-your-fragment)
* [De metagegevens configureren](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [De boomstructuur weergeven](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Voorvertoning van de JSON-representatie](/help/assets/content-fragments/content-fragments-json-preview.md)


>[!NOTE]
>
>Inhoudsfragmenten kunnen worden gebruikt:
>
>* wanneer het ontwerpen van pagina&#39;s; zie [ het Authoring van de Pagina met de Fragmenten van de Inhoud ](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* voor [ Hoofdloze Levering van de Inhoud gebruikend de Fragmenten van de Inhoud met GraphQL ](/help/assets/content-fragments/content-fragments-graphql.md).

>[!NOTE]
>
>De Fragmenten van de inhoud zijn a **eigenschap van de Plaatsen**, maar worden opgeslagen als **Assets**.
>
>Zij worden hoofdzakelijk geleid met de **[console van de Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)**, hoewel zij nog van de **[Assets](/help/assets/content-fragments/content-fragments-managing.md)** console kunnen worden beheerd.
>
>Er zijn twee redacteurs voor het ontwerpen van de Fragmenten van de Inhoud - de nieuwe redacteur en de originele redacteur. De nieuwe redacteur is het gebrek. Hoewel de basisfunctionaliteit hetzelfde is, zijn er enkele verschillen.
>
>In deze sectie wordt de oorspronkelijke editor beschreven.
>
>De standaardeditor voor [ Fragmenten van de Inhoud - Authoring ](/help/sites-cloud/administering/content-fragments/authoring.md) is de nieuwe redacteur, die van zowel de **3&rbrace; console van de Fragmenten van de Inhoud** als de **Assets** console wordt betreden. Zie de documentatie van Plaatsen, [ de Fragmenten van de Inhoud - Authoring ](/help/sites-cloud/administering/content-fragments/authoring.md), voor details van de nieuwe redacteur.
>
>Om de [ originele redacteur ](/help/assets/content-fragments/content-fragments-variations.md) te gebruiken, open eerst de nieuwe redacteur en deactiveer dan de **Nieuwe redacteur** schakelaar.
>
>Beide editors hebben een knevelschakelaar in de hoogste toolbar om snelle toegang tot de andere redacteur te verlenen.

## Inhoudsfragmenten maken {#creating-content-fragments}

### Een inhoudsmodel maken {#creating-a-content-model}

[ de fragmentmodellen van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) kunnen worden toegelaten en worden gecreeerd, voorafgaand aan het creëren van inhoudsfragmenten met gestructureerde inhoud.

### Een inhoudsfragment maken {#creating-a-content-fragment}

De methode voor het maken van een inhoudsfragment is:

1. Ga naar de map **Assets** waar u het fragment wilt maken.
1. Selecteer **Maken** en vervolgens **Inhoudsfragment** om de wizard te openen.
1. In de eerste stap van de wizard moet u de basis van het nieuwe fragment opgeven.

   * [ Model ](/help/assets/content-fragments/content-fragments-models.md) - gebruikt om een fragment tot stand te brengen dat gestructureerde inhoud vereist; bijvoorbeeld, het **Adventure** model

      * Alle beschikbare modellen worden weergegeven.

   Na selectie, gebruik **daarna** te werk te gaan.

   ![ Uitgezochte Model van het Fragment van de Inhoud ](assets/cfm-managing-01.png)

1. Geef in de stap **Eigenschappen** het volgende op:

   * **Basis**

      * **Titel**

        De fragmenttitel.

        Verplicht.

      * **Beschrijving**

      * **Markeringen**

   * **Geavanceerd**

      * **Naam**

        De naam; wordt gebruikt om de URL te vormen.

        Verplicht; wordt automatisch afgeleid van de titel, maar kan worden bijgewerkt.

1. Selecteer **Maken** om de actie te voltooien en **open** vervolgens het fragment voor het bewerken of keer terug naar de console met **Gereed**.

   >[!NOTE]
   >Op **Lijst** wijze van de console kunt u de **Montages van de Mening** bijwerken om de **Model van het Fragment van de Inhoud** kolom toe te laten.

## Handelingen voor een inhoudsfragment in de Assets-console {#actions-for-a-content-fragment-assets-console}

In de **Assets** console is een waaier van acties beschikbaar voor uw inhoudsfragmenten, of:

* Vanuit de werkbalk; nadat u het fragment hebt geselecteerd, zijn alle relevante handelingen beschikbaar.
* Als [ snelle acties ](/help/sites-cloud/authoring/basic-handling.md#quick-actions); een ondergroep acties beschikbaar voor de individuele fragmentkaarten.

![ Acties in toolbar ](assets/cfm-managing-02.png)

Selecteer het fragment om de werkbalk weer te geven met de toepasselijke acties:

* **opnieuw verwerken Assets**
* **creeer**
* **Download**

   * Sla het fragment op als een ZIP-bestand. U kunt opgeven of u elementen, variaties of metagegevens wilt opnemen.

* **Controle**
* **Eigenschappen**

   * Hiermee kunt u de metagegevens van het fragment weergeven, bewerken of beide.

* **geeft** uit

   * Laat u [ het fragment voor het uitgeven van inhoud ](/help/assets/content-fragments/content-fragments-variations.md) samen met zijn elementen, variaties, bijbehorende inhoud en meta-gegevens openen.

* **Snel publiceren**
* **beheer Publicatie**
* **beheert Markeringen**
* **aan Inzameling**
* **Exemplaar** (en **Deeg**)
* **Beweging**
* **Schrapping**

>[!NOTE]
>
>Veel van deze zijn [ standaardacties voor Assets ](/help/assets/manage-digital-assets.md) en/of [ Desktop app van AEM ](https://helpx.adobe.com/nl/experience-manager/desktop-app/aem-desktop-app.html).

## De fragmenteditor openen {#opening-the-fragment-editor}

U opent als volgt het fragment voor bewerking in de oorspronkelijke editor:

>[!CAUTION]
>
>Om een inhoudsfragment uit te geven hebt u [ de aangewezen toestemmingen ](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions) nodig. Neem contact op met de systeembeheerder als er problemen optreden.

1. Ga naar de locatie van het inhoudsfragment.

1. Open het fragment om het te bewerken.

1. Het fragment wordt geopend in de nieuwe editor. Deactiveer de **Nieuwe schakelaar van de Redacteur** (hoogste recht) om de originele redacteur te openen:

   ![ de redacteur van het Fragment ](assets/cfm-managing-03.png)

1. Breng de gewenste wijzigingen aan.

1. Wanneer klaar, gebruik **sparen**, **sparen en sluit** of **dicht** zoals vereist.

   >[!NOTE]
   >
   >**sparen &amp; sluit** is beschikbaar als **sparen** drop-down lijst.

   >[!NOTE]
   >
   >Zowel **sparen &amp; dicht** en **dicht** zullen de redacteur weggaan - zie [ sparen, dicht en Versies ](#save-close-and-versions) voor volledige informatie over hoe de diverse opties voor inhoudsfragmenten werken.

## Modi en handelingen in de Inhoudsfragmenteditor {#modes-actions-content-fragment-editor}

Er zijn verschillende modi en acties beschikbaar in de Inhoudsfragmenteditor.

### Modi in de Content Fragment Editor {#modes-in-the-content-fragment-editor}

Navigeer door de verschillende modi met de pictogrammen in het zijpaneel:

* Variaties: [ het uitgeven van de inhoud ](#editing-the-content-of-your-fragment) en [ het Leiden uw Variaties ](#creating-and-managing-variations-within-your-fragment)

* [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Gekoppelde inhoud](#associating-content-with-your-fragment)
* [Metagegevens](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [Boomstructuur](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Voorvertoning](/help/assets/content-fragments/content-fragments-json-preview.md)

![ Wijzen in de redacteur van het Fragment van de Inhoud ](assets/cfm-managing-04.png)

### Werkbalkhandelingen in de Inhoudsfragmenteditor {#toolbar-actions-in-the-content-fragment-editor}

Sommige functies in de bovenste werkbalk zijn beschikbaar in meerdere modi:

{de acties van 0} Toolbar beschikbaar in diverse wijzen ![&#128279;](assets/cfm-managing-top-toolbar.png)

* Er wordt een bericht weergegeven wanneer er al naar het fragment wordt verwezen op een inhoudspagina. U kunt **sluiten** het bericht.

* Het zijpaneel kan worden verborgen/getoond gebruikend het **pictogram van de Kant van de Knevel**.

* Onder de fragmentnaam kunt u de naam van het [ Model van het Fragment van de Inhoud zien ](/help/assets/content-fragments/content-fragments-models.md) dat voor het creëren van het huidige fragment wordt gebruikt:

   * De naam is ook een verbinding die de modelredacteur opent.

* Zie de status van het fragment, bijvoorbeeld informatie over wanneer het is gemaakt, gewijzigd of gepubliceerd. De status heeft ook een kleurcode:

   * **Nieuw**: grijs
   * **Ontwerp**: blauw
   * **Gepubliceerd**: groen
   * **Gewijzigd**: oranje
   * **Gedeactiveerd**: rood

* Een knoop laat u toe om **Nieuwe Redacteur** uit te proberen, door *nieuwe* [ Redacteur van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/authoring.md) direct te openen die via de [ console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console) toegankelijk is.

  >[!WARNING]
  >
  >De nieuwe editor wordt op hetzelfde tabblad geopend. Het wordt afgeraden beide editors tegelijk te openen.

* **sparen** verleent toegang tot **sparen &amp; sluit** optie.

* De drie punts (**..**) drop-down verleent toegang tot extra acties:
   * **de paginaverwijzingen van de Update**
      * Hiermee werkt u alle paginaverwijzingen bij.
   * **[Snel publiceren](#publishing-and-referencing-a-fragment)**
   * **[beheer Publicatie](#publishing-and-referencing-a-fragment)**

<!--
This updates any page references and ensures that the Dispatcher is flushed as required. -->

## Opslaan, sluiten en versies {#save-close-and-versions}

>[!NOTE]
>
>De versies kunnen ook [ worden gecreeerd, worden vergeleken en van de Chronologie ](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) worden teruggedraaid.

De editor heeft verschillende opties:

* **sparen** en **sparen &amp; sluit**

   * **sparen** zal de recentste veranderingen bewaren en in de redacteur blijven.
   * **sparen &amp; sluit** zal de recentste veranderingen bewaren en de redacteur weggaan.

  >[!CAUTION]
  >
  >Om een inhoudsfragment uit te geven hebt u [ de aangewezen toestemmingen ](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions) nodig. Neem contact op met de systeembeheerder als er problemen optreden.

  >[!NOTE]
  >
  >Het is mogelijk om in de redacteur te blijven, makend een reeks veranderingen, alvorens te bewaren.

  >[!CAUTION]
  >
  >Naast het eenvoudig opslaan van uw wijzigingen, werken de acties ook alle verwijzingen bij en zorgen ze ervoor dat de Dispatcher naar wens wordt leeggemaakt. Deze wijzigingen kunnen enige tijd in beslag nemen. Daarom kan de prestaties van een groot/complex/zwaar geladen systeem worden beïnvloed.
  >
  >Houd dit proces in mening wanneer het gebruiken van **sparen &amp; sluit** en dan snel het opnieuw ingaan van de fragmentredacteur om meer veranderingen aan te brengen en te bewaren.

* **dicht**

  Zal de redacteur weggaan zonder de recentste veranderingen (dat wordt gemaakt sinds laatste **sparen**) op te slaan.

Terwijl het uitgeven van uw inhoudsfragment maakt AEM automatisch versies om ervoor te zorgen dat de vroegere inhoud kan worden hersteld als u uw veranderingen annuleert (gebruikend **dicht** zonder sparen):

1. Wanneer een inhoudsfragment voor het uitgeven van AEM controles op het bestaan van het op koekje-gebaseerde teken wordt geopend dat erop wijst of een *het uitgeven zitting* bestaat:

   1. Als het token wordt gevonden, wordt het fragment beschouwd als onderdeel van de bestaande bewerkingssessie.
   2. Als het teken *niet* beschikbaar is en de gebruiker begint inhoud uit te geven, wordt een versie gecreeerd en een teken voor deze nieuwe het uitgeven zitting wordt verzonden naar de cliënt, waar het in een koekje wordt bewaard.

2. Terwijl er een *actieve* het uitgeven zitting is, wordt de inhoud die automatisch bewaard om de 600 seconden (gebrek) wordt.

   >[!NOTE]
   >
   >Het interval voor automatisch opslaan kan worden geconfigureerd met het mechanisme `/conf` .
   >
   >Standaardwaarde, zie:
   >  `/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

3. Als de gebruiker de bewerking annuleert, wordt de versie die aan het begin van de bewerkingssessie is gemaakt, hersteld en wordt de token verwijderd om de bewerkingssessie te beëindigen.
4. Als de gebruiker **&#x200B;**&#x200B;selecteert sparen uitgeeft, blijven de bijgewerkte elementen/de variaties voortbestaan en het teken wordt verwijderd om de het uitgeven zitting te beëindigen.

## De inhoud van het fragment bewerken {#editing-the-content-of-your-fragment}

Zodra u uw fragment hebt geopend, kunt u het [ lusje van Variaties ](/help/assets/content-fragments/content-fragments-variations.md) gebruiken om uw inhoud te schrijven.

## Variaties maken en beheren in uw fragment {#creating-and-managing-variations-within-your-fragment}

Zodra u de Hoofdinhoud hebt gecreeerd, kunt u, [ Variaties ](/help/assets/content-fragments/content-fragments-variations.md) van die inhoud tot stand brengen en leiden.

## Inhoud koppelen aan uw fragment {#associating-content-with-your-fragment}

U kunt [ inhoud ](/help/assets/content-fragments/content-fragments-assoc-content.md) met een fragment ook associëren. Dit biedt een verbinding zodat elementen (dat wil zeggen afbeeldingen) (optioneel) met het fragment kunnen worden gebruikt wanneer het aan een inhoudspagina wordt toegevoegd.

## De metagegevens (eigenschappen) van het fragment weergeven en bewerken {#viewing-and-editing-the-metadata-properties-of-your-fragment}

U kunt, de eigenschappen van een fragment bekijken en uitgeven gebruikend het [ Meta-gegevens ](/help/assets/content-fragments/content-fragments-metadata.md) lusje.

## Tijdlijn voor inhoudsfragmenten {#timeline-for-content-fragments}

Naast de standaardopties, [ verstrekt de Chronologie ](/help/assets/manage-digital-assets.md#timeline) zowel informatie als acties specifiek voor inhoudsfragmenten:

* Informatie weergeven over versies, opmerkingen en annotaties
* Handelingen voor versies

   * **[keert aan deze Versie](#reverting-to-a-version)** terug (selecteer een bestaand fragment, toen een specifieke versie)

   * **[vergelijk met Huidige](#comparing-fragment-versions)** (selecteer een bestaand fragment, toen een specifieke versie)

   * Voeg a **Etiket** en/of **Commentaar** toe (selecteer een bestaand fragment, toen een specifieke versie)

   * **sparen als Versie** (selecteer een bestaand fragment, dan omhoog pijl bij de bodem van Chronologie)

* Handelingen voor annotaties

   * **Schrapping**

>[!NOTE]
>
>Opmerkingen zijn:
>
>* Standaardfunctionaliteit voor alle elementen
>* Gemaakt in tijdlijn
>* Verwant aan het fragmentelement
>
>Annotaties (voor inhoudsfragmenten) zijn:
>
>* Opgegeven in de fragmenteditor
>* Specifiek voor een geselecteerd tekstsegment binnen het fragment
>
>Noch toon de commentaren ingegaan in de nieuwe [ redacteur van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/authoring.md#commenting-on-your-fragment).

Bijvoorbeeld:

![ Chronologie ](assets/cfm-managing-05.png)

## Fragmentversies vergelijken {#comparing-fragment-versions}

**vergelijk met Huidige** actie is beschikbaar bij de [ Chronologie ](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) nadat u een specifieke versie hebt geselecteerd.

Dit wordt geopend:

* de **Huidige** (recentste) versie (verlaten)

* de geselecteerde versie **v&lt; *x.y* >** (juist)

Zij worden naast elkaar getoond, waarbij:

* Eventuele verschillen worden gemarkeerd

   * Verwijderde tekst - rood
   * Ingevoegde tekst - groen
   * Vervangen tekst - blauw

* Met het pictogram voor volledig scherm kunt u een van beide versies afzonderlijk openen en vervolgens terugschakelen naar de parallelle weergave
* U kunt **terugkeren** aan de specifieke versie
* **Gedaan** zal u aan de console terugkeren

>[!NOTE]
>
>U kunt de fragmentinhoud niet bewerken wanneer u fragmenten vergelijkt.

![ vergelijkend Variaties ](assets/cfm-managing-06.png)

## Een versie herstellen  {#reverting-to-a-version}

U kunt terugkeren naar een specifieke versie van het fragment:

* Direct van de [ Chronologie ](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

  Selecteer de vereiste versie, dan terugkeren **aan deze** actie van Versie.

* Terwijl [ het vergelijken van een versie aan de huidige versie ](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) u **&#x200B;**&#x200B;aan de geselecteerde versie kunt terugkeren.

## Een fragment publiceren en ernaar verwijzen {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Als uw fragment op een model gebaseerd is, dan zou u moeten ervoor zorgen dat het [ model ](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model) is gepubliceerd.
>
>Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, wordt dit in een selectielijst aangegeven en wordt het model met het fragment gepubliceerd.

Inhoudsfragmenten moeten worden gepubliceerd voor gebruik in de publicatieomgeving. Dit gebeurt met de standaard Assets-functionaliteit:

* [Snel publiceren](/help/assets/manage-publication.md#quick-publish)
* [ beheer Publicatie ](/help/assets/manage-publication.md#manage-publication)

Dit is toegankelijk:

* Na verwezenlijking; het gebruiken van [ acties beschikbaar in de console van Assets ](#actions-for-a-content-fragment-assets-console).
* Van de [ Redacteur van het Fragment van de Inhoud ](#toolbar-actions-in-the-content-fragment-editor).

Bovendien wanneer u [ een pagina publiceert die het fragment ](/help/sites-cloud/authoring/fragments/content-fragments.md#publishing) gebruikt; het fragment is vermeld in de paginaverwijzingen.

>[!CAUTION]
>
>Nadat een fragment is gepubliceerd en/of waarnaar wordt verwezen, geeft AEM een waarschuwing weer wanneer een auteur het fragment opent voor opnieuw bewerken. Hiermee wordt u gewaarschuwd dat wijzigingen in het fragment ook van invloed zijn op de pagina&#39;s waarnaar wordt verwezen.

## Een fragment verwijderen {#deleting-a-fragment}

Een fragment verwijderen:

1. In de **Assets** console navigeert aan de plaats van het inhoudsfragment.
2. Selecteer het fragment.

   >[!NOTE]
   >
   >De **schrapping** actie is niet beschikbaar als snelle actie.

3. Selecteer **Schrapping** van de toolbar.
4. Bevestig **schrapping** actie.

   >[!CAUTION]
   >
   >Als er al naar het fragment wordt verwezen op een pagina, wordt er een waarschuwingsbericht weergegeven en moet u bevestigen dat u wilt doorgaan met **Verwijderen forceren**. Het fragment wordt samen met de bijbehorende component voor inhoudsfragmenten verwijderd uit alle inhoudspagina&#39;s.
