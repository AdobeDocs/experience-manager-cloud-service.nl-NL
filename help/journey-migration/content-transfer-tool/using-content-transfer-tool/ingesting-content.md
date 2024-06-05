---
title: Inhoud in Cloud Service invoegen
description: Leer hoe u met de Cloud Acceleration Manager inhoud kunt opnemen van uw migratieset naar een bestemmings Cloud Service-instantie.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2905'
ht-degree: 1%

---

# Inhoud in Cloud Service invoegen {#ingesting-content}

## Ingestieproces in Cloud Acceleration Manager {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inktatie van inhoud"
>abstract="Ingestie verwijst naar het opnemen van inhoud van de migratie die is ingesteld in de Cloud Service-instantie van de bestemming. De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html#top-up-extraction-process" text="Extractie naar boven"

Voer de onderstaande stappen uit om uw migratieset in te voeren met gebruik van Cloud Acceleration Manager:

1. Ga naar Cloud Acceleration Manager. Klik op de projectkaart en klik op de kaart voor inhoudsoverdracht. Navigeren naar **Ingestietaken** en klik op **Nieuwe inname**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Controleer de innamecontrolelijst en zorg ervoor dat alle stappen zijn voltooid. Deze stappen zijn nodig om een succesvolle inname te waarborgen. Ga door naar de **Volgende** stap alleen als de checklist is voltooid.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geef de vereiste informatie op om een opname te maken.

   * **Migratieset:** Selecteer de migratieset die de geëxtraheerde gegevens als bron bevat.
      * De Reeksen van de migratie zullen verlopen na een lange periode van inactiviteit, zodat wordt verwacht dat de inname vrij snel na de extractie plaatsvindt. Controleren [Vervaldatum migratieset](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor meer informatie.

   >[!TIP]
   > Als de extractie wordt uitgevoerd, wordt dit in het dialoogvenster aangegeven. Nadat de extractie is voltooid, wordt de inname automatisch gestart. Als de extractie mislukt of wordt gestopt, wordt de innametaak geannuleerd.

   * **Doel:** Selecteer de doelomgeving. In deze omgeving wordt de inhoud van de migratieset opgenomen.
      * De oplossingen steunen geen bestemmingen van het type Snelle Milieu van de Ontwikkeling (RDE) of Voorproef, en zij verschijnen niet als mogelijke bestemmingskeus, zelfs als de gebruiker toegang tot het heeft.
      * Terwijl een migratiereeks in veelvoudige bestemmingen gelijktijdig kan worden opgenomen, kan een bestemming het doel van slechts één lopende of wachtende opname tegelijkertijd zijn.

   * **Niveau:** Selecteer de laag. (Auteur/Publicatie).
      * Als de bron `Author`, wordt aanbevolen het geneesmiddel in te nemen in de `Author` laag op het doel. Evenzo als de bron `Publish`, moet het doel `Publish` ook.

   >[!NOTE]
   > Als de doellaag `Author`, wordt de auteurinstantie gesloten tijdens de lengte van de opname en niet beschikbaar voor gebruikers (bijvoorbeeld, auteurs of iedereen die onderhoud uitvoert). De reden is om het systeem te beschermen en om eventuele veranderingen te voorkomen die verloren zouden kunnen gaan of een innameconflict zouden veroorzaken. Zorg ervoor dat uw team zich hiervan bewust is. Houd er ook rekening mee dat de omgeving tijdens de opname door de auteur wordt genegeerd.

   * **Sluitereffect:** Kies de optie `Wipe` value
      * De **Sluitereffect** Hiermee stelt u het beginpunt van de opname van het doel in. Indien **Sluitereffect** is ingeschakeld, wordt de bestemming, inclusief alle inhoud, teruggezet naar de versie van AEM die is opgegeven in Cloud Manager. Als deze optie niet is ingeschakeld, behoudt de bestemming de huidige inhoud als beginpunt.
      * Deze optie doet **NOT** van invloed op de manier waarop de inname van inhoud wordt uitgevoerd. De inname gebruikt altijd een strategie voor het vervangen van inhoud en _niet_ een samenvoegstrategie voor inhoud, zowel in **Sluitereffect** en **Niet-sluitereffect** In bepaalde gevallen overschrijft de opname van een migratieset de inhoud van hetzelfde pad op de bestemming. Als de migratieset bijvoorbeeld `/content/page1` en de bestemming bevat al `/content/page1/product1`, verwijdert de inname de gehele `page1` pad en de bijbehorende subpagina&#39;s, inclusief `product1`en vervangt u deze door de inhoud in de migratieset. Dit betekent dat een zorgvuldige planning moet worden uitgevoerd wanneer een **Niet-sluitereffect** opname naar een bestemming die inhoud bevat die behouden moet blijven.

   >[!IMPORTANT]
   > Als de instelling **Sluitereffect** wordt toegelaten voor de opname, stelt het de volledige bestaande bewaarplaats met inbegrip van de gebruikerstoestemmingen op de instantie van de doelCloud Service opnieuw in. Dit opnieuw instellen geldt ook voor een beheerder die is toegevoegd aan de **beheerders** groep en die gebruiker moet opnieuw aan de beheerdersgroep worden toegevoegd om een opname te beginnen.

   * **Pre-kopie:** Kies de optie `Pre-copy` value
      * U kunt de optionele pre-copy stap uitvoeren om de inname aanzienlijk te versnellen. Zie [Inschakelen met AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) voor meer informatie .
      * Als het opnemen met pre-copy wordt gebruikt (voor S3 of Azure Data Store), wordt het geadviseerd om te lopen `Author` Inname eerst alleen. Zo versnelt u de `Publish` inname wanneer deze later wordt uitgevoerd.

   >[!IMPORTANT]
   > U kunt een opname aan het bestemmingsmilieu in werking stellen slechts als u tot lokaal behoort **AEM** groep op de de auteursdienst van de bestemmingsCloud Service. Als u geen inname kunt starten, zie [Kan inname niet starten](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) voor meer informatie .

1. Wanneer de keuze voor inname eenmaal is gemaakt, wordt een schatting van de duur van de inname weergegeven. Dit is een inspanningsschatting gebaseerd op historische gegevens van vergelijkbare ingestie.

   * Deze schatting wordt alleen berekend en weergegeven als de waarden voor &#39;grootte controleren&#39; van de extractie zijn verzameld en beschikbaar zijn.
   * Deze waarde is een schatting en mag, hoewel intelligent berekend, niet als exact worden beschouwd. De werkelijke duur kan door verschillende factoren worden gewijzigd.
   * Tijdens het uitvoeren van de opname is deze waarde ook beschikbaar in het dialoogvenster Duur, dat u kunt openen via &quot;**Duur weergeven**&quot; de werking van de inname.

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_estimate"
>title="Schatting van de opzettingsduur"
>abstract="Een geschatte duur van een bepaalde inname kan worden weergegeven om een algemene indruk te geven van de duur ervan. De nauwkeurigheid ervan is beperkt."

![afbeelding](/help/journey-migration/content-transfer-tool/assets/estimate.png)

1. Klikken **Ingest**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. U kunt de opname van de de lijstmening van Banen van de Opname dan controleren en het de actiemenu van de opname gebruiken om de duur en het logboek te bekijken aangezien de opname vordert.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klik op de knop **i)** voor meer informatie over de innametaak. U kunt de duur van elke stap van de Ingestie zien wanneer het loopt of door te klikken **...** en klik vervolgens op **Duur weergeven**. Uit de informatie over de extractie blijkt ook dat men zich realiseert wat er wordt ingeslikt.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## Top Up-inname {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Top Up-inname"
>abstract="Gebruik de functie top-up om inhoud te verplaatsen die is gewijzigd sinds de vorige activiteit van de inhoudsoverdracht. Controleer de logboeken op fouten of waarschuwingen na voltooiing van de inname. Eventuele fouten moeten onmiddellijk worden verholpen door de gemelde problemen te verhelpen of door contact op te nemen met de klantenservice van de Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html" text="Logbestanden weergeven"

Het gereedschap Inhoud overbrengen heeft een functie waarmee u differentiële inhoud kunt extraheren door een *top-up* van de migratieset. Hierdoor kan de migratieset worden gewijzigd, zodat alleen de inhoud wordt opgenomen die sinds de vorige extractie is gewijzigd, zonder dat alle inhoud opnieuw moet worden geëxtraheerd.

>[!NOTE]
>Na de eerste overdracht van inhoud wordt aanbevolen regelmatig differentiële toevoegingen toe te passen om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat deze live gaat met de Cloud Service. Als u de pre-exemplaarstap voor de eerste opname hebt gebruikt, kunt u pre-exemplaar voor verdere bovenop-up ingestions overslaan (als de top-up migratie vastgestelde grootte minder dan 200 GB is). De reden is dat het tijd kan toevoegen aan het hele proces.

Als u differentiële inhoud wilt innemen nadat bepaalde indelingen zijn voltooid, moet u een [Extractie bovenaan](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)en gebruikt u vervolgens de innamemethode met de **Sluitereffect** option **uitgeschakeld**. Zorg ervoor dat u de **Sluitereffect** uitleg hierboven om te voorkomen dat inhoud die al op de bestemming staat, verloren gaat.

Begin met het maken van een Ingestietaak en zorg ervoor dat **Sluitereffect** is uitgeschakeld tijdens de inname, zoals hieronder wordt getoond:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Problemen oplossen {#troubleshooting}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_troubleshooting"
>title="Problemen met inslikken van inhoud oplossen"
>abstract="Verwijs naar de innamelogboeken en de documentatie om oplossingen aan gemeenschappelijke redenen te vinden waarom een inname kan ontbreken en de manier vinden om het probleem te bevestigen. Als de injectie eenmaal is vastgezet, kan deze weer worden uitgevoerd."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html" text="Inhoudsoverdrachten valideren"

### CAM Kan migratietoken niet ophalen {#cam-unable-to-retrieve-the-migration-token}

Het automatisch ophalen van het migratietoken kan om verschillende redenen mislukken, waaronder u [een IP-lijst van gewenste personen instellen via Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) in de omgeving van de doelCloud Service. In dergelijke scenario&#39;s, ziet u de volgende dialoogdoos wanneer u probeert om een opname te beginnen:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

U kunt het migratietoken handmatig ophalen door op de koppeling Token ophalen in het dialoogvenster te klikken. Er wordt een ander tabblad geopend waarin het token wordt weergegeven. U kunt het token vervolgens kopiëren en plakken in het dialoogvenster **Invoer van migratietoken** veld. Nu moet je de inname kunnen starten.

>[!NOTE]
>
>De token is beschikbaar voor gebruikers die tot de lokale server behoren **AEM** groep op de de auteursdienst van de bestemmingsCloud Service.

### Kan inname niet starten {#unable-to-start-ingestion}

U kunt een opname aan het bestemmingsmilieu in werking stellen slechts als u tot lokaal behoort **AEM** groep op de de auteursdienst van de bestemmingsCloud Service. Als u niet tot de groep van AEM beheerders behoort, ziet u een fout zoals hieronder getoond wanneer u probeert om een opname te beginnen. U kunt de beheerder vragen om u toe te voegen aan de lokale **AEM** of vraag om de token zelf, die u vervolgens in de **Invoer van migratietoken** veld.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Kan de migratieservice niet bereiken {#unable-to-reach-migration-service}

Nadat een opname wordt gevraagd, kan een bericht als het volgende aan de gebruiker worden voorgesteld: &quot;De migratiedienst op het bestemmingsmilieu is onbereikbaar. Als dat het geval is, probeert u het later opnieuw of neemt u contact op met de Adobe.&quot;

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Dit bericht geeft aan dat de Cloud Acceleration Manager de migratieservice van de doelomgeving niet kan bereiken om de opname te starten. Dit kan om verschillende redenen gebeuren.

>[!NOTE]
> 
> Het veld &quot;Migratietoken&quot; wordt weergegeven omdat het ophalen van dat token in sommige gevallen niet is toegestaan. Door het handmatig aanbrengen van de injectie toe te staan, kan de gebruiker de opname snel starten, zonder extra hulp. Als het token is opgegeven en het bericht nog steeds wordt weergegeven, was het ophalen van het token niet het probleem.

* AEM as a Cloud Service handhaaft de milieustaat, en moet af en toe de migratiedienst opnieuw beginnen om diverse normale redenen. Als die dienst opnieuw begint, kan het niet worden bereikt, maar is uiteindelijk beschikbaar.
* Het is mogelijk dat een ander proces op de instantie wordt uitgevoerd. Als [Versie-updates AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html) wordt een update toegepast, is het systeem mogelijk bezet en is de migratieservice regelmatig niet beschikbaar. Zodra dat proces is voltooid, kan opnieuw worden geprobeerd om met de inname te beginnen.
* Als een [IP de Lijst van gewenste personen is toegepast](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) via Cloud Manager wordt het bereiken van de migratieservice door Cloud Acceleration Manager geblokkeerd. Een IP adres kan niet voor ingesties worden toegevoegd omdat zijn adres dynamisch is. Momenteel, is de enige oplossing de IP lijst van gewenste personen tijdens de opname en het indexeren proces onbruikbaar te maken.
* Er kunnen andere redenen zijn die een onderzoek vereisen. Neem contact op met de klantenservice van de Adobe als de opname of indexering nog steeds mislukt.

### Updates en oplossingen AEM versie {#aem-version-updates-and-ingestions}

[Versie-updates AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html) worden automatisch toegepast op omgevingen om deze up-to-date te houden met de meest recente AEM as a Cloud Service versie. Als de update wordt geactiveerd wanneer een opname wordt uitgevoerd, kunnen er onvoorspelbare resultaten optreden, waaronder de beschadiging van de omgeving.

Als de &quot;Updates van de Versie van de AEM&quot;op het bestemmingsprogramma wordt ingezien, probeert het innameproces om zijn rij onbruikbaar te maken alvorens het begint. Wanneer de opname volledig is, wordt de status van de versieupdater teruggegeven aan hoe het was alvorens ingestions begonnen.

>[!NOTE]
>
> Er is niet langer een behoefte om een steunkaartje te registreren om &quot;AEM de Updates van de Versie&quot;gehandicapt te krijgen.

Als &quot;AEM de Updates van de Versie&quot;actief is (namelijk de updates lopen of een rij worden gevormd om) in werking te stellen, zal de ingang niet beginnen en het gebruikersinterface presenteert het volgende bericht. Zodra de updates volledig zijn, kan de opname worden begonnen. U kunt Cloud Manager gebruiken om de huidige status van de pijpleidingen van het programma te bekijken.

>[!NOTE]
>
> De &quot;AEM Updates van de Versie&quot;wordt in werking gesteld in de pijpleiding van het milieu en wacht tot de pijpleiding duidelijk is. Als updates langer in de wachtrij worden geplaatst dan u had verwacht, moet u ervoor zorgen dat de pijpleiding niet per ongeluk is vergrendeld in een aangepaste workflow.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### Bijkomende congestiefout als gevolg van Uniqueness Constraint {#top-up-ingestion-failure-due-to-uniqueness-constraint-violation}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_uuid"
>title="Ongelijkheidsbeperking schending"
>abstract="Een gemeenschappelijke oorzaak van een niet-sluitingsmislukking is een conflict in knoop ids. Er kan slechts een van de conflicterende knooppunten bestaan."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html#top-up-ingestion-process" text="Bovenste inname"

Een gemeenschappelijke oorzaak van een [Bovenste inname](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) error is een conflict in knoop ids. Als u deze fout wilt identificeren, downloadt u het innamelogboekbestand met de interface van Cloud Acceleration Manager en zoekt u een item als de volgende:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] met waarde a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Elk knooppunt in AEM moet een unieke uuid hebben. Deze fout geeft aan dat een knooppunt dat wordt ingesloten, dezelfde uuid heeft als een knooppunt dat zich in een ander pad op de doelinstantie bevindt. Deze situatie kan om twee redenen gebeuren:

* Een knooppunt wordt verplaatst naar de bron tussen een extractie en een volgende [Extractie bovenaan](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
   * _ONTHOUDEN_: Voor Top-Up-extracties bestaat het knooppunt nog steeds in de migratieset, zelfs als het niet meer bestaat op de bron.
* Een knoop op de bestemming wordt bewogen tussen een ingestie en een verdere top-up ingestie.

Dit conflict moet handmatig worden opgelost. Iemand die bekend is met de inhoud, moet beslissen welke van de twee knooppunten moet worden verwijderd, rekening houdend met andere inhoud die ernaar verwijst. De oplossing kan vereisen dat de top-up extractie opnieuw wordt gedaan zonder de beledigende knoop.

### Opsommingsfout vanwege niet-verwijderen knooppunt waarnaar wordt verwezen {#top-up-ingestion-failure-due-to-unable-to-delete-referenced-node}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_referenced_node"
>title="Kan knooppunt waarnaar wordt verwezen niet verwijderen"
>abstract="Een gemeenschappelijke oorzaak van een niet-veeggebaren ingangsmislukking is een versieconflict voor een bepaalde knoop op de bestemmingsinstantie. De versies van het knooppunt moeten worden hersteld."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html#top-up-ingestion-process" text="Bovenste inname"

Een andere veelvoorkomende oorzaak van een [Bovenste inname](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) de mislukking is een versieconflict voor een bepaalde knoop op de bestemmingsinstantie. Als u deze fout wilt identificeren, downloadt u het innamelogboekbestand met de interface van Cloud Acceleration Manager en zoekt u een item als de volgende:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: Unable to delete referenced node: 8a2289f4-b904-4bd0-8410-15e41e 976a8

Dit kan gebeuren als een knooppunt op de bestemming wordt gewijzigd tussen een opname en een volgende opname **Niet-sluitereffect** Inname zodanig dat er een nieuwe versie is gemaakt. Als de migratieset is geëxtraheerd met &#39;include-versies&#39; ingeschakeld, kan er een conflict optreden omdat de bestemming nu een recentere versie heeft waarnaar wordt verwezen door versiegeschiedenis en andere inhoud. Het opnameproces kan het beledigende versieknooppunt niet verwijderen omdat ernaar wordt verwezen.

De oplossing kan vereisen dat de top-up extractie opnieuw wordt gedaan zonder de beledigende knoop. Of u maakt een kleine migratieset van het aanstootgevende knooppunt, maar met &quot;include-versies&quot; uitgeschakeld.

De beste praktijken wijzen erop dat als **Niet-sluitereffect** opname moet worden uitgevoerd met behulp van een migratieset die versies bevat. Het is van cruciaal belang dat de inhoud op de bestemming zo weinig mogelijk wordt gewijzigd, totdat de migratie is voltooid. Anders kunnen deze conflicten optreden.

### Ingestiefout vanwege waarden voor eigenschappen van grote knooppunten {#ingestion-failure-due-to-large-node-property-values}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_bson"
>title="Eigenschap voor grote knooppunten"
>abstract="Een veelvoorkomende oorzaak van een mislukte opname is dat de maximale grootte van eigenschapswaarden voor knooppunten wordt overschreden. Volg de documentatie, met inbegrip van de documentatie met betrekking tot het BPA-verslag, om deze situatie te verhelpen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html" text="Migratievereisten"

Eigenschapwaarden voor knooppunten die zijn opgeslagen in MongoDB, mogen niet groter zijn dan 16 MB. Als een nodewaarde de gesteunde grootte overschrijdt, ontbreekt het opnemen en het logboek zal een bevatten `BSONObjectTooLarge` fout en geef op welk knooppunt het maximum heeft overschreden. Dit is een MongoDB-beperking.

Zie de `Node property value in MongoDB` notitie in [Voorwaarden voor het gereedschap Inhoud overbrengen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md) voor meer informatie en een koppeling naar een gereedschap voor eikenhout waarmee u alle grote knooppunten kunt vinden. Als alle knooppunten met grote afmetingen zijn verholpen, voert u de extractie en inname opnieuw uit.

Als u deze beperking wilt voorkomen, voert u het [Analysator van best practices](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) over de bron AEM instantie en de bevindingen die zij presenteert, met name de [&quot;Niet-ondersteunde Repository Structure&quot; (URS)](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/urs) patroon.

### Ingestie gestopt {#ingestion-rescinded}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_rescinded"
>title="Ingestie gestopt"
>abstract="De extractie waarop de inname wachtte, is niet succesvol afgerond. De opname is geannuleerd omdat deze niet kon worden uitgevoerd."

Een opname die met een lopende extractie werd gecreeerd aangezien zijn bronmigratie wordt geplaatst wacht geduldig tot die extractie slaagt, en op dat punt begint normaal. Als de extractie mislukt of wordt gestopt, beginnen de opname en de indexeertaak niet, maar worden deze geannuleerd. In dit geval controleert u de extractie om te bepalen waarom dit is mislukt, verhelpt u het probleem en begint u opnieuw te extraheren. Als de vaste extractie eenmaal is uitgevoerd, kan een nieuwe opname worden gepland.

### Verwijderd element niet aanwezig na herhaalde opname

Over het algemeen wordt het niet aanbevolen om de gegevens van de cloudomgeving tussen innames te wijzigen.

Wanneer een element wordt verwijderd uit de bestemming Cloud Service met behulp van de interface voor middelenaanraking, worden de knooppuntgegevens verwijderd, maar wordt het elementblok met de afbeelding niet onmiddellijk verwijderd. Het is duidelijk voor schrapping zodat het niet meer in UI verschijnt; nochtans, blijft het in de datastore tot de huisvuilinzameling voorkomt en de blob wordt verwijderd.

In het scenario waarin een eerder gemigreerd element wordt verwijderd en de volgende opname wordt uitgevoerd voordat de opschoonfunctie het element heeft verwijderd, wordt het verwijderde element niet hersteld wanneer dezelfde migratieset wordt gebruikt. Wanneer de opname de wolkenomgeving voor het middel controleert, zijn er geen knoopgegevens; daarom zal de opname de knoopgegevens aan het wolkenmilieu kopiëren. Als het echter de blob store controleert, ziet het dat de blob aanwezig is en wordt het kopiëren van de blob overgeslagen. Daarom zijn de metagegevens aanwezig na invoer wanneer u het element vanuit de aanraakinterface bekijkt, maar de afbeelding niet. Houd er rekening mee dat migratiesets en inname van inhoud niet zijn ontworpen om deze kwestie af te handelen. Ze zijn bedoeld om nieuwe inhoud toe te voegen aan de cloud-omgeving en eerder gemigreerde inhoud niet te herstellen.

## Volgende functies {#whats-next}

Wanneer de opname is gelukt, wordt AEM indexering automatisch gestart. Zie [Indexeren na migreren van inhoud](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) voor meer informatie .

Als u Inhoud invoegen hebt voltooid in de Cloud Service, kunt u logboeken van elke stap (extractie en opname) weergeven en op fouten zoeken. Zie [Logboeken voor een migratieset weergeven](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md) voor meer informatie.
