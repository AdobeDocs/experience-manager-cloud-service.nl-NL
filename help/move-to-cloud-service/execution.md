---
title: Uitvoeringsfase
description: Uitvoeringsfase
translation-type: tm+mt
source-git-commit: 0dd05c1f6dc197daf154d4df6e6661e00455b233
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 100%

---


# Uitvoering {#execution-phase}

Voordat u de uitvoeringsfase start, moet u het onboardingproces voor Cloud Service hebben afgerond. U moet zich ook vertrouwd maken met Cloud Manager omdat dit het enige mechanisme is voor het implementeren van code op AEM Cloud Service.

Met Cloud Manager kunnen organisaties AEM in de cloud helemaal zelf beheren. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid.

Raadpleeg de volgende bronnen voor meer informatie:

* [Onboarding bij Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/home.html) laat u kennismaken met zelfhulpbronnen voor onboarding bij Experience Manager as a Cloud Service.

* [Git integreren met Adobe Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) biedt informatie over het gebruik van een Single Git-repository voor het implementeren van code.

* [Adobe Experience as a Cloud Service-configuratie](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/security/ims-support.html#aem-configuration) biedt informatie over het beheer van producten en gebruikerstoegang in Admin Console.


## Inleiding {#introduction}

De exacte stappen van uw overgang naar Cloud Service zijn afhankelijk van de systemen die u hebt aangeschaft en de levenscyclusprocedures voor softwareontwikkeling die u volgt.

De volgende afbeelding toont de belangrijkste stappen in de uitvoeringsfase:

![afbeelding](/help/move-to-cloud-service/assets/exec-image1.png)

## Overdracht van content {#content-transfer}

Als u content van uw huidige AEM-instantie wilt overbrengen naar uw Cloud Service-instantie, kunt u de Adobe Content Transfer-tool gebruiken.

Hiermee geeft u precies aan welke subset van content moet worden overgedragen van uw AEM-broninstantie naar uw AEM Cloud Service-instantie.

>[!NOTE]
>We raden u aan om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.

Raadpleeg [De tool Content Transfer](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md) voor meer informatie.

>[!IMPORTANT]
>De minimale systeemvereisten voor de Content Transfer-tool zijn AEM 6.3 + en JAVA 8. Bij lagere versies van AEM moet u de content-repository upgraden naar AEM 6.5 om de tool Content Transfer te gebruiken.

## Herstructurering van code {#code-refactor}

Voor het ontwikkelen en uitvoeren van code in AEM as a Cloud Service is een speciale denkwijze vereist. Code moet robuust en veerkrachtig zijn, vooral omdat een instantie op elk moment kan worden gestopt. Code in Cloud Service moet &#39;beseffen&#39; dat deze altijd in een cluster wordt uitgevoerd. Dit betekent dat er altijd meer dan één instantie actief is.

Bepaalde wijzigingen zijn vereist voor AEM Maven-projecten om compatibel te zijn met AEM as a Cloud Service. AEM as a Cloud Service vereist dat *content* en *code* in afzonderlijke pakketten van elkaar worden gescheiden voor implementatie in AEM.

* `/apps` en `/libs` worden beschouwd als onveranderbare gebieden van AEM omdat deze niet kunnen worden gewijzigd (maken, bijwerken, verwijderen) nadat AEM is gestart (dat wil zeggen tijdens runtime). Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

* Alle andere items in de repository, `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`, enz. zijn veranderbaar, wat betekent dat ze tijdens de uitvoering kunnen worden gewijzigd.

Raadpleeg de [aanbevolen pakketstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure) voor meer informatie.

Er zijn enkele aanvullende ontwikkelingsrichtlijnen die u moet kennen wanneer u code ontwikkelt voor AEM as a Cloud Service. Raadpleeg [Ontwikkelingsrichtlijnen voor AEM as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) voor meer informatie.

Van uw planningsfase zou u een lijst met gebieden moeten hebben waarbij herstructurering is vereist om compatibiliteit met Cloud Service te garanderen. Bekijk ook de [ontwikkelingsrichtlijnen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) voor meer informatie over hoe u code kunt wijzigen en optimaliseren voor de overgang naar Cloud Service.

Gebruik de volgende tools om de herstructurering van uw code sneller uit te voeren:

* [Asset Workflow Migration](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Dispatcher Converter](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [Moderniseringstools](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

U wordt aangeraden de code lokaal te herstructureren en te testen voordat u deze via Cloud Manager Git naar een Cloud Service-omgeving verplaatst.

Raadpleeg de documentatie bij [AEM SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk) voor meer informatie.

Hieronder worden enkele aanvullende bronnen weergegeven:

* Bekijk de video over het installeren van de Dispatcher SDK voor uitleg:

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Bekijk de video over het configureren van de Dispatcher SDK voor meer informatie over het configureren:

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

* Raadpleeg de [Local Development Setup](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)-documentatie om een lokale ontwikkelomgeving op te stellen


Om de doorlopende codeontwikkeling op uw actieve AEM en de herstructurering van code als onderdeel van uw overgangstraject beter te beheren, adviseren we een &#39;bevriesperiode&#39; voor code in te plannen tot u klaar bent met de herstructurering van uw Maven-project en het project compatibel is met AEM as a Cloud Service.

Zodra de projectherstructurering is voltooid, kunt u starten met de ontwikkeling van nieuwe code die op deze nieuwe structuur wordt gebaseerd. Hierdoor treden minder fouten op in de Cloud Manager-pipeline tijdens het implementeren en testen van code.

>[!NOTE]
>De overdracht van content en de herstructurering van code hoeven niet opeenvolgend worden uitgevoerd. Deze taken kunnen onafhankelijk van elkaar worden uitgevoerd. De juiste projectstructuur is echter vereist om ervoor te zorgen dat de content correct wordt weergegeven in uw Cloud Service-omgeving.

## Best practices voor het implementeren en testen van code {#best-practices}

Cloud Manager for Cloud Services-pipeline-uitvoeringen ondersteunen de uitvoering van tests die worden uitgevoerd voor de stagingomgeving.

Raadpleeg [Codekwaliteitstests](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing) voor meer informatie over het schrijven van testscripts en de aanbevolen dekking van minimaal 50%.

Of raadpleeg [Inzicht in aangepaste regels voor codekwaliteit](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html) voor meer informatie over de kwaliteitsregels voor aangepaste code die wordt uitgevoerd door Cloud Manager. Deze regels zijn gebaseerd op de best practices van AEM Engineering.

Cloud Manager is het enige mechanisme voor het implementeren van code in Cloud Service-omgevingen.

Volg de onderstaande bronnen voor informatie over het gebruik van Cloud Manager voor het beheren en implementeren van uw code.

* [Omgevingen beheren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [De CI/CD-pipeline configureren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [Uw code implementeren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Best practices voor Go-Live-voorbereiding {#go-live}

Voor een vloeiende en geslaagde Go-Live van AEM as a Cloud Service voert u de volgende stappen uit:

* &#39;Bevriesperiode&#39; voor code en content inplannen
* De content een laatste keer aanvullen
* Testiteraties voltooien
* Prestatie- en beveiligingstests uitvoeren
* Snelle overstap
