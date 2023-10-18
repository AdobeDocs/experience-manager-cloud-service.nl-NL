---
title: Wat is cache voor adaptieve formulieren? en hoe een AEM adaptief formulier in cache te plaatsen?
description: De Adaptive Forms-cache is ontworpen voor Adaptive Forms en voor documenten met als doel de tijd die nodig is om een adaptief formulier of document te genereren te verkorten.
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
source-git-commit: 5e02cf36112ce29cd3ebfd772623654328598bf2
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Adaptieve Forms-cache configureren {#configure-adaptive-forms-cache}

Een cache is een mechanisme om de toegangstijd voor gegevens te verkorten, de latentie te verminderen en de invoer-/uitvoersnelheid (I/O) te verbeteren. In de Adaptive Forms-cache worden alleen de HTML-inhoud en de JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier op de client te genereren, verkort. Het is speciaal ontworpen voor Adaptive Forms.

## Adaptieve Forms-cache configureren bij auteur- en publicatieinstanties {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://[server]:[port]/system/console/configMgr`.
1. Klikken **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om de configuratiewaarden te bewerken.
1. In de [!UICONTROL edit configuration values] het maximale aantal formulieren op of documenteert een exemplaar van de AEM [!DNL Forms Server] kan in het cachegeheugen **[!UICONTROL Number of Adaptive Forms]** veld. De standaardwaarde is 100.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Number Adaptive Forms in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

   ![Configuratiedialoogvenster voor Adaptive Forms HTML-cache](assets/cache-configuration-edit.png)

1. Klikken **[!UICONTROL Save]** om de configuratie op te slaan.

Uw omgeving is geconfigureerd voor het gebruik van cacheadaptieve Forms en gerelateerde elementen.


## (Optioneel) Adaptief formuliercache configureren bij Dispatcher {#configure-the-cache}

U kunt ook Adaptief in cache plaatsen van formulieren configureren bij Dispatcher voor een extra prestatieverhoging.

### Voorwaarden {#pre-requisites}

* De optie [samenvoegen of vooraf invullen van gegevens op de client](prepopulate-adaptive-form-fields.md#prefill-at-client) -optie. Hiermee kunt u unieke gegevens samenvoegen voor elk exemplaar van een vooraf ingevuld formulier.
* [Een uitlijningsagent inschakelen voor elke publicatie-instantie](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en#invalidating-dispatcher-cache-from-a-publishing-instance). Het helpt betere caching prestaties voor Adaptive Forms te bereiken. De standaard-URL van spoelmiddelen is `http://[server]:[port]]/etc/replication/agents.publish/flush.html`.

### Overwegingen bij het in cache plaatsen van Adaptive Forms op een Dispatcher {#considerations}

* Wanneer u de Adaptive Forms-cache gebruikt, gebruikt u de AEM [!DNL Dispatcher] om clientbibliotheken (CSS en JavaScript) van een adaptief formulier in cache te plaatsen.
* Zorg dat de Adaptive Forms-cache uitgeschakeld blijft wanneer u aangepaste componenten ontwikkelt op de server die voor ontwikkeling wordt gebruikt.
* URL&#39;s zonder extensie worden niet in de cache opgeslagen. Bijvoorbeeld URL met patroon `/content/forms/[folder-structure]/[form-name].html` worden in cache geplaatst en worden URL&#39;s met een patroon genegeerd `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content`. Gebruik dus URL&#39;s met extensies om de voordelen van caching te benutten.
* Overwegingen voor gelokaliseerde adaptieve Forms:
   * URL-indeling gebruiken `http://host:port/content/forms/af/<afName>.<locale>.html` een gelokaliseerde versie van een adaptief formulier aanvragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`
   * Uitschakelen met landinstelling browser <!-- [Disable using browser locale](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) -->voor URL&#39;s met opmaak `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wanneer u URL-indeling gebruikt `http://host:port/content/forms/af/<adaptivefName>.html`, en **[!UICONTROL Use Browser Locale]** in configuratiemanager is uitgeschakeld, wordt de niet-gelokaliseerde versie van het adaptieve formulier weergegeven. De niet-gelokaliseerde taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier. De landinstelling die is geconfigureerd voor uw browser (landinstelling browser) wordt niet in overweging genomen en er wordt een niet-gelokaliseerde versie van het Adaptief formulier weergegeven.
   * Wanneer u URL-indeling gebruikt `http://host:port/content/forms/af/<adaptivefName>.html`, en **[!UICONTROL Use Browser Locale]** in Configuration Manager is ingeschakeld, wordt een gelokaliseerde versie van het Adaptive Form beschikbaar gesteld. De taal van het gelokaliseerde Adaptieve formulier is gebaseerd op de landinstelling die is geconfigureerd voor uw browser (landinstelling browser). Het kan leiden tot [alleen de eerste instantie van een adaptief formulier in cache plaatsen]. Als u wilt voorkomen dat het probleem op uw exemplaar optreedt, raadpleegt u [problemen oplossen](#only-first-insatnce-of-adptive-forms-is-cached).

### Het in cache plaatsen van Dispatcher inschakelen

Voer de onderstaande stappen uit, zodat u het in cache plaatsen van Adaptieve Forms op Dispatcher kunt inschakelen en configureren:

1. Open volgende URL voor elk publiceer geval van uw milieu en vorm de replicatieagent:
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [Voeg het volgende toe aan uw dispatcher.any-bestand](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#automatically-invalidating-cached-files):

   ```JSON
      /invalidate
      {
      /0000
      {
      /glob "*"
      /type "deny"
      }
      /0001
      {
      # Consider all HTML files stale after an activation.
      /glob "*.html"
      /type "allow"
      }
      /0002
      {
      # Exclude htmls present in AF directories
      /glob "/content/forms/**/*.html"
      /type "deny"
      }
   ```

   Wanneer u het bovenstaande toevoegt:

   * Een adaptief formulier blijft in cache totdat een bijgewerkte versie van het formulier niet wordt gepubliceerd.

   * Wanneer een nieuwere versie van een bron waarnaar in een adaptief formulier wordt verwezen, wordt gepubliceerd, wordt het beïnvloede adaptieve formulier automatisch ongeldig gemaakt. Er zijn enkele uitzonderingen op de automatische ongeldigmaking van bronnen waarnaar wordt verwezen. Zie voor meer informatie over uitzonderingen de [problemen oplossen](#troubleshooting) sectie.
1. [Voeg het onderstaande bestand met regels dispatcher.any of aangepaste regels toe](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#specifying-the-documents-to-cache). De URL&#39;s die caching niet ondersteunen, worden uitgesloten. Bijvoorbeeld interactieve communicatie.

   ```JSON
      /0000 {
            /glob "*"
            /type "allow"
      }
      ## Don't cache csrf login tokens
      /0001 {
            /glob "/libs/granite/csrf/token.json"
            /type "deny"
      }
      ## Don't cache IC - print channel
      /0002 {
            /glob "/content/forms/**/channels/print.html"
            /type "deny"
      }
      ## Don't cache IC - web channel
      /0003 {
            /glob "/content/forms/**/channels/web.html"
            /type "deny"
      }
   ```

1. [De volgende parameters toevoegen aan de lijst met URL-parameters negeren](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#ignoring-url-parameters):

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Uw AEM omgeving is geconfigureerd om Adaptive Forms in cache te plaatsen. Alle typen Adaptive Forms worden in het cachegeheugen opgeslagen. Als u toegangsmachtigingen voor gebruikers voor een pagina moet controleren voordat u de pagina in de cache aflevert, raadpleegt u [caching, beveiligde inhoud](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html).

## Problemen oplossen {#troubleshooting}

### Sommige Adaptive Forms-afbeeldingen of video&#39;s worden niet automatisch ongeldig gemaakt in de Dispatcher-cache {#videos-or-images-not-auto-invalidated}

#### Probleem {#issue1}

Wanneer u afbeeldingen of video&#39;s selecteert en toevoegt via de middelenbrowser aan een adaptief formulier en deze worden bewerkt in de Middelen-editor, worden deze elementen niet automatisch ongeldig gemaakt in de Dispatcher-cache.

#### Oplossing {#Solution1}

Nadat u de afbeeldingen en video hebt gepubliceerd, maakt u de publicatie van de Adaptive Forms die naar deze elementen verwijst, expliciet ongedaan en publiceert u deze.

### Bepaalde adaptieve Forms met inhoudsfragmenten of ervaringsfragmenten worden niet automatisch ongeldig gemaakt uit de Dispatcher-cache {#content-or-experience-fragment-not-auto-invalidated}

#### Probleem {#issue2}

Wanneer u een inhoudsfragment of een Ervingsfragment toevoegt aan een adaptief formulier en deze elementen onafhankelijk worden bewerkt en gepubliceerd, wordt Adaptive Forms met deze elementen niet automatisch ongeldig gemaakt uit de Dispatcher-cache.

#### Oplossing {#Solution2}

Nadat u een bijgewerkt inhoudsfragment of ervaringsfragment hebt gepubliceerd, publiceert en publiceert u de Adaptieve Forms die deze elementen gebruikt, expliciet.

### Alleen de eerste instantie van een adaptief formulier wordt in de cache geplaatst{#only-first-insatnce-of-adptive-forms-is-cached}

#### Probleem {#issue3}

Wanneer de Adaptive Form URL geen lokalisatiegegevens heeft, en **[!UICONTROL Use Browser Locale]** in de configuratiemanager wordt toegelaten. Er wordt een gelokaliseerde versie van het adaptieve formulier verzonden en alleen de eerste instantie van het adaptieve formulier wordt in de cache opgeslagen en aan elke volgende gebruiker bezorgd.

#### Oplossing {#Solution3}

1. Open conf.d/httpd-dispatcher.conf of een ander configuratiebestand dat is geconfigureerd om te laden tijdens runtime.

1. Voeg de volgende code toe aan het bestand en sla deze op. Dit is een voorbeeldcode die u kunt aanpassen aan uw omgeving.

```XML
   <VirtualHost *:80>
        # Set log level high during development / debugging and then turn it down to whatever is appropriate
    LogLevel rewrite:trace6
        # Start Rewrite Engine
    RewriteEngine On
        # Handle actual URL convention (just pass through)
        RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
 
        # Handle selector based redirection basded on browser language
        # The Rewrite Cond(ition) is looking for the Accept-Lanague header and if found takes the first two characters which most likely is the desired language selector.
        RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
        RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
   </VirtualHost>
```



>[!MORELIKETHIS]
>
>* [Problemen met caching oplossen voor as a Cloud Service AEM Forms](/help/forms/troubleshooting-caching-performance.md)