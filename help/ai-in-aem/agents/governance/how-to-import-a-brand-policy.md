---
title: Hoe een merkbeleid importeren
description: Adobe Governance Agent gebruiken om een Brand Policy te importeren
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 94d671ebbd5aeb5992fdbc9d779ffbca51f82585
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 0%

---


# Hoe te om een Beleid van het Merk in te voeren {#how-to-import-a-brand-policy}

## Overzicht {#overview}

Een merkbeleid definieert de regels, normen en beperkingen die ervoor zorgen dat alle inhoud die door Adobe Experience Manager wordt geproduceerd of bijgewerkt, consistent blijft met de merkidentiteit van een bedrijf. Dit omvat gewoonlijk de toon van stem, terminologie, visuele richtlijnen, en redactionele regels.

De agent van de Governance gebruikt merkbeleid als bron van waarheid om bestaande pagina&#39;s te analyseren en inhoudsgeneratie te begeleiden. De klanten kunnen hun eigen oorspronkelijk merkbeleid verstrekken, dat de Agent van de Governance automatisch in AI-leesbare beleidscontroles omzet. Deze controles worden dan gebruikt om inhoud te bevestigen en de Agent van de Productie van een betrouwbaar, afdwingbaar kader te voorzien om pagina&#39;s te produceren of bij te werken die met het merk worden gericht.

## Wat is een merkenbeleid in de bestuursagent {#what-is-a-brand-policy-in-the-governance-agent}

In de context van de Governance Agent, is een merkbeleid een gestructureerde vertegenwoordiging van uw merkregels die door AI kunnen worden begrepen en worden gehandhaafd. In plaats van klanten te verplichten om hun richtlijnen in een technisch formaat te herschrijven, keurt de Agent van de Governance merkbeleid in hun originele vorm (bijvoorbeeld, documenten, richtlijnen, of regelbeschrijvingen) goed.

Nadat het beleid is geïmporteerd, wordt het omgezet in een set AI-beleidscontroles die het volgende kunnen doen:

* Bestaande pagina&#39;s analyseren om inconsistenties tussen merken te detecteren
* Afwijkingen van de vlag van toon, terminologie of dwingende regels
* Duidelijke begeleiding bieden aan downstreamagenten
* Zorg ervoor dat gegenereerde of bijgewerkte inhoud door het ontwerp brandwerend blijft

Met deze aanpak kunnen teams hun bestaande merkdocumentatie hergebruiken en profiteren van geautomatiseerd beheer en schaalbare contentproductie.

## Hoe het Beleid van het Merk wordt gebruikt {#how-brand-policies-are-used}

Nadat een merkbeleid is geïmporteerd:

* De bestuursagent interpreteert en normaliseert het beleid in afdwingbare AI controles
* Pagina&#39;s kunnen worden geanalyseerd aan de hand van het beleid om hiaten of overtredingen vast te stellen
* De agent van de Productie gebruikt deze controles als beperkingen wanneer het produceren van of het bijwerken van inhoud
* De naleving van het merk wordt verenigbaar, herhaalbaar, en controleerbaar over plaatsen en teams


## Een merkbeleid importeren {#import-a-brand-policy}

Een merk importeren in de Governance Agent:

1. Maak een merk door een naam en een hoofddomein te geven. U kunt dit doen door op de **knoop van de Context van de Governance** op de linkernavigatie in uw huis van Experience Manager te klikken, dan druk **+ voeg merk** knoop toe, zoals hieronder getoond:

   ![&#x200B; Toevoegend een nieuw merk &#x200B;](/help/ai-in-aem/agents/governance/assets/add_brand.png){width="70%"}

1. De naam van het merk en een beschrijving instellen in het volgende venster

   ![&#x200B; noemend het merk &#x200B;](/help/ai-in-aem/agents/governance/assets/add_brand_dialogue.png){width="60%"}

1. Nieuwe merken worden gemaakt in conceptstatus. Zorg ervoor u uw pas gecreeerd merk in een Actieve status verandert, door op de kaart van uw merk te klikken, geef (potlood) in de hoogste juiste hoek van het scherm uit, plaats de **Status** aan **Actief** in het volgende venster, en klik **sparen Veranderingen**. U moet de merken toelaten door hen aan Actief te plaatsen alvorens hen te kunnen gebruiken.

   ![&#x200B; plaats de status van het merk aan Actief &#x200B;](/help/ai-in-aem/agents/governance/assets/set_brand_active.png){width="60%"}

1. Zodra het merk wordt gecreeerd, creeer een belangrijkste domein in het volgende venster door de **1&rbrace; verbinding van Domeinen &lbrace;op de linkerzijde te drukken:**

   ![&#x200B; Vormend een domein voor het merk &#x200B;](/help/ai-in-aem/agents/governance/assets/add_domain.png)

   >[!IMPORTANT]
   >
   >Net als bij nieuwe merken worden nieuwe domeinen gemaakt met de status Concept. Om dit te veranderen, ga naar uw Merk, klik op **Domeinen**, dan geef uw domein uit gebruikend het potloodpictogram en plaats zijn status aan **Actief**.

1. Nadat u het belangrijkste domein hebt gevormd, kunt u uw document van het merkbeleid door te gaan uploaden aan **Beleid** in de hogere linkerhoek van het venster, en drukkend **+ voeg de knoop van het Beleid** toe.

   ![&#x200B; Toevoegend een beleid van de kaart van het Merk &#x200B;](/help/ai-in-aem/agents/governance/assets/add_policy_treeview.png)

   >[!NOTE]
   >
   >Alternatief, kunt u beleid ook toevoegen door over te schakelen naar het **1&rbrace; lusje van Beleid &lbrace;en het drukken van** + voegt het Beleid **verbinding toe.**

1. In het volgende venster, druk op **upload PDFs** en selecteer uw document(s) van het merkbeleid in formaat PDF

   ![&#x200B; upload uw document van het merkbeleid &#x200B;](/help/ai-in-aem/agents/governance/assets/upload_brand_policy_document.png){width="70%"}

   De Governance Agent zal uw merkbeleidsrichtsnoer ontleden met natuurlijke taal, en het zal de controles uit het document halen en hen vertalen in daadwerkelijke taken. Nadat het document is verwerkt, kunt u een overzicht van de import weergeven, inclusief het aantal controles en de status van het beleid, zoals hieronder wordt getoond:

   ![&#x200B; een overzichtsvenster van de status van het merkbeleid &#x200B;](/help/ai-in-aem/agents/governance/assets/policy_status.png)

1. Zodra uw merk wordt gecreeerd, en uw beleidsdocument wordt geupload, kunt u een gedetailleerde per-merkmening krijgen door naar het **Merken** lusje te gaan, en op de kaart van een merk te klikken. Dit is de mening u voor het creëren van categorieën van controles zult willen gebruiken, door de drie punten naast een bestaande categorie te drukken, en **+ te selecteren voeg Categorie** toe, zoals aangetoond in het hieronder screenshot:

   ![&#x200B; voeg categorie &#x200B;](/help/ai-in-aem/agents/governance/assets/add_category.png) toe

   U kunt deze weergave ook gebruiken om controles te maken, te bewerken en te verwijderen, die we in de onderstaande stappen nader zullen toelichten.

1. Voor een meer korrelige mening van elke individuele controle, kunt u op het **lusje van Controles** overschakelen, en een lijst van elke individuele controle bekijken die uit uw richtsnoerdocumenten wordt gehaald. U kunt controles filteren op basis van merk of status:

   ![&#x200B; zie individuele merkcontroles &#x200B;](/help/ai-in-aem/agents/governance/assets/see_brand_checks.png)

   Bovendien, kunt u extra details op elke individuele controle bekijken door de drie punten (**te klikken...**) links van de controle, en het drukken van **details van de Mening**. Hiermee wordt een nieuw venster geopend met meer informatie over de controle:

   ![&#x200B; Bekijk individuele controledetails &#x200B;](/help/ai-in-aem/agents/governance/assets/view_check_details.png)

   U kunt controles ook schrappen door **Schrapping** van de zelfde menuplaats te drukken, of hen uit te geven door **te drukken geeft** uit:

   ![&#x200B; Uitgevend een controle &#x200B;](/help/ai-in-aem/agents/governance/assets/edit_check.png)

1. U kunt een controle manueel toevoegen door **te drukken voegt Controle** in de hogere linkerhoek van het venster van Controles toe:

   ![&#x200B; Toevoegend een controle &#x200B;](/help/ai-in-aem/agents/governance/assets/add_check.png)

   In het volgende scherm, kunt u details zoals vormen:

   * De naam van de controle
   * De regel, die in natuurlijke taal wordt beschreven
   * De categorie
   * De werkingssfeer(en) waarop het van toepassing is

   ![&#x200B; Vormend de controledetails &#x200B;](/help/ai-in-aem/agents/governance/assets/add_check_window.png)

1. Tot slot voor een lijst van domeinen en de merken zij met worden geassocieerd, kunt u de **Domeinen** tabel drukken. Met deze sectie kunt u domeinen toevoegen, verwijderen of wijzigen in uw lijst.

