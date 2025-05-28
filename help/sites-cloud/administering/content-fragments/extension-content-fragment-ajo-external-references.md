---
title: De extensie Externe referenties van AJO voor inhoudsfragmenten gebruiken
description: Meer informatie over de extensie Externe referenties van het inhoudsfragment AJO
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
source-git-commit: f755a5c621b68b3110642e6cfe150798555b6707
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---


# De extensie Externe referenties van het inhoudsfragment AJO {#content-fragment-external-references-extension}

Als u een voorbeeld wilt bekijken van ervaringen met AEM op een ander Adobe-product, kunt u de extensie voor de gebruikersinterface inschakelen:

* **Externe Verwijzingen van AJO**

De extensie Externe referenties van AJO werkt door verwijzingen naar inhoudsfragment op te halen uit alle organisaties en sandboxen die aan vooraf gedefinieerde tags zijn gekoppeld. In de extensie worden vervolgens details weergegeven.

Voor een integratie met Adobe Journey Optimizer (AJO) zijn de details bijvoorbeeld afhankelijk van het feit of de verwijzing een campagne, een reis of een sjabloon is.

>[!NOTE]
>
>Voor details van hoe te om de uitbreiding toe te laten, zie [ Extension Manager in AEM Experience Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

Als u bijvoorbeeld de extensie wilt gebruiken met AJO:

>[!NOTE]
>
>Zie ook [ de Integratie van AJO ](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/integrations/aem-fragments).

1. Open de [ Console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console).

1. Navigeer naar het inhoudsfragment - het fragment dat is gemaakt en dat wordt gebruikt via verschillende AJO-kanalen.

1. Open uw Fragment van de Inhoud in de [ redacteur ](/help/sites-cloud/administering/content-fragments/managing.md#editing-the-content-of-your-fragment).

1. De extensie Externe AJO-verwijzingen is beschikbaar als een tabblad in het rechterdeelvenster. Selecteer het tabblad waarop u de extensie wilt openen:

   ![ de Externe uitbreiding van Verwijzingen van AJO ](/help/sites-cloud/administering/content-fragments/assets/cf-ajo-fragment-external-references-extension.png)

   Nadat een referentietype is geselecteerd, worden de bijbehorende externe verwijzingen als een tabel met de kolommen weergegeven:

   * **Naam**: de naam van de verwijzing waar het fragment van de Inhoud wordt gebruikt
   * **de Voorproef** selecteert deze verbinding om de voorproef te beginnen
   * **Status**: het statuut van de verwijzing

1. U kunt het **Type van Verwijzing** van drop-down selecteren om tussen drie verwijzingstypes te schakelen:

   * **Campagne**
      * Hiermee geeft u een lijst weer van alle campagnes met koppelingen naar het huidige inhoudsfragment.
      * Vervolgens kunt u een voorvertoning van een geselecteerde campagne weergeven.
      * Standaard
   * **Reis**
      * Hiermee geeft u de laatste reis weer.
      * Vervolgens kunt u een geselecteerde Reis selecteren en hiervan een voorvertoning weergeven.
   * **Malplaatje**
      * Hier worden sjablonen weergegeven die betrekking hebben op het inhoudsfragment.
      * Vervolgens kunt u een geselecteerde sjabloon selecteren en hiervan een voorvertoning weergeven.