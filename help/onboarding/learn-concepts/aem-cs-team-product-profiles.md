---
title: AEM als team van Cloud Servicen en productprofielen
description: Volg deze pagina om over AEM als Team van de Cloud Service en Profielen van het Product te leren.
source-git-commit: 312b1ce7dc660d1bb4fe199be0e7403069d30161
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# AEM als team van Cloud Servicen en productprofielen {#product-profiles}

AEM als Cloud Service is het volledig clouds-inheemse aanbod dat AEM als dienst levert. Het levert AEM op een wolkeninheemse manier, met nieuwe attributen zoals altijd, altijd huidig, altijd veilig, en altijd op schaal. Tezelfdertijd behoudt het het belangrijkste waardevoorstel dat AEM verstrekt als aanpasbaar platform aan klanten en laat teams van ondernemingsrang toe om in hun ontwikkeling en leveringsprocedure te integreren. Om naar [Inleiding aan Adobe Experience Manager als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en) te verwijzen om meer over AEM als Cloud Service te leren.

Uw AEM als teamleden van de Cloud Service worden tijdens het instappen toegevoegd aan en toegewezen aan een of meer van de volgende productprofielen via Admin Console.


## AEM als productprofielen {#aem-product-profiles} van de Cloud Service

De volgende productprofielen zijn in AEM beschikbaar als team van Cloud Servicen:

* **AEM beheerder**: Een AEM Beheerder wordt typisch toegewezen aan ontwikkelaars, in het bijzonder ontwikkelaars die toegang tot, bijvoorbeeld, de ontwikkelomgevingen zullen moeten hebben. Het productprofiel AEM Beheerders wordt gebruikt om beheerdersrechten toe te kennen in de bijbehorende AEM.

* **AEM gebruiker**: AEM Gebruikers zijn de gebruikers in uw organisatie die AEM als Cloud Service gebruiken als onderdeel van de overeenkomst met Adobe. Deze leden moeten toegang krijgen tot AEM om hun taken uit te voeren. Het profiel AEM gebruikers wordt doorgaans toegewezen aan een auteur van AEM inhoud die de inhoud maakt en reviseert (dit kan van verschillende typen zijn). bijvoorbeeld pagina&#39;s, middelen, publicaties enzovoort) voordat deze op uw website worden gepubliceerd. Het hieronder weergegeven profiel voor AEM gebruikers wordt toegewezen aan deze leden.

   >[!NOTE]
   >Elke gebruiker die als een Cloud Service-productprofiel aan een AEM is toegewezen, heeft (alleen-lezen) toegang tot Cloud Manager.

## Productprofielen van Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager heeft vooraf geconfigureerde productprofielen, of meer eenvoudig, op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van uw team van Cloud Manager door de profielen aan deze productprofielen toe te wijzen en moet zich vertrouwd maken met deze productprofielen en aan welk teamlid ze moeten toewijzen.
>[!NOTE]
>Raadpleeg [Op rol gebaseerde machtigingen in Cloud Manager](/help/onboarding/what-is-required/user-roles-permissions.md) voor meer informatie.

Aan elk productprofiel zijn specifieke machtigingen gekoppeld. Bijvoorbeeld, als u in de rol van a bent:

* **Bedrijfs Eigenaar**, hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, de pijpleiding toe te voegen/uit te geven en om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of codekwaliteit op te stellen.

* **De Manager** van de plaatsing, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of code-kwaliteit op te stellen.

* **De ontwikkelaar**, hebt u de toestemming om Persoonlijk Token van de Toegang te produceren om tot Git toegang te hebben.

* **Programmamanager**, hebt u de toestemming om tot Git toegang te hebben.

Een gebruiker kan aan veelvoudige productprofielen worden toegewezen. Bijvoorbeeld, geeft het toewijzen van zowel de rollen Bedrijfs van de Eigenaar als van de Manager van de Plaatsing aan een gebruiker hen de combinatie of de som deze toestemmingen.

Uw team van Cloud Manager omvat ten minste:

* Één Bedrijfs Eigenaar, die typisch ook de Beheerder van het Systeem is en de eerste persoon moet zijn om login en tot de Manager van de Wolk toegang te hebben
* One Deployment Manager
* Eén ontwikkelaar

   >[!NOTE]
   >Gebruikers die toegang tot AEM als Cloud Service willen krijgen, moeten behoren tot een van twee productprofielen `AEM Users-xxx` of `AEM Administrators-xxx`. U moet over machtigingen voor de instantie beschikken. Machtigingen om de gekoppelde Cloud Manager te beheren zijn niet voldoende.