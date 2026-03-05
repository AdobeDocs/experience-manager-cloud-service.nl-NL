---
title: Opmerkingen bij de release voor Cloud Manager 2026.3.0
description: Meer informatie over de release van Cloud Manager 2026.3.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: eb3e826e27e14b8b1da534440f11d43e973130ec
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2026.3.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Meer informatie over de release van Cloud Manager 2026.3.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [&#x200B; huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service &#x200B;](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2026.3.0 in AEM as a Cloud Service is donderdag 5 maart 2026.

De volgende geplande release is donderdag 2 april 2026.


## Nieuwe functies - Cloud Manager {#cloud-manager-whats-new}

* **Cloud Manager steunt nu a** Sluitereffect **optie voor** de invoer van het Exemplaar van de Inhoud **&#x200B;**

  Wanneer u **Sluitereffect** toelaat, schrapt Cloud Manager de bestaande inhoud bij de bestemming alvorens de invoer te beginnen, zodat kunt u van een schone lei beginnen en conflicten met reeds bestaande inhoud vermijden. Als u **Wipe** gehandicapt verlaat, voert Cloud Manager de nieuwe inhoud bovenop de bestaande bestemmingsinhoud in. Er wordt een bevestigingsbericht weergegeven voordat het sluitereffect begint en Cloud Manager geeft een logboek van de sluiteractie en de importgegevens voor traceerbaarheid.

  Zie ook [&#x200B; inhoud van het Exemplaar &#x200B;](/help/implementing/developing/tools/content-copy.md#copy-content).

* **Steun voor rekbaarheid UI in AEM Experience Hub**
De steun voor Uitbreidingen UI in [&#x200B; AEM Experience Hub &#x200B;](https://experience.adobe.com/experiencemanager) wordt nu toegelaten, latend ontwikkelaars de interface met douanefunctionaliteit uitbreiden en widgets die gebruikend Adobe App Builder worden gebouwd.

  Meer leren, zie [&#x200B; AEM Experience Hub &#x200B;](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Verbeterde stabiliteit, prestaties, en betrouwbaarheid**

  Deze release bevat updates voor optimalisatie en onderhoud die de stabiliteit, prestaties en betrouwbaarheid van Cloud Manager verbeteren.


## Beta-programma&#39;s {#private-beta-program}

Neem deel aan bètaprogramma&#39;s van Cloud Manager om exclusieve toegang te krijgen tot de volgende functies voordat ze in het algemeen worden uitgebracht.

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Adobe raadt klanten aan voorzichtig te zijn en zich niet te verlaten op de juiste werking of prestaties van bètareleases of op begeleidende documentatie of materialen. Functies en API&#39;s in bèta kunnen zonder voorafgaande kennisgeving worden gewijzigd. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

Zie ook [&#x200B; de programma&#39;s van Beta van AEM &#x200B;](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

De volgende mogelijkheden zijn momenteel beschikbaar:
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Cloud Manager MCP-server voor IDE&#39;s met AI-voeding{#mcp-server-for-cm}

U kunt nu een server proberen MCP (ModelContext Protocol) die Cloud Manager Openbare APIs als hulpmiddelen voor AI-Toegelaten windes (zoals Cursor) blootstelt. Nadat u het aansluit, kunt u conversationele herinneringen gebruiken om programma&#39;s, pijpleidingen, milieu&#39;s, en bewaarplaatsen een lijst te maken en te beheren, die u helpen sneller bewegen zonder uw redacteur te verlaten.

Zie de documentatie [&#x200B; Gebruik MCP met AEM as a Cloud Service &#x200B;](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

Zie het leerprogramma {de Server van 0} Cloud Manager MCP [.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-server/cloud-manager#)

Geïnteresseerd in de bèta? E-mail [&#x200B; GRP-AEM-CM-MCP-FEEDBACK@adobe.com &#x200B;](mailto:GRP-AEM-CM-MCP-FEEDBACK@adobe.com) met uw Adobe OrgID en identiteitskaart van het Programma.


<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI Extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Snellere builds met module caching {#quick-build-cm-pipelines}

Een nieuw bouwstijlmodel compileert slechts veranderde modules (eerder dan de volledige repo) gebruikend module-vlakke caching om bouwstijltijden te verkorten. Het is van toepassing op code-kwaliteit, volledig-stapel, en stadium-slechts pijpleidingen.

![&#x200B; geeft de Dialoogvenster van de Pijpleiding van de Niet-Productie uit die de twee opties van de Strategie van de Bouwstijl tonen die Volledige Bouwstijl en Slimme zijn &#x200B;](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*geef de de dialoogdoos uit van de Pijpleiding van de Niet-Productie die de twee opties toont van de Strategie van de Bouwstijl die Volledig zijn bouwt en Smart bouwt.*

In **voeg/geef de dialoogdoos van de Pijpleiding** toe, onder het **lusje van de Code van Source**, laat een nieuwe **Bouw Strategie** sectie u één van de volgende bouwstijlopties kiezen:

* **Volledig bouwt** — bouwt alle modules in de bewaarplaats op elke looppas.
* **Slim bouwt** — bouwt slechts modules die sinds laatste worden veranderd begaan, die algemene bouwtijd verkort.

U controleert welke pijpleidingen gebruiken **Slimme bouwstijl**. Tijdens bèta, verschijnt deze optie slechts voor **Kwaliteit van de Code** en **Dev de 3&rbrace; pijpleidingen van de Plaatsing.**

Geïnteresseerd? E-mail [&#x200B; beta_quickbuild_cmpipelines@adobe.com &#x200B;](mailto:beta_quickbuild_cmpipelines@adobe.com) met uw Adobe OrgID en identiteitskaart van het Programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

## Bugfixes {#bug-fixes}

* Correctie van een probleem waarbij de herstelpunten-API een fout van 500 kon retourneren bij het ophalen van herstelpunten. Het eindpunt behandelt nu ongeldige waarden correct, die verenigbare en betrouwbare reacties verzekeren. (CMGR-72963)
* Cloud Manager accepteert nu URL&#39;s in de GitHub-opslagruimte met of zonder het achtervoegsel `.git` , waarbij het API-gedrag wordt uitgelijnd met de gebruikersinterface en de gegevensopslagruimte flexibeler wordt. (CMGR-73296)
* Validatie van de naam van een productprofiel is nu niet hoofdlettergevoelig. Hierdoor worden fouten voorkomen bij het maken van profielen met namen die alleen verschillen per hoofdletter. (CMGR-74075)
* U kunt veelvoudige herstelt verrichtingen van de zelfde pijpleidingsuitvoering nu uitvoeren, toelatend opeenvolgende herstelt voor milieu&#39;s zoals Stadium en Productie zonder een nieuwe pijpleidingslooppas te vereisen. (CMGR-73538)


<!-- ## Known issues {#known-issues} -->

