---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release die specifiek zijn voor vervangen en verwijderde functies in [!DNL Adobe Experience Manager] als [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: bbd8277fc5ed81bc656900ec3a993630aa5ffad5
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 5%

---

# Verouderde en verwijderde functies {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Vervangen en verwijderde functies in AEM as a Cloud Service"
>abstract="AEM as a Cloud Service heeft een implementatiemodel in de cloud. Bepaalde mogelijkheden en functies zijn vervangen door in de cloud geïntegreerde tegenhangers en op dit tabblad worden die functies weergegeven."


Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies. Ook, als [!DNL Adobe Experience Manager] als [!DNL Cloud Service] biedt een implementatiemodel in de cloud, bepaalde mogelijkheden en functies zijn vervangen door in de cloud geïntegreerde tegenhangers.

De aanstaande verwijdering/vervanging van [!DNL Experience Manager] vermogens zijn de volgende regels van toepassing :

1. Aankondiging van afkeuring komt voorop. Verouderde mogelijkheden blijven beschikbaar maar worden niet verder uitgebreid.
1. Capabilities waarvan is aangekondigd dat ze zullen worden afgekeurd, worden ten vroegste in de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in [!DNL Experience Manager] als [!DNL Cloud Service]. Functies die in een toekomstige versie moeten worden verwijderd, worden doorgaans eerst vervangen door een alternatief.

Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Mogelijkheden | Verouderde functie | Vervanging |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | Eigenschappen van Experience Fragments voor **Status van sociale media**. | De functie wordt binnenkort verwijderd. |
| [!DNL Sites] | Eenvoudige inhoudsfragmenten op basis van een sjabloon. | [Op modellen gebaseerde gestructureerde inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md) nu. |
| [!DNL Assets] | `DAM Asset Update` werkwijze voor het verwerken van opgenomen afbeeldingen. | Bij gebruik van middelen [assetmicroservices](/help/assets/asset-microservices-overview.md) nu. |
| [!DNL Assets] | Elementen rechtstreeks uploaden naar [!DNL Experience Manager]. Zie [verouderde API&#39;s voor middelenupload](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Gebruiken [Direct binair uploaden](/help/assets/add-assets.md). Voor technische details, zie [directe upload-API&#39;s](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bepaalde workflowstappen](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) in `DAM Asset Update` werkstroom wordt niet ondersteund, inclusief het aanroepen van opdrachtregelprogramma&#39;s zoals [!DNL ImageMagick]. | [Middelenmicroservices](/help/assets/asset-microservices-overview.md) bieden een vervanging voor veel workflows. Gebruik voor aangepaste verwerking [nabewerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | MPEG-transcodering van video&#39;s. | Gebruik voor het genereren van miniaturen in MPEG [Middelenmicroservices](/help/assets/asset-microservices-overview.md). Gebruik voor MPEG-transcodering [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | De replicatie UI van de boom onder het &quot;Distribute&quot;lusje van de replicatieagent (verwijdering na 30 September, 2021) | [Publicatie beheren](/help/operations/replication.md#manage-publication) of [workflow voor publicatiestructuur](/help/operations/replication.md#publish-content-tree-workflow) benaderingen |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit [!DNL Experience Manager] with [!DNL Experience Manager] als [!DNL Cloud Service].

| Gebied | Functie | Vervanging |
| ------------ | ------------------ | ----------- |
| Gebruikersinterface | De klassieke gebruikersinterface wordt verwijderd uit de gebruikersinterface van het product. Een paar Klassieke dialogen UI zijn beschikbaar voor een paar uitgezochte mogelijkheden, zoals de Controleur van de Verbinding, de Leegmaken van de Versie, en sommige configuraties van de Cloud Service. Binnenkort [productupdates](/help/release-notes/home.md) kan de beschikbaarheid van de klassieke gebruikersinterface verder verwijderen. | Standaardinterface |
| [!DNL Dynamic Media] | Eerdere integratie met [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) en [Dynamic Media Hybride, modus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic) niet beschikbaar in [!DNL Experience Manager] als [!DNL Cloud Service]. | Gebruiken [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) verstrekt [!DNL Experience Manager] als [!DNL Cloud Service]. |
| [!DNL Sites] | Portal Director en Portlet-component | Deze mogelijkheden zijn verouderd in [!DNL Experience Manager] 6.4 en zijn nu verwijderd uit [!DNL Experience Manager]. |
| [!DNL Sites] | Design Importer | Deze mogelijkheid is verwijderd als onveranderlijke gedeelten van het dialoogvenster [!DNL Experience Manager] opslagruimte zijn niet toegankelijk bij uitvoering. |
| [!DNL Assets] | [!DNL Assets] delen met Marketing Cloud Assets Core Service en Creative Cloud services is niet beschikbaar. | Voor integratie met [!DNL Adobe Creative Cloud], gebruik [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). |
| [!DNL Foundation] | Ondersteuning voor Apache Sling-gegevensbronnen (OSGi bundle org.apache.sling.datasource) | N.v.t. |
| [!DNL Foundation] | Ondersteuning voor JST-scriptsjablonen (OSGi bundle org.apache.sling.scripting.jst) | N.v.t. |
| [!DNL Foundation] | Ondersteuning voor het Apache Felix Http-whiteboard | OSGi Http-whiteboard |

## Java API {#java-api}

Zie [deze pagina](/help/release-notes/deprecated-apis.md) voor verouderde of verwijderde Java API&#39;s, die soms worden geïntroduceerd.

## OSGI-configuratie {#osgi-configuration}

Zie [dit artikel](/help/implementing/deploying/osgi-configuration-api.md) voor eventuele beperkingen met betrekking tot de configuratie van OSGI-eigenschappen, waarvan sommige in de loop der tijd kunnen worden ingevoerd.
