---
title: Een SSL-certificaat toevoegen - SSL-certificaten beheren
description: Een SSL-certificaat toevoegen - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: 99eb33c3c42094f787d853871aee3a3607856316
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---


# Een SSL-certificaat toevoegen {#adding-an-ssl-certificate}

>[!NOTE]
>AEM als Cloud Service accepteert alleen OV-(Organisatie-validatie) of EV-(Uitgebreide validatie) certificaten. DV-certificaten (Domain Validation) worden niet geaccepteerd.

Een Certificaat neemt een paar dagen in beslag om te verstrekken en het wordt geadviseerd om het certificaat zelfs maanden van tevoren te provisioning. Raadpleeg [Een SSL-certificaat ophalen](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) voor meer informatie.

## Certificaatformaat {#certificate-format}

SSL-bestanden moeten de PEM-indeling hebben om te kunnen worden geïnstalleerd in Cloud Manager. Algemene bestandsextensies die binnen de PEM-indeling vallen, zijn onder andere `.pem,`.`crt`,  `.cer`en  `.cert`.

Voer de onderstaande stappen uit om de indeling van uw SSL-bestanden te converteren naar PEM:

1. PFX converteren naar PEM

`openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

1. P7B converteren naar PEM

`openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

1. DER converteren naar PEM

`openssl x509 -inform der -in certificate.cer -out certificate.pem`

## Belangrijke overwegingen {#important-considerations}

* Een gebruiker moet de rol van bedrijfseigenaar of implementatiebeheerder hebben om een SSL-certificaat te installeren in Cloud Manager.

* Cloud Manager staat op elk gewenst moment maximaal 10 SSL-certificaten toe die kunnen worden gekoppeld aan een of meer omgevingen in uw gehele programma, zelfs als het certificaat is verlopen. Met de interface van Cloud Manager kunnen echter maximaal 50 SSL-certificaten met deze beperking in het programma worden geïnstalleerd.

## Certificaat {#adding-a-cert} toevoegen

Voer de onderstaande stappen uit om een certificaat toe te voegen:

1. Meld u aan bij Cloud Manager.
1. Navigeer naar **Environment**-scherm vanaf de pagina **Overzicht**.
1. Klik op **SSL Certificaten** van het linkernavigatiemenu. Op dit scherm wordt een tabel weergegeven met de details van bestaande SSL-certificaten.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)
1. Selecteer de **knop Certificaat toevoegen** om het dialoogvenster **SSL-certificaat toevoegen** te openen.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)
   1. Geef een naam voor het certificaat op in **Certificaatnaam**. Dit kan elke naam zijn die u helpt gemakkelijk naar uw certificaat te verwijzen.
   1. Plak de **Certificaatketen**, **Persoonlijke sleutel** en **Certificaatketen** in hun respectievelijke velden. Gebruik het plakpictogram rechts van het invoervak.
De drie velden zijn niet optioneel en moeten worden opgenomen.

1. Klik **Opslaan** om uw certificaat te verzenden. U ziet het als een nieuwe rij in de tabel.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
   >[!NOTE]
   >Eventuele fouten worden weergegeven. U moet alle fouten aanpakken voordat uw certificaat kan worden opgeslagen. Verwijs naar [de Fouten van het Certificaat](#certificate-errors) om meer over het richten van gemeenschappelijke fouten te leren.

## Certificaatfouten {#certificate-errors}

### Certificaatvolgorde {#correct-certificate-order} corrigeren

De gemeenschappelijkste reden voor een certificaatplaatsing om te ontbreken is dat de midden of kettingcertificaten niet in de correcte orde zijn. Met name moeten tussentijdse certificaatbestanden eindigen op het basiscertificaat of het basiscertificaat dat zich het dichtst bij het basiscertificaat bevindt en in aflopende volgorde staan, van het `main/server`-certificaat tot het basiscertificaat.

U kunt de orde van uw middendossiers bepalen gebruikend het volgende bevel:

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

Met de volgende opdrachten kunt u controleren of de persoonlijke sleutel en het `main/server`-certificaat overeenkomen:

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>De uitvoer van deze twee opdrachten moet exact hetzelfde zijn. Als u geen overeenkomende persoonlijke sleutel kunt vinden voor uw `main/server`-certificaat, moet u het certificaat opnieuw sleutelken door een nieuwe CSR te genereren en/of een bijgewerkt certificaat aan te vragen bij uw SSL-leverancier.

### Geldigheidsdatums certificaat {#certificate-validity-dates}

Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is in de toekomst

Controleer de geldigheid van de certificaatketen.
