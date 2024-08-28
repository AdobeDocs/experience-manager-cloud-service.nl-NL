---
title: Richtlijnen en tips en trucs voor het gebruik van het gereedschap Inhoud overbrengen
description: Leer de richtlijnen en de beste werkwijzen voor het gebruik van het gereedschap Inhoud overbrengen.
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 11%

---


# Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen {#guidelines}

## Richtlijnen en beste praktijken {#best-practices}

<!-- Alexandru: hiding for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Guidelines and Best Practices"
>abstract="Review guidelines and best practices to use the Content Transfer tool including revision cleanup tasks, Disk space considerations and more."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html" text="Important Considerations for using Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/group-migration.md#important-considerations" text="Important Considerations when Migrating Groups" 

-->

Met het gereedschap Inhoud overbrengen wordt het proces voor inhoudsoverdracht geïntegreerd met Cloud Acceleration Manager. U moet deze versie (2.0 of hoger, maar versie 3.0 wordt nu aanbevolen) gebruiken om alle voordelen te behalen die deze biedt:

* Zelfbediening om een migratieset één keer uit te pakken en tegelijkertijd in meerdere omgevingen in te voeren
* Verbeterde gebruikerservaring dankzij betere laadstatussen, instructies en foutafhandeling
* Logbestanden voor insluiting blijven bestaan en zijn altijd beschikbaar voor probleemoplossing

Als u de nieuwste versie wilt gebruiken, verwijdert u oudere versies van het gereedschap Inhoud overbrengen. Met versie 2.0 en hoger kunt u migratiesets maken en extractie en inname van de sets opnieuw uitvoeren.
Versies die ouder zijn dan 2.0.0 worden niet ondersteund en u wordt geadviseerd de meest recente versie te gebruiken.

De volgende Richtlijnen en Beste praktijken zijn op de nieuwe versie van het Hulpmiddel van de Overdracht van de Inhoud van toepassing:

* De opruiming van de Herziening van de looppas ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) en [ de controles van de gegevensopslag ](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html) op de **bron** bewaarplaats zodat kunt u potentiële problemen identificeren en de grootte van de bewaarplaats verminderen.[

* In de innamefase, adviseert de Adobe dat u de inname gebruikend *in werking stelt veegt* wijze toegelaten waar de bestaande bewaarplaats (Auteur of Publish) in het milieu van de Cloud Service van doelAdobe Experience Manager (AEM) wordt geschrapt. Werk vervolgens bij met de gegevens van de migratieset. Deze modus is sneller dan de modus Vegen, waarbij de migratieset boven op de huidige inhoud wordt toegepast.

* Wanneer alle content is verplaatst, is de juiste projectstructuur in de Cloud Service-omgeving vereist. Anders wordt de content niet correct weergegeven in de Cloud Service-omgeving.

* Voordat u de content Transfer-tool uitvoert, moet u ervoor zorgen dat er voldoende schijfruimte is in de submap `crx-quickstart` van de AEM-broninstantie. Dit is omdat de Content Transfer-tool een lokale kopie van de repository maakt die later wordt geüpload naar de migratieset.
De algemene formule voor het berekenen van de vereiste vrije schijfruimte is als volgt:
  `data store size + node store size * 1.5`

* *Grootte van dataopslagplaats*: De Content Transfer-tool gebruikt 64 GB, ook als de werkelijke dataopslagplaats groter is.
* *Grootte van node-opslagplaats*: De grootte van de segmentopslagdirectory of de grootte van de MongoDB-database.
Voor een segmentopslagplaats van 20 GB is dus 94 GB aan vrije schijfruimte vereist.

* Een migratieset moet gedurende de gehele activiteit van de inhoudsoverdracht worden gehandhaafd om de aanvulling van de inhoud te steunen. Er kunnen maximaal 20 migratiesets per project in Cloud Acceleration Manager worden gemaakt en onderhouden op een moment tijdens de activiteit voor inhoudsoverdracht. Als er meer dan 20 migratiesets nodig zijn, maakt u een tweede project in Cloud Acceleration Manager. Dit vereist echter extra projectbeheer en beheer buiten het product om te voorkomen dat inhoud op het doel door meerdere gebruikers wordt overschreven.

* Wijzig de installatiemap van het gereedschap CTT niet. Standaard vindt de installatie plaats in het crx-quickstart/cloud-migratiepad. Deze specifieke locatie wordt intern gebruikt door andere bibliotheken. Als u dit pad wijzigt, kan dit leiden tot extractieproblemen.

## Belangrijke overwegingen voordat u het gereedschap Inhoud overbrengen gebruikt {#important-considerations}

Bekijk de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Content Transfer-tool:

* De minimale systeemvereisten voor Content Transfer Tool zijn AEM 6.3 + en Java™ 8. Als u een lagere versie AEM, upgradet u de gegevensopslagruimte naar AEM 6.5 om het gereedschap Inhoud overbrengen te gebruiken.

* Java™ moet zijn geconfigureerd in de AEM omgeving, zodat de opdracht `java` kan worden uitgevoerd door de gebruiker die AEM start.

* Het gereedschap voor het overbrengen van inhoud kan worden gebruikt met de volgende typen gegevensopslag: File Data Store, S3 Data Store, Shared S3 Data Store en Azure Blob Store Data Store.

* Als u het Milieu van de zandbak van a ** gebruikt, zorg ervoor dat uw milieu huidig is en aan de recentste versie bevorderd. Als u een *Productieomgeving* gebruikt, wordt deze automatisch bijgewerkt.

* Om een opname te beginnen, moet u tot de lokale AEM **beheerders** groep in de instantie van de Cloud Service behoren u inhoud overbrengt naar. Niet-geprivilegieerde gebruikers kunnen geen toegang krijgen zonder handmatig het migratietoken op te geven.

* Als het plaatsen **bestaande inhoud op de instantie van de Wolk alvorens wordt toegelaten** wordt de optie van de opname toegelaten, schrapt het de volledige bestaande bewaarplaats en leidt tot een nieuwe bewaarplaats om inhoud in te nemen. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Het is ook waar voor een admin gebruiker die aan de **wordt toegevoegd beheerders** groep. De gebruiker moet aan de **beheerders** groep worden gelezen om het toegangstoken voor het Hulpmiddel van de Overdracht van de Inhoud terug te winnen.

* Oplossingen ondersteunen het samenvoegen van inhoud van meerdere bronnen in de instantie van de Cloud Service van het doel niet als de inhoud van de twee bronnen naar dezelfde paden op het doel wordt verplaatst. Als u inhoud van meerdere bronnen naar één doelinstantie wilt verplaatsen, zorgt u ervoor dat de inhoudspaden van de bronnen elkaar niet overlappen.

* De extractietoets is 14 dagen geldig vanaf het moment dat deze is gemaakt of vernieuwd. Het kan op elk ogenblik worden verlengd. Als de extractietoets is verlopen, kunt u geen extractie uitvoeren.

* Met het gereedschap Inhoud overbrengen (CTT) kunt u geen inhoudanalyse uitvoeren voordat u inhoud van de broninstantie naar de doelinstantie overbrengt. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een Publish-omgeving. De inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. Een gebruiker kan een migratieset opnemen in een instantie Auteur, een instantie Publish of beide. De Adobe beveelt aan dat terwijl het bewegen van inhoud naar een instantie van de Productie, CTT op de instantie van de bronauteur wordt geïnstalleerd om inhoud naar de instantie van de doelauteur te verplaatsen. En installeer op dezelfde manier CTT op de Publish-broninstantie om inhoud naar de Publish-doelinstantie te verplaatsen. Zie [ Lopend het Hulpmiddel van de Overdracht van de Inhoud op een instantie van Publish ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool) voor meer details.

* De groepen die door het Hulpmiddel van de Overdracht van de Inhoud worden overgebracht zijn slechts die groepen die door de inhoud worden vereist om toestemmingen tevreden te stellen. Het _proces van de Extractie_ kopieert het volledige `/home/groups` in de migratiereeks. Voor meer informatie, zie [ Migratie van de Groep ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md). Het _1} proces van de Opname {kopieert alle groepen die in gemigreerde inhoud ACLs van verwijzingen worden voorzien._ Zie [ het Migreren van Gesloten Groepen van de Gebruiker ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) voor extra overwegingen voor groepen die in een gesloten beleid van de Groep van de Gebruiker (CUG) worden gebruikt.

* Tijdens de extractiefase wordt de Content Transfer-tool uitgevoerd op een actieve AEM-broninstantie.

* De *Fase van de Opname* voor de Schalen van de Auteur onderaan de volledige plaatsing van de Auteur. Dit betekent dat de AEM van de auteur niet beschikbaar is tijdens het hele innameproces. Zorg ook ervoor dat geen pijpleidingen van Cloud Manager worden uitgevoerd terwijl u de *1} fase van de Opname {in werking stelt.*

* Wanneer u `Amazon S3` of `Azure` gebruikt als gegevensopslag op het AEM van de bron, moet de gegevensopslag zo worden geconfigureerd dat de opgeslagen balken niet kunnen worden verwijderd (opschoning). Dit verzekert integriteit van indexgegevens en het nalaten om deze manier te vormen kan in ontbroken extracties wegens gebrek aan integriteit van deze indexgegevens resulteren.

* Als u aangepaste indexen gebruikt, moet u ervoor zorgen dat u de aangepaste indexen configureert met het knooppunt `tika` voordat u het gereedschap Inhoud overbrengen uitvoert. Zie [ het Voorbereiden van de Nieuwe Definitie van de Index ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#preparing-the-new-index-definition) voor meer details.

* Als u aanvullende onderdelen wilt uitvoeren, mag de inhoudstructuur van bestaande inhoud niet veranderen van het tijdstip waarop de eerste extractie wordt uitgevoerd tot het moment waarop de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

* Als u van plan bent versies op te nemen als onderdeel van een migratieset en aanvullende versies uitvoert met `wipe=false` , moet u versiebeheer uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld houdt en top-ups uitvoert in een migratieset, moet u de opname uitvoeren als `wipe=true` .

* Een migratieset verloopt na een langdurige periode van inactiviteit, waarna de gegevens ervan niet meer beschikbaar zijn. Het overzicht [ Vastgestelde Vervaldatum van de Migratie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html#migration-set-expiry) voor meer details.

## Volgende functies {#whats-next}

Nadat u de richtlijnen, de beste praktijken en de belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen hebt geleerd, kunt u het gereedschap nu installeren en gebruiken, te beginnen met het maken van een migratieset. Zie [ Begonnen het Worden met het Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).
