---
title: Contentfragmenten
description: Met Adobe Experience Managers als Cloud Service Content Fragments kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en gebruiken
translation-type: tm+mt
source-git-commit: 5d72645aa3a5296e7b616101955734f03425ab59
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 5%

---


# Contentfragmenten {#content-fragments}

Inhoudsfragmenten in Adobe Experience Manager (AEM) als Cloud Service worden [gemaakt en beheerd als pagina-onafhankelijke elementen](/help/assets/content-fragments/content-fragments.md).

U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

Samen met de bijgewerkte JSON-exportfunctie kunnen gestructureerde inhoudsfragmenten ook worden gebruikt om AEM-inhoud via Content Services te leveren aan andere kanalen dan AEM-pagina&#39;s.

>[!NOTE]
>
>**Inhoudsfragmenten** en **[ervaringsfragmenten](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)**zijn verschillende functies in AEM:
>
>* **Inhoudsfragmenten** zijn redactionele inhoud, voornamelijk tekst en verwante afbeeldingen. Het zijn pure inhoud, zonder ontwerp en lay-out.
>* **De Fragmenten** van de ervaring zijn volledig opgemaakt inhoud en zo fragmenten van een Web-pagina.
>
>
De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.

>[!CAUTION]
>
>Deze pagina moet worden gelezen in combinatie met [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) (en verwante pagina&#39;s), omdat deze de basisterminologie en -concepten introduceert en fragmenten maakt en beheert.

Met de inhoudsfragmenten kunt u:

* **Marketings- en Campagne-strategie**
   * Inhoud controleren via centraal beheerde inhoudsfragmenten.
* **Creative Pro**
   * Het bijhouden van creatieve elementen via verzamelingen die zijn gekoppeld aan inhoudsfragmenten.
* **Schrijvers kopiëren**
   * Schrijf in de fragmenteditor voor AEM-inhoud.
   * Kan inhoudvariaties maken.
   * Kan relevante inhoud aan het inhoudsfragment koppelen.
   * Kan versioning/workflow gebruiken.
   * Kan inhoudsfragment delen.
   * Kan vertalingen centraal beheren.
* **Producenten en journalisten**
   * Maak een keuze uit vooraf gedefinieerde fragmenten en variaties bij het ontwerpen in AEM.
   * Kan erop vertrouwen dat het fragment en de bijbehorende inhoud altijd up-to-date zijn terwijl kopieerschrijvers en -creatieven hun updates in centraal beheerde fragmenten en elementen maken.
   * Kan voor relevantie vertrouwen op gekoppelde media-inhoud die wordt verwerkt.
   * U kunt ad-hocinhoudvariaties maken terwijl u er toch voor zorgt dat deze variaties centraal worden beheerd in het fragment.

## Een inhoudsfragment toevoegen aan uw pagina {#adding-a-content-fragment-to-your-page}

1. Open de pagina om deze te bewerken.
2. Voeg de component **Inhoudsfragment** toe. vanuit de browser **Components** of **Insert New Component**.
3. U kunt:
   * Open de **middelenbrowser** en filter voor **inhoudsfragmenten** (de standaardinstelling is Afbeeldingen). Sleep het gewenste fragment vervolgens naar de componentinstantie.
   * Selecteer de component van het inhoudsfragment, dan **vorm** van de toolbar. In het dialoogvenster kunt u het selectiedialoogvenster openen waarin u het gewenste **inhoudsfragment** kunt selecteren.
   >[!NOTE]
   >
   >Een andere methode is om een specifiek inhoudsfragment rechtstreeks naar de pagina te slepen. Hiermee wordt automatisch de bijbehorende component (inhoudsfragment) gemaakt.

4. In eerste instantie wordt de inhoud van het **hoofdelement** en de **stramienpagina** (variatie) weergegeven. U kunt desgewenst andere elementen en/of variaties [](#selecting-the-element-or-variation) selecteren.

   ![Inhoudsfragmenten in de middelenbrowser](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Zie ook voor meer informatie over de verdere bewerkingsfunctionaliteit:
   >
   >* [Responsieve lay-out](/help/sites-cloud/authoring/features/responsive-layout.md)
   >* [Paginacontent bewerken](/help/sites-cloud/authoring/fundamentals/editing-content.md)


### Het element of de variatie selecteren {#selecting-the-element-or-variation}

Open het dialoogvenster **Configuratie** van het fragment om het fragment te configureren voor gebruik op de huidige pagina. Het dialoogvenster kan afhankelijk zijn van de gebruikte component.

In het juiste configuratiedialoogvenster kunt u de beschikbare parameters selecteren, waaronder:

* **Inhoudsfragment**
   * Geef op welk fragment moet worden gebruikt.
* **Weergavemodus**:
   * **Element voor één tekst**
   * **Meerdere elementen**
* **Element**
   * Afhankelijk van het gebruikte model is een selectie beschikbaar.
   >[!NOTE]
   >
   >Welke elementen beschikbaar zijn, is afhankelijk van het gebruikte model.

* **Variatie**
   * De standaard **master** is altijd beschikbaar.
   * Er is een selectie beschikbaar als er variaties zijn gemaakt voor het fragment.

* **ID**

   * **HTML ID** -kenmerk dat op de component moet worden toegepast.

### Snelle verbinding met de fragmenteditor {#quick-connection-to-fragment-editor}

U kunt de fragmentbron voor bewerking (het element) openen met het pictogram **Bewerken** op de componentwerkbalk. Hierdoor kunt u het inhoudsfragment [](/help/assets/content-fragments/content-fragments.md)bewerken en beheren.

>[!CAUTION]
>
>Zoals altijd heeft het bewerken van de fragmentbron invloed op alle pagina&#39;s die naar dat inhoudsfragment verwijzen.

### Tussenliggende inhoud toevoegen {#adding-in-between-content}

Wanneer een specifiek inhoudsfragment aan de pagina wordt toegevoegd, is hier **een tijdelijke aanduiding voor componenten** Slepen tussen elke HTML-alinea (en boven/onder) van het fragment.

Hierdoor kunt u tussenliggende (dat wil zeggen [tussenliggende inhoud)](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) extra inhoud aan de fragmentinhoud toevoegen (op een van de beschikbare punten) zonder dat u het basisfragment hoeft te wijzigen.

Voor tussenliggende inhoud kunt u:

* Voeg componenten toe vanuit de browser [](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)Componenten.
* Voeg elementen toe vanuit de [middelenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
* Gebruik [Gekoppelde inhoud](#using-associated-content) als bron voor tussenliggende inhoud.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

![Component invoegen](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
>
>U kunt ook visuele elementen (afbeeldingen) [invoegen in het fragment zelf](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Visuele elementen die in het fragment zelf worden ingevoegd, worden aan de voorafgaande alinea in het fragment gekoppeld. Dit betekent dat u geen tussenliggende inhoud tussen een visueel element en de voorgaande alinea kunt plaatsen.

>[!CAUTION]
>
>Nadat u tussenliggende inhoud hebt toegevoegd aan een inhoudsfragment op uw pagina, kan het wijzigen van de structuur van het onderliggende inhoudsfragment (in de editor voor het inhoudsfragment) leiden tot onjuiste/onverwachte resultaten.
>
>Als dit gebeurt, wordt de tussenliggende inhoud als volgt bewaard:
>
>* Tussen componenten heeft een absolute positie binnen de reeks componenten in de fragmentstroom. Deze positie verandert niet, zelfs niet wanneer de inhoud van alinea&#39;s in het fragment verandert.
   >  Hierdoor kan het lijken alsof de relatieve positionering is gewijzigd, aangezien de tussenliggende alinea&#39;s geen contextafhankelijke relatie hebben met de (fragment)alinea&#39;s naast de alinea&#39;s.
>* Tenzij de twee alinea&#39;s met elkaar in strijd zijn; in dat geval wordt de tussenliggende inhoud niet weergegeven (hoewel deze inhoud intern nog steeds aanwezig is).


### Gekoppelde inhoud gebruiken {#using-associated-content}

Als u [content hebt gekoppeld](/help/assets/content-fragments/content-fragments-assoc-content.md) aan het [contentfragment](/help/assets/content-fragments/content-fragments.md), zijn deze assets beschikbaar in het zijpaneel (nadat u het fragment op de contentpagina hebt geplaatst). Gekoppelde content is in feite een speciale bron van content voor [tussenliggende content](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
>
>Er zijn verschillende methoden om [visuele elementen (bijvoorbeeld afbeeldingen)](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

>[!NOTE]
>
>Als er meerdere inhoudsfragmenten op één pagina staan, wordt op het tabblad **Gekoppelde inhoud** de voor alle fragmenten geschikte elementen weergegeven.

Nadat u een fragment met de bijbehorende inhoud aan de pagina hebt toegevoegd, wordt een nieuw tabblad (**Gekoppelde inhoud**) geopend in het zijpaneel.

Van hieruit kunt u de elementen naar de gewenste locatie slepen (naar een bestaande component of naar de gewenste positie waar de juiste component wordt gemaakt):

![Een afbeelding invoegen](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### Elementen die in het fragment zijn ingevoegd {#assets-inserted-into-the-fragment}

Als elementen (bijvoorbeeld afbeeldingen) in het fragment zelf zijn ingevoegd, zijn de opties voor het bewerken van deze elementen in de pagina-editor beperkt.

Voor een afbeelding kunt u bijvoorbeeld

* Snijd, roteer of draai de afbeelding.
* Voeg een titel of alternatieve tekst toe.
* Geef een grootte op.
* U kunt ook de lay-out configureren.

Andere wijzigingen, zoals verplaatsen, kopiëren en verwijderen, moeten worden aangebracht in de fragmenteditor.

### Publiceren {#publishing}

Fragmenten moeten worden gepubliceerd zodat ze op gepubliceerde webpagina&#39;s kunnen worden gebruikt:

* Een fragment kan worden gepubliceerd nadat het fragment is [gemaakt in de middelenconsole](/help/assets/content-fragments/content-fragments-managing.md#publishing-and-referencing-a-fragment).
* Als een *niet-gepubliceerd fragment* wordt gebruikt op een pagina die wordt gepubliceerd, kan het fragment ook op dit moment worden gepubliceerd.
