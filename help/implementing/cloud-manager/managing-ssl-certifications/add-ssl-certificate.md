---
title: Een SSL-certificaat toevoegen
description: Leer hoe u uw eigen SSL-certificaat kunt toevoegen met de zelfbedieningsprogramma's van Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 64aa010c3d840adad9e1ab6040a6d80c07cd8455
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# Een SSL-certificaat toevoegen {#adding-an-ssl-certificate}

Leer hoe u uw eigen SSL-certificaat kunt toevoegen met de zelfbedieningsprogramma&#39;s van Cloud Manager.

>[!TIP]
>
>Een certificaat kan een paar dagen aan levering vergen. De Adobe beveelt daarom aan dat het certificaat ruim vóór een bepaalde uiterste datum of datum van inbedrijfstelling wordt verstrekt.

## Certificaatvereisten {#certificate-requirements}

Herzie **Vereisten van het Certificaat** in [ Inleiding aan het Leiden SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) om ervoor te zorgen AEM as a Cloud Service het certificaat steunt dat u wilt toevoegen.

## Een certificaat toevoegen {#adding-a-cert}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Van het linkernavigatievenster, onder **Diensten**, klik **SSL Certificaten**. (Mogelijk moet u in de linkerbovenhoek op het hamburgerpictogram klikken om het navigatievenster te kunnen gebruiken. Er wordt een tabel weergegeven met de details van bestaande SSL-certificaten.

   ![ Toevoegend een SSL cert ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Klik **toevoegen SSL Certificaat** om **te openen voeg SSL de dialoogdoos van het Certificaat** toe.

   * Ga een naam voor uw certificaat in **Naam van het Certificaat** in. Dit veld is alleen ter informatie en kan elke naam zijn waarmee u gemakkelijk naar het certificaat kunt verwijzen.
   * Plak het **Certificaat**, **Persoonlijke sleutel**, en **de ketting van het Certificaat** waarden in hun respectieve gebieden. Alle drie velden zijn verplicht.

   ![ voeg SSL de dialoogdoos van het Certificaat toe ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * Eventuele gevonden fouten in waarden worden weergegeven. Voordat u het certificaat kunt opslaan, moet u alle fouten verhelpen.
Zie [ de fouten van het Certificaat ](#certificate-errors) om meer over het richten van gemeenschappelijke fouten te leren.

1. Klik **sparen**.

![ Opgeslagen SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png) Uw certificaat wordt nu getoond als nieuwe rij in de lijst, gelijkend op het beeld hierboven.

>[!NOTE]
>
>Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** zijn om een SSL certificaat in Cloud Manager te installeren.

## Certificaatfouten {#certificate-errors}

Er kunnen bepaalde fouten optreden als een certificaat niet correct is geïnstalleerd of voldoet aan de eisen van Cloud Manager.

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

### Clientcertificaten verwijderen {#client-certificates}

Wanneer u een certificaat toevoegt, als er een fout optreedt die lijkt op het volgende:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Waarschijnlijk hebt u het clientcertificaat opgenomen in de certificaatketen. Zorg ervoor dat de keten het clientcertificaat niet bevat en probeer het opnieuw.

### Certificaatbeleid {#certificate-policy}

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

### Geldigheidsdatums van certificaten {#certificate-validity-dates}

Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is vanaf de huidige datum. Controleer de geldigheid van de certificaatketen.

## Volgende stappen {#next-steps}

Gefeliciteerd! U hebt nu een werkend SSL-certificaat voor uw project. Deze stap is vaak de eerste die een aangepaste domeinnaam instelt.

* Aan opstelling ziet een naam van het douanedomein, [ een Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.
* Om over het bijwerken van en het beheren van uw SSL certificaten in Cloud Manager te leren, zie [ SSL Certificaten beheren ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).
