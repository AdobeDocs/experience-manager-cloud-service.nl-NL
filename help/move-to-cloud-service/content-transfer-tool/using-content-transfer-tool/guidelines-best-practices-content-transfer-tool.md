---
title: Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen
description: Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen
source-git-commit: b421cc5e6078112adecb856d723a1bae628d8ec7
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 25%

---


# Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen {#guidelines}

## Richtlijnen en best practices {#best-practices}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Richtlijnen en best practices"
>abstract="Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen controleren, waaronder taken voor het opschonen van revisies, overwegingen voor schijfruimte en meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="Belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Belangrijke overwegingen voor het gebruik van het gereedschap Toewijzing gebruiker"

Bekijk de onderstaande sectie voor meer informatie over richtlijnen en aanbevolen procedures voor het gebruik van de Content Transfer-tool:

* Het is raadzaam om [Revision Cleanup](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) en [consistentiecontroles voor de dataopslagplaats](https://helpx.adobe.com/nl/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) op de **bronrepository** uit te voeren om potentiële problemen te identificeren en de repository te verkleinen.

* Als de AEM Cloud CDN-configuratie (Content Delivery Network) is geconfigureerd met een lijst met toegestane IP&#39;s, moet u ervoor zorgen dat de IP&#39;s van de bronomgeving worden toegevoegd aan deze lijst, zodat de bronomgeving en de AEM Cloud-omgeving met elkaar kunnen communiceren.

* Tijdens de opnamefase wordt het aanbevolen dat u de modus voor *wissen* inschakelt. Hiermee wordt de bestaande repository (auteur of publicatie) in de AEM Cloud Service-doelomgeving volledig gewist en vervolgens bijgewerkt met de content van de migratieset. Deze modus is veel sneller dan de modus voor niet-wissen, waarbij de migratieset boven op de huidige content wordt toegepast.

* Wanneer alle content is verplaatst, is de juiste projectstructuur in de Cloud Service-omgeving vereist. Anders wordt de content niet correct weergegeven in de Cloud Service-omgeving.

* Voordat u de content Transfer-tool uitvoert, moet u ervoor zorgen dat er voldoende schijfruimte is in de submap `crx-quickstart` van de AEM-broninstantie. Dit is omdat de Content Transfer-tool een lokale kopie van de repository maakt die later wordt geüpload naar de migratieset.
De algemene formule voor het berekenen van de vereiste vrije schijfruimte is als volgt:
   `data store size + node store size * 1.5`

   * *Grootte van dataopslagplaats*: De Content Transfer-tool gebruikt 64 GB, ook als de werkelijke dataopslagplaats groter is.
   * *Grootte van node-opslagplaats*: De grootte van de segmentopslagdirectory of de grootte van de MongoDB-database.
Voor een segmentopslagplaats van 20 GB is dus 94 GB aan vrije schijfruimte vereist.

* Een migratieset moet gedurende de gehele activiteit van de inhoudsoverdracht worden gehandhaafd om de toevoeging van inhoud te steunen. Aangezien maximaal tien migratiesets tegelijk tijdens de activiteit van de inhoudsoverdracht kunnen worden gemaakt en onderhouden, wordt aangeraden de opslagplaats voor inhoud dienovereenkomstig te verdelen om ervoor te zorgen dat de migratiesets niet opraken.

## Belangrijke overwegingen voordat u het gereedschap Inhoud overbrengen gebruikt {#important-considerations}

Bekijk de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Content Transfer-tool:

* De minimale systeemvereisten voor de Content Transfer-tool zijn AEM 6.3 + en JAVA 8. Als u een lagere AEM gebruikt, moet u de opslagplaats voor inhoud upgraden naar AEM 6.5 om het gereedschap Inhoud overbrengen te kunnen gebruiken.

* Java moet op het AEM milieu worden gevormd, zodat het `java` bevel door de gebruiker kan worden uitgevoerd die AEM begint.

* Het wordt aanbevolen oudere versies van het gereedschap Inhoud overbrengen te verwijderen bij de installatie van versie 1.3.0, omdat het programma een belangrijke architecturale wijziging heeft ondergaan. Met 1.3.0 moet u ook nieuwe migratiesets maken en de extractie en inname van de nieuwe migratiesets opnieuw uitvoeren.

* U kunt het gereedschap Inhoud overbrengen gebruiken met de volgende typen gegevensopslag: File Data Store, S3 Data Store, Shared S3 Data Store en Azure Blob Store Data Store.

* Als u een *Sandbox Milieu* gebruikt, zorg ervoor dat uw milieu huidig is en aan de recentste versie wordt bevorderd. Als u een *Productieomgeving* gebruikt, wordt deze automatisch bijgewerkt.

* Om het hulpmiddel van de Overdracht van de Inhoud te gebruiken, moet u een admin gebruiker op uw broninstantie zijn en tot de lokale AEM **beheerders** groep in de instantie behoren van de Cloud Service u inhoud overbrengt naar. Zonder deze machtigingen kunnen gebruikers het toegangstoken tot de Content Transfer-tool niet ophalen.

* Als de instelling **Bestaande inhoud op een Cloud-instantie vegen voor inname** is ingeschakeld, wordt de gehele bestaande opslagruimte verwijderd en wordt een nieuwe opslagplaats gemaakt waarin inhoud wordt opgenomen. Dit betekent dat alle instellingen, inclusief de machtigingen voor de Cloud Service van het doel, opnieuw worden ingesteld. Dit geldt ook voor een beheerder die wordt toegevoegd aan de groep **beheerders**. De gebruiker moet aan **beheerders** groep opnieuw worden toegevoegd om het toegangstoken voor CTT terug te winnen.

* Het toegangstoken kan periodiek of na een specifieke tijdspanne verlopen of nadat het milieu van de Cloud Service is bevorderd. Als het toegangstoken is verlopen, zult u niet met de instantie van de Cloud Service kunnen verbinden en u moet het nieuwe toegangstoken terugwinnen. Het statuspictogram dat aan een bestaande migratieset is gekoppeld, wordt gewijzigd in een rode cloud en er wordt een bericht weergegeven wanneer u de muisaanwijzer op de desbetreffende cloud plaatst.

* Met het CTT-hulpprogramma (Content Transfer Tool) wordt geen inhoudanalyse uitgevoerd voordat inhoud van de broninstantie naar de doelinstantie wordt overgebracht. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een publicatieomgeving. Alle inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. De gebruiker heeft de capaciteit om een migratie in te voeren die in een instantie Auteur of Publish of beide wordt geplaatst. Men adviseert dat terwijl het bewegen van inhoud naar een instantie van de Productie, CTT op de instantie van de bronauteur moet worden geïnstalleerd om inhoud naar de instantie van de doelauteur te verplaatsen en zo ook, CTT op de bron te installeren publiceer instantie om inhoud naar het doel te verplaatsen publiceer instantie. Raadpleeg [Het gereedschap Inhoud overbrengen uitvoeren op een instantie Publiceren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-ctt-on-publish) voor meer informatie.

* De gebruikers en de Groepen die door het Hulpmiddel van de Overdracht van de Inhoud worden overgebracht zijn slechts die die door de inhoud worden vereist om aan toestemmingen te voldoen. Met het proces *Extractie* wordt de gehele `/home` naar de migratieset gekopieerd en met het proces *Ingestie* worden alle gebruikers en groepen gekopieerd waarnaar in de gemigreerde inhoud-ACL&#39;s wordt verwezen. Als u de bestaande gebruikers en groepen automatisch wilt toewijzen aan hun IMS-id&#39;s, raadpleegt u [Hulpprogramma voor het toewijzen van gebruikers gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration).

* Tijdens de extractiefase wordt de Content Transfer-tool uitgevoerd op een actieve AEM-broninstantie.

* Nadat u de *Extractie*-fase van het proces voor de overdracht van inhoud hebt voltooid en voordat u de *Ingestiefase* start om inhoud in uw AEM as a Cloud Service *Stage* of *Production*-instanties in te voeren, moet u een ondersteuningsticket registreren om de Adobe te informeren over uw voornemen om *Ingestie&lt;a9 uit te voeren/> zodat Adobe ervoor kan zorgen dat er geen onderbrekingen optreden tijdens het* Ingestieproces *.* U zult het steunkaartje 1 week vóór uw geplande *Ingestiedatum* moeten registreren. Zodra, hebt u het steunkaartje voorgelegd, zal het ondersteuningsteam begeleiding op volgende stappen verstrekken. U kunt een steunkaartje met de volgende details registreren:

   * De nauwkeurige datum en de geschatte tijd (met uw tijd-streek) wanneer u van plan bent om de *Ingestiefase* te beginnen.
   * Omgevingstype (werkgebied of productie) waarin u gegevens wilt opnemen.
   * Programma-id.

* De *Ingestiefase* voor de auteur schalen de volledige auteurplaatsing. Dit betekent dat de auteur-AEM niet beschikbaar is tijdens het volledige opnameproces. Zorg er ook voor dat er geen Cloud Manager-pijpleidingen worden uitgevoerd terwijl u de *Ingestiefase* uitvoert.

* Wanneer u `Amazon S3` of `Azure` gebruikt als gegevensopslag op het bron AEM systeem, moet de gegevensopslag zo worden geconfigureerd dat de opgeslagen blokken niet kunnen worden verwijderd (opschonen). Dit verzekert integriteit van indexgegevens en het nalaten om deze manier te vormen kan in ontbroken extracties wegens gebrek aan integriteit van deze indexgegevens resulteren.

* Als u douaneindexen gebruikt, moet u ervoor zorgen om de douaneindexen met `tika` knoop te vormen alvorens het Hulpmiddel van de Overdracht van de Inhoud in werking te stellen. Raadpleeg [De nieuwe indexdefinitie voorbereiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#preparing-the-new-index-definition) voor meer informatie.

* Als u aanvullende onderdelen wilt maken, is het van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

* Als u van plan bent versies op te nemen als onderdeel van een migratieset en extra-ups uitvoert met `wipe=false`, dan moet u versiezuivering uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld houdt en top-ups uitvoert in een migratieset, moet u de opname uitvoeren als `wipe=true`.

## Volgende functies {#whats-next}

Nadat u de richtlijnen, de beste praktijken en de belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen hebt geleerd, kunt u het gereedschap nu installeren en gebruiken, te beginnen met het maken van een migratieset. Zie [Aan de slag met Content Transfer To](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) voor meer informatie.
