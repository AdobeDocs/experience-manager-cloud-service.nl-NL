---
title: Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen
description: Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
source-git-commit: b0d219f712b1dbbfa70d66ac14c0a66dc89ebbab
workflow-type: tm+mt
source-wordcount: '1595'
ht-degree: 19%

---

# Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen {#guidelines}

## Richtlijnen en best practices {#best-practices}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Richtlijnen en best practices"
>abstract="Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen controleren, waaronder taken voor het opschonen van revisies, overwegingen voor schijfruimte en meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Belangrijke overwegingen voor het gebruik van het gereedschap Toewijzing gebruiker"

Er is een nieuwe versie van het gereedschap Inhoud overbrengen beschikbaar waarin het proces voor de overdracht van inhoud wordt geïntegreerd met het programma voor de versnelling van de cloud. U wordt ten zeerste aangeraden over te schakelen naar deze nieuwe versie om alle voordelen van deze versie te benutten:

* Zelfbediening om een migratieset één keer uit te pakken en tegelijkertijd in meerdere omgevingen in te voeren
* Verbeterde gebruikerservaring dankzij betere laadstatussen, hulplijnen en foutafhandeling
* Logbestanden voor congestie blijven bestaan en zijn altijd beschikbaar voor probleemoplossing

Als u de nieuwe versie wilt gebruiken, moet u de installatie van oudere versies van het gereedschap Inhoud overbrengen ongedaan maken. Dit is nodig omdat de nieuwe versie een grote architectonische verandering heeft. Met v2.0.10 moet u nieuwe migratiesets maken en de extractie en opname opnieuw uitvoeren op de nieuwe migratiesets. Als er al een migratie wordt uitgevoerd, kunt u de vorige versie van CTT blijven gebruiken totdat de migratie is voltooid.

De volgende Richtlijnen en Beste praktijken zijn op de nieuwe versie van het Hulpmiddel van de Overdracht van de Inhoud van toepassing:

* Het is raadzaam om [Revision Cleanup](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) en [consistentiecontroles voor de dataopslagplaats](https://helpx.adobe.com/nl/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) op de **bronrepository** uit te voeren om potentiële problemen te identificeren en de repository te verkleinen.

* Tijdens de opnamefase wordt het aanbevolen dat u de modus voor *wissen* inschakelt. Hiermee wordt de bestaande repository (auteur of publicatie) in de AEM Cloud Service-doelomgeving volledig gewist en vervolgens bijgewerkt met de content van de migratieset. Deze modus is veel sneller dan de modus voor niet-wissen, waarbij de migratieset boven op de huidige content wordt toegepast.

* Wanneer alle content is verplaatst, is de juiste projectstructuur in de Cloud Service-omgeving vereist. Anders wordt de content niet correct weergegeven in de Cloud Service-omgeving.

* Voordat u de content Transfer-tool uitvoert, moet u ervoor zorgen dat er voldoende schijfruimte is in de submap `crx-quickstart` van de AEM-broninstantie. Dit is omdat de Content Transfer-tool een lokale kopie van de repository maakt die later wordt geüpload naar de migratieset.
De algemene formule voor het berekenen van de vereiste vrije schijfruimte is als volgt:
   `data store size + node store size * 1.5`

   * *Grootte van dataopslagplaats*: De Content Transfer-tool gebruikt 64 GB, ook als de werkelijke dataopslagplaats groter is.
   * *Grootte van node-opslagplaats*: De grootte van de segmentopslagdirectory of de grootte van de MongoDB-database.
Voor een segmentopslagplaats van 20 GB is dus 94 GB aan vrije schijfruimte vereist.

* Een migratieset moet gedurende de gehele activiteit van de inhoudsoverdracht worden gehandhaafd om de toevoeging van inhoud te steunen. Per project kunnen maximaal vijf migratiesets worden gemaakt en onderhouden in Cloud Acceleration Manager tijdens de activiteit voor het overbrengen van inhoud. Als u meer dan vijf migratiesets nodig hebt, moet u een tweede project maken in Cloud Acceleration Manager. Dit vereist echter extra projectbeheer en beheer buiten het product om te voorkomen dat inhoud op het doel door meerdere gebruikers wordt overschreven.

## Belangrijke overwegingen voordat u het gereedschap Inhoud overbrengen gebruikt {#important-considerations}

Bekijk de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Content Transfer-tool:

* De minimale systeemvereisten voor de Content Transfer-tool zijn AEM 6.3 + en JAVA 8. Als u een lagere AEM gebruikt, moet u de opslagplaats voor inhoud upgraden naar AEM 6.5 om het gereedschap Inhoud overbrengen te kunnen gebruiken.

* Java moet zijn geconfigureerd in de AEM omgeving, zodat de `java` kan worden uitgevoerd door de gebruiker die AEM start.

* U kunt het gereedschap Inhoud overbrengen gebruiken met de volgende typen gegevensopslag: File Data Store, S3 Data Store, Shared S3 Data Store en Azure Blob Store Data Store.

* Als u een *Sandbox-omgeving*, zorgt u ervoor dat uw omgeving actueel is en wordt bijgewerkt naar de nieuwste versie. Als u een *Productieomgeving* gebruikt, wordt deze automatisch bijgewerkt.

* Om een inname te beginnen, moet u tot de lokale AEM behoren **beheerders** in de instantie Cloud Service waarnaar u inhoud overbrengt. Niet-geprivilegieerde gebruikers kunnen geen toegang krijgen zonder handmatig het migratietoken op te geven.

* Als de instelling **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingeschakeld, wordt de gehele bestaande opslagplaats verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud kan worden ingevoerd. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Dit geldt ook voor een beheerder die is toegevoegd aan de **beheerders** groep. De gebruiker moet opnieuw aan worden toegevoegd **beheerders** groep om het toegangstoken voor het Hulpmiddel van de Overdracht van de Inhoud terug te winnen.

* Oplossingen ondersteunen het samenvoegen van inhoud van meerdere bronnen in de instantie van de Cloud Service van het doel niet als de inhoud van de twee bronnen naar dezelfde paden op het doel wordt verplaatst. Als u inhoud van meerdere bronnen naar één doelinstantie wilt verplaatsen, moet u ervoor zorgen dat de inhoudspaden van de Cloud Servicen elkaar niet overlappen.

* De extractiecode is 14 dagen geldig vanaf het moment dat deze is gemaakt/vernieuwd. Het kan op elk ogenblik worden verlengd. Als de extractietoets is verlopen, kunt u geen extractie uitvoeren.

* Met het CTT-hulpprogramma (Content Transfer Tool) wordt geen inhoudanalyse uitgevoerd voordat inhoud van de broninstantie naar de doelinstantie wordt overgebracht. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een publicatieomgeving. Alle inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. De gebruiker heeft de capaciteit om een migratie in te voeren die in een instantie Auteur of Publish of beide wordt geplaatst. Men adviseert dat terwijl het bewegen van inhoud naar een instantie van de Productie, CTT op de instantie van de bronauteur moet worden geïnstalleerd om inhoud naar de instantie van de doelauteur te verplaatsen en zo ook, CTT op de bron te installeren publiceer instantie om inhoud naar het doel te verplaatsen publiceer instantie. Zie [Het gereedschap Inhoud overbrengen uitvoeren op een instantie Publiceren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-ctt-on-publish) voor meer informatie .

* De gebruikers en de Groepen die door het Hulpmiddel van de Overdracht van de Inhoud worden overgebracht zijn slechts die die door de inhoud worden vereist om aan toestemmingen te voldoen. De *Extractie* proceskopieën `/home` in de migratieset en de *Inname* proces kopieert alle gebruikers en groepen die in gemigreerde inhoud ACLs van verwijzingen worden voorzien. Als u de bestaande gebruikers automatisch wilt toewijzen aan hun IMS-id&#39;s, raadpleegt u [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration).

* Tijdens de extractiefase wordt de Content Transfer-tool uitgevoerd op een actieve AEM-broninstantie.

* Na het voltooien van de *Extractie* fase van het proces voor de overdracht van inhoud en vóór het begin van de *Ingestiefase* om inhoud in uw as a Cloud Service AEM in te voeren *Werkgebied* of *Productie* instanties, zult u een steunkaartje moeten registreren om Adobe van uw voornemen op de hoogte te brengen om te lopen *Inname* zodat Adobe ervoor kan zorgen dat er geen onderbrekingen optreden tijdens de *Inname* proces. U zult het steunkaartje 1 week voorafgaand aan uw gepland moeten registreren *Inname* datum. Zodra, hebt u het steunkaartje voorgelegd, zal het ondersteuningsteam begeleiding op volgende stappen verstrekken. U kunt een steunkaartje met de volgende details registreren:

   * De exacte datum en geschatte tijd (met uw tijd-streek) wanneer u van plan bent om te beginnen *Inname* fase.
   * Omgevingstype (werkgebied of productie) waarin u gegevens wilt opnemen.
   * Programma-id.

* De *Ingestiefase* voor de auteur schalen neer de volledige auteursplaatsing. Dit betekent dat de auteur-AEM niet beschikbaar is tijdens het volledige opnameproces. Zorg er ook voor dat er geen Cloud Manager-pijplijnen worden uitgevoerd terwijl u het dialoogvenster *Inname* fase.

* Wanneer u `Amazon S3` of `Azure` aangezien de gegevensopslag op het bron AEM systeem, de gegevensopslag zou moeten worden gevormd zodat de opgeslagen vlekken niet kunnen worden geschrapt (huisvuil verzameld). Dit verzekert integriteit van indexgegevens en het nalaten om deze manier te vormen kan in ontbroken extracties wegens gebrek aan integriteit van deze indexgegevens resulteren.

* Als u douaneindexen gebruikt, moet u ervoor zorgen om de douaneindexen te vormen met `tika` knooppunt voordat u Content Transfer Tool uitvoert. Zie [De nieuwe indexdefinitie voorbereiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#preparing-the-new-index-definition) voor meer informatie .

* Als u aanvullende onderdelen wilt maken, is het van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

* Als u van plan bent versies op te nemen als onderdeel van een migratieset en als u aanvullende versies uitvoert met `wipe=false`Vervolgens moet u versiebeheer uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld wilt houden en extra-ups wilt uitvoeren in een migratieset, moet u de opname uitvoeren als `wipe=true`.

## Volgende functies {#whats-next}

Nadat u de richtlijnen, de beste praktijken en de belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen hebt geleerd, kunt u het gereedschap nu installeren en gebruiken, te beginnen met het maken van een migratieset. Zie [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) voor meer informatie.
