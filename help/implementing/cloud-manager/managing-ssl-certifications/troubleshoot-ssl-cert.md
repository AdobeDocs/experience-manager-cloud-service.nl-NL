---
title: SSL-certificaatfouten oplossen
description: Leer hoe u SSL-certificaatfouten kunt oplossen door algemene oorzaken aan te geven, zodat u veilige verbindingen kunt onderhouden.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ff8c7fb21b4d8bcf395d28c194a7351281eef45b
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# SSL-certificaatfouten oplossen {#certificate-errors}

Er kunnen bepaalde fouten optreden als een certificaat niet correct is geïnstalleerd of niet voldoet aan de eisen van Cloud Manager.

+++**Ongeldig certificaat**

Deze fout treedt op omdat de klant een gecodeerde persoonlijke sleutel heeft toegevoegd en een persoonlijke sleutel met de indeling DER heeft gebruikt.

+++

+++**Persoonlijke sleutel moet formaat PKCS 8 zijn**

Deze fout treedt op omdat de klant een gecodeerde persoonlijke sleutel heeft toegevoegd en een persoonlijke sleutel met de indeling DER heeft gebruikt.

+++

+++**Correcte certificaatorde**

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

Wanneer u een certificaat toevoegt, als er een fout optreedt die lijkt op het volgende:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Waarschijnlijk hebt u het clientcertificaat opgenomen in de certificaatketen. Zorg ervoor dat de keten het clientcertificaat niet bevat en probeer het opnieuw.

+++

+++**beleid van het Certificaat**

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

+++**de geldigheidsdata van het Certificaat**

Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is vanaf de huidige datum. Controleer de geldigheid van de certificaatketen.

+++