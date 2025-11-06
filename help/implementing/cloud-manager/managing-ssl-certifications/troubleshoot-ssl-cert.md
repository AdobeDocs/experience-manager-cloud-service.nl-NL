---
title: Problemen met SSL-certificaten oplossen
description: Leer hoe u problemen met SSL-certificaten kunt oplossen door algemene oorzaken aan te geven, zodat u veilige verbindingen kunt onderhouden.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 8fb8f708-51a5-46d0-8317-6ce118a70fab
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# SSL-certificaatproblemen oplossen {#certificate-problems}

Leer hoe u problemen met SSL-certificaten kunt oplossen door algemene oorzaken aan te geven, zodat u veilige verbindingen kunt onderhouden.

+++**Ongeldig certificaat**

## Ongeldig certificaat {#invalid-certificate}

Deze fout treedt op omdat de klant een gecodeerde persoonlijke sleutel heeft gebruikt en de sleutel in DER-indeling heeft verstrekt.

+++

+++**Persoonlijke sleutel moet formaat PKCS 8 zijn**

## Persoonlijke sleutel moet de PKCS 8-indeling hebben {#pkcs-8}

Deze fout treedt op omdat de klant een gecodeerde persoonlijke sleutel heeft gebruikt en de sleutel in DER-indeling heeft verstrekt.

+++

+++**Correcte certificaatorde**

## Certificaatvolgorde corrigeren {#certificate-order}

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

+++ 

+++**verwijder cliëntcertificaten**

## Clientcertificaten verwijderen {#client-certificates}

Wanneer u een certificaat toevoegt, als er een fout optreedt die lijkt op het volgende:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Waarschijnlijk hebt u het clientcertificaat opgenomen in de certificaatketen. Zorg ervoor dat de keten het clientcertificaat niet bevat en probeer het opnieuw.

+++

+++**beleid van het Certificaat**

## Certificaatbeleid {#policy}

Controleer het beleid van uw certificaat als de volgende fout optreedt.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

Ingesloten OID-waarden identificeren gewoonlijk het certificaatbeleid. Het uitvoeren van een certificaat naar tekst en het zoeken naar OID onthult het beleid van het certificaat.

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

+++

+++**Geldigheid van certificaten

## Geldigheid van certificaat {#validity}

Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is vanaf de huidige datum. Controleer de geldigheid van de certificaatketen.

+++

+++**Onjuist SAN-certificaat is toegepast op mijn domein

## Onjuist SAN-certificaat is toegepast op mijn domein {#wrong-san-cert}

Laten we zeggen dat u `dev.yoursite.com` en `stage.yoursite.com` wilt koppelen aan uw niet-productieomgeving en `prod.yoursite.com` aan uw productieomgeving.

Als u de CDN voor deze domeinen wilt configureren, hebt u een certificaat nodig dat voor elk domein is geïnstalleerd. U installeert dus één certificaat dat `*.yoursite.com` voor de niet-productiedomeinen dekt en een ander certificaat dat `*.yoursite.com` ook voor uw productiedomeinen dekt.

Deze configuratie is geldig. Wanneer u echter een van de certificaten bijwerkt, omdat beide certificaten dezelfde SAN-invoer dekken, installeert de CDN het meest recente certificaat op alle toepasselijke domeinen, wat onverwacht kan lijken.

Hoewel dit onverwacht kan zijn, is dit geen fout en is het standaardgedrag van onderliggende CDN. Als u twee of meer SAN-certificaten hebt die betrekking hebben op hetzelfde SAN-domeinitem en dat domein wordt gedekt door één certificaat en het andere wordt bijgewerkt, wordt het laatste domein nu geïnstalleerd voor het domein.

+++
