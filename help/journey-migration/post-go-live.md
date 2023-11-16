---
title: Post Go-Live
description: Leer hoe u op problemen kunt controleren en de prestaties kunt verbeteren
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 9%

---

# Post Go-Live {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="AEM voor probleemoplossing"
>abstract="De beste praktijken van het overzicht voor ononderbroken ontwikkeling en beheert logboeken samen met hulpmiddelen zoals de console &amp; CRXDE Lite van de Ontwikkelaar om met het oplossen van problemenkwesties met AEM te helpen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html" text="Logbestanden openen en beheren"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools" text="as a Cloud Service ontwikkelingsinstrumenten AEM"

Deze reis is het laatste deel, zodat leert u hoe te om op kwesties te controleren en prestaties te verbeteren nadat de migratie volledig is. U moet ervoor zorgen dat tijdelijke bestanden worden opgeschoond, best practices voor continue ontwikkeling controleren en logbestanden beheren.

## Het verhaal tot nu toe {#story-so-far}

In de vorige stap van de reis, leerde u hoe te om de migratie uit te voeren en [GoLive](/help/journey-migration/go-live.md) zodra de code en de inhoud klaar waren om naar AEM as a Cloud Service te worden verplaatst.

## Doelstelling {#objective}

In dit document worden de gereedschappen beschreven die beschikbaar zijn om problemen op te lossen in AEM as a Cloud Service omgevingen:

* **Developer Console**
* **CRXDE Lite**
* **Tool voor beheren van logbestanden**

## Developer Console {#developer-console}

Foutopsporing AEM as a Cloud Service ontwikkelaarsomgevingen is beschikbaar in de Developer Console voor ontwikkelings-, stage- en productieomgevingen.

Zie [Implementatie van AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) voor meer informatie over ontwikkelingsinstrumenten.

## CRXDE Lite {#crxde-lite}

Als gebruiker hebt u toegang tot CRXDE Lite in de ontwikkelomgeving, maar niet in de stage- of productieomgeving.

>[!IMPORTANT]
>Schrijven naar onveranderlijke opslagplaatsen zoals `/libs` en `/apps` resulteert in fouten. Bovendien hebt u geen toegang tot ontwikkelaarstools voor testomgevingen en productieomgevingen.

Zie [Ontwikkelen met CRXDE Lite](/help/implementing/developing/tools/crxde.md) voor meer informatie over hoe te om uw AEM toepassing te ontwikkelen gebruikend CRXDE Lite.

## Logbestanden beheren {#managing-logs}

Gebruikers hebben toegang tot een lijst met beschikbare logbestanden voor de geselecteerde omgeving.

Zie [Logbestanden openen en beheren](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie over het openen en beheren van logbestanden via de gebruikersinterface of de API via Cloud Manager.

## Contact opnemen met ondersteuning {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Help en ondersteuning"
>abstract="Neem contact op met AEM ondersteuningsteam van de Adobe voor meer informatie of om eventuele problemen op te lossen."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Ondersteuning voor Experience Cloud"

Als u vragen heeft over toegang tot Cloud Service, neem dan contact op met uw Adobe of [Ondersteuning voor Experience Cloud](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) voor meer informatie .

## Documentlessen {#document-learnings}

Als de migratie is voltooid, documenteert u de tijdens dit proces verworven kennis. Sommige vragen die het documentatieproces kunnen helpen zijn:

* Wat werkte goed en wat niet?
* Wat waren de belangrijkste pijnpunten?
* Recommendations als er een toekomstige migratie is.

Deze cursussen na de migratie delen met belanghebbenden en teams binnen uw organisatie.

## De reis eindigt - of wel? {#journey-ends}

Gefeliciteerd! U hebt de AEM as a Cloud Service migratiereis voltooid! U zou een inzicht in moeten hebben hoe te:

* Ga aan de slag met de overgang naar AEM as a Cloud Service
* Bepaal of uw implementatie klaar is om te worden verplaatst naar AEM as a Cloud Service
* Uw code en inhoud in de cloud klaar maken
* De migratie uitvoeren
* Controleren op problemen en prestaties verbeteren
