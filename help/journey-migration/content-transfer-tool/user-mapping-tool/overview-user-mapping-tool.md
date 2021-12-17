---
title: Overzicht van het gereedschap Toewijzing aan gebruiker
description: Overzicht van het gereedschap Toewijzing aan gebruiker
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 7%

---


# Overzicht van het gereedschap Toewijzing aan gebruiker {#overview-user-mapping-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Gereedschap Toewijzing gebruiker"
>abstract="Met het gereedschap Inhoud overbrengen kunt u gebruikers en groepen van het bestaande AEM naar AEM as a Cloud Service verplaatsen. Bestaande gebruikers en groepen moeten aan hun IMS-id&#39;s worden toegewezen om dubbele gebruikers en groepen op de Cloud Service-auteur te voorkomen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Belangrijke overwegingen voor het gebruik van het gereedschap Toewijzing gebruiker"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Gebruikerstoewijzing gebruiken"

## Inleiding {#introduction}

Als onderdeel van de as a Cloud Service overgang naar Adobe Experience Manager (AEM) moet u gebruikers en groepen verplaatsen van uw bestaande AEM naar AEM as a Cloud Service. Dit wordt gedaan door het Hulpmiddel van de Overdracht van de Inhoud.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.  Hiervoor moet gebruik worden gemaakt van de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) dat Single Sign-On biedt voor alle Adobe-cloudtoepassingen. Raadpleeg voor meer informatie [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en#identity-management). Vanwege deze wijziging moeten bestaande gebruikers en groepen worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers en groepen in de auteur van de Cloud Service te voorkomen.

## Gereedschap Toewijzing gebruiker {#mapping-tool}

Met het gereedschap Inhoud overbrengen (zonder gebruikerstoewijzing) worden alle gebruikers en groepen gemigreerd die zijn gekoppeld aan de inhoud die wordt gemigreerd. Het hulpmiddel van de Toewijzing van de Gebruiker is een deel van het Hulpmiddel van de Overdracht van de Inhoud, en zijn enig doel is de gebruikers en de groepen te wijzigen zodat zij correct door IMS kunnen worden erkend, de enig-sign-on functionaliteit die door AEM as a Cloud Service wordt gebruikt. Zodra deze wijzigingen zijn aangebracht, migreert het gereedschap Inhoud overbrengen de gebruikers en groepen van de opgegeven inhoud zoals gewoonlijk.

### Volgende functies {#whats-next}

Nadat u hebt geleerd wat een hulpmiddel voor het toewijzen van gebruikers is, kunt u nu belangrijke overwegingen en uitzonderlijke gevallen beoordelen voordat u het gereedschap Toewijzing gebruiker gaat gebruiken. Zie [Belangrijke overwegingen voor het gereedschap Toewijzing van gebruikers](/help/journey-migration/content-transfer-tool/user-mapping-tool/considerations-user-mapping-tool.md) voor meer informatie .