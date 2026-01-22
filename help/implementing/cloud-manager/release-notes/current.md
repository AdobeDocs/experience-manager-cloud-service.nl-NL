---
title: Opmerkingen bij de release voor Cloud Manager 2026.1.0
description: Meer informatie over de release van Cloud Manager 2026.1.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 54566e3ea99c4ac03e266eab52163a516701b611
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2026.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Meer informatie over de release van Cloud Manager 2026.1.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [&#x200B; huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service &#x200B;](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2026.1.0 in AEM as a Cloud Service is donderdag 22 januari 2026.

De volgende geplande release is donderdag 5 februari 2026.

## Nieuwe functies - Cloud Manager {#cloud-manager-whats-new}

* **de pijpleidingen van de Configuratie steunen nu beheerde geheimen**

  Gebruikers kunnen nu rechtstreeks in Cloud Manager-configuratiepijpleidingen geheimen toevoegen en beheren. Deze geheimen treden veilig waarden in de specificaties van de pijpleidingsconfiguratie met voeten en steunen flexibele, milieu-specifieke plaatsingen.

  ![&#x200B; Mening/geeft de variabelen optie op het drop-down menu voor een geselecteerde pijpleiding &#x200B;](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-option.png) uit
  *Mening/geef Variabelen optie op het drop-down menu voor een geselecteerde pijpleiding uit.*

  ![&#x200B; de dialoogdoos van de Configuratie van Variabelen &#x200B;](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*de dialoogdoos van de Configuratie van Variabelen.*

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

### Uitbreidbaarheid en aanpassing van Experience Hub {#exp-hub-extensibility}

[&#x200B; Experience Hub &#x200B;](/help/experience-hub.md) dient als uw ingangspunt aan AEM, die voor de behoeften van uw organisatie wordt aangepast. Vertel Adobe over uw bestaande AEM UI-extensies, zodat ze u kunnen helpen deze extensies zo weinig mogelijk in Experience Hub in te schakelen.

![&#x200B; Diagram van de rekbaarheid en aanpassingswerkschema van Experience Hub &#x200B;](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Sluit aangepaste ervaringen in Experience Hub in om het dashboard van uw organisatie uit te breiden en aan te passen. Naast ingebouwde widgets Adobe, voeg uw eigen gebruiken toe gebruikend het [&#x200B; kader van de Uitbreidbaarheid 0&rbrace; UI. &#x200B;](https://developer.adobe.com/uix/docs/) Creëer op JavaScript gebaseerde UI-apps en zorg ervoor dat deze aan uw gebruikers worden gepresenteerd, zodat ze aan de specifieke vereisten en workflows voldoen.

Geïnteresseerd in de bèta? E-mail [&#x200B; beta_exphubextensibility@adobe.com &#x200B;](mailto:beta_exphubextensibility@adobe.com) met uw Adobe OrgID en een korte beschrijving van de aanpassing u van plan bent te creëren.

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

### Je eigen gang (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [&#x200B; externe bewaarplaatsen in Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![&#x200B; voeg de dialoogdoos van de Bewaarplaats &#x200B;](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png) toe

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

**vaak gestelde vragen over BYOG**

| Vraag | Antwoord |
|---|---|
| *hoe kan een projectschakelaar terug naar de Adobe-Beheerde bewaarplaats van het Git indien nodig?* | Het is eenvoudig om terug te schakelen. [&#x200B; werk de pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) bij om aan de bewaarplaats van Adobe te richten en de externe bewaarplaats te verwijderen als het niet meer vereist is. |
| *is het mogelijk om verschillende bewaarplaatsen voor verschillende milieu&#39;s (bijvoorbeeld, niet-productie tegenover productie) te vormen om het testen in niet productie eerst toe te staan?* | Ja, verschillende opslagruimten kunnen worden geconfigureerd voor afzonderlijke omgevingen. De ontwikkelings- of codekwaliteitspijplijn kan bijvoorbeeld naar een externe opslagplaats verwijzen terwijl de productiepijplijn verbonden blijft met de Adobe-opslagplaats. Zorg ervoor dat de synchronisatietaak tussen de twee opslagruimten actief blijft tijdens deze configuratie. |
| *blijven de bestaande montages zoals `IP Allow` lijsten werken?* | Ja, bestaande `IP Allow` lijsten werken nog steeds zoals gewoonlijk. Nochtans, als de externe bewaarplaats van het Git door een firewall wordt beschermd, moeten de noodzakelijke [&#x200B; adressen van Adobe IP aan de lijst van gewenste personen &#x200B;](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) worden toegevoegd. |
| *Werken al bewaarplaats GitLab URLs? De repository URL in gebruik volgt de notatie `https://gitlab_dedicated_url.com/path/repo-name.git` , die afwijkt van het voorbeeld in de documentatie.* | Ja, om het even welke bewaarplaats GitLab die API V3 of V4 steunt wordt gesteund, met inbegrip van zelf-ontvangen GitLab URLs als die in [&#x200B; wordt beschreven voeg externe bewaarplaatsen in Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/external-repositories.md) toe (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Toegangstokens beheren{#manage-access-tokens}

Het gebruik **beheert de Tokens van de Toegang** in Cloud Manager aan mening, hernoemt, en schrapt toegangstokens verbonden aan externe bewaarplaatsen BYOG, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [&#x200B; de Tokens van de Toegang beheren &#x200B;](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->


## Bugfixes {#bug-fixes}

Er zijn geen significante insectenmoeilijke situaties in de versie van Cloud Manager van december 2025.


<!-- ## Known issues {#known-issues} -->

