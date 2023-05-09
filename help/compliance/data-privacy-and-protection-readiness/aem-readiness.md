---
title: Regels voor gegevensbescherming en gegevensbescherming - Adobe Experience Manager as a Cloud Service-gereedheid
description: Meer informatie over Adobe Experience Manager as a Cloud Service-ondersteuning voor de verschillende Data Protection and Data Privacy Regulations; met inbegrip van de algemene gegevensbeschermingsverordening van de EU (GDPR), de California Consumer Privacy Act en de wijze waarop een nieuw AEM as a Cloud Service project moet worden uitgevoerd.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: acd80887d71a528604d37fa2787bca3c3a48d7c4
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 1%

---

# Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over de regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Voor meer informatie over Adobe aan privacykwesties, en dit betekent voor u als klant van de Adobe, zie [Adobe](https://www.adobe.com/privacy.html).

Adobe verschaft documentatie en procedures (met API&#39;s, indien beschikbaar), zodat de privacybeheerder van de klant of AEM beheerder verzoeken om gegevensbescherming en privacy van gegevens kan verwerken en onze klanten kunnen helpen zich aan deze regels te houden. De gedocumenteerde procedures zullen klanten toestaan om de regelgevende verzoeken manueel of door in APIs uit te voeren, waar beschikbaar, van een extern portaal of een dienst uit te voeren.

>[!CAUTION]
>
>De hier gedocumenteerde details zijn beperkt tot Adobe Experience Manager as a Cloud Service.
>
>Voor gegevens van een andere Adobe On-demand-dienst, samen met eventuele privacyverzoeken, moeten maatregelen worden genomen met betrekking tot die dienst.
>
>Zie voor meer informatie [Adobe](https://www.adobe.com/privacy.html).

## Inleiding {#introduction}

Exemplaren van Adobe Experience Manager as a Cloud Service, en de toepassingen die op hen lopen, zijn eigendom van en werken door onze klanten.

Bijgevolg vallen gegevensbeschermingsvoorschriften, zoals GDPR, CCPA en andere, grotendeels onder de verantwoordelijkheid van de klanten.

In een zeer korte inleiding bevatten de verordeningen betreffende de privacy en bescherming van gegevens nieuwe regels die moeten worden gevolgd door de taken van:

* Bedrijfsentiteiten (CCPA) en/of gegevensverwerkingsverantwoordelijken (GDPR)

* Dienstverleners (CCPA) en/of gegevensverwerkers (GDPR)

De belangrijkste bepalingen van deze verordeningen zijn:

1. Uitgebreide definitie van persoonsgegevens zodat deze alle unieke id&#39;s omvat; zoals in direct en indirect identificeerbare gegevens.

2. Versterkte toestemmingsvereisten.

3. Meer aandacht voor verwijderingsrechten (gegevensgummetje).

4. Uitschakelen van verkoop van gegevens.

Voor Adobe Experience Manager as a Cloud Service:

* De instanties en toepassingen die erop worden uitgevoerd, zijn eigendom van en worden beheerd door de klant.

   * Dit betekent in feite dat de klant de regelgevende taken beheert, waaronder Business Entities en Service Provider, Data Controller en Data Processor.

   * De Adobe Experience Platform Privacy Service zal geen deel uitmaken van de workflow voor AEM, zoals in het onderstaande diagram wordt geïllustreerd.

* AEM bevat documentatie en procedures voor de privacybeheerder en/of AEM beheerder van de klant om de verzoeken om privacyregelgeving uit te voeren; handmatig of via API&#39;s, indien beschikbaar.

* Er is geen nieuwe service of interface toegevoegd.

   * In plaats daarvan worden procedures en APIs gedocumenteerd voor gebruik door klant UIs/portals die verzoeken van de privacyverordening behandelen.

* AEM bevat geen out-of-the-box tools ter ondersteuning van de workflow voor privacyverzoeken.

   * Adobe zal documentatie en procedures voor de de privacybeheerder en/of AEM van de klant verstrekken, toelatend hen om verzoeken met betrekking tot de privacyverordeningen manueel uit te voeren.

Adobe biedt procedures voor de behandeling van privacyverzoeken met betrekking tot Access, Delete en Opt-Out voor Adobe Experience Manager as a Cloud Service. In sommige gevallen zijn er API&#39;s beschikbaar die kunnen worden aangeroepen via een door de klant ontwikkeld portaal of scripts om te helpen met automatisering.

In het volgende diagram ziet u hoe een workflow voor privacyverzoeken eruit kan zien (geïllustreerd met Adobe Experience Manager 6.5):

![Gegevensbescherming en privacy](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager as a Cloud Service en gereedheid voor regelgeving {#aem-as-a-cloud-service-and-regulatory-readiness}

Zie de volgende secties voor documentatie over regelgeving voor productgebieden van AEM as a Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Zie [Gereedheid van AEM stichting voor gegevensbeveiliging en gegevensprivacyverordeningen](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager as a Cloud Service-sites {#aem-sites}

Zie [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager as a Cloud Service-integratie met Adobe Target en Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Deze Adobe Experience Manager as a Cloud Service-integratie is mogelijk met services die geschikt zijn voor gegevensbescherming en privacy (bijvoorbeeld GDPR). Er worden geen persoonsgegevens van Adobe Target of Adobe Analytics in AEM opgeslagen met betrekking tot de integratie.
Zie voor meer informatie:

* [Adobe Target - Overzicht van privacy](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/cmp-privacy-and-general-data-protection-regulation.html)

* [Adobe Analytics Data Privacy Workflow](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html)
