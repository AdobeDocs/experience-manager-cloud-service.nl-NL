---
title: CDN in AEM as a Cloud Service
description: Leer hoe te om AEM-geleide CDN te gebruiken en hoe te om uw eigen CDN aan AEM-beheerde CDN te richten.
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
role: Admin
source-git-commit: 6600f5c1861e496ae8ee3b6d631ed8c033c4b7ef
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 2%

---


# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties."

AEM as a Cloud Service wordt geleverd met een geïntegreerde CDN, die is ontworpen om latentie te verminderen door cacheable inhoud te leveren van randknooppunten dicht bij de browser van de gebruiker. Dit volledig beheerde CDN wordt geoptimaliseerd voor AEM toepassingsprestaties.

AEM-beheerde CDN voldoet aan de prestaties en de veiligheidsbehoeften van de meeste klanten. Voor publiceer rij, kunnen de klanten verkiezen om verkeer door hun eigen CDN te leiden, die zij moeten leiden. Deze optie is beschikbaar per geval, vooral wanneer de klanten bestaande erfenisintegratie met een leverancier hebben CDN die moeilijk zijn te vervangen.

De klanten die aan de Edge Delivery Services rij willen publiceren kunnen uit beheerde CDN van de Adobe voordeel halen. Zie [ Beheerde Adobe CDN ](#aem-managed-cdn). <!-- CQDOC-21758, 5b -->


<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## Adobe beheerde CDN {#aem-managed-cdn}

<!-- CQDOC-21758, 5a -->

Als u zich wilt voorbereiden op de levering van inhoud met behulp van AEM ingebouwde CDN via de zelfbedieningsinterface van Cloud Manager, kunt u gebruikmaken van de beheerde CDN-functies van de Adobe. Met deze functionaliteit kunt u CDN-beheer met zelfbediening afhandelen, inclusief het configureren en installeren van SSL-certificaten, zoals DV- (Domain Validation) of EV/OV-certificaten (Extended/Organization Validation). Raadpleeg de volgende bronnen voor meer informatie over deze methoden:

* [Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)
* [Inleiding tot aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
* [Inleiding tot SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)
* [Een CDN-configuratie toevoegen](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)

**Beperkend verkeer**

Door gebrek, voor een AEM-beheerde opstelling CDN, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. U kunt verkeer tot de publicatiedienst voor een bepaald milieu beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) als gebruikersinterface van Cloud Manager.

Zie [ het Leiden IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) om meer te leren.

>[!CAUTION]
>
>AEM beheerde CDN dient verzoeken slechts van toegestane IPs. Als u uw eigen CDN aan AEM-beheerde CDN richt, dan zorg ervoor IPs van uw CDN in de IP Lijst van gewenste personen inbegrepen is.

### Het verkeer op de CDN configureren {#cdn-configuring-cloud}

U kunt verkeer bij CDN op diverse manieren vormen, die omvatten:

* het blokkeren van kwaadwillig verkeer met [ Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md) (met inbegrip van naar keuze licentiable geavanceerde regels van WAF)
* het wijzigen van de aard van het [ verzoek en de reactie ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)
* het toepassen van 301/302 [ cliënt-zijredirects ](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)
* het verklaren van [ oorsprongselectors ](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) om volmacht een verzoek aan niet-AEM backends om te keren

Gebruik YAML-bestanden in Git om deze functies te configureren. En, gebruik Cloud Manager [ Config Pipeline ](/help/implementing/dispatcher/cdn-configuring-traffic.md) om hen op te stellen.

### CDN-foutpagina&#39;s configureren {#cdn-error-pages}

U kunt een CDN foutenpagina vormen om de standaard, unbranded pagina te vervangen. Deze aangepaste pagina wordt weergegeven in het zeldzame geval dat AEM niet beschikbaar is. Voor meer details, zie [ Vormend CDN foutenpagina&#39;s ](/help/implementing/dispatcher/cdn-error-pages.md).

### Inhoud in cache wissen op de CDN {#purge-cdn}

Het plaatsen van TTL gebruikend HTTP Cachebeheer kopbal is een efficiënte benadering om de prestaties van de inhoudslevering en inhoudsversheid in evenwicht te brengen. In scenario&#39;s waarin het van essentieel belang is om bijgewerkte inhoud direct te leveren, kan het echter nuttig zijn om de CDN-cache rechtstreeks te wissen.

Lees over [ vormend een zuiveringsAPI teken ](/help/implementing/dispatcher/cdn-credentials-authentication.md/#purge-API-token) en [ zuiverend caching inhoud CDN ](/help/implementing/dispatcher/cdn-cache-purge.md).

### Basisverificatie bij de CDN {#basic-auth}

Voor lichte gebruikersverificatiegevallen, waaronder die van zakelijke belanghebbenden die inhoud controleren, moet u de inhoud beschermen door een standaarddialoogvenster weer te geven waarin een gebruikersnaam en wachtwoord vereist zijn. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md).

## Door de klant beheerde CDN verwijst naar AEM beheerde CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="CDN van de klant wijst naar AEM Beheerde CDN"
>abstract="AEM als Cloud Service biedt klanten een optie om zijn bestaande CDN te gebruiken. Voor de publicatielaag kunnen klanten optioneel naar de laag verwijzen vanuit hun eigen CDN, die ze moeten beheren. Dit scenario wordt toegestaan op een geval-voor-geval basis, gebaseerd op het voldoen van bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun leverancier CDN heeft die moeilijk is te verlaten."

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het beheren en het richten aan AEM-beheerde CDN, op voorwaarde dat het volgende wordt voldaan:

* De klant moet een bestaande CDN hebben die moeilijk te vervangen zou zijn.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM as a Cloud Service te werken - zie de hieronder vermelde configuratieinstructies.
* De klant moet ingenieurs CDN hebben die op vraag in op geval betrekking hebbende kwesties zich voordoen.
* De klant moet een laadtest uitvoeren en met succes slagen alvorens aan productie te gaan.

Configuratieinstructies:

1. Wijs de CDN toe aan de ingangen van de Adobe CDN als zijn oorsprongdomein. Bijvoorbeeld `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` .
1. Stel SNI in op de invoer van de Adobe CDN.
1. Stel de Hostkop in op het oorspronkelijke domein. Bijvoorbeeld: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` .
1. Stel de header `X-Forwarded-Host` in met de domeinnaam, zodat AEM de hostheader kan bepalen. Bijvoorbeeld: `X-Forwarded-Host:example.com` .
1. Stel `X-AEM-Edge-Key` in. De waarde zou moeten worden gevormd gebruikend een Cloud Manager config pijpleiding, zoals die in [ wordt beschreven dit artikel ](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

   * Nodig zodat de Adobe CDN de bron van de verzoeken kan bevestigen en `X-Forwarded-*` kopballen tot de AEM toepassing kan overgaan. Bijvoorbeeld, `X-Forwarded-For` wordt gebruikt om cliëntIP te bepalen. Zo, wordt het de verantwoordelijkheid van de vertrouwde op bezoeker (namelijk de klant beheerde CDN) om de juistheid van de `X-Forwarded-*` kopballen te verzekeren (zie de nota hieronder).
   * De toegang tot de ingangen van de Adobe CDN kan optioneel worden geblokkeerd wanneer er geen `X-AEM-Edge-Key` aanwezig is. Informeer Adobe als u directe toegang tot de ingangen van CDN van de Adobe (moet worden geblokkeerd) nodig hebt.

Zie de [ sectie van de de verkopersconfiguraties van de Steekproef CDN ](#sample-configurations) voor configuratievoorbeelden van belangrijke verkopers CDN.

Alvorens levend verkeer goed te keuren, zou u met klantensteun van de Adobe moeten bevestigen dat het verkeer dat van begin tot eind correct functioneert.

Nadat u `X-AEM-Edge-Key` hebt ingesteld, kunt u testen of de aanvraag correct is gerouteerd. Dit wordt als volgt weergegeven.

In Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

In Windows:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>Wanneer u uw eigen CDN gebruikt, hoeft u geen domeinen en certificaten in Cloud Manager te installeren. Het verpletteren in Adobe CDN wordt gedaan door het standaarddomein `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` te gebruiken, dat in het verzoek `Host` kopbal zou moeten worden verzonden. Als u de aanvraagheader `Host` overschrijft met een aangepaste domeinnaam, wordt de aanvraag mogelijk onjuist doorgestuurd via de Adobe-CDN of worden er 421 fouten gegenereerd.

>[!NOTE]
>
>De klanten die hun eigen CDN beheren zouden de integriteit van de kopballen moeten verzekeren die door naar AEM CDN worden verzonden. Het wordt bijvoorbeeld aanbevolen dat klanten alle `X-Forwarded-*` headers wissen en ze instellen op bekende en gecontroleerde waarden. `X-Forwarded-For` moet bijvoorbeeld het IP-adres van de client bevatten, terwijl `X-Forwarded-Host` de host van de site moet bevatten.

>[!NOTE]
>
>Sandbox-programmaomgevingen bieden geen ondersteuning voor een door de klant geleverde CDN.

De extra hop tussen klant CDN en AEM CDN is slechts nodig als er een geheim voorgeheugenmisser is. Door de strategieën van de geheim voorgeheugenoptimalisering te gebruiken die in dit artikel worden beschreven, zou de toevoeging van een klant CDN slechts verwaarloosbare latentie moeten introduceren.

Deze CDN-configuratie van de klant wordt ondersteund voor de publicatielaag, maar niet vóór de auteurslaag.

### Configuratie van foutopsporing

Gebruik de header `x-aem-debug` met de waarde `edge=true` om fouten op te sporen in een BYOCDN-configuratie. Bijvoorbeeld:

In Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -v -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>" -H "x-aem-debug: edge=true"
```

In Windows:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -v --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>" --header "x-aem-debug: edge=true"
```

Dit weerspiegelt bepaalde eigenschappen die worden gebruikt in de aanvraag in de antwoordheader van `x-aem-debug` . Bijvoorbeeld:

```
x-aem-debug: byocdn=true,edge=true,edge-auth=edge-auth,edge-key=edgeKey1,X-AEM-Edge-Key=set,host=publish-p87058-e257304-cmstg.adobeaemcloud.com,x-forwarded-host=wknd.site,adobe_unlocked_byocdn=true
```

Met behulp van deze methode kunt u bijvoorbeeld de waarden van de host controleren, of de randverificatie is geconfigureerd en de headerwaarde van de x-door:sturen-host, of een Edge-toets is ingesteld en welke sleutel wordt gebruikt (voor het geval één sleutel overeenkomt).

### Voorbeeld-CDN-leveranciersconfiguraties {#sample-configurations}

Hieronder worden verschillende configuratievoorbeelden van verschillende toonaangevende CDN-leveranciers weergegeven.

**Akamai**

![ Akamai1 ](assets/akamai1.png " Akamai ")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![ CloudFront1 ](assets/cloudfront1.png " Amazon CloudFront ")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![ Cloudflare1 ](assets/cloudflare1.png " Cloudflare ")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

### Algemene fouten {#common-errors}

De voorbeeldconfiguraties die worden geleverd, tonen de benodigde basisinstellingen. Nochtans, kan een klantenconfiguratie andere beïnvloedende regels hebben die, de kopballen verwijderen uitgeven of herschikken nodig voor AEM as a Cloud Service om het verkeer te dienen. Hieronder vindt u een aantal algemene fouten die optreden wanneer u een door de klant beheerde CDN configureert om naar AEM as a Cloud Service te wijzen.

**Redirection aan het publiceer de diensteindpunt**

Wanneer een verzoek een verboden antwoord van 403 ontvangt, betekent dit dat in het verzoek een aantal vereiste koppen ontbreken. Een algemene reden hiervoor is dat de CDN zowel het apex- als het `www` -domeinverkeer beheert, maar niet de juiste header voor het `www` -domein toevoegt. Dit probleem kan worden opgelost door de AEM as a Cloud Service CDN-logboeken te controleren en de benodigde aanvraagheaders te controleren.

**Fout 421 Verkeerd opnieuw richten**

Wanneer een aanvraag een fout van 421 ontvangt met een hoofdtekst rond `Requested host does not match any Subject Alternative Names (SANs) on TLS certificate` , geeft deze aan dat de HTTP `Host` -set niet overeenkomt met een host op de certificaten voor de host. Dit geeft meestal aan dat `Host` of de SNI-instelling onjuist is. Zorg ervoor dat zowel de instellingen voor `Host` als die voor SNI verwijzen naar de publicatie-p&lt;PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com host.


**teveel richt Lijn** opnieuw

Wanneer een pagina een &quot;Te veel Redirect&quot;lijn krijgt, wordt één of andere verzoekkopbal toegevoegd bij CDN die redirect aanpast die het terug naar zich dwingt. Als voorbeeld:

* Er wordt een CDN-regel gemaakt die overeenkomt met het apex-domein of het www-domein en de X-Forwarded-Host-header van alleen het apex-domein toevoegt.
* Een verzoek om een apex domein past deze CDN regel aan, die het apex domein als X-Door:sturen-Gastheer kopbal toevoegt.
* Er wordt een aanvraag verzonden naar de oorsprong waar een omleiding expliciet overeenkomt met de hostheader voor het apex-domein (bijvoorbeeld ^example.com).
* Er wordt een herschrijfregel geactiveerd die de aanvraag voor het apex-domein herschrijft naar https met het www-subdomein.
* Die omleiding wordt dan verzonden naar de rand van de klant, waar de CDN regel opnieuw teweeggebracht re-toevoegend de x-Door:sturen-Gastheer kopbal voor het apex domein niet www subdomain. Dan begint het proces opnieuw tot het verzoek ontbreekt.

Om dit probleem op te lossen, evalueert uw SSL omleidingsstrategie, CDN regels, richt en herschrijf regelcombinaties opnieuw.

## Geolocatiekoppen {#geo-headers}

De AEM beheerde CDN voegt kopballen aan elk verzoek met toe:

* landcode: `x-aem-client-country`
* continentale code: `x-aem-client-continent`

>[!NOTE]
>
>Als er een klant beheerde CDN is, wijzen deze kopballen op de plaats van de CDN volmachtsserver van de klant eerder dan de daadwerkelijke cliënt. De klanten zouden geolocatiekopballen door hun eigen CDN moeten beheren wanneer het gebruiken van een klant beheerde CDN.

De waarden voor de landcodes zijn Alpha-2 codes die onder [ worden beschreven ISO 3166-1 ](https://en.wikipedia.org/wiki/ISO_3166-1).

De waarden voor de continentale codes zijn:

* AF Afrika
* AN Antarctica
* AS Azië
* EU Europa
* NA North America
* OC Oceanië
* SA South America

Deze informatie is handig voor het doorsturen naar een andere URL op basis van het land van oorsprong van het verzoek. Gebruik de header Variëren voor het in cache plaatsen van reacties die afhankelijk zijn van geo-informatie. Omleidingen naar een specifieke landingspagina moeten bijvoorbeeld altijd `Vary: x-aem-client-country` bevatten. Indien nodig kunt u `Cache-Control: private` gebruiken om caching te voorkomen. Zie ook [ Caching ](/help/implementing/dispatcher/caching.md#html-text).
