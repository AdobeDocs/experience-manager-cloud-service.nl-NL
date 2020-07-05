---
title: Fase na Go-Live
description: Fase na Go-Live
translation-type: ht
source-git-commit: 0565d053b6040bc99ae79823711d56eb9aecdfb3
workflow-type: ht
source-wordcount: '242'
ht-degree: 100%

---


# Na Go-Live {#post-go-live}

In de fase na Go-Live moet u ervoor zorgen dat tijdelijke bestanden worden opgeschoond. Het is ook tijd om de best practices te evalueren voor continue ontwikkeling en voor het beheer van de logbestanden.

De volgende tools zijn handig om problemen met AEM as a Cloud Service op te lossen:

* **Developer Console**
* **CRX/DE Lite**
* **Tool voor beheren van logbestanden**


## Developer Console {#developer-console}

Foutopsporing van AEM as a Cloud Service-ontwikkelomgevingen is beschikbaar in de Developer Console voor ontwikkelings-, stage- en productieomgevingen.

Raadpleeg [Implementeren voor AEM as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools) voor meer informatie over ontwikkelingstools.

## CRX/DE Lite {#crxde-lite}

Als gebruiker hebt u toegang tot CRX/DE Lite in de ontwikkellingsomgeving, maar niet in de stage- of productieomgeving.

>[BELANGRIJK]
>Het schrijven naar onveranderlijke repository&#39;s zoals `/libs` en `/apps` tijdens uitvoering resulteert in fouten. Bovendien hebt u als klant geen toegang tot ontwikkelaarstools voor staging- en productieomgevingen.

Raadpleeg [Ontwikkelen met CRX/DE Lite](https://docs.adobe.com/help/en/experience-manager-65/developing/devtools/developing-with-crxde-lite.html) voor meer informatie over het ontwikkelen van uw AEM-applicatie met gebruik van CRX/DE Lite.

## Logbestanden beheren {#managing-logs}

Gebruikers hebben toegang tot een lijst met beschikbare logbestanden voor de geselecteerde omgeving.

Raadpleeg [Logbestanden openen en beheren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) voor meer informatie over het openen en beheren van logbestanden via de gebruikersinterface of met de API via Cloud Manager.

### Aanvullende ondersteuning {#additional-support}

Als u vragen hebt over toegang tot Cloud Service, neemt u contact op met uw Adobe-vertegenwoordiger of de Adobe AEM CQ-ondersteuningsportal.
