---
title: '[!DNL Experience Manager Assets] integration with  [!DNL Adobe Workfront]'
description: Inleiding aan integratie tussen  [!DNL Assets]  en  [!DNL Workfront]
role: Admin, Leader, Architect
feature: Workfront Integrations and Apps
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [!DNL Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. Dankzij de integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid en tijd-aan-markt van inhoud verbeteren door het werk en het beheer van digitale elementen intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

De aanbiedingen van de Adobe aan [ integreren  [!DNL Workfront]  en  [!DNL Adobe Experience Manager Assets]  (het steunen van Assets Essentials en Assets as a Cloud Service) ](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html).

Met de geïntegreerde native Experience Manager kunt u:

* Snel de integratie in Workfront instellen.

* Automatisch mappen maken die zijn gekoppeld tussen Workfront en Experience Manager.

* Metagegevens voor bestaande gekoppelde elementen eenvoudig synchroniseren.

* Werk automatisch projectmeta-gegevens bij wanneer het in Workfront wordt veranderd.

* Maak vloeiend verbinding tussen verschillende Experience Manager Assets-opslagruimten en één Workfront-omgeving of verschillende Workfront-omgevingen met één Experience Manager Assets-opslagplaats voor alle organisatie-id&#39;s.


## Adobe Workfront for Experience Manager Enhanced Connector {#enhanced-connector-information}


Vanaf juni 2022 heeft Adobe een nieuwe native integratie uitgebracht voor de aansluiting van Workfront op Adobe Experience Manager Assets as a Cloud Service. Deze integratie is de vereiste methode geworden om deze twee oplossingen aan te sluiten. Elke toekomstige nieuwe implementatie van de verbeterde connector (1.9.8 en hoger) om Workfront aan te sluiten op AEM Assets as a Cloud Service wordt geblokkeerd. Voor meer informatie over hoe te om deze integratie te plaatsen, zie [ de as a Cloud Service integratie van Experience Manager Assets ](workfront-connector-configure.md) vormen.

>[!NOTE]
>
>Adobe biedt geen ondersteuning voor het gebruik van de Workfront voor parallel geïntegreerde aansluiting en Experience Manager met verbeterde Experience Manager.

Voor installaties vóór juni 2022 zijn de volgende punten van belang voor de implementatie en configuratie van [!DNL Adobe Workfront for Experience Manager enhanced connector] :

* Voor Adobe is implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] vereist. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt het niet gesteund door Adobe.
* Adobe kan updates aan [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze schakelaar overtollig maken; als dit voorkomt, kunnen klanten worden vereist om van het gebruik van deze schakelaar over te gaan.
* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, zie stap 5 (a) van [ verbeterde instructies van de schakelaarinstallatie ](workfront-connector-install.md).
* Zie [ de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar ](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen ](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).[