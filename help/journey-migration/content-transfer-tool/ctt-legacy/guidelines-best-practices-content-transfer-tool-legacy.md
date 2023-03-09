---
title: Richtlijnen en aanbevolen procedures voor het gebruik van Content Transfer Tool (verouderd)
description: Richtlijnen en aanbevolen procedures voor het gebruik van het gereedschap Inhoud overbrengen
hide: true
hidefromtoc: true
exl-id: 03449606-0fb4-4a9f-9abb-6b17c27a6046
source-git-commit: 3c8035e4db5729f58bae29136a32a0b9944d6a2f
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 13%

---

# Richtlijnen en aanbevolen procedures voor het gebruik van Content Transfer Tool (verouderd) {#guidelines}

## Richtlijnen en best practices {#best-practices}

Bekijk de onderstaande sectie voor meer informatie over richtlijnen en aanbevolen procedures voor het gebruik van de Content Transfer-tool:

* Uitvoeren [Revisie opschonen](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) en [consistentiecontroles gegevensopslag](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html?lang=en) op de **bron** opslagplaats om potentiële problemen te identificeren en de grootte van de opslagplaats te verminderen.

* Als het AEM Netwerk van de Levering van de Inhoud van de Auteur van de Wolk (CDN) wordt gevormd om een lijst van gewenste personen van IPs te hebben, zorg ervoor dat het bronmilieu IPs ook aan de lijst van gewenste personen wordt toegevoegd. Dit zorgt ervoor dat de bronomgeving en AEM Cloud-omgeving met elkaar kunnen communiceren.

* Voer de inname uit met de *vegen* Modus ingeschakeld waarbij de bestaande gegevensopslagruimte (auteur of publicatie) in de AEM Cloud Service-doelomgeving wordt verwijderd en vervolgens bijgewerkt met de gegevens van de migratieset. Deze modus is veel sneller dan de modus voor niet-wissen, waarbij de migratieset boven op de huidige content wordt toegepast.

* Wanneer alle content is verplaatst, is de juiste projectstructuur in de Cloud Service-omgeving vereist. Anders wordt de content niet correct weergegeven in de Cloud Service-omgeving.

* Voordat u de content Transfer-tool uitvoert, moet u ervoor zorgen dat er voldoende schijfruimte is in de submap `crx-quickstart` van de AEM-broninstantie. Dit is omdat de Content Transfer-tool een lokale kopie van de repository maakt die later wordt geüpload naar de migratieset.
De algemene formule voor het berekenen van de vereiste vrije schijfruimte is als volgt:
   `data store size + node store size * 1.5`

   * *Grootte van dataopslagplaats*: De Content Transfer-tool gebruikt 64 GB, ook als de werkelijke dataopslagplaats groter is.
   * *Grootte van node-opslagplaats*: De grootte van de segmentopslagdirectory of de grootte van de MongoDB-database.
Voor een segmentopslagplaats van 20 GB is dus 94 GB aan vrije schijfruimte vereist.

* Een migratieset moet gedurende de gehele activiteit van de inhoudsoverdracht worden gehandhaafd om de aanvulling van de inhoud te steunen. Omdat maximaal tien migratiesets tegelijk tijdens de activiteit van de inhoudsoverdracht kunnen worden gemaakt en onderhouden, wordt het aanbevolen de opslagplaats voor inhoud dienovereenkomstig te splitsen. Dit zorgt ervoor dat de migratiesets niet opraken.

## Belangrijke overwegingen voordat u het gereedschap Inhoud overbrengen gebruikt {#important-considerations}

Bekijk de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Content Transfer-tool:

* De minimale systeemvereisten voor Content Transfer Tool zijn AEM 6.3 + en Java™ 8. Als u een lagere AEM gebruikt, moet u de opslagplaats voor inhoud upgraden naar AEM 6.5 om het gereedschap Inhoud overbrengen te kunnen gebruiken.

* Java™ moet zijn geconfigureerd in de AEM omgeving, zodat de `java` kan worden uitgevoerd door de gebruiker die AEM start.

* Verwijder oudere versies van het gereedschap Inhoud overbrengen bij de installatie van versie 1.3.0 omdat het gereedschap een belangrijke architecturale wijziging had ondergaan. Met 1.3.0 moet u ook migratiesets maken en extractie en inname van de nieuwe migratiesets opnieuw uitvoeren.

* U kunt het gereedschap Inhoud overbrengen gebruiken met de volgende typen gegevensopslag: File Data Store, S3 Data Store, Shared S3 Data Store en Azure Blob Store Data Store.

* Als u een *Sandbox-omgeving*, zorgt u ervoor dat uw omgeving actueel is en wordt bijgewerkt naar de nieuwste versie. Als u een *Productieomgeving* gebruikt, wordt deze automatisch bijgewerkt.

* Om het hulpmiddel van de Overdracht van de Inhoud te gebruiken, moet u een admin gebruiker op uw broninstantie zijn en tot de lokale AEM behoren **beheerders** in de instantie Cloud Service waarnaar u inhoud overbrengt. De onbevoorrechte gebruikers kunnen niet het toegangstoken terugwinnen om het Hulpmiddel van de Overdracht van de Inhoud te gebruiken.

* Als de instelling **Bestaande inhoud vegen op Cloud-instantie voordat deze wordt ingesloten** is ingeschakeld, wordt de gehele bestaande opslagplaats verwijderd en wordt een opslagplaats gemaakt waarin inhoud kan worden ingevoerd. Dit werkschema betekent dat het alle montages met inbegrip van toestemmingen op de instantie van de doelCloud Service terugstelt. Dit resultaat geldt zelfs voor een beheerder die is toegevoegd aan de **beheerder** groep. De gebruiker moet aan de **beheerder** groep om het toegangstoken voor het Hulpmiddel van de Overdracht van de Inhoud terug te winnen.

* Het gereedschap Inhoud overbrengen ondersteunt het samenvoegen van inhoud van meerdere bronnen naar de instantie van de Cloud Service target niet als de inhoud van de twee bronnen naar dezelfde paden op het doel wordt verplaatst. Als u inhoud van meerdere bronnen naar één doelinstantie wilt verplaatsen, moet u ervoor zorgen dat de inhoudspaden van de Cloud Servicen elkaar niet overlappen.

* Het toegangstoken kan periodiek of na een specifieke tijdspanne verlopen of nadat het milieu van de Cloud Service is bevorderd. Als de toegangstoken is verlopen, kunt u niet met de instantie van de Cloud Service verbinden. In dat geval, moet u het nieuwe toegangstoken terugwinnen. Het statuspictogram dat aan een bestaande migratieset is gekoppeld, verandert in een rode cloud en geeft een bericht weer wanneer u de muisaanwijzer op de cloud plaatst.

* Met het CTT-hulpprogramma (Content Transfer Tool) wordt geen inhoudanalyse uitgevoerd voordat inhoud van de broninstantie naar de doelinstantie wordt overgebracht. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een publicatieomgeving. De inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. Gebruiker kan een migratieset opnemen in een instantie Auteur of een instantie Publiceren of beide. Tijdens het verplaatsen van inhoud naar een instantie Production, installeert u CTT op de instantie source Author om inhoud naar de instantie targetAuthor te verplaatsen. En installeer op dezelfde manier CTT op de bronPublish instantie om inhoud naar het doelPublish instantie te verplaatsen. Zie [Het gereedschap Inhoud overbrengen uitvoeren op een instantie Publiceren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#running-tool) voor meer informatie .

* De gebruikers en de Groepen die door het Hulpmiddel van de Overdracht van de Inhoud worden overgebracht zijn slechts die die door de inhoud worden vereist om aan toestemmingen te voldoen. De *Extractie* proceskopieën `/home` in de migratieset en de *Inname* proces kopieert alle gebruikers en groepen die in gemigreerde inhoud ACLs van verwijzingen worden voorzien. Als u de bestaande gebruikers en groepen automatisch wilt toewijzen aan hun IMS-id&#39;s, raadpleegt u [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=en).

* Tijdens de extractiefase wordt de Content Transfer-tool uitgevoerd op een actieve AEM-broninstantie.

* Na het voltooien van de *Extractie* fase van het proces voor de overdracht van inhoud en vóór het begin van de *Ingestiefase* om inhoud in uw as a Cloud Service AEM in te voeren *Werkgebied* of *Productie* instanties, registreer een steunkaartje. Adobe op de hoogte stellen van uw voornemen om *Inname* zodat Adobe ervoor kan zorgen dat er geen onderbrekingen optreden tijdens de *Inname* proces. Logboek één week voor uw geplande ondersteuningsticket *Inname* datum. Nadat u het steunkaartje hebt voorgelegd, verstrekt het ondersteuningsteam raad over de volgende stappen. Logboek een steunkaartje met de volgende details:

   * De exacte datum en geschatte tijd (met uw tijd-streek) wanneer u van plan bent om te beginnen *Inname* fase.
   * Omgevingstype (werkgebied of productie) waarin u gegevens wilt opnemen.
   * Programma-id.

* De *Ingestiefase* voor de auteur schalen neer de volledige auteursplaatsing. Dit proces betekent dat de auteur AEM niet beschikbaar is tijdens het hele innameproces. Zorg er ook voor dat er geen Cloud Manager-pijplijnen worden uitgevoerd terwijl u het dialoogvenster *Inname* fase.

* Wanneer u `Amazon S3` of `Azure` aangezien de gegevensopslag op het bron AEM systeem, de gegevensopslag zou moeten worden gevormd zodat de opgeslagen vlekken niet kunnen worden geschrapt (huisvuil verzameld). Dit verzekert integriteit van indexgegevens en het nalaten om deze manier te vormen kan in ontbroken extracties wegens gebrek aan integriteit van deze indexgegevens resulteren.

* Als u douaneindexen gebruikt, moet u ervoor zorgen om de douaneindexen te vormen met `tika` knooppunt voordat u Content Transfer Tool uitvoert. Zie [De nieuwe indexdefinitie voorbereiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=en#preparing-the-new-index-definition) voor meer informatie .

* Als u aanvullende onderdelen wilt uitvoeren, moet u ervoor zorgen dat de inhoudstructuur van de bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de extractie van de aanvulling wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

* Als u van plan bent versies op te nemen als onderdeel van een migratieset en als u aanvullende versies uitvoert met `wipe=false`Vervolgens moet u versiebeheer uitschakelen vanwege een huidige beperking in het gereedschap Inhoud overbrengen. Als u versiereiniging liever ingeschakeld wilt houden en extra-ups wilt uitvoeren in een migratieset, moet u de opname uitvoeren als `wipe=true`.

## Volgende functies {#whats-next}

Nadat u de richtlijnen, de beste praktijken en de belangrijke overwegingen voor het gebruik van het gereedschap Inhoud overbrengen hebt geleerd, kunt u het gereedschap nu installeren en gebruiken, te beginnen met het maken van een migratieset. Zie [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) voor meer informatie.
