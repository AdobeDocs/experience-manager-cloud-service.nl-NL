---
title: Live checklist
description: Meer informatie over alle elementen die nodig zijn voor een geslaagde Go-Live met AEM as a Cloud Service.
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 64344b9b2cce8d7c7f05d3e5ba94049346308a9d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Live checklist {#Go-Live-Checklist}

Controleer deze lijst met activiteiten om ervoor te zorgen dat Go-Live probleemloos en succesvol wordt uitgevoerd.

* Stel een de productiepijplijn van begin tot eind met functionele en UI het testen in werking om te verzekeren **altijd huidige** AEM productervaring. Zie de volgende bronnen.
   * [Versie-updates AEM](/help/implementing/deploying/aem-version-updates.md)
   * [Aangepaste functionele tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [UI-tests](/help/implementing/cloud-manager/ui-testing.md)
* Als u van AEM 6.5 migreert, zou u inhoud aan productie moeten migreren en ervoor zorgen dat een relevante ondergroep bij het opvoeren voor het testen beschikbaar is.
   * De beste praktijken van DevOps voor AEM impliceren dat de code zich omhoog van ontwikkeling aan het productiemilieu beweegt terwijl de inhoud zich van productiemilieu&#39;s beweegt.
* Plan een code- en inhoudstijdsperiode.
   * Zie ook de sectie [ Code en de Inhoud bevriezen Tijdlijnen voor de Migratie ](#code-content-freeze)
* Voer de laatste top-up van de inhoud uit.
* Dispatcher-configuraties valideren.
   * Gebruik een lokale Dispatcher-validator waarmee u de Dispatcher lokaal kunt configureren, valideren en simuleren
      * [ opstelling de lokale hulpmiddelen van Dispatcher ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools#prerequisites).
   * Herzie zorgvuldig de virtuele gastheerconfiguratie.
      * De eenvoudigste (en standaard)oplossing is om `ServerAlias *` op te nemen in het virtuele hostbestand in `/dispatcher/src/conf.d/available_vhostsfolder` . Hierdoor kunnen de aliassen van de host die worden gebruikt door product functionele tests, Dispatcher cache-validatie en klonen functioneren.
      * Als `ServerAlias *` echter niet acceptabel is, moeten in aanvulling op uw aangepaste domeinen ten minste de volgende `ServerAlias` -items zijn toegestaan:
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* Vorm CDN, SSL en DNS.
   * Als u uw eigen CDN gebruikt, ga een steunkaartje in om aangewezen het verpletteren te vormen.
      * Zie de sectie [ CDN van de Klant richt aan AEM Beheerde CDN ](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) in de documentatie CDN voor details.
      * Vorm SSL en DNS volgens de documentatie van uw verkoper CDN.
   * Als u geen extra CDN gebruikt, beheer SSL en DNS volgens de volgende documentatie:
      * SSL-certificaten beheren
         * [Inleiding tot SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)
         * [SSL-certificaten beheren](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Aangepaste domeinnamen (DNS) beheren
         * Zorg ervoor dat de DNS-cutover geen onverwachte problemen veroorzaakt. Creeer testsubdomain om uw productieinstantie met aan te sluiten alvorens u gaat-leven en een ronde van het testen van UAT doet. Dus als uw domein example.com is, kunt u een subdomein maken test.example.com en dit toepassen op productie. Tijdens het testen van UAT van het domein, zoek dingen zoals juiste verbindingsredirection, caching, en de configuraties van Dispatcher.
         * [Inleiding tot aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Een aangepaste domeinnaam beheren](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * Herinner me om TTL te bevestigen die voor uw DNS verslag wordt geplaatst.
      * TTL is de hoeveelheid tijd een DNS verslag in een geheim voorgeheugen alvorens de server om een update te vragen blijft.
      * Als u zeer hoge TTL hebt, duurt het bijwerken van uw DNS verslag langer om zich te verspreiden.
* Voer prestatie- en beveiligingstests uit die voldoen aan uw zakelijke vereisten en doelstellingen.
   * Tests uitvoeren in een werkgebiedomgeving.  Het is even groot als de productie.
   * Ontwikkelomgevingen hebben niet dezelfde grootte als stadium en productie.
* Besnoeiing over en zorg ervoor dat daadwerkelijke go-live zonder enige nieuwe plaatsing of inhoudsupdate wordt uitgevoerd.
* Maak profielen voor gebruikersmeldingen voor Admin Consoles. Zie [ Profielen van het Bericht ](/help/journey-onboarding/notification-profiles.md)
* Overweeg het vormen van de Regels van de Filter van het Verkeer om te controleren welk verkeer niet op uw website zou moeten worden toegestaan.
   * De regels van de Filter van het Verkeer van het tarief kunnen een efficiënt hulpmiddel tegen aanvallen zijn DDoS. Een speciale categorie van de Regels van de Filter van het Verkeer, genoemd de (Firewall van de Toepassing van het Web) regels van WAF, vereist een afzonderlijke vergunning.
   * Zie documentatie voor sommige [ voorgestelde starterregels ](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

U kunt altijd naar de lijst verwijzen als u uw taken tijdens Go-Live opnieuw moet kalibreren.
