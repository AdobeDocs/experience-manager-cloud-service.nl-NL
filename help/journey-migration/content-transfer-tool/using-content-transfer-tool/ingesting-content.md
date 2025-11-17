---
title: Inhoud in Cloud Service invoegen
description: Leer hoe u de Cloud Acceleration Manager gebruikt om inhoud van uw migratieset in te voeren in een Cloud Service-doelexemplaar.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
feature: Migration
role: Admin
source-git-commit: 7c0703d746601742a28c3c98f35e69de70f25e05
workflow-type: tm+mt
source-wordcount: '3647'
ht-degree: 1%

---

# Inhoud in Cloud Service invoegen {#ingesting-content}

## Ingestieproces in de Cloud Acceleration Manager {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inktatie van inhoud"
>abstract="Ingestie verwijst naar het opnemen van inhoud van de migratie die is ingesteld op de Cloud Service-doelinstantie. De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content#top-up-extraction-process" text="Extractie naar boven"

Volg de onderstaande stappen om uw migratieset in te voeren met de Cloud Acceleration Manager:

1. Ga naar Cloud Acceleration Manager. Klik op de projectkaart en klik op de kaart voor inhoudsoverdracht. Navigeer aan **IngestieBanen** en klik **Nieuwe Ingestie**

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Controleer de innamecontrolelijst en zorg ervoor dat alle stappen zijn voltooid. Deze stappen zijn nodig om een succesvolle inname te waarborgen. Ga aan de **Volgende** stap slechts te werk als checklist wordt voltooid.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geef de vereiste informatie op om een opname te maken.

   * **Reeks van de Migratie:** selecteer de migratiereeks die de gehaalde gegevens als Source bevat.
      * De Reeksen van de migratie zullen verlopen na een lange periode van inactiviteit, zodat wordt verwacht dat de inname vrij snel na de extractie plaatsvindt. Het overzicht [ Vastgestelde Verval van de Migratie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor details.

   >[!TIP]
   > Als de extractie wordt uitgevoerd, wordt dit in het dialoogvenster aangegeven. Nadat de extractie is voltooid, wordt de inname automatisch gestart. Als de extractie mislukt of wordt gestopt, wordt de innametaak geannuleerd.

   * **Doel:** selecteer het bestemmingsmilieu. In deze omgeving wordt de inhoud van de migratieset opgenomen.
      * De oplossingen steunen geen bestemmingen van het type Snelle Milieu van de Ontwikkeling (RDE) of Voorproef, en zij verschijnen niet als mogelijke bestemmingskeus, zelfs als de gebruiker toegang tot het heeft.
      * Terwijl een migratiereeks in veelvoudige bestemmingen gelijktijdig kan worden opgenomen, kan een bestemming het doel van slechts één lopende of wachtende opname tegelijkertijd zijn.

   * **Rij:** selecteer de rij. (Auteur/Publicatie).
      * Als de bron `Author` was, wordt aangeraden de bron in de `Author` -laag op het doel in te voeren. Als de bron `Publish` was, moet het doel ook `Publish` zijn.

   >[!NOTE]
   > Als de doellaag `Author` is, wordt de auteurinstantie gesloten tijdens de lengte van de opname en niet beschikbaar voor gebruikers (bijvoorbeeld, auteurs of iedereen die onderhoud uitvoert). De reden is om het systeem te beschermen en om eventuele veranderingen te voorkomen die verloren zouden kunnen gaan of een innameconflict zouden veroorzaken. Zorg ervoor dat uw team zich hiervan bewust is. Houd er ook rekening mee dat de omgeving tijdens de opname door de auteur wordt genegeerd.

   >[!NOTE]
   > Als de doellaag `Publish` is, blijft de publicatie-instantie actief tijdens de opname.  Nochtans, als het samenstellingsproces terwijl opneming loopt, zal een conflict tussen de twee processen waarschijnlijk gebeuren.  Om deze reden onbruikbaar maakt het inslikken proces 1) het compaction getimede manuscript zodat zal de samenperking niet tijdens de inname beginnen, en 2) controleert of momenteel de compensatie loopt, en als het is, wacht tot het alvorens de inname gaat te voltooien.  Als het publiceren neemt langer dan verwacht, controleer de innamelogboeken voor verwante logboekverklaringen.

   * **Sluitereffect:** kies de `Wipe` waarde
      * De **Sluitereffect** optie plaatst het uitgangspunt van de bestemming van de opname. Als **Sluitereffect** wordt toegelaten, wordt de bestemming met inbegrip van al zijn inhoud teruggesteld aan de versie van AEM die in Cloud Manager wordt gespecificeerd. Als deze optie niet is ingeschakeld, behoudt de bestemming de huidige inhoud als beginpunt.
      * Deze optie beïnvloedt **NIET** hoe de opname van inhoud zal worden uitgevoerd. De congestie gebruikt altijd een strategie van de inhoudsvervanging en _niet_ een strategie van de inhoudssamenvoeging zodat, in zowel **Wipe** als **niet-Wipe** gevallen, zal het opnemen van een migratiereeks inhoud in de zelfde weg op de bestemming beschrijven. Als de migratieset bijvoorbeeld `/content/page1` bevat en het doel al `/content/page1/product1` bevat, verwijdert de opname het gehele `page1` -pad en de bijbehorende subpagina&#39;s, inclusief `product1` , en vervangt u deze door de inhoud in de migratieset. Dit betekent zorgvuldige planning moet worden gedaan wanneer het uitvoeren van a **niet-Wipe** opname aan een bestemming die om het even welke inhoud bevat die zou moeten worden gehandhaafd.
      * Niet-vette ingesties zijn specifiek ontworpen voor de meest voorkomende inname. Deze indelingen hebben een incrementele hoeveelheid nieuwe inhoud die is gewijzigd sinds de laatste inname in een bestaande migratieset. Het uitvoeren van niet-wegwerpinjecties buiten dit gebruiksgeval kan leiden tot zeer lange inname.

   >[!IMPORTANT]
   > Als het plaatsen **Sluitereffect** voor de opname wordt toegelaten, stelt het de volledige bestaande bewaarplaats met inbegrip van de gebruikerstoestemmingen op de instantie van doelCloud Service terug. Dit het terugstellen is waar ook voor een admin gebruiker die aan de **wordt toegevoegd beheerders** groep en die gebruiker moet aan de beheerdersgroep opnieuw worden toegevoegd om een opname te beginnen.

   * **pre-Exemplaar:** kies de `Pre-copy` waarde
      * U kunt de optionele pre-copy stap uitvoeren om de inname aanzienlijk te versnellen. Zie [ Ingesting met AzCopy ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) voor meer details.
      * Als inesten met voorkopie wordt gebruikt (voor S3 of Azure Data Store), wordt aangeraden `Author` inname eerst alleen uit te voeren. Hierdoor wordt de opname van `Publish` sneller wanneer deze later wordt uitgevoerd.

   >[!IMPORTANT]
   > U kunt een opname aan het bestemmingsmilieu in werking stellen slechts als u tot de lokale **beheerders van AEM** groep op de de auteursdienst van bestemmingsCloud Service behoort. Als u geen ingestie kunt beginnen, zie [ Onbekwaam om Ingestie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) voor meer details te beginnen.

1. Nadat de keuze voor inname is gemaakt, kan een schatting van de duur van de inname worden weergegeven. Dit is een inspanningsschatting gebaseerd op historische gegevens van vergelijkbare ingestie.

   * Deze schatting wordt niet berekend of getoond voor **niet-veeggebaren** ingestions, aangezien CAM niet weet hoeveel inhoud op het doelsysteem in dit geval is.
   * Deze schatting wordt alleen berekend en weergegeven als de waarden voor &#39;grootte controleren&#39; van de extractie zijn verzameld en beschikbaar zijn.
   * Deze waarde is een schatting en mag, hoewel intelligent berekend, niet als exact worden beschouwd. De werkelijke duur kan door verschillende factoren worden gewijzigd.
   * Terwijl ingestie loopt, zal deze waarde ook beschikbaar in de duurdialoog zijn, die door de &quot;**wordt betreden de duur van de Mening**&quot;actie van de opname.

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_estimate"
>title="Schatting van de opzettingsduur"
>abstract="Een geschatte duur van een bepaalde inname kan worden weergegeven om een algemene indruk te geven van de duur ervan. De nauwkeurigheid ervan is beperkt."

![afbeelding](/help/journey-migration/content-transfer-tool/assets/estimate.png)

1. Klik **Samenvatting**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. U kunt de opname van de de lijstmening van Banen van de Opname dan controleren en het de actiemenu van de opname gebruiken om de duur en het logboek te bekijken aangezien de opname vordert.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klik **(i)** knoop in de rij voor meer informatie over de innametaak. U kunt de duur van elke stap van de Opname zien wanneer het loopt of door **te klikken...**, en dan **de duur van de Mening** te klikken. Uit de informatie over de extractie blijkt ook dat men zich realiseert wat er wordt ingeslikt.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## Top Up-inname {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Top Up-inname"
>abstract="Gebruik de functie top-up om inhoud te verplaatsen die is gewijzigd sinds de vorige activiteit van de inhoudsoverdracht. Controleer de logboeken op fouten of waarschuwingen na voltooiing van de inname. Eventuele fouten moeten onmiddellijk worden opgelost door de gemelde problemen te verhelpen of door contact op te nemen met de klantenservice van Adobe."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs" text="Logbestanden weergeven"

Het hulpmiddel van de Overdracht van de Inhoud heeft een eigenschap die de extractie van differentiële inhoud door a *bovenop-up* van de migratiereeks uit te voeren toestaat. Hierdoor kan de migratieset worden gewijzigd, zodat alleen de inhoud wordt opgenomen die sinds de vorige extractie is gewijzigd, zonder dat alle inhoud opnieuw moet worden geëxtraheerd.

>[!NOTE]
>Na de eerste overdracht van inhoud wordt aanbevolen regelmatig differentiële toevoegingen toe te passen om de periode waarin de inhoud wordt vastgezet voor de uiteindelijke differentiële overdracht van inhoud te verkorten voordat u live gaat op Cloud Service. Als u de pre-exemplaarstap voor de eerste opname hebt gebruikt, kunt u pre-exemplaar voor verdere bovenop-up ingestions overslaan (als de top-up migratie vastgestelde grootte minder dan 200 GB is). De reden is dat het tijd kan toevoegen aan het hele proces.

Om differentiële inhoud in te voeren nadat sommige ingestions volledig zijn, moet u a [ Hoogste Extractie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) in werking stellen, en dan de inlaatmethode met **gebruiken Wipe** gehandicapte optie ****. Ben zeker om de **Sluiterende** verklaring hierboven te lezen om het verliezen van inhoud reeds op de bestemming te vermijden.

Begin door een Baan van de Opname te creëren en ervoor te zorgen dat **Sluitereffect** tijdens het opnemen wordt onbruikbaar gemaakt, zoals hieronder getoond:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Problemen oplossen {#troubleshooting}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_troubleshooting"
>title="Problemen met inslikken van inhoud oplossen"
>abstract="Verwijs naar de innamelogboeken en de documentatie om oplossingen aan gemeenschappelijke redenen te vinden waarom een inname kan ontbreken en de manier vinden om het probleem te bevestigen. Als de injectie eenmaal is vastgezet, kan deze weer worden uitgevoerd."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers" text="Inhoudsoverdrachten valideren"

### CAM Kan migratietoken niet ophalen {#cam-unable-to-retrieve-the-migration-token}

De automatische terugwinning van het migratietoken kan om verschillende redenen, met inbegrip van u [ vestiging een IP lijst van gewenste personen via Cloud Manager ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) op het milieu van doelCloud Service ontbreken. In dergelijke scenario&#39;s, ziet u de volgende dialoogdoos wanneer u probeert om een opname te beginnen:

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

U kunt het migratietoken handmatig ophalen door op de koppeling Token ophalen in het dialoogvenster te klikken. Er wordt een ander tabblad geopend waarin het token wordt weergegeven. U kunt het teken dan kopiëren en het in het **symbolische input van de Migratie** gebied kleven. Nu moet je de inname kunnen starten.

>[!NOTE]
>
>Het teken is beschikbaar aan gebruikers die tot de lokale **de beheerders van AEM** groep op de de auteursdienst van bestemmingsCloud Service behoren.

### Kan inname niet starten {#unable-to-start-ingestion}

U kunt een opname aan het bestemmingsmilieu in werking stellen slechts als u tot de lokale **beheerders van AEM** groep op de de auteursdienst van bestemmingsCloud Service behoort. Als u niet tot de groep van de Beheerders van AEM behoort, ziet u een fout zoals hieronder getoond wanneer u probeert om een opname te beginnen. U kunt of uw beheerder vragen om u aan de lokale **beheerders van AEM toe te voegen** of om het teken zelf te vragen, dat u in het **symbolische input van de Migratie** gebied kunt dan kleven.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Kan de migratieservice niet bereiken {#unable-to-reach-migration-service}

Nadat een opname wordt gevraagd, kan een bericht als het volgende aan de gebruiker worden voorgesteld: &quot;De migratiedienst op het bestemmingsmilieu is onbereikbaar. Als dit het geval is, probeert u het later opnieuw of neemt u contact op met de ondersteuning van Adobe.&quot;

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Dit bericht geeft aan dat de Cloud Acceleration Manager de migratieservice van de doelomgeving niet kon bereiken om de opname te starten. Dit kan om verschillende redenen gebeuren.

>[!NOTE]
> 
> Het veld &quot;Migratietoken&quot; wordt weergegeven omdat het ophalen van dat token in sommige gevallen niet is toegestaan. Door het handmatig aanbrengen van de injectie toe te staan, kan de gebruiker de opname snel starten, zonder extra hulp. Als het token is opgegeven en het bericht nog steeds wordt weergegeven, was het ophalen van het token niet het probleem.

* AEM as a Cloud Service handhaaft de milieustaat, en moet af en toe de migratiedienst opnieuw beginnen om diverse normale redenen. Als die dienst opnieuw begint, kan het niet worden bereikt, maar is uiteindelijk beschikbaar.
* Het is mogelijk dat een ander proces op de instantie wordt uitgevoerd. Bijvoorbeeld, als [ de Updates van de Versie van AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) een update toepast, kan het systeem bezig zijn en de migratiedienst regelmatig niet beschikbaar. Zodra dat proces is voltooid, kan opnieuw worden geprobeerd om met de inname te beginnen.
* Als een [ IP Lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) door Cloud Manager is toegepast, verhindert het Cloud Acceleration Manager de migratiedienst te bereiken. Een IP adres kan niet voor ingesties worden toegevoegd omdat zijn adres dynamisch is. Momenteel, is de enige oplossing de IP lijst van gewenste personen tijdens de opname en het indexeren proces onbruikbaar te maken door 0.0.0.0/0 aan de lijst van gewenste personen tijdelijk toe te voegen terwijl de opname en het indexeren proces lopen.
* Er kunnen andere redenen zijn die een onderzoek vereisen. Neem contact op met de klantenservice van Adobe als het invoeren of indexeren nog steeds mislukt.

### Updates en oplossingen voor AEM-versies {#aem-version-updates-and-ingestions}

{de Updates van de Versie van 0} AEM [ worden automatisch toegepast op milieu&#39;s om hen met de meest recente versie van AEM as a Cloud Service bijgewerkt te houden. ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates) Als de update wordt geactiveerd wanneer een opname wordt uitgevoerd, kunnen er onvoorspelbare resultaten optreden, waaronder de beschadiging van de omgeving.

Als de &quot;Updates van de Versie van AEM&quot;op het bestemmingsprogramma wordt ingezien, probeert het innameproces om zijn rij onbruikbaar te maken alvorens het begint. Wanneer de opname volledig is, wordt de status van de versieupdater teruggegeven aan hoe het was alvorens ingestions begonnen.

>[!NOTE]
>
> U hoeft niet langer een ondersteuningsticket te registreren om &quot;AEM Version Updates&quot; uit te schakelen.

Als de &quot;Updates van de Versie van AEM&quot;actief is (d.w.z. de updates lopen of een rij worden gevormd om) in werking te stellen, zal de ingang niet beginnen en het gebruikersinterface presenteert het volgende bericht. Zodra de updates volledig zijn, kan de opname worden begonnen. Cloud Manager kan worden gebruikt om de huidige toestand van de pijpleidingen van het programma te zien.

>[!NOTE]
>
> De &quot;Updates van de Versie van AEM&quot;wordt in werking gesteld in de pijpleiding van het milieu en wacht tot de pijpleiding duidelijk is. Als updates langer in de wachtrij worden geplaatst dan u had verwacht, moet u ervoor zorgen dat de pijpleiding niet per ongeluk is vergrendeld in een aangepaste workflow.

![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### Ingestiefout als gevolg van Cloud Environment niet gereed {#ingestion-failure-due-to-cloud-environment-not-in-ready-state}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_cloud_environment_not_in_ready_state"
>title="Cloud-omgeving niet gereed"
>abstract="In zeldzame gevallen kan de doelcloud onverwachte problemen veroorzaken, waardoor de opname mislukt."

In zeldzame gevallen kan de Cloud Service-doelomgeving van de opname onverwachte problemen ondervinden. Als gevolg hiervan zal de inname mislukken omdat de omgeving niet in de verwachte gebruiksklare toestand verkeert. Controleer het innamelogboek om meer details van de aangetroffen foutenstaat te openbaren.

Zorg ervoor dat de auteursomgeving beschikbaar is en wacht een paar minuten voordat u de inname opnieuw bevestigt. Neem contact op met de klantenondersteuning als het probleem zich blijft voordoen.

### Bijkomende congestiefout als gevolg van Uniqueness Constraint {#top-up-ingestion-failure-due-to-uniqueness-constraint-violation}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_uuid"
>title="Ongelijkheidsbeperking schending"
>abstract="Een gemeenschappelijke oorzaak van een niet-sluitingsmislukking is een conflict in knoop ids. Er kan slechts een van de conflicterende knooppunten bestaan."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Bovenste inname"

Een gemeenschappelijke oorzaak van de mislukking van de Opname van de a [ ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) is een conflict in knoopids. Als u deze fout wilt identificeren, downloadt u het innamelogboek met de gebruikersinterface van Cloud Acceleration Manager en zoekt u een item als de volgende:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint overtreden bezit [ jcr :uuid] die waarde a1a1a1a1-b2b2-c3-d4d4-e5e5e5e5e5: /some/path/jcr :content, /some/other/path/jcr :content

Elk knooppunt in AEM moet een unieke uuid hebben. Deze fout geeft aan dat een knooppunt dat wordt ingesloten, dezelfde uuid heeft als een knooppunt dat zich in een ander pad op de doelinstantie bevindt. Deze situatie kan om twee redenen gebeuren:

* Een knoop wordt bewogen op de bron tussen een extractie en een verdere [ Top-Up Extractie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
   * _VERGEET_: Voor Top-Up extracties, zal de knoop nog in de migratiereeks bestaan, zelfs als het niet meer op de bron bestaat.
* Een knoop op de bestemming wordt bewogen tussen een ingestie en een verdere top-up ingestie.

Dit conflict moet handmatig worden opgelost. Iemand die bekend is met de inhoud, moet beslissen welke van de twee knooppunten moet worden verwijderd, rekening houdend met andere inhoud die ernaar verwijst. De oplossing kan vereisen dat de top-up extractie opnieuw wordt gedaan zonder de beledigende knoop.

### Opsommingsfout vanwege niet-verwijderen knooppunt waarnaar wordt verwezen {#top-up-ingestion-failure-due-to-unable-to-delete-referenced-node}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_referenced_node"
>title="Kan knooppunt waarnaar wordt verwezen niet verwijderen"
>abstract="Een gemeenschappelijke oorzaak van een niet-veeggebaren ingangsmislukking is een versieconflict voor een bepaalde knoop op de bestemmingsinstantie. De versies van het knooppunt moeten worden hersteld."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content#top-up-ingestion-process" text="Bovenste inname"

Een andere gemeenschappelijke oorzaak van de mislukking van de Opname van de a [ ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) is een versieconflict voor een bepaalde knoop op de bestemmingsinstantie. Als u deze fout wilt identificeren, downloadt u het innamelogboek met de gebruikersinterface van Cloud Acceleration Manager en zoekt u een item als de volgende:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: Unable to delete referenced node: 8a2289f4-b904-4bd0-8410-15e41e 976a8

Dit kan gebeuren als een knoop op de bestemming tussen een opname en een verdere **niet-Wipe** opname zodanig wordt gewijzigd dat een nieuwe versie is gecreeerd. Als de migratieset is geëxtraheerd met &#39;include-versies&#39; ingeschakeld, kan er een conflict optreden omdat de bestemming nu een recentere versie heeft waarnaar wordt verwezen door versiegeschiedenis en andere inhoud. Het opnameproces kan het beledigende versieknooppunt niet verwijderen omdat ernaar wordt verwezen.

De oplossing kan vereisen dat de top-up extractie opnieuw wordt gedaan zonder de beledigende knoop. Of u maakt een kleine migratieset van het aanstootgevende knooppunt, maar met &quot;include-versies&quot; uitgeschakeld.

De beste praktijken wijzen erop dat als a **niet-Wipe** ingestie moet worden in werking gesteld gebruikend een migratiereeks die versies omvat, het cruciaal is dat de inhoud op de bestemming zo weinig mogelijk wordt gewijzigd, tot de migratiereis volledig is. Anders kunnen deze conflicten optreden.

### Ingestiefout vanwege waarden voor eigenschappen van grote knooppunten {#ingestion-failure-due-to-large-node-property-values}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_bson"
>title="Eigenschap voor grote knooppunten"
>abstract="Een veelvoorkomende oorzaak van een mislukte opname is dat de maximale grootte van eigenschapswaarden voor knooppunten wordt overschreden. Volg de documentatie, met inbegrip van de documentatie met betrekking tot het BPA-verslag, om deze situatie te verhelpen."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool" text="Migratievereisten"

Eigenschapwaarden voor knooppunten die zijn opgeslagen in MongoDB, mogen niet groter zijn dan 16 MB. Als een nodewaarde de gesteunde grootte overschrijdt, ontbreekt het opnemen en het logboek zal of bevatten:

* een `BSONObjectTooLarge` -fout en geef op welk knooppunt het maximum heeft overschreden, of
* a `BsonMaximumSizeExceededException` fout, die aangeeft dat er een knooppunt is dat waarschijnlijk Unicode-tekens bevat die de maximumgrootte overschrijden **

Dit is een MongoDB-beperking.

Zie de `Node property value in MongoDB` nota in [ Eerste vereisten voor het Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md) voor meer informatie en een verbinding aan een hulpmiddel van Oak dat alle grote knopen kon helpen vinden. Als alle knooppunten met grote afmetingen zijn verholpen, voert u de extractie en inname opnieuw uit.

Om deze beperking mogelijk te vermijden, stel de [ Analysator van Beste praktijken ](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) op de bronAEM instantie in werking en herzie de bevindingen het, met name [ &quot;Niet gestaafde Structuur van de Bewaarplaats&quot; (URS) ](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/urs) patroon voorstelt.

>[!NOTE]
>
>[ versie 2.1.50+ van de Analysator van Beste praktijken van 0} zal over grote knopen rapporteren die unicode karakters bevatten die de maximumgrootte overschrijden. ](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) Zorg ervoor dat u de nieuwste versie uitvoert. In BPA-versies vóór 2.1.50 worden deze grote knooppunten niet geïdentificeerd en gerapporteerd. Deze knooppunten moeten afzonderlijk worden gedetecteerd met behulp van de hiervoor genoemde Oak-voorwaarde.

### Ingestiefout als gevolg van onverwachte intermitterende fouten {#ingestion-failure-due-to-unexpected-intermittent-errors}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_intermittent_errors"
>title="Onverwachte intermitterende fouten"
>abstract="Soms kunnen zich onverwachte afwisselende downstreamservicefouten voordoen en helaas is het enige middel om de inname eenvoudig opnieuw te proberen."

Soms zouden onverwachte intermitterende problemen zich lenen voor mislukte inname, waarbij het helaas de enige mogelijkheid is om de inname opnieuw te proberen. Onderzoek het innamelogboek om de oorzaak van de mislukking te ontdekken en te zien of richt het zich op om het even welke hieronder vermelde fouten, waar een herpoging zou moeten worden geprobeerd.

#### MongoDB-problemen {#mongo-db-issues}

* `Atlas prescale timeout error` - In de introductiefase wordt geprobeerd de doelcloud-database vooraf in te stellen op een geschikte grootte die is afgestemd op de grootte van de inhoud van de migratieset die wordt opgenomen. Deze bewerking wordt soms niet binnen de verwachte tijd voltooid.
* `Exhausted mongo restore retries` - Pogingen om een lokale stortplaats van de opgenomen migratie vastgestelde vastgestelde inhoud aan het wolkengegevensbestand te herstellen zijn uitgeput. Dit wijst op een algemene gezondheid/netwerkkwestie met MongoDB, die zich vaak na een paar minuten geneest.
* `Mongo network error` - Soms kan het tot stand brengen van een verbinding met MongoDB mislukken, waardoor het innameproces vroeg wordt afgesloten en wordt gerapporteerd dat dit is mislukt. Er moet worden geprobeerd de inname eenvoudig opnieuw uit te voeren.
* `Mongo server selection error` - Dit is een zeldzame time-outfout aan de clientzijde van het mongo die om een aantal onderliggende redenen kan optreden. Als u het later opnieuw probeert, wordt het probleem waarschijnlijk verholpen.
* `Mongo took too long to start` - In zeer zeldzame gevallen kan het lokale MongoDB-bestand dat wordt gebruikt in de innameworkflow, niet worden gestart. Als u het later opnieuw probeert, wordt het probleem waarschijnlijk verholpen.

#### AZCopy issues {#azcopy-issues}

* `AZCopy critical failure` - In zeldzame gevallen kan het gereedschap AZCopy dat wordt gebruikt om de stap voor het kopiëren van de opname uit te voeren, onverwacht mislukken. In dit geval moet worden geprobeerd de inname opnieuw te proberen.

### Ingestie gestopt {#ingestion-rescinded}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_rescinded"
>title="Ingestie gestopt"
>abstract="De extractie waarop de inname wachtte, is niet succesvol afgerond. De opname is geannuleerd omdat deze niet kon worden uitgevoerd."

Een opname die met een lopende extractie werd gecreeerd aangezien zijn bronmigratie wordt geplaatst wacht geduldig tot die extractie slaagt, en op dat punt begint normaal. Als de extractie mislukt of wordt gestopt, beginnen de opname en de indexeertaak niet, maar worden deze geannuleerd. In dit geval controleert u de extractie om te bepalen waarom dit is mislukt, verhelpt u het probleem en begint u opnieuw te extraheren. Als de vaste extractie eenmaal is uitgevoerd, kan een nieuwe opname worden gepland.

### Wachten op inname mislukt {#waiting-ingestion-not-started}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_waiting_ingestion_not_started"
>title="Wachten op inname niet gestart"
>abstract="De opname kon niet worden gestart nadat een extractie was voltooid."

Een opname die met een lopende extractie werd gecreeerd aangezien zijn bronmigratie plaatste wacht tot die extractie slaagt, en op dat punt probeert de opname normaal te beginnen. Als de inname niet kan worden gestart, wordt deze gemarkeerd als mislukt. Mogelijke redenen om niet te beginnen zijn: een IP Lijst van gewenste personen wordt gevormd op het milieu van de doelauteur; het doelmilieu is niet beschikbaar voor één of andere andere andere reden.  Controleer in dit geval waarom de inname niet is begonnen, verhelpt het probleem en start de inname opnieuw (het is niet nodig de extractie opnieuw uit te voeren).

### Verwijderd element niet aanwezig na herhaalde opname

Over het algemeen wordt het niet aanbevolen om de gegevens van de cloudomgeving tussen innames te wijzigen.

Wanneer een element wordt verwijderd uit de Cloud Service-bestemming met de Assets Touch-gebruikersinterface, worden de knooppuntgegevens verwijderd, maar wordt het assetblob met de afbeelding niet onmiddellijk verwijderd. Het is duidelijk voor schrapping zodat het niet meer in UI verschijnt; nochtans, blijft het in de datastore tot de huisvuilinzameling voorkomt en de blob wordt verwijderd.

In het scenario waarin een eerder gemigreerd element wordt verwijderd en de volgende opname wordt uitgevoerd voordat de opschoonfunctie het element heeft verwijderd, wordt het verwijderde element niet hersteld wanneer dezelfde migratieset wordt gebruikt. Wanneer de opname de wolkenomgeving voor het middel controleert, zijn er geen knoopgegevens; daarom zal de opname de knoopgegevens aan het wolkenmilieu kopiëren. Als het echter de blob store controleert, ziet het dat de blob aanwezig is en wordt het kopiëren van de blob overgeslagen. Daarom zijn de metagegevens aanwezig na invoer wanneer u het element vanuit de aanraakinterface bekijkt, maar de afbeelding niet. Houd er rekening mee dat migratiesets en inname van inhoud niet zijn ontworpen om deze kwestie af te handelen. Ze zijn bedoeld om nieuwe inhoud toe te voegen aan de cloud-omgeving en eerder gemigreerde inhoud niet te herstellen.

## Volgende functies {#whats-next}

Wanneer de opname is gelukt, wordt automatisch begonnen met de indexering van AEM. Zie [ Indexerend na het Migreren van Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md) voor meer informatie.

Nadat u de Ingesting Content in Cloud Service hebt voltooid, kunt u logboeken van elke stap (extractie en opname) weergeven en op fouten zoeken. Zie [ het Bekijken Logboeken voor een Reeks van de Migratie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md) om meer te leren.
