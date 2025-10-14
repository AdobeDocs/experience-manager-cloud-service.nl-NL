---
title: Overzicht van ervaringsfragmenten
description: Erviteitsfragmenten uitbreiden voor Adobe Experience Manager as a Cloud Service
exl-id: bd4ea763-d17c-40a6-9a86-a24d7600229e
feature: Developing, Experience Fragments
role: Admin, Architect, Developer
source-git-commit: bc422429d4a57bbbf89b7af2283b537a1f516ab5
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 0%

---

# Ervaar fragmenten{#experience-fragments}

## De basisbeginselen {#the-basics}

Een [&#x200B; Fragment van de Ervaring &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) is een groep van één of meerdere componenten met inbegrip van inhoud en lay-out die binnen pagina&#39;s van verwijzingen kunnen worden voorzien.

Een Master of Variant van het Fragment van de Ervaring, of beide, gebruikt:

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

Omdat er geen `/libs/cq/experience-fragments/components/xfpage/xfpage.html` is, wordt het opnieuw ingesteld op

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## De onbewerkte HTML-vertoning {#the-plain-html-rendition}

Met de kiezer `.plain.` in de URL hebt u toegang tot de onbewerkte HTML-uitvoering.

Deze vertoning is beschikbaar in de browser. Het primaire doel is echter om andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang te geven tot de inhoud van het Experience Fragment door alleen de URL te gebruiken.

Met de normale HTML-uitvoering voegt u het protocol-, host- en contextpad toe aan paden die:

* van het type: `src`, `href` of `action`

* of eindigen met: `-src`, of `-href`

Bijvoorbeeld:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Koppelingen verwijzen altijd naar de publicatie-instantie. Ze zijn bedoeld voor gebruik door derden. De koppeling wordt dus altijd aangeroepen vanuit het publicatie-exemplaar en niet vanuit de auteur-instantie.
>
>Voor verdere informatie zie [&#x200B; het externaliseren URLs &#x200B;](/help/implementing/developing/tools/externalizer.md).

![&#x200B; Onbewerkte vertoning van HTML &#x200B;](assets/xf-14.png)

De selector voor normale uitvoering gebruikt een transformator in plaats van aanvullende scripts. [&#x200B; het Verschuiven Rewriter &#x200B;](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wordt gebruikt als transformator. Deze transformator wordt gevormd bij het volgende:

* `/libs/experience-fragments/config/rewriter/experiencefragments`

### De generatie van HTML-uitvoeringen configureren {#configuring-html-rendition-generation}

De HTML-uitvoering wordt gegenereerd met behulp van de Sling Rewriter Pipelines. De pijpleiding wordt bepaald bij `/libs/experience-fragments/config/rewriter/experiencefragments`. De HTML Transformer ondersteunt de volgende opties:

* `allowedCssClasses`
   * Een RegEx-expressie die overeenkomt met de CSS-klassen die in de uiteindelijke uitvoering moeten blijven staan.
   * Deze optie is handig als de klant bepaalde CSS-klassen wil verwijderen
* `allowedTags`
   * Een lijst met HTML-tags die zijn toegestaan in de uiteindelijke uitvoering.
   * Standaard zijn de volgende tags toegestaan (geen configuratie vereist): html, head, title, body, img, p, span, ul, li, a, b, i, em, strong, h1, h2, h3, h4, h5, h6, br, noscript, div, link en script

Adobe raadt u aan de rewriter te configureren met behulp van een overlay. Zie [&#x200B; Bedekkingen in AEM as a Cloud Service &#x200B;](/help/implementing/developing/introduction/overlays.md).

## Sjablonen voor ervaringsfragmenten {#templates-for-experience-fragments}

>[!CAUTION]
>
>***slechts*** editable malplaatjes worden gesteund voor de Fragmenten van de Ervaring.
>
>De Fragmenten van de ervaring kunnen slechts op pagina&#39;s worden gebruikt die op editable malplaatjes gebaseerd zijn.

<!-- 
***Only*** [editable templates](/help/sites-developing/page-templates-editable.md) are supported for Experience Fragments.
-->

Wanneer u een nieuwe sjabloon ontwikkelt voor Experience Fragments, kunt u de standaardwerkwijzen volgen voor een bewerkbare sjabloon.

<!-- 
When developing a new template for Experience Fragments you can follow the standard practices for an [editable template](/help/sites-developing/page-templates-editable.md).
-->

Om een malplaatje van het Fragment van de Ervaring tot stand te brengen dat door **wordt ontdekt creeer de tovenaar van het Fragment van de Ervaring**, moet u één van deze regelreeksen volgen:

1. Beide:

   1. Het middeltype van het malplaatje (de aanvankelijke knoop) moet erven van:
      `cq/experience-fragments/components/xfpage`

   1. De naam van de sjabloon moet beginnen met:
      `experience-fragments`
Met dit patroon kunnen gebruikers ervaringsfragmenten maken in /content/experience-fragments, aangezien de eigenschap `cq:allowedTemplates` van deze map alle sjablonen bevat die een naam hebben die begint met `experience-fragment` . Klanten kunnen deze eigenschap bijwerken en hun eigen naamgevingsschema of sjabloonlocaties opnemen.

1. [&#x200B; Toegestane malplaatjes &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md#configure-allowed-templates-folder) kunnen in de console van de Fragmenten van de Ervaring worden gevormd.

<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- 
>[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Componenten voor ervaringsfragmenten {#components-for-experience-fragments}

Het ontwikkelen van componenten voor gebruik met/in de Fragmenten van de Ervaring volgt standaardpraktijken.

De enige extra configuratie moet ervoor zorgen dat de componenten op het malplaatje worden toegestaan. Deze mogelijkheid wordt bereikt met het inhoudsbeleid.

<!--
[Developing components](/help/sites-developing/components.md) for use with/in Experience Fragments follow standard practices.

The only additional configuration is to ensure that the components are [allowed on the template, this is achieved with the Content Policy](/help/sites-developing/page-templates-editable.md#content-policies).
-->

## De Experience Fragment Link Rewriter Provider - HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM kunt u ervaringsfragmenten maken. Een ervaringsfragment:

* bestaat uit een groep componenten samen met een lay-out;
* kan bestaan onafhankelijk van een AEM-pagina.

Een van de gebruiksgevallen voor dergelijke groepen is het insluiten van inhoud in aanraakpunten van derden, zoals Adobe Target.

### Standaardkoppeling herschrijven {#default-link-rewriting}

<!--Using the [Export to Target](/help/sites-administering/experience-fragments-target.md) feature, you can:
-->

Met de functie Exporteren naar doel kunt u:

* een fragment van de Ervaring tot stand brengen,
* er componenten aan toevoegen,
* en exporteer het als een Adobe Target-aanbieding in HTML-indeling of in JSON-indeling.

Deze functie kan worden ingeschakeld op een instantie van de auteur van AEM. Het vereist een geldige Configuratie van Adobe Target, en configuraties voor de Verbinding Externalzer.

<!--
This feature can be [enabled on an author instance of AEM](/help/sites-administering/experience-fragments-target.md#Prerequisites). It requires a valid Adobe Target Configuration, and configurations for the Link Externalizer.
-->

De functie Extern koppelen wordt gebruikt om te bepalen welke URL&#39;s correct zijn wanneer de HTML-versie van het doelaanbod wordt gemaakt. Deze versie wordt vervolgens naar Adobe Target verzonden. Dit proces is nodig omdat Adobe Target vereist dat alle koppelingen binnen de Target HTML-aanbieding openbaar toegankelijk zijn. Het betekent dat alle bronnen waarnaar de koppelingen verwijzen, en het ervaringsfragment zelf, moeten worden gepubliceerd voordat ze kunnen worden gebruikt.

Wanneer u een HTML-doelaanbieding samenstelt, wordt standaard een aanvraag verzonden naar een aangepaste Sling-kiezer in AEM. Deze kiezer wordt `.nocloudconfigs.html` genoemd. Zoals de naam al aangeeft, wordt een eenvoudige HTML-rendering van een Experience-fragment gemaakt, maar worden cloudconfiguraties niet opgenomen (wat overbodige informatie zou zijn).

Nadat u de HTML-pagina hebt gegenereerd, wordt de Sling Rewriter-pijplijn gewijzigd in de uitvoer:

1. De elementen `html` , `head` en `body` worden vervangen door `div` -elementen. De elementen `meta` , `noscript` en `title` worden verwijderd (dit zijn onderliggende elementen van het oorspronkelijke `head` -element en worden niet meegenomen wanneer ze worden vervangen door het `div` -element).

   Dit proces wordt uitgevoerd om ervoor te zorgen dat de HTML Target Offer kan worden opgenomen in Doelactiviteiten.

2. AEM wijzigt alle interne koppelingen in de HTML, zodat deze verwijzen naar een gepubliceerde bron.

   AEM volgt dit patroon voor kenmerken van HTML-elementen om te bepalen welke koppelingen moeten worden gewijzigd:

   1. `src` kenmerken
   2. `href` kenmerken
   3. `*-src` -kenmerken (zoals `data-src` en `custom-src` )
   4. `*-href` -kenmerken (zoals `data-href` , `custom-href` en `img-href` )

   >[!NOTE]
   >
   >De interne koppelingen in de HTML zijn relatieve koppelingen, maar er kunnen zich gevallen voordoen waarin aangepaste componenten volledige URL&#39;s verschaffen in de HTML. AEM negeert deze volledig ontwikkelde URL&#39;s standaard en brengt geen wijzigingen aan.

   De koppelingen in deze kenmerken worden uitgevoerd via de AEM Link Externalzer `publishLink()` om de URL opnieuw te maken alsof deze zich op een gepubliceerde instantie bevindt en als zodanig openbaar te maken.

Als u een implementatie buiten de doos gebruikt, moet het hierboven beschreven proces voldoende zijn om het doelaanbod te genereren op basis van het ervaringsfragment en het vervolgens te exporteren naar Adobe Target. Er zijn echter enkele gebruiksgevallen die in dit proces niet in aanmerking worden genomen. Enkele van deze gevallen die niet in aanmerking worden genomen omvatten het volgende:

* Sling Mapping beschikbaar op alleen de publicatie-instantie
* Dispatcher omleiding

Voor deze gebruiksgevallen biedt AEM de Link Rewriter Provider Interface.

### Interface Rewriter-provider koppelen {#link-rewriter-provider-interface}

Voor meer gecompliceerde gevallen, die niet door het [&#x200B; gebrek &#x200B;](#default-link-rewriting) worden behandeld, biedt AEM de Interface van de Leverancier van de Verbinding Rewriter aan. Deze interface is een `ConsumerType` -interface die u als service in uw bundels kunt implementeren. Het omzeilt de wijzigingen die AEM uitvoert op interne koppelingen van een HTML-aanbieding, zoals deze worden weergegeven op basis van een Experience Fragment. Met deze interface kunt u het herschrijven van interne HTML-koppelingen aanpassen aan uw bedrijfsbehoeften.

Voorbeelden van gebruiksgevallen om deze interface als dienst uit te voeren omvatten:

* Sling Mappings worden ingeschakeld op de publicatie-instanties, maar niet op de auteurinstantie
* Een Dispatcher of vergelijkbare technologie wordt gebruikt om URL&#39;s intern om te leiden
* `sling:alias mechanisms` zijn ingesteld voor bronnen

>[!NOTE]
>
>Deze interface verwerkt alleen de interne HTML-koppelingen van het gegenereerde doelaanbod.

De Link Rewriter Provider Interface ( `ExperienceFragmentLinkRewriterProvider`) ziet er als volgt uit:

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### Hoe te om de Interface van de Leverancier van de Verbinding te gebruiken Rewriter {#how-to-use-the-link-rewriter-provider-interface}

Om de interface te gebruiken, moet u eerst een bundel tot stand brengen die een nieuwe de dienstcomponent bevat die de interface van de Leverancier van Rewriter van de Verbinding uitvoert.

Deze service wordt gebruikt om in het dialoogvenster Exporteren naar doel van ervaringsfragment te stoppen zodat deze toegang kan hebben tot de verschillende koppelingen.

Bijvoorbeeld `ComponentService` :

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

Voor de dienst aan het werk, zijn er nu drie methodes die binnen de dienst moeten worden uitgevoerd:

* `[shouldRewrite](#shouldrewrite)`
* `[rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* `[getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

Wijs aan het systeem of het de verbindingen moet herschrijven wanneer een vraag voor de Uitvoer aan Doel op een bepaalde verandering van het Fragment van de Ervaring wordt gemaakt. U kunt de volgende methode implementeren:

`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

Bijvoorbeeld:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

Deze methode ontvangt, als parameter, de Variatie van het Fragment van de Ervaring die de Uitvoer naar systeem van het Doel herschrijft.

In het bovenstaande voorbeeld wilt u het volgende herschrijven:

* koppelingen aanwezig in `src`

* `href` alleen kenmerken

* voor een specifiek ervaringsfragment:
  `/content/experience-fragment/master`

Eventuele andere Erviteitsfragmenten die door het systeem Exporteren naar doel worden doorgegeven, worden genegeerd en niet beïnvloed door wijzigingen die in deze service worden geïmplementeerd.

#### rewriteLink {#rewritelink}

Voor de wijziging van het Fragment van de Ervaring die door het herschrijfproces wordt beïnvloed, gaat het dan te werk om de de diensthandvat de verbinding te laten herschrijven. Telkens wanneer een koppeling wordt aangetroffen in de interne HTML, wordt de volgende methode aangeroepen:

`rewriteLink(String link, String tag, String attribute)`

De methode ontvangt de parameters als invoer:

* `link`
De `String` -representatie van de koppeling die wordt verwerkt. Deze vertegenwoordiging is gewoonlijk relatieve URL die aan het middel op de auteursinstantie richten.

* `tag`
De naam van het HTML-element dat wordt verwerkt.

* `attribute`
De exacte kenmerknaam.

Als het systeem Exporteren naar doel dit element bijvoorbeeld verwerkt, kunt u `CSSInclude` als volgt definiëren:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

De aanroep van de methode `rewriteLink()` wordt uitgevoerd met de volgende parameters:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wanneer u de dienst creeert, zijn uw besluiten gebaseerd op de bepaalde input, en herschrijven dan dienovereenkomstig de verbinding.

U wilt bijvoorbeeld het `/etc.clientlibs` -gedeelte van de URL verwijderen en het juiste externe domein toevoegen. Om dingen eenvoudig te houden, denk dat u toegang tot een Resolver van het Middel voor uw dienst, zoals in `rewriteLinkExample2` hebt:

>[!NOTE]
>
>Voor meer informatie over hoe te om een middeloplosser door een de dienstgebruiker te krijgen zie de Gebruikers van de Dienst in AEM.

<!--
>For more information on how to get a resource resolver through a service user see [Service Users in AEM](/help/sites-administering/security-service-users.md).
-->

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>Als de bovenstaande methode `null` retourneert, laat het systeem Exporteren naar doel de koppeling zoals deze is, een relatieve koppeling naar een bron.

#### Prioriteiten - getPriority {#priorities-getpriority}

Het is niet ongebruikelijk om verscheidene diensten te nodig om voor verschillende soorten Fragments van de Ervaring te behandelen, of zelfs om een Generische Dienst te hebben die het externaliseren en in kaart brengen voor alle Fragments van de Ervaring behandelt. In deze gevallen, conflicten over welke de dienst aan gebruik zou kunnen zich voordoen, zodat verstrekt AEM de mogelijkheid om **Prioriteiten** voor de verschillende diensten te bepalen. De prioriteiten worden bepaald volgens de methode:

* `getPriority()`

Met deze methode kunt u verschillende services gebruiken waarbij de methode `shouldRewrite()` true retourneert voor hetzelfde ervaringsfragment. De dienst die het hoogste aantal van zijn `getPriority()` methode terugkeert is de dienst die de Variatie van het Fragment van de Ervaring behandelt.

Als voorbeeld kunt u een `GenericLinkRewriterProvider` hebben die de basistoewijzing voor alle fragmenten van de Ervaring behandelt en wanneer de `shouldRewrite()` methode `true` voor alle Variaties van het Fragment van de Ervaring terugkeert. Voor verschillende specifieke ervaringsfragmenten wilt u wellicht speciale afhandeling. In dit geval kunt u dus een `SpecificLinkRewriterProvider` opgeven waarvoor de methode `shouldRewrite()` alleen waar retourneert voor bepaalde Ervings-fragmentvariaties. Om ervoor te zorgen dat `SpecificLinkRewriterProvider` wordt gekozen voor het verwerken van deze Experience Fragment-variaties, moet het in de `getPriority()` -methode een hoger getal retourneren dan `GenericLinkRewriterProvider.`
