---
title: Omgevingen maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen te maken.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
feature: Onboarding
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---

# Omgevingen maken {#create-environments}

In dit deel van het [aan boord gaan,](overview.md) U leert hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen te maken.

## Doelstelling {#objective}

Na het lezen van het vorige document op deze instapreis, [Programma&#39;s maken;](create-program.md) u hebt nu uw eigen Cloud Manager-programma. Nu kunt u leren hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen voor dat programma te maken.

Na het lezen van dit document zult u:

* Begrijp wat een omgeving is.
* Weet het verschil tussen de verschillende omgevingen.
* U kunt uw eigen omgeving maken.

## Wat is een omgeving? {#environments}

De omgevingen bevinden zich onder de programma&#39;s in de hiërarchie van Cloud Manager. Terwijl de programma&#39;s u toestaan om uw oplossing te organiseren en toegang tot bepaalde teamleden aan die programma&#39;s te verlenen, behoren de milieu&#39;s tot specifieke programma&#39;s en zijn individuele instanties van de oplossingen van de Adobe binnen die programma&#39;s. Omgevingen worden gebruikt voor een specifiek doel, zoals het ontwerpen van inhoud of het testen van nieuwe ontwikkelingen. De CI/CD-pijpleidingen van Cloud Manager vergemakkelijken de implementatie van code vanuit it-opslagruimten naar deze omgevingen.

Als u het voorbeeld van de theoretische Onderneming van het WKND Reizen en van het Avontuur herinnert, die een huurder is die zich op reis-verwante media concentreert, zouden zij twee programma&#39;s kunnen hebben. Namelijk één programma van Plaatsen voor zijn afdeling van het Tijdschrift WKND, en één programma van Activa voor de afdeling van Media WKND. Elk programma zou waarschijnlijk een paar milieu&#39;s zoals één productiemilieu hebben die het daadwerkelijke verkeer van de plaats en één ontwikkelomgeving voor het testen van nieuwe toepassingscode dienen.

Er zijn vier verschillende typen omgevingen:

* **Productie en fase** - De productie- en testomgevingen zijn als twee beschikbaar en worden respectievelijk voor productie- en testdoeleinden gebruikt.
* **Ontwikkeling** - Een ontwikkelomgeving kan worden gecreëerd voor ontwikkelings- en testdoeleinden en kan alleen worden geassocieerd met niet-productiepijpleidingen.
* **Snelle ontwikkeling** - Een snelle ontwikkelomgeving (RDE) stelt een ontwikkelaar in staat snel wijzigingen te implementeren en te evalueren, waardoor de tijd die nodig is om functies te testen waarvan is aangetoond dat ze werken in een lokale ontwikkelomgeving, tot een minimum wordt beperkt.

In het kader van deze instapreis creëert u een ontwikkelomgeving die u kunt gebruiken om de mogelijkheden van AEM as a Cloud Service te verkennen.

## Omgevingen maken {#creating-environments}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Selecteer het programma waaraan u een omgeving wilt toevoegen.

1. Om een milieu toe te voegen, van **Programmaoverzicht** pagina, op de **Omgevingen** kaart, selecteren **Omgeving toevoegen**.

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

Uw cloudbronnen zijn gemaakt en zijn klaar om te worden geopend door uw team. Als systeembeheerder, moet u uw teamleden aan productprofielen in AEM as a Cloud Service van Adobe Admin Console eerst toewijzen zodat zij tot die middelen kunnen toegang hebben.

Daarom moet u de instapreis voortzetten door het document opnieuw te bekijken [Teamleden toewijzen aan AEM as a Cloud Service productprofielen](assign-profiles-aem.md). In dat document, leert u hoe te om uw teamleden rechten te verlenen om tot uw nieuwe milieu&#39;s toegang te hebben.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) - Meer informatie over de typen omgevingen die u kunt maken en hoe u deze kunt maken voor uw Cloud Manager-project
* [Adobe Cloud Manager gebruiken - omgevingen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) - Cloud Manager-omgevingen bestaan uit AEM services voor schrijven, publiceren en verzenden. Leer hoe de verschillende milieu&#39;s rollen steunen en kunnen worden betrokken gebruikend verschillende CI/CD pijpleidingen.
* [Snelle ontwikkelomgevingen](/help/implementing/developing/introduction/rapid-development-environments.md) - Zie deze documentatie voor details over hoe te om RDE te gebruiken
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager Environment Types](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/environment-types.md) - Watch this video for an overview of Cloud Manager environment types from an AEM champion. -->

