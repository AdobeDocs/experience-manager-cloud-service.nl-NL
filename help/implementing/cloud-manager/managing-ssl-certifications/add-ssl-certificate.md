---
title: Een SSL-certificaat toevoegen
description: Leer hoe u uw eigen SSL-certificaat of DV-certificaat (Domeinvalidatie) toevoegt met de Cloud Manager-tools voor zelfbediening.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: fcde1f323392362d826f9b4a775e468de9550716
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---


# Een SSL-certificaat toevoegen

Leer hoe u een door de klant beheerd SSL-certificaat of een Adobe die is gegenereerd en beheerd DV-certificaat (Domeinvalidatie) toevoegt met behulp van de Cloud Manager-tools voor zelfbediening.


## Een SSL- of DV-certificaat toevoegen {#adding-an-ssl-certificate}

Een certificaat kan een paar dagen aan levering vergen. Daarom beveelt de Adobe aan dat het certificaat ruim vóór een eventuele deadline of doorlopende datum wordt verstrekt.

Ben zeker u herziet **vereisten van het Certificaat** in [ Inleiding aan het Leiden SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) om ervoor te zorgen AEM as a Cloud Service het certificaat steunt dat u wilt toevoegen.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

>[!NOTE]
>
>Klanten mogen geen DV-certificaten (Domain Validation) uploaden.

**om een SSL of DV- certificaat toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht**, navigeer aan het **milieu&#39;s** scherm.

1. Van het linkernavigatievenster, onder **Diensten**, klik **SSL Certificaten**. Als u het linkernavigatievenster niet ziet zoals in de volgende afbeelding, moet u mogelijk op het hamburgerpictogram in de linkerbovenhoek klikken.

   ![ Toevoegend een SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Vlak de hoger-juiste hoek van de pagina, klik **voeg SSL Certificaat** toe.

1. In **voeg SSL certificaat** dialoogdoos toe, die op uw bijzonder gebruiksgeval wordt gebaseerd, doe één van het volgende:

   | Hoofdletters gebruiken | Stappen |
   | --- | --- |
   | **voeg een Adobe geleid certificaat (DV) toe** | **om een Adobe beheerde certificaat (DV) toe te voegen:**<br> a. Selecteer de beheerde Adobe van het certificaattype **(DV)**.<br>![ voeg een DV- certificaat ](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br> b toe. In de **Uitgezochte domeinen** drop-down lijst, selecteer één of meerdere domeinen die u verbonden aan het DV- certificaat wilt.<br> Geen domeinen om te selecteren? Als dat het geval is, moet u een aangepast domein toevoegen. Zie [ een douanedomein ](#add-custom-domain) toevoegen. Wanneer u wordt gebeëindigd toevoegend een naam van het douanedomein, terugkeer aan dit onderwerp en begin opnieuw bij stap 1.<br> d. Ga verder met stap 7. |
   | **voeg een klant geleid certificaat (OV/EV) toe** | **om een klant geleid certificaat (OV/EV) toe te voegen:**<br> a. Selecteer de beheerde Klant van het certificaattype **(OV/EV)**.<br> b. Op het **gebied van de Naam van het Certificaat**, ga een naam voor uw certificaat in. Dit veld is alleen ter informatie en kan elke naam zijn waarmee u gemakkelijk naar het certificaat kunt verwijzen.<br> c. In het **Certificaat**, **Persoonlijke sleutel**, en **de ketting van het Certificaat** gebieden, kleef de vereiste waarden in hun respectieve gebieden.<br>![ voeg SSL doos van de certificaatdialoog ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br> toe om het even welke ontdekte fouten in waarden worden getoond. Voordat u het certificaat kunt opslaan, moet u alle fouten verhelpen. Zie [ de Fouten van het Certificaat ](#certificate-errors) om meer over het oplossen van problemen gemeenschappelijke fouten te leren.<br> d. Ga verder met stap 7. |

<!--
    **Add an SSL certificate:**
    1. Select the certificate type **Customer managed (OV/EV)**.
    1. In **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your certificate easily.
    1. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.

        ![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)
  
    Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate errors](#certificate-errors) to learn more about troubleshooting common errors.

    **Add a DV certificate:**
    1. Select the certificate type **Adobe managed (DV)**.

        ![Adding a DC certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

    1. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV certificate.

        No domains to select? If so, it means that you must add a custom domain. See [Add a custom domain](#add-custom-domain). When you are finished, resume the steps from the beginning again. -->

1. In de laag-juiste hoek van de dialoogdoos, klik **sparen**.

   Nadat het certificaat is uitgegeven, ziet u een groen vinkje in de bovenstaande afbeelding

   ![ Uitgegeven DV cert ](assets/issued-dv-certificate.png)

### Een aangepast domein toevoegen {#add-custom-domain}

Voordat u een Adobe kunt toevoegen die is gegenereerd en beheerd Domain Validated (DV)-certificaat, moet u eerst een aangepast domein toevoegen. Het proces om dit te doen is bijna het zelfde als gedetailleerd in [ Inleiding aan de namen van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/introduction.md) en [ voeg een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toe. Deze functionaliteit is nu echter enigszins uitgebreid, zoals hieronder wordt beschreven.

1. Wanneer het toevoegen van een naam van het douanedomein, in **verifieer domein** dialoogdoos, selecteer een **Adobe beheerde certificaat**.

   ![ kies Adobe-geleid ](assets/verify-domain-dialog.png)

1. In **verifieer domein** dialoogdoos, voeg een CNAME verificatierecord aan uw DNS toe.

   ![ voeg de ingang van CNAME ](assets/verify-domain-dialog-adobe-managed.png) toe

1. Nadat het domein wordt gecreeerd, klik de ellipsknoop in de lijst van domeinen en selecteer **verifieer** om het domein te verifiëren.

   ![ verifieer domein ](assets/verify-domain.png)

1. Hervat de taak [ voeg een DV- certificaat ](#adding-an-ssl-certificate) toe.

### Problemen met certificaatfouten oplossen {#certificate-errors}

Er kunnen bepaalde fouten optreden als een certificaat niet correct is geïnstalleerd of niet voldoet aan de eisen van Cloud Manager.

+++

* **Correcte certificaatorde**

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

+++

* **verwijder cliëntcertificaten**

  Wanneer u een certificaat toevoegt, als er een fout optreedt die lijkt op het volgende:

  ```text
  The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
  ```

  Waarschijnlijk hebt u het clientcertificaat opgenomen in de certificaatketen. Zorg ervoor dat de keten het clientcertificaat niet bevat en probeer het opnieuw.

+++

+++

* **beleid van het Certificaat**

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

+++

* **de geldigheidsdata van het Certificaat**

  Cloud Manager verwacht dat het SSL-certificaat ten minste 90 dagen geldig is vanaf de huidige datum. Controleer de geldigheid van de certificaatketen.

+++

## Volgende stappen {#next-steps}

U hebt nu een werkend SSL-certificaat toegevoegd voor uw project. Deze stap is vaak de eerste die een aangepaste domeinnaam instelt.

* Aan opstelling ziet een naam van het douanedomein, [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.
* Om over het bijwerken van en het beheren van uw SSL certificaten in Cloud Manager te leren, zie [ SSL certificaten beheren ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).
