---
title: Vanity-URL's maken met Dynamic Media met OpenAPI-mogelijkheden
description: Gebruik Dynamic Media OpenAPI-mogelijkheden om uw lange URL's voor middelenlevering te transformeren in korte, merkloze URL's. Een ijdelheids-URL is een korte, schone, eenvoudig te onthouden en leesbare versie van uw complexe bezorgings-URL. U kunt uw merknaam, productnamen en relevante trefwoorden opnemen in de vanzelf-URL om de zichtbaarheid van uw merk en de betrokkenheid van gebruikers te vergroten
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: e4ee2e3f251f585a3e057c04d62039a0c2e8bef1
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---


# URL&#39;s met vanity gebruiken{#vanity-urls}

Gebruik [!DNL Dynamic Media OpenAPI capabilities] om uw lange URL&#39;s voor middelenlevering te converteren naar korte, merkloze URL&#39;s. URL&#39;s voor standaardlevering van middelen omvatten door het systeem gegenereerde UUID&#39;s van elementen die de URL van de levering complex maken, moeilijk te onthouden en te delen. Vervang deze UUID&#39;s met elementen door eenvoudige id&#39;s (Vanity ID&#39;s) om een vanity URL te genereren. Een ijdelings-URL is een korte, schone en leesbare versie van uw complexe bezorgings-URL.

Zie de volgende URL-indelingen om het verschil te begrijpen:
* [Standaard-leverings-URL](#standard-urls)
* [Vanity URL&#39;s](#vanity-url)

Standaard levering-URL&#39;s gebruiken `aaid` gevolgd door een UUID, terwijl vanity-URL&#39;s `avid` gebruiken, gevolgd door een aangepaste id (vanity identifier).

Gebruik korte en eenvoudige ijdeligheidsidentificatoren om uw bezorgings-URL kort, schoon, leesbaar, gemakkelijk te onthouden en te delen te maken. Gebruik uw merknaam, productnamen en relevante trefwoorden als ijdelings-id&#39;s om de zichtbaarheid van uw merk en de betrokkenheid van de gebruiker te vergroten.

Wanneer de gebruiker op de URL van uw ijdelheid klikt, wordt [!DNL Dynamic Media with OpenAPI] automatisch toegewezen aan de oorspronkelijke elementlocatie op het moment van inname en worden deze op de juiste wijze omgezet op het moment van levering naar de server waarop het element wordt geplaatst.

Leer [ tot Vanity URLs ](#create-vanity-urls) leiden.

## Standaard URL&#39;s voor levering{#standard-urls}

De standaard-URL voor het leveren van [!DNL Dynamic Media with OpenAPI] elementen bevat een unieke door het systeem gegenereerde id en volgt de volgende indeling.

***Formaat:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:aaid:aem:<asset-uuid>/as/<seoname>.<format>`

De standaard levering URL omvat `aaid` (*daadwerkelijke activa herkenningsteken*) na `urn:` en UUID tussen `urn:aaid:aem:` en `/as/<seoname>.<format>`.

***Voorbeeld:*** `https://delivery-p30902-e145436.adobeaemcloud.com/adobe/assets/urn:aaid:aem:43341ab1-4086-44d2-b7ce-ee546c35613b/as/check.jpeg`

In het bovenstaande voorbeeld is `43341ab1-4086-44d2-b7ce-ee546c35613b` de UUID.

## Vanity URL&#39;s{#vanity-url}

De vanity URLs omvat een ijdelings herkenningsteken in plaats van activa UUID en volgt het volgende formaat.

***Formaat:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/as/<seoname>.<format>`

De vanity URL omvat `avid` (*daadwerkelijke vanity herkenningsteken*) na `urn:` en uw ijdelings identiteitskaart tussen `urn:avid:aem:` en `/<seoname>.<format>`.

***Voorbeeld:*** `https://delivery-p30902-e145436.adobeaemcloud.com/adobe/assets/urn:avid:aem:VanityCheck/as/check.jpeg`

In het bovenstaande voorbeeld is `VanityCheck` de ijdeligheids-id die de UUID heeft vervangen.

## Belangrijke mogelijkheden en voordelen verkennen{#capabilities-and-benefits-of-vanity-urls}

Het gebruik van zinvolle vanity-id&#39;s om de URL&#39;s voor standaardlevering van elementen aan te passen biedt verschillende voordelen en meetbare gevolgen. Enkele belangrijke mogelijkheden en voordelen van vanity URLs omvatten het volgende.

### Belangrijkste mogelijkheden{#key-capabilities}

* **aanpassing URL:** vervang lange herkenningstekens (activa UUIDs) in levering URL met kortere, merkgebonden alternatieven om een schonere levering URL te produceren.
* **Realtime redirection:** Vanity URLs leidt aan originele activa UUIDs bij runtime opnieuw zonder werkschema&#39;s te onderbreken. De gebruikers zien schone URLs in de adresbar terwijl het systeem het technische verpletteren behandelt.
* **Gemakkelijk verbindingsbeheer:** pas uw ijdelheid URLs op elk ogenblik aan zonder de prestaties van de activalevering te beïnvloeden.

### Belangrijkste voordelen{#key-benefits}

* **verbetert gebruikerservaring:** Schone en kortere vanity URLs is leesbaar, gebruikersvriendelijk, gemakkelijk te herinneren en te delen.

* **verbetert gebruikersbetrokkenheid:** Branded URLs bouwt gebruikersvertrouwen en vertrouwen. Gebruikers kunnen vaker op professionele, brandingkoppelingen klikken, wat leidt tot hogere doorkliksnelheden.

* **optimalisering SEO:** URLs die relevante sleutelwoorden omvatten verbetert de classificaties en de ontdekkingsbaarheid van de onderzoeksmotor.

* **Verbeterde merkzichtbaarheid:** merk-specifieke URLs versterken merkaanwezigheid over alle marketing kanalen, met inbegrip van e-mail, sociale media, en reclamecampagnes.
Bovendien versterkt een consistent gebruik van merkgebonden URL&#39;s in alle communicatie de merkidentiteit en -herkenning.

* **het volgen van de Campagne en analyses:** Gebruik unieke vanity URLs voor verschillende campagnes en kanalen om gedetailleerde inzichten in verkeersbronnen en omzettingsprestaties te bereiken.

## Vereisten{#prerequisites-for-creating-vanity-id}

Om ijdelheid URL tot stand te brengen, zorg ervoor u reeds [ de activa voor openbare levering ](/help/assets/manage-organize-assets-view.md#manage-asset-status) hebt goedgekeurd.

## Vanity-URL&#39;s maken{#create-vanity-urls}

Voer de volgende stappen uit om vanity URLs tot stand te brengen:
1. [Metagegevens van elementen instellen](#set-up-asset-metadata)
1. [Omgevingsvariabele van Cloud Manager maken en toewijzen](#map-cloud-manager-environment-variable)
1. [Goedkeuren van de elementen die vanity URL vereisen voor levering](/help/assets/manage-organize-assets-view.md#manage-asset-status)
1. [URL&#39;s met ijkpunten genereren](#generate-vanity-urls)

### Metagegevens van elementen instellen{#set-up-asset-metadata}

Voer het volgende uit om de vanity-id in te stellen in het metagegevensformulier van uw element:
1. Navigeer naar de detailpagina van de map met uw elementen voor levering [!DNL Dynamic Media with OpenAPI] .
1. [ geef die meta-gegevens uit ](/help/assets/metadata-assets-view.md#edit-metadata-forms) door één van het volgende te doen:
   * Voeg een nieuw metagegevensveld toe en geef de vereiste ID als waarde voor dat veld op.
   * Werk bestaand veld bij door de waarde van een bestaande eigenschap voor metagegevens te vervangen door de vereiste ijdeligheids-id. Leer de [ beste praktijken ](#best-practices) voor het creëren van ijdeligheidsidentiteitskaart
     ![ vanity identiteitskaart ](/help/assets/assets/vanity-id-metadata.png)
Leer meer over [ meta-gegevensschema&#39;s ](/help/assets/metadata-schemas.md).

     >[!NOTE]
     >
     > * Gebruik unieke vanity-id&#39;s voor elk element. Controleer altijd of elementen die hetzelfde metagegevensformulier delen, unieke vanity-id&#39;s hebben voor DM met OpenAPI-levering via vanity-URL&#39;s. Als twee elementen dezelfde vanity-id hebben, levert DM met OpenAPI het element dat de id het laatst heeft ontvangen, waarbij de vorige machtiging van de id voor een ander element wordt overschreven.
     >
     > * Een enkel element kan meerdere vanity-id&#39;s hebben. [ de steun van Adobe van het Contact ](https://helpx.adobe.com/in/contact.html) en wint een verzoek op om vereiste vanity IDs te produceren.

Na vestiging uw identiteitskaart van de Veerzaamheid in de vorm van activa meta-gegevens, [ kaart dit meta-gegevensgebied aan het de leveringsmechanisme van het systeem ](#map-cloud-manager-environment-variable).

### Omgevingsvariabele van Cloud Manager maken en toewijzen{#map-cloud-manager-environment-variable}

Voer de volgende stappen uit om een omgevingsvariabele te maken en deze toe te wijzen aan het metagegevensveld met de vanity-id:

1. [ navigeer aan de configuratiepagina van uw milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) en doe het volgende:
   1. Voeg `ASSET_DELIVERY_VANITY_ID` variabele toe. Dit is de sleutel.
   1. Gebruik het waardeveld om toe te wijzen aan de eigenschap met metagegevens van het element die de vanity-id bevat. De toewijzing volgt de `dc:<your-metadata-property>` -indeling, waarbij het voorvoegsel voor de toewijzing van metagegevens (zoals dc:) varieert op basis van de configuratieeigenschap voor de metagegevens van het element.
      ![ variabele ASSET_DELIVERY_VANITY_ID ](/help/assets/assets/environment-config.png)
1. Sla de wijzigingen op om de pods opnieuw te starten in uw omgeving.

### De activa goedkeuren voor levering{#approve-assets-for-delivery}

Na het in kaart brengen van de `ASSET_DELIVERY_VANITY_ID` variabele in uw milieu van Cloud Manager aan het bezit van activa meta-gegevens dat ijdelings identiteitskaart houdt, [ keurt uw activa goed die ijdelheid URL voor levering ](/help/assets/manage-organize-assets-view.md#manage-asset-status) vereisen.

### Vanity-URL&#39;s genereren{#generate-vanity-urls}

Maak de volgende vervangingen in uw standaard levering URL om het in een ijdelheid URL om te zetten:

* Vervang **UUID** met uw **ijdelings identiteitskaart**.
* Vervang `aaid` door `avid` .

Zie de [ transformatie URL van norm aan ijdelheid URL ](#standard-urls) hierboven.
Leer hoe te [ om Dynamische Media met OpenAPI levering URLs ](/help/assets/approve-assets.md#copy-delivery-url-for-approved-assets) voor uw activa te kopiëren.

Wanneer de gebruiker op de URL van de ijdelheid klikt, wijst [!DNL Dynamic Media with OpenAPI] automatisch de ijdelheidsidentiteitskaart aan het originele element UUID toe in ingstijd en lost hen op behoorlijk op leveringstijd om het middel aan de gebruiker zonder enige vertraging te dienen. U kunt de vanity-URL in real-time aanpassen zonder dat dit van invloed is op de prestaties van de levering van elementen.

[Verbeter de impact van uw ijdelings-URL&#39;s met behulp van de geavanceerde aanpassingsmogelijkheden van de AEM Cloud Service.](#scale-using-vanity-url)

## Schalen met URL&#39;s met vanity{#scale-using-vanity-url}

AEM as a Cloud Service laat u toe om [ de DNS en CDN namen ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/introduction) binnen uw Webadressen aan te passen. Gebruik deze mogelijkheden AEMCS met uw ijdelheid URLs om hen in unieke web-adressen om te zetten die schoon, beschrijvend, van branding voorzien, intuïtief zijn en [ bovengenoemde voordelen ](#key-benefits) verstrekken.

Zie de volgende vanity URL en zijn klantgerichte componenten:

**formaat van URL van de Vanity:**

`https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/as/<seoname>.<format>`

<table style="border-collapse:collapse; table-layout:auto; width:auto;">
<tr valign="top">
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>https://delivery&#8209;&lt;tenant&gt;.adobeaemcloud.com</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#customize-dns"> pas dit DNS </a> aan</div>
</td>
<td style="padding:0 6px; white-space:nowrap; text-align:center;">/</td>
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>adobe/assets/urn:avid:aem:</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#rewrite-cdn-rules"> pas URL met herschrijf regels aan </a></div>
</td>
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>&lt;vanity-id&gt;</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#create-vanity-urls"> creeer vanity identiteitskaart </a></div>
</td>
<td style="padding:0 4px; white-space:nowrap; text-align:left; width:1%;">
<code>/as/&lt;seoname&gt;.&lt;format&gt;</code>
</td>
</tr>
</table>

{het formaat van 0} Vanity URL met aangepaste DNS en CDN namen:**&#x200B;**

`https://<custom-dns>` `/` `dam/assets/` `<vanity-id>` `/as/<seoname>.<format>`

**Aanpasbare Componenten URL**

* ***[DNS naam (hostname):](#customize-DNS)*** `https://delivery-<tenant>.adobeaemcloud.com` is het serverdomein dat gastheren uw activa. [ pas DNS aan om hostname ](#customize-DNS) te veranderen.
* ***[CDN herschrijft regels:](#rewrite-cdn-rules)*** `adobe/assets/urn:avid:aem:` is de wegstructuur die activatypes en leveringsmethodes identificeert. [ herschrijf CDN regels ](#rewrite-cdn-rules) om de domeinweg te wijzigen.

### DNS aanpassen{#customize-dns}

[ omhoog een verzoek aan de steun van Adobe ](https://helpx.adobe.com/in/contact.html) om vereiste douaneDNS voor uw leveringsrij te produceren. Volg deze [ beste praktijken ](#best-practices) voor het creëren van de namen van douaneDNS.

### CDN-regels herschrijven{#rewrite-cdn-rules}

Voer de volgende stappen uit om de CDN-regels voor levering te herschrijven:

1. Navigeer naar de AEM-opslagplaats om een YAML-configuratiebestand te maken.
2. Voer de stappen in [ opstelling ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-error-pages#setup) sectie uit om CDN regels te vormen en de configuratie door uw de configuratiepijplijn van Cloud Manager op te stellen.
Volg deze [ beste praktijken ](#best-practices) voor het creëren van uw domeinweg.
   [ Leer meer over CDN die regels ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#request-transformations) herschrijven.

Hieronder volgen voorbeelden van herschrijfregels voor het toevoegen van bestandsnamen met extensies in vanity-URL&#39;s. Pas deze herschrijfregels aan volgens uw specifieke vereisten. [ de steun van Adobe van het Contact ](https://helpx.adobe.com/in/contact.html) voor verdere hulp:

```- name: cdn-rewrite-rule
  when:
    allOf:
      - reqProperty: tier
        equals: delivery
```

#### Voor SVG, GIF en PDF {#svg-gif-pdf}

```
    type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:svg|gif|pdf|docx|xlsx))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/original/as/\1\2
```

#### Voor video{#video}

Voor video&#39;s zoals MP4, MOV, AVI en MKV

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:mp4|mov|avi|mkv))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/play\2
```

#### Voor afbeelding{#image}

Voor alle afbeeldingstypen, met uitzondering van SVG.

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.[^/]+)(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/as/\1\2
```

## Volg de aanbevolen procedures voor het maken van schone vanity-URL&#39;s{#best-practices}

Volg deze beste praktijken voor het creëren van vanity IDs, douaneDNS en domeinnamen:

1. Gebruik geen speciale tekens in vanity-id&#39;s, zoals spaties, schuine strepen, afbreekstreepjes en meer. Het systeem vervangt speciale karakters in vanity IDs gebruikend een vooraf bepaalde afbeelding.
1. Gebruik uw merknaam, productnamen en relevante trefwoorden in uw ijdelings-id&#39;s, aangepaste DNS- en domeinnamen om uw merkzichtbaarheid en betrokkenheid van gebruikers te vergroten.
1. Gebruik korte, beschrijvende woorden of tekenreeksen die betekenis overbrengen.
1. Gebruik teksten die gebruikers voor kliks uitnodigen.
