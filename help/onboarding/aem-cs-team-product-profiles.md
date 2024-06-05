---
title: as a Cloud Service teams en productprofielen AEM
description: Leer hoe AEM as a Cloud Service team en productprofielen toegang tot uw gelicentieerde oplossingen van de Adobe kunnen verlenen en beperken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---


# as a Cloud Service teams en productprofielen AEM {#product-profiles}

Leer hoe AEM as a Cloud Service team en productprofielen toegang tot uw gelicentieerde oplossingen van de Adobe kunnen verlenen en beperken.

## Productprofielen {#profiles}

Wanneer het verlenen van een gebruikerstoegang tot een specifieke oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersrechten. Deze zijn beschikbaar en toegankelijk via de [Admin Console](/help/journey-onboarding/admin-console.md).

## as a Cloud Service productprofielen AEM {#aem-product-profiles}

AEM as a Cloud Service is een volledig cloudeigen aanbod dat AEM als service biedt. Het levert AEM op een wolkeninheemse manier, met nieuwe attributen zoals altijd, altijd huidig, altijd veilig, en altijd op schaal. Tezelfdertijd behoudt het het belangrijkste waardevoorstel dat AEM als klantgericht platform aan klanten verstrekt en ondernemingscoreteams toestaat om in hun ontwikkeling en leveringsprocedure te integreren. Zie [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md) voor meer informatie over AEM as a Cloud Service.

Uw AEM as a Cloud Service teamleden worden tijdens het instappen toegevoegd en toegewezen aan een of meer van de volgende productprofielen via de Admin Console.

* **AEM**: Een AEM beheerder wordt typisch toegewezen aan ontwikkelaars, in het bijzonder ontwikkelaars die toegang tot, bijvoorbeeld, de ontwikkelomgevingen nodig hebben. Het het productprofiel van de AEM beheerder wordt gebruikt om beheerdervoorrechten in de bijbehorende AEM instantie te verlenen.

* **AEM**: AEM gebruikers zijn de gebruikers in uw organisatie die AEM over het algemeen as a Cloud Service gebruiken om inhoud te maken. Deze gebruikers moeten toegang krijgen tot AEM om hun taken uit te voeren. Het profiel van het AEM gebruikersproduct wordt doorgaans toegewezen aan een auteur van AEM inhoud die de inhoud maakt en controleert. Deze inhoud kan van vele soorten zoals pagina&#39;s, activa, publicaties, etc. zijn. Het hieronder weergegeven profiel voor AEM gebruikers wordt toegewezen aan deze leden.

![Productprofielen](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Elke gebruiker die is toegewezen aan een AEM as a Cloud Service productprofiel heeft alleen-lezentoegang tot Cloud Manager via de **Gebruiker van Cloud Manager** rol.
>
>Gebruikers met alleen de **Gebruiker van Cloud Manager** Deze rol kan u aanmelden bij Cloud Manager en naar de AEM auteursomgevingen navigeren (als deze bestaan) door de **Programma&#39;s** menuopties. De **Gebruiker van Cloud Manager** de rol is niet voldoende om toegang te krijgen tot de programmagegevens . Als dergelijke toegang nodig is, moeten de gebruikers extra rollen door hun systeembeheerder worden verleend.

>[!WARNING]
>
>De **AEM** de naam van het productprofiel mag niet worden gewijzigd. De naam van de **AEM** met het productprofiel worden de beheerdersrechten verwijderd van alle gebruikers die aan dat profiel zijn toegewezen.

>[!TIP]
>
>* Ga voor meer informatie over AEM productprofielen naar [AEM productprofielen toewijzen](/help/journey-onboarding/assign-profiles-aem.md).
>* Voor meer informatie over het instapproces raadpleegt u [instapreis](/help/journey-onboarding/overview.md).

## Productprofielen van Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager heeft vooraf geconfigureerde productprofielen die kunnen worden beschouwd als op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van het team van Cloud Manager door deze toe te wijzen aan deze productprofielen.

>[!TIP]
>
>Zie [Op rollen gebaseerde machtigingen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) voor meer informatie .

Aan elk van de productprofielen zijn specifieke machtigingen gekoppeld.

* **Zakelijke eigenaar**
   * In deze rol hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, code in AEM milieu op te stellen, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker is verantwoordelijk voor het definiëren van KPI&#39;s, het goedkeuren van productieimplementaties en het overschrijven van belangrijke 3-tivelige fouten indien nodig.
* **Implementatiebeheer**
   * In deze rol, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code op te stellen aan AEM milieu, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker beheert implementatiebewerkingen en gebruikt Cloud Manager voor het uitvoeren van testings-/productieimplementaties, het bewerken van CI-/CD-pijpleidingen, het goedkeuren van belangrijke 3-laagfouten indien nodig, en kan toegang krijgen tot de git-opslagruimte.
* **Ontwikkelaar**
   * In deze rol, hebt u de toestemming om persoonlijke toegangstokens te produceren om tot git toegang te hebben.
   * Deze gebruiker ontwikkelt en test de code van de douanetoepassing en gebruikt hoofdzakelijk de status van de Manager van de Wolk om plaatsingsstatus te bekijken en kan tot de git bewaarplaats voor codeverplichtingen toegang hebben.
* **Programmabeheerder**
   * In deze rol, hebt u de toestemming om pijpleidingen te plannen, de de kwaliteitsspoorten van drie lagen met voeten te treden, en productiegoedkeuring te verstrekken.
   * Deze gebruiker gebruikt Cloud Manager om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kan belangrijke drie-rij mislukkingen goedkeuren wanneer noodzakelijk.

Een gebruiker kan aan veelvoudige productprofielen worden toegewezen. Als u bijvoorbeeld beide toewijst **Zakelijke eigenaar** en **Implementatiebeheer** r rollen aan een gebruiker geeft hen de som deze toestemmingen.

Uw team van Cloud Manager omvat ten minste:

* Eén **Zakelijke eigenaar**, die doorgaans ook de systeembeheerder is, en als eerste moet aanmelden bij en toegang krijgen tot Cloud Manager
* Eén **Implementatiebeheer**
* Eén **Ontwikkelaar**

>[!NOTE]
>
>Om toegang te krijgen tot AEM as a Cloud Service, moeten gebruikers tot een van twee productprofielen behoren: `AEM Users` of `AEM Administrators`. Rechten om Cloud Manager te beheren zijn niet voldoende.

>[!TIP]
>
>* Ga voor meer informatie over productprofielen van Cloud Manager naar [Teamleden toewijzen aan productprofielen van Cloud Manager](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Voor meer informatie over het instapproces raadpleegt u [instapreis](/help/journey-onboarding/overview.md).
