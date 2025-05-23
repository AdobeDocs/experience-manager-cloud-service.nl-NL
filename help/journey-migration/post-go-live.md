---
title: Post Go-Live
description: Leer hoe u op problemen kunt controleren en de prestaties kunt verbeteren.
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
feature: Migration
role: Admin
source-git-commit: bb2688701b80a560ea9078c2b7b6594ff55ce824
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 4%

---

# Post Go-Live {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Problemen met AEM oplossen"
>abstract="Beste praktijken voor de ononderbroken ontwikkeling en het beheer van logboeken evalueren. Meer informatie over tools zoals Developer Console en CRXDE Lite voor hulp bij het oplossen van problemen met AEM."
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs" text="Logbestanden openen en beheren"
>additional-url="https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#aem-as-a-cloud-service-development-tools" text="AEM as a Cloud Service-ontwikkelingstools"

Deze reis is het laatste deel, zodat leert u hoe te om op kwesties te controleren en prestaties te verbeteren nadat de migratie volledig is. Zorgen voor de opschoning van tijdelijke bestanden, best practices voor continue ontwikkeling controleren en logbestanden beheren.

## Het verhaal tot nu toe {#story-so-far}

In de vorige stap van de reis, leerde u hoe te om de migratie uit te voeren en [ gaan-leven ](/help/journey-migration/go-live.md) zodra de code en de inhoud klaar waren om over naar AEM as a Cloud Service te worden bewogen.

## Doelstelling {#objective}

In dit document worden de gereedschappen beschreven die beschikbaar zijn om problemen in AEM as a Cloud Service-omgevingen op te lossen:

* **Developer Console**
* **CRXDE Lite**
* **Tool voor beheren van logbestanden**

## Developer Console {#developer-console}

Fouten opsporen in AEM as a Cloud Service-ontwikkelomgevingen is in de Developer Console beschikbaar voor ontwikkelings-, stage- en productieomgevingen.

Zie [ het Uitvoeren voor AEM as a Cloud Service ](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) om meer over ontwikkelingshulpmiddelen te leren.

## CRXDE Lite {#crxde-lite}

Als gebruiker hebt u toegang tot CRXDE Lite in de ontwikkelomgeving, maar niet in het stadium of de productie.

>[!IMPORTANT]
>Het schrijven naar onveranderlijke opslagruimten, zoals `/libs` en `/apps` bij uitvoering, resulteert in fouten. Bovendien hebt u geen toegang tot ontwikkelaarstools voor testomgevingen en productieomgevingen.

Zie [ Ontwikkelen met CRXDE Lite ](/help/implementing/developing/tools/crxde.md) voor meer informatie over hoe te om uw toepassing van AEM te ontwikkelen gebruikend CRXDE Lite.

## Logbestanden beheren {#managing-logs}

Gebruikers hebben toegang tot een lijst met beschikbare logbestanden voor de geselecteerde omgeving.

Zie [ Toegang tot en het Leiden Logboeken ](/help/implementing/cloud-manager/manage-logs.md) om tot logboeken door het gebruikersinterface of van API als Cloud Manager toegang te hebben en te leiden.

## Contact opnemen met ondersteuning {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Help en ondersteuning"
>abstract="Neem contact op met het ondersteuningsteam van Adobe dat AEM ondersteunt voor meer informatie of om eventuele problemen op te lossen."
>additional-url="https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html" text="Ondersteuning voor Experience Cloud"

Als u vragen over toegang tot Cloud Service hebt, contacteer uw vertegenwoordiger van Adobe of [ Steun voor Experience Cloud ](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) voor meer details.

## Documentlessen {#document-learnings}

Als de migratie is voltooid, documenteert u de tijdens dit proces verworven kennis. Sommige vragen die het documentatieproces kunnen helpen zijn:

* Wat werkte goed en wat niet?
* Wat waren de belangrijkste pijnpunten?
* Aanbevelingen voor toekomstige migratie.

Deze cursussen na de migratie delen met belanghebbenden en teams binnen uw organisatie.

## De reis eindigt - of wel? {#journey-ends}

Gefeliciteerd! U hebt de AEM as a Cloud Service Migration Journey voltooid! U zou een inzicht in moeten hebben hoe te:

* Ga aan de slag met AEM as a Cloud Service
* Bepaal of uw implementatie klaar is om naar AEM as a Cloud Service te worden verplaatst
* Uw code en inhoud in de cloud klaar maken
* De migratie uitvoeren
* Controleren op problemen en prestaties verbeteren
