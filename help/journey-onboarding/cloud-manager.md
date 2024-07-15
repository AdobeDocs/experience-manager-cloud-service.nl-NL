---
title: Toegang tot Cloud Manager
description: Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Toegang tot Cloud Manager {#cloud-resources}

In dit deel van de [ onboarding reis, ](overview.md) leert u hoe te om tot Cloud Manager toegang te hebben zodat u opstelling uw projectmiddelen kunt.

## Doelstelling {#objective}

In het vorige artikel in dit onboarding reis, [ toewijzend de Leden van het Team aan de Profielen van het Product van Cloud Manager, ](assign-profiles-cloud-manager.md) u uw team AEMaaCS de juiste rollen verleende. Leer nu hoe u toegang krijgt tot Cloud Manager, zodat u uw projectbronnen kunt instellen die uw team gebruikt.

Aangezien u de vorige stap hebt uitgevoerd, heeft uw team toegang tot Cloud Manager. Cloud Manager wordt gebruikt om uw projectmiddelen zoals programma&#39;s en milieu&#39;s tot stand te brengen en te beheren.

Nadat u dit document hebt gelezen, hebt u het volgende nodig:

* Dat een systeembeheerder aan de **wordt toegewezen BedrijfsEigenaar** rol moet eerste in uw organisatie zijn om zich aan te melden en tot Cloud Manager toegang te hebben die.
* Meld u aan bij Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één toegangspunt voor uw team. Het steunt klanten met ondernemingsontwikkelingsmontages met zijn speciaal gebouwde CI/CD pijpleidingen, die worden uitgerust om grondig te verzekeren en hoogste codekwaliteit om uitzonderlijke ervaringen te leveren. Cloud Manager biedt alles wat nodig is om op zelfbediening aan de slag te gaan, inclusief de mogelijkheid om cloudbronnen en -omgevingen te maken.

Typisch is een teamlid dat aan het **productprofiel van de Bedrijfs eigenaar** wordt toegewezen verantwoordelijk voor het toevoegen van uw wolkenmiddelen zoals programma&#39;s en milieu&#39;s. Dit individu begrijpt de bedrijfsbehoeften en wie de eerste Cloud Manager-configuratie voltooit.

Voor deze onboarding reis, wijst u, als systeembeheerder, reeds aan het **BedrijfsEigenaar** productprofiel toe en kan opstelling de wolkenmiddelen. Afhankelijk van daadwerkelijke projectvereisten, kunnen de bedrijfseigenaars of niet het zelfde als de systeembeheerder zijn.

## Cloud Manager openen als systeembeheerder en bedrijfseigenaar {#access-sysadmin-bo}

Alvorens de teamleden die u aan de **rol van de Bedrijfs eigenaar** toewees tot wolkenmanager toegang hebben en beginnen wolkenmiddelen te creëren, moet de systeembeheerder de **rol van de Bedrijfs Eigenaar** worden toegewezen. Ze moeten zich ook aanmelden bij Cloud Manager, zoals u in de vorige stap op deze instapreis hebt gedaan.

1. Zorg ervoor dat u, als systeembeheerder, de **toegewezen rol van de BedrijfsEigenaar** hebt.

   * Terugkeer aan de vorige stap in deze reis, [ wijs de Leden van het Team aan de Profielen van het Product van Cloud Manager toe, ](assign-profiles-cloud-manager.md) voor meer informatie over het toewijzen van de **BedrijfsEigenaar** rol aan de systeembeheerder.

1. Teken in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en wordt voorgesteld van de normale het landen pagina.

Door met succes binnen als systeembeheerder met de **rol van de BedrijfsEigenaar te ondertekenen**, initialiseert u Cloud Manager voor gebruik door de andere gebruikers met de **BedrijfsEigenaar** rol. Je ontvangt geen bevestiging of bericht. Eenvoudig aanmelden is voldoende.

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

Alternatief, kunt u aan Cloud Manager **Programma&#39;s en de pagina van Producten** van de homepage van Adobe Experience Cloud ook navigeren door deze stappen te volgen

1. Navigeer rechtstreeks aan [ Adobe Experience Cloud ](https://experience.adobe.com) en login gebruikend uw Adobe ID.

1. Van de homepage van Adobe Experience Cloud, uitgezochte **Experience Manager** om de AEM homepage te openen.

   ![ homepage van het Experience Cloud ](/help/journey-onboarding/assets/setup-resources2.png)

1. Op de **Cloud Manager** tegel, uitgezochte **Lancering**.

   ![ AEM homepage ](/help/journey-onboarding/assets/setup-resources3.png)

1. Nadat u zich hebt aangemeld, gaat u naar de bestemmingspagina van Cloud Manager. Zie [ het Bekijken van de Programma&#39;s van Cloud Manager ](#viewing-programs) voor meer details.

Hoe u via Cloud Manager toegang krijgt tot uw programma&#39;s en producten, is aan u en heeft geen invloed op de manier waarop u Cloud Manager gebruikt of op de manier waarop u uw programma&#39;s beheert.

>[!NOTE]
>
>Afhankelijk van de rollen die in Cloud Manager worden toegewezen en de status van de toepassing, ziet u verschillende schermen terwijl het gebruiken van het gebruikersinterface van Cloud Manager.

## Programma&#39;s weergeven {#viewing-programs}

Nadat u Cloud Manager hebt geopend, is wat u ziet afhankelijk van de status van uw programma&#39;s, zoals in de volgende secties wordt beschreven.

### Als er geen programma&#39;s bestaan {#no-programs}

Als er geen programma&#39;s in uw organisatie aanwezig zijn, wordt u op de bestemmingspagina opgedragen het eerste programma te maken.

![ Geen programma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Wanneer er al programma&#39;s bestaan {#programs-exist}

Als er programma&#39;s in uw organisatie aanwezig zijn, wordt op de landingspagina uw bestaande programma&#39;s weergegeven en wordt ook een knop weergegeven waarmee u aanvullende programma&#39;s kunt toevoegen.

![ de Programma&#39;s bestaan ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Wanneer een Programma bestaat en u een Beheerder van het Systeem bent {#programs-exist-sysadmin}

Als de programma&#39;s in uw organisatie bestaan en u een systeembeheerder bent, dan uw het landen paginasvertoningen **leiden de knoop van de Toegang** samen met **voegt de optie van het Programma** toe.

![ de beheerdermening van het Systeem ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Gebruikersrollen controleren {#verify-user-roles}

Zodra u met succes in Cloud Manager hebt geregistreerd, kunt u verifiëren dat u het **productprofiel van de Bedrijfs eigenaar** bent toegewezen.

1. Selecteer het profiel rechtsboven in het venster.

1. Om de rollen te tonen die aan uw gebruiker worden toegewezen, selecteer **Rollen van de Gebruiker**.

   ![ de rollen van de Gebruiker ](/help/journey-onboarding/assets/setup-resources6.png)

1. De dialoog zou moeten bevestigen dat uw gebruiker de **rol van de BedrijfsEigenaar** heeft.

   ![ Lijst van gebruikersrollen ](/help/journey-onboarding/assets/setup-resources7.png)

U hebt zich met succes bij Cloud Manager als Bedrijfseigenaar aangemeld! Als u niet de **rol van de BedrijfsEigenaar** wordt toegewezen, contacteer uw systeembeheerder.

## Volgende functies {#whats-next}

Nu u als systeembeheerder tot Cloud Manager kunt toegang hebben, bent u bereid om uw eerste programma tot stand te brengen.

Ga uw aan boord komende reis door het document te herzien [ voort creeer een Programma ](create-program.md) waar u leert dit te doen.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ Inleiding aan Cloud Manager ](/help/onboarding/cloud-manager-introduction.md) -
Meer informatie over Cloud Manager, Cloud Manager-programma&#39;s en omgevingen.
* [ het Team van AEM as a Cloud Service en de Profielen van het Product ](/help/onboarding/aem-cs-team-product-profiles.md) - leer hoe het team en de productprofielen van AEM as a Cloud Service toegang tot uw vergunning gegeven oplossingen van de Adobe kunnen verlenen en beperken.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
