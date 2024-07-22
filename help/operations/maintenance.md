---
title: Onderhoudstaken in AEM as a Cloud Service
description: Meer informatie over onderhoudstaken in AEM as a Cloud Service en hoe u deze kunt configureren.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
feature: Operations
role: Admin
source-git-commit: b8bed4acf895f1cf04ea92ae27b87c7bfb38863d
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 0%

---

# Onderhoudstaken in AEM as a Cloud Service {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Onderhoudstaken"
>abstract="Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM as a Cloud Service is de noodzaak voor klanten om de operationele eigenschappen van onderhoudstaken te configureren minimaal. De klanten kunnen hun middelen op toepassing-vlakke zorgen concentreren, verlatend de infrastructuurverrichtingen aan Adobe."

Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM as a Cloud Service is de noodzaak voor klanten om de operationele eigenschappen van onderhoudstaken te configureren minimaal. De klanten kunnen hun middelen op toepassing-vlakke zorgen concentreren, verlatend de infrastructuurverrichtingen aan Adobe.

## Onderhoudstaken configureren {#maintenance-tasks-configuring}

In vorige versies van AEM kon u onderhoudstaken configureren met de onderhoudskaart (Opties > Bewerkingen > Onderhoud). Voor AEM as a Cloud Service is de onderhoudskaart niet meer beschikbaar, dus configuraties moeten worden toegewezen aan broncontrole en worden geïmplementeerd met de Cloud Manager. De Adobe beheert die onderhoudstaken die montages hebben die niet door klanten (bijvoorbeeld, de Inzameling van de Schrapping van de Datastore) configureerbaar zijn. Andere onderhoudstaken kunnen door klanten worden geconfigureerd, zoals in de onderstaande tabel wordt beschreven.

>[!CAUTION]
>
>Adobe behoudt zich het recht voor om de configuratie-instellingen voor onderhoudstaken van een klant te negeren om problemen zoals prestatievermindering te beperken.

De volgende tabel illustreert de onderhoudstaken die beschikbaar zijn.

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Onderhoudstaken</th>
    <th>Wie eigenaar is van de configuratie</th>
    <th>Hoe te om (facultatief) te vormen</th>
  </tr>  
  <tr>
    <td>Afvalverzameling datastore</td>
    <td>Adobe</td>
    <td>N.v.t. volledig eigendom van de Adobe</td>
  </td> 
  </tr>
  <tr>
    <td>Versie wissen</td>
    <td>Klant</td>
    <td>De zuivering van de versie wordt momenteel onbruikbaar gemaakt door gebrek, maar het beleid kan worden gevormd, zoals die in de <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks"> sectie van de Aanzuivering van de Versie en van de Aanzuivering van het Logboek van de Controle van de Aanzuivering </a> wordt beschreven.<br/><br/> het zuiveren zal spoedig door gebrek worden toegelaten, met die waarden met voeten treden.<br>
   </td>
  </td>
  </tr>
  <tr>
    <td>Logboek controleren leegmaken</td>
    <td>Klant</td>
    <td>Het logboek van de controle zuivert wordt momenteel onbruikbaar gemaakt door gebrek, maar het beleid kan worden gevormd, zoals die in de <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks"> sectie van de Aanzuivering van de Versie en van de Aanzuivering van het Logboek van de Controle </a> wordt beschreven.<br/><br/> het zuiveren zal spoedig door gebrek worden toegelaten, met die waarden met voeten treden.<br>
   </td>
   </td>
  </tr>
  <tr>
    <td>Lucene Binaries Cleanup</td>
    <td>Adobe</td>
    <td>Ongebruikt en daarom door Adobe gehandicapt.</td>
  </td>
  </tr>
  <tr>
    <td>Ad-hoc taak wissen</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf het uit-van-de-doos de configuratieknooppunt van het Venster van het Onderhoud onder <code>/libs</code> door eigenschappen onder de omslag <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> of <code>granite_monthly</code> te creëren.</p>
    <p>Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails. Schakel de onderhoudstaak in door een ander knooppunt onder het bovenstaande knooppunt toe te voegen. Noem het <code>granite_TaskPurgeTask</code>, met attribuut <code>sling:resourceType</code> plaatste aan <code>granite/operations/components/maintenance/task</code> en attribuut <code>granite.maintenance.name</code> plaatste aan <code>TaskPurge</code>. Configureer de OSGI-eigenschappen. Zie <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code> voor de lijst met eigenschappen.</p>
  </td>
  </tr>
    <tr>
    <td>Werkstroom leegmaken</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf het uit-van-de-doos de configuratieknooppunt van het Venster van het Onderhoud onder <code>/libs</code> door eigenschappen onder de omslag <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> of <code>granite_monthly</code> te creëren. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails.</p>
    <p>Schakel de onderhoudstaak in door een ander knooppunt onder het bovenstaande knooppunt toe te voegen (noem het knooppunt <code>granite_WorkflowPurgeTask</code> ) met de juiste eigenschappen. Vorm de eigenschappen OSGI zie <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html#regular-purging-of-workflow-instances"> AEM 6.5 documentatie van de Taak van het Onderhoud </a>.</p>
  </td>
  </tr>
  <tr>
    <td>Project wissen</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf het uit-van-de-doos de configuratieknooppunt van het Venster van het Onderhoud onder <code>/libs</code> door eigenschappen onder de omslag <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> of <code>granite_monthly</code> te creëren. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails.</p>
    <p>Schakel de onderhoudstaak in door een ander knooppunt onder het bovenstaande knooppunt toe te voegen (noem het knooppunt <code>granite_ProjectPurgeTask</code> ) met de juiste eigenschappen. Zie de lijst met [OSGI-eigenschappen](/help/implementing/deploying/configuring-osgi.md) onder **Adobe Projecten leegmaken**.</p>
  </td>
  </tr>
  </tbody>
</table>

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Configuratie van venster Onderhoud</th>
    <th>Wie eigenaar is van de configuratie</th>
    <th>Configuratietype</th>
    <th>Parameters</th>
  </tr>
  <tr>
    <td>Dagelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
  <td>
  <p><strong> windowSchedule=daily </strong> (deze waarde zou niet moeten worden veranderd)</p>
  <p><strong> windowStartTime=HH:MM </strong> die als 24 uurklok gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Dagelijkse Venster van het Onderhoud zouden moeten beginnen uitvoerend.</p>
  <p><strong> windowEndTime=HH:MM </strong> die als 24 uurklok gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Dagelijkse Venster van het Onderhoud zouden moeten ophouden uitvoerend als zij nog niet hebben voltooid.</p>
  <p>Een onderhoudstaak kan niet meer dan één keer tijdens dit tijdsbestek worden uitgevoerd.</p>
  </td> 
  </tr>
  <tr>
    <td>Wekelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td>
    <p><strong> windowSchedule=wekelijks </strong> (deze waarde zou niet moeten worden veranderd)</p>
    <p><strong> windowStartTime=HH:MM </strong> die als 24 uurklok gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het wekelijkse Venster van het Onderhoud zouden moeten beginnen uitvoerend.</p>
    <p><strong> windowEndTime=HH:MM </strong> die als 24 uurklok gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Wekelijkse Venster van het Onderhoud zouden moeten ophouden uitvoerend als zij nog niet hebben voltooid.</p>
    <p>Een onderhoudstaak kan niet meer dan één keer tijdens dit tijdsbestek worden uitgevoerd.</p>
    <p><strong> windowScheduleWeekdays= Serie van twee waarden van 1-7 (bijvoorbeeld, [5,5]) </strong> De eerste waarde van de serie is de begindag wanneer de baan gepland is en de tweede waarde is de einddag wanneer de baan zou worden tegengehouden. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</p>
    </td>
  </tr>
  <tr>
    <td>Maandelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td>
    <p><strong> windowSchedule=month </strong> (deze waarde zou niet moeten worden veranderd)</p>
    <p><strong> windowStartTime=HH:MM </strong> die als 24 uurklok gebruikt. Definieert wanneer de onderhoudstaken die aan het Maandelijkse Onderhoudsvenster zijn gekoppeld, moeten worden uitgevoerd.</p>
    <p><strong> windowEndTime=HH:MM </strong> die als 24 uurklok gebruikt. Definieert wanneer de onderhoudstaken die zijn gekoppeld aan het venster Maandelijks onderhoud, niet meer moeten worden uitgevoerd als ze nog niet zijn voltooid.</p>
    <p>Een onderhoudstaak kan niet meer dan één keer tijdens dit tijdsbestek worden uitgevoerd.</p>
    <p><strong> windowScheduleWeekdays=Array van twee waarden van 1-7 (bijvoorbeeld, [5,5]) </strong> De eerste waarde van de serie is de begindag wanneer de baan gepland is en de tweede waarde is de einddag wanneer de baan zou worden tegengehouden. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</p>
    <p><strong> windowFirstLastStartDay= 0/1 </strong> 0 aan programma op de eerste week van de maand of 1 aan programma op de laatste week van de maand. Het ontbreken van een waarde zou banen effectief plannen op de dag die door windowScheduleWeekdays (elke maand) wordt geregeld.</p>
    </td>
    </tr>
    </tbody>
</table>

**Plaatsen**:

* Dagelijks - /apps/settings/granite/operations/onderhoud/granite_day
* Wekelijks - /apps/settings/granite/operations/onderhoud/graniet_week
* Maandelijks - /apps/settings/granite/operations/onderhoud/granite_maandelijks

**steekproeven van de Code**:

Codemonster 1 (dagelijks)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
  xmlns:jcr="http://www.jcp.org/jcr/1.0" 
  jcr:primaryType="sling:Folder"
  sling:configCollectionInherit="true"
  sling:configPropertyInherit="true"
  windowSchedule="daily"
  windowStartTime="03:00"
  windowEndTime="05:00"
 />
```

Codemonster 2 (wekelijks)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="weekly"
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

Codesteekproef 3 (maandelijks)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="monthly"
   windowFirstLastStartDay=0
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

## Onderhoudstaken voor versiereiniging en controlelogbestand opschonen {#purge-tasks}

Het zuiveren versies en het controlelogboek verminderen de grootte van de bewaarplaats, en in sommige scenario&#39;s, kunnen prestaties verbeteren.

>[!NOTE]
>
>AEM Guides-klanten moeten Version Purge niet configureren.

### Standaardwaarden {#defaults}

Het leegmaken is momenteel niet standaard ingeschakeld, maar dit verandert in de toekomst. De milieu&#39;s die vóór de standaard het zuiveren worden gecreeerd zullen een conservatievere drempel hebben zodat het zuiveren niet onverwacht voorkomt. Zie de secties Leegmaken van versiebestand en Logboek controleren hieronder voor meer informatie over het standaardbeleid voor leegmaken.
<!-- Version purging and audit log purging are on by default, with different default values for environments with ids higher than **TBD** versus those with ids lower than that value. -->

<!-- ### Overriding the default values with a new configuration {#override} -->

De standaardwaarden voor leegmaken kunnen worden overschreven door een configuratiebestand te declareren en te implementeren zoals hieronder wordt beschreven.

<!-- The reason for this behavior is to clarify the ambiguity over whether the default purge values would take effect once you remove the declaration. -->

### Een configuratie toepassen {#configure-purge}

Declareer een configuratiedossier en stel het op zoals die in de volgende stappen wordt beschreven.

>[!NOTE]
>Zodra u de versie zuivert knoop in het configuratiedossier opstelt, moet u het houden gedeclareerd en niet het verwijderen. De configuratiepijplijn zal ontbreken als u probeert om dit te doen.
> 
>Op dezelfde manier zodra u de knoop van de zuivering van het controlelogboek in het configuratiedossier opstelt, moet u het gedeclareerd houden en niet het verwijderen.

**1** - creeer de volgende omslag en dossierstructuur in de top-level omslag van uw project in Git:

```
config/
     mt.yaml
```

**2** - verklaar eigenschappen in het configuratiedossier, die omvatten:

* een &quot;kind&quot;bezit met de waarde &quot;MaintenanceTasks&quot;.
* een eigenschap &quot;version&quot; (momenteel is dit versie 1).
* een optioneel object ‘metadata’ met de eigenschap `envTypes` met een door komma&#39;s gescheiden lijst van het omgevingstype (dev, stage, prod) waarvoor deze configuratie geldig is. Als er geen object metadata wordt gedeclareerd, is de configuratie geldig voor alle omgevingstypen.
* een gegevensobject met zowel `versionPurge` - als `auditLogPurge` -objecten.

Zie de definities en syntaxis van de objecten `versionPurge` en `auditLogPurge` hieronder.

U zou de configuratie gelijkend op het volgende voorbeeld moeten structureren:

```
kind: "MaintenanceTasks"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  versionPurge:
    maximumVersions: 15
    maximumAgeDays: 20
    paths: ["/content"]
    minimumVersions: 1
    retainLabelledVersions: false
  auditLogPurge:
    rules:
      - replication:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["Activate", "Deactivate", "Delete", "Test", "Reverse", "Internal Poll"]
      - pages:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["PageCreated", "PageModified", "PageMoved", "PageDeleted", "VersionCreated", "PageRestored", "PageValid", "PageInvalid"]
      - dam:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["ASSET_EXPIRING", "METADATA_UPDATED", "ASSET_EXPIRED", "ASSET_REMOVED", "RESTORED", "ASSET_MOVED", "ASSET_VIEWED", "PROJECT_VIEWED", "PUBLISHED_EXTERNAL", "COLLECTION_VIEWED", "VERSIONED", "ADDED_COMMENT", "RENDITION_UPDATED", "ACCEPTED", "DOWNLOADED", "SUBASSET_UPDATED", "SUBASSET_REMOVED", "ASSET_CREATED", "ASSET_SHARED", "RENDITION_REMOVED", "ASSET_PUBLISHED", "ORIGINAL_UPDATED", "RENDITION_DOWNLOADED", "REJECTED"]
```

Houd er rekening mee dat de configuratie alleen geldig is als:

* alle eigenschappen moeten worden gedefinieerd. Er zijn geen overgeërfde standaardinstellingen.
* de typen (gehele getallen, tekenreeksen, booleans, enz.) in de onderstaande eigenschappentabellen moeten in acht worden genomen.

>[!NOTE]
>Met `yq` kunt u de YAML-opmaak van het configuratiebestand lokaal valideren (bijvoorbeeld `yq mt.yaml` ).

**3** - vorm de pijpleidingen van de niet-productie en van de productieconfiguratie.

Rapid Development Environment (RDE&#39;s) bieden geen ondersteuning voor leegmaken. Voor andere milieutypes in productie (niet zandbak) programma&#39;s, creeer een gerichte plaatsing config pijpleiding in Cloud Manager.

Zie [ vormend productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) en [ vormend niet-productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) voor meer details.

### Versie wissen {#version-purge}

>[!NOTE]
>
>AEM Guides-klanten moeten Version Purge niet configureren.

#### Standaardwaarden versie wissen {#version-purge-defaults}

<!-- For version purging, environments with an id higher than **TBD** have the following default values: -->

Het leegmaken is momenteel niet standaard ingeschakeld, maar dit verandert in de toekomst.

De omgevingen die zijn gemaakt nadat de standaardzuiveringsfunctie is ingeschakeld, hebben de volgende standaardwaarden:

* Versies ouder dan 30 dagen worden verwijderd.
* De meest recente vijf versies in de afgelopen 30 dagen worden bewaard.
* Ongeacht de bovenstaande regels blijft de meest recente versie (naast het huidige bestand) behouden.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Voor omgevingen die zijn gemaakt voordat de standaardzuiveringsfunctie is ingeschakeld, worden de onderstaande standaardwaarden weergegeven. Het wordt echter aanbevolen deze waarden te verlagen om de prestaties te optimaliseren.

* Versies ouder dan 7 jaar worden verwijderd.
* Alle versies in de afgelopen 7 jaar worden bewaard.
* Na 7 jaar worden andere versies dan de meest recente versie (naast het huidige bestand) verwijderd.

#### Eigenschappen van versie wissen {#version-purge-properties}

De toegestane eigenschappen worden hieronder weergegeven.

De kolommen die op *gebrek* wijzen wijzen wijzen wijzen wijzen op de standaardwaarden in de toekomst, wanneer de gebreken worden toegepast; *TBD* wijst op milieu-id die nog niet wordt bepaald.

| Eigenschappen | future default for envs>TBD | toekomstige standaardwaarde voor envs&lt;=TBD | vereist | type | Waarden |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| paden | [&quot;/content&quot;] | [&quot;/content&quot;] | Ja | array van tekenreeksen | Hiermee geeft u op onder welke paden naar purge versies worden gegaan wanneer nieuwe versies worden gemaakt.  Klanten moeten deze eigenschap declareren, maar de enige toegestane waarde is &quot;/content&quot;. |
| maximumAgeDays | 30 | 2557 (7 jaar + 2 schrikkeldagen) | Ja | Geheel | Elke versie die ouder is dan de geconfigureerde waarde, wordt verwijderd. Als de waarde 0 is, wordt het leegmaken niet uitgevoerd op basis van de leeftijd van de versie. |
| maximumVersions | 5 | 0 (geen limiet) | Ja | Geheel | Elke versie die ouder is dan de n-de nieuwste versie, wordt verwijderd. Als de waarde 0 is, wordt het leegmaken niet uitgevoerd op basis van het aantal versies. |
| minimumVersions | 1 | 1 | Ja | Geheel | Het minimale aantal versies dat ongeacht de leeftijd wordt bewaard. Ten minste één versie wordt altijd behouden; de waarde ervan moet 1 of hoger zijn. |
| preserveLabledVersioned | false | false | Ja | boolean | Hiermee bepaalt u of expliciet gelabelde versies worden uitgesloten van de verwijdering. Voor een betere optimalisatie van de opslagplaats wordt aangeraden deze waarde in te stellen op false. |


**Interacties van het Bezit**

In de volgende voorbeelden wordt getoond hoe eigenschappen interageren wanneer ze worden gecombineerd.

Voorbeeld:

```
maximumAgeDays = 30
maximumVersions = 10
minimumVersions = 2
```

Als er 11 versies zijn op dag 23, wordt de oudste versie leeggemaakt wanneer de onderhoudstaak voor leegmaken wordt uitgevoerd, aangezien de eigenschap `maximumVersions` op 10 is ingesteld.

Als er 5 versies op dag 31 zijn, wordt alleen 3 gewist omdat de eigenschap `minimumVersions` is ingesteld op 2.

Voorbeeld:

```
maximumAgeDays = 30
maximumVersions = 0
minimumVersions = 1
```

Geen versies hoger dan 30 dagen worden gewist, omdat de eigenschap `maximumVersions` op 0 is ingesteld.

Eén versie ouder dan 30 dagen wordt bewaard.

### Logboek controleren leegmaken {#audit-purge}

#### Standaardwaarden controlelogbestand wissen {#audit-purge-defaults}

<!-- For audit log purging, environments with an id higher than **TBD** have the following default values: -->

Het leegmaken is momenteel niet standaard ingeschakeld, maar dit verandert in de toekomst.

De omgevingen die zijn gemaakt nadat de standaardzuiveringsfunctie is ingeschakeld, hebben de volgende standaardwaarden:

* Replicatie-, DAM- en pagina-auditlogs die ouder zijn dan 7 dagen, worden verwijderd.
* Alle mogelijke gebeurtenissen worden geregistreerd.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Voor omgevingen die zijn gemaakt voordat de standaardzuiveringsfunctie is ingeschakeld, worden de onderstaande standaardwaarden weergegeven. Het wordt echter aanbevolen deze waarden te verlagen om de prestaties te optimaliseren.

* Replicatie-, DAM- en pagina-auditlogs ouder dan 7 jaar worden verwijderd.
* Alle mogelijke gebeurtenissen worden geregistreerd.

>[!NOTE]
>Aanbevolen wordt dat klanten, die wettelijke vereisten hebben om onbewerkbare controlelogboeken te produceren, met gespecialiseerde, externe diensten integreren.

#### Eigenschappen van logbestand controleren {#audit-purge-properties}

De toegestane eigenschappen worden hieronder weergegeven.

De kolommen die op *gebrek* wijzen wijzen wijzen wijzen wijzen op de standaardwaarden in de toekomst, wanneer de gebreken worden toegepast; *TBD* wijst op milieu-id die nog niet wordt bepaald.


| Eigenschappen | future default for envs>TBD | toekomstige standaardwaarde voor envs&lt;=TBD | vereist | type | Waarden |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| regels | - | - | Ja | Object | Een of meer van de volgende knooppunten: replicatie, pagina&#39;s, dam. Elk van deze knopen bepaalt regels, met de eigenschappen hieronder. Alle eigenschappen moeten worden gedeclareerd. |
| maximumAgeDays | 7 dagen | 2557 (7 jaar + 2 schrikkeldagen) | Ja | integer | Voor replicatie, pagina&#39;s of dam: het aantal dagen dat de auditlogboeken worden bewaard. Auditlogboeken die ouder zijn dan de geconfigureerde waarde, worden gewist. |
| contentPath | &quot;/content&quot; | &quot;/content&quot; | Ja | String | Het pad waaronder de auditlogboeken worden gewist, voor het verwante type. Moet worden ingesteld op &quot;/content&quot;. |
| typen | alle waarden | alle waarden | Ja | Opsommingsarray | Voor **replicatie**, zijn de opgesomde waarden: Activeer, Deactivate, Schrapping, Test, Omgekeerde, Interne Opiniepeiling. Voor **pagina&#39;s**, zijn de opgesomde waarden: PageCreated, PageModified, PageMoved, PageDelited, VersionCreated, PageRestored, PageRolled uit, PageValid, PageInvalid. Voor **dam**, zijn de opgesomde waarden: ASSET_EXPIRING, METADATA_UPDATED, ASSET_EXPIRED, ASSET_REMOVED, RESTORED, ASSET_MOVED, ASSET_VIEWED, PROJECT_VIEWED, PUBLISHED_EXTERNAL, COLLECTION_VIEVERED. SIONED, ADDED_COMMENT, RENDITION_UPDATED, ACCEPTED, DOWNLOADED, SUBASSET_UPDATED, SUBASSET_REMOVED, ASSET_CREATED, ASSET_SHARED, RENDITION_REMOVED, ASSET_PUBLISHED, ORIGINAL_UPDATED, RENDITION_DOWNLOADED , AFGEWEZEN. |
