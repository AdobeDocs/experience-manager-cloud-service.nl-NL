---
title: Fase na Go-Live
description: Fase na Go-Live
exl-id: f9b0b2fa-e29c-4faa-a5e7-e5edd04b25ca
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 63%

---

# Na Go-Live {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="AEM"
>abstract="De beste praktijken van het overzicht voor ononderbroken ontwikkeling en beheert logboeken samen met hulpmiddelen zoals de console &amp; CRXDE Lite van de Ontwikkelaar om met het oplossen van problemenkwesties met AEM te helpen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html" text="Logbestanden openen en beheren"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools" text="AEM als instrumenten voor de ontwikkeling van Cloud Servicen"


In de fase na Go-Live moet u ervoor zorgen dat tijdelijke bestanden worden opgeschoond. Het is ook tijd om de best practices te evalueren voor continue ontwikkeling en voor het beheer van de logbestanden.

De volgende tools zijn handig om problemen met AEM as a Cloud Service op te lossen:

* **Developer Console**
* **CRX/DE Lite**
* **Tool voor beheren van logbestanden**


## Developer Console {#developer-console}

Foutopsporing van AEM as a Cloud Service-ontwikkelomgevingen is beschikbaar in de Developer Console voor ontwikkelings-, stage- en productieomgevingen.

Raadpleeg [Implementeren voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools) voor meer informatie over ontwikkelingstools.

## CRX/DE Lite {#crxde-lite}

Als gebruiker hebt u toegang tot CRX/DE Lite in de ontwikkellingsomgeving, maar niet in de stage- of productieomgeving.

>[!IMPORTANT]
>Het schrijven naar onveranderlijke repository&#39;s zoals `/libs` en `/apps` tijdens uitvoering resulteert in fouten. Bovendien hebt u als klant geen toegang tot ontwikkelaarstools voor staging- en productieomgevingen.

Raadpleeg [Ontwikkelen met CRX/DE Lite](/help/implementing/developing/tools/crxde.md) voor meer informatie over het ontwikkelen van uw AEM-applicatie met gebruik van CRX/DE Lite.

## Logbestanden beheren {#managing-logs}

Gebruikers hebben toegang tot een lijst met beschikbare logbestanden voor de geselecteerde omgeving.

Raadpleeg [Logbestanden openen en beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) voor meer informatie over het openen en beheren van logbestanden via de gebruikersinterface of met de API via Cloud Manager.

### Aanvullende ondersteuning {#additional-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Help en ondersteuning"
>abstract="Neem contact op met ons AEM ondersteuningsteam om uitleg te krijgen of om eventuele zorgen weg te nemen."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Ondersteuning voor Experience Cloud"

Als u vragen over toegang tot Cloud Service hebt, contacteer uw vertegenwoordiger van de Adobe of [Steun voor Experience Cloud](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) voor meer details.
