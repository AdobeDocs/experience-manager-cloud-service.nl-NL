---
title: Omgevingen maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen te maken.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
feature: Onboarding
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---

# Omgevingen maken {#create-environments}

In dit deel van de [ onboarding reis ](overview.md), leert u hoe te om Cloud Manager te gebruiken om uw eerste milieu&#39;s tot stand te brengen.

## Doelstelling {#objective}

Na het lezen van het vorige document in dit op instapweigering reis, [ Creërend Programma&#39;s ](create-program.md), hebt u nu uw eigen programma van Cloud Manager. Nu kunt u leren hoe u Cloud Manager kunt gebruiken om uw eerste omgevingen voor dat programma te maken.

Na het lezen van dit document zult u:

* Begrijp wat een omgeving is.
* Weet het verschil tussen de verschillende omgevingen.
* U kunt uw eigen omgeving maken.

## Wat is een omgeving? {#environments}

Het milieu bevindt zich onder programma&#39;s binnen de hiërarchie van Cloud Manager. Terwijl de programma&#39;s u toestaan om uw oplossing te organiseren en toegang tot bepaalde teamleden aan die programma&#39;s te verlenen, behoren de milieu&#39;s tot specifieke programma&#39;s en zijn individuele instanties van de oplossingen van de Adobe binnen die programma&#39;s. Omgevingen worden gebruikt voor een specifiek doel, zoals het ontwerpen van inhoud of het testen van nieuwe ontwikkelingen. Cloud Manager CI/CD-pijpleidingen vergemakkelijken de implementatie van code vanuit git-opslagruimten naar deze omgevingen.

Als u het voorbeeld van de theoretische Onderneming van het WKND Reizen en van het Avontuur herinnert, die een huurder is die zich op reis-verwante media concentreert, zouden zij twee programma&#39;s kunnen hebben. Namelijk één programma van Plaatsen voor zijn afdeling van het Tijdschrift WKND, en één programma van Assets voor de afdeling van Media WKND. Elk programma zou waarschijnlijk een paar milieu&#39;s zoals één productiemilieu hebben die het daadwerkelijke verkeer van de plaats en één ontwikkelomgeving voor het testen van nieuwe toepassingscode dienen.

Er zijn vier verschillende typen omgevingen:

* **Productie en Stadium** - de productie en het opvoeren milieu&#39;s zijn beschikbaar als paar en voor productie en testende doeleinden, respectievelijk gebruikt.
* **Ontwikkeling** - een ontwikkelomgeving kan voor ontwikkeling en het testen doeleinden worden gecreeerd en kan met niet-productiepijpleidingen slechts worden geassocieerd.
* **Snelle Ontwikkeling** - een snelle ontwikkelomgeving (RDE) staat een ontwikkelaar toe om veranderingen snel op te stellen en te herzien, die de hoeveelheid tijd minimaliseren om eigenschappen te testen die om aan een lokale ontwikkelomgeving worden bewezen te werken.

In het kader van deze instapreis creëert u een ontwikkelomgeving die u kunt gebruiken om de mogelijkheden van AEM as a Cloud Service te verkennen.

## Omgevingen maken {#creating-environments}

1. Logon aan Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Selecteer het programma waaraan u een omgeving wilt toevoegen.

1. Om een milieu toe te voegen, van de **pagina van het Overzicht van het 0&rbrace; Programma, op de** Milieu **kaart, uitgezocht** voeg Milieu **toe.**

   ![ kaart van Milieu&#39;s ](/help/implementing/cloud-manager/assets/no-environments.png)

   * **voegt de optie van het Milieu** toe is ook beschikbaar op **Milieu** tabel.

     ![ Milieu&#39;s tabel ](/help/implementing/cloud-manager/assets/environments-tab.png)

   * **voeg Milieu** optie toe kan wegens gebrek aan toestemmingen of afhankelijk van de vergunning gegeven middelen worden onbruikbaar gemaakt.

1. In **voeg milieu** dialoog toe die verschijnt:

   * Selecteer een **Type van Milieu**.
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes weergegeven achter het omgevingstype Ontwikkeling.
   * Verstrek een **naam van het Milieu**.
   * Verstrek een **beschrijving van het Milieu**.
   * Selecteer het Gebied van de a **Wolk**.

   ![ voeg milieudialoog ](/help/implementing/cloud-manager/assets/add-environment2.png) toe

1. Klik **sparen** om het gespecificeerde milieu toe te voegen.

Zodra het milieu beschikbaar is, kunnen de leden van uw organisatie die aan het **productprofiel van de 1&rbrace; ontwikkelaar** wordt toegewezen zich bij Cloud Manager aanmelden en Cloud Manager git bewaarplaatsen beheren.

## Volgende functies {#whats-next}

Nu je dit deel van de instapreis hebt gelezen, moet je:

* Begrijp wat een omgeving is.
* Weet het verschil tussen de verschillende omgevingen.
* U kunt uw eigen omgeving maken.

Uw cloudbronnen zijn gemaakt en zijn klaar om te worden geopend door uw team. Als systeembeheerder, moet u uw teamleden aan productprofielen in AEM as a Cloud Service van Adobe Admin Console eerst toewijzen zodat zij tot die middelen kunnen toegang hebben.

Daarom zou u uw aan boord gaan reis door het document te herzien [ moeten voortzetten toewijzend de Leden van het Team aan de Profielen van het Product van AEM as a Cloud Service ](assign-profiles-aem.md). In dat document, leert u hoe te om uw teamleden rechten te verlenen om tot uw nieuwe milieu&#39;s toegang te hebben.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ het Leiden Milieu ](/help/implementing/cloud-manager/manage-environments.md) - Leer over de soorten milieu&#39;s die u kunt creëren en hoe te om hen voor uw project van Cloud Manager tot stand te brengen
* [ Gebruikend Adobe Cloud Manager - Milieu&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=nl-NL) - de milieu&#39;s van Cloud Manager zijn samengesteld uit AEM creatie, het publiceren, en de diensten van Dispatcher. Leer hoe de verschillende milieu&#39;s rollen steunen en kunnen worden betrokken gebruikend verschillende CI/CD pijpleidingen.
* [ Snelle Milieu&#39;s van de Ontwikkeling ](/help/implementing/developing/introduction/rapid-development-environments.md) - zie deze documentatie voor details over hoe te om RDE te gebruiken
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager Environment Types](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/environment-types.md) - Watch this video for an overview of Cloud Manager environment types from an AEM champion. -->

