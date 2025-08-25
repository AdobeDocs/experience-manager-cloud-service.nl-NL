---
title: 'Probleemoplossing 403: Verboden fouten in Edge Delivery Services-formulierverzending'
description: Leer hoe u 403 Verboden fouten kunt opsporen en oplossen bij het verzenden van formulieren van Edge Delivery Services naar AEM Publish. Deze handleiding behandelt algemene oorzaken, zoals CORS, Dispatcher-regels en problemen met het filter Referrer.
feature: Edge Delivery Services
role: Admin, Developer
exl-id: f397e059-f1b3-4afa-bd38-8f5fc591bb22
source-git-commit: d457bf9af377176222c2b96816fbbc4265e6b167
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# Probleemoplossing 403: Verboden fouten in Edge Delivery Services-formulierverzending {#troubleshooting-403-forbidden-edge-delivery}

Wanneer het voorleggen van vormen van Edge Delivery Services aan AEM publiceren, kunt u a **403 ontmoeten Verboden** fout. Deze fout geeft aan dat de server weigert het verzoek te verwerken, doorgaans als gevolg van beveiligingsconfiguraties. In dit artikel kunt u de meest voorkomende oorzaken van dit probleem identificeren en oplossen.

## Probleembeschrijving

De gebruikers ervaren a **403 Verboden** fout wanneer het voorleggen van vormen van Edge Delivery Services aan AEM publiceren. De fout wordt weergegeven als:

- HTTP-statuscode: 403
- Foutbericht: &quot;Verboden&quot; of &quot;Toegang geweigerd&quot;
- Het verzenden van het formulier mislukt zonder dat de AEM-server voor verzending wordt bereikt

Dit probleem treedt vaak op in Edge Delivery Services-integraties, waarbij formulieren die worden gehost op Edge-domeinen (`.aem.live`, `.aem.page`, `.hlx.page`, `.hlx.live` ) proberen gegevens naar AEM-publicatie-instanties te verzenden.

>[!IMPORTANT]
>
>Met repoless-instellingen kunnen meerdere sites worden gehost met dezelfde opslagplaats. Voor een correcte verzending van formulieren moet elk sitedomein afzonderlijk aan de lijsten van gewenste personen worden toegevoegd.
>
>**Voorbeeld:**
>
>- Repository: `https://github.com/adobe/abc`
>- Site 1: `main--abc--adobe.aem.live`
>- Site 2: `main--abc1--adobe.aem.live`
>
>Beide domeinen hebben verschillende ingangen van de lijst van gewenste personen nodig om vormvoorlegging te functioneren van beide plaatsen.

## Algemene oorzaken en oplossingen

Een fout van het type 403 Verboden in het verzenden van een Edge Delivery Services-formulier kan meerdere oorzaken hebben. Voer de volgende stappen voor het oplossen van problemen in de juiste volgorde uit:

### &#x200B;1. Problemen met CORS (Cross Origin Resource Sharing)

**Symptomen:**

- Browserconsole geeft CORS-foutberichten weer
- Het lusje van het netwerk toont het verzoek dat alvorens de server wordt geblokkeerd te bereiken
- Foutberichten waarin &quot;Verzoek van kruisoorsprong geblokkeerd&quot; wordt vermeld

**Diagnose:**

1. Browser voor ontwikkelaars openen (F12)
2. Het tabblad Console controleren op CORS-foutberichten
3. Zoek naar berichten zoals: `Access to fetch at 'https://publish-xxx.adobeaemcloud.com' from origin 'https://main--repo--owner.aem.live' has been blocked by CORS policy`

**Oplossing:**
Configureer CORS-instellingen in AEM om aanvragen van uw specifieke Edge Delivery-sitedomeinen toe te staan:

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Sites - Add each site domain individually
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true

# Legacy Franklin domains (if still in use)
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>Vervang `main--abc--adobe.aem.live` en `main--abc1--adobe.aem.live` door de werkelijke sitedomeinen. Voor elke site die vanuit dezelfde opslagplaats wordt gehost, is een apart CORS-configuratieitem vereist.

Voor gedetailleerde configuratie CORS, verwijs naar de [ Gids van de Configuratie van CORS ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).

### &#x200B;2. Dispatcher-regels

**Symptomen:**

- 403 fout komt zonder CORS- berichten in browser console voor
- De aanvraag is bij de server ingediend, maar wordt geblokkeerd door Dispatcher
- Fout voordat AEM-toepassingslaag is bereikt

**Diagnose:**

1. Controleren of de aanvraag-URL overeenkomt met alle Dispatcher-filterregels
2. Dispatcher-configuratie controleren op `/filter` -regels die POST-aanvragen kunnen blokkeren
3. Verifieer dat het eindpunt van de vormvoorlegging in de configuratie van Dispatcher wordt toegestaan

**Oplossing:**
Dispatcher-configuratie bijwerken om aanvragen voor het verzenden van formulieren toe te staan:

1. Zorgt ervoor dat POST-verzoeken om eindpunten voor verzending te vormen zijn toegestaan
2. Voeg de juiste filterregels toe voor Edge Delivery-domeinen
3. Controleren of het pad naar de verzendserver niet is geblokkeerd

Voorbeeld Dispatcher-filterconfiguratie:

```apache
/filter {
  # Allow POST requests to form submission servlet
  /0100 { /type "allow" /method "POST" /url "/content/forms/af/*" }
  /0101 { /type "allow" /method "POST" /url "/adobe/forms/af/submit/*" }
  /0102 { /type "allow" /method "POST" /url "/content/forms/portal/submit/adaptiveform" }
}
```

### &#x200B;3. Problemen met filters referentie

**Symptomen:**

- 403-fout zonder CORS-problemen in browserconsole
- De aanvraag bereikt AEM, maar wordt door het filter Verkoperder afgewezen
- Fout treedt op in de AEM-toepassingslaag

**Diagnose:**
Controleer de AEM-foutlogboeken voor de afkeuring van filters voor referenties:

1. [Logbestanden van AEM Cloud Service openen via Cloud Manager](/help/implementing/cloud-manager/manage-logs.md)
2. Zoeken naar items in `aemerror.log` met:
   - &quot;Verwijzend filter&quot;
   - &quot;org.apache.sling.security.impl.ReferrerFilter&quot;
   - Berichten die fout bij verwijzingsvalidatie aangeven

**Logingang van het Voorbeeld:**

```
[ERROR] org.apache.sling.security.impl.ReferrerFilter Referrer filter rejected request with referrer 'https://main--abc--adobe.aem.live' for POST /content/forms/af/submit
```

**Oplossing:**
Configureer het filter Referrer om uw specifieke Edge Delivery-sitedomeinen toe te staan:

1. Maak of werk het OSGi-configuratiebestand bij: `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. Voeg de volgende configuratie toe met uw specifieke sitedomeinen:

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
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

3. De configuratie implementeren via Cloud Manager

>[!IMPORTANT]
>
>**voor repoless montages:** u moet elk plaatsdomein individueel aan de `allow.hosts` serie toevoegen. Het gebruik van alleen regex-patronen volstaat mogelijk niet voor alle scenario&#39;s. Omvat zowel specifieke domeinen als regex patronen voor uitvoerige dekking.

>[!WARNING]
>
>De Filter van de Referateur van AEM is geen OSGi- configuratiemechanisme, die betekent slechts één configuratie op de dienst van AEM tegelijkertijd actief is. Voeg waar mogelijk geen aangepaste filterconfiguraties voor Referrer toe, aangezien hierdoor native configuraties van AEM worden overschreven en de productfunctionaliteit kan worden verbroken.

## Diagnostische stappen

Voer de volgende stappen uit om de specifieke oorzaak van de 403-fout te achterhalen:

### Stap 1: Browserconsole controleren

1. Browser voor ontwikkelaars openen (F12)
2. Naar het tabblad Console gaan
3. Poging tot het verzenden van formulieren
4. Zoeken naar foutberichten met betrekking tot CORS

**als de fouten CORS aanwezig zijn:** volg de oplossing CORS hierboven.
**als geen fouten CORS:** ga aan Stap 2 te werk.

### Stap 2: Het Lusje van het Netwerk van de controle

1. Browser voor ontwikkelaars openen (F12)
2. Naar het tabblad Netwerk gaan
3. Poging tot het verzenden van formulieren
4. Controleer de mislukte aanvraagdetails
5. Antwoordheaders en status bekijken

**als het verzoek geen server bereikt:** Waarschijnlijk een kwestie van Dispatcher.
**als het verzoek server bereikt maar ontbreekt:** waarschijnlijk een kwestie van de Filter van de Referateur.

### Stap 3: AEM-logbestanden controleren

1. Toegang tot Cloud Manager
2. Navigeren naar omgevingen → Uw omgeving → Logs
3. Downloaden of weergeven `aemerror.log`
4. Zoeken naar items rond het tijdstip van verzending van het formulier
5. Zoeken naar berichten die betrekking hebben op het filter Referrer of de beveiliging

## Preventie en beste praktijken

### &#x200B;1. Correcte configuratie tijdens installatie

- Instellingen voor CORS-, Dispatcher- en Referrer-filters configureren tijdens de eerste Edge Delivery Services-installatie
- **voor elke nieuwe plaats:** voeg het specifieke domein aan alle lijsten van gewenste personen (CORS, de Filter van de Referentie) toe
- Formulierverzendingen testen in de ontwikkelomgeving voordat ze live gaan

### &#x200B;2. Milieuspecifieke configuraties

- Verschillende configuraties gebruiken voor ontwikkelings-, staging- en productieomgevingen
- Localhost-domeinen opnemen voor lokale ontwikkelingstests
- **Document alle plaatsdomeinen** die de toegang van de lijst van gewenste personen voor uw bewaarplaats nodig hebben

### &#x200B;3. Controle en registratie

- Logboekcontrole instellen voor afwijzing van filter Referrer
- Correcte foutafhandeling uitvoeren in verzendcode van formulier
- Browserontwikkelprogramma&#39;s gebruiken tijdens testen

### &#x200B;4. Documentatie en teamkennis

- **handhaaf een register** van alle plaatsdomeinen die de zelfde bewaarplaats gebruiken
- Trainingontwikkelingsteam bij stappen voor probleemoplossing
- Een controlelijst bijhouden voor het instellen van een Edge Delivery Services-formulier
- **lijsten van gewenste personen van de Update** wanneer de nieuwe plaatsen van bestaande bewaarplaatsen worden gecreeerd

## Domeinbeheer van site voor instellingen zonder gegevensoverdracht

Houd Helix-5 en repoless architecturen aan de volgende richtlijnen:

### Bij het maken van nieuwe sites

1. **identificeer het plaatsdomein** (bijvoorbeeld, `main--newsite--adobe.aem.live`)
2. **Update de configuratie van CORS** om het nieuwe domein te omvatten
3. **de Filter van de Verwijzing van de Update** om het nieuwe domein in `allow.hosts` te omvatten
4. **de vormvoorlegging van de Test** van de nieuwe plaats
5. **Document het nieuwe domein** in uw plaatsregistratie

### Naamgevingspatronen van domeinen

- Standaardpatroon: `{branch}--{site}--{owner}.aem.live`
- Elke site krijgt een uniek domein, zelfs wanneer dezelfde opslagplaats wordt gedeeld
- Zowel `.aem.live` als `.aem.page` domeinen kunnen worden gebruikt

### Configuratiebeheer

- Gebruik specifieke domeinvermeldingen in `allow.hosts` voor betere beveiliging
- Toevoegen met regex-patronen voor een bredere dekking
- Lijsten van gewenste personen regelmatig controleren en bijwerken terwijl sites worden toegevoegd of verwijderd

## Aanvullende bronnen

- [Configuratie van filters met verwijzing naar AEM Headless](/help/headless/deployment/referrer-filter.md)
- [ de Gids van de Configuratie van CORS ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [ Begrijpend Middel dat van de dwars-Oorsprong ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) deelt
- [Edge Delivery Services Forms-documentatie](/help/edge/docs/forms/universal-editor/publish-forms.md)

## Verwante onderwerpen

- [Verzendhandelingen configureren](/help/forms/configuring-submit-actions.md)
- [Forms-verzendservice](/help/forms/forms-submission-service.md)
- [Edge Delivery Services - Overzicht](/help/edge/overview.md)


**heb extra hulp nodig?** Als u problemen blijft ondervinden nadat u deze stappen voor het oplossen van problemen hebt uitgevoerd, neemt u contact op met de klantenondersteuning van Adobe via:

- Uw specifieke foutberichten
- Omgevingsdetails AEM Cloud Service
- **Alle de plaatsdomeinen van Edge Delivery Services** die de toegang van de vormvoorlegging vereisen
- Relevante logbestandvermeldingen op het moment van de fout

**heb extra hulp nodig?** Als u problemen blijft ondervinden nadat u deze stappen voor het oplossen van problemen hebt uitgevoerd, neemt u contact op met de klantenondersteuning van Adobe via:

- Uw specifieke foutberichten
- Omgevingsdetails AEM Cloud Service
- Edge Delivery Services-domeininformatie
- Relevante logbestandvermeldingen op het moment van de fout
