---
title: Opmerkingen bij de release voor Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de release van Cloud Manager 2025.1.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 613a5602706d4d0d63fce7a20bf52660d9a9d335
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

Meer informatie over de release van Cloud Manager 2025.1.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.1.0 in AEM as a Cloud Service is woensdag 22 januari 2025.

De volgende geplande release is donderdag 13 februari 2025.


## Nieuwe functies {#what-is-new}

* **de kwaliteitsregels van de Code - de Verbetering van de Server SonarQube:** de stap van de Kwaliteit van de Code van Cloud Manager zal beginnen SonarQube Server 9.9 met de versie van Cloud Manager 2025.2.0 te gebruiken, die voor Donderdag, 13 februari, 2025 wordt gepland.

  Om voor te bereiden, zijn de bijgewerkte regels SonarQube nu beschikbaar bij [ Regels van de Kwaliteit van de Code ](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules).

  U kunt de nieuwe regels &quot;vroege controle&quot;door de volgende variabele van de pijpleidingstekst te plaatsen:

  `CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

  Stel bovendien de volgende variabele in om ervoor te zorgen dat de stap voor de codekwaliteit wordt uitgevoerd voor dezelfde commit (wordt normaal gesproken overgeslagen voor dezelfde `commitId`):

  `CM_DISABLE_BUILD_REUSE` = `true`

![ pagina van de Configuratie van Variabelen ](/help/implementing/cloud-manager/release-notes/assets/variables-config.png)

>[!NOTE]
>
>De Adobe adviseert het creëren van een nieuwe pijpleiding van de Kwaliteit van CI/CD Code, die aan de zelfde tak wordt gevormd zoals uw belangrijkste productiepijplijn. Plaats de aangewezen variabelen *vóór* 13 februari, versie 2025 om te bevestigen dat de nieuwe gedwongen regels geen blockers introduceren.

* **Java 17 en Java 21 bouwt steun:** de klanten kunnen nu met Java 17 of Java 21 bouwen, die toegang tot prestatiesverhogingen en nieuwe taaleigenschappen krijgen. Voor configuratiestappen, met inbegrip van het bijwerken van uw Gemaakt project en bibliotheekversies, zie [ milieu bouwen ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Wanneer de versie voor samenstellen is ingesteld op Java 17 of Java 21, wordt Java 21 gebruikt voor de runtime.

   * **toe:laten van de Eigenschap**
      * Deze functie wordt op donderdag 13 februari 2025 voor alle klanten ingeschakeld, samen met de standaardimplementatie van de nieuwe SonarQube-versie.
      * De klanten kunnen het ** onmiddellijk toelaten door de twee hierboven beschreven variabele configuraties voor de bevordering van SonarQube 9.9 versie te plaatsen.

   * **Java 21 runtime plaatsing**
      * De Java 21-runtime wordt geïmplementeerd tijdens het bouwen met Java 17 of Java 21.
      * De geleidelijke implementatie naar alle Cloud Manager-omgevingen begint in februari voor sandboxen en ontwikkelomgevingen en loopt in april door tot productieomgevingen.
      * De klanten die met Java 11 bouwen die wensen om Java 21 runtime *vroeger goed te keuren* kunnen Adobe in [ aemcs-java-adopter@adobe.com ](mailto:aemcs-java-adopter@adobe.com) contacteren.

* **&quot;CDN Configurations&quot;anders genoemd aan &quot;Toewijzingen van het Domein&quot;:** als deel van gebruikersinterfaceverbeteringen in AEM Cloud Manager, wordt het etiket &quot;Configuraties CDN&quot;nu anders genoemd aan &quot;Toewijzingen van het Domein.&quot; Door deze wijziging wordt de terminologie beter afgestemd op de functionaliteit. <!-- CMGR-64738 -->

  ![ &quot;CDN Configurations&quot;anders genoemd aan &quot;Toewijzingen van het Domein&quot;in het gebruikersinterface ](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)

* **Voorziening een Plaats van Edge Delivery met één klik:** Cloud Manager laat nu gebruikers met de aangewezen toestemmingen en de vergunningen toe om een plaats van Edge Delivery Services van de steekproef met enkel één enkele klik tot stand te brengen. Dit gestroomlijnde proces biedt de volgende geautomatiseerde functies:

   * **Integratie GitHub** - leidt automatisch tot een bewaarplaats GitHub binnen een bestaande organisatie, pre-gevormd met een boilerplate malplaatje voor Edge Delivery Services.
   * **AEM de Installatie van de Toepassing van de Synchronisatie van de Code van de Synchronisatie van de Code** - installeert de toepassing van de Synchronisatie van de AEM op de bewaarplaats, die naadloze synchronisatie en plaatsing verzekert.
   * **de Opstelling van Collaboration van de Inhoud** - Verbindt een aangewezen omslag van de Aandrijving van Google voor inhoudsopslag, die een samenwerkingsmilieu voor inhoudsbeheer verstrekken.
   * **Inhoud het Publiceren** - de gebruikers kunnen inhoud voor provisioned plaatsen nu direct van het gebruikersinterface van Cloud Manager publiceren, die werkschema&#39;s vereenvoudigen en efficiency verbeteren.
   * **Verbeterde Collaboration** - het platform staat gebruikers toe om veelvoudige medewerkers aan de omslag van de de inhoudsopslag van de Aandrijving van Google toe te voegen, die teamwerk en inhoudsbijdragen vergemakkelijkt.

  Deze verbeteringen zijn bedoeld om de automatisering te verbeteren, installatieprocessen te vereenvoudigen en de samenwerking voor gebruikers van Edge Delivery Services te verbeteren. <!-- CMGR-59362 -->

  ![ Levering een Plaats van Edge Delivery ](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

  ![ de plaatsdialoog van Edge Delivery van de Levering ](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)

* **Verbeterde steun voor Edge Delivery Services plaatsen:** Cloud Manager steunt nu onboarding voor de recentste Edge Delivery Services plaatsen. Deze update omvat een uitvoerige refactoring van CDN en leveringsstapel, resulterend in betere robuustheid en onderhoudsbaarheid.

* **Geavanceerde het filtreren opties voor pijpleidingen:** Cloud Manager kenmerkt nu geavanceerde het filtreren opties op de pagina van Pijpleidingen, die u tot relevante gegevens laat snel toegang hebben en plaatsingsefficiency verbetert. Enkele van de belangrijkste functies zijn:

   * **het Filtreren van meerdere criteria:** verfijnen onderzoeksresultaten met filters zoals pijpleidingsnaam, milieu, en voeren code op.
   * **Gestroomlijnd Onderzoek van de Pijpleiding:** bepaal gemakkelijk van specifieke pijpleidingen voor snellere navigatie en beter werkschemabeheer de plaats.

  Al met al maken deze verbeteringen het beheren en implementeren van pijpleidingen efficiënter en gebruiksvriendelijker.

  ![ eigenschap van de de filters van de Pijpleiding ](/help/implementing/cloud-manager/release-notes/assets/pipeline-filters.png)

* **Zelfbediening CDN Configuratie voor de Dienst van Edge Delivery:** De nieuwe adopters van de Dienst van Edge Delivery kunnen hun CDN door Cloud Manager nu onafhankelijk vormen. Deze update breidt de ondersteuning uit van `.hlx.page/live` naar de nieuwe `.aem.page/live` , waardoor gebruikers meer flexibiliteit en gestroomlijnde installatie krijgen.

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Maak deel uit van het Cloud Manager-programma voor vroege adoptie en heb de kans om toekomstige functies te testen.

* **Vroege het programmaupdate van de Goedkeuringsarts - de bevestigingssteun van PR voor Bitbucket en GitLab:** Cloud Manager steunt nu de bevestiging van het Verzoek van de Trek (PR) voor zowel Cloud als zelf-ontvangen versies van Bitbucket en GitLab. Met deze functie kunnen klanten hun codewijzigingen testen op basis van de kwaliteitsdrempels voor code van de Adobe voordat ze een PR samenvoegen. Door te zorgen voor een hogere codekwaliteit voordat de code wordt samengevoegd, verbetert deze verbetering het succespercentage van codewijzigingen in productiepijpleidingen aanzienlijk, waardoor de tijd tot aan de markt wordt verkort en de ontwikkelingsworkflows worden gestroomlijnd.

  Voor meer informatie over &quot;breng Uw Eigen Git&quot;- nu met steun voor GitLab en Bitbucket - en om omhoog als Vroege Inschrijver te ondertekenen, zie [ de Nota&#39;s van de Versie van Cloud Manager Oktober 2024 ](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md##gitlab-bitbucket).

* **Geavanceerde Milieu van de Test:** een doel-gebouwde oplossing die wordt ontworpen om het hiaat tussen ontwikkeling en productie te overbruggen. Deze omgeving is toegesneden op de behoeften van de onderneming en bevat productieniveau-specificaties ter ondersteuning van nauwkeurige gebruikersacceptatietests (UAT) en grondige prestatiebeoordelingen.

  Als u in het zich aansluiten bij het Vroege programma van de Goedkeuring geinteresseerd bent, gelieve [ deze vorm ](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Furldefense.com%2Fv3%2F__https%3A%2Fwww.feedbackprogram.adobe.com%2Fh%2Fs%2F6N425LYG1jQ1Nc0F20Zllt__%3B!!OgNkHJCYlf_CHg!fIp-QrZ9si3kcUIjRCniEzqAAa8FcU1iN34SGQFtlcQ36eUQXOZWbDHP7oZajqddgpuOVMAVD L5CQpkZ6ths76Qks8%24&amp;data=05%7C02%7Cpanchapa%40adobe.com%7Cf81bcaa4b20544f1818b08dcd07c78c c%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638610680502164019%7CUnknown%7CU FpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6IK1haWwiLCJXVCI6Mn0%7C0%7C%7C%7C &amp;sdata=aGo6zz2ldPrta4lpvo3CLNENR5ghHDDCPbG1adUaNZQ%3D&amp;reserved=0) te voltooien en een e-mail naar [ earlyadopter_cs_advtestenvironment@adobe.com ](mailto:earlyadopter_cs_advtestenvironment@adobe.com) met uw `OrgID` te verzenden.



<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
