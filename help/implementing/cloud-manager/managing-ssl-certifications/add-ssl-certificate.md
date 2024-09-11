---
title: Een SSL-certificaat toevoegen
description: Leer hoe u uw eigen SSL-certificaat of DV-certificaat (Domeinvalidatie) toevoegt met de Cloud Manager-tools voor zelfbediening.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 6fb672e03fe28ae8af6dc873791c7d1ac1fb8fd7
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Een SSL-certificaat toevoegen

Leer hoe u een door de klant beheerd SSL-certificaat of een Adobe die is gegenereerd en beheerd DV-certificaat (Domeinvalidatie) toevoegt met behulp van de Cloud Manager-tools voor zelfbediening.

Zie ook [ problemen oplossen SSL certificaatfouten ](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).


## Een SSL-certificaat toevoegen {#adding-an-ssl-certificate}

Een certificaat kan een paar dagen aan levering vergen. Daarom beveelt de Adobe aan dat het certificaat ruim vóór een eventuele deadline of doorlopende datum wordt verstrekt.

Ben zeker u herziet **vereisten van het Certificaat** in [ Inleiding aan het Leiden SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) om ervoor te zorgen AEM as a Cloud Service het certificaat steunt dat u wilt toevoegen.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

>[!NOTE]
>
>Klanten mogen geen DV-certificaten (Domain Validation) uploaden.

**om een SSL certificaat toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht**, navigeer aan het **milieu&#39;s** scherm.

1. Van het linkernavigatievenster, onder **Diensten**, klik **SSL Certificaten**. Als u het linkernavigatievenster niet ziet zoals in de volgende afbeelding, moet u mogelijk op het hamburgerpictogram in de linkerbovenhoek klikken.

   ![ Toevoegend een SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Vlak de hoger-juiste hoek van de pagina, klik **voeg SSL Certificaat** toe.

1. In **voeg SSL certificaat** dialoogdoos toe, die op [ uw bijzonder gebruiksgeval ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) wordt gebaseerd, doe één van het volgende:

   | | Hoofdletters gebruiken | Stappen |
   | --- | --- | --- |
   | 1 | **voeg een Adobe geleid certificaat (DV) toe** | **om een Adobe beheerde certificaat (DV) toe te voegen:**<br> a. Selecteer de beheerde Adobe van het certificaattype **(DV)**.<br>![ voeg een DV- certificaat ](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br> b toe. In de **Uitgezochte domeinen** drop-down lijst, selecteer één of meerdere domeinen die u verbonden aan het DV- certificaat wilt.<br> Geen domeinen om te selecteren? Als dat het geval is, moet u een aangepast domein toevoegen. Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. Wanneer u wordt gebeëindigd toevoegend een naam van het douanedomein, terugkeer aan dit onderwerp en begin opnieuw bij stap 1.<br> d. Ga verder met stap 7. |
   | 2 | **voeg een klant geleid certificaat (OV/EV) toe** | **om een klant geleid certificaat (OV/EV) toe te voegen:**<br> a. Selecteer de beheerde Klant van het certificaattype **(OV/EV)**.<br> b. Op het **gebied van de Naam van het Certificaat**, ga een naam voor uw certificaat in. Dit veld is alleen ter informatie en kan elke naam zijn waarmee u gemakkelijk naar het certificaat kunt verwijzen.<br> c. In het **Certificaat**, **Persoonlijke sleutel**, en **de ketting van het Certificaat** gebieden, kleef de vereiste waarden in hun respectieve gebieden.<br>![ voeg SSL doos van de certificaatdialoog ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br> toe om het even welke ontdekte fouten in waarden worden getoond. Voordat u het certificaat kunt opslaan, moet u alle fouten verhelpen. Zie [ de Fouten van het Certificaat ](#certificate-errors) om meer over het oplossen van problemen gemeenschappelijke fouten te leren.<br> d. Ga verder met stap 7. |

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

   Nadat het certificaat met succes wordt uitgegeven, toont het een groen vinkje in de **SSL Certificaten** lijst.

U hebt nu een werkend SSL-certificaat toegevoegd voor uw project. Deze stap is vaak de eerste die een aangepaste domeinnaam instelt.

* Aan opstelling ziet een naam van het douanedomein, [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.
* Om over het bijwerken van en het beheren van uw SSL certificaten in Cloud Manager te leren, zie [ SSL certificaten beheren ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

<!--
### Add a custom domain {#add-custom-domain}

Before you can add an Adobe generated and managed Domain Validated (DV) certificate, you must first add a custom domain. The process for doing so is nearly the same as detailed in [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) and [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). However, that functionality is now slightly expanded, as described below.

1. When adding a custom domain name, in the **Verify domain** dialog box, select an **Adobe managed certificate**.

    ![Choose Adobe-managed](assets/verify-domain-dialog.png)

1. In the **Verify domain** dialog box, add a CNAME verification record to your DNS.

    ![Add CNAME entry](assets/verify-domain-dialog-adobe-managed.png)

1. After the domain is created, click the ellipsis button in the list of domains and select **Verify** to verify the domain.

    ![Verify domain](assets/verify-domain.png) 

1. Resume the task [Add a DV certificate](#adding-an-ssl-certificate). -->


