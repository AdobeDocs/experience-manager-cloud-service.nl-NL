---
title: Uitvoeringsfase
description: Uitvoeringsfase
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 4%

---


# Uitvoering {#execution-phase}

Voordat u de uitvoeringsfase start, moet u aan boord zijn van de cloudservice. U moet zich ook vertrouwd maken met Cloud Manager omdat dit het enige mechanisme is voor het implementeren van code op AEM Cloud Service.

Met Cloud Manager kunnen organisaties AEM in de cloud zelf beheren. Het omvat een ononderbroken integratie en ononderbroken levering (CI/CD) kader dat de teams van IT en implementatiepartners de levering van aanpassingen of updates zonder prestaties of veiligheid te compromitteren laat versnellen.

Raadpleeg de volgende bronnen voor meer informatie:

* [Ga aan bij Experience Manager als cloudservice](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/home.html) om zelfhulp-bronnen te begrijpen over instappen voor Experience Manager als cloudservice.

* [Git integreren met Adobe Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) voor meer informatie over het gebruik van een Single Git-opslagplaats voor het implementeren van code.

* [Adobe Experience as a Cloud Service Configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/security/ims-support.html#aem-configuration) to learn about Managing Products and User Access in Admin Console.


## Inleiding {#introduction}

De exacte stappen van uw overgang naar de cloudservice zijn afhankelijk van de systemen die u hebt aangeschaft en de levenscycluspraktijken van de softwareontwikkeling die u volgt.

Het volgende cijfer toont de belangrijkste stappen betrokken bij de uitvoeringsfase:

![image](/help/move-to-cloud-service/assets/exec-image1.png)

## Inhoud overbrengen {#content-transfer}

Als u inhoud van uw huidige AEM-instantie wilt overbrengen naar uw Cloud Service-instantie, kunt u het Adobe Content Transfer Tool gebruiken.

Met dit gereedschap kunt u de gewenste inhoudsubset opgeven die u van uw AEM-broninstantie naar uw AEM Cloud Service-instantie wilt overbrengen.

>[!NOTE]
>U wordt aangeraden regelmatig differentiële toevoegingen aan inhoud uit te voeren om de periode voor het bevriezen van de inhoud voor de laatste differentiële overdracht van inhoud te verkorten voordat u live gaat met de Cloud-service.

Raadpleeg het [gereedschap](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md) Inhoud overbrengen voor meer informatie.

>[!IMPORTANT]
>De minimale systeemvereisten voor Content Transfer Tool zijn AEM 6.3 + en JAVA 8. Als u een lagere AEM-versie gebruikt, moet u de opslagplaats voor inhoud upgraden naar AEM 6.5 om het gereedschap Inhoud overbrengen te kunnen gebruiken.

## Code Refactoring {#code-refactor}

Voor het ontwikkelen en uitvoeren van code in AEM als Cloud Service is een wijziging in de geestesinstelling vereist. Code moet veerkrachtig zijn, vooral omdat een instantie op elk moment kan worden gestopt. Code die wordt uitgevoerd in Cloud Service, moet zich ervan bewust zijn dat deze altijd wordt uitgevoerd in een cluster. Dit betekent dat er altijd meer dan één instantie actief is.

Bepaalde wijzigingen zijn vereist voor AEM Maven-projecten om compatibel te zijn met AEM als cloudservice. AEM als Cloud Service vereist een scheiding van *inhoud* en *code* in afzonderlijke pakketten voor implementatie in AEM.

* `/apps` en `/libs` worden beschouwd als onveranderbare gebieden van AEM omdat deze niet kunnen worden gewijzigd (maken, bijwerken, verwijderen) nadat AEM is gestart (dat wil zeggen tijdens runtime). Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

* Alle andere gegevens in de opslagplaats, `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp` , enz. Dit zijn allemaal veranderbare gebieden, wat betekent dat deze tijdens runtime kunnen worden gewijzigd.

Raadpleeg de [aanbevolen pakketstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure) voor meer informatie.

Er zijn enkele aanvullende ontwikkelrichtlijnen die u moet kennen wanneer u zich ontwikkelt op AEM als cloudservice. Raadpleeg [AEM als richtlijnen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) voor de ontwikkeling van cloudservices voor meer informatie.

Van uw fase van de Planning, zou u een lijst van gebieden moeten hebben die moeten worden gerefactored om met de Dienst van de Wolk compatibel te zijn. U moet ook de [ontwikkelingsrichtlijnen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) raadplegen voor meer informatie over hoe u code kunt wijzigen en optimaliseren om naar Cloud Service te gaan.

Om sommige van uw code te versnellen refactoring taken, kunt u de volgende hulpmiddelen gebruiken:

* [Workflowmigratie van middelen](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Dispatcher Converter](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [Moderniseringsinstrumenten](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

U wordt aangeraden de code lokaal te vernieuwen en te testen voordat u deze via Cloud Manager Git naar een Cloud Service-omgeving verplaatst.

Raadpleeg de documentatie bij [AEM SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk) voor meer informatie.

Hieronder worden enkele aanvullende bronnen weergegeven:

* Bekijk de SDK van Dispatcher installeren om te begrijpen hoe u de SDK van Dispatcher kunt installeren:

   > [!VIDEO](https://video.tv.adobe.com/v/30601)

* Kijk de SDK van Dispatcher configureren om te begrijpen hoe u de SDK van Dispatcher kunt configureren:

   > [!VIDEO](https://video.tv.adobe.com/v/30602)

* Raadpleeg de documentatie bij [Local Development Setup](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) om een lokale ontwikkelomgeving in te stellen


Als u uw doorlopende codeontwikkeling op uw actieve AEM samen met de code het refactoring taak als deel van uw overgangsreis wilt beheren, adviseert men om een periode van de codeschrift te plannen tot u voltooit het herstructureren van uw Maven project om met AEM als Dienst van de Wolk compatibel te zijn.

Zodra, wordt de projectherstructurering gedaan, kunt u nieuwe codeontwikkeling hervatten die op deze nieuwe structuur wordt gebaseerd. Hierdoor worden fouten met de pijplijnen van Cloud Manager tijdens het implementeren en testen van code verminderd.

>[!NOTE]
>De taken Inhoudsoverdracht en Codereflector zijn niet opeenvolgend uitgevoerd. Deze taken kunnen onafhankelijk van elkaar worden uitgevoerd. De juiste projectstructuur is echter vereist om ervoor te zorgen dat de inhoud correct wordt weergegeven in uw cloudservice-omgeving.

## Beste praktijken voor de Plaatsing van de Code en het Testen {#best-practices}

Cloud Manager for Cloud Services-pijplijnuitvoeringen ondersteunen de uitvoering van tests die worden uitgevoerd tegen de werkgebiedomgeving.

Raadpleeg [Codekwaliteitstests](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing) voor meer informatie over het schrijven van testscripts en de aanbevolen dekking van minimaal 50%.

Bovendien, verwijs naar het [Begrip van de Regels](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html) van de Kwaliteit van de Code van de Douane om meer over de kwaliteitsregels te leren van de douanecode die door de Manager van de Wolk worden uitgevoerd die op beste praktijken van de Techniek van AEM wordt gecreeerd.

Het gebruik van Cloud Manager is het enige mechanisme voor het implementeren van code in Cloud Service-omgevingen.

Volg de onderstaande bronnen voor informatie over het gebruik van Cloud Manager voor het beheren en implementeren van uw code.

* [Omgevingen beheren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [Het vormen van uw CI-CD Pijpleiding](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [Uw code implementeren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Aanbevolen procedures voor Go-Live-voorbereiding {#go-live}

Als u een vloeiende en geslaagde live-toepassing op AEM als cloudservice wilt garanderen, kunt u de volgende stappen uitvoeren:

* Code en periode voor het bevriezen van inhoud plannen
* Bovenkant van uiteindelijke inhoud uitvoeren
* Volledige testherhalingen
* Prestaties en beveiligingstests uitvoeren
* Besnoeiing
