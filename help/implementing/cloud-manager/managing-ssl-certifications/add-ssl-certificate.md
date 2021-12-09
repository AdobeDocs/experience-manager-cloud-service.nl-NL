---
title: Een SSL-certificaat toevoegen - SSL-certificaten beheren
description: Een SSL-certificaat toevoegen - SSL-certificaten beheren
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
source-git-commit: 828490e12d99bc8f4aefa0b41a886f86fee920b4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Een SSL-certificaat toevoegen {#adding-an-ssl-certificate}

>[!NOTE]
>AEM as a Cloud Service accepteert alleen certificaten die voldoen aan het OV- (Organisatie-validatie) of EV-beleid (Extended Validation). Het DV-beleid (Domain Validation) wordt niet geaccepteerd. Bovendien moet elk certificaat een X.509 TLS-certificaat zijn van een vertrouwde certificeringsinstantie (CA) met een overeenkomende 2048-bits RSA-privésleutel. AEM as a Cloud Service accepteert jokertekens voor SSL-certificaten voor een domein.

Een Certificaat neemt een paar dagen in beslag om te verstrekken en het wordt geadviseerd om het certificaat zelfs maanden van tevoren te provisioning. Zie [Een SSL-certificaat ophalen](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) voor meer informatie .

## Certificaatindeling {#certificate-format}

SSL-bestanden moeten de PEM-indeling hebben om te kunnen worden geïnstalleerd in Cloud Manager. Algemene bestandsextensies die binnen de PEM-indeling vallen, zijn onder meer `.pem,` .`crt`, `.cer`, en `.cert`.

Voer de onderstaande stappen uit om de indeling van uw SSL-bestanden te converteren naar PEM:

* PFX converteren naar PEM

   `openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

* P7B converteren naar PEM

   `openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

* DER converteren naar PEM

   `openssl x509 -inform der -in certificate.cer -out certificate.pem`

## Belangrijke overwegingen {#important-considerations}

* Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat te installeren in Cloud Manager.

* Cloud Manager staat op elk gewenst moment maximaal 10 SSL-certificaten toe die kunnen worden gekoppeld aan een of meer omgevingen in uw gehele programma, zelfs als het certificaat is verlopen. Met de interface van Cloud Manager kunnen echter maximaal 50 SSL-certificaten met deze beperking in het programma worden geïnstalleerd. Doorgaans kan een certificaat meerdere domeinen (tot 100 SAN&#39;s) bestrijken. U kunt dus overwegen meerdere domeinen in hetzelfde certificaat te groeperen om binnen deze limiet te blijven.


## Een certificaat toevoegen {#adding-a-cert}

Voer de onderstaande stappen uit om een certificaat toe te voegen:

1. Meld u aan bij Cloud Manager.
1. Navigeren naar **Omgevingen** scherm van **Overzicht** pagina.
1. Klikken op **SSL-certificaten** in het navigatiemenu aan de linkerkant. Op dit scherm wordt een tabel weergegeven met de details van bestaande SSL-certificaten.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klikken op **SSL-certificaat toevoegen** openen **SSL-certificaat toevoegen** in.

   * Geef een naam op voor uw certificaat in **Certificaatnaam**. Dit kan elke naam zijn die u helpt gemakkelijk naar uw certificaat te verwijzen.
   * Plak de **Certificaat**, **Persoonlijke sleutel** en **Certificaatketen** in hun respectieve velden. Gebruik het plakpictogram rechts van het invoervak.
De drie velden zijn niet optioneel en moeten worden opgenomen.

      ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)


      >[!NOTE]
      >Eventuele fouten worden weergegeven. U moet alle fouten aanpakken voordat uw certificaat kan worden opgeslagen. Zie de [Certificaatfouten](#certificate-errors) meer te leren over het richten van gemeenschappelijke fouten.

1. Klikken **Opslaan** om uw certificaat in te dienen. U ziet het als een nieuwe rij in de tabel.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

## Certificaatfouten {#certificate-errors}

### Certificaatbeleid {#certificate-policy}

Als de fout &quot;Certificaatbeleid moet in overeenstemming zijn met OV of OV en niet met DV-beleid.&quot; wordt weergegeven, controleert u het beleid van uw certificaat.

Normaliter worden certificaattypen geïdentificeerd door de OID-waarden die zijn ingesloten in het beleid. Deze OID&#39;s zijn uniek en daarom wordt bij het converteren van een certificaat naar een tekstformulier en het zoeken naar de OID bevestigd dat het certificaat een overeenkomst heeft.

U kunt de certificaatdetails als volgt bekijken.

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

Deze tabellen bieden identificatie van patronen.

| Patroon | Certificaattype | Aanvaardbaar |
|---|---|---|
| `2.23.140.1.2.1` | DV | Nee |
| `2.23.140.1.2.2` | OV | Ja |
| `2.23.140.1.2.3` and `TLS Web Server Authentication` | IV cert met toestemming voor gebruik voor https | Ja |

`grep`pingelen voor de patronen, kunt u uw certificaattype bevestigen.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```

### Certificaatvolgorde corrigeren {#correct-certificate-order}

De gemeenschappelijkste reden voor een certificaatplaatsing om te ontbreken is dat de midden of kettingcertificaten niet in de correcte orde zijn. Met name tussentijdse certificaatbestanden moeten eindigen op het basiscertificaat of het basiscertificaat dat zich het dichtst bij het basiscertificaat bevindt en in aflopende volgorde staan vanaf het basiscertificaat `main/server` certificaat aan de wortel.

U kunt de orde van uw middendossiers bepalen gebruikend het volgende bevel:

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

U kunt controleren of de persoonlijke sleutel en `main/server` certificaat komt overeen met behulp van de volgende opdrachten:

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>De uitvoer van deze twee opdrachten moet exact hetzelfde zijn. Als u geen overeenkomende persoonlijke sleutel kunt vinden voor uw `main/server` -certificaat, moet u het certificaat opnieuw coderen door een nieuwe CSR te genereren en/of een bijgewerkt certificaat aan te vragen bij uw SSL-leverancier.

### Geldigheidsdatums certificaat {#certificate-validity-dates}

Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is in de toekomst. Controleer de geldigheid van de certificaatketen.
