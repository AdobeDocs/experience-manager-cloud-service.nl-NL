---
title: Overzicht van ontwikkelingsagent
description: Leer hoe de Agent van de Ontwikkeling in AEM ontbroken pijpleidingen in Cloud Manager analyseert en logboeken bouwt om codemoeilijke situaties voor te stellen en het zuiveren te versnellen.
feature: Agentic AI, AI Assistant, AI Tools, User Roles
role: User, Admin, Architect, Developer
exl-id: 2194556f-aac2-4cdd-8f7f-00c92c8c4424
source-git-commit: eeaa119711b480197b5807b85eb9c566a735f270
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Overzicht van ontwikkelingsagent {#development-agent-overview}

Met de ontwikkelingsagent kunnen ontwikkelaars en beheerders van AEM code efficiënter maken, debuggen, implementeren en optimaliseren.

Momenteel, kan de agent pijpleidingsstatussen terugwinnen en u helpen het ontbreken oplossen van bouwstijlstappen problemen door moeilijke situaties voor te stellen, bespaart tijd wanneer het zuiveren van de plaatsingen van AEM as a Cloud Service aan ontwikkelings, stadium, en productiemilieu&#39;s. Het onderzoekt bouwlogboeken en verwante code om een moeilijke situatie aan te bevelen die u manueel kunt toepassen.

>[!VIDEO](https://video.tv.adobe.com/v/3478006?quality=12&learn=on)

>[!IMPORTANT]
>
>Door AI gegenereerde reacties kunnen onjuist of misleidend zijn. Controleer de voorgestelde oplossingen en reacties met twee controles.
>
>Zie ook [&#x200B; Generatieve AI de Richtlijnen van de Gebruiker van Adobe Experience Cloud &#x200B;](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

<!-- 
## Cloud Manager Pipeline Troubleshooting  {#cloud-manager-pipeline-troubleshooting}
-->

Om tot deze agent toegang te hebben, verwijs naar de [&#x200B; versienota&#39;s &#x200B;](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs) voor instructies op hoe te in het bètaprogramma inschrijven, en ben zeker om op uw interesse in de Agent van de Ontwikkeling te wijzen. U kunt ook de agent-specifieke terugkoppelen van de Ontwikkeling e-mail aan [&#x200B; aem-devagent@adobe.com &#x200B;](mailto:aem-devagent@adobe.com).

[&#x200B; volg langs een leerprogramma &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/development-agent-troubleshoot-ci-cd-pipeline) om te leren hoe te om de Agent van de Ontwikkeling te gebruiken om pijpleidingsmislukkingen problemen op te lossen.

## Toegang tot de ontwikkelingsagent via Cloud Manager {#how-to-access-the-agent}

U hebt toegang tot de ontwikkelingsagent via de AI-assistent in gebruikersinterfaces, waaronder Cloud Manager of Experience Hub.

**om tot de Agent van de Ontwikkeling door Cloud Manager toegang te hebben:**

1. Om begonnen te worden, klik [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com/#/@foundationinternal/home) om zijn homepage te openen.

   ![&#x200B; Adobe Experience Cloud homepage &#x200B;](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. In het linkerspoor, onder de **rubriek van de Diensten**, klik **Cloud Manager**.

   ![&#x200B; de drop-down lijst die de vooraf ingestelde Schrijver toont van de Inhoud wordt geselecteerd &#x200B;](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >De weergegeven widgets, gereedschappen en artefacten zijn afhankelijk van de persoon van de gebruiker, de rechten en het AEM-implementatietype (AEM as a Cloud Service of Managed Services 6.5/6.5 LTS).

1. In het linkerspoor, onder **Programma**, klik **![pictogram van het Overzicht &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) Overzicht**.

1. Voor de **pagina van het Overzicht van het 0&rbrace; Programma, in de** Pijpleidingen **kaart, klik een pijpleiding.**

   ![&#x200B; Geselecteerde pijpleiding &#x200B;](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-select.png)

1. In de **Bouwstijl en het Scannen van de Code** pagina, neem nota van de ontbroken pijpleiding.

   ![&#x200B; de mislukking van de Pijpleiding zoals gezien in de Bouwstijl en Code het Scannen pagina &#x200B;](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-failure.png)

1. Vlak de hoger-juiste hoek van het gebruikersinterface van AEM (of van de pagina&#39;s van Cloud Manager of de auteursinstantie van de milieu&#39;s van AEM), klik het **AI Hulp** pictogram.

   ![&#x200B; AI Hulp pictogram op de toolbar &#x200B;](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   Zie ook [&#x200B; AI Medewerker in AEM &#x200B;](/help/implementing/cloud-manager/ai-assistant-in-aem.md).

1. In het **AI Medewerker** vakje van de paneeltekst dichtbij de bodem, typ uw vraag of herinnering, dan druk `Enter` of klik ![&#x200B; verzend pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   Bijvoorbeeld:
   *in het &quot;eda-org-01-geen-toegang&quot;programma, analyseer het gebrek aan de &quot;no-access&quot;pijpleiding en los problemen op.*

   De vraag resulteert in de volgende reactie.

   ![&#x200B; AI Hulp herinnering en resulterende reactie &#x200B;](/help/ai-in-aem/agents/development/assets/dev-agent-prompt-response.png)


## Machtigingen {#permissions}

De het oplossen van problemenbaan van de pijpleiding van de Agent van de Ontwikkeling vereist of de Cloud Manager - rol van de Ontwikkelaar of de Cloud Manager - rol van de Manager van het Programma.

## Voorbeeldaanwijzingen {#sample-prompts}

| Vragen | Resultaat |
| --- | --- |
| *los mijn ontbroken pijpleiding* problemen op | Voert een analyse uit van waarom een pijpleiding ontbrak; als het onduidelijk is welke pijpleiding wordt bedoeld, zullen extra vragen aan de gebruiker worden gesteld. |
| *maak een lijst van mijn ontbroken pijpleidingen voor programma HoofdProgramma.* | Terwijl de resultaten kunnen variëren, brengt deze snelle output een lijst van ontbroken pijpleidingen, met een vervolgsuggestie om naar een specifieke pijpleiding te verwijzen om te analyseren. |
| *analyseer mijn ontbroken pijpleiding genoemd &quot;Dev Pijpleiding.&quot;* | Deze herinnering resulteert in een analyse van de ontbroken pijpleiding met suggesties om te bevestigen. Als er meerdere fouten zijn, worden aanvullende vragen gesteld aan de gebruiker. |
| *lost pijpleidingsuitvoering 1234567* problemen op | Door nauwkeurige identiteitskaart van de pijpleidingsuitvoering te verstrekken, wordt een pijpleidingsanalyse uitgevoerd. |

## Functies buiten bereik {#out-of-scope-features}

Het oplossen van problemen van de pijpleiding werkt op de de bouwstijlstap van de full-Stack pijpleiding. Voor andere pijpleidingstypes en stappen, zuivert mislukkingen door het downloaden en inspecteren van de logboeken.

Zie [&#x200B; Logboeken van de Toegang en van de Download &#x200B;](/help/implementing/cloud-manager/manage-logs.md).
