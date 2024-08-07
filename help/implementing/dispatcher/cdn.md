---
title: CDN in AEM as a Cloud Service
description: Leer hoe te om AEM-geleide CDN te gebruiken en hoe te om uw eigen CDN aan AEM-beheerde CDN te richten.
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
role: Admin
source-git-commit: 655b92f0fd3c6fb69bdd9343719537d6328fa7be
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 4%

---


# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties."

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

AEM-geleide CDN voldoet aan de prestaties en de veiligheidsvereisten van de meeste klant. Voor de publicatielaag kunnen klanten optioneel naar de laag verwijzen vanuit hun eigen CDN, die ze moeten beheren. Dit scenario wordt toegestaan op een geval-voor-geval basis, gebaseerd op het voldoen van bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun leverancier CDN heeft die moeilijk is te verlaten.

<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## CDN met AEM beheer  {#aem-managed-cdn}

Volg de onderstaande secties om Cloud Manager-gebruikersinterface voor zelfbediening te gebruiken voor het voorbereiden van de levering van inhoud met behulp van AEM kant-en-klare CDN:

1. [SSL-certificaten beheren](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beperkend verkeer**

Door gebrek, voor een AEM-beheerde opstelling CDN, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. U kunt verkeer tot de publicatiedienst voor een bepaald milieu beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) als gebruikersinterface van Cloud Manager.

Zie [ het Leiden IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) om meer te leren.

>[!CAUTION]
>
>Slechts worden de verzoeken van toegestane IPs gediend door AEM beheerde CDN. Als u uw eigen CDN aan AEM-beheerde CDN richt, dan zorg ervoor IPs van uw CDN in de lijst van gewenste personen inbegrepen is.

### Het vormen van Verkeer bij CDN {#cdn-configuring-cloud}

U kunt verkeer bij CDN op diverse manieren vormen, die omvatten:

* het blokkeren van kwaadwillig verkeer met [ Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md) (met inbegrip van naar keuze licentiable geavanceerde regels van WAF)
* het wijzigen van de aard van het [ verzoek en de reactie ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)
* het toepassen van 301/302 [ cliënt-zijredirects ](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)
* het verklaren van [ oorsprongselectors ](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) om volmacht een verzoek aan niet-AEM backends om te keren

Leer hoe te om deze eigenschappen te vormen door YAML- dossiers in git te gebruiken en hen op te stellen door de Pijpleiding van Cloud Manager [ te gebruiken Config ](/help/implementing/dispatcher/cdn-configuring-traffic.md).

### CDN-foutpagina&#39;s configureren {#cdn-error-pages}

Een CDN foutenpagina kan worden gevormd om de standaard, unbranded pagina met voeten te treden die aan browser in de zeldzame gebeurtenis wordt gediend die AEM niet kan worden bereikt. Voor meer details, zie [ Vormend CDN foutenpagina&#39;s ](/help/implementing/dispatcher/cdn-error-pages.md).

### Inhoud in cache wissen op de CDN {#purge-cdn}

Het plaatsen van TTL gebruikend HTTP Cachebeheer kopbal is een efficiënte benadering om de prestaties van de inhoudslevering en inhoudsversheid in evenwicht te brengen. In scenario&#39;s waarin het van essentieel belang is om onmiddellijk bijgewerkte inhoud te leveren, kan het echter nuttig zijn om de CDN-cache rechtstreeks leeg te maken.

Lees over [ vormend een zuiveringsAPI teken ](/help/implementing/dispatcher/cdn-credentials-authentication.md/#purge-API-token) en [ zuiverend caching inhoud CDN ](/help/implementing/dispatcher/cdn-cache-purge.md).

### Basisverificatie bij de CDN {#basic-auth}

Voor lichte gebruikersverificatiegevallen, waaronder die van zakelijke belanghebbenden die inhoud controleren, moet u de inhoud beschermen door een standaarddialoogvenster weer te geven waarin een gebruikersnaam en wachtwoord vereist zijn. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md) en sluit zich aan bij het vroege adopterprogramma.

## CDN van de klant wijst aan AEM beheerde CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="CDN van de klant wijst naar AEM Beheerde CDN"
>abstract="AEM als Cloud Service biedt klanten een optie om zijn bestaande CDN te gebruiken. Voor de publicatielaag kunnen klanten optioneel naar de laag verwijzen vanuit hun eigen CDN, die ze moeten beheren. Dit scenario wordt toegestaan op een geval-voor-geval basis, gebaseerd op het voldoen van bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun leverancier CDN heeft die moeilijk is te verlaten."

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het leiden en het richten aan AEM-beheerde CDN, op voorwaarde dat het volgende wordt voldaan:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De Klant moet CDN kunnen vormen om met AEM as a Cloud Service te werken - zie de hieronder vermelde configuratieinstructies.
* De klant moet ingenieurs CDN hebben die op vraag in geval-gerelateerde kwesties zijn.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Wijs de CDN toe aan de ingangen van de Adobe CDN als zijn oorsprongdomein. Bijvoorbeeld `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` .
1. Stel SNI in op de invoer van de Adobe CDN.
1. Stel de Hostkop in op het oorspronkelijke domein. Bijvoorbeeld: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` .
1. Stel de header `X-Forwarded-Host` in met de domeinnaam, zodat AEM de hostheader kan bepalen. Bijvoorbeeld: `X-Forwarded-Host:example.com` .
1. Stel `X-AEM-Edge-Key` in. De waarde zou moeten worden gevormd gebruikend een Cloud Manager config pijpleiding, zoals die in [ wordt beschreven dit artikel.](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value)

   * Nodig zodat de Adobe CDN de bron van de verzoeken kan bevestigen en `X-Forwarded-*` kopballen tot de AEM toepassing kan overgaan. Bijvoorbeeld, `X-Forwarded-For` wordt gebruikt om cliëntIP te bepalen. Zo, wordt het de verantwoordelijkheid van de vertrouwde op bezoeker (namelijk klant-beheerde CDN) om de juistheid van de `X-Forwarded-*` kopballen te verzekeren (zie de nota hieronder).
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
>Wanneer u uw eigen CDN gebruikt, hoeft u geen domeinen en certificaten in Cloud Manager te installeren. Het verpletteren in Adobe CDN wordt gedaan door het standaarddomein `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` te gebruiken dat in de verzoek `Host` kopbal zou moeten worden verzonden. Als u de aanvraagheader `Host` overschrijft met een aangepaste domeinnaam, kan de aanvraag onjuist worden gerouteerd door de Adobe-CDN.


>[!NOTE]
>
>De klanten die hun eigen CDN beheren zouden de integriteit van de kopballen moeten verzekeren die door naar AEM CDN worden verzonden. Het wordt bijvoorbeeld aanbevolen dat klanten alle `X-Forwarded-*` headers wissen en ze instellen op bekende en gecontroleerde waarden. `X-Forwarded-For` moet bijvoorbeeld het IP-adres van de client bevatten, terwijl `X-Forwarded-Host` de host van de site moet bevatten.

>[!NOTE]
>
>Sandbox programmamilieu&#39;s steunen geen klant-Geleverde CDN.

De extra hop tussen klant CDN en AEM CDN is slechts nodig als er een geheim voorgeheugenmisser is. Door de strategieën van de geheim voorgeheugenoptimalisering te gebruiken die in dit artikel worden beschreven, zou de toevoeging van een klant CDN slechts verwaarloosbare latentie moeten introduceren.

Deze CDN-configuratie van de klant wordt ondersteund voor de publicatielaag, maar niet vóór de auteurslaag.

### Voorbeeld van CDN-leveranciersconfiguraties {#sample-configurations}

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

De verstrekte steekproefconfiguraties tonen de basismontages nodig, maar een klantenconfiguratie kan andere beïnvloedende regels hebben die, de kopballen verwijderen wijzigen of herschikken nodig voor AEM as a Cloud Service om het verkeer te dienen. Hieronder vindt u een aantal algemene fouten die optreden wanneer u een door de klant beheerde CDN configureert om naar AEM as a Cloud Service te wijzen.

**Redirection aan het Eindpunt van de Dienst van Publish**

Wanneer een verzoek een verboden antwoord van 403 ontvangt, betekent dit dat in het verzoek een aantal vereiste koppen ontbreken. Een algemene reden hiervoor is dat de CDN zowel het apex- als het `www` -domeinverkeer beheert, maar niet de juiste header voor het `www` -domein toevoegt. Dit probleem kan worden opgelost door de AEM as a Cloud Service CDN-logboeken te controleren en de benodigde aanvraagheaders te controleren.

**Te veel richt Lijn** om

Wanneer een pagina een &quot;Te veel Redirect&quot;lijn krijgt, wordt één of andere verzoekkopbal toegevoegd bij CDN die redirect aanpast die het terug naar zich dwingt. Als voorbeeld:

* Er wordt een CDN-regel gemaakt die overeenkomt met het apex-domein of het www-domein en de X-Forwarded-Host-header van alleen het apex-domein toevoegt.
* Een verzoek om een apex domein past deze CDN regel aan, die het apex domein als X-Door:sturen-Gastheer kopbal toevoegt.
* Er wordt een aanvraag verzonden naar de oorsprong waar een omleiding expliciet overeenkomt met de hostheader voor het apex-domein (bijvoorbeeld ^example.com).
* Er wordt een herschrijfregel geactiveerd die de aanvraag voor het apex-domein herschrijft naar https met het www-subdomein.
* Die omleiding wordt dan verzonden naar de rand van de klant, waar de CDN regel opnieuw teweeggebracht re-toevoegend de x-Door:sturen-Gastheer kopbal voor het apex domein niet www subdomain. Dan begint het proces opnieuw tot het verzoek ontbreekt.

Om dit probleem op te lossen, evalueert uw SSL omleidingsstrategie, CDN regels, richt en herschrijf regelcombinaties opnieuw.

## Geolocatie-headers {#geo-headers}

De AEM-beheerde CDN voegt kopballen aan elk verzoek met toe:

* landcode: `x-aem-client-country`
* continentale code: `x-aem-client-continent`

>[!NOTE]
>
>Als er een klant-geleide CDN is, wijzen deze kopballen op de plaats van de klantenCDN volmachtsserver eerder dan de daadwerkelijke cliënt. Daarom voor klant-beheerde CDN, zouden de geolocatiekopballen door klanten CDN moeten worden beheerd.

De waarden voor de landcodes zijn Alpha-2 die codes [ hier ](https://en.wikipedia.org/wiki/ISO_3166-1) worden beschreven.

De waarden voor de continentale codes zijn:

* AF Afrika
* AN Antarctica
* AS Azië
* EU Europa
* NA North America
* OC Oceanië
* SA South America

Deze informatie kan nuttig zijn in gevallen zoals omleiding naar een andere URL op basis van de oorsprong (land) van het verzoek. Gebruik de header Variëren voor het in cache plaatsen van reacties die afhankelijk zijn van geo-informatie. Omleidingen naar een specifieke landingspagina moeten bijvoorbeeld altijd `Vary: x-aem-client-country` bevatten. Indien nodig kunt u `Cache-Control: private` gebruiken om caching te voorkomen. Zie ook [ Caching ](/help/implementing/dispatcher/caching.md#html-text).
