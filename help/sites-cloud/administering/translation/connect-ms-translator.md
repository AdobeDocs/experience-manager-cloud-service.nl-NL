---
title: Verbinding maken met Microsoft Translator
description: Leer hoe u AEM kunt verbinden met Microsoft Translator vanuit de verpakking om uw vertaalworkflow te automatiseren.
feature: Language Copy
role: Admin
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Verbinding maken met Microsoft Translator {#connecting-to-microsoft-translator}

AEM verstrekt een ingebouwde schakelaar voor [ Vertaler van Microsoft ](https://www.microsoft.com/en-us/translator/business/) om paginainhoud of activa te vertalen. Nadat u van Microsoft een licentie hebt verkregen voor het gebruik van Microsoft Translator, configureert u de connector volgens de instructies op deze pagina.

>[!TIP]
>
>Als u aan het vertalen van inhoud nieuw bent, zie [&#128279;](/help/journey-sites/translation/overview.md) de Vertaalreis van 0&rbrace; Plaatsen, die geleid weg door uw inhoud van AEM Sites te vertalen gebruikend AEM krachtige vertaalhulpmiddelen, ideaal voor die zonder AEM of vertaalervaring.

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud wordt de toewijzing naast vertaalde tekst weergegeven, bijvoorbeeld `Translations by Microsoft` |
| Workspace-id | (Optioneel) De id van de aangepaste Microsoft Translator-engine die u wilt gebruiken |
| Subscription Key | Je Microsoft Subscription Key voor Microsoft Translator |

De volgende procedure leidt tot een configuratie van de Vertaler van Microsoft.

1. In het [ navigatievenster ](/help/sites-cloud/authoring/basic-handling.md#first-steps), uitgezochte **Hulpmiddelen** > **Cloud Servicen** > **Cloud Servicen van de Vertaling**.
1. Navigeer naar de plaats waar u de configuratie wilt creëren. Normaal gesproken bevindt dit zich in de hoofdmap van de site of kan het een algemene standaardconfiguratie zijn.
1. Selecteer **creeer** knoop.
1. Definieer uw configuratie.
   1. Selecteer **Vertaler van Microsoft** in drop-down.
   1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van Cloud Servicen en in de drop-down lijsten van het paginabezit.
   1. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat.

   ![ creeer vertaalconfiguratie ](../assets/create-translation-config.png)

1. Klik **creëren**.
1. In **geef het venster van de Configuratie** uit, verstrek de waarden voor de vertaaldienst die in de vorige lijst wordt beschreven.

   ![ geef vertaalconfiguratie ](../assets/msft-config-ui.png) uit

1. Selecteer **verbinden** om de verbinding te verifiëren.
1. Selecteer **sparen &amp; Sluiten**.

## De configuraties van de vertaalservice publiceren {#publishing-the-translator-service-configurations}

Als definitieve stap, gelieve uw configuraties van de Vertaler van Microsoft te publiceren om gepubliceerde vertaalde inhoud te steunen, gebruikend [ het publiceren van een boom ](/help/sites-cloud/authoring/sites-console/publishing-pages.md#publishing-and-unpublishing-a-tree) actie.
