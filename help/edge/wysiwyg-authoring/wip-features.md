---
title: Functies voor onderhanden werk-sites voor Edge Delivery Services
description: Ontdek welke AEM Sites-functies en gebruiksscenario's momenteel worden gebruikt en ontdek alternatieve oplossingen wanneer u Edge Delivery Services gebruikt.
solution: Experience Manager Sites
feature: Edge Delivery Services
role: User
exl-id: 21745f53-a7ef-4eec-9170-b267c2f4314e
source-git-commit: 92da26452438f2b56cdec1aecc76587d4982f00e
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Functies voor onderhanden werk-sites voor Edge Delivery Services {#wip-sites-features}

Ontdek welke AEM Sites-functies en gebruiksscenario&#39;s momenteel worden gebruikt en ontdek alternatieve oplossingen wanneer u Edge Delivery Services gebruikt.

>[!TIP]
>
>Werk in uitvoering betekent niet het einde van de weg. Neem contact op met uw Adobe als u een functie nodig hebt of een kwestie wilt gebruiken die in dit document als werk in uitvoering wordt vermeld. U en Adobe kunnen samenwerken om uw specifieke behoeften te begrijpen en alternatieve oplossingen te vinden.

## Onderhanden werk-eigenschappen {#wip-features}

Als u Edge Delivery Services gebruikt met AEM Sites, zijn de meeste Sites-functies beschikbaar. Bijvoorbeeld, bijna om het even welke actie beschikbaar in de [ Console van Plaatsen ](/help/sites-cloud/authoring/sites-console/introduction.md) is van toepassing op Edge Delivery Services.

Sommige functies zijn echter in uitvoering. De eigenschappen van WIP zijn eigenschappen van de console van Plaatsen die of nog niet beschikbaar voor Edge Delivery Services met AEM Sites of slechts gedeeltelijk beschikbaar zijn. Daarom kunnen de eigenschappen van het WIP verschillend worden voorgesteld dan hun Plaatsen tegenhangers of er kunnen alternatieve oplossingen voor het gebruiksgeval zijn.

De volgende lijst stelt dergelijke eigenschappen van WIP en afwisselende oplossingen voor. Als voor uw project een WIP-functie nodig is, bekijkt u de hieronder voorgestelde alternatieven en vraagt u de Adobe om samen te werken om uw gebruiksscenario te begrijpen.

| Functie Sites | Status in Edge | Notities | Edge-documentatie |
|---|---|---|---|
| [ Overerving van de Pagina ](/help/sites-cloud/administering/msm-and-translation.md) | Beschikbaar |  | [ Overerving van de Inhoud in de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [ Overerving van de Component ](/help/sites-cloud/administering/msm-and-translation.md) | Gedeeltelijk beschikbaar | Componenten nemen inhoud over, maar overerving kan alleen op paginaniveau worden ongedaan gemaakt | [ Overerving van de Inhoud in de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [ Exemplaar van de Taal ](/help/sites-cloud/administering/translation/overview.md) | Gedeeltelijk beschikbaar | Componenten nemen inhoud over, maar overerving kan alleen op paginaniveau worden ongedaan gemaakt | [ Overerving van de Inhoud in de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [ Multisite Beheer van de Plaats ](/help/sites-cloud/administering/msm/overview.md) | Gedeeltelijk beschikbaar | Componenten nemen inhoud over, maar overerving kan alleen op paginaniveau worden ongedaan gemaakt | [ Overerving van de Inhoud in de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [ Lanceringen ](/help/sites-cloud/authoring/launches/overview.md) | Gedeeltelijk beschikbaar | Componenten nemen inhoud over, maar overerving kan alleen op paginaniveau worden ongedaan gemaakt | [ Overerving van de Inhoud in de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [Paginasjablonen](/help/sites-cloud/authoring/page-editor/templates.md) | Gedeeltelijk beschikbaar | Pagina&#39;s die met sjablonen zijn gemaakt, zijn onafhankelijke kopieën van de oorspronkelijke sjabloon. | [ Gebruikend de Malplaatjes van de Pagina met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/templates.md) |
| [ de Hub en het richten van de context ](/help/sites-cloud/authoring/personalization/overview.md) | Niet beschikbaar |  |  |
| [ Timewarp ](/help/sites-cloud/authoring/launches/preview.md) | Niet beschikbaar |  |  |
| [ Verwante Inhoud ](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#associated-content-browser) | Niet beschikbaar |  |  |
| [Ervaringsfragmenten](/help/sites-cloud/authoring/fragments/experience-fragments.md) | Alternatief | Een pagina maken en een fragmentcomponent gebruiken |  |

## Gebruiksgevallen van onderhanden werk {#wip-use-cases}

Omdat de Edge Delivery Services op een volledig nieuwe en moderne technologiestapel worden voortgebouwd, zijn de volgende gebruiksgevallen van AEM Sites nog niet volledig behandeld en zijn werk in ontwikkeling. Als voor uw project een WIP-gebruiksscenario nodig is, neemt u contact op met de Adobe om samen te werken en inzicht te krijgen in de behoeften van uw project.

| Hoofdlettergebruik voor sites | Details |
|---|---|
| Logica aan de serverzijde om pagina&#39;s te renderen | AEM runtime gebruiken als toepassingsserver |
| Dynamische pagina&#39;s | SSI of een dynamische include-techniek |
| Gebruikersbeheer | AEM gebruiken als IdP |
| Verificatie | AEM gebruiken voor beveiligde inhoud |
| Inhoud toestaan | AEM als veilig extranet |
