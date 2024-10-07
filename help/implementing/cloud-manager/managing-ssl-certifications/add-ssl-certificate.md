---
title: Een SSL-certificaat toevoegen
description: Leer hoe u uw eigen SSL-certificaat of een DV-certificaat (Domain Validation) voor Adobe kunt toevoegen met de zelfbedieningsprogramma's van Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 493c5729c3107f151685a243006b17196b74c1bd
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Een SSL-certificaat toevoegen {#add-ssl-cert}

Leer hoe u uw eigen SSL-certificaat of een door Adobe beheerd DV-certificaat (Domain Validation) toevoegt met Cloud

>[!TIP]
>
>Een certificaat kan een paar dagen aan levering vergen. Daarom raadt de Adobe aan dat als u uw eigen certificaat verstrekt, dit ruim vóór om het even welke deadline of go-live datum wordt verstrekt.

## Vereisten {#prerequisites}

* Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** zijn om een certificaat toe te voegen.
* Als u uw eigen certificaat installeert, ben zeker om **vereisten van het Certificaat** in [ Inleiding te herzien aan het Leiden SSL Certificaten.](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements)

## Een SSL-certificaat toevoegen {#add-certificate}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.
1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijmenu te openbaren.
1. Onder de **rubriek van de Diensten**, klik ![ Slot gesloten pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificaten**.

   ![ Toevoegend een SSL certificaat ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Vlak de hoger-juiste hoek van de SSL pagina van Certificaten, klik **SSL Certificaat** toevoegen.

1. In **voeg SSL certificaat** dialoogdoos toe, die op [ uw bijzonder gebruiksgeval ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) wordt gebaseerd, doe één van het volgende:

   | | Hoofdletters gebruiken | Stappen |
   | --- | --- | --- |
   | 1 | **voeg een beheerde Adobe (DV) certificaat toe** | **om een beheerde Adobe (DV) certificaat toe te voegen:**<br> a. In **voeg SSL doos van het Certificaat** toe, selecteer de beheerde Adobe van het certificaattype **(DV)**.<br>![ voeg een DV- certificaat ](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br> b toe. Op het **gebied van de Naam van het Certificaat**, ga een naam in u verbonden aan het certificaat wilt.<br> c. In de **Uitgezochte domeinen** drop-down lijst, selecteer één of meerdere domeinen die u verbonden aan het DV- certificaat wilt.<br> Geen domeinen om te selecteren? Als dat het geval is, moet u een aangepast domein toevoegen. Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. Wanneer u wordt gebeëindigd toevoegend een naam van het douanedomein, terugkeer aan dit onderwerp en begin opnieuw bij stap 1.<br> d. Ga verder met stap 7. |
   | 2 | **voeg een klant geleid (OV/EV) certificaat toe** | **om een klant beheerde (OV/EV) certificaat toe te voegen:**<br> a. In **voeg SSL de dialoogdoos van het Certificaat** toe, selecteer de beheerde Klant van het certificaattype **(OV/EV)**.<br> b. Op het **gebied van de Naam van het Certificaat**, ga een naam voor uw certificaat in. Dit veld is alleen ter informatie en kan elke naam zijn waarmee u gemakkelijk naar het certificaat kunt verwijzen.<br> c. In het **Certificaat**, **Persoonlijke sleutel**, en **de ketting van het Certificaat** gebieden, kleef de vereiste waarden in hun respectieve gebieden.<br>![ voeg SSL doos van de certificaatdialoog ](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br> toe om het even welke ontdekte fouten in waarden worden getoond. Voordat u het certificaat kunt opslaan, moet u alle fouten verhelpen. Zie [ de Fouten van het Certificaat ](#certificate-errors) om meer over het oplossen van problemen gemeenschappelijke fouten te leren.<br> d. Ga verder met stap 7. |

1. In de laag-juiste hoek van de dialoogdoos, klik **sparen**.

Nadat het certificaat met succes wordt uitgegeven, wordt het getoond met een groen vinkje in de **SSL Certificaten** lijst.

U hebt nu een werkend SSL-certificaat toegevoegd voor uw project. Deze stap is vaak de eerste die een aangepaste domeinnaam instelt.

* Aan opstelling ziet een naam van het douanedomein, [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.
* Om over het bijwerken van en het beheren van uw SSL certificaten in Cloud Manager te leren, zie [ SSL certificaten beheren ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

>[!TIP]
>
>Als u kwesties hebt die of uw certificaten toevoegen beheren, te zien gelieve het document [ SSL certificaatfouten oplossen.](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md)
