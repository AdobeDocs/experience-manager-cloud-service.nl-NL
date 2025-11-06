---
title: Regels voor gegevensbescherming en gegevensbescherming - Adobe Experience Manager as a Cloud Service-gereedheid
description: Meer informatie over Adobe Experience Manager as a Cloud Service-ondersteuning voor de verschillende Data Protection and Data Privacy Regulations en over de manier waarop u aan deze vereisten moet voldoen wanneer u een nieuw AEM as a Cloud Service-project implementeert. Deze verordeningen omvatten de Algemene Verordening van de EU van de Bescherming van Gegevens (GDPR), de Wet van de Consumentenprivacy van Californië.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
feature: Compliance
role: Admin, Developer, Leader
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 1%

---

# Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Voor meer informatie over Adobe antwoorden op privacykwesties, en wat deze reacties voor u als klant van Adobe betekenen, zie [&#x200B; het Centrum van de Privacy van Adobe &#x200B;](https://www.adobe.com/privacy.html).

Om Adobe-klanten te helpen zich aan deze regels te houden, biedt Adobe documentatie en procedures (met API&#39;s, indien beschikbaar) voor de privacybeheerders van de klant en AEM-beheerders:

* De documentatie helpt beheerders gegevensbeveiliging en verzoeken om privacy van gegevens af te handelen.
* De gedocumenteerde procedures laten klanten de regelgevende verzoeken manueel in werking stellen of API vraag maken, waar beschikbaar, van een extern portaal of de dienst.

>[!CAUTION]
>
>De hier gedocumenteerde details zijn beperkt tot Adobe Experience Manager as a Cloud Service.
>
>Gegevens van een andere Adobe On-demand Service, samen met eventuele gerelateerde privacyverzoeken, vereisen dat op die service actie wordt ondernomen.
>
>Voor meer informatie, zie [&#x200B; het Centrum van de Privacy van Adobe &#x200B;](https://www.adobe.com/privacy.html).

## Inleiding {#introduction}

Exemplaren van Adobe Experience Manager as a Cloud Service, en de toepassingen die erop draaien, zijn eigendom van en worden geëxploiteerd door klanten van Adobe.

Bijgevolg vallen gegevensbeschermingsvoorschriften, zoals GDPR, CCPA en andere, grotendeels onder de verantwoordelijkheid van de klanten.

In een korte inleiding bevatten de verordeningen betreffende de privacy en bescherming van gegevens nieuwe regels die moeten worden gevolgd door de taken van:

* Bedrijfsentiteiten (CCPA) en/of gegevensverwerkingsverantwoordelijken (GDPR)

* Dienstverleners (CCPA) en/of gegevensverwerkers (GDPR)

De belangrijkste bepalingen van deze verordeningen zijn:

1. Uitgebreide definitie van persoonsgegevens zodat deze alle unieke id&#39;s omvat, zoals direct en indirect identificeerbare gegevens.

2. Versterking van de toestemmingseisen.

3. Meer aandacht voor verwijderingsrechten (gegevenswissing).

4. Uitschakelen van verkoop van gegevens.

Voor Adobe Experience Manager as a Cloud Service:

* De instanties en toepassingen die erop worden uitgevoerd, zijn eigendom van en worden beheerd door de klant.

   * Eigendom betekent in feite dat de klant de regelgevende taken beheert, waaronder Business Entities en Service Provider, Data Controller en Data Processor.

   * De Adobe Experience Platform Privacy Service maakt geen deel uit van de workflow voor AEM, zoals in het onderstaande diagram wordt geïllustreerd.

* AEM bevat documentatie en procedures waarmee de privacybeheerder van de klant en/of de AEM-beheerder de privacyregelgevingsaanvragen kunnen uitvoeren; handmatig of via API&#39;s, indien beschikbaar.

* Er is geen nieuwe service of interface toegevoegd.

   * In plaats daarvan worden procedures en APIs gedocumenteerd voor gebruik door klant UIs/portals die verzoeken van de privacyverordening behandelen.

* AEM biedt geen kant-en-klare gereedschappen ter ondersteuning van de workflow voor privacyverzoeken.

   * Adobe biedt documentatie en procedures voor de privacybeheerder van de klant, de AEM-beheerder of beide, zodat deze handmatig aanvragen kan uitvoeren die betrekking hebben op de privacyregels.

Adobe biedt procedures voor het verwerken van privacyverzoeken met betrekking tot Access, Delete en Opt-Out voor Adobe Experience Manager as a Cloud Service. In sommige gevallen zijn er API&#39;s beschikbaar die kunnen worden aangeroepen via een door de klant ontwikkeld portaal, of scripts die u helpen met automatisering.

In het volgende diagram ziet u hoe een workflow voor privacyverzoeken eruit kan zien (geïllustreerd met Adobe Experience Manager 6.5):

![&#x200B; de Bescherming van Gegevens en Privacy &#x200B;](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager as a Cloud Service en gereedheid voor regelgeving {#aem-as-a-cloud-service-and-regulatory-readiness}

Zie de volgende secties voor documentatie over regelgeving voor productgebieden van AEM as a Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Zie [&#x200B; Readiness van de Stichting van AEM voor de Regels van de Bescherming van Gegevens en van de Privacy van Gegevens &#x200B;](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager as a Cloud Service-sites {#aem-sites}

Zie [&#x200B; Readiness van AEM Sites voor de Regels van de Bescherming van Gegevens en van de Privacy van Gegevens &#x200B;](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager as a Cloud Service-integratie met Adobe Target en Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Integraties van Adobe Experience Manager as a Cloud Service met Adobe Target en Adobe Analytics worden geïmplementeerd met services die geschikt zijn voor gegevensbescherming en privacy (bijvoorbeeld GDPR). In AEM worden geen persoonsgegevens van Adobe Target of Adobe Analytics met betrekking tot de integratie opgeslagen.
Zie voor meer informatie:

* [&#x200B; Adobe Target - het Overzicht van de Privacy &#x200B;](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/cmp-privacy-and-general-data-protection-regulation.html?lang=nl-NL)

* [&#x200B; Workflow van de Privacy van Gegevens van Adobe Analytics &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html?lang=nl-NL)
