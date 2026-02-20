---
title: Opmerkingen bij de release voor Cloud Manager 2026.1.0
description: Meer informatie over de release van Cloud Manager 2026.1.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 2ea076c42a6406548bf48cd246227fc8ddb3a080
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2026.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Meer informatie over de release van Cloud Manager 2026.1.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2026.1.0 in AEM as a Cloud Service is donderdag 22 januari 2026.

De volgende geplande release is donderdag 5 februari 2026.

## Nieuwe functies - Cloud Manager {#cloud-manager-whats-new}

* **de pijpleidingen van de Configuratie steunen nu beheerde geheimen**

  Gebruikers kunnen nu rechtstreeks in Cloud Manager-configuratiepijpleidingen geheimen toevoegen en beheren. Deze geheimen treden veilig waarden in de specificaties van de pijpleidingsconfiguratie met voeten en steunen flexibele, milieu-specifieke plaatsingen.

  ![ Mening/geeft de variabelen optie op het drop-down menu voor een geselecteerde pijpleiding ](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-option.png) uit
  *Mening/geef Variabelen optie op het drop-down menu voor een geselecteerde pijpleiding uit.*

  ![ de dialoogdoos van de Configuratie van Variabelen ](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*de dialoogdoos van de Configuratie van Variabelen.*

* **Verbeterde stabiliteit, prestaties, en betrouwbaarheid**

  Deze release bevat updates voor optimalisatie en onderhoud die de stabiliteit, prestaties en betrouwbaarheid van Cloud Manager verbeteren.




## Beta-programma&#39;s {#private-beta-program}

Neem deel aan bètaprogramma&#39;s van Cloud Manager om exclusieve toegang te krijgen tot de volgende functies voordat ze in het algemeen worden uitgebracht.

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Adobe raadt klanten aan voorzichtig te zijn en zich niet te verlaten op de juiste werking of prestaties van bètareleases of op begeleidende documentatie of materialen. Functies en API&#39;s in bèta kunnen zonder voorafgaande kennisgeving worden gewijzigd. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

Zie ook [ de programma&#39;s van Beta van AEM ](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

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

![ geeft de Dialoogvenster van de Pijpleiding van de Niet-Productie uit die de twee opties van de Strategie van de Bouwstijl tonen die Volledige Bouwstijl en Slimme zijn ](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*geef de de dialoogdoos uit van de Pijpleiding van de Niet-Productie die de twee opties toont van de Strategie van de Bouwstijl die Volledig zijn bouwt en Smart bouwt.*

In **voeg/geef de dialoogdoos van de Pijpleiding** toe, onder het **lusje van de Code van Source**, laat een nieuwe **Bouw Strategie** sectie u één van de volgende bouwstijlopties kiezen:

* **Volledig bouwt** — bouwt alle modules in de bewaarplaats op elke looppas.
* **Slim bouwt** — bouwt slechts modules die sinds laatste worden veranderd begaan, die algemene bouwtijd verkort.

U controleert welke pijpleidingen gebruiken **Slimme bouwstijl**. Tijdens bèta, verschijnt deze optie slechts voor **Kwaliteit van de Code** en **Dev de 3} pijpleidingen van de Plaatsing.**

Geïnteresseerd? E-mail [ beta_quickbuild_cmpipelines@adobe.com ](mailto:beta_quickbuild_cmpipelines@adobe.com) met uw Adobe OrgID en identiteitskaart van het Programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

## Bugfixes {#bug-fixes}

Er zijn geen significante insectenmoeilijke situaties in de versie van Cloud Manager van december 2025.


<!-- ## Known issues {#known-issues} -->

