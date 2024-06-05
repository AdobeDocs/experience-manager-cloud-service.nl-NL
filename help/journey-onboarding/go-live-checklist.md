---
title: Live checklist
description: Meer informatie over alle elementen die nodig zijn voor een geslaagde GoLive met AEM as a Cloud Service
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Live checklist {#Go-Live-Checklist}

Controleer deze lijst met activiteiten om ervoor te zorgen dat Go-Live probleemloos en succesvol wordt uitgevoerd.

* Voer een end-to-end productiepijplijn uit met functionele en UI-tests om een **altijd huidig** AEM productervaring. Zie de volgende bronnen.
   * [Versie-updates AEM](/help/implementing/deploying/aem-version-updates.md)
   * [Aangepaste functionele tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [UI-tests](/help/implementing/cloud-manager/ui-testing.md)
* Als u van AEM 6.5 migreert, zou u inhoud aan productie moeten migreren en ervoor zorgen dat een relevante ondergroep bij het opvoeren voor het testen beschikbaar is.
   * De beste praktijken van DevOps voor AEM impliceren dat de code zich omhoog van ontwikkeling aan het productiemilieu beweegt terwijl de inhoud zich van productiemilieu&#39;s beweegt.
* Plan een code- en inhoudstijdsperiode.
   * Zie ook de sectie [Tijdlijnen voor code en inhoud vastzetten voor migratie](#code-content-freeze)
* Voer de laatste top-up van de inhoud uit.
* Valideer de configuraties van de verzender.
   * Gebruik een lokale verzender-validator waarmee de verzender lokaal kan worden geconfigureerd, gevalideerd en gesimuleerd
      * [Stel de lokale verzendprogramma&#39;s in.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)
   * Herzie zorgvuldig de virtuele gastheerconfiguratie.
      * De eenvoudigste (en standaard) oplossing moet `ServerAlias *` in uw virtuele hostbestand in het dialoogvenster `/dispatcher/src/conf.d/available_vhostsfolder`.
         * Hierdoor kunnen de hostaliassen die door productfunctionele tests, cachevalidatie van de verzender en klonen worden gebruikt, functioneren.
      * Als `ServerAlias *` niet aanvaardbaar is, ten minste: `ServerAlias` ingangen moeten naast uw douanedomeinen worden toegestaan:
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* Vorm CDN, SSL en DNS.
   * Als u uw eigen CDN gebruikt, ga een steunkaartje in om aangewezen het verpletteren te vormen.
      * Zie de sectie [CDN van de klant wijst naar AEM Beheerde CDN](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) in de CDN-documentatie voor meer informatie.
      * Vorm SSL en DNS volgens de documentatie van uw verkoper CDN.
   * Als u geen extra CDN gebruikt, beheer SSL en DNS volgens de volgende documentatie:
      * SSL-certificaten beheren
         * [Inleiding tot het beheren van SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [SSL-certificaat beheren](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Aangepaste domeinnamen (DNS) beheren
         * Om ervoor te zorgen dat de DNS cutover geen onverwachte problemen zal introduceren, is het best om een testsubdomain tot stand te brengen om uw productieinstantie aan te sluiten alvorens u gaat-leven en een ronde van het testen van UAT doet. Dus als uw domein example.com is, kunt u een subdomein maken test.example.com en dit toepassen op productie. Tijdens het testen van de UAT van het domein zult u dingen zoals juiste verbindingsredirection, caching, en verzender configuraties willen zoeken.
         * [Inleiding tot aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Aangepaste domeinnaam beheren](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * Herinner me om TTL te bevestigen die voor uw DNS verslag wordt geplaatst.
      * TTL is de hoeveelheid tijd een DNS verslag in een geheim voorgeheugen alvorens de server om een update te vragen blijft.
      * Als u zeer hoge TTL hebt, zullen de updates aan uw DNS verslag langer duren om zich te verspreiden.
* Voer prestatie- en beveiligingstests uit die voldoen aan uw zakelijke vereisten en doelstellingen.
   * Test de werkgebiedomgeving.  Het is even groot als de productie.
   * Ontwikkelomgevingen hebben niet dezelfde grootte als stadium en productie.
* Besnoeiing over en zorg ervoor dat daadwerkelijke go-live zonder enige nieuwe plaatsing of inhoudsupdate wordt uitgevoerd.
* Maak profielen voor gebruikersmeldingen van Admin Consoles. Zie [Meldingsprofielen](/help/journey-onboarding/notification-profiles.md)
* Overweeg het vormen van de Regels van de Filter van het Verkeer om te controleren welk verkeer niet op uw website zou moeten worden toegestaan.
   * De regels van de de beperkingsverkeersfilter van het tarief kunnen een efficiënt hulpmiddel tegen aanvallen zijn DDoS. Een speciale categorie van de regels van het verkeersfilter, genoemd de regels van WAF, vereist een afzonderlijke vergunning.
   * Zie documentatie voor sommige [voorgestelde startersregels](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

U kunt altijd naar de lijst verwijzen als u uw taken tijdens Go-Live opnieuw moet kalibreren.
