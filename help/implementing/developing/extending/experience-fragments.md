---
title: Overzicht van ervaringsfragmenten
description: Erviteitsfragmenten uitbreiden voor Adobe Experience Manager as a Cloud Service
exl-id: bd4ea763-d17c-40a6-9a86-a24d7600229e
source-git-commit: 433e95366a8cc0baebb1ccd02a64603ab26dfb86
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 0%

---

# Ervaar fragmenten{#experience-fragments}

## De basisbeginselen {#the-basics}

An [Ervaar fragment](/help/sites-cloud/authoring/fragments/content-fragments.md) is een groep van één of meerdere componenten met inbegrip van inhoud en lay-out die binnen pagina&#39;s kunnen worden van verwijzingen voorzien.

Een Master of Variant van het Fragment van de Ervaring, of beide, gebruikt:

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

Omdat er geen `/libs/cq/experience-fragments/components/xfpage/xfpage.html`, wordt het volgende hersteld

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## De normale HTML-vertoning {#the-plain-html-rendition}

Met de `.plain.` in de URL, kunt u tot de normale vertoning van de HTML toegang hebben.

Deze vertoning is beschikbaar in de browser. Het primaire doel is echter om andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang te geven tot de inhoud van het Experience Fragment door alleen de URL te gebruiken.

Met de uitvoering voor normale HTML worden het protocol, de host en het contextpad toegevoegd aan paden die:

* van het type: `src`, `href`, of `action`

* of eindigen met: `-src`, of `-href`

Bijvoorbeeld:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Koppelingen verwijzen altijd naar de publicatie-instantie. Ze zijn bedoeld voor gebruik door derden. De koppeling wordt dus altijd aangeroepen vanuit het publicatie-exemplaar en niet vanuit de auteur-instantie.
>
>Zie voor meer informatie [URL&#39;s extern maken](/help/implementing/developing/tools/externalizer.md).

![Onbewerkte HTML-uitvoering](assets/xf-14.png)

De selector voor normale uitvoering gebruikt een transformator in plaats van aanvullende scripts. De [Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wordt gebruikt als transformator. Deze transformator wordt gevormd bij het volgende:

* `/libs/experience-fragments/config/rewriter/experiencefragments`

### De generatie van de HTML-uitvoering configureren {#configuring-html-rendition-generation}

De uitvoering van de HTML wordt gegenereerd met behulp van de Sling Rewriter Pipelines. De pijpleiding wordt bepaald bij `/libs/experience-fragments/config/rewriter/experiencefragments`. De transformator van de HTML steunt de volgende opties:

* `allowedCssClasses`
   * Een RegEx-expressie die overeenkomt met de CSS-klassen die in de uiteindelijke uitvoering moeten blijven staan.
   * Deze optie is handig als de klant bepaalde CSS-klassen wil verwijderen
* `allowedTags`
   * Een lijst met HTML-tags die zijn toegestaan in de uiteindelijke uitvoering.
   * Standaard zijn de volgende tags toegestaan (geen configuratie vereist): html, head, title, body, img, p, span, ul, li, a, b, i, em, strong, h1, h2, h3, h4, h5, h6, br, noscript, div, link en script

Adobe raadt aan de rewriter te configureren met behulp van een overlay. Zie [Bedekkingen in AEM as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

## Sjablonen voor ervaringsfragmenten {#templates-for-experience-fragments}

>[!CAUTION]
>
>***Alleen*** bewerkbare sjablonen worden ondersteund voor Experience Fragments.
>
>De Fragmenten van de ervaring kunnen slechts op pagina&#39;s worden gebruikt die op editable malplaatjes gebaseerd zijn.

<!-- >***Only*** [editable templates](/help/sites-developing/page-templates-editable.md) are supported for Experience Fragments.
-->

Wanneer u een nieuwe sjabloon ontwikkelt voor Experience Fragments, kunt u de standaardwerkwijzen volgen voor een bewerkbare sjabloon.

<!-- When developing a new template for Experience Fragments you can follow the standard practices for an [editable template](/help/sites-developing/page-templates-editable.md).
-->

Een ervaringsfragmentsjabloon maken die wordt gedetecteerd door de **Experience Fragment maken** wizard, moet u een van de volgende regelsets volgen:

1. Beide:

   1. Het middeltype van het malplaatje (de aanvankelijke knoop) moet erven van:
      `cq/experience-fragments/components/xfpage`

   1. De naam van de sjabloon moet beginnen met:
      `experience-fragments`
Met dit patroon kunnen gebruikers ervaringsfragmenten maken in /content/experience-fragments als de `cq:allowedTemplates` eigenschap van deze map bevat alle sjablonen met namen die beginnen met `experience-fragment`. Klanten kunnen deze eigenschap bijwerken en hun eigen naamgevingsschema of sjabloonlocaties opnemen.

1. [Toegestane sjablonen](/help/sites-cloud/authoring/fragments/content-fragments.md#configure-allowed-templates-folder) kan in de console van de Fragmenten van de Ervaring worden gevormd.

<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
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

In AEM hebt u de mogelijkheid om ervaringsfragmenten te maken. Een ervaringsfragment:

* bestaat uit een groep componenten samen met een lay-out;
* kan onafhankelijk van een AEM pagina bestaan.

Een van de gebruiksgevallen voor dergelijke groepen is het insluiten van inhoud in aanraakpunten van derden, zoals Adobe Target.

### Standaardkoppeling herschrijven {#default-link-rewriting}

<!--Using the [Export to Target](/help/sites-administering/experience-fragments-target.md) feature, you can:
-->

Met de functie Exporteren naar doel kunt u:

* een fragment van de Ervaring tot stand brengen,
* er componenten aan toevoegen,
* en exporteer het vervolgens als een Adobe Target-aanbieding in de indeling HTML of JSON.

Deze functie kan worden ingeschakeld op een instantie van AEM. Het vereist een geldige Configuratie van Adobe Target, en configuraties voor de Verbinding Externalzer.

<!--
This feature can be [enabled on an author instance of AEM](/help/sites-administering/experience-fragments-target.md#Prerequisites). It requires a valid Adobe Target Configuration, and configurations for the Link Externalizer.
-->

De Verbinding ExternalAlizer wordt gebruikt om correcte URLs te bepalen nodig wanneer het creëren van de versie van de HTML van het Voorstel van het Doel, dat dan naar Adobe Target wordt verzonden. Dit proces is noodzakelijk aangezien Adobe Target vereist dat alle verbindingen binnen de Aanbieding van de HTML van het Doel openbaar kunnen worden betreden. Het betekent dat alle bronnen waarnaar de koppelingen verwijzen, en het ervaringsfragment zelf, moeten worden gepubliceerd voordat ze kunnen worden gebruikt.

Wanneer u een Target HTML-aanbieding samenstelt, wordt standaard een aanvraag verzonden naar een aangepaste Sling-kiezer in AEM. Deze kiezer wordt `.nocloudconfigs.html`. Zoals de naam al aangeeft, wordt een GPU-rendering van een Experience-fragment gemaakt, maar worden cloudconfiguraties niet opgenomen (wat overbodige informatie zou zijn).

Nadat u de pagina van de HTML produceert, wordt de Sling Rewriter pijpleiding gewijzigd aan de output:

1. De `html`, `head`, en `body` elementen worden vervangen door `div` elementen. De `meta`, `noscript`, en `title` elementen worden verwijderd (het zijn onderliggende elementen van het origineel) `head` -element, en wordt niet in aanmerking genomen wanneer deze worden vervangen door de `div` element).

   Dit proces wordt uitgevoerd om ervoor te zorgen dat de HTML Target-aanbieding kan worden opgenomen in doelactiviteiten.

2. AEM wijzigt om het even welke interne verbindingen aanwezig in de HTML, zodat zij aan een gepubliceerde middel richten.

   Als u wilt bepalen welke koppelingen moeten worden gewijzigd, AEM u dit patroon voor kenmerken van HTML-elementen volgt:

   1. `src` attributes
   2. `href` attributes
   3. `*-src` kenmerken (zoals `data-src`, en `custom-src`)
   4. `*-href` kenmerken (zoals `data-href`, `custom-href`, en `img-href`)

   >[!NOTE]
   >
   >De interne koppelingen in de HTML zijn relatieve koppelingen, maar er kunnen zich gevallen voordoen waarin aangepaste componenten volledige URL&#39;s in de HTML bevatten. Standaard worden deze volledige URL&#39;s genegeerd en worden geen wijzigingen aangebracht.

   De verbindingen in deze attributen worden in werking gesteld door de AEM Verbinding Externalzer `publishLink()` om de URL opnieuw te maken alsof deze zich op een gepubliceerd exemplaar bevindt, en als zodanig openbaar te maken.

Als u een implementatie buiten de doos gebruikt, moet het hierboven beschreven proces voldoende zijn om het doelaanbod te genereren op basis van het ervaringsfragment en het vervolgens te exporteren naar Adobe Target. Er zijn echter enkele gebruiksgevallen die in dit proces niet in aanmerking worden genomen. Enkele van deze gevallen die niet in aanmerking worden genomen omvatten het volgende:

* Sling Mapping beschikbaar op alleen de publicatie-instantie
* Omleiding van Dispatcher

Voor deze gebruiksgevallen, verstrekt AEM de Interface van de Leverancier van de Verbinding Rewriter.

### Interface Rewriter-provider koppelen {#link-rewriter-provider-interface}

Voor meer gecompliceerde gevallen die niet onder de [default](#default-link-rewriting), AEM biedt de Interface van de Leverancier van de Verbinding Rewriter aan. Deze interface is `ConsumerType` interface die u in uw bundels, als dienst kunt uitvoeren. Het omzeilt de aanpassingen AEM op interne verbindingen van een aanbieding van de HTML zoals die van een Fragment van de Ervaring worden teruggegeven uitvoeren. Met deze interface kunt u het herschrijven van interne HTML-koppelingen aanpassen aan uw bedrijfsbehoeften.

Voorbeelden van gebruiksgevallen om deze interface als dienst uit te voeren omvatten:

* Sling Mappings worden ingeschakeld op de publicatie-instanties, maar niet op de auteurinstantie
* Een Dispatcher of vergelijkbare technologie wordt gebruikt om URL&#39;s intern om te leiden
* De `sling:alias mechanisms` beschikken over middelen

>[!NOTE]
>
>Deze interface verwerkt alleen de interne HTML-koppelingen van het gegenereerde doelaanbod.

De koppeling Rewriter Provider Interface ( `ExperienceFragmentLinkRewriterProvider`) is als volgt:

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

Bijvoorbeeld: `ComponentService`:

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
De `String` een weergave van de koppeling die wordt verwerkt. Deze vertegenwoordiging is gewoonlijk relatieve URL die aan het middel op de auteursinstantie richten.

* `tag`
De naam van het HTML-element dat wordt verwerkt.

* `attribute`
De exacte kenmerknaam.

Als het systeem Exporteren naar doel dit element bijvoorbeeld verwerkt, kunt u definiëren `CSSInclude` als:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

De oproep aan de `rewriteLink()` De methode wordt uitgevoerd met behulp van de volgende parameters:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wanneer u de dienst creeert, zijn uw besluiten gebaseerd op de bepaalde input, en herschrijven dan dienovereenkomstig de verbinding.

In het voorbeeld wilt u het dialoogvenster `/etc.clientlibs` deel van URL en voeg het aangewezen externe domein toe. Om dingen eenvoudig te houden, overweeg dat u toegang tot een Resolver van het Middel voor uw dienst, zoals in hebt `rewriteLinkExample2`:

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
>Als de bovenstaande methode retourneert `null`Dan verlaat het systeem van de Uitvoer naar Doel de verbinding zoals het is, een relatieve verbinding aan een middel is.

#### Prioriteiten - getPriority {#priorities-getpriority}

Het is niet ongebruikelijk om verscheidene diensten te nodig om voor verschillende soorten Fragments van de Ervaring te behandelen, of zelfs om een Generische Dienst te hebben die het externaliseren en in kaart brengen voor alle Fragments van de Ervaring behandelt. In deze gevallen kunnen conflicten ontstaan over de dienst die moet worden gebruikt, zodat AEM de mogelijkheid biedt om **Prioriteiten** voor verschillende diensten. De prioriteiten worden bepaald volgens de methode:

* `getPriority()`

Deze methode maakt het gebruik van verschillende diensten mogelijk wanneer de `shouldRewrite()` Deze methode retourneert true voor hetzelfde ervaringsfragment. De dienst die het hoogste aantal van zijn terugkeert `getPriority()`De methode is de dienst die de Variatie van het Fragment van de Ervaring behandelt.

U kunt bijvoorbeeld een `GenericLinkRewriterProvider` dat de basisafbeelding voor alle fragmenten van de Ervaring behandelt en wanneer `shouldRewrite()` methode retourneert `true` voor alle Experience Fragment Variations. Voor verscheidene specifieke Fragments van de Ervaring, kunt u speciale behandeling willen, zodat kunt u in dit geval verstrekken `SpecificLinkRewriterProvider` waarvoor de `shouldRewrite()` Deze methode retourneert alleen true voor bepaalde Experience Fragment-variaties. Controleer of `SpecificLinkRewriterProvider` wordt gekozen om die Variaties van het Fragment van de Ervaring te behandelen, moet het in zijn terugkeren `getPriority()` methode een hoger getal dan `GenericLinkRewriterProvider.`
