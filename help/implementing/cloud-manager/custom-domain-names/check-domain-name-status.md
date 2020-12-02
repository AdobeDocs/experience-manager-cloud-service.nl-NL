---
title: Status domeinnaam controleren
description: Status domeinnaam controleren
translation-type: tm+mt
source-git-commit: 5cd22d8af20bb947e4cdab448cf8f20c6596bb2e
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# Status domeinnaam {#check-status} controleren

U kunt bepalen of uw domeinnaam met succes is geverifieerd door op het statuspictogram voor de domeinnaam te klikken in de tabel betreffende omgevingen op de pagina Domeininstellingen.

>[!NOTE]
>Cloud Manager activeert automatisch een TXT-verificatie wanneer u Opslaan selecteert in de verificatiestap van de wizard Aangepast domein toevoegen. Voor verdere controles, moet u actief het &quot;verifieer opnieuw&quot;pictogram naast de status selecteren. AFBEELDING INVOEGEN

Cloud Manager controleert het eigendom van domeinen via de TXT-waarde en geeft een van de volgende statusberichten weer:

* **Domeinverificatie**
FailedTXT-waarde ontbreekt of wordt met fouten gedetecteerd. Volg de instructies en probeer het opnieuw. Wanneer u klaar bent, moet u het pictogram &quot;Opnieuw controleren&quot; naast de status selecteren.

* **Domeinverificatie In**
ProgressVerification wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw controleren&quot; naast de status hebt geselecteerd.

* **Verified, Deployment**
FailedTXT verification was successfully. De CDN-implementatie is echter mislukt. Een vertegenwoordiger van de Adobe wordt automatisch op de hoogte gesteld.

* **Domein geverifieerd en**
geïmplementeerdDeze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt. Opmerking: Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen. Ga naar het Vormen DNS de VERBINDING van het TUSSENVOEGSEL van Montages leren hoe te om dit te doen.

* ****
DeletingDeletion of Custom Domain name is in process.

* **Verwijderen**
FailedDeletion of Custom Domain name failed. U moet het opnieuw proberen. Ga naar Aangepaste domeinnaam verwijderen voor meer informatie over het onderwerp.


## DNS-instellingen configureren {#configure-dns}

Nadat uw naam van het douanedomein met succes wordt geverifieerd en opgesteld, bent u bereid om de DNS verslagen voor uw naam van het douanedomein met uw DNS leverancier bij te werken. Hierdoor kan uw site bezoekers bedienen. Deze activiteit wordt daarom typisch gedaan vóór Go-live.

>[!NOTE]
>U of het aangewezen individu in uw organisatie moet login of uw DNS leverancier (het bedrijf kunnen contacteren van wie u het domein van) kocht en updates in uw DNS montages maken.

Hiervoor moet u bepalen of u uw DNS-instellingen moet configureren naar een `CNAME`- of Apex-record die uw aangepaste domeinnaam verwijst naar de domeinnaam van Cloud Manager. Een `CNAME` of een verslag, zodra provisioned zal al Internet verkeer voor het domein leiden aan waar het richt. Als die plaats niet provisioned is om het verkeer te dienen, zal er een stroomonderbreking zijn. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en de klant klaar is voor Go-Live.

### CNAME-record {#cname-record}

De volgende secties zullen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

Een Canonical Name- of `CNAME`-record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein, zoals `www.example.com`, toe te wijzen aan het domein dat de inhoud van dat subdomein host.

Meld u aan bij uw Domeinregister en maak een CNAME-record om de aangepaste domeinnaam naar het doel te verwijzen, zoals hieronder wordt weergegeven:

| CNAME | Aangepast domeinnaampunt voor doel |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

### APEX-record {#apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals example.com. Een apex domein wordt gevormd met `A`, `ALIAS`, of `ANAME` verslag door uw DNS leverancier. De Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg alle volgende A verslagen aan DNS van uw Domein montages via uw domeinleverancier toe:

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

## DNS-recordstatus {#check-status-dns-record} controleren

U kunt bepalen of uw domeinnaam correct aan uw AEM als website van de Cloud Service door het pictogram van de Status voor het DNS verslag van de lijst op de Milieu&#39;s van de pagina van de Montages van het Domein te klikken oplost. Cloud Manager voert een DNS-zoekopdracht voor uw domeinnaam uit en geeft een van de volgende statusberichten weer:

>[!NOTE]
>Cloud Manager zal automatisch een DNS raadpleging teweegbrengen wanneer uw Naam van het Domein van de Douane eerst met succes wordt geverifieerd en wordt opgesteld. Voor verdere pogingen, moet u actief **oplossen opnieuw** pictogram naast de status selecteren. AFBEELDING INVOEGEN

* **DNS status not**
detectedDNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld. Deze status wordt ook waargenomen wanneer uw naam van het Domein van de Douane in het proces van schrapping is.

* **DNS lost**
Incorrect opThis wijst erop dat of DNS archiefconfiguratie nog niet heeft opgelost/over gewezen of onjuist is. Een vertegenwoordiger van de Adobe wordt automatisch op de hoogte gesteld.

   >[!NOTE]
   >U moet of `CNAME` of `A-record` door de overeenkomstige instructies te volgen vormen. Ga naar het Vormen DNS de VERBINDING van het TUSSENVOEGSEL van Montages om meer over het onderwerp te leren. Wanneer u klaar bent, moet u het pictogram &#39;Opnieuw oplossen&#39; naast de status selecteren.

* **DNS-resolutie In**
ProgressResolution wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw oplossen&quot; naast de status hebt geselecteerd.

* **DNS lost**
correct op Uw DNS montages worden behoorlijk gevormd. Uw site is bestemd voor bezoekers.
