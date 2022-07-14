---
title: Omgevingen maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen te maken.
role: Admin, User, Developer
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# Omgevingen maken {#create-environments}

In dit deel van het [aan boord gaan,](overview.md) u leert hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen te maken.

## Doelstelling {#objective}

Na het lezen van het vorige document op deze instapreis, [Programma&#39;s maken;](create-program.md) u hebt nu uw eigen Cloud Manager-programma. Nu kunt u leren hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen voor dat programma te maken.

Na het lezen van dit document zult u:

* Begrijp wat een omgeving is.
* Weet het verschil tussen de verschillende omgevingen.
* U kunt uw eigen omgeving maken.

## Wat is een omgeving? {#environments}

De omgevingen bevinden zich onder de programma&#39;s in de hiërarchie van Cloud Manager. Terwijl de programma&#39;s u toestaan om uw oplossing te organiseren en toegang tot bepaalde teamleden aan die programma&#39;s te verlenen, behoren de milieu&#39;s tot specifieke programma&#39;s en zijn de individuele instanties van de Adobe oplossingen binnen die programma&#39;s. Omgevingen worden gebruikt voor een specifiek doel, zoals het ontwerpen van inhoud of het testen van nieuwe ontwikkelingen. De CI/CD-pijpleidingen van Cloud Manager vergemakkelijken de implementatie van code vanuit it-opslagruimten naar deze omgevingen.

Als u het voorbeeld van de theoretische Onderneming van het WKND Reizen en van het Avontuur herinnert, die een huurder is die zich op reisgerelateerde media concentreert, zouden zij twee programma&#39;s kunnen hebben: één Sites-programma voor de afdeling WKND Magazine en één Assets-programma voor de afdeling WKND Media. Elk programma zou waarschijnlijk een paar milieu&#39;s zoals één productiemilieu hebben die het daadwerkelijke verkeer van de plaats en één ontwikkelomgeving voor het testen van nieuwe toepassingscode dienen.

Er zijn drie verschillende typen omgevingen:

* **Productie en fase** - De productie- en testomgevingen zijn als twee beschikbaar en worden respectievelijk voor productie- en testdoeleinden gebruikt.
* **Ontwikkeling** - Er kan een ontwikkelomgeving worden gecreëerd voor zowel ontwikkelings- als testdoeleinden en deze kan alleen worden geassocieerd met niet-productiepijpleidingen.

Voor deze instapreis creëert u een ontwikkelomgeving.

## Omgevingen maken {#creating-environments}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waaraan u een omgeving wilt toevoegen.

1. Van de **Programmaoverzicht** pagina, klik op **Omgeving toevoegen** op de **Omgevingen** kaart om een omgeving toe te voegen.

   ![Milieukaart](/help/implementing/cloud-manager/assets/no-environments.png)

   * De **Omgeving toevoegen** deze optie is ook beschikbaar op de **Omgevingen** tab.

      ![Het tabblad Omgevingen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * De **Omgeving toevoegen** Deze optie kan worden uitgeschakeld bij gebrek aan machtigingen of afhankelijk van de gelicentieerde bronnen.

1. In de **Omgeving toevoegen** dialoogvenster dat wordt weergegeven:

   * Selecteer een **Type omgeving**.
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes weergegeven achter het omgevingstype Ontwikkeling.
   * Een **Omgevingsnaam**.
   * Een **Omgevingsbeschrijving**.
   * Selecteer een **Cloud Region**.

   ![Omgevingsdialoogvenster toevoegen](/help/implementing/cloud-manager/assets/add-environment2.png)

1. Klikken **Opslaan** om de opgegeven omgeving toe te voegen.

Zodra het milieu beschikbaar is, worden de leden van uw organisatie toegewezen aan **Ontwikkelaar** Het productprofiel kan u aanmelden bij Cloud Manager en de opslagruimten voor cloudbeheer beheren.

## Volgende functies {#whats-next}

Nu je dit deel van de instapreis hebt gelezen, moet je:

* Begrijp wat een omgeving is.
* Weet het verschil tussen de verschillende omgevingen.
* U kunt uw eigen omgeving maken.

Uw cloudbronnen zijn gemaakt en zijn klaar om te worden geopend door uw team. Als systeembeheerder moet u uw teamleden eerst aan AEM as a Cloud Service productprofielen van Adobe Admin Console toewijzen om tot die middelen toegang te hebben.

Daarom moet u de instapreis voortzetten door het document opnieuw te bekijken [Teamleden toewijzen aan AEM as a Cloud Service productprofielen.](assign-profiles-aem.md)  In dat document zult u leren hoe te om uw teamleden de rechten te verlenen zij hebben om tot uw nieuwe milieu&#39;s toegang te hebben.

## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) - Meer informatie over de typen omgevingen die u kunt maken en hoe u deze kunt maken voor uw Cloud Manager-project
* [Adobe Cloud Manager gebruiken - omgevingen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) - Cloud Manager-omgevingen bestaan uit AEM services voor schrijven, publiceren en verzenden. Leer hoe de verschillende milieu&#39;s rollen steunen en kunnen worden betrokken gebruikend verschillende CI/CD pijpleidingen.
