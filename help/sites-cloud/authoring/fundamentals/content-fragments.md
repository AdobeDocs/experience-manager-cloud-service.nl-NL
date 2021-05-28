---
title: Contentfragmenten
description: Met Adobe Experience Manager als Cloud Service Content Fragments kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en gebruiken
exl-id: 7a44fc4e-3793-4aa3-8c21-db0567c93244
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '1163'
ht-degree: 3%

---

# Contentfragmenten {#content-fragments}

Inhoudsfragmenten in Adobe Experience Manager (AEM) als Cloud Service worden [gemaakt en beheerd als paginasonafhankelijke elementen](/help/assets/content-fragments/content-fragments.md).

U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

Samen met de bijgewerkte JSON-exportfunctie kunnen gestructureerde inhoudsfragmenten ook worden gebruikt om AEM inhoud via Content Services te leveren aan andere kanalen dan AEM pagina&#39;s.

>[!NOTE]
>
>**Content** Fragmentations en  **[Experience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** Fragmentes zijn verschillende functies in AEM:
>
>* **Inhoudsfragmentaties** zijn redactionele inhoud, voornamelijk tekst en verwante afbeeldingen. Het zijn pure inhoud, zonder ontwerp en lay-out.
>* **Ervaring met** fragmentaties is volledig opgemaakt, waardoor fragmenten van een webpagina worden opgemaakt.

>
>
De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.

>[!CAUTION]
>
>Deze pagina moet worden gelezen in combinatie met [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) (en verwante pagina&#39;s), omdat deze basisterminologie en -concepten introduceert en fragmenten maakt en beheert.

Met de inhoudsfragmenten kunt u:

* **Marketings- en Campagne-strategie**
   * Inhoud controleren via centraal beheerde inhoudsfragmenten.
* **Creative Pro**
   * Het bijhouden van creatieve elementen via verzamelingen die zijn gekoppeld aan inhoudsfragmenten.
* **Schrijvers kopiëren**
   * Schrijf in de fragmenteditor voor AEM inhoud.
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
2. Voeg de component **Inhoudsfragment** toe. in de browser **Components** of **Nieuwe component invoegen**.
3. U kunt:
   * Open de browser **Middelen** en filter voor **Inhoudsfragmenten** (de standaardinstelling is Afbeeldingen). Sleep het gewenste fragment vervolgens naar de componentinstantie.
   * Selecteer de component van het inhoudsfragment, dan **vorm** van de toolbar. In het dialoogvenster kunt u het selectiedialoogvenster openen waarin u het gewenste **Inhoudsfragment** kunt selecteren.

   >[!NOTE]
   >
   >Een andere methode is om een specifiek inhoudsfragment rechtstreeks naar de pagina te slepen. Hiermee wordt automatisch de bijbehorende component (inhoudsfragment) gemaakt.

4. Aanvankelijk zal de inhoud van **Main** Element en **Master** (variatie) worden getoond. U kunt [andere elementen en/of variaties ](#selecting-the-element-or-variation) selecteren zoals vereist.

   ![Inhoudsfragmenten in de middelenbrowser](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Zie ook voor meer informatie over de verdere bewerkingsfunctionaliteit:
   >
   >* [Responsieve lay-out](/help/sites-cloud/authoring/features/responsive-layout.md)
   * [Paginacontent bewerken](/help/sites-cloud/authoring/fundamentals/editing-content.md)


### Element of Variatie selecteren {#selecting-the-element-or-variation}

Open het dialoogvenster **Configuratie** van het fragment om het fragment te configureren voor gebruik op de huidige pagina. Het dialoogvenster kan afhankelijk zijn van de gebruikte component.

>[!NOTE]
Zie ook [Core Components, de Content Fragment Component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)

In het juiste configuratiedialoogvenster kunt u de beschikbare parameters selecteren, waaronder:

* **Inhoudsfragment**
   * Geef op welk fragment moet worden gebruikt.
* **Weergavemodus**:
   * **Element voor één tekst**
   * **Meerdere elementen**
* **Element**
   * Afhankelijk van het gebruikte model is een selectie beschikbaar.

   >[!NOTE]
   Welke elementen beschikbaar zijn, is afhankelijk van het gebruikte model.

* **Variatie**
   * De standaard **master** is altijd beschikbaar.
   * Er is een selectie beschikbaar als er variaties zijn gemaakt voor het fragment.

* **ID**

   * **HTML** IDattribute to apply to the component.

### Snelle verbinding met fragmenteditor {#quick-connection-to-fragment-editor}

U kunt de fragmentbron voor bewerking (het element) openen met het pictogram **Bewerken** op de componentwerkbalk. Hierdoor kunt u het inhoudsfragment](/help/assets/content-fragments/content-fragments.md) bewerken en beheren.[

>[!CAUTION]
Zoals altijd heeft het bewerken van de fragmentbron invloed op alle pagina&#39;s die naar dat inhoudsfragment verwijzen.

### Tussenliggende inhoud {#adding-in-between-content} toevoegen

Wanneer een specifiek inhoudsfragment aan de pagina wordt toegevoegd, is er een tijdelijke aanduiding **Componenten hier slepen** tussen elke HTML-alinea (en boven/onder) van het fragment.

Hierdoor kunt u extra inhoud [tussen (d.w.z. tussen inhoud)](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) de fragmentinhoud (op een van de beschikbare punten) toevoegen zonder het basisfragment te hoeven veranderen.

Voor tussenliggende inhoud kunt u:

* Voeg componenten van [Componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) toe.
* Voeg elementen toe vanuit de [middelenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
* Gebruik [Gekoppelde inhoud](#using-associated-content) als bron voor tussenliggende inhoud.

>[!CAUTION]
De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

![Component invoegen](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
U kunt ook [visuele elementen (afbeeldingen) invoegen in het fragment zelf](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
Visuele elementen die in het fragment zelf worden ingevoegd, worden aan de voorafgaande alinea in het fragment gekoppeld. Dit betekent dat u geen tussenliggende inhoud tussen een visueel element en de voorgaande alinea kunt plaatsen. Als u dit verbindingsniveau nodig hebt, kunt u de afbeelding aan het fragment toevoegen (als een [gemengd-mediafragment](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)).

>[!CAUTION]
Nadat u tussenliggende inhoud hebt toegevoegd aan een inhoudsfragment op uw pagina, kan het wijzigen van de structuur van het onderliggende inhoudsfragment (in de editor voor het inhoudsfragment) leiden tot onjuiste/onverwachte resultaten.
Als dit gebeurt, wordt de tussenliggende inhoud als volgt bewaard:
* Tussen componenten heeft een absolute positie binnen de reeks componenten in de fragmentstroom. Deze positie verandert niet, zelfs niet wanneer de inhoud van alinea&#39;s in het fragment verandert.

Hierdoor kan het lijken alsof de relatieve positionering is gewijzigd, aangezien de tussenliggende alinea&#39;s geen contextafhankelijke relatie hebben met de (fragment)alinea&#39;s naast de alinea&#39;s.
* Tenzij de twee alinea&#39;s met elkaar in strijd zijn; in dat geval wordt de tussenliggende inhoud niet weergegeven (hoewel deze inhoud intern nog steeds aanwezig is).


### Gekoppelde inhoud {#using-associated-content} gebruiken

Als u [content hebt gekoppeld](/help/assets/content-fragments/content-fragments-assoc-content.md) aan het [contentfragment](/help/assets/content-fragments/content-fragments.md), zijn deze assets beschikbaar in het zijpaneel (nadat u het fragment op de contentpagina hebt geplaatst). Gekoppelde inhoud is in feite een speciale bron van inhoud voor [tussen inhoud](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
Er zijn verschillende methoden om [visuele elementen (bijvoorbeeld afbeeldingen)](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

>[!NOTE]
Als er meerdere inhoudsfragmenten op één pagina staan, worden op het tabblad **Gekoppelde inhoud** de elementen weergegeven die geschikt zijn voor alle fragmenten.

Nadat u een fragment met de bijbehorende inhoud aan de pagina hebt toegevoegd, wordt een nieuw tabblad (**Gekoppelde inhoud**) geopend in het zijpaneel.

Van hieruit kunt u de elementen naar de gewenste locatie slepen (naar een bestaande component of naar de gewenste positie waar de juiste component wordt gemaakt):

![Een afbeelding invoegen](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### In het fragment ingevoegde elementen {#assets-inserted-into-the-fragment}

Als elementen (bijvoorbeeld afbeeldingen) in het fragment zelf zijn ingevoegd (als [gemengde-mediafragmenten](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)), zijn de opties voor het bewerken van deze elementen in de pagina-editor beperkt.

Voor een afbeelding kunt u bijvoorbeeld

* Snijd, roteer of draai de afbeelding.
* Voeg een titel of alternatieve tekst toe.
* Geef een grootte op.
* U kunt ook de lay-out configureren.

Andere wijzigingen, zoals verplaatsen, kopiëren en verwijderen, moeten worden aangebracht in de fragmenteditor.

### Publiceren {#publishing}

Fragmenten moeten worden gepubliceerd zodat ze op gepubliceerde webpagina&#39;s kunnen worden gebruikt:

* Een fragment kan worden gepubliceerd nadat het fragment [in de middelenconsole is gemaakt](/help/assets/content-fragments/content-fragments-managing.md#publishing-and-referencing-a-fragment).
* Als een *niet-gepubliceerd fragment* wordt gebruikt op een pagina die wordt gepubliceerd, kan het fragment ook op dit moment worden gepubliceerd.
