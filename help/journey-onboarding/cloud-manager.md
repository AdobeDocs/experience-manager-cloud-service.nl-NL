---
title: Toegang tot Cloud Manager
description: Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 858a9c4b61fd3a80a257313e48816b067ca77175
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---

# Toegang tot Cloud Manager {#cloud-resources}

In dit deel van de [&#x200B; onboarding reis &#x200B;](overview.md), leert u hoe te om tot Cloud Manager toegang te hebben zodat u opstelling uw projectmiddelen kunt.

## Doelstelling {#objective}

In het vorige artikel in dit onboarding reis, [&#x200B; toewijzend de Leden van het Team aan de Profielen van het Product van Cloud Manager &#x200B;](assign-profiles-cloud-manager.md), verleende u uw team AEMaaCS de juiste rollen. Nu, leer hoe te om tot Cloud Manager toegang te hebben zodat u uw projectmiddelen kunt opstelling die uw team van plan is te gebruiken.

Aangezien u de vorige stap hebt uitgevoerd, heeft uw team toegang tot Cloud Manager. Cloud Manager wordt gebruikt om uw projectmiddelen, zoals programma&#39;s en milieu&#39;s tot stand te brengen en te beheren.

Nadat u dit document hebt gelezen, hebt u het volgende nodig:

* Dat een systeembeheerder aan de **wordt toegewezen BedrijfsEigenaar** rol moet eerste in uw organisatie zijn om zich aan te melden en tot Cloud Manager toegang te hebben die.
* Meld u aan bij Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één toegangspunt voor uw team. Het steunt klanten met ondernemingsontwikkelingsmontages met zijn speciaal gebouwde CI/CD pijpleidingen, die worden uitgerust om grondig te verzekeren en hoogste codekwaliteit om uitzonderlijke ervaringen te leveren. Cloud Manager biedt alles wat nodig is om op zelfbediening aan de slag te gaan, zoals de mogelijkheid om cloudbronnen en -omgevingen te maken.

Typisch is een teamlid dat aan het **productprofiel van de Bedrijfs eigenaar** wordt toegewezen verantwoordelijk voor het toevoegen van uw wolkenmiddelen, zoals programma&#39;s en milieu&#39;s. Dit individu begrijpt de bedrijfsbehoeften en wie de eerste Cloud Manager-configuratie voltooit.

Voor deze onboarding reis, wijst u, als systeembeheerder, reeds aan het **BedrijfsEigenaar** productprofiel toe en kan opstelling de wolkenmiddelen. Afhankelijk van daadwerkelijke projectvereisten, kunnen de bedrijfseigenaars of niet het zelfde als de systeembeheerder zijn.

## Cloud Manager openen als systeembeheerder en bedrijfseigenaar {#access-sysadmin-bo}

Vóór de teamleden die u aan de **rol van de Bedrijfs eigenaar** toewees kunnen tot Cloud Manager toegang hebben en beginnen wolkenmiddelen te creëren, moet de systeembeheerder de **rol van BedrijfsEigenaar** worden toegewezen. Ze moeten zich ook aanmelden bij Cloud Manager, zoals u in de vorige stap op deze instapreis hebt gedaan.

1. Zorg ervoor dat u, als systeembeheerder, de **toegewezen rol van de BedrijfsEigenaar** hebt.

   Terugkeer aan de vorige stap, [&#x200B; wijs de Leden van het Team aan de Profielen van het Product van Cloud Manager &#x200B;](assign-profiles-cloud-manager.md) toe, voor details bij het toewijzen van de **BedrijfsEigenaar** rol aan de systeembeheerder.

1. Teken in Cloud Manager bij [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com).
1. In de Snelle groepering van de Toegang, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.

   ![&#x200B; Cloud Manager op console &#x200B;](/help/journey-onboarding/assets/consol-cloud-manager.png)

Een systeembeheerder met de **rol van de BedrijfsEigenaar** moet binnen aan Cloud Manager eerst ondertekenen. Dit aanvankelijke teken-binnen laat andere gebruikers met de **rol van de Eigenaar van 0&rbrace; Bedrijfs toe om programma&#39;s tot stand te brengen; geen bevestiging verschijnt.**

<!--
By successfully signing in as a system administrator with the **Business Owner** role, you use Cloud Manager for use by the other users with the **Business Owner** role. You do not receive a confirmation or any message. Simply signing in is sufficient.

Until you sign in to Cloud Manager as a system administrator with the **Business Owner** role, other users with the **Business Owner** role cannot create programs in Cloud Manager. This rule is true even if they are assigned the correct roles. -->

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

1. Ga naar [&#x200B; experience.adobe.com/experiencemanager &#x200B;](https://experience.adobe.com/experiencemanager).
1. In het linkerzijpaneel, klik **Cloud Manager**.

>[!NOTE]
>
>Afhankelijk van de rollen die in Cloud Manager worden toegewezen en de status van de toepassing, ziet u verschillende schermen terwijl het gebruiken van het gebruikersinterface van Cloud Manager.

<!--
Users with the **Business Owner** role receive a welcome email with a link to get started. Follow the steps below to navigate to Cloud Manager using this welcome email.

1. From your welcome email, click **Get started**, as shown in the figure below.
    ![Email example](/help/journey-onboarding/assets/get-started-email.png)

1. Navigate to Cloud Manager's **Programs & Products** page.

   >[!TIP]
   >
   >You can also navigate directly to Cloud Manager's login page from `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`. Bookmark this page for future reference.

1. You are directed to Cloud Manager's landing page. -->

<!-- OLD
Alternatively, you can navigate to Cloud Manager's **Programs and Products** page from the Adobe Experience Cloud home page using these steps.

1. Navigate directly to [Adobe Experience Cloud](https://experience.adobe.com) and login using your Adobe ID.

1. From the Adobe Experience Cloud home page, select **Experience Manager** to open the AEM home page.

   ![Experience Cloud homepage](/help/journey-onboarding/assets/setup-resources2.png)

1. On the **Cloud Manager** tile, select **Launch**.

   ![AEM home page](/help/journey-onboarding/assets/setup-resources3.png)

1. After successfully logging on, you are directed to the Cloud Manager landing page. See [Viewing Cloud Manager's Programs](#viewing-programs) for more details.

How you access your programs and products via Cloud Manager is up to you and has no effect on how you use Cloud Manager or how you manage your programs.

>[!NOTE]
>
>Depending on the roles assigned in Cloud Manager and the state of the application, you see different screens while using the Cloud Manager user interface. -->

## Programma&#39;s weergeven {#viewing-programs}

Nadat u Cloud Manager hebt geopend, is wat u ziet afhankelijk van de status van uw programma&#39;s, zoals in de volgende secties wordt beschreven.

### Als er geen programma&#39;s bestaan {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken.

![&#x200B; Geen programma&#39;s &#x200B;](/help/journey-onboarding/assets/cloud-manager-programs-do-not-exist.png)

### Wanneer programma&#39;s al bestaan {#programs-exist}

Als er programma&#39;s in uw organisatie aanwezig zijn, wordt op de landingspagina uw bestaande programma&#39;s weergegeven en wordt ook een knop weergegeven waarmee u aanvullende programma&#39;s kunt toevoegen.

![&#x200B; de Programma&#39;s bestaan &#x200B;](/help/journey-onboarding/assets/cloud-manager-programs-exist.png)

### Wanneer een programma bestaat en u een Beheerder van het Systeem bent {#programs-exist-sysadmin}

Als de programma&#39;s in uw organisatie bestaan en u een systeembeheerder bent, dan toont uw landende pagina **de Manage knoop van de Toegang** samen met **voegt de optie van het Programma** toe.

![&#x200B; de beheerdermening van het Systeem &#x200B;](/help/journey-onboarding/assets/cloud-manager-programs-as-sysadmin.png)

## Verifieer uw gebruikersrollen {#verify-user-roles}

Zodra u met succes in Cloud Manager hebt het programma geopend, kunt u verifiëren dat u het **productprofiel van de Bedrijfs eigenaar** &lbrace;wordt toegewezen.

1. Vlak de hoger-juiste hoek van de pagina, klik het **pictogram van de Rekening**.

1. Klik **Rollen van de Gebruiker**.

   ![&#x200B; de rollen van de Gebruiker &#x200B;](/help/journey-onboarding/assets/cloud-manager-user-roles.png)

1. In het **de dialoogvakje van de Rollen van de Gebruiker**, bevestig dat uw gebruiker de **BedrijfsEigenaar** rol heeft.

   ![&#x200B; Lijst van gebruikersrollen &#x200B;](/help/journey-onboarding/assets/cloud-manager-user-roles-business-owner.png)

U hebt zich met succes bij Cloud Manager als Bedrijfseigenaar aangemeld. Als u niet de **rol van de BedrijfsEigenaar** wordt toegewezen, contacteer uw systeembeheerder.

## Wat nu? {#whats-next}

Nu u als systeembeheerder tot Cloud Manager kunt toegang hebben, bent u bereid om uw eerste programma tot stand te brengen.

Ga uw aan boord komende reis door het document te herzien [&#x200B; voort creeer een Programma &#x200B;](create-program.md) waar u leert dit te doen.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [&#x200B; Inleiding aan Cloud Manager &#x200B;](/help/onboarding/cloud-manager-introduction.md) -
Meer informatie over Cloud Manager, Cloud Manager-programma&#39;s en omgevingen.
* [&#x200B; het Team van AEM as a Cloud Service en de Profielen van het Product &#x200B;](/help/onboarding/aem-cs-team-product-profiles.md) - leer hoe het team en de productprofielen van AEM as a Cloud Service toegang tot uw vergunning gegeven oplossingen van Adobe kunnen verlenen en beperken.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
