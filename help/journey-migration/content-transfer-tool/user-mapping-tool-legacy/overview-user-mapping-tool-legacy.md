---
title: Overzicht van het Hulpprogramma voor het toewijzen van gebruikers (verouderd)
description: Overzicht van het Hulpprogramma voor het toewijzen van gebruikers (verouderd)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 9%

---

# Overzicht van het Hulpprogramma voor het toewijzen van gebruikers (verouderd) {#overview-user-mapping-tool}

>[!INFO]
>
>Deze documentatie verwijst naar een verouderde versie van het hulpmiddel. Voor meer informatie over de meest recente versie raadpleegt u [Toewijzing van gebruikers en belangrijkste migratie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

<!-- Alexandru: drafting this for now

NOTE: "LEGACY" for user mapping includes everything before (that is, not including) 2.0.16 of CTT.

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## Inleiding {#introduction}

Als onderdeel van de as a Cloud Service overgang naar Adobe Experience Manager (AEM) moet u gebruikers en groepen van uw bestaande AEM naar AEM as a Cloud Service verplaatsen. Deze migratie wordt uitgevoerd met het gereedschap Inhoud overbrengen.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag. Deze integratie vereist het gebruik van de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor het beheren van gebruikers en gebruikersgroepen. De gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS), dat één aanmelding voor alle Adobe-cloudtoepassingen biedt. Zie voor meer informatie [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=en#identity-management). Vanwege deze wijziging moeten bestaande gebruikers en groepen worden toegewezen aan hun IMS-id&#39;s om dubbele gebruikers en groepen in de auteur-instantie van de Cloud Service te voorkomen.

## Gereedschap Toewijzing gebruiker {#mapping-tool}

Met het gereedschap Inhoud overbrengen (zonder gebruikerstoewijzing) worden alle gebruikers en groepen gemigreerd die zijn gekoppeld aan de inhoud die wordt gemigreerd. Het gereedschap Toewijzing gebruiker maakt deel uit van het gereedschap Inhoud overbrengen. Het enige doel is de gebruikers te bewerken, zodat ze correct worden herkend door IMS, de functionaliteit voor eenmalige aanmelding die door AEM as a Cloud Service wordt gebruikt. Nadat deze wijzigingen zijn doorgevoerd, worden de gebruikers en groepen van de opgegeven inhoud met het gereedschap Inhoud overbrengen naar de gebruikelijke locatie gemigreerd.

### Volgende functies {#whats-next}

Nadat u hebt geleerd wat een hulpmiddel voor het toewijzen van gebruikers is, kunt u nu belangrijke overwegingen en uitzonderlijke gevallen beoordelen voordat u het gereedschap Toewijzing gebruiker gaat gebruiken. Zie [Belangrijke overwegingen voor het gereedschap Toewijzing van gebruikers](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md) voor meer informatie .
