---
title: 'Teamleden toewijzen aan productprofielen van Cloud Manager '
description: Volg deze pagina om te leren hoe u teamleden kunt toewijzen aan productprofielen van Cloud Manager
hide: true
hidefromtoc: true
index: false
source-git-commit: 3dbcc5dd09479a84ed13aad0ee3d8c229520e10f
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 0%

---


# Teamleden toewijzen aan productprofielen van Cloud Manager {#assign-team-members}

Nadat u hebt geleerd hoe u zich aanmeldt bij [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) en uw rechten hebt bekeken als [Systeembeheerder](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=en), kunt u nu teamleden toewijzen aan productprofielen voor Cloud Manager.

## Doelstelling {#objective}

Dit document geeft een overzicht van hoe teamleden vanuit de Admin Console kunnen worden toegewezen aan productprofielen van Cloud Manager.

Nadat u deze sectie hebt gelezen, kunt u het volgende doen:

* Begrijp waarom en hoe u teamleden moet toevoegen.
* Meer informatie over drie verschillende productprofielen van Cloud Manager, zoals Business Owner, Deployment Manager en Developer.
* Teamleden toewijzen aan productprofielen van Cloud Manager, zoals Business Owner, Deployment Manager en Developer.

## Vereisten {#prerequisites}

Voordat u met deze sectie begint, moet u rekening houden met de volgende voorwaarden. U moet een:

* Een systeembeheerder en begrijp [Productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).
* Begrijp [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) grondbeginselen.
* U moet gegevens over uw teamleden hebben. Een systeembeheerder moet de namen en e-mailadressen en de rollen en de verantwoordelijkheden voor de teamleden hebben die toegang tot AEM als Cloud Service zullen vereisen.

   >[!NOTE]
   >Met het oog op het instappen, adviseren wij dat u aanvankelijk gebruikers toevoegt die aan de directe taken, zoals beheerders, ontwikkelaars en inhoudsauteurs zullen deelnemen. U kunt de rest van het instapsysteem voortzetten zonder alle gebruikers toe te voegen. Nadat u klaar bent met het instappen, kunt u aan een groter aantal gebruikers later schrapen.

## Productprofielen van Cloud Manager bekijken {#review-product-profiles}

Vanuit Admin Console kunt u de lijst met Cloud Manager-profielen weergeven.

>[!NOTE]
>Voordat u de productprofielen van Cloud Manager vanuit Admin Console bekijkt, is het raadzaam de beschikbare [Productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) te bekijken.

Voer de onderstaande stappen uit om de lijst met profielen van Cloud Manager weer te geven:

1. Meld u aan bij [Adobe Admin Console](https://adminconsole.adobe.com/). Van **Overzicht** pagina, selecteer **Adobe Experience Manager als Cloud Service** van **Producten en de diensten** kaart.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

   >[!NOTE]
   >Raadpleeg Aanmelden bij Admin Console voor meer informatie over het gebruik van Admin Console.


1. Navigeer naar de **Cloud Manager**-instantie uit de tabel met de lijst met alle instanties.

   ![](/help/onboarding/onboarding-journey/assets/assign-team2.png)

1. De lijst met vooraf geconfigureerde [productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) wordt weergegeven.

   ![](/help/onboarding/onboarding-journey/assets/assign-team3.png)


## Gebruikers toewijzen aan productprofiel van zakelijke eigenaar {#assign-users-business-owner}

U kunt nu gebruikers toevoegen en deze toewijzen aan het productprofiel van de Business Owner van Cloud Manager.

>[!NOTE]
>Om dit te kunnen doen, moet u vanaf de Adobe Admin-console een gebruiker toevoegen aan zowel het product (in dit geval AEM als Cloud Service) als het [Productprofiel Bedrijfseigenaar van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

De volgende stappen zullen u door dit laten lopen:

1. Bepaal de gebruiker(s) die Cloud Manager-programma&#39;s zal beheren en voeg deze toe aan het bedrijfseigenaarsproductprofiel. De systeembeheerder moet de eerste persoon zijn die toegang heeft tot en zich aanmeldt bij Cloud Manager. U dient uzelf (Systeembeheerder) eerst toe te voegen aan het productprofiel van de bedrijfseigenaar.

1. Selecteer [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Overzicht** pagina, selecteer **Adobe Experience Manager als een Cloud Service** product van **Producten en services** kaart zoals hieronder getoond.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Selecteer het tabblad **Gebruikers** in de bovenste navigatie en selecteer **Gebruiker toevoegen**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Typ in het dialoogvenster **Gebruikers toevoegen aan uw team** de e-mailadres van de gebruiker die u wilt toevoegen. Selecteer Adobe ID bij Type id als de Federated ID voor uw teamleden nog niet is ingesteld.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Selecteer **Adobe Experience Manager als Cloud Service** in de productselectie en wijs **Bedrijfseigenaar** productprofiel toe aan de gebruiker, zoals hieronder wordt weergegeven.

   >[!NOTE]
   >Raadpleeg [Productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) om ervoor te zorgen dat aan de juiste gebruikers de juiste rol(en) in de Admin Console wordt toegewezen, zoals hieronder wordt weergegeven.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

   >[!NOTE]
   >Wijs de gebruiker toe aan ten minste één productprofiel zodat de gebruiker toegang heeft tot Cloud Manager. Vergeet niet uzelf (Systeembeheerder) toe te wijzen aan de bedrijfseigenaar.

1. Klik **Opslaan**. Er wordt een welkomstbericht verzonden naar de gebruiker die u hebt toegevoegd. De uitgenodigde gebruiker kan tot de Manager van de Wolk toegang hebben door de verbinding in welkome e-mail te klikken en zich binnen te ondertekenen gebruikend hun Adobe ID.

Gefeliciteerd! Uw nieuwe team van Cloud Manager, inclusief de uzelf die is toegewezen aan de rol &quot;Business Owner&quot;, is nu ingesteld. Leden ontvangen een welkomstbericht waarin ze worden uitgenodigd zich aan te melden en toegang te krijgen tot Cloud Manager. In de rol van bedrijfseigenaar bent u nu maar één stap verwijderd van aanmelding bij Cloud Manager en maakt u het maken van uw cloudbronnen mogelijk.

## Gebruikers toewijzen aan het productprofiel van Deployment Manager {#assign-users-deployment-manager}

1. Bepaal de gebruiker(s) die Cloud Manager-programma&#39;s zal beheren en voeg deze toe aan het productprofiel van Deployment Manager. De systeembeheerder moet de eerste persoon zijn die toegang heeft tot en zich aanmeldt bij Cloud Manager. U dient uzelf (Systeembeheerder) eerst toe te voegen aan het productprofiel van de bedrijfseigenaar.

1. Selecteer [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Overzicht** pagina, selecteer **Adobe Experience Manager als een Cloud Service** product van **Producten en services** kaart zoals hieronder getoond.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Selecteer het tabblad **Gebruikers** in de bovenste navigatie en selecteer **Gebruiker toevoegen**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Typ in het dialoogvenster **Gebruikers toevoegen aan uw team** de e-mailadres van de gebruiker die u wilt toevoegen. Selecteer Adobe ID bij Type id als de Federated ID voor uw teamleden nog niet is ingesteld.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Selecteer **Adobe Experience Manager als Cloud Service** in de productselectie en wijs **Deployment Manager**-productprofiel toe aan de gebruiker, zoals hieronder wordt weergegeven.

   >[!NOTE]
   >Raadpleeg [Productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) om ervoor te zorgen dat aan de juiste gebruikers de juiste rol(en) in de Admin Console wordt toegewezen, zoals hieronder wordt weergegeven.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png).

   >[!IMPORTANT]
   >Gebruikers kunnen worden toegevoegd aan het productprofiel van Deployment Manager nadat bronnen voor Cloud Manager zijn gemaakt.

## Gebruikers toewijzen aan productprofiel voor ontwikkelaars {#assign-users-developer}

1. Bepaal de gebruiker(s) die Cloud Manager-programma&#39;s zal beheren en voeg deze toe aan het productprofiel voor ontwikkelaars. De systeembeheerder moet de eerste persoon zijn die toegang heeft tot en zich aanmeldt bij Cloud Manager. U dient uzelf (Systeembeheerder) eerst toe te voegen aan het productprofiel van de bedrijfseigenaar.

1. Selecteer [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Overzicht** pagina, selecteer **Adobe Experience Manager als een Cloud Service** product van **Producten en services** kaart zoals hieronder getoond.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Selecteer het tabblad **Gebruikers** in de bovenste navigatie en selecteer **Gebruiker toevoegen**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Typ in het dialoogvenster **Gebruikers toevoegen aan uw team** de e-mailadres van de gebruiker die u wilt toevoegen. Selecteer Adobe ID bij Type id als de Federated ID voor uw teamleden nog niet is ingesteld.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Selecteer **Adobe Experience Manager als Cloud Service** in de productselectie en wijs **Developer** productprofiel toe aan de gebruiker, zoals hieronder wordt weergegeven.

   >[!NOTE]
   >Raadpleeg [Productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) om ervoor te zorgen dat aan de juiste gebruikers de juiste rol(en) in de Admin Console wordt toegewezen, zoals hieronder wordt weergegeven.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png).


   >[!IMPORTANT]
   >Gebruikers kunnen aan het productprofiel voor ontwikkelaars worden toegevoegd nadat bronnen voor Cloud Manager zijn gemaakt.

## Volgende functies {#whats-next}

Als systeembeheerder die aan *Bedrijfs eigenaar* rol wordt toegewezen, moet u tot de Manager van de Wolk toegang hebben en login.
>[!NOTE]
>Raadpleeg [Navigeren naar Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en) voor meer informatie over aanmelding en toegang tot Cloud Manager.

Een gebruiker van de Manager van de Wolk in de rol Bedrijfs van Eigenaar kan login en opstelling uw wolkenmiddelen met inbegrip van uw Programma&#39;s en Milieu. Zo kunt u ervoor zorgen dat uw team van experts zo snel mogelijk toegang krijgt tot AEM als Cloud Service.
Nadat uw bedrijfseigenaar uw cloudbronnen heeft ingesteld, kunnen ontwikkelaars en implementatiemanagers die met succes zijn toegevoegd aan de productprofielen van Cloud Manager toegang krijgen tot Cloud Manager en zichzelf vertrouwd maken met de manier waarop ze kunnen doorgaan met hun leerpad.

## Aanvullende bronnen {#additional-resources}

Volg de aanvullende bronnen voor meer informatie over:

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=en)
* [Productprofielen van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)
* [Overzicht van identiteit Admin Console](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
