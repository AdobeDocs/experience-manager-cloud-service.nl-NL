---
title: Meer informatie over Cloud Manager
description: Volg deze pagina voor meer informatie over Cloud Manager, Cloud Manager-programma's en omgevingen.
source-git-commit: 185a933e12ad81689168ad88574019ed219db06d
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Inleiding tot Cloud Manager {#intro-cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM als Cloud Service en fungeert als één ingangspunt voor uw team.

Om klanten met de montages van de ondernemingsontwikkeling te steunen, AEM als Cloud Service volledig integreert met de Manager van de Wolk en zijn doel-gebouwde CI/CD pijpleidingen, die worden uitgerust om grondige tests en hoogste codekwaliteit te verzekeren om uitzonderlijke ervaringen te leveren.

Om ervoor te zorgen dat klanten snel kunnen beginnen met AEM als Cloud Service, biedt Cloud Manager alles wat nodig is om op een zelfbedieningsmanier aan de slag te gaan, inclusief de mogelijkheid om cloudbronnen en -omgevingen te maken. Op deze manier hebben uw AEM ontwikkelaars via Cloud Manager toegang tot de gegevensopslagruimte voor it. Met behulp van Cloud Manager kunnen ontwikkelingsteams ervoor zorgen dat wijzigingen vaak zelf worden uitgevoerd.

Uw systeembeheerder zal verantwoordelijk zijn voor het instellen van uw team van Cloud Manager, dat personen zal omvatten die uw cloudbronnen en -ontwikkelaars zullen maken. Raadpleeg [Enterprise Team Development Setup voor AEM als een Cloud Service](/help/implementing/cloud-manager/enterprise-team-dev-setup.md) om te leren hoe Cloud Manager ondersteuning biedt in Enterprise Team Development Setup.

## Cloud Manager-programma&#39;s {#cloud-manager-programs}

Cloud Manager-programma&#39;s zijn een reeks Cloud Manager-omgevingen die logische reeksen bedrijfsinitiatieven ondersteunen, die doorgaans overeenkomen met een aangeschafte Service Level Agreement (SLA). Bijvoorbeeld, kan één Programma de AEM middelen vertegenwoordigen om de globale openbare Websites te steunen, terwijl een ander Programma een interne Centrale DAM vertegenwoordigt. Bekijk deze [video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en) voor meer informatie over het gebruik van Cloud Manager-programma&#39;s.

Een gebruiker kan een **Sandbox** of een **Production** programma tot stand brengen.

* Een *Productieprogramma* wordt gecreeerd om levend verkeer op het aangewezen tijdstip in de toekomst toe te laten.
Raadpleeg [Inleiding tot productieprogramma&#39;s](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer informatie.

* Een *Sandbox-programma* wordt doorgaans gemaakt voor trainingsdoeleinden, het uitvoeren van demo&#39;s, activering, concepttest of documentatie. Het is niet de bedoeling om levend verkeer te vervoeren en zal beperkingen hebben die een productieprogramma niet zal hebben. Het zal Plaatsen en Activa omvatten en zal met een tak van het Git worden geleverd die steekproefcode, een Dev milieu, en een niet productiepijplijn omvat.
Raadpleeg [Inleiding tot Sandbox-programma&#39;s](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) voor meer informatie.

## Cloud Manager-omgevingen {#cloud-manager-environments}

Uw cloudomgevingen worden gemaakt, geopend en weergegeven via Cloud Manager. Dit kan een productieomgeving, een werkgebiedomgeving of een ontwikkelomgeving zijn. Verschillende omgevingen ondersteunen verschillende doeleinden en kunnen worden gebruikt met behulp van verschillende CI-/CD-leidingen. De milieu&#39;s bestaan uit diensten zoals:

* [AEM Author Services](#author-services)
* [AEM-publicatieservices](#publish-services)
* [Verzendservices](#dispatcher-services)

   >[!NOTE]
   > Raadpleeg de video [Adobe Cloud Manager-omgevingen gebruiken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager) voor meer informatie over de beschikbare omgevingen. Zie [Omgevingen beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en) voor meer informatie over de typen omgeving die een gebruiker kan maken en over de manier waarop de gebruiker een omgeving kan maken.

### AEM-auteurservice {#author-services}

AEM Author Service is inbegrepen in een omgeving waar site-inhoud en digitale middelen worden gemaakt, beheerd en bijgewerkt. Doorgaans hebben alleen interne gebruikers toegang tot de Auteur-service en bevinden deze zich achter een aanmeldingsscherm. De ontwerpservice is ontworpen als een ontwikkelings- en voorvertoningsomgeving.

### AEM-publicatieservice {#publish-services}

De AEM-publicatieservice is inbegrepen in een omgeving die fungeert als host voor de gebruikerservaring, zoals een website. Dit is de service waarmee bezoekers van de site de site kunnen bekijken en communiceren. De publicatieservice is doorgaans openbaar beschikbaar.

### AEM Dispatcher Service {#dispatcher-services}

De verzender is een `Apache HTTP Web server` module die een veiligheid en prestatieslaag verstrekt die vóór de Dienst van de Publicatie AEM zit.