---
title: Inleiding tot SSL-certificaten
description: Voor meer informatie over de zelfbedieningsprogramma's van Cloud Manager kunt u SSL-certificaten installeren en beheren.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: b94debebf36f379fc2cb2f193a244fe154c77537
workflow-type: tm+mt
source-wordcount: '1260'
ht-degree: 0%

---


# Inleiding tot SSL-certificaten{#introduction}

In deze video ziet u hoe u SSL-certificaten (Secure Socket Layer) installeert en beheert.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL-certificaten beheren"
>abstract="Leer hoe Cloud Manager functies voor zelfbediening heeft om SSL-certificaten te installeren en te beheren om uw site te beveiligen voor uw gebruikers. Cloud Manager gebruikt een platform-TLS-service voor het beheer van SSL-certificaten en persoonlijke sleutels die eigendom zijn van klanten en die zijn verkregen van certificeringsinstanties van derden."
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Een SSL-certificaat weergeven, bijwerken en vervangen"
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Status van een SSL-certificaat controleren"

## Wat zijn SSL-certificaten? {#overview}

Bedrijven en organisaties gebruiken SSL-certificaten (Secure Socket Layer) om hun websites te beveiligen en hun klanten in staat te stellen er vertrouwen in te stellen. Een webserver heeft een SSL-certificaat nodig om het SSL-protocol te kunnen gebruiken.

Wanneer een entiteit, zoals een organisatie of bedrijf, een certificaat aanvraagt van een certificeringsinstantie (CA), voltooit de CA een verificatieproces. Dit proces kan zich van het verifiëren van domeinnaamcontrole tot het verzamelen van de documenten van de bedrijfregistratie en abonneeovereenkomsten uitstrekken. Nadat de informatie van een entiteit is geverifieerd, ondertekent de CA hun openbare sleutel gebruikend de privé sleutel van CA. Omdat alle belangrijke Autoriteiten van het Certificaat wortelcertificaten in Webbrowsers hebben, wordt het certificaat van de entiteit verbonden door a *ketting van vertrouwen*, en Webbrowser erkent het als vertrouwd op certificaat.

>[!IMPORTANT]
>
>Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze onderdelen moeten worden verkregen van een certificeringsinstantie, een vertrouwde externe organisatie. Sommige bekende Autoriteiten van het Certificaat omvatten *DigiCert*, *versleutelings*, *GlobalSign*, *Vertrouwen*, en *Verisign*.

## Certificaten beheren met Cloud Manager {#cloud-manager}

Cloud Manager biedt zelfbedieningstools voor het installeren en beheren van SSL-certificaten, waarmee de sitebeveiliging voor uw gebruikers wordt gegarandeerd. Cloud Manager ondersteunt twee modellen voor het beheer van uw certificaten.

| | Model | Beschrijving |
| --- | --- | --- |
| A | **[Adobe-Beheerde SSL certificaat (DV)](#adobe-managed)** | Met Cloud Manager kunnen gebruikers DV-certificaten (Domain Validation) configureren die door Adobe worden geleverd voor snelle domeininstallatie. |
| B | **[Klantgeleid SSL certificaat (OV/EV)](#customer-managed)** | Cloud Manager biedt de dienst van platformTLS (de Veiligheid van de Laag van het Vervoer) aan om u te laten OV en EV SSL certificaten beheren die u en privé sleutels van de Autoriteiten van het Certificaat van de derde bezit, zoals *laat versleutelen*. |

Beide modellen bieden de volgende algemene functies voor het beheer van uw certificaten:

* Elke Cloud Manager-omgeving kan meerdere certificaten gebruiken.
* Een persoonlijke sleutel kan meerdere SSL-certificaten uitgeven.
* De platformTLS de dienstroutes verzoeken aan de dienst CDN van de klant die op het SSL certificaat wordt gebaseerd dat wordt gebruikt om te eindigen en de dienst CDN die gastheren dat domein.

>[!IMPORTANT]
>
>[&#x200B; om een douanedomein met een milieu &#x200B;](/help/implementing/cloud-manager/custom-domain-names/introduction.md) toe te voegen en te associëren, moet u een geldig SSL certificaat hebben dat het domein behandelt.

### Door Adobe beheerde SSL-certificaten (DV) {#adobe-managed}

DV-certificaten zijn het meest elementaire niveau van SSL-certificering en worden vaak gebruikt voor testdoeleinden of voor het beveiligen van websites met basiscodering. DV de certificaten zijn beschikbaar in zowel [&#x200B; productieprogramma&#39;s als zandbakprogramma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

Nadat het DV-certificaat is gemaakt, wordt dit door Adobe automatisch elke drie maanden vernieuwd, tenzij het wordt verwijderd.

>[!IMPORTANT]
>
>Als uw milieu (DV) SSL certificaten met een op CNAME-Gebaseerde bevestiging gebruikt, me ervan bewust ben dat het verwijderen van het CNAME- verslag voorafgaand aan automatische certificaatvernieuwing de vernieuwing kan veroorzaken om te ontbreken. De verwijdering kan leiden tot een vervaldatum van het certificaat en onderbreking van de service. Om deze kwestie te vermijden, zorg ervoor dat het CNAME- verslag door het volledige vernieuwingsproces op zijn plaats blijft. Het vernieuwingsproces baseert zich op de aanwezigheid van het verslag CNAME voor domeineigendomsbevestiging.

### Door de klant beheerde SSL-certificaten (OV/EV) {#customer-managed}

OV- en EV-certificaten bieden voor CA gevalideerde informatie. Met deze informatie kunnen gebruikers beoordelen of de eigenaar van de website, de e-mailafzender of de digitale handtekening van code of PDF-documenten kan worden vertrouwd. DV-certificaten staan een dergelijke eigendomsverificatie niet toe.

OV en EV bieden deze functies bovendien via DV-certificaten in Cloud Manager.

* Meerdere omgevingen kunnen een OV/EV-certificaat gebruiken. Dat wil zeggen dat het eenmaal kan worden toegevoegd, maar meerdere keren wordt gebruikt.
* Elk OV/EV-certificaat bevat doorgaans meerdere domeinen.
* Cloud Manager accepteert OV/EV-jokertekens voor een domein.

>[!TIP]
>
>Als u meerdere aangepaste domeinen hebt, is het mogelijk dat u niet elke keer een certificaat wilt uploaden wanneer u een nieuw domein toevoegt. In dat geval kunt u profiteren van het verkrijgen van één certificaat dat meerdere domeinen bestrijkt.

#### Vereisten voor door de klant beheerde OV/EV SSL-certificaten {#requirements}

Als u ervoor kiest om uw eigen door de klant beheerde SSL-certificaat toe te voegen, moet het voldoen aan de volgende bijgewerkte vereisten:

* DV-certificaten (Domain Validation, domeinvalidatie) en zelfondertekende certificaten worden niet ondersteund.
* Het certificaat moet voldoen aan het OV- (Organisatie Validatie) of EV-beleid (Uitgebreide Validatie).
* Het certificaat moet een X.509 TLS-certificaat zijn dat is uitgegeven door een vertrouwde certificeringsinstantie (CA).
* Tot de ondersteunde cryptografische sleuteltypen behoren:

   * RSA 2048-bits, standaardondersteuning.
RSA-sleutels die groter zijn dan 2048 bits (zoals 3072-bits of 4096-bits RSA-sleutels) worden op dit moment niet ondersteund.
   * Elliptische curvetoetsen (EC) `prime256v1` (`secp256r1`) en `secp384r1`
   * ECDSA-certificaten (Elliptic Curve Digital Signature Algorithm). Dergelijke certificaten worden Adobe-geadviseerd over RSA voor betere prestaties, veiligheid, en efficiency.

* Certificaten moeten de juiste notatie hebben om te slagen voor validatie. Persoonlijke sleutels moeten de `PKCS#8` -indeling hebben.

>[!NOTE]
>Als uw organisatie naleving gebruikend sleutels met 3072 bits RSA vereist, is het Adobe-geadviseerde alternatief ECDSA certificaten (`secp256r1` of `secp384r1`) te gebruiken.


#### Aanbevolen procedures voor certificaatbeheer

* **vermijd overlappende certificaten:**

   * Gebruik geen overlappende certificaten die overeenkomen met hetzelfde domein om een vloeiend certificaatbeheer te garanderen. Als u bijvoorbeeld een jokertekencertificaat (*.example.com) naast een specifiek certificaat (dev.example.com) hebt, kan dit leiden tot verwarring.
   * De laag TLS geeft voorrang aan het meest specifieke en onlangs opgestelde certificaat.

  Voorbeelden:

   * &quot;Dev Certificate&quot; dekt `dev.example.com` en wordt geïmplementeerd als een domeintoewijzing voor `dev.example.com` .
   * Met &quot;werkgebiedcertificaat&quot; wordt `stage.example.com` bestreken en wordt het geïmplementeerd als een domeintoewijzing voor `stage.example.com` .
   * Als het &quot;Certificaat van het Stadium&quot;*na* &quot;Dev Certificaat wordt opgesteld/bijgewerkt,&quot;het ook verzoeken voor `dev.example.com` dient.

     Om dergelijke conflicten te vermijden, zorg ervoor dat de certificaten zorgvuldig scoped aan hun voorgenomen domeinen zijn.

* **Certificaten van de Vervanging:**

  Jokertekens worden wel ondersteund (bijvoorbeeld `*.example.com` ), maar moeten alleen worden gebruikt als dat nodig is. In geval van overlapping krijgt het specifiekere certificaat voorrang. Het specifieke certificaat dient bijvoorbeeld `dev.example.com` in plaats van het jokerteken (`*.example.com`).

* **Bevestiging en het oplossen van problemen:**
Voordat u probeert een certificaat te installeren met Cloud Manager, raadt Adobe u aan de integriteit van het certificaat lokaal te valideren met gereedschappen zoals `openssl` . Bijvoorbeeld:

  `openssl verify -untrusted intermediate.pem certificate.pem`


<!--
>[!NOTE]
>
>If two certificates cover the same domain are installed, the one that is more exact is applied.
>
>For example, if your domain is `dev.adobe.com` and you have one certificate for `*.adobe.com` and another for `dev.adobe.com`, the more specific one (`dev.adobe.com`) is used.
-->

#### Indeling voor door de klant beheerde certificaten {#certificate-format}

SSL-certificaatbestanden moeten de PEM-indeling hebben om bij Cloud Manager te worden geïnstalleerd. Algemene bestandsextensies in de PEM-indeling zijn onder andere `.pem,` . `crt` , `.cer` en `.cert` .

De volgende `openssl` -opdrachten kunnen worden gebruikt om niet-PEM-certificaten om te zetten.

* PFX converteren naar PEM

  ```shell
  openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
  ```

* P7B converteren naar PEM

  ```shell
  openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
  ```

* DER converteren naar PEM

  ```shell
  openssl x509 -inform der -in certificate.cer -out certificate.pem
  ```

## Beperkingen {#limitations}

### Aantal geïnstalleerde SSL-certificaten {#number-installed-ssl-certs}

Cloud Manager biedt op elk moment ondersteuning voor maximaal 70 geïnstalleerde certificaten. Deze certificaten kunnen aan één of meerdere milieu&#39;s over uw programma worden geassocieerd en ook om het even welke verlopen certificaten omvatten.

Als u de limiet hebt bereikt, controleert u uw certificaten en kunt u eventueel verlopen certificaten verwijderen. U kunt ook meerdere domeinen in hetzelfde certificaat groeperen omdat een certificaat meerdere domeinen kan bestrijken (maximaal 100 SAN&#39;s).

### Laten we tarieflimieten coderen voor DV-certificaten die door Adobe worden beheerd

Adobe-beheerde DV-certificaten vertrouwen op Let&#39;s Encrypt. Naast de Cloud Manager-limiet voor geïnstalleerde certificaten, dwingt Encrypt zijn eigen tarieflimieten af. Één zeer belangrijke grens is **Nieuwe Certificaten per Exacte Reeks van Herkenningstekens**: tot 5 certificaten kunnen voor de zeer zelfde reeks hostnames binnen om het even welke periode van 7 dagen worden uitgegeven. Als deze limiet is bereikt, wordt een fout weergegeven en kunnen er geen certificaten meer worden gemaakt voor de hostnaam die is ingesteld totdat het snelheidslimietvenster opnieuw is ingesteld. Voor de recentste waarden en andere verwante grenzen, zie [&#x200B; tarief-grenzen documentatie &#x200B;](https://letsencrypt.org/docs/rate-limits/#new-certificates-per-exact-set-of-identifiers) van de Encrypt.

## Meer informatie {#learn-more}

Een gebruiker met de vereiste machtigingen kan Cloud Manager gebruiken om SSL-certificaten voor een programma te beheren. Raadpleeg de volgende documenten voor meer informatie over het gebruik van deze functies.

* [&#x200B; voeg een SSL certificaat toe &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [&#x200B; beheer SSL certificaten &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

