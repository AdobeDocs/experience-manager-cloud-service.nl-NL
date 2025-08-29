---
title: Toegang tot Cloud Manager
description: Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 841e30bc279a3859ce9a302b18ddf566d8163100
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Toegang tot Cloud Manager {#cloud-resources}

In dit deel van de [ onboarding reis ](overview.md), leert u hoe te om tot Cloud Manager toegang te hebben zodat u opstelling uw projectmiddelen kunt.

## Doelstelling {#objective}

In het vorige artikel in dit onboarding reis, [ toewijzend de Leden van het Team aan de Profielen van het Product van Cloud Manager ](assign-profiles-cloud-manager.md), verleende u uw team AEMaaCS de juiste rollen. Nu, leer hoe te om tot Cloud Manager toegang te hebben zodat u uw projectmiddelen kunt opstelling die uw team van plan is te gebruiken.

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

   Terugkeer aan de vorige stap, [ wijs de Leden van het Team aan de Profielen van het Product van Cloud Manager ](assign-profiles-cloud-manager.md) toe, voor details bij het toewijzen van de **BedrijfsEigenaar** rol aan de systeembeheerder.

1. Teken in Cloud Manager bij [ experience.adobe.com ](https://experience.adobe.com/).
1. In de Snelle groepering van de Toegang, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.

   ![ Cloud Manager op console ](/help/journey-onboarding/assets/consol-cloud-manager.png)

Door met succes binnen als systeembeheerder met de **rol van de BedrijfsEigenaar te ondertekenen**, gebruikt u Cloud Manager voor gebruik door de andere gebruikers met de **BedrijfsEigenaar** rol. Je ontvangt geen bevestiging of bericht. Eenvoudig aanmelden is voldoende.

Totdat u binnen aan Cloud Manager als systeembeheerder met de **rol van BedrijfsEigenaar** ondertekent, kunnen andere gebruikers met de **rol van BedrijfsEigenaar** geen programma&#39;s in Cloud Manager tot stand brengen. Deze regel is waar zelfs als zij de correcte rollen worden toegewezen.

## Navigeren naar Cloud Manager {#navigate-cloud-manager}

De gebruikers met de **rol van de BedrijfsEigenaar** ontvangen een welkome e-mail met een verbinding om te beginnen. Volg de onderstaande stappen om naar Cloud Manager te navigeren met deze welkomstmail.

1. Van uw welkome e-mail, klik **begonnen worden**, zoals aangetoond in het hieronder cijfer.
   ![ E-mailvoorbeeld ](/help/journey-onboarding/assets/get-started-email.png)

1. Navigeer aan Cloud Manager **Programma&#39;s &amp; de pagina van Producten**.

   >[!TIP]
   >
   >U kunt ook rechtstreeks vanuit `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)` naar de Cloud Manager-aanmeldingspagina navigeren. Bladwijzer maken van deze pagina voor toekomstig gebruik.

1. U wordt naar de bestemmingspagina van Cloud Manager geleid.

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

![ Geen programma&#39;s ](/help/journey-onboarding/assets/cloud-manager-programs-do-not-exist.png)

### Wanneer programma&#39;s al bestaan {#programs-exist}

Als er programma&#39;s in uw organisatie aanwezig zijn, wordt op de landingspagina uw bestaande programma&#39;s weergegeven en wordt ook een knop weergegeven waarmee u aanvullende programma&#39;s kunt toevoegen.

![ de Programma&#39;s bestaan ](/help/journey-onboarding/assets/cloud-manager-programs-exist.png)

### Wanneer een programma bestaat en u een Beheerder van het Systeem bent {#programs-exist-sysadmin}

Als de programma&#39;s in uw organisatie bestaan en u een systeembeheerder bent, dan toont uw landende pagina **de Manage knoop van de Toegang** samen met **voegt de optie van het Programma** toe.

![ de beheerdermening van het Systeem ](/help/journey-onboarding/assets/cloud-manager-programs-as-sysadmin.png)

## Verifieer uw gebruikersrollen {#verify-user-roles}

Zodra u met succes in Cloud Manager hebt het programma geopend, kunt u verifiëren dat u het **productprofiel van de Bedrijfs eigenaar** &lbrace;wordt toegewezen.

1. Vlak de hoger-juiste hoek van de pagina, klik het **pictogram van de Rekening**.

1. Klik **Rollen van de Gebruiker**.

   ![ de rollen van de Gebruiker ](/help/journey-onboarding/assets/cloud-manager-user-roles.png)

1. In het **de dialoogvakje van de Rollen van de Gebruiker**, bevestig dat uw gebruiker de **BedrijfsEigenaar** rol heeft.

   ![ Lijst van gebruikersrollen ](/help/journey-onboarding/assets/cloud-manager-user-roles-business-owner.png)

U hebt zich met succes bij Cloud Manager als Bedrijfseigenaar aangemeld. Als u niet de **rol van de BedrijfsEigenaar** wordt toegewezen, contacteer uw systeembeheerder.

## Wat nu? {#whats-next}

Nu u als systeembeheerder tot Cloud Manager kunt toegang hebben, bent u bereid om uw eerste programma tot stand te brengen.

Ga uw aan boord komende reis door het document te herzien [ voort creeer een Programma ](create-program.md) waar u leert dit te doen.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ Inleiding aan Cloud Manager ](/help/onboarding/cloud-manager-introduction.md) -
Meer informatie over Cloud Manager, Cloud Manager-programma&#39;s en omgevingen.
* [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md) - leer hoe het team en de productprofielen van AEM as a Cloud Service toegang tot uw vergunning gegeven oplossingen van Adobe kunnen verlenen en beperken.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
