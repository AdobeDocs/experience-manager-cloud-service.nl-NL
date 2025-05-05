---
title: Relatie van activa
description: Leer hoe u digitale elementen die gemeenschappelijke kenmerken delen, koppelt. Maak ook bronafhankelijke relaties tussen digitale elementen met behulp van asset-relaties.
role: User
feature: Collaboration,Asset Management
solution: Experience Manager, Experience Manager Assets
exl-id: 89149283-bbf2-40d3-9a4c-5b27ff5f944e
source-git-commit: 41ac6c5c18d1acb094f1107bd4a477df058ea55a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Relatie van activa {#related-assets}

Met [!DNL Adobe Experience Manager Assets] kunt u elementen handmatig koppelen op basis van de behoeften van uw organisatie met behulp van de functie voor verwante elementen. U kunt bijvoorbeeld een licentiebestand koppelen aan een element of aan een afbeelding/video over een vergelijkbaar onderwerp. U kunt elementen die bepaalde algemene kenmerken delen, aan elkaar koppelen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen. Als u bijvoorbeeld een PDF-bestand hebt dat is gegenereerd vanuit een INDD-bestand, kunt u het PDF-bestand koppelen aan het INDD-bronbestand.

Met deze functie hebt u de flexibiliteit om een PDF-bestand of JPG-bestand met een lage resolutie te delen met leveranciers of agentschappen en het INDD-bestand met een hoge resolutie alleen op verzoek beschikbaar te maken.

>[!NOTE]
>
>Alleen gebruikers met bewerkingsmachtigingen voor elementen kunnen de elementen releren en de relatie tussen de elementen verbreken.

## Stappen om elementen te koppelen {#steps-to-relate-assets}

1. Open vanuit de interface [!DNL Experience Manager] de pagina **[!UICONTROL Properties]** voor een element dat u wilt koppelen.

   ![ open de pagina van de Eigenschappen van activa om de activa ](assets/asset-properties-relate-assets.png) met elkaar in verband te brengen

1. Om andere activa met de activa te relateren u selecteerde, klik **[!UICONTROL Asset Relations]** ![ met elkaar verband houdende activa ](assets/do-not-localize/link-relate.png).
1. Voer een van de volgende handelingen uit:

   * Als u het bronbestand voor het element wilt koppelen, selecteert u **[!UICONTROL Add Source]** in de lijst. U kunt slechts één element als bron koppelen.
   * Selecteer **[!UICONTROL Add Derived]** in de lijst als u een afgeleid bestand wilt koppelen. U kunt meerdere elementen in deze categorie koppelen.
   * Selecteer **[!UICONTROL Add Other]** in de lijst om een relatie in twee richtingen tussen de elementen te maken. U kunt meerdere elementen in deze categorie koppelen.

1. Navigeer in het **[!UICONTROL Select Assets]** -scherm naar de locatie van het element dat u wilt koppelen en selecteer het. U kunt één enkel middel tegelijkertijd of veelvoudige activa selecteren door de verschuivingssleutel te houden terwijl het klikken, die om het even welke [ gesteunde dossierformaten in de Mening van Assets ](/help/assets/supported-file-formats-assets-view.md) kan omvatten.

   ![ voeg verwante activa ](assets/add-related-asset.png) toe

1. Klik op **[!UICONTROL Select]**. Afhankelijk van uw keuze voor relatie in stap 3 wordt het gerelateerde element weergegeven onder een van de juiste categorieën in de sectie **[!UICONTROL Asset Relations]** . Als het element dat u hebt verwant bijvoorbeeld het bronbestand voor het huidige element is, wordt het weergegeven onder **[!UICONTROL Source]** .

   ![ Assets relatievoorbeeld ](assets/asset-relations-example.png)

1. Klik **[!UICONTROL Unrelate]** ![ losse activa ](assets/do-not-localize/link-unrelate-icon.png) beschikbaar voor alle verwante activa in elke sectie ([!UICONTROL Source], [!UICONTROL Derived], en [!UICONTROL Other]) om activa niet-met elkaar in verband te brengen.

## Gerelateerde elementen vertalen {#translating-related-assets}

Het maken van bron-/afgeleide relaties tussen elementen met behulp van de functie voor gerelateerde elementen is ook handig in vertaalworkflows. Wanneer u een vertaalworkflow uitvoert op een afgeleid element, haalt [!DNL Experience Manager Assets] automatisch elk element op waarnaar het bronbestand verwijst en dat het voor vertaling bevat. Op deze manier wordt het element waarnaar door het bronelement wordt verwezen, samen met de bron en afgeleide elementen omgezet. Als het bronbestand verwant is aan een ander element, haalt [!DNL Experience Manager Assets] het element waarnaar wordt verwezen op en wordt het opgenomen voor vertaling.

Zie [ activa in AEM ](/help/assets/translate-assets.md) vertalen.

## Volgende stappen {#next-steps}

* Feedback geven op het product met de optie [!UICONTROL Feedback] die beschikbaar is in de gebruikersinterface van de Assets-weergave

* Verstrek documentatie terugkoppelt gebruikend [!UICONTROL Edit this page] ![ uitgeeft de pagina ](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![ creeer een kwestie GitHub ](assets/do-not-localize/github-issue.png) beschikbaar op juiste sidebar

* De Zorg van de Klant van het contact [&#128279;](https://experienceleague.adobe.com/nl?support-solution=General#support)

>[!MORELIKETHIS]
>
>* [ de versies van de Mening van activa ](/help/assets/manage-organize-assets-view.md#view-versions)
>* [ vertaalde activa in AEM ](/help/assets/translate-assets.md)
>* [ Ondersteunde Formaten van het Dossier in de Mening van Assets ](/help/assets/supported-file-formats-assets-view.md).
