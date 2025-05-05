---
title: Inleiding tot Cloud Manager
description: Leer hoe Cloud Manager uw AEM project ondersteunt via programma's, omgevingen en pijpleidingen.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---


# Inleiding tot Cloud Manager {#intro-cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één toegangspunt voor uw team. De speciaal gebouwde CI/CD-pijpleidingen zijn uitgerust om grondig te testen en de hoogste codekwaliteit te verzekeren om uitzonderlijke ervaringen te bieden. Om ervoor te zorgen dat klanten snel met hun projecten kunnen beginnen, biedt Cloud Manager alles wat nodig is op een zelfbediening manier, zoals de mogelijkheid om cloudbronnen en -omgevingen te maken en toegang te krijgen tot uw git-opslagruimten. Deze functies ondersteunen instellingen voor bedrijfsontwikkeling, zodat teams regelmatig wijzigingen kunnen doorvoeren, snel uitzonderlijke digitale ervaringen kunnen opdoen en tijd-naar-waarde kunnen versnellen.

Uw systeembeheerder is verantwoordelijk voor het instellen van uw Cloud Manager-team, dat personen zal omvatten die uw cloudbronnen en -ontwikkelaars zullen maken. Voor meer informatie over hoe te opstelling en schaal uw team van de ondernemingsontwikkeling en zie hoe AEM as a Cloud Service uw ontwikkelingsproces kan steunen, zie {de Opstelling van de Ontwikkeling van het Team van 0} Onderneming voor AEM as a Cloud Service [&#128279;](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md).

## Navigeren naar overzichtspagina van Cloud Manager {#navigate-cloud-manager}

Ga als volgt te werk om naar Cloud Manager te navigeren.

1. Navigeer naar de Cloud Manager-aanmeldingspagina op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com/) .

1. Selecteer het programma van Cloud Manager **Programma&#39;s en Producten** pagina om de **pagina van het Overzicht** te lanceren.

U kunt ook vanuit de startpagina van Adobe Experience Cloud naar de pagina Cloud Manager-programma&#39;s en -producten navigeren door deze stappen te volgen.

1. Navigeer naar Adobe Experience Cloud op [`https://experience.adobe.com` ](https://experience.adobe.com) en meld u aan met uw Adobe ID.

1. Zorg ervoor dat u zich in de juiste organisatie bevindt door te verwijzen naar de naam van de organisatie die rechtsboven op de werkbalk wordt weergegeven.

1. Selecteer **Experience Manager**.

1. Op **Cloud Manager** kaart, klik **Lancering**

## Op rollen gebaseerde machtigingen in Cloud Manager {#role-based-permissions}

| Machtiging | Beschrijving | Business Owner | Deployment Manager | Program Manager | Developer |
|--- |--- |--- |--- |--- |--- |
| Voeg Programma <br> toe geeft Programma uit | Voeg een Nieuw Programma <br> toe of verwijder oplossingen of toe:voegen-ons | x |  |  |  |
| Omgeving maken | Productie- en staging- en ontwikkelomgevingen creëren | x | x |  |  |
| Omgeving bijwerken | Productie- en ontwikkelomgevingen bijwerken | x | x |  |  |
| Dev-omgeving verwijderen | Ontwikkelomgevingen verwijderen | x | x |  |  |
| Instellingen pijpleiding | Pijpleidingen instellen en bewerken |  | x |  |  |
| Uitvoering pijpleiding | Pijpleidingen starten | x | x |  |  |
| Uitvoering pijpleiding | Belangrijke gate-fouten met drie lagen afwijzen/goedkeuren | x | x | x |  |
| Uitvoering pijpleiding | Live goedkeuring opgeven | x | x | x |  |
| Uitvoering pijpleiding | Implementaties voor productieplanning | x | x | x |  |
| Pipet verwijderen | Verwijderen van pijpleiding toestaan |  | x |  |  |
| Uitvoering annuleren | Huidige uitvoering annuleren |  | x |  |  |
| Token voor persoonlijke toegang genereren | Toegangsuitrusting |  | x |  | x |
| RDE maken | Een snelle ontwikkelomgeving maken | x |  |  | x |
| RDE opnieuw instellen | Een snelle ontwikkelomgeving opnieuw instellen | x |  |  | x |
| Inhoudssets maken/wijzigen | Een inhoudset maken of wijzigen voor het kopiëren van inhoud |  | x |  |  |
| Kopie van inhoud starten/annuleren | Een proces voor het kopiëren van inhoud starten of annuleren |  | x |  |  |

>[!NOTE]
>
>Een gebruiker kan aan veelvoudige rollen worden toegewezen. Bijvoorbeeld, geeft de toewijzing van zowel **BedrijfsEigenaar** als **de rollen van de Manager van de Plaatsing** aan een gebruiker de som deze toestemmingen.

>[!TIP]
>
>Aangepaste machtigingsprofielen met configureerbare machtigingen zijn ook beschikbaar. Gelieve te zien de toestemmingen van de Douane van het document [&#128279;](/help/implementing/cloud-manager/custom-permissions.md) voor meer details.

## Cloud Manager-programma&#39;s {#cloud-manager-programs}

Cloud Manager-programma&#39;s zijn een reeks Cloud Manager-omgevingen die ondersteuning bieden voor logische groepen bedrijfsinitiatieven. Deze groepen komen meestal overeen met een aangeschafte Service level agreement (SLA). Bijvoorbeeld, kan één programma de AEM middelen vertegenwoordigen om de openbare Website van een organisatie te steunen, terwijl een ander programma interne DAM vertegenwoordigt.


Bekijk deze [ video ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) om meer te leren bij het gebruiken van de programma&#39;s van Cloud Manager.

Een gebruiker kan a **zandbak** of a **productie** programma tot stand brengen.

* A **productieprogramma** wordt gecreeerd om levend verkeer op de aangewezen tijd in de toekomst toe te laten.
   * Zie [ Inleiding aan de Programma&#39;s van de Productie ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer details.

* A **zandbakprogramma** wordt typisch gecreeerd om de doeleinden van opleiding, lopende demo&#39;s, activering, creërend POCs, of voor documentatie te dienen.
   * Het is niet de bedoeling om levend verkeer te vervoeren en zal beperkingen hebben die een productieprogramma niet zal hebben.
   * Het omvat Plaatsen en Assets en wordt geleverd automatisch bevolkt met een git tak die steekproefcode, een ontwikkelomgeving, en een niet productiepijplijn omvat.
   * Zie [ Inleiding aan Programma&#39;s Sandbox ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) voor meer details.

## Cloud Manager Environment {#cloud-manager-environments}

Uw cloudomgevingen worden gemaakt, geopend en weergegeven via Cloud Manager. Deze omgevingen kunnen productie-, staging- of ontwikkelomgevingen zijn. Verschillende omgevingen hebben verschillende doeleinden en kunnen worden gebruikt met verschillende CI-/CD-leidingen. De milieu&#39;s bestaan uit diensten zoals:

* [AEM Authoring](#author-services)
* [AEM Publishing Services](#publish-services)
* [Dispatcher Services](#dispatcher-services)

>[!TIP]
>
> Zie de video [ Gebruikend de Milieu&#39;s van Cloud Manager van de Adobe ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) een overzicht van de beschikbare milieu&#39;s.
>
>Zie [ Milieu&#39;s ](/help/implementing/cloud-manager/manage-environments.md) beheren om meer over types van milieu te leren een gebruiker kan creëren en hoe de gebruiker een milieu kan creëren.

### AEM Authoring {#author-services}

Een AEM-ontwerpservice is inbegrepen in omgevingen waar site-inhoud en digitale middelen worden gemaakt, beheerd en bijgewerkt. Doorgaans hebben alleen interne gebruikers toegang tot de ontwerpservice en wordt deze achter een aanmeldingsscherm onderhouden. De ontwerpservice fungeert als zowel een ontwerpomgeving als een voorvertoningsomgeving.

### AEM Publishing Service {#publish-services}

Een AEM publicatieservice is inbegrepen in omgevingen waarin de ervaring van eindgebruikers wordt ondergebracht, zoals op websites. Dit is de service waarmee bezoekers van de site de site kunnen bekijken en communiceren. Doorgaans is de publicatieservice openbaar beschikbaar.

### AEM Dispatcher Service {#dispatcher-services}

De verzender is een `Apache HTTP Web server` -module die een beveiligings- en prestatielaag biedt die zich vóór de AEM publicatieservice bevindt.
