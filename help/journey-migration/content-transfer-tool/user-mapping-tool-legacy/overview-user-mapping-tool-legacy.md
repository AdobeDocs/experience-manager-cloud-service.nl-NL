---
title: Overzicht van het Hulpprogramma voor het toewijzen van gebruikers (verouderd)
description: Overzicht van het Hulpprogramma voor het toewijzen van gebruikers (verouderd)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
source-git-commit: 69dfe7f98628ab67cc3a994c32b1530550ec6a01
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 9%

---

# Overzicht van het gereedschap Toewijzing aan gebruiker {#overview-user-mapping-tool}


<!-- Alexandru: drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## Inleiding {#introduction}

Als onderdeel van de as a Cloud Service overgang naar Adobe Experience Manager (AEM) moet u gebruikers en groepen verplaatsen van uw bestaande AEM naar AEM as a Cloud Service. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.  Hiervoor moet gebruik worden gemaakt van de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) dat Single Sign-On biedt voor alle Adobe-cloudtoepassingen. Raadpleeg voor meer informatie [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en#identity-management). Vanwege deze wijziging moeten bestaande gebruikers en groepen worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers en groepen in de auteur van de Cloud Service te voorkomen.

## Gereedschap Toewijzing gebruiker {#mapping-tool}

Met het gereedschap Inhoud overbrengen (zonder gebruikerstoewijzing) worden alle gebruikers en groepen gemigreerd die zijn gekoppeld aan de inhoud die wordt gemigreerd. Het hulpmiddel van de Toewijzing van de Gebruiker is een deel van het Hulpmiddel van de Overdracht van de Inhoud, en zijn enig doel is de gebruikers te wijzigen zodat zij correct door IMS, de enig-sign-on functionaliteit kunnen worden erkend die door AEM as a Cloud Service wordt gebruikt. Zodra deze wijzigingen zijn aangebracht, migreert het gereedschap Inhoud overbrengen de gebruikers en groepen van de opgegeven inhoud zoals gewoonlijk.

### Volgende functies {#whats-next}

Nadat u hebt geleerd wat een hulpmiddel voor het toewijzen van gebruikers is, kunt u nu belangrijke overwegingen en uitzonderlijke gevallen beoordelen voordat u het gereedschap Toewijzing gebruiker gaat gebruiken. Zie [Belangrijke overwegingen voor het gereedschap Toewijzing van gebruikers](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md) voor meer informatie .
