---
title: AEM productprofielen toewijzen
description: Zodra u uw wolkenmiddelen hebt gevormd, zult u uw teamtoegang tot AEM moeten verlenen gebruikend AEM productprofielen.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 77ae5d79ecb8a11a230cee461f247ffe0e9891a5
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# AEM productprofielen toewijzen {#assign-profiles-aem}

In dit deel van het [aan boord gaan,](overview.md) u zult leren hoe te om u teamtoegang tot AEM te verlenen gebruikend AEM productprofielen.

## Doelstelling {#objective}

Nadat u het vorige document in deze instapreis hebt gelezen, [Omgevingen maken](create-environments.md) en uw cloudbronnen geconfigureerd hebben, moet u uw team toegang verlenen tot AEM zelf via AEM productprofielen. Als systeembeheerder, doet u dit door AEM productprofielen toe te wijzen.

Na het lezen van dit document moet u begrijpen:

* Wat AEM productprofielen zijn.
* Teamleden toevoegen aan AEM gebruikersproductprofiel.
* Hoe te om teamleden aan AEM het productprofiel van Beheerders toe te voegen.

## Productprofielen AEM {#aem-product-profiles}

Als u AEM wilt gebruiken, moeten uw teamleden worden toegewezen aan ten minste één AEM productprofiel. Rechten om toegang te krijgen tot Cloud Manager zijn niet voldoende. Gebruikers moeten tot een van de volgende twee productprofielen behoren:

* `AEM Users` - Tot deze groep behoren normale gebruikers die dagelijkse taken voor het schrijven van inhoud uitvoeren.
* `AEM Administrators` - Deze groep omvat gebruikers die verantwoordelijk zijn voor geavanceerde functies of AEM.

Elke gebruiker die is toegewezen aan een AEM productprofiel krijgt ook alleen-lezen toegang tot Cloud Manager. Schrijftoegang tot Cloud Manager wordt mogelijk verleend via andere productprofielen.

>[!CAUTION]
>
>Bewerk of verwijder de productprofielen AEM Beheerders of AEM gebruikers niet. Als u deze profielnamen bewerkt, kan het aanmelden bij de AEM-cloudinstantie worden verbroken.

## Vereisten {#prerequisites}

Voordat u deze sectie gaat lezen, moet u over de volgende informatie beschikken die beschikbaar is voor uw team dat de AEM gaat gebruiken.

* Namen
* E-mailadressen
* Taken en verantwoordelijkheden

>[!TIP]
>
>Met het oog op het instappen, adviseren wij dat u aanvankelijk gebruikers toevoegt die aan de directe taken, zoals beheerders, ontwikkelaars en inhoudsauteurs zullen deelnemen. U kunt de rest van het instapsysteem voortzetten zonder alle gebruikers toe te voegen. Nadat u klaar bent met het instappen, kunt u aan een groter aantal gebruikers later schrapen.

## AEM productprofielen weergeven {#view-profiles}

Voer de volgende stappen uit om de AEM productprofielen van de Admin Console te bekijken.

1. Aanmelden bij Admin Console bij [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Van de **Overzicht** pagina, selecteert u **Adobe Experience Manager as a Cloud Service** van de **Producten en diensten** kaart.

   ![Producten en servicekaart](/help/journey-onboarding/assets/assign-team1.png)

1. Navigeer en selecteer de instantie.

   ![Instantie selecteren](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. U zult de lijst van AEM as a Cloud Service productprofielen zien die aan een gebruiker kunnen worden toegewezen die op hun rollen wordt gebaseerd.

   ![Productprofielen](/help/journey-onboarding/assets/cloud-profiles-2.png)

## Teamleden toevoegen aan productprofielen {#add-team-members}

Nu u vertrouwd bent met de beschikbare profielen, kunt u hen zonodig aan uw teamleden toewijzen.

Deze taken vereisen u om een systeembeheerder met te zijn **Zakelijke eigenaar** Productprofiel van Cloud Manager.

1. Navigeer naar uw programma vanuit Cloud Manager en selecteer de optie **Toegang beheren** van de context van het betrokken milieu.

   ![Toegang beheren](/help/journey-onboarding/assets/add-team1.png)

1. Een nieuw lusje navigeert u aan de Admin Console van waar u toegang tot de auteursinstantie van het milieu hebt. Selecteren **AEM** of **AEM** op basis van de machtigingen die deze persoon moet krijgen.

   ![Toegang toewijzen](/help/journey-onboarding/assets/add-team2.png)

1. Selecteren `AEM Administrator` of `AEM User` en klik op **Gebruiker toevoegen** zoals hieronder getoond en leg de noodzakelijke details voor volledige toevoegend het teamlid voor.

   ![Teamlid toevoegen](/help/journey-onboarding/assets/add-team3.png)

1. Herhaal deze stappen voor alle omgevingen, inclusief ontwikkeling, staging en productie, als u beschikt over de informatie van teamleden die toegang nodig hebben.

De gebruiker die u hebt toegevoegd, heeft nu toegang tot de AEM services van de as a Cloud Service auteur.

## Einde van de reis? {#the-end}

Gefeliciteerd! De gebruikers die u hebt toegewezen aan AEM as a Cloud Service productprofielen zijn nu klaar om de AEM ontwerpomgeving te openen en inhoud te maken met AEM as a Cloud Service. Op dezelfde manier hebben ontwikkelaars nu toegang tot Cloud Manager om git te gebruiken voor het opslaan van aangepaste toepassingscode en het implementeren ervan. In die zin is uw instapreis voltooid en kunnen uw gebruikers nu AEMaaCS gebruiken.

Als u echter beter wilt begrijpen hoe auteurs en ontwikkelaars het systeem gebruiken, kunt u doorgaan met twee optionele onderdelen van deze instapreis:

* [Taken van ontwikkelaar- en implementatiebeheer](developers.md) - Waar u leert hoe ontwikkelaars toegang krijgen tot git om hun aangepaste code op te slaan en te implementeren met behulp van Cloud Manager-pijpleidingen.
* [AEM](aem-users.md) - Waar leert u hoe u toegang krijgt tot de AEM omgeving waar u inhoud kunt gaan maken.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Producten en gebruikerstoegang in Admin Console beheren](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - Leer hoe u de Admin Console kunt gebruiken voor het beheer van de toegang tot het gebruik.
* [Toegang tot AEM doorlopen configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en) - Bekijk deze verkorte analyse om meer te leren over het configureren van Adobe IMS-gebruikers, gebruikersgroepen en productprofielen in de Admin Console.

