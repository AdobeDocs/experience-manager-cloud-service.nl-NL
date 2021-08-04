---
title: 'Teamleden toewijzen aan AEM als profielen van het Product van de Cloud Service '
description: Volg deze pagina om te leren hoe u teamleden toewijst aan AEM als profielen van het Product van de Cloud Service
hide: true
hidefromtoc: true
index: false
source-git-commit: ae8e5bde38472f4d9bce0e69bf70acbef5932146
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 1%

---


# Teamleden toewijzen aan AEM als profielen van het Product van de Cloud Service {#assign-team-members-cloud-service}

## Doelstelling {#objective}

Dit document helpt u de stappen begrijpen die uw Beheerder van het Systeem moet nemen om uw teamleden aan AEM als profielen van het product van de Cloud Service toe te wijzen en waarom het cruciaal is om uw Auteurs van AEM toe te laten om op hun reis met AEM te beginnen.

Na het lezen van deze sectie moet u begrijpen:

* Waarom en hoe uw teamleden aan AEM als profielen van het Cloud Service van het product worden toegewezen.
* Teamleden toevoegen aan AEM gebruikersproductprofiel.
* Hoe te om teamleden aan AEM het productprofiel van Beheerders toe te voegen.


## Inleiding {#introduction}

Om toegang tot AEM als Cloud Service te krijgen, moeten gebruikers tot één van twee productprofielen behoren, zoals `AEM Users` of `AEM Administrators`. Uw teamleden moeten machtigingen krijgen voor het AEM exemplaar, aangezien machtigingen voor het beheren van Cloud Manager niet voldoende zijn. Meer weten?

>[!NOTE]
>Elke gebruiker die door de systeembeheerder aan AEM gebruikersproductprofiel is toegewezen, heeft (alleen-lezen) toegang tot Cloud Manager.

## Voorwaarden {#prerequisites}

Voordat u deze sectie gaat lezen, moet u rekening houden met het volgende:

* [AEM als Cloud Service productprofielen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles)
* Wees vertrouwd met [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en)
* De productprofielen van de Manager van de Wolk zijn toegewezen aan uw teamleden zoals aangewezen en de wolkenmiddelen zijn opstelling
* Gegevens over uw teamlid: De Beheerder van het systeem moet de namen en e-mailadressen en de rollen en de verantwoordelijkheden voor de teamleden hebben die toegang tot AEM als Cloud Service zullen vereisen.

   >[!NOTE]
   >Met het oog op het instappen, adviseren wij dat u aanvankelijk gebruikers toevoegt die aan de directe taken, zoals beheerders, ontwikkelaars en inhoudsauteurs zullen deelnemen. U kunt de rest van het instapsysteem voortzetten zonder alle gebruikers toe te voegen. Nadat u klaar bent met het instappen, kunt u aan een groter aantal gebruikers later schrapen.


   >[!IMPORTANT]
   >Voordat u de stappen controleert waarmee u teamleden toewijst aan AEM als productprofielen voor Cloud Servicen, moet u de volgende twee stappen uitvoeren:
   >
   >1. Meld u aan bij [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en). Raadpleeg Aanmelden bij Admin Console voor meer informatie.
      >
      >
   1. Bekijk [AEM als Profiles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles) van het Product van de Cloud Service.


Voer de onderstaande stappen uit om de lijst met Cloud Manager-profielen van Adobe Admin Console weer te geven:

1. Meld u aan bij [Adobe Admin Console](https://adminconsole.adobe.com/). Van **Overzicht** pagina, selecteer **Adobe Experience Manager als Cloud Service** van **Producten en de diensten** kaart.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Navigeer en selecteer de instantie (Author-instantie van de milieu van de Ontwikkeling) zoals aangetoond in het hieronder beeld.

   ![](/help/onboarding/onboarding-journey/assets/cloud-profiles-1.png)


1. U zult de lijst van AEM als productprofielen zien van de Cloud Service die aan een gebruiker zullen moeten worden toegewezen die op hun rol wordt gebaseerd.

   >[!NOTE]
   >Zie [AEM als Cloud Service productprofielen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles) voor meer informatie.

   ![](/help/onboarding/onboarding-journey/assets/cloud-profiles-2.png)


## Teamleden toevoegen aan AEM gebruiker of AEM profiel van beheerdersproduct {#add-team-members}

Gebruikers die toegang willen krijgen tot AEM als instantie Cloud Service, moeten behoren tot een van twee productprofielen `AEM Users` of `AEM Administrators`.

>[!NOTE]
>U moet machtigingen voor de instantie hebben. Rechten voor het beheer van Cloud Manager zijn onvoldoende. Meer weten?

De stappen hieronder moeten door een Beheerder van het Systeem worden gevolgd die ook de rol van BedrijfsEigenaar is.

1. Navigeer naar uw programma vanuit Cloud Manager en selecteer de knop **Toegang beheren** in de context van de omgeving die u interessant vindt, zoals hieronder wordt weergegeven.

   ![](/help/onboarding/onboarding-journey/assets/add-team1.png)

1. Een nieuw tabblad navigeert u naar Adobe Admin Console vanwaar u toegang hebt tot de instantie van de auteur van de omgeving. Selecteer *AEM Beheerders* of *AEM Gebruikers* op basis van de machtigingen die deze persoon moet geven. Meer informatie over [AEM als Cloud Service productprofielen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/add-team2.png)

1. Selecteer `AEM Administrator` of `AEM User` en klik op **Gebruiker toevoegen** zoals hieronder getoond en verzend de noodzakelijke details om het toevoegen van het teamlid te voltooien.

   ![](/help/onboarding/onboarding-journey/assets/add-team3.png)

   De gebruiker u toevoegde zal nu toegang tot de AEM als diensten van de Auteur van de Cloud Service hebben!

   >[!NOTE]
   >U zult deze stappen voor alle milieu&#39;s met inbegrip van Ontwikkeling, Stadium en Productie willen herhalen, als u de informatie van teamleden hebt die toegang beschikbaar nodig hebben.


## Volgende functies {#whats-next}

De gebruikers die u als Cloud Service productprofielen hebt toegewezen aan AEM zijn nu klaar om te leren hoe te om tot Auteur toegang te hebben en vertrouwd te worden met auteurspagina&#39;s in AEM als Cloud Service. U zou de weg moeten volgen, door het document het Leren Weg voor AEM Gebruikers of het Leren Weg voor Ontwikkelaars en de Managers van de Plaatsing te herzien.

## Aanvullende bronnen {#additional-resources}

* [Toegang tot AEM configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en)
* [Handleiding Snel aan de slag met de authoring van pagina&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=en)
