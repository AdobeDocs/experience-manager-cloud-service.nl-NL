---
title: Ondersteuning voor Edge Delivery Services in Cloud Manager
description: Leer hoe u Cloud Manager-projecten kunt leveren met behulp van Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4e887b753eaf09e104c68484792f00dcb08ee304
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 0%

---

# Ondersteuning voor Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Leer hoe u uw licentie voor Edge Delivery Services gebruikt om een site voor Edge Delivery Services te maken.

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->

## Edge Delivery Services in het kort {#edge-overview}

Edge Delivery Services is een samenstellbare set services die u in staat stelt om op zeer flexibele wijze inhoud op uw website te schrijven. Op deze manier kunt u het volgende doen:

* Maak snelle sites met een perfecte Lighthouse Score.
* Bewaking van de prestaties voortdurend via RUM (Real Use Monitoring).
* Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen.

U kunt zowel AEM inhoudsbeheer als WYSIWYG-authoring gebruiken met behulp van de Universal Editor en op document gebaseerde authoring.

Met Cloud Manager in AEM as a Cloud Service kunt u Edge Delivery Service inschakelen voor uw project.

>[!TIP]
>
>Voor details over Edge Delivery Services en hoe het met AEM kan worden gebruikt, te zien gelieve het document [ overzicht van Edge Delivery Services ](/help/edge/overview.md).

## Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites vergunning hebt gegeven, kunt u aan boord uw plaats met Edge Delivery Services direct in Cloud Manager en gaan levend [ gebruikend een geleide, zelfbediening ervaring ](/help/implementing/cloud-manager/managing-code/private-repositories.md).

Bovendien kunt u tot een verenigde ervaring toegang hebben voor het beheren van al uw AEM eigenschappen terwijl het verzekeren van consistentie over zeer belangrijke werkschema&#39;s. Dit zijn domeinnaambeheer, SSL-certificaatbeheer en CDN-toewijzingen.

## Edge Delivery Services toevoegen aan een productie- of sandboxprogramma

Om programma&#39;s toe te voegen of uit te geven, moet u een lid van de **rol van de Bedrijfs Eigenaar {zijn 0} of toestemming worden gegeven om dit te doen.**
Uw organisatie moet een licentie voor ongebruikte Edge Delivery Services hebben voordat deze kan worden toegepast op een productieprogramma.

>[!NOTE]
>
>Zodra de vergunning van Edge Delivery Services wordt toegepast op of uit een programma verwijderd, wordt de verandering onmiddellijk van kracht zonder de behoefte om een pijpleiding in werking te stellen. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

Voer afhankelijk van uw gebruiksgeval een van de volgende handelingen uit:

| Hoofdletters gebruiken | Beschrijving |
| --- | --- |
| Ik wil Edge Delivery Services toevoegen aan een nieuw productieprogramma. | Zie [ productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.<br> in de tovenaar, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil Edge Delivery Services toevoegen aan een bestaand productieprogramma. | Zie [ programma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) uitgeven.<br> in **geef de dialoogdoos van het Programma** uit, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil Edge Delivery Services toevoegen aan een nieuw of bestaand sandboxprogramma. | Zie [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) creëren.<br> wanneer u een zandbakprogramma creeert, worden de Edge Delivery Services toegevoegd aan het programma door gebrek; u te hoeven niet om het te selecteren.<br> Bestaande zandbakprogramma&#39;s erven automatisch Edge Delivery Services. |

## Adobe aanbevolen pad voor gecontracteerde klanten {#recommended-path-eds}

Als gecontracteerde klant kunt u ervoor zorgen dat u optimaal profiteert van de Adobe door toegang te krijgen tot uw licentie voor Edge Delivery Services en deze te verbruiken via Cloud Manager. Deze benadering laat u [ beheerde Adobe gebruiken CDN ](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) en uit zeer belangrijke voordelen zoals zelfbediening CDN beheer, met inbegrip van de configuratie en de installatie van DV of EV/OV certificaten voordeel halen. Als u geen Edge Delivery Services vergunning met Adobe hebt en besluit om die voordelen over te slaan, kunt u een klant-beheerde CDN slechts gebruiken. Deze opstelling moet op het platform aem.live zijn.

Als u een contract hebt met licenties voor AEM as a Cloud Service Sites-Edge Delivery Services, meldt u zich aan bij Cloud Manager om ervoor te zorgen dat u het volgende kunt doen:

* Gebruik uw licentie voor uw gekozen programma.
* Haal voordeel uit [ API-eerste ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) voordelen voor het uitvoeren van (creeer, Gelezen, Update, Schrapping) verrichtingen CRUD.
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* Toegang SLA die (*binnenkort komt*) <!-- ADD LINK TO IT WHEN FINALLY ADDED --> meldt
* Ondersteuning voor Adobe. Zorg ervoor dat de sites van uw Edge Delivery Services zijn geregistreerd via een productieprogramma in Cloud Manager voor een correcte herkenning en ondersteuning door de Adobe.

## Een site voor Edge Delivery Services toevoegen {#eds-add-site}

Nadat u Edge Delivery Services aan een productieprogramma hebt toegevoegd, wordt uw licentie voor Edge Delivery Services erop toegepast.

Een nieuw, klikbaar lusje genoemd **Edge Delivery** wordt gezien op de pagina van het Overzicht. Als u op het tabblad klikt, wordt een tabel weergegeven met elke Edge Delivery-site die u hebt toegevoegd. In het linkernavigatievenster, onder de **Diensten** groepering, zult u een menuoptie genoemd **plaatsen van Edge Delivery** opmerken.

![ pagina van het Overzicht die de Plaatsen van Edge Delivery in linkernavigatievenster en het lusje van Edge Delivery rechts van het lusje van de Levering van Publish tonen ](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**om een plaats van Edge Delivery toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:
   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Dan, dichtbij de laag-juiste hoek van de pagina, klik **toevoegen de plaats van Edge Delivery**.

     ![ voeg de Plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

     De **Edge Delivery om lijst**, zoals die in het beeld hierboven wordt gezien te doen, is een facultatieve controlelijstgids aan boord die wordt bedoeld om u te helpen met het gebruiken van Edge Delivery beginnen. Zie [ Ongeveer Edge Delivery lijst ](#ed-todo-list) te doen.

   * Klik in de linkerbovenhoek van de pagina op het hamburgerpictogram om het linkernavigatiemenu weer te geven. Onder de **rubriek van de Diensten**, klik **de Plaatsen van Edge Delivery**. Vlak de hoger-juiste hoek van de pagina, klik **plaats** toevoegen.

     ![ voeg de Plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. In **voeg de plaats van Edge Delivery** dialoogdoos toe, doe het volgende:

   | Tekstveld | Wat moet u doen? |
   | --- | --- |
   | Sitenaam | Voer de naam in van de Edge Delivery-site die u toevoegt. De naam fungeert als een unieke id voor de site in Cloud Manager. |
   | URL opslagplaats | Dit veld verwijst naar de Git-opslagplaats waar de code van uw website is opgeslagen.<br> ga URL van de bewaarplaats van het Git in die de noodzakelijke dossiers en middelen (zoals HTML, CSS, JavaScript, en andere Webactiva) voor uw plaats van Edge Delivery bevat. Op deze manier kan Cloud Manager tijdens het implementatieproces de code uit die opslagplaats ophalen. |
   | Sitebeschrijving (optioneel) | Voer een korte beschrijving in van de Edge Delivery-site die u toevoegt.<br> Deze beschrijving helpt om de plaats te identificeren en te onderscheiden, die het gemakkelijker maken om onder andere plaatsen te beheren en te erkennen u hebt toegevoegd. U kunt desgewenst details opnemen over het doel, de inhoud of andere relevante informatie van de site die de functie of het bereik van de site kan verduidelijken. |

1. In de laag-juiste hoek van de dialoogdoos, voegt de klik **** toe.

1. In **verifieer bezit van de bewaarplaats** dialoogdoos, doe elk van het volgende:

   | Stap | Beschrijving |
   | --- | --- |
   | 1 | Voeg een dossier met de plaatsweg aan de `main` tak van de bewaarplaats van het Git toe die in het **Repository URL** gebied van de Bewaarplaats vermeld is. Klik zo nodig op het pictogram Kopiëren om het pad naar het klembord te kopiëren.<br> Het locatiepad is:<br>`well-known/adobe/cloudmanager-challenge.txt`.<br><br> voeg *niet* een periode bij het begin van de plaatsweg toe, is binnen:<br>`.well-known/adobe/cloudmanager-challenge.txt` |
   | 2 | Voeg de gegenereerde code toe aan het bestand dat u in Stap 1 hebt gemaakt. Klik zo nodig op het pictogram Kopiëren om de code naar het klembord te kopiëren. |
   | 3 | Maak in de Git-opslagplaats een pull-aanvraag en voeg deze samen om de code vast te leggen. |

1. Klik **verifieer**. Nadat de opslagplaats is geverifieerd, verandert de status in de tabel Edge Deliver Sites in een groene cirkel met daarin een wit vinkje.

## De Edge Delivery-lijst met taken {#ed-todo-list}

De **Edge Delivery om lijst** te doen is een onboarding taak controlelijst die wordt bedoeld om u door onboarding te begeleiden, uw plaats van Edge Delivery te beheren al manier aan [ gaan-Levend ](/help/journey-onboarding/go-live-checklist.md).

|  | Taak | Beschrijving |
| --- | --- | --- |
| 1 | Deelnemen aan het samenwerkingskanaal voor producten | Het klikken **legt nu verzoek voor** legt een verzoek aan Adobe voor om een kanaal voor uw bedrijf tot stand te brengen. Als het kanaal reeds bestaat, door:sturen u aan het kanaal van uw bedrijf. |
| 2 | Volledige voorwaarden | Het klikken van **Mening die Begonnen leerprogramma** krijgt, leidt u aan [ Begonnen het worden - Leerprogramma van de Ontwikkelaar ](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-site toevoegen | Zie [ een plaats van Edge Delivery ](#eds-add-site) toevoegen. |
| 4 | Domein toevoegen | Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |
| 5 | SSL-certificaat toevoegen | Zie [ SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
| 6 | De CDN van uw Edge Delivery-site configureren | Zie [ een configuratie CDN ](#add-cdn) toevoegen. |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on) (2 minuten, 13 seconden)

## Een CDN-configuratie toevoegen aan uw Edge Delivery-site {#add-cdn}

Zie [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen.

## Een Edge Delivery-site verwijderen {#eds-site-delete}

>[!IMPORTANT]
>
>Als u een plaats van Edge Delivery Services schrapt, worden om het even welke bijbehorende configuraties CDN ook verwijderd. Met deze actie wordt de verbinding tussen aangepaste domeinen en de site verbroken. Zie CDN-configuraties voor meer informatie. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**om een plaats van Edge Delivery te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:
   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de site wilt verwijderen. Klik **Schrapping**, dan klik **Schrapping** opnieuw om de verwijdering van de plaats te bevestigen.

     ![ voeg de Plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klik in de linkerbovenhoek van de pagina op het hamburgerpictogram om het linkernavigatiemenu weer te geven. Onder de **rubriek van de Diensten**, klik **de Plaatsen van Edge Delivery**. Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de site wilt verwijderen. Klik **Schrapping**, dan klik **Schrapping** opnieuw om de verwijdering van de plaats te bevestigen.


     ![ voeg de Plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)


<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
