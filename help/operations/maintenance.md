---
title: Onderhoudstaken in AEM as a Cloud Service
description: Onderhoudstaken in AEM as a Cloud Service
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: 9177741a57bb16c36b51d1a042538b9cee20a0b8
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# Onderhoudstaken in AEM as a Cloud Service

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Onderhoudstaken"
>abstract="Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM as a Cloud Service, is de behoefte aan klanten om de operationele eigenschappen van onderhoudstaken te vormen minimaal. De klanten kunnen hun middelen op toepassing-vlakke zorgen concentreren, verlatend de infrastructuurverrichtingen aan Adobe."

Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM as a Cloud Service, is de behoefte aan klanten om de operationele eigenschappen van onderhoudstaken te vormen minimaal. De klanten kunnen hun middelen op toepassing-vlakke zorgen concentreren, verlatend de infrastructuurverrichtingen aan Adobe.

## Onderhoudstaken configureren

In vorige versies van AEM kon u onderhoudstaken configureren met de onderhoudskaart (Opties > Bewerkingen > Onderhoud). Voor AEM as a Cloud Service, is de Kaart van het Onderhoud niet meer beschikbaar zodat zouden de configuraties aan broncontrole moeten worden geëngageerd en door de Manager van de Wolk worden opgesteld. Adobe zal onderhoudstaken beheren die geen klantenbesluiten (bijvoorbeeld, de Inzameling van het huisvuil van de Datastore) vereisen terwijl andere onderhoudstaak door de klant kan worden gevormd (zie de lijst hieronder).

>[!CAUTION]
>
>Adobe behoudt zich het recht voor om de configuratie-instellingen voor onderhoudstaak van een klant te negeren om problemen zoals prestatievermindering te beperken.

De volgende tabel illustreert de onderhoudstaken die beschikbaar zijn op het moment van de release van AEM as a Cloud Service.

<!--| Maintenance Task | Who owns the configuration | How to configure (optional)  |
|---|---|---|
| Datastore garbage collection | Adobe | N/A - fully Adobe owned |
| Version Purge | Adobe | Fully owned by Adobe, but in the future, customers will be able to configure certain parameters. |
| Audit Log Purge  | Adobe | Fully owned by Adobe, but in the future, customers will be able to configure certain parameters. |
| Lucene Binaries Cleanup | Adobe | Unused and therefore disabled by Adobe. |
| Ad-hoc Task Purge | Customer | Must be done in git. <br> Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the the folder `/apps/settings/granite/operations/maintenance/granite_weekly` or `granite_daily`. See the Maintenance Window table below for additional configuration details. <br> Enable the maintenance task by adding another node under the node above (name it `granite_TaskPurgeTask`) with the appropriate properties. <br> Configure the OSGI properties see the [AEM 6.5 Maintenance Task documentation](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)|
| Workflow Purge | Customer |  Must be done in git. <br> Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the the folder`/apps/settings/granite/operations/maintenance/granite_weekly` or `granite_daily`. See the Maintenance Window table below for additional configuration details. <br> Enable the maintenance task by adding another node under the node above (name it `granite_WorkflowPurgeTask`) with the appropriate properties. <br> Configure the OSGI properties see [AEM 6.5 Maintenance Task documentation](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Project Purge | Customer |  Must be done in git. <br> Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the the folder `/apps/settings/granite/operations/maintenance/granite_weekly` or `granite_daily`. See the Maintenance Window table below for additional configuration details. <br> Enable the maintenance task by adding a node under the node above (name it `granite_ProjectPurgeTask`) with the appropriate properties. <br> Configure OSGI properties see [AEM 6.5 Maintenance Task documentation](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Customers can schedule each of the Workflow Purge, Ad-hoc Task Purge and Project Purge Maintenance tasks to be executed during the daily, weekly, or monthly maintenance windows. These configurations should be edited directly in source control. The table below describes the configuration parameters available for each of the window. Also, see the locations and code samples provided after the table.-->

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
    <td>N.v.t. volledig in Adobe bezit</td>
  </td> 
  </tr>
  <tr>
    <td>Versie wissen</td>
    <td>Adobe</td>
    <td>Volledig eigendom van Adobe, maar in de toekomst zullen klanten bepaalde parameters kunnen configureren.</td>
  </td>
  </tr>
  <tr>
    <td>Logboek controleren leegmaken</td>
    <td>Adobe</td>
    <td>Volledig eigendom van Adobe, maar in de toekomst zullen klanten bepaalde parameters kunnen configureren.</td>
  </td>
  </tr>
  <tr>
    <td>Lucene Binaries Cleanup</td>
    <td>Adobe</td>
    <td>Ongebruikt en daarom door Adobe uitgeschakeld.</td>
  </td>
  </tr>
  <tr>
    <td>Ad-hoc taak wissen</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf de uit-van-de-doos knoop van de het vensterconfiguratie van het Onderhoud onder <code>/libs</code> door eigenschappen onder de map te maken <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> of <code>granite_daily</code>.</p>
    <p>Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails. Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven toe te voegen (noem het) <code>granite_TaskPurgeTask</code>) met de juiste eigenschappen. Vorm de eigenschappen OSGI zie <a href="https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html">AEM 6.5 Onderhoudstaken</a>.</p>
  </td>
  </tr>
    <tr>
    <td>Werkstroom leegmaken</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf de uit-van-de-doos knoop van de het vensterconfiguratie van het Onderhoud onder <code>/libs</code> door eigenschappen onder de map te maken <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> of <code>granite_daily</code>. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails.</p>
    <p>Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven toe te voegen (noem het) <code>granite_WorkflowPurgeTask</code>) met de juiste eigenschappen. De eigenschappen van OSGI configureren <a href="https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html">AEM 6.5 Onderhoudstaken</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Project wissen</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf de uit-van-de-doos knoop van de het vensterconfiguratie van het Onderhoud onder <code>/libs</code> door eigenschappen onder de map te maken <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> of <code>granite_daily</code>. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails.</p>
    <p>Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven toe te voegen (noem het) <code>granite_ProjectPurgeTask</code>) met de juiste eigenschappen. De eigenschappen van OSGI configureren <a href="https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html">AEM 6.5 Onderhoudstaken</a>.</p>
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
  <p><strong>windowSchedule=daily</strong> (deze waarde mag niet worden gewijzigd)</p>
  <p><strong>windowStartTime=HH:MM</strong> gebruiken als 24-uurs klok. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Dagelijkse Venster van het Onderhoud zouden moeten beginnen uitvoerend.</p>
  <p><strong>windowEndTime=HH:MM</strong> gebruiken als 24-uurs klok. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Dagelijkse Venster van het Onderhoud zouden moeten ophouden uitvoerend als zij nog niet hebben voltooid.</p>
  </td> 
  </tr>
  <tr>
    <td>Wekelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td>
    <p><strong>windowSchedule=wekelijks</strong> (deze waarde mag niet worden gewijzigd)</p>
    <p><strong>windowStartTime=HH:MM</strong> gebruiken als 24-uurs klok. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het wekelijkse Venster van het Onderhoud zouden moeten beginnen uitvoerend.</p>
    <p><strong>windowEndTime=HH:MM</strong> gebruiken als 24-uurs klok. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Wekelijkse Venster van het Onderhoud zouden moeten ophouden uitvoerend als zij nog niet hebben voltooid.</p>
    <p><strong>windowScheduleWeekdays= Array van 2 waarden van 1-7 (bijvoorbeeld [5,5])</strong> De eerste waarde van de array is de startdag waarop de taak is gepland en de tweede waarde is de einddag waarop de taak wordt gestopt. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</p>
    </td>
  </tr>
  <tr>
    <td>Maandelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td>
    <p><strong>windowSchedule=daily</strong> (deze waarde mag niet worden gewijzigd)</p>
    <p><strong>windowStartTime=HH:MM</strong> gebruiken als 24-uurs klok. Definieert wanneer de onderhoudstaken die aan het Maandelijkse Onderhoudsvenster zijn gekoppeld, moeten worden uitgevoerd.</p>
    <p><strong>windowEndTime=HH:MM</strong> gebruiken als 24-uurs klok. Definieert wanneer de onderhoudstaken die zijn gekoppeld aan het venster Maandelijks onderhoud niet meer worden uitgevoerd als deze nog niet zijn voltooid.</p>
    <p><strong>windowScheduleWeekdays=Array van 2 waarden van 1-7 (bijvoorbeeld [5,5])</strong> De eerste waarde van de array is de startdag waarop de taak is gepland en de tweede waarde is de einddag waarop de taak wordt gestopt. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0 naar schema op de eerste week van de maand of 1 naar schema op de laatste week van de maand. Het ontbreken van een waarde zou banen effectief plannen elke dag zoals die door windowScheduleWeekdays elke maand wordt geregeld.</p>
    </td> 
    </tr>
    </tbody>
</table>

**Locaties**:

* Dagelijks - /apps/settings/granite/operations/onderhoud/granite_day
* Wekelijks - /apps/settings/granite/operations/onderhoud/graniet_week
* Maandelijks - /apps/settings/granite/operations/onderhoud/granite_maandelijks

**Codevoorbeelden**:

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
