---
title: AEM as a Cloud Service-team en productprofielen
description: Leer hoe AEM as a Cloud Service-teams en productprofielen toegang tot uw bekabelde Adobe-oplossingen kunnen verlenen en beperken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---


# AEM as a Cloud Service-team en productprofielen {#product-profiles}

Leer hoe AEM as a Cloud Service-teams en productprofielen toegang tot uw bekabelde Adobe-oplossingen kunnen verlenen en beperken.

## Productprofielen {#profiles}

Wanneer het verlenen van een gebruikerstoegang tot een specifieke oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersrechten. Deze zijn beschikbaar en toegankelijk via de [ Admin Console ](/help/journey-onboarding/admin-console.md).

## AEM as a Cloud Service-productprofielen {#aem-product-profiles}

AEM as a Cloud Service is een volledig eigen cloudaanbod dat AEM als service biedt. Het levert AEM op een wolkeninheemse manier, met nieuwe attributen zoals altijd, altijd huidig, altijd veilig, en altijd op schaal. Tezelfdertijd behoudt het het belangrijkste waardevoorstel dat AEM als klantgericht platform aan klanten verstrekt en ondernemingscoreteams toestaat om in hun ontwikkeling en leveringsprocedure te integreren. Zie [ Inleiding aan Adobe Experience Manager as a Cloud Service ](/help/overview/introduction.md) om meer over AEM as a Cloud Service te leren.

Uw AEM as a Cloud Service-teamleden worden tijdens het instappen toegevoegd aan en toegewezen aan een of meer van de volgende productprofielen via de Admin Console.

* **AEM Beheerders**: Een AEM beheerder wordt typisch toegewezen aan ontwikkelaars, in het bijzonder ontwikkelaars die toegang tot, bijvoorbeeld, de ontwikkelomgevingen nodig hebben. Het het productprofiel van de AEM beheerder wordt gebruikt om beheerdervoorrechten in de bijbehorende AEM instantie te verlenen.

* **AEM Gebruikers**: AEM gebruikers zijn de gebruikers in uw organisatie die AEM as a Cloud Service over het algemeen gebruiken om inhoud tot stand te brengen. Deze gebruikers moeten toegang krijgen tot AEM om hun taken uit te voeren. Het profiel van het AEM gebruikersproduct wordt doorgaans toegewezen aan een auteur van AEM inhoud die de inhoud maakt en controleert. Deze inhoud kan van vele soorten zoals pagina&#39;s, activa, publicaties, etc. zijn. Het hieronder weergegeven profiel voor AEM gebruikers wordt toegewezen aan deze leden.

![ Profielen van het Product ](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Elke gebruiker die aan een het productprofiel van AEM as a Cloud Service wordt toegewezen heeft read-only toegang tot Cloud Manager via de **** rol van de Gebruiker van Cloud Manager.
>
>De gebruikers met slechts de **rol van de Gebruiker 0} Cloud Manager kunnen in Cloud Manager registreren en aan de AEM auteursmilieu&#39;s (als zij bestaan) navigeren door de** Programma&#39;s **menuopties te gebruiken.** De **rol van de Gebruiker van 0} Cloud Manager {is niet voldoende om tot programmadetails toegang te hebben.** Als dergelijke toegang nodig is, moeten de gebruikers extra rollen door hun systeembeheerder worden verleend.

>[!WARNING]
>
>De **AEM Beheerders** naam van het productprofiel moet niet worden veranderd. Het veranderen van de naam van het **AEM Beheerders** productprofiel zal beheerderrechten uit alle gebruikers verwijderen die aan dat profiel worden toegewezen.

>[!TIP]
>
>* Meer over AEM productprofielen leren, zie [ Toewijzend AEM Profielen van het Product ](/help/journey-onboarding/assign-profiles-aem.md).
>* Voor meer informatie over het onboarding proces, zie [ onboarding reis ](/help/journey-onboarding/overview.md).

## Cloud Manager-productprofielen {#cloud-manager-product-profiles}

Cloud Manager beschikt over vooraf geconfigureerde productprofielen die kunnen worden beschouwd als op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van uw Cloud Manager-team door deze toe te wijzen aan deze productprofielen.

>[!TIP]
>
>Zie [ Rol Gebaseerde Toestemmingen in Cloud Manager ](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) voor meer details.

Aan elk van de productprofielen zijn specifieke machtigingen gekoppeld.

* **BedrijfsEigenaar**
   * In deze rol hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, code in AEM milieu op te stellen, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker is verantwoordelijk voor het definiëren van KPI&#39;s, het goedkeuren van productieimplementaties en het overschrijven van belangrijke 3-tivelige fouten indien nodig.
* **Manager van de Plaatsing**
   * In deze rol, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code op te stellen aan AEM milieu, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker beheert implementatiebewerkingen en gebruikt Cloud Manager om staging-/productieimplementaties uit te voeren, CI-/CD-pijpleidingen te bewerken, belangrijke 3-tielfouten indien nodig goed te keuren en toegang te krijgen tot de git-opslagruimte.
* **Ontwikkelaar**
   * In deze rol, hebt u de toestemming om persoonlijke toegangstokens te produceren om tot git toegang te hebben.
   * Deze gebruiker ontwikkelt en test de code van de douanetoepassing en gebruikt hoofdzakelijk Cloud Manager om plaatsingsstatus te bekijken en kan tot de git bewaarplaats voor codeverplichtingen toegang hebben.
* **Manager van het Programma**
   * In deze rol, hebt u de toestemming om pijpleidingen te plannen, de de kwaliteitsspoorten van drie lagen met voeten te treden, en productiegoedkeuring te verstrekken.
   * Deze gebruiker gebruikt Cloud Manager om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kan belangrijke 3-rij mislukkingen goedkeuren wanneer noodzakelijk.

Een gebruiker kan aan veelvoudige productprofielen worden toegewezen. Bijvoorbeeld, die zowel **BedrijfsEigenaar** toewijst en **Plaatsing leidt** r rollen aan een gebruiker hen de som deze toestemmingen.

Uw Cloud Manager-team omvat ten minste:

* Één **BedrijfsEigenaar**, die typisch ook de systeembeheerder is, en moet de eerste persoon aan login en toegang Cloud Manager zijn
* Één **Manager van de Plaatsing**
* Één **Ontwikkelaar**

>[!NOTE]
>
>Gebruikers die toegang tot AEM as a Cloud Service willen krijgen, moeten behoren tot een van de volgende twee productprofielen: `AEM Users` of `AEM Administrators` . Machtigingen om Cloud Manager te beheren volstaan niet.

>[!TIP]
>
>* Meer over het productprofielen van Cloud Manager leren, zie [ Toewijzend de Leden van het Team aan de Profielen van het Product van Cloud Manager ](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Voor meer informatie over het onboarding proces, zie [ onboarding reis ](/help/journey-onboarding/overview.md).
