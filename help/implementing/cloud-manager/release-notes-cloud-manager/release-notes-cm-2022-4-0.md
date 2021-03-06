---
title: Opmerkingen bij de release Cloud Manager 2022.4.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2022.4.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: e7ff623b-aeca-40a6-bf48-98af270a4117
source-git-commit: 458d63c27bb2ab4d09237aa3ecb96c0f6d5e67ed
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Opmerkingen bij de release Cloud Manager 2022.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Deze pagina documenteert de opmerkingen bij de release voor Cloud Manager 2022.4.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2022.4.0 in AEM as a Cloud Service is 7 april 2022. De volgende release is gepland voor 5 mei 2022.

## Wat is er nieuw? {#what-is-new}

* De verbeteringen van de duur en het succespercentage van pijpleiding bouwstappen zijn uitgevoerd en zullen incrementeel aan alle klanten door de maand van April worden uitgevoerd.
* U kunt nu gemakkelijk een git-vertakking vinden door de eerste paar tekens van de naam in het invoerveld in de wizard Toevoegen en Bewerken in de pijplijn te typen en een selectie te maken uit voorgestelde overeenkomsten voor beide typen [productie](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) en [niet-productie](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) pijpleidingen.
* Kort na de release van april zal India beschikbaar komen voor selectie bij het definiëren van het wolkengebied tijdens het creëren van het milieu.
* De **Pijpleidingen** pagina heeft nu paginering om de bruikbaarheid voor programma &#39; s met een groot aantal pijpleidingen te verbeteren .
   * Er worden 50 rijen per pagina weergegeven in de tabel.
* De versie van de [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) gebruikt door Cloud Manager is bijgewerkt naar versie 36.
* Oracle JDK is nu de standaard-JDK voor de ontwikkeling en werking van AEM toepassingen. Het buildproces van Cloud Manager wordt automatisch overgeschakeld op het gebruik van Oracle JDK, zelfs als er expliciet een andere optie is geselecteerd in de Maven-toolchain.
   * Voor meer informatie over het schakelen naar Oracle JDK raadpleegt u [de documentatie van het Milieu van de Bouwstijl.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support)
   * Zie [het Java-ondersteuningsbeleid voor Adobe Experience Manager - Veelgestelde vragen](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) gemeenschappelijke vragen over deze wijziging te beantwoorden.
* De uitvoering van de pijpleiding zal nu sneller ontbreken door oudere AEM versies tijdens de bevestigingsstap te ontdekken. De gebruikers zullen met een bericht in UI worden voorgesteld om hen te begeleiden.

## Opgeloste problemen {#bug-fixes}

* Het logboek dat in de stap van de Test UI wordt gecreeerd is nu beschikbaar voor download via UI.
* De configuratiepijpleidingen van het Web kunnen nu slechts pakketten van Web rij config uitvoeringen hergebruiken.
* Er is meer duidelijkheid toegevoegd aan de berichten in de gebruikersinterface over het bijwerken van AEM in een verouderde omgeving.
