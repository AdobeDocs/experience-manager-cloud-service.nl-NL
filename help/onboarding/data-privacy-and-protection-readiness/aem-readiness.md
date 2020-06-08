---
title: Regels voor gegevensbescherming en gegevensbescherming - Adobe Experience Manager als voorbereiding op de cloudservice
description: 'Meer informatie over Adobe Experience Manager als ondersteuning voor de verschillende Data Protection and Data Privacy Regulations; met inbegrip van de algemene gegevensbeschermingsverordening van de EU (GDPR), de California Consumer Privacy Act en de wijze waarop een nieuwe AEM als Cloud Service-project moet worden geïmplementeerd. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 1%

---


# Adobe Experience Manager als Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over de regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Meer informatie over het antwoord van Adobe op privacy-problemen en wat dit voor u als Adobe-klant betekent, vindt u in het Privacy Center [van](https://www.adobe.com/privacy.html)Adobe.

Adobe biedt documentatie en procedures (met API&#39;s, indien beschikbaar), waarmee de privacybeheerder van de klant of de AEM-beheerder gegevensbeschermings- en privacyverzoeken kan verwerken en waarmee onze klanten aan deze regels kunnen voldoen. De gedocumenteerde procedures zullen klanten toestaan om de regelgevende verzoeken manueel of door in APIs uit te voeren, waar beschikbaar, van een extern portaal of een dienst uit te voeren.

>[!CAUTION]
>
>De hier beschreven details zijn beperkt tot Adobe Experience Manager als Cloud Service.
>
>Voor gegevens van een andere Adobe On-demand-service, samen met eventuele privacyverzoeken, moeten acties op die service worden ondernomen.
>
>Zie het Privacy Center [van](https://www.adobe.com/privacy.html)Adobe voor meer informatie.

## Inleiding {#introduction}

Exemplaren van Adobe Experience Manager als Cloud Service en de toepassingen die erop worden uitgevoerd, zijn eigendom van en worden beheerd door onze klanten.

Bijgevolg vallen gegevensbeschermingsvoorschriften, zoals GDPR, CCPA en andere, grotendeels onder de verantwoordelijkheid van de klanten.

In een zeer korte inleiding bevatten de verordeningen betreffende de privacy en bescherming van gegevens nieuwe regels die moeten worden gevolgd door de taken van:

* Bedrijfsentiteiten (CCPA) en/of gegevensverwerkingsverantwoordelijken (GDPR)

* Dienstverleners (CCPA) en/of gegevensverwerkers (GDPR)

De belangrijkste bepalingen van deze verordeningen zijn:

1. Uitgebreide definitie van persoonsgegevens zodat deze alle unieke id&#39;s omvat; zoals in direct en indirect identificeerbare gegevens.

2. Versterkte toestemmingsvereisten.

3. Meer aandacht voor verwijderingsrechten (gegevensgummetje).

4. Uitschakelen van verkoop van gegevens.

Voor Adobe Experience Manager als cloudservice:

* De instanties en toepassingen die erop worden uitgevoerd, zijn eigendom van en worden beheerd door de klant.

   * Dit betekent in feite dat de klant de regelgevende taken beheert, waaronder Business Entities en Service Provider, Data Controller en Data Processor.

   * De Adobe Experience Platform Privacy Service maakt geen deel uit van de workflow voor AEM, zoals in het onderstaande diagram wordt geïllustreerd.

* AEM omvat documentatie en procedures voor de privacybeheerder van de klant en/of de beheerder van AEM om de verzoeken van de privacyverordening uit te voeren; handmatig of via API&#39;s, indien beschikbaar.

* Er is geen nieuwe service of interface toegevoegd.

   * In plaats daarvan worden procedures en APIs gedocumenteerd voor gebruik door klant UIs/portals die verzoeken van de privacyverordening behandelen.

* AEM zal geen uit-van-de-doos hulpmiddelen omvatten om het privacyverzoekwerkschema te steunen.

   * Adobe verstrekt documentatie en procedures voor de de privacybeheerder van de klant en/of beheerder AEM, toelatend hen om verzoeken met betrekking tot de privacyverordeningen manueel uit te voeren.

Adobe biedt procedures voor het verwerken van privacyverzoeken met betrekking tot Access, Delete en Opt-Out voor Adobe Experience Manager als Cloud Service. In sommige gevallen zijn er API&#39;s beschikbaar die kunnen worden aangeroepen via een door de klant ontwikkeld portaal of scripts om te helpen met automatisering.

In het volgende diagram ziet u hoe een workflow voor privacyverzoeken eruit kan zien (geïllustreerd met Adobe Experience Manager 6.5):

![Gegevensbescherming en privacy](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager als Cloud Service en Regelgeving {#aem-as-a-cloud-service-and-regulatory-readiness}

Zie de volgende secties voor documentatie over regelgeving voor productgebieden van AEM als Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

See [AEM Foundation Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager as a Cloud Service-sites {#aem-sites}

See [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager als Cloud Service-integratie met Adobe Target en Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Deze Adobe Experience Manager als integratie met de Cloud Service is mogelijk met services die geschikt zijn voor gegevensbescherming en privacy (bijvoorbeeld GDPR). Er worden geen persoonlijke gegevens van Adobe Target of Adobe Analytics opgeslagen in AEM met betrekking tot de integratie.
Zie voor meer informatie:

* [Adobe Target - Overzicht van privacy](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics Data Privacy Workflow](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
