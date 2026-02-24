---
title: Verbinding maken met Microsoft Translator
description: Leer hoe u AEM kunt verbinden met Microsoft Translator, offline, om uw vertaalworkflow te automatiseren.
feature: Language Copy
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="van toepassing op AEM Sites)."
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
solution: Experience Manager Sites
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Verbinding maken met Microsoft Translator {#connecting-to-microsoft-translator}

AEM verstrekt een ingebouwde schakelaar voor [&#x200B; Vertaler van Microsoft &#x200B;](https://www.microsoft.com/en-us/translator/business/) om paginainhoud of activa te vertalen. Nadat u van Microsoft een licentie hebt verkregen voor het gebruik van Microsoft Translator, configureert u de connector volgens de instructies op deze pagina.

>[!TIP]
>
>Als u aan het vertalen van inhoud nieuw bent, zie [&#x200B; de Vertaalreis van 0&rbrace; Plaatsen, die geleid weg door uw inhoud van AEM Sites te vertalen gebruikend de krachtige vertaalhulpmiddelen van AEM, ideaal voor die zonder AEM of vertaalervaring.](/help/journey-sites/translation/overview.md)

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud wordt de toewijzing naast vertaalde tekst weergegeven, bijvoorbeeld `Translations by Microsoft` |
| Workspace-id | (Optioneel) De id van de aangepaste Microsoft Translator-engine die u wilt gebruiken |
| Subscription Key | Je Microsoft Subscription Key voor Microsoft Translator |

De volgende procedure leidt tot een configuratie van de Vertaler van Microsoft.

1. In het [&#x200B; navigatievenster &#x200B;](/help/sites-cloud/authoring/basic-handling.md#first-steps), uitgezochte **Hulpmiddelen** > **de Diensten van de Wolk** > **de Diensten van de Wolk van de Vertaling**.
1. Navigeer naar de plaats waar u de configuratie wilt creëren. Normaal gesproken bevindt dit zich in de hoofdmap van de site of kan het een algemene standaardconfiguratie zijn.
1. Selecteer **creeer** knoop.
1. Definieer uw configuratie.
   1. Selecteer **Vertaler van Microsoft** in drop-down.
   1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van de Diensten van de Wolk en in de drop-down lijsten van het paginabezit.
   1. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat.

   ![&#x200B; creeer vertaalconfiguratie &#x200B;](../assets/create-translation-config.png)

1. Klik **creëren**.
1. In **geef het venster van de Configuratie** uit, verstrek de waarden voor de vertaaldienst die in de vorige lijst wordt beschreven.

   ![&#x200B; geef vertaalconfiguratie &#x200B;](../assets/msft-config-ui.png) uit

1. Selecteer **verbinden** om de verbinding te verifiëren.
1. Selecteer **sparen &amp; Sluiten**.

## De configuraties van de vertaalservice publiceren {#publishing-the-translator-service-configurations}

Als definitieve stap, gelieve uw configuraties van de Vertaler van Microsoft te publiceren om gepubliceerde vertaalde inhoud te steunen, gebruikend [&#x200B; het publiceren van een boom &#x200B;](/help/sites-cloud/authoring/sites-console/publishing-pages.md#publishing-and-unpublishing-a-tree) actie.
