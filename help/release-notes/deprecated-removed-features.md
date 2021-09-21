---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release specifiek voor vervangen en verwijderde functies in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 8294709d6c5685fd5b88a52835b4082e3e713a51
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 5%

---

# Verouderde en verwijderde functies {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Vervangen en verwijderde functies in AEM als Cloud Service"
>abstract="AEM als Cloud Service heeft een implementatiemodel in de cloud. Bepaalde mogelijkheden en functies zijn vervangen door in de cloud geïntegreerde tegenhangers en op dit tabblad worden die functies weergegeven."


Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies. Aangezien [!DNL Adobe Experience Manager] als [!DNL Cloud Service] een implementatiemodel in de cloud biedt, zijn ook bepaalde mogelijkheden en functies vervangen door in de cloud geïntegreerde tegenhangers.

Om de aanstaande verwijdering/vervanging van [!DNL Experience Manager] mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Verouderde mogelijkheden blijven beschikbaar maar worden niet verder uitgebreid.
1. Capabilities waarvan is aangekondigd dat ze zullen worden afgekeurd, worden ten vroegste in de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als verouderd in [!DNL Experience Manager] als [!DNL Cloud Service] zijn gemerkt. Functies die in een toekomstige versie moeten worden verwijderd, worden doorgaans eerst vervangen door een alternatief.

Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Mogelijkheden | Verouderde functie | Vervanging |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | Eenvoudige inhoudsfragmenten op basis van een sjabloon. | [Op modellen gebaseerde gestructureerde ](/help/assets/content-fragments/content-fragments-models.md) inhoudsfragmentatie. |
| [!DNL Assets] | `DAM Asset Update` werkwijze voor het verwerken van opgenomen afbeeldingen. | Bij het opnemen van bedrijfsmiddelen worden nu [assetmicroservices](/help/assets/asset-microservices-overview.md) gebruikt. |
| [!DNL Assets] | Upload elementen rechtstreeks naar [!DNL Experience Manager]. Zie [API&#39;s voor het uploaden van afgekeurde elementen](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Gebruik [Directe binaire upload](/help/assets/add-assets.md). Voor technische details, zie [directe upload APIs](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bepaalde workflowstepsin-](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) workflowworkflows worden niet ondersteund, zoals het aanroepen van opdrachtregelprogramma&#39;s  `DAM Asset Update`   [!DNL ImageMagick]. | [De ](/help/assets/asset-microservices-overview.md) microservices van bedrijfsmiddelen bieden een vervanging voor veel workflows. Voor aangepaste verwerking gebruikt u [nabewerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | MPEG-transcodering van video&#39;s. | Gebruik [Asset microservices](/help/assets/asset-microservices-overview.md) voor het genereren van miniaturen in MPEG. Gebruik [Dynamic Media](/help/assets/manage-video-assets.md) voor MPEG-transcodering. |
| [!DNL Foundation] | De replicatie UI van de boom onder het &quot;Distribute&quot;lusje van de replicatieagent (verwijdering na 30 September, 2021) | [Workflowbenaderingen ](/help/operations/replication.md#manage-publication) voor de structuur van de  [ ](/help/operations/replication.md#publish-content-tree-workflow) inhoudsstructuur beheren |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit [!DNL Experience Manager] met [!DNL Experience Manager] als [!DNL Cloud Service].

| Gebied | Functie | Vervanging |
| ------------ | ------------------ | ----------- |
| Gebruikersinterface | De klassieke gebruikersinterface wordt verwijderd uit de gebruikersinterface van het product. Een paar Klassieke dialogen UI zijn beschikbaar voor een paar uitgezochte mogelijkheden, zoals de Controleur van de Verbinding, de Leegmaken van de Versie, en sommige configuraties van de Cloud Service. De komende [productupdates](/help/release-notes/home.md) kunnen Klassieke beschikbaarheid van UI verder verwijderen. | Standaardinterface |
| [!DNL Dynamic Media] | Eerdere integraties met [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) en [Dynamic Media Hybrid mode](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic) zijn niet beschikbaar in [!DNL Experience Manager] als [!DNL Cloud Service]. | Gebruik [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) als [!DNL Cloud Service] meegeleverd bij [!DNL Experience Manager]. |
| [!DNL Sites] | Portal Director en Portlet-component | Deze mogelijkheden zijn verouderd in [!DNL Experience Manager] 6.4 en zijn nu verwijderd uit [!DNL Experience Manager]. |
| [!DNL Sites] | Design Importer | Deze mogelijkheid is verwijderd omdat onveranderlijke gedeelten van de [!DNL Experience Manager]-opslagruimte niet toegankelijk zijn tijdens runtime. |
| [!DNL Assets] | [!DNL Assets] delen met Marketing Cloud Assets Core Service en Creative Cloud services is niet beschikbaar. | Gebruik [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) voor integratie met [!DNL Adobe Creative Cloud]. |
| [!DNL Foundation] | Ondersteuning voor Apache Sling-gegevensbronnen (OSGi bundle org.apache.sling.datasource). | N.v.t. |

## Java API {#java-api}

Zie [deze pagina](/help/release-notes/deprecated-apis.md) voor verouderde of verwijderde Java API&#39;s, die soms worden geïntroduceerd.

## OSGI-configuratie {#osgi-configuration}

Zie [dit artikel](/help/implementing/deploying/osgi-configuration-api.md) voor om het even welke beperkingen rond configuratie van eigenschappen OSGI, waarvan sommige in tijd kunnen worden geïntroduceerd.
