---
title: Een SSL-certificaat toevoegen
description: Leer hoe u uw eigen SSL-certificaat kunt toevoegen met de zelfbedieningsprogramma's van Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Een SSL-certificaat toevoegen {#adding-an-ssl-certificate}

Leer hoe u uw eigen SSL-certificaat kunt toevoegen met de zelfbedieningsprogramma&#39;s van Cloud Manager.

>[!TIP]
>
>Een certificaat kan een paar dagen aan levering vergen. De Adobe beveelt daarom aan dat het certificaat ruim van tevoren wordt verstrekt.

## Certificaatvereisten {#certificate-requirements}

Herzie de sectie **Vereisten van het Certificaat** van de document [ Inleiding aan het Leiden SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) om ervoor te zorgen dat het certificaat u wilt toevoegen door AEM as a Cloud Service wordt gesteund.

## Een certificaat toevoegen {#adding-a-cert}

Ga als volgt te werk om een certificaat toe te voegen met Cloud Manager.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan **Milieu&#39;s** scherm van de **pagina van het Overzicht**.

1. Klik **SSL Certificaten** van het linkernavigatievenster. Een tabel met details van bestaande SSL-certificaten wordt weergegeven op het hoofdscherm.

   ![ Toevoegend een SSL cert ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klik **toevoegen SSL Certificaat** om **te openen voeg SSL de dialoogdoos van het Certificaat** toe.

   * Ga een naam voor uw certificaat in **Naam van het Certificaat** in.
      * Dit is alleen ter informatie en kan elke naam zijn waarmee u gemakkelijk naar uw certificaat kunt verwijzen.
   * Plak het **Certificaat**, **Persoonlijke sleutel**, en **de ketting van het Certificaat** waarden in hun respectieve gebieden. Alle drie velden zijn verplicht.
   * In sommige gevallen kan het certificaat van de eindgebruiker in de keten worden opgenomen en moet het worden verwijderd voordat de keten in het veld wordt geplakt.

   ![ voeg SSL de dialoog van het Certificaat toe ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * Eventuele fouten worden weergegeven.
      * U moet alle fouten aanpakken voordat uw certificaat kan worden opgeslagen.
      * Zie [ sectie van de Fouten van het Certificaat ](#certificate-errors) om meer over het richten van gemeenschappelijke fouten te leren.

1. Klik **sparen** om uw certificaat te bewaren.

Als het certificaat eenmaal is opgeslagen, wordt het weergegeven als een nieuwe rij in de tabel.

![ Opgeslagen SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

>[!NOTE]
>
>Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** zijn om een SSL certificaat in Cloud Manager te installeren.

>[!NOTE]
>
>Als u een fout ontvangt die vergelijkbaar is met `The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.` , hebt u waarschijnlijk het clientcertificaat opgenomen in de certificaatketen. Zorg ervoor dat het clientcertificaat niet in de keten is opgenomen en probeer het opnieuw.

## Certificaatfouten {#certificate-errors}

Er kunnen bepaalde fouten optreden als een certificaat niet correct is geïnstalleerd of voldoet aan de eisen van Cloud Manager.

### Certificaatbeleid {#certificate-policy}

Controleer het beleid van uw certificaat als de volgende fout optreedt.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

Het certificaatbeleid wordt gewoonlijk bepaald door ingesloten OID-waarden. Als u een certificaat op tekst uitvoert en naar de OID zoekt, wordt het beleid van het certificaat weergegeven.

U kunt de certificaatdetails als tekst uitvoeren gebruikend het volgende voorbeeld als gids.

```text
openssl x509 -in 9178c0f58cb8fccc.pem -text
certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            91:78:c0:f5:8c:b8:fc:cc
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = US, ST = Arizona, L = Scottsdale, O = "GoDaddy.com, Inc.", OU = http://certs.godaddy.com/repository/, CN = Go Daddy Secure Certificate Authority - G2
        Validity
            Not Before: Nov 10 22:55:36 2021 GMT
            Not After : Dec  6 15:35:06 2022 GMT
        Subject: C = US, ST = Colorado, L = Denver, O = Alexandra Alwin, CN = adobedigitalimpact.com
        Subject Public Key Info:
...
```

Het OID-patroon in de tekst definieert het beleidstype van het certificaat.

| Patroon | Beleid | Aanvaardbaar in Cloud Manager |
|---|---|---|
| `2.23.140.1.1` | EV | Ja |
| `2.23.140.1.2.2` | OV | Ja |
| `2.23.140.1.2.1` | DV | Nee |

Door `grep` voor de patronen OID in de tekst van het outputcertificaat te pingelen, kunt u uw certificaatbeleid bevestigen.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```

### Certificaatvolgorde corrigeren {#correct-certificate-order}

De gemeenschappelijkste reden voor een certificaatplaatsing om te ontbreken is dat de midden of kettingcertificaten niet in de correcte orde zijn.

Tussentijdse certificaatbestanden moeten eindigen met het basiscertificaat of het certificaat dat zich het dichtst bij het basiscertificaat bevindt. Ze moeten in aflopende volgorde staan, van het `main/server` -certificaat tot aan het basiscertificaat.

U kunt de orde van uw middendossiers bepalen gebruikend het volgende bevel.

```shell
openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout
```

Met de volgende opdrachten kunt u controleren of de persoonlijke sleutel en het `main/server` -certificaat overeenkomen.

```shell
openssl x509 -noout -modulus -in certificate.pem | openssl md5
```

```shell
openssl rsa -noout -modulus -in ssl.key | openssl md5
```

>[!NOTE]
>
>De uitvoer van deze twee opdrachten moet exact hetzelfde zijn. Als u geen overeenkomende persoonlijke sleutel voor uw `main/server` -certificaat kunt vinden, moet u het certificaat opnieuw sleutelken door een nieuwe CSR te genereren en/of een bijgewerkt certificaat aan te vragen bij uw SSL-leverancier.

### Geldigheidsdatums certificaat {#certificate-validity-dates}

Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is vanaf de huidige datum. Controleer de geldigheid van de certificaatketen.
