---
title: as a Cloud Service teams en productprofielen AEM
description: Leer hoe AEM as a Cloud Service team en productprofielen en toegang tot uw gelicentieerde Adobe oplossingen verlenen en beperken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 2d793f22e554c2a4bde8831b5053d1640ba07c70
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# as a Cloud Service teams en productprofielen AEM {#product-profiles}

Leer hoe AEM as a Cloud Service team en productprofielen en toegang tot uw gelicentieerde Adobe oplossingen verlenen en beperken.

## Productprofielen {#profiles}

Wanneer het verlenen van een gebruikerstoegang tot een specifieke oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. De profielen van het product laten elke oplossing toe om zijn eigen reeks gebruikerstoestemmingen te hebben. Deze zijn beschikbaar en toegankelijk via de [Admin Console.](/help/journey-onboarding/admin-console.md)

## as a Cloud Service productprofielen AEM {#aem-product-profiles}

AEM as a Cloud Service is een volledig cloudeigen aanbod dat AEM als service biedt. Het levert AEM op een wolkeninheemse manier, met nieuwe attributen zoals altijd, altijd huidig, altijd veilig, en altijd op schaal. Tezelfdertijd behoudt het het belangrijkste waardevoorstel dat AEM als klantgericht platform aan klanten verstrekt en ondernemingscoreteams toestaat om in hun ontwikkeling en leveringsprocedure te integreren. Zie [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md) voor meer informatie over AEM as a Cloud Service.

Uw AEM as a Cloud Service teamleden worden tijdens het instappen toegevoegd aan en toegewezen aan een of meer van de volgende productprofielen via de Admin Console.

* **AEM**: Een AEM beheerder wordt typisch toegewezen aan ontwikkelaars, in het bijzonder ontwikkelaars die toegang tot, bijvoorbeeld, de ontwikkelomgevingen zullen moeten hebben. Het het productprofiel van de AEM beheerder zal worden gebruikt om beheerdervoorrechten in de bijbehorende AEM instantie te verlenen.

* **AEM**: AEM gebruikers zijn de gebruikers in uw organisatie die AEM over het algemeen as a Cloud Service gebruiken om inhoud tot stand te brengen. Deze gebruikers moeten toegang krijgen tot AEM om hun taken uit te voeren. Het profiel van het AEM gebruikersproduct wordt doorgaans toegewezen aan een auteur van AEM inhoud die de inhoud maakt en bekijkt. Deze inhoud kan van vele soorten zoals pagina&#39;s, activa, publicaties, etc. zijn. Het hieronder weergegeven profiel voor AEM gebruikers wordt toegewezen aan deze leden.

![Productprofielen](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Elke gebruiker die is toegewezen aan een AEM as a Cloud Service productprofiel heeft (alleen-lezen) toegang tot Cloud Manager.

>[!TIP]
>
>Raadpleeg voor meer informatie over het instapproces de [op instapreis.](/help/journey-onboarding/overview.md)

## Productprofielen van Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager heeft vooraf geconfigureerde productprofielen die kunnen worden beschouwd als op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van het team van Cloud Manager door deze toe te wijzen aan deze productprofielen.

>[!TIP]
>
>Raadpleeg het document [Op rollen gebaseerde machtigingen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) voor meer informatie .

Aan elk van de productprofielen zijn specifieke machtigingen gekoppeld.

* **Zakelijke eigenaar** - In deze rol hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, pijpleidingen toe te voegen/uit te geven/te schrappen/in werking te stellen, code in AEM milieu op te stellen, of de controles van de codekwaliteit uit te voeren.
* **Implementatiebeheer** - In deze rol, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code op te stellen aan AEM milieu, of de controles van de codekwaliteit uit te voeren.
* **Ontwikkelaar** - In deze rol, hebt u de toestemming om persoonlijke toegangstokens te produceren om toegang tot it te hebben.
* **Programmabeheerder** - In deze rol, hebt u de toestemming om pijpleidingen te plannen, de drie-rij kwaliteitsspoorten met voeten te treden, en productiegoedkeuring te verstrekken.

Een gebruiker kan aan veelvoudige productprofielen worden toegewezen. Als u bijvoorbeeld beide toewijst **Zakelijke eigenaar** en **Implementatiebeheer** r rollen aan een gebruiker geeft hen de som deze toestemmingen.

Uw team van Cloud Manager omvat ten minste:

* Eén **Zakelijke eigenaar**, die doorgaans ook de systeembeheerder is, en als eerste moet aanmelden bij en toegang krijgen tot Cloud Manager
* Eén **Implementatiebeheer**
* Eén **Ontwikkelaar**

>[!NOTE]
>
>Om toegang te krijgen tot AEM as a Cloud Service, moeten gebruikers tot een van twee productprofielen behoren: `AEM Users` of `AEM Administrators`. Rechten om Cloud Manager te beheren zijn niet voldoende.
