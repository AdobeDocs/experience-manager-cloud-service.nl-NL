---
title: Opmerkingen bij de release voor Cloud Manager 2025.10.0
description: Meer informatie over de release van Cloud Manager 2025.10.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 673e6a2403026e33c3bbd225b7296a1fb8877404
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.10.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Meer informatie over de release van Cloud Manager 2025.10.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.10.0 in AEM as a Cloud Service is donderdag 2 oktober 2025.

De volgende geplande release is donderdag 6 november 2025.

## Nieuwe functies {#what-is-new}

* **Specifieke stadium-slechts en productie-enige plaatsingspijpleidingen**

  Cloud Manager biedt nu speciale implementatiepijpleidingen voor alleen het werkgebied en de productie, die meer flexibiliteit bieden voor het onafhankelijk beheren van implementaties in testomgevingen en productieomgevingen. Zie [ gesplitst werkgebied-slechts en productie-slechts pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md).

* **AEM Cloud Health Assessment Service**

  Adobe introduceert de AEM Cloud Health Assessment Service, een geautomatiseerd, niet-invasief hulpprogramma voor controle dat uw AEM as a Cloud Service-omgeving optimaliseert, beveiligt en aansluit bij de best practices.

  Deze service doet het volgende:

   * Scant omgevingen naar knelpunten in de oppervlakteprestaties, inefficiëntie en potentiële risico&#39;s.
   * Analyseert inhoudsstructuren (blauwdrukken, live kopieën) en aangepaste configuraties.
   * Identificeert verouderde gebiedsdelen (AEM SDK, derdebibliotheken).
   * Hiermee worden kwaliteitsproblemen met code gemarkeerd (onjuiste annotaties, inefficiënte patronen).
   * Levert actionable begeleiding door dashboards zoals **Centrum van Acties**.
   * Steunt pro-actieve optimalisering door vroege probleemopsporing en sanering.

  Teams kunnen hun AEM-omgevingen voortdurend bewaken en verbeteren voor betere prestaties, betere beveiliging en onderhoud op lange termijn.

  Zie [ Beoordeling van de Gezondheid voor de Milieu&#39;s van de Productie en van het Stadium ](/help/implementing/cloud-manager/reports/report-health-assessment.md).

* **de steun van de Pijpleiding Config**

  Config Pipelines worden nu ondersteund voor sites die met Edge Delivery Services zijn gebouwd en deze mogelijkheid uitbreiden tot buiten de Cloud Service-omgevingen. U kunt **Pijpleidingen Config** gebruiken om montages zoals configuratie CDN, met inbegrip van de regels van de verkeersfilter en oorsprongskiezers te beheren. Zie [ Ondersteunde Configuraties ](/help/operations/config-pipeline.md#configurations).

  Edge Delivery config pijpleidingen steunen ook geheimen door de pijpleidingsvariabelen van Cloud Manager.

  Zie [ toevoegen de Pijpleiding van Edge Delivery ](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

* **gestroomlijnde de opstellingsdialoogdoos van het Domein in kaart brengen-CDN**

  Cloud Manager heeft het **Domein van de Kaart aan CDN** stroom vereenvoudigd om verwarring en snelheidsconfiguratie te verminderen. De dialoogdoos benadrukt nu **Adobe beheerde CDN** (met een &quot;Aanbevolen&quot;badge).

  ![ Domein van de Kaart aan CDN dialoogdoos met Adobe beheerde geselecteerde radioknoop CDN ](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-adobe-managed-cdn.png).

  Zie [ een domeinafbeelding ](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md) toevoegen.

  De dialoogdoos stelt ook één enkele, beknopte controlelijst voor **Andere CDN leverancier** kaart voor, die op instructionele inhoud met het volgende zich richt:

   * Plaats de oorsprong van de CDN op `publish-p<PROGRAM_ID>-e<ENV_ID>.adobeaemcloud.com` .
   * Plaats **Gastheer/SNI** om de originele gastheer door:sturen.
   * Voeg `X-AEM-Edge-Key` toe (na het opstellen van de sleutel in Cloud Manager).
   * Stel `X-Forwarded-Host` in op het klantgerichte domein.
   * Wis andere `X-Forwarded-*` kopteksten alvorens AEM te bereiken.

  ![ Domein van de Kaart aan CDN dialoogdoos met Andere geselecteerde CDN leverancierskeuzerondje ](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-other-cdn-provider.png)

  <!-- (no redundant `Origin` field or "Learn more" clutter) -->De bijbehorende voettekst biedt twee handige koppelingen: voorbeeldconfiguraties voor belangrijke CDN&#39;s en een koppeling naar volledige documentatie. Één enkele bevestigingsknoop-I heeft gevormd Mijn CDN-voltooit de stroom.

  Zie [ CDN in AEM as a Cloud Service ](/help/implementing/dispatcher/cdn.md#point-to-point-CDN).

<!--
### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md) has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. -->


## Beta-programma&#39;s {#private-beta-program}

Neem deel aan bètaprogramma&#39;s van Cloud Manager om exclusieve toegang te krijgen tot de volgende functies voordat ze in het algemeen worden uitgebracht.

De volgende mogelijkheden zijn momenteel beschikbaar:
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Uitbreidbaarheid en aanpassing van Experience Hub {#exp-hub-extensibility}

[ Experience Hub ](/help/experience-hub.md) dient als uw ingangspunt aan AEM, die voor de behoeften van uw organisatie wordt aangepast. Vertel Adobe over uw bestaande AEM UI-extensies, zodat ze u kunnen helpen deze extensies zo weinig mogelijk in Experience Hub in te schakelen.

![ Diagram van de rekbaarheid en aanpassingswerkschema van Experience Hub ](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Sluit aangepaste ervaringen in Experience Hub in om het dashboard van uw organisatie uit te breiden en aan te passen. Naast ingebouwde widgets Adobe, voeg uw eigen gebruiken toe gebruikend het [ kader van de Uitbreidbaarheid 0} UI. ](https://developer.adobe.com/uix/docs/) Creëer op JavaScript gebaseerde UI-apps en zorg ervoor dat deze aan uw gebruikers worden gepresenteerd, zodat ze aan de specifieke vereisten en workflows voldoen.

Geïnteresseerd in de bèta? E-mail [ beta_exphubextensibility@adobe.com ](mailto:beta_exphubextensibility@adobe.com) met uw Adobe OrgID en een korte beschrijving van de aanpassing u van plan bent te creëren.

### Snellere builds met module caching {#quick-build-cm-pipelines}

Een nieuw bouwstijlmodel compileert slechts veranderde modules (eerder dan de volledige repo) gebruikend module-vlakke caching om bouwstijltijden te verkorten. Het is van toepassing op code-kwaliteit, volledig-stapel, en stadium-slechts pijpleidingen.

Geïnteresseerd? E-mail [ beta_quickbuild_cmpipelines@adobe.com ](mailto:beta_quickbuild_cmpipelines@adobe.com) met uw Adobe OrgID en identiteitskaart van het Programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->



### Één-klik terugschroeven van prijzen voor pijpleidingsplaatsingen {#one-click-rollback}

Snel aan een vorige plaatsing terugkeren als de recentste klantenbroncode niet zoals verwacht-geen behoefte werkt om de volledige pijpleiding opnieuw te voeren of begaat manueel terug.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![ herstel klantenbroncode van de kaart van Milieu ](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png) *van Milieu&#39;s hierboven die **tonen herstelt**>**Vorige code stelde**optie voor een geselecteerd milieu.*

![ herstel vorige code opgesteld dialoogdoos ](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
*in **herstel vorige code opgesteld**dialoogdoos, herzie de momenteel opgestelde versie en de versie u wilt herstellen, dan klikken bevestigt *****.

![ Herstellend activering ](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager rolt het milieu terug naar de vroegere bouwstijl, houdt inhoud en configuratie intact, en merkt het milieu **Herstellend**tot de plaatsing voltooit.*

![ de codeversie van Source in gebruik ](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *de mening van de Details van het Milieu, zoals hierboven gezien, toont nu ook de actieve bron-code versie in gebruik.*

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ restorecode@adobe.com ](mailto:restorecode@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.

Zie [ de Vorige Code herstellen die in AEM as a Cloud Service ](/help/operations/restore-previous-code-deployed.md) wordt opgesteld.

Zie ook [ Inhoud terugzetten in AEM as a Cloud Service ](/help/operations/restore.md).

### Speciale testomgeving {#specialized-test-environment}

Cloud Manager steunt nu de toevoeging van een nieuw milieutype genoemd **Gespecialiseerde het Testen Milieu**. De omgeving is ontworpen om teams te helpen functies onder bijna-productieomstandigheden te valideren voordat ze live gaan. Dit omgevingstype is verschillend van *Productie + Stadium*, *Ontwikkeling*, of *Snelle Ontwikkeling* milieu&#39;s en biedt een geconcentreerde ruimte voor het runnen van geavanceerde bevestigingsscenario&#39;s aan.

**Recente verhogingen**

* U kunt een Specialized het Testen Milieu op een niet productiepijplijn door een eenvoudigere, meer intuïtieve werkschema nu vormen. De gestroomlijnde installatie versnelt voltooiing en vermindert configuratiefouten.
* **Inhoud van het Exemplaar** wordt nu gesteund in Gespecialiseerde het Testen milieu&#39;s. U kunt **Inhoud van het Exemplaar** veilig in geïsoleerde testende milieu&#39;s in werking stellen die Productie weerspiegelen. <!-- (CMGR‑68900) -->

Zie [ een Gespecialiseerde het Testen Milieu ](/help/implementing/cloud-manager/specialized-test-environment.md) toevoegen.

![ voeg milieu dialoogdoos met Gespecialiseerde het Testen van Milieu geselecteerde radioknoop ](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png) toe

>[!NOTE]
>
>Adobe heeft bètatoegangsaanvragen voor gespecialiseerde testomgevingen gesloten, omdat het voldoende aantal deelnemers heeft bereikt. De functie is nu in voorbereiding op algemene beschikbaarheid.

<!--
If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


### Je eigen gang (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png) toe

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

**vaak gestelde vragen over BYOG**

| Vraag | Antwoord |
|---|---|
| *hoe kan een projectschakelaar terug naar de Adobe-Beheerde bewaarplaats van het Git indien nodig?* | Het is eenvoudig om terug te schakelen. [ werk de pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) bij om aan de bewaarplaats van Adobe te richten en de externe bewaarplaats te verwijderen als het niet meer vereist is. |
| *is het mogelijk om verschillende bewaarplaatsen voor verschillende milieu&#39;s (bijvoorbeeld, niet-productie tegenover productie) te vormen om het testen in niet productie eerst toe te staan?* | Ja, verschillende opslagruimten kunnen worden geconfigureerd voor afzonderlijke omgevingen. De ontwikkelings- of codekwaliteitspijplijn kan bijvoorbeeld naar een externe opslagplaats verwijzen terwijl de productiepijplijn verbonden blijft met de Adobe-opslagplaats. Zorg ervoor dat de synchronisatietaak tussen de twee opslagruimten actief blijft tijdens deze configuratie. |
| *blijven de bestaande montages zoals `IP Allow` lijsten werken?* | Ja, bestaande `IP Allow` lijsten werken nog steeds zoals gewoonlijk. Nochtans, als de externe bewaarplaats van het Git door een firewall wordt beschermd, moeten de noodzakelijke [ adressen van Adobe IP aan de lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) worden toegevoegd. |
| *Werken al bewaarplaats GitLab URLs? De repository URL in gebruik volgt de notatie `https://gitlab_dedicated_url.com/path/repo-name.git` , die afwijkt van het voorbeeld in de documentatie.* | Ja, om het even welke bewaarplaats GitLab die API V3 of V4 steunt wordt gesteund, met inbegrip van zelf-ontvangen GitLab URLs als die in [ wordt beschreven voeg externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toe (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Toegangstokens beheren{#manage-access-tokens}

Het gebruik **beheert de Tokens van de Toegang** in Cloud Manager aan mening, hernoemt, en schrapt toegangstokens verbonden aan externe bewaarplaatsen BYOG, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [ de Tokens van de Toegang beheren ](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->


## Bugfixes {#bug-fixes}

Er zijn geen significante insectenmoeilijke situaties in de versie van Oktober Cloud Manager.


<!-- ## Known issues {#known-issues} -->

