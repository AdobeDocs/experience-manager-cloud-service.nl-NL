---
title: Belangrijkste functies beheren
description: Belangrijkste functies voor migratie beheren met Admin Console
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Belangrijkste functies beheren {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="Belangrijkste functies beheren"
>abstract="Leer wat u moet doen om gebruikers tijdens of na een migratie van inhoud te beheren"

Voordat inhoud wordt overgebracht naar de AEM as a Cloud Service-cloud, kunnen een aantal taken worden uitgevoerd op de Admin Console.  Dit zijn: gebruikers maken, groepen maken en gebruikers toewijzen aan groepen; deze gebruikers en groepen bevinden zich in IMS, Adobe Identity Management Service, die wordt gebruikt voor het beheer van gebruikers en groepen voor alle op de cloud gebaseerde services van Adobe.

## Groepen en hun gebruikers in Admin Console maken

[&#x200B; Gebruikend Admin Console voor de Hoofden van AEM &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up) verstrekt gedetailleerde instructies op hoe te om gebruikers en groepen in IMS tot stand te brengen, en hoe te om de gebruikers aan de groepen tezelfdertijd of later toe te voegen.  Het document bevat drie opties voor het maken ervan: Handmatig via de Admin Console, via CSV-upload via de Admin Console en via een gebruikerssynchronisatieprogramma.

Met de handmatige optie kunt u één groep of gebruiker tegelijk maken. Met de CSV-upload kunt u meerdere gebruikers en groepen tegelijk maken en koppelen en met het gereedschap Gebruikerssynchronisatie kunt u een bestaande IDP gebruiken om de IMS-gebruikers en -groepen te maken en te beheren.

Wanneer een gebruiker IMS gebruikt om zich aan te melden bij AEM, wordt een AEM-representatie van de gebruiker gemaakt.  Bovendien hebben alle IMS-groepen waarin de gebruiker zich bevindt, in AEM gelijkwaardige AEM-groepen gemaakt.  Deze door IMS gemaakte AEM-gebruikers en -groepen worden nog steeds hoofdzakelijk beheerd met behulp van de Admin Console.

Nadat de migratie van de inhoud is voltooid, moeten IMS-groepen normaal gesproken over een extra configuratie beschikken, zodat gebruikers toegang hebben tot de gemigreerde inhoud.  Zie [&#x200B; migrerende Belangrijkste na Migratie &#x200B;](/help/journey-migration/managing-principals-after-migration.md)

Zie ook [&#x200B; Leerprogramma, de gebruikers van AEM, groepen en toestemmingen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) om meer over te leren hoe de gebruikers en de groepen van AEM en IMS worden geïntegreerd en worden beheerd.
