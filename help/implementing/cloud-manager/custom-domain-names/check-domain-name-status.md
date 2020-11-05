---
title: Status domeinnaam controleren
description: Status domeinnaam controleren
translation-type: tm+mt
source-git-commit: 91b06bcd96fe8a37c3fb20ef90e1684f6d19183f
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Status domeinnaam controleren {#check-status}

U kunt bepalen of uw domeinnaam met succes is geverifieerd door op het statuspictogram voor de domeinnaam te klikken in de tabel betreffende omgevingen op de pagina Domeininstellingen.

>[!NOTE]
>Cloud Manager activeert automatisch een TXT-verificatie wanneer u Opslaan selecteert in de verificatiestap van de wizard Aangepast domein toevoegen. Voor verdere controles, moet u actief het &quot;verifieer opnieuw&quot;pictogram naast de status selecteren. AFBEELDING INVOEGEN

Cloud Manager controleert het eigendom van domeinen via de TXT-waarde en geeft een van de volgende statusberichten weer:

* **Domeinverificatie mislukt** TXT-waarde ontbreekt of wordt met fouten gedetecteerd. Volg de instructies en probeer het opnieuw. Wanneer u klaar bent, moet u het pictogram &quot;Opnieuw controleren&quot; naast de status selecteren.

* **Domeinverificatie bezig** met verificatie. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw controleren&quot; naast de status hebt geselecteerd.

* **Verified, Deployment Failed** TXT verification was successfully. De CDN-implementatie is echter mislukt. Een vertegenwoordiger van de Adobe wordt automatisch op de hoogte gesteld.

* **Domein geverifieerd en geïmplementeerd** Deze status geeft aan dat uw aangepaste domeinnaam klaar is om te worden gebruikt. Opmerking: Op dit moment is uw aangepaste domeinnaam klaar om te worden getest en moet deze naar de domeinnaam van Cloud Manager worden verwezen. Ga naar het Vormen DNS de VERBINDING van het TUSSENVOEGSEL van Montages leren hoe te om dit te doen.

* **Verwijderen** van aangepaste domeinnaam wordt verwerkt.

* **Verwijderen** van aangepaste domeinnaam is mislukt. U moet het opnieuw proberen. Ga naar Aangepaste domeinnaam verwijderen voor meer informatie over het onderwerp.


## DNS-instellingen configureren {#configure-dns}

Nadat uw naam van het douanedomein met succes wordt geverifieerd en opgesteld, bent u bereid om de DNS verslagen voor uw naam van het douanedomein met uw DNS leverancier bij te werken. Hierdoor kan uw site bezoekers bedienen. Deze activiteit wordt daarom typisch gedaan vóór Go-live.

>[!NOTE]
>U of het aangewezen individu in uw organisatie moet login of uw DNS leverancier (het bedrijf kunnen contacteren van wie u het domein van) kocht en updates in uw DNS montages maken.

Hiervoor moet u bepalen of u uw DNS-instellingen moet configureren voor een `CNAME` of Apex-record die uw aangepaste domeinnaam verwijst naar de domeinnaam van Cloud Manager. Een `CNAME` of een verslag, zodra provisioned zal al Internet verkeer voor het domein leiden aan waar het richt. Als die plaats niet provisioned is om het verkeer te dienen, zal er een stroomonderbreking zijn. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en de klant klaar is voor Go-Live.

### CNAME-record {#cname-record}

De volgende secties zullen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

Een Canonical Name of `CNAME` record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein toe te wijzen, zoals `www.example.com` het domein dat de inhoud van dat subdomein host.

Meld u aan bij uw Domeinregister en maak een CNAME-record om de aangepaste domeinnaam naar het doel te verwijzen, zoals hieronder wordt weergegeven:

| CNAME | Aangepast domeinnaampunt voor doel |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |
