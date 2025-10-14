---
title: Opvallende wijzigingen in Adobe Experience Manager (AEM) as a Cloud Service
description: Opvallende wijzigingen in Adobe Experience Manager (AEM) as a Cloud Service.
exl-id: fe11d779-66cd-45aa-aa6b-c819b88d2405
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 6%

---

# Opvallende wijzigingen in Adobe Experience Manager as a Cloud Service {#notable-changes-aem-cloud}

Adobe Experience Manager (AEM) Cloud Service biedt veel nieuwe functies en mogelijkheden voor het beheer van uw AEM-projecten. Er zijn echter enkele verschillen tussen AEM Sites op locatie of in Adobe Managed Service in vergelijking met AEM Cloud Service. In dit document worden de belangrijke verschillen belicht.

>[!CONTEXTUALHELP]
>id="aem_cloud_notable_changes"
>title="Opvallende wijzigingen in AEM as a Cloud Service"
>abstract="Op dit tabblad kunt u inhoud weergeven die u helpt de verschillen te begrijpen tussen AEM op locatie of in Adobe Managed Services in vergelijking met AEM as a Cloud Service."
>additional-url="https://video.tv.adobe.com/v/330543" text="Ontwikkeling van AEM as a Cloud Service"


>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in AEM als geheel benadrukt. Voor meer informatie en oplossing-specifieke veranderingen zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* [Nieuwe functies en verschillen](/help/overview/what-is-new-and-different.md) tussen Adobe Experience Manager as a Cloud Service en eerdere versies
>* De [architectuur](/help/overview/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)

De belangrijkste verschillen zijn te vinden op de volgende gebieden:

* [/apps en /libs zijn onveranderlijk bij runtime](#apps-libs-immutable)

* [OSGi-bundels en -configuraties moeten als code worden behandeld](#osgi)

* [Wijzigingen in de publicatieopslagplaats zijn niet toegestaan](#changes-to-publish-repo)

* [Aangepaste uitvoermodi zijn niet toegestaan](#custom-runmodes)

* [Verwijderen van replicatieagents en gerelateerde wijzigingen](#replication-agents)

* [Verwijderen van klassieke gebruikersinterface](#classic-ui)

* [Levering op de publicatievorm](#publish-side-delivery)

* [Afhandeling en levering van bedrijfsmiddelen](#asset-handling)

## /apps en /libs zijn onveranderlijk bij runtime {#apps-libs-immutable}

Alle inhoud en submappen in `/apps` en `/libs` zijn alleen-lezen. Om het even welke eigenschap of douanecode die verwacht om veranderingen daar aan te brengen doet niet dit. Er wordt een fout geretourneerd dat dergelijke inhoud alleen-lezen is en de schrijfbewerking niet kan worden voltooid. Dit heeft gevolgen voor verschillende gebieden van AEM:

* Wijzigingen in `/libs` zijn helemaal niet toegestaan.
   * Dit is geen nieuwe regel, maar deze is niet toegepast in eerdere versies op locatie van AEM.
* Bedekkingen voor gebieden in `/libs` die kunnen worden bedekt, zijn nog steeds toegestaan binnen `/apps` .
   * Dergelijke overlays moeten afkomstig zijn van Git via de CI/CD-pijpleiding.
* De statische informatie van het malplaatjeontwerp die in `/apps` wordt opgeslagen kan niet door middel van UI worden uitgegeven.
   * Het wordt aanbevolen Bewerkbare sjablonen te gebruiken.
   * Als de Statische Malplaatjes nog worden vereist, moet de configuratieinformatie uit Git als pijpleiding CI/CD komen.
* MSM de Vervaging en de douaneMSM uitrolconfiguraties moeten van Git door middel van de pijpleiding worden geïnstalleerd CI/CD.
* I18n de vertaalveranderingen moeten uit Git door middel van de CI/CD pijpleiding komen.

## OSGi-bundels en -configuraties moeten als code worden behandeld {#osgi}

Wijzigingen in OSGi-bundels en -configuraties moeten via de CI/CD-pijplijn worden aangebracht.

* Nieuwe of bijgewerkte OSGi-bundels moeten via Git worden ingevoerd via de CI/CD-pijplijn.
* De veranderingen in configuraties OSGi kunnen slechts uit Git door middel van de pijpleiding CI/CD komen.

De webconsole, die in eerdere versies van AEM werd gebruikt om OSGi-bundels en -configuraties te wijzigen, is niet beschikbaar in AEM Cloud Service.

## Wijzigingen in publicatieruimte zijn niet toegestaan {#changes-to-publish-repo}

Naast wijzigingen in de map `/home` op de publicatielijst zijn directe wijzigingen in de publicatiereserver niet toegestaan op AEM Cloud Service. In eerdere versies van AEM op locatie of AEM op AMS konden wijzigingen in de code rechtstreeks worden doorgevoerd in de publicatieruimte. Sommige beperkingen kunnen op de volgende manieren worden beperkt:

* Voor inhoud en op inhoud-gebaseerde configuratie: breng uw veranderingen op de instantie van de Auteur aan en publiceer hen.
* Voor code en configuratie: breng uw veranderingen in de gegevensopslagplaats van GIT aan en stel de pijpleiding van CI/CD in werking om hen uit te rollen.

## Aangepaste uitvoermodi zijn niet toegestaan {#custom-runmodes}

Aanvullende of aangepaste uitvoermodi zijn niet mogelijk in AEM Cloud Service. Voor een lijst van looppas wijzen die uit-van-de-doos voor de Dienst van de Wolk AEM worden verstrekt, zie [&#x200B; het Opstellen aan AEM as a Cloud Service &#x200B;](/help/implementing/deploying/overview.md#runmodes).

## Verwijderen van replicatieagents en gerelateerde wijzigingen {#replication-agents}

In de Dienst van de Wolk AEM, wordt de inhoud gepubliceerd gebruikend [&#x200B; het Verdelen van de Distributie van de Inhoud &#x200B;](https://sling.apache.org/documentation/bundles/content-distribution.html). De replicatieagenten die in vorige versies van AEM worden gebruikt worden niet meer gebruikt of verstrekt, die de volgende gebieden van bestaande Projecten van AEM zouden kunnen beïnvloeden:

* Aangepaste workflows die bijvoorbeeld inhoud doorsturen naar replicatieagents van voorvertoningsservers.
* Aanpassing aan replicatieagenten om inhoud om te zetten.
* Het gebruiken van Omgekeerde Replicatie om inhoud van Publish terug naar Auteur te brengen.

Daarnaast worden de pauze- en uitschakelknoppen verwijderd uit de beheerconsole van de replicatieagent.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in AEM Cloud Service.

## Levering op de publicatievorm {#publish-side-delivery}

De versnelling van HTTP met inbegrip van CDN en verkeersbeheer voor de auteur en de Publish diensten worden verstrekt door gebrek in de Dienst van de Wolk AEM.

Voor projecten die van AMS of een op-gebouw installatie overgaan, adviseert Adobe sterk gebruikend ingebouwde CDN, omdat de eigenschappen binnen de Dienst van de Wolk AEM voor CDN worden geoptimaliseerd verstrekt.

## Afhandeling en levering van bedrijfsmiddelen {#asset-handling}

Het uploaden, verwerken en downloaden van middelen wordt in [!DNL Experience Manager Assets] geoptimaliseerd als een [!DNL Cloud Service] . AEM [!DNL Assets] is nu efficiënter, maakt meer schaling mogelijk en kunt u sneller uploaden en downloaden. Bovendien is dit van invloed op de bestaande aangepaste code en bepaalde bewerkingen. Voor een lijst van veranderingen en voor pariteit met [!DNL Experience Manager] 6.5 eigenschappen, zie de [&#x200B; veranderingen in  [!DNL Assets]](/help/assets/assets-cloud-changes.md).
