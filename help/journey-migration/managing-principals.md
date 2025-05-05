---
title: Belangrijkste functies beheren
description: Hoofdbeginselen voor migratie beheren, Admin Console gebruiken
source-git-commit: 5bf497fb2122cc3d3ff0903aeb680a35e90f33b0
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# Belangrijkste functies beheren {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="Belangrijkste functies beheren"
>abstract="Leer wat u moet doen om gebruikers tijdens of na een migratie van inhoud te beheren"

Voordat inhoud wordt overgebracht naar de AEM as a Cloud Service-cloudomgeving, kunnen een aantal taken worden uitgevoerd op de Admin Console.  Dit zijn: gebruikers maken, groepen maken en gebruikers toewijzen aan groepen; deze gebruikers en groepen bevinden zich in IMS, de Identity Management Service van de Adobe, die wordt gebruikt om gebruikers en groepen voor alle cloudgebaseerde services van de Adobe te beheren.

### Groepen en hun gebruikers in Admin Console maken

[ Gebruikend Admin Console voor AEM Belanghebbenden ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up) verstrekt gedetailleerde instructies op hoe te om gebruikers en groepen in IMS tot stand te brengen, en hoe te om de gebruikers aan de groepen tezelfdertijd of later toe te voegen.  Het document bevat drie opties voor het maken ervan: Handmatig via de Admin Console, via CSV-upload via de Admin Console en via een gebruikerssynchronisatieprogramma.

Met de handmatige optie kunt u één groep of gebruiker tegelijk maken. Met de CSV-upload kunt u meerdere gebruikers en groepen tegelijk maken en koppelen en met het gereedschap Gebruikerssynchronisatie kunt u een bestaande IDP gebruiken om de IMS-gebruikers en -groepen te maken en te beheren.

Wanneer een gebruiker IMS gebruikt om zich aan te melden bij AEM, wordt een AEM representatie van de gebruiker gemaakt.  Bovendien hebben alle IMS-groepen waarin de gebruiker zich bevindt, equivalente AEM groepen die in AEM zijn gemaakt.  Deze IMS-gecreeerde AEM gebruikers en groepen worden nog hoofdzakelijk beheerd gebruikend de Admin Console.

Nadat de migratie van de inhoud is voltooid, moeten IMS-groepen normaal gesproken over een extra configuratie beschikken, zodat gebruikers toegang hebben tot de gemigreerde inhoud.  Zie [ migrerende Belangrijkste na Migratie ](/help/journey-migration/managing-principals-after-migration.md)

Zie ook [ Leerprogramma, AEM gebruikers, groepen en toestemmingen ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) om meer over te leren hoe AEM en IMS gebruikers en groepen worden geïntegreerd en worden beheerd.