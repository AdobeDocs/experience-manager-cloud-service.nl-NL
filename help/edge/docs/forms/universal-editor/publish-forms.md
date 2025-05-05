---
title: Publiceer AEM Forms for Edge Delivery Services.
description: Publiceer uw Edge Delivery Services-formulieren snel en naadloos.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: e4a71d1a513bebed67b9571a483871dc16c36daa
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Adaptief formulier publiceren naar Edge Delivery Services

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>


Wanneer het formulier gereed en gebruiksklaar is, kunt u het publiceren zodat het voor uw klanten toegankelijk is voor gegevensverzameling en -verzending. Als u het formulier publiceert, weet u zeker dat het formulier beschikbaar is op Edge Delivery, zodat gebruikers er probleemloos mee kunnen werken. Met dit proces kunnen klanten het formulier in real-time invullen en verzenden, zodat ze gegevens op efficiënte wijze kunnen vastleggen en de verwerking kunnen stroomlijnen.

## Vereisten

* Een vorm die gebruikend het **malplaatje van Edge Delivery Services** wordt gecreeerd. [ leer meer ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) over het creëren van een op EDS-Gebaseerde vorm.

## Uw formulier publiceren

U kunt om het even welke **op EDS-Gebaseerde Aangepaste Vorm** aan Edge Delivery publiceren door deze stappen te volgen:

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. Open uw adaptieve vorm in de redacteur en klik het **Publish** pictogram op het hogere spoor.
   ![ klik publiceren ](/help/forms/assets/publish-icon-eds-form.png)

1. Wanneer u **klikt publiceer**, verschijnt een scherm of pop-up dat de het publiceren activa, met inbegrip van de titel van de vorm toont. In dit voorbeeld, wordt het **&#x200B;**&#x200B;malplaatje Wknd_Form gebruikt.
   ![ op Klik publiceren ](/help/forms/assets/on-click-publish.png)

1. Klik **publiceren** opnieuw, en een bevestigingspop-up verschijnt, erop wijzend dat uw vorm nu wordt gepubliceerd.
   ![ publiceer Succes ](/help/forms/assets/publish-success.png)

1. Om de van de vorm te controleren publiceer status, klik **opnieuw publiceren**.
   ![ publiceer Status ](/help/forms/assets/publish-status.png)

1. **unpublish** een vorm, open uw vorm in de redacteur, klik het drie-punt menu in de hoger-juiste hoek en klik **unpublish**.
   ![ Unpublish ](/help/forms/assets/unpublish--form.png)

## Formulierverzending in Edge Delivery inschakelen door een referentiefilter voor AEM Publisher te configureren

Om veilige vormvoorlegging te verzekeren, moet u de Filter van de a **Referrer** in de Uitgever van AEM vormen. Met dit filter zorgt u ervoor dat alleen geautoriseerde aanvragen van Edge Delivery schrijfbewerkingen (POST, PUT, DELETE, COPY, MOVE) kunnen uitvoeren om ongeoorloofde wijzigingen te voorkomen. Hieronder vindt u de stappen voor het configureren van een referentiefilter voor AEM Publisher:

### De AEM Instance URL in Edge Delivery bijwerken

Wijzig `submitBaseUrl` in het {**dossier 1} constant.js binnen het vormblok om de instantie URL van AEM te specificeren:**

**voor de Opstelling van de Wolk:**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```

**voor Lokale Ontwikkeling:**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### De configuratie van CORS wijzigen

Pas de **montages CORS** aan om de verzoeken van de vormvoorlegging van de domeinen van Edge Delivery toe te staan. Verwijs naar de [ Gids van de Configuratie CORS ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors) voor details.

**de Configuratie van de Steekproef CORS:**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

Voor lokale ontwikkeling, verwijs naar de [ documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter) om CORS van uw **gastheer URL van ontwikkelingsUI** toe te laten.

### Filter Referrer configureren

Opstelling de **Filter van de Verwijzer** in de Dienst van de Wolk AEM via Cloud Manager. [ weet meer ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) over het vormen van het verwijzingsfilter op een instantie van de Dienst van de Wolk AEM die een wolkenmanager gebruikt.

**Configuratie JSON voor de Filter van de Referateur:**

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
    "https://.*\\.hlx\\.page:443",
    "https://.*\\.hlx\\.live:443"
  ],
  "filter.methods": [
    "POST",
    "PUT",
    "DELETE",
    "COPY",
    "MOVE"
  ],
  "exclude.agents.regexp": [
    ""
  ]
}
```

Deze configuratie specificeert welke methodes van HTTP worden gefiltreerd, welke verwijzingen worden toegestaan, en welke gebruikersagenten van de filter worden uitgesloten. Door deze configuraties uit te voeren, **vormvoorlegging via Edge Delivery** zal worden beveiligd en beperkt tot erkende bronnen slechts.

### Gepubliceerd adaptief formulier openen

Uw Aangepaste Vorm is nu toegankelijk via **Edge Delivery** gebruikend het volgende formaat URL:

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

Bijvoorbeeld, is URL voor **k-Vorm**:

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


## Zie ook

{{universal-editor-see-also}}

