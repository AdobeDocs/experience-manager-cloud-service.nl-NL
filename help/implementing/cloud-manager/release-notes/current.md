---
title: Opmerkingen bij de release voor Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de release van Cloud Manager 2025.1.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: f6c1aa32647bcabeb0781973f81b75c11edc6a5d
workflow-type: tm+mt
source-wordcount: '412'
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

* **&quot;CDN Configurations&quot;anders genoemd aan &quot;Toewijzingen van het Domein&quot;:** als deel van gebruikersinterfaceverbeteringen in AEM Cloud Manager, wordt het etiket &quot;Configuraties CDN&quot;nu anders genoemd aan &quot;Toewijzingen van het Domein&quot;voor betere terminologiegroepering met functionaliteit. <!-- CMGR-64738 -->

  ![ &quot;CDN Configurations&quot;anders genoemd aan &quot;Toewijzingen van het Domein&quot;in het gebruikersinterface ](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)


<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->

<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
