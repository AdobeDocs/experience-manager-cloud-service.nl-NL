---
title: as a Cloud Service teams en productprofielen AEM
description: Volg deze pagina om informatie over AEM as a Cloud Service Team en Profielen van het Product te leren.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 56ca8e80081e62ceb3f5fc2bf9c32aa3bcee12c6
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# as a Cloud Service teams en productprofielen AEM {#product-profiles}

## Productprofielen {#profiles}

Wanneer het verlenen van een gebruikerstoegang tot een specifieke oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersmachtigingen. Deze zijn beschikbaar en toegankelijk via de [Adobe Admin Console](/help/onboarding/learn-concepts/admin-console.md).

Meer informatie over [as a Cloud Service productprofielen AEM](#aem-product-profiles) en [Productprofielen van Cloud Manager](#cloud-manager-product-profiles) om te begrijpen hoe deze in overleg werken terwijl uw team is ingesteld.

## as a Cloud Service productprofielen AEM {#aem-product-profiles}

AEM as a Cloud Service is het volledig cloud-native aanbod dat AEM als service biedt. Het levert AEM op een wolkeninheemse manier, met nieuwe attributen zoals altijd, altijd huidig, altijd veilig, en altijd op schaal. Tezelfdertijd behoudt het het belangrijkste waardevoorstel dat AEM als klantgericht platform aan klanten verstrekt en ondernemingscoreteams toestaat om in hun ontwikkeling en leveringsprocedure te integreren. Zie [Inleiding tot Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en) voor meer informatie over AEM as a Cloud Service.

Uw AEM as a Cloud Service teamleden worden tijdens het instappen toegevoegd aan en toegewezen aan een of meer van de volgende productprofielen via Admin Console.

* **AEM**: Een AEM Beheerder wordt typisch toegewezen aan ontwikkelaars, in het bijzonder ontwikkelaars die toegang tot, bijvoorbeeld, de ontwikkelomgevingen zullen moeten hebben. Het productprofiel AEM Beheerders wordt gebruikt om beheerdersrechten toe te kennen in de bijbehorende AEM.

* **AEM**: AEM Gebruikers zijn de gebruikers in uw organisatie die AEM as a Cloud Service gebruiken als onderdeel van de overeenkomst met Adobe. Deze leden moeten toegang krijgen tot AEM om hun taken uit te voeren. Het profiel AEM gebruikers wordt doorgaans toegewezen aan een auteur van AEM inhoud die de inhoud maakt en reviseert (dit kan van verschillende typen zijn). bijvoorbeeld pagina&#39;s, middelen, publicaties enzovoort) voordat deze op uw website worden gepubliceerd. Het hieronder weergegeven profiel voor AEM gebruikers wordt toegewezen aan deze leden.

   ![](/help/onboarding/learn-concepts/assets/admin-console-profiles.png)

   >[!NOTE]
   >Elke gebruiker die is toegewezen aan een AEM as a Cloud Service productprofiel heeft (alleen-lezen) toegang tot Cloud Manager.

## Productprofielen van Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager heeft vooraf geconfigureerde productprofielen, of meer eenvoudig, op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van uw team van Cloud Manager door de profielen aan deze productprofielen toe te wijzen en moet zich vertrouwd maken met deze productprofielen en aan welk teamlid ze moeten toewijzen.
>[!NOTE]
>Zie [Op rollen gebaseerde machtigingen in Cloud Manager](/help/onboarding/learn-concepts/cloud-manager-introduction.md##role-based-permissions) voor meer informatie .

Aan elk productprofiel zijn specifieke machtigingen gekoppeld. Bijvoorbeeld, als u in de rol van a bent:

* **Zakelijke eigenaar**, hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, de pijpleiding toe te voegen/uit te geven en om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of codekwaliteit op te stellen.

* **Implementatiebeheer**, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of code-kwaliteit op te stellen.

* **Ontwikkelaar**, hebt u de toestemming om Persoonlijk Token van de Toegang te produceren om tot Git toegang te hebben.

* **Programmabeheerder**, hebt u de toestemming om pijpleidingen te plannen, de kwaliteitskates van drie lagen met voeten te treden, en productietoestemming te verstrekken.

Een gebruiker kan aan veelvoudige productprofielen worden toegewezen. Bijvoorbeeld, geeft het toewijzen van zowel de rollen Bedrijfs van de Eigenaar als van de Manager van de Plaatsing aan een gebruiker hen de combinatie of de som deze toestemmingen.

Uw team van Cloud Manager omvat ten minste:

* Één Bedrijfs Eigenaar, die typisch ook de Beheerder van het Systeem is en moet de eerste persoon zijn om login en tot de Manager van de Wolk toegang te hebben
* One Deployment Manager
* Eén ontwikkelaar

   >[!NOTE]
   >Om toegang te krijgen tot AEM as a Cloud Service, moeten gebruikers tot een van twee productprofielen behoren: `AEM Users` of `AEM Administrators`. U moet machtigingen aan de instantie hebben. Rechten voor het beheer van de gekoppelde Cloud Manager zijn onvoldoende.
