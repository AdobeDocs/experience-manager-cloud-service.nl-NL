---
title: '[!DNL Experience Manager Assets] integratie met  [!DNL Adobe Workfront]'
description: Inleiding aan integratie tussen  [!DNL Assets]  en  [!DNL Workfront]
role: Admin, Leader, Developer
feature: Workfront Integrations and Apps
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [!DNL Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. Dankzij de integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid en tijd-aan-markt van inhoud verbeteren door het werk en het beheer van digitale elementen intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

Adobe biedt aan [&#x200B; te integreren  [!DNL Workfront]  en  [!DNL Adobe Experience Manager Assets]  (het steunen van de Hoofdzaak van Activa en Assets as a Cloud Service) &#x200B;](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html?lang=nl-NL).

Met de native Experience Manager-integratie kunt u:

* Snel de integratie in Workfront instellen.

* Automatisch mappen maken die zijn gekoppeld tussen Workfront en Experience Manager.

* Metagegevens voor bestaande gekoppelde elementen eenvoudig synchroniseren.

* Werk automatisch projectmeta-gegevens bij wanneer het in Workfront wordt veranderd.

* Maak vloeiend verbinding tussen verschillende Experience Manager Assets-opslagruimten en één Workfront-omgeving of verschillende Workfront-omgevingen met één Experience Manager Assets-opslagplaats voor alle organisatie-id&#39;s.


## Adobe Workfront for Experience Manager Enhanced Connector {#enhanced-connector-information}


Vanaf juni 2022 heeft Adobe een nieuwe native integratie uitgebracht voor de aansluiting van Workfront op Adobe Experience Manager Assets as a Cloud Service. Deze integratie is de vereiste methode geworden om deze twee oplossingen aan te sluiten. Elke toekomstige nieuwe implementatie van de verbeterde connector (1.9.8 en hoger) voor de verbinding van Workfront met AEM Assets as a Cloud Service wordt geblokkeerd. Voor meer informatie over hoe te opstelling deze integratie, zie [&#x200B; de integratie van Experience Manager Assets as a Cloud Service &#x200B;](workfront-connector-configure.md) vormen.

>[!NOTE]
>
>Adobe biedt geen ondersteuning voor het parallel gebruiken van de Workfront for Experience Manager Enhanced Connector en Experience Manager integration.

Voor installaties vóór juni 2022 zijn de volgende punten van belang voor de implementatie en configuratie van [!DNL Adobe Workfront for Experience Manager enhanced connector] :

* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] . Indien geïmplementeerd en geconfigureerd zonder een gecertificeerde partner of [!DNL Adobe Professional Services] , wordt dit niet ondersteund door Adobe.
* Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze connector redundant maken. Als dit gebeurt, kunnen klanten worden gevraagd over te stappen van het gebruik van deze connector.
* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, zie stap 5 (a) van [&#x200B; verbeterde instructies van de schakelaarinstallatie &#x200B;](workfront-connector-install.md).
* Zie [&#x200B; de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar &#x200B;](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen [.](https://express.adobe.com/page/Tc7Mq6zLbPFy8/)