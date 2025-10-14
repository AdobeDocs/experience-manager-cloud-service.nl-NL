---
title: AEM-productprofielen toewijzen
description: Nadat u uw cloudbronnen hebt geconfigureerd, geeft u uw team toegang tot AEM zelf met behulp van AEM-productprofielen.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---

# AEM-productprofielen toewijzen {#assign-profiles-aem}

>[!CONTEXTUALHELP]
>id="assets_user_entitlements"
>title="AEM-productprofielen toewijzen"
>abstract="Je mag Experience Manager Assets niet gebruiken. Neem contact op met de beheerder."

In dit deel van de [&#x200B; onboarding reis &#x200B;](overview.md), leert u hoe te om u teamtoegang tot AEM te verlenen gebruikend de productprofielen van AEM.

## Doelstelling {#objective}

Nadat u het vorige document in deze onboarding reis hebt gelezen, [&#x200B; creeer Milieu &#x200B;](create-environments.md), en hebben uw wolkenmiddelen gevormd, verleent uw teamtoegang tot AEM zelf gebruikend de productprofielen van AEM. Als systeembeheerder doet u dit door AEM-productprofielen toe te wijzen.

Na het lezen van dit document is het verstandig:

* Wat zijn AEM-productprofielen?
* Teamleden toevoegen aan het productprofiel van AEM-gebruikers.
* Teamleden toevoegen aan het productprofiel van AEM-beheerders.

## AEM-productprofielen {#aem-product-profiles}

Als u AEM wilt gebruiken, moeten uw teamleden worden toegewezen aan ten minste één AEM-productprofiel. Toestemmingen om toegang te krijgen tot Cloud Manager zijn niet voldoende. Gebruikers moeten tot een van de volgende twee productprofielen behoren:

* `AEM Users` - Deze groep omvat normale gebruikers die dagelijkse taken uitvoeren om inhoud te ontwerpen.
* `AEM Administrators` - Deze groep bevat gebruikers die verantwoordelijk zijn voor geavanceerde functies of AEM.

>[!NOTE]
>
>Elke gebruiker die aan een het productprofiel van AEM as a Cloud Service wordt toegewezen heeft read-only toegang tot Cloud Manager via de **&#x200B;**&#x200B;rol van de Gebruiker van Cloud Manager.
>
>De gebruikers met de **rol van de Gebruiker van Cloud Manager** kunnen slechts in Cloud Manager registreren en aan de auteursmilieu&#39;s van AEM navigeren (als zij bestaan) door de het menuopties van Programma&#39;s te gebruiken. De **rol van de Gebruiker van 0&rbrace; Cloud Manager &lbrace;is niet voldoende om tot programmadetails toegang te hebben.** Als dergelijke toegang nodig is, moeten de gebruikers extra rollen door hun systeembeheerder worden verleend.
>Zie de [&#x200B; Extra sectie van Middelen hieronder &#x200B;](#additional-resources) voor meer informatie over de gebruikersrollen van Cloud Manager.

>[!CAUTION]
>
>Bewerk of verwijder de productprofielen AEM-beheerders of AEM-gebruikers niet. Als u deze profielnamen bewerkt, kan het aanmelden bij de AEM-cloudinstantie worden verbroken.

## Vereisten {#prerequisites}

Voordat u deze sectie gaat lezen, moet u over de volgende informatie beschikken over uw team dat AEM gaat gebruiken.

* Namen
* E-mailadressen
* Taken en verantwoordelijkheden

>[!TIP]
>
>Met het oog op instapweigering raadt Adobe u aan eerst gebruikers toe te voegen die aan de directe taken zullen deelnemen, zoals beheerders, ontwikkelaars en auteurs van inhoud. U kunt de rest van het instapsysteem voortzetten zonder alle gebruikers toe te voegen. Nadat u klaar bent met het instappen, kunt u aan een groter aantal gebruikers later schrapen.

## AEM-productprofielen weergeven {#view-profiles}

Voer de volgende stappen uit om de AEM-productprofielen van de Admin Console te bekijken.

1. Meld u aan bij Admin Console op [`https://adminconsole.adobe.com` &#x200B;](https://adminconsole.adobe.com) .

1. Van de **pagina van het Overzicht**, uitgezochte **Adobe Experience Manager as a Cloud Service** van de **Producten en de diensten** kaart.

   ![&#x200B; Producten en de dienstenkaart &#x200B;](/help/journey-onboarding/assets/assign-team1.png)

1. Navigeer en selecteer de instantie.

   ![&#x200B; Uitgezochte instantie &#x200B;](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. U kunt de lijst met AEM as a Cloud Service-productprofielen zien die op basis van hun rollen aan een gebruiker kunnen worden toegewezen.

   ![&#x200B; Profielen van het Product &#x200B;](/help/journey-onboarding/assets/cloud-profiles-2.png)

## Teamleden toevoegen aan productprofielen {#add-team-members}

Nu u vertrouwd bent met de beschikbare profielen, kunt u hen zonodig aan uw teamleden toewijzen.

Deze taken vereisen u om een systeembeheerder met het **BedrijfsEigenaar** het productprofiel van Cloud Manager te zijn.

1. Navigeer aan uw programma van Cloud Manager en selecteer de **Manage knoop van de Toegang** van de context van het milieu van belang.

   ![&#x200B; beheer toegang &#x200B;](/help/journey-onboarding/assets/add-team1.png)

1. Een nieuw tabblad navigeert u naar de Admin Console vanwaar u toegang hebt tot de instantie van de auteur van de omgeving. Selecteer **de Beheerders van AEM** of **Gebruikers van AEM** die op de toestemmingen worden gebaseerd dit individu moet worden gegeven.

   ![&#x200B; wijs toegang &#x200B;](/help/journey-onboarding/assets/add-team2.png) toe

1. Selecteer `AEM Administrator` of `AEM User` en klik **voeg Gebruiker** zoals hieronder getoond toe en verzend de noodzakelijke details om het toevoegen van het teamlid te voltooien.

   ![&#x200B; voeg teamlid &#x200B;](/help/journey-onboarding/assets/add-team3.png) toe

1. Herhaal deze stappen voor alle omgevingen, inclusief ontwikkeling, staging en productie, als u beschikt over de informatie van teamleden die toegang nodig hebben.

De gebruiker die u hebt toegevoegd, heeft nu toegang tot de AEM as a Cloud Service Author-services.

## Einde van de reis? {#the-end}

Gefeliciteerd! De gebruikers die u hebt toegewezen aan AEM as a Cloud Service-productprofielen zijn nu klaar om de AEM-ontwerpomgeving te openen en inhoud te maken met AEM as a Cloud Service. Op dezelfde manier hebben ontwikkelaars nu toegang tot Cloud Manager om git te gebruiken voor het opslaan van aangepaste toepassingscode en het implementeren ervan. In die zin is uw instapreis voltooid en kunnen uw gebruikers nu AEMaaCS gebruiken.

Als u echter beter wilt begrijpen hoe auteurs en ontwikkelaars het systeem gebruiken, kunt u doorgaan met twee optionele onderdelen van deze instapreis:

* [&#x200B; de Taken van de Manager van de Ontwikkelaar en van de Plaatsing &#x200B;](developers.md) - waar u leert hoe de ontwikkelaars toegang hebben tot git om hun douanecode op te slaan en het op te stellen gebruikend de pijpleidingen van Cloud Manager.
* [&#x200B; de Taken van de Gebruiker van AEM &#x200B;](aem-users.md) - waar u leert om tot het milieu van AEM toegang te hebben waar u kunt beginnen inhoud te creëren.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [&#x200B; het Team van AEM as a Cloud Service en de Profielen van het Product &#x200B;](/help/onboarding/aem-cs-team-product-profiles.md) - leer hoe het team en de productprofielen van AEM as a Cloud Service toegang tot uw vergunning gegeven oplossingen van Adobe kunnen verlenen en beperken.
* [&#x200B; het Leiden Producten en de Toegang van de Gebruiker in Admin Console &#x200B;](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - leer hoe te om Admin Console te gebruiken om gebruikstoegang te beheren.
* [&#x200B; het Vormen toegang tot AEM lopen-door &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=nl-NL) - Check uit dit verkorte looppas-hoewel om over het vormen van gebruikers IMS van Adobe, gebruikersgroepen, en productprofielen in Admin Console te leren.

