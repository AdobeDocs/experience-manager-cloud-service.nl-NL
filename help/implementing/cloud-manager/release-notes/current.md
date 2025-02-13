---
title: Opmerkingen bij de release voor Cloud Manager 2025.2.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de release van Cloud Manager 2025.2.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: c2a0961cae6d36d8ea3116c6e7982889257f90c8
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.2.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

Meer informatie over de release van Cloud Manager 2025.2.0 in AEM (Adobe Experience Manager) as a Cloud Service.


Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.2.0 in AEM as a Cloud Service is donderdag 13 februari 2025.

De volgende geplande release is donderdag 13 maart 2025.

## Nieuwe functies {#what-is-new}

* **Update aan de regels van de codekwaliteit.**
Vanaf donderdag 13 februari 2025 gebruikt de stap voor de kwaliteit van de Cloud Manager-code nu een bijgewerkte SonarQube-versie 9.9.5.90363.

  De bijgewerkte regels, beschikbaar voor Cloud Manager op AEM as a Cloud Service bij [ deze verbinding ](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules), bepalen veiligheidsscores en codekwaliteit voor de pijpleidingen van Cloud Manager. Deze update kan van invloed zijn op uw kwaliteitswachttijden en kan implementaties blokkeren.

* **Java 17 en Java 21 bouwt steun.**

  Klanten kunnen nu bouwen met Java 17 of Java 21, waardoor ze toegang krijgen tot prestatieverbeteringen en nieuwe taalfuncties. Voor configuratiestappen, met inbegrip van het bijwerken van uw Gemaakt project en bibliotheekversies, zie [ milieu bouwen ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Wanneer de versie voor samenstellen is ingesteld op Java 17 of Java 21, wordt Java 21 gebruikt voor de runtime.

   * **toe:laten van de Eigenschap**
      * Deze functie wordt op donderdag 13 februari 2025 voor alle klanten ingeschakeld, samen met de standaardimplementatie van de nieuwe SonarQube-versie.
      * De klanten kunnen het ** onmiddellijk toelaten door de twee hierboven beschreven variabele configuraties voor de bevordering van SonarQube 9.9 versie te plaatsen.

   * **Java 21 runtime plaatsing**
      * De Java 21-runtime wordt geïmplementeerd tijdens het bouwen met Java 17 of Java 21.
      * De geleidelijke implementatie naar alle Cloud Manager-omgevingen begint in februari voor sandboxen en ontwikkelomgevingen en loopt in april door tot productieomgevingen.
      * De klanten die met Java 11 bouwen die wensen om Java 21 runtime *vroeger goed te keuren* kunnen Adobe in [ aemcs-java-adopter@adobe.com ](mailto:aemcs-java-adopter@adobe.com) contacteren.

* **99.99% uptime rapportering voor Edge Delivery Services.**
De high-availability 99.99% uptime rapportering is nu beschikbaar voor in aanmerking komende Edge Delivery Services programma&#39;s. Om deze functie in te schakelen, moeten klanten zich met succes aan boord van hun Edge Delivery Services-sites bevinden en hun 99,99% Service level agreement (SLA) toepassen in Cloud Manager.

  Zie ook [ SLA ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla).

* **Verbeterde gebruikersuitnodiging voor Edge Delivery Services.**
Er zijn verbeteringen aangebracht in de ervaring met het uitnodigen van gebruikers naar de opslagplaats voor inhoud die is gekoppeld aan Edge Delivery Services. <!-- CMGR-65331 -->

* **automatische verwezenlijking van profielen Admin op publiceer instanties.**
Eerder stond Cloud Manager het handmatig maken van beheerprofielen toe op publicatieexemplaren, maar bood standaard geen ondersteuning voor automatisch maken. Met deze update worden nu automatisch beheerprofielen gemaakt voor publicatieexemplaren, waardoor de bruikbaarheid wordt verbeterd en de installatietijd voor klanten wordt verkort.

  Voor meer details, zie [ Toestemmingen van de Douane ](/help/implementing/cloud-manager/custom-permissions.md).

  ![ Activiteiten die van de Pijpleiding ](/help/implementing/cloud-manager/release-notes/assets/product-profiles.png) filtreren

* **Overgang aan OAuth voor milieu&#39;s van Cloud Service.**
De nieuwe milieu&#39;s van Cloud Service gebruiken nu op OAuth-Gebaseerde dienst-aan-dienst authentificatie voor de integratieprojecten van Adobe Developer Console in plaats van de eerder gebruikte JWT authentificatiemethode. JWT-authenticatie is afgekeurd en is gepland voor einde van de levensduur in juni 2025.

* **Steun voor EC (Elliptische Kromme) PrivéSleutels (secp384r1).**
Cloud Manager biedt nu ondersteuning voor `secp384r1` OV/EV SSL-certificaten (Elliptic Curve (EC)) met verbeterde beveiliging en compatibiliteit voor door klanten beheerde OV/EV SSL-certificaten.
Voor meer details, zie [ Vereisten voor klant-geleide OV/EV SSL certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md). <!-- CMGR-63636 -->

<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## Bugfixes

* **(UI) Oplossing voor een probleem dat CDN-configuratie voor domeinen in Cloud Manager verhinderde.**
Klanten die een CDN-configuratie in Cloud Manager probeerden toe te voegen, kregen een schermfout te zien wanneer zij een domein in het keuzemenu selecteerden. Deze gebruikersinterfacefout verhinderde domeinafbeelding in productiemilieu&#39;s, die het configuratieproces blokkeren.

  Bovendien bleven sommige domeinen ontoegankelijk op de achtergrond, ondanks dat ze uit de gebruikersinterface werden verwijderd. Dit probleem leidde tot conflicten met bestaande CDN-configuraties.

  Met deze correctie kunt u nu een domein selecteren in de vervolgkeuzelijst zonder dat er een fout optreedt. De inconsistenties van de steun die domeinherconfiguratie verhinderde zijn behandeld. En tenslotte, zorgt de verbeterde bevestiging nu ervoor dat de conflicterende domeinen behoorlijk worden verwijderd alvorens hen opnieuw toe te voegen.<!-- CMGR-64888 -->
* **(Backend) Probleem opgelost waarbij SSL-vervalberichten meerdere keren werden verzonden.**
Een fout werd geïdentificeerd waar de SSL planner van het vervalsingsbericht, die wordt ontworpen om één keer per dag om middernacht te lopen, verkeerd tweemaal per dag-eens om middernacht en opnieuw om 12:30 AM teweegbracht. Deze kwestie resulteerde in veelvoudige overtollige berichten die met betrekking tot het verlopen SSL certificaten worden verzonden.

  De berichtplanner loopt nu correct slechts eenmaal per dag zoals bedoeld. En u ontvangt niet langer dubbele SSL-vervalberichten. <!-- CMGR-64748 -->




<!-- ## Known issues {#known-issues} -->
