---
title: Hartelijk dank voor EDS Forms configureren
description: Leer hoe u pagina's voor bedankt kunt configureren en omleiding kunt geven voor EDS Forms om de gebruikerservaring te optimaliseren en gebruikersreizen te stroomlijnen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e2970c7a141025222c6b119787142e7c39d453af
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Pagina&#39;s bedankt configureren en omleiden configureren in Adaptieve Forms-blokken

Dank u pagina&#39;s en omleiding zijn essentiële aspecten van de verbetering van de gebruikerservaring, die gebruikers van bevestiging, duidelijke mededeling, en vlotte navigatie voorzien na de verzending van het formulier.

## Pagina&#39;s met bedankt configureren

Dank u pagina&#39;s dienen als geruststellende erkenning aan gebruikers en laten organisaties toe om essentiële informatie mee te delen terwijl het versterken van merkidentiteit. Voer de volgende stappen uit om een pagina voor bedankt voor EDS Forms te configureren:

1. Open uw AEM Edge Delivery-projectmap op Microsoft SharePoint of Google Workspace.
1. Maak een Microsoft Word- of Google Docs-bestand met de naam &quot;thankyou&quot; in de projectmap.
1. Voeg uw dank toe aan het bestand &quot;dankuwel&quot;.
   ![Voorbeeld van een pagina voor bedankt](/help/edge/assets/sample-thankyou-page.png)
1. Gebruik AEM Sidekick om een voorvertoning van het &quot;thankyou&quot;-bestand te bekijken en dit te publiceren.

## Gebruikers omleiden na verzending

Omleiding vergemakkelijkt naadloze gebruikersreizen door gebruikers naar relevante bestemmingen te leiden, de betrokkenheid te optimaliseren en de conversietarieven te verhogen.

Standaard leidt het blok Adaptive Forms de gebruikers om naar de pagina &quot;thanku&quot;. Als u gebruikers wilt omleiden naar een andere pagina dan de standaardpagina &quot;Thanku&quot;, hebt u twee opties:

* de bestaande pagina &quot;Bedankt&quot; vervangen door een andere pagina, of
* leidt u de pagina &quot;bedankt&quot; om naar een andere pagina van uw keuze.

### De bestaande &quot;thankyou&quot;-pagina vervangen

1. Open &quot;[EDS-project]/blocks/form/form.js&quot;.
1. Wijzig de `thankyou` pagina in de volgende regel naar keuze:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Bijvoorbeeld:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Zorg ervoor dat er een pagina met dezelfde naam aanwezig is in uw Edge Delivery Service-projectmap op de Microsoft SharePoint- of Google Workspace. Als de pagina niet bestaat, gaat u verder en publiceert u deze.

1. Ga aan controle in de bijgewerkte omslag &#39;form.js&#39; en zijn onderliggende dossiers aan uw project van de Dienst van de Levering van de Rand op GitHub te werk. Deze update zorgt ervoor dat het formulier nu naar de opgegeven bijgewerkte pagina wordt omgeleid.

1. Zorg ervoor dat de pagina in uw EDS-projectmap bestaat en publiceer deze.


### Omleiding website gebruiken

Configureer een omleiding van een website om de pagina &quot;Thankyou&quot; naar een andere pagina te sturen. Zie de [Documentatie omleiden](https://www.aem.live/docs/redirects) voor gedetailleerde instructies.


