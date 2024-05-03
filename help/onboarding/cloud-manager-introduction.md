---
title: Inleiding tot Cloud Manager
description: Meer informatie over hoe Cloud Manager uw AEM project ondersteunt via programma's, omgevingen en pijpleidingen.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: 6181b066742357169b67f605ac3970685537bb5e
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---


# Inleiding tot Cloud Manager {#intro-cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één ingangspunt voor uw team. De speciaal gebouwde CI/CD-pijpleidingen zijn uitgerust om grondig te testen en de hoogste codekwaliteit te verzekeren om uitzonderlijke ervaringen te bieden. Om ervoor te zorgen dat klanten hun projecten snel kunnen starten, biedt Cloud Manager alles wat vereist is op een zelfbediening manier, zoals de mogelijkheid om cloudbronnen en -omgevingen te maken en toegang te krijgen tot uw git-opslagruimten. Deze functies ondersteunen instellingen voor bedrijfsontwikkeling, zodat teams regelmatig wijzigingen kunnen doorvoeren, snel uitzonderlijke digitale ervaringen kunnen opdoen en tijd-naar-waarde kunnen versnellen.

Uw systeembeheerder is verantwoordelijk voor het instellen van uw Cloud Manager-team. Dit team omvat personen die uw cloudbronnen en -ontwikkelaars maken. Voor meer informatie over hoe te opstelling en schaal uw team van de ondernemingsontwikkeling en zie hoe AEM as a Cloud Service uw ontwikkelingsproces kan steunen, zie [Enterprise Team Development Setup voor AEM as a Cloud Service](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md).

## Navigeren naar de overzichtspagina van Cloud Manager {#navigate-cloud-manager}

Ga als volgt te werk om naar Cloud Manager te navigeren.

1. Ga naar de aanmeldingspagina van Cloud Manager op [`https://my.cloudmanager.adobe.com`.](https://my.cloudmanager.adobe.com/).

1. Selecteer het programma in Cloud Manager **Programma&#39;s en producten** pagina om de **Overzicht** pagina.

U kunt ook vanuit de startpagina van Adobe Experience Cloud naar de pagina Programma&#39;s en producten van Cloud Manager navigeren door deze stappen uit te voeren.

1. Ga naar Adobe Experience Cloud op [`https://experience.adobe.com`](https://experience.adobe.com) en aanmelden met uw Adobe ID.

1. Zorg ervoor dat u zich in de juiste organisatie bevindt door te verwijzen naar de naam van de organisatie die rechtsboven op de werkbalk wordt weergegeven.

1. Selecteren **Experience Manager**.

1. Op de **Cloud Manager** kaart, klik **Starten**

## Op rollen gebaseerde machtigingen in Cloud Manager {#role-based-permissions}

| Machtiging | Beschrijving | Business Owner | Deployment Manager | Program Manager | Developer |
|--- |--- |--- |--- |--- |--- |
| Programma toevoegen<br>Programma bewerken | Een nieuw programma toevoegen<br>Oplossingen of invoegtoepassingen toevoegen of verwijderen | x |  |  |  |
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
>Een gebruiker kan aan veelvoudige rollen worden toegewezen. Als u bijvoorbeeld beide toewijst **Zakelijke eigenaar** en **Implementatiebeheer** rollen aan een gebruiker geven de gebruiker de som deze toestemmingen.

>[!TIP]
>
>Aangepaste machtigingsprofielen met configureerbare machtigingen zijn ook beschikbaar. Zie het document [Aangepaste machtigingen](/help/implementing/cloud-manager/custom-permissions.md) voor meer informatie .

## Cloud Manager-programma&#39;s {#cloud-manager-programs}

Cloud Manager-programma&#39;s zijn een reeks omgevingen van Cloud Manager die logische groepen bedrijfsinitiatieven ondersteunen. Deze groepen komen doorgaans overeen met een aangeschafte Service Level Agreement (SLA). Bijvoorbeeld, kan één programma de AEM middelen vertegenwoordigen om de openbare Website van een organisatie te steunen, terwijl een ander programma interne DAM vertegenwoordigt.


Dit bekijken [video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) voor meer informatie over het gebruik van Cloud Manager-programma&#39;s.

Een gebruiker kan een **Sandbox** of **Productie** programma.

* A **productieprogramma** wordt gecreeerd om levend verkeer op het aangewezen tijdstip in de toekomst toe te laten.
   * Zie [Inleiding tot productieprogramma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer informatie .

* A **sandboxprogramma** wordt typisch gecreeerd ten behoeve van opleiding, lopende demo&#39;s, enablement, het creëren van POCs, of voor documentatie.
   * Het is niet de bedoeling om levend verkeer te vervoeren en zal beperkingen hebben die een productieprogramma niet zal hebben.
   * Het omvat Plaatsen en Activa en wordt geleverd automatisch bevolkt met een git tak die steekproefcode, een ontwikkelomgeving, en een niet productiepijplijn omvat.
   * Zie [Inleiding tot Sandbox-programma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) voor meer informatie .

## Cloud Manager-omgevingen {#cloud-manager-environments}

Uw cloudomgevingen worden gemaakt, geopend en weergegeven via Cloud Manager. Deze omgevingen kunnen productie-, staging- of ontwikkelomgevingen zijn. Verschillende omgevingen hebben verschillende doeleinden en kunnen worden gebruikt met verschillende CI-/CD-leidingen. De milieu&#39;s bestaan uit diensten zoals:

* [AEM Authoring](#author-services)
* [AEM Publishing Services](#publish-services)
* [Verzendservices](#dispatcher-services)

>[!TIP]
>
> De video bekijken [Adobe Cloud Manager-omgevingen gebruiken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) een overzicht van de beschikbare omgevingen.
>
>Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie over typen omgevingen die een gebruiker kan maken en over de manier waarop de gebruiker een omgeving kan maken.

### AEM Authoring {#author-services}

Een AEM-ontwerpservice is inbegrepen in omgevingen waar site-inhoud en digitale middelen worden gemaakt, beheerd en bijgewerkt. Doorgaans hebben alleen interne gebruikers toegang tot de ontwerpservice en wordt deze achter een aanmeldingsscherm onderhouden. De ontwerpservice fungeert als zowel een ontwerpomgeving als een voorvertoningsomgeving.

### AEM Publishing Service {#publish-services}

Een AEM publicatieservice is inbegrepen in omgevingen waarin de ervaring van eindgebruikers wordt ondergebracht, zoals op websites. Dit is de service waarmee bezoekers van de site de site kunnen bekijken en communiceren. Doorgaans is de publicatieservice openbaar beschikbaar.

### AEM Dispatcher Service {#dispatcher-services}

De verzender is een `Apache HTTP Web server` die een veiligheids en prestatieslaag verstrekt die vóór de AEM het publiceren dienst zit.
