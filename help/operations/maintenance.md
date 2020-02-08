---
title: Onderhoudstaken in AEM als cloudservice
description: 'Onderhoudstaken in AEM als cloudservice '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Onderhoudstaken in AEM als cloudservice

Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM als Cloud Service is de noodzaak voor klanten om de operationele eigenschappen van onderhoudstaken te configureren minimaal. Klanten kunnen hun bronnen richten op problemen op toepassingsniveau en de infrastructuurbewerkingen aan Adobe overlaten.

Raadpleeg de volgende pagina&#39;s voor meer informatie over onderhoudstaken:

* [AEM-onderhoudshandleiding](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Onderhoudstaken van het transactiedashboard](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Onderhoudstaken configureren

In eerdere versies van AEM kon u onderhoudstaken configureren met de onderhoudskaart (Opties > Bewerkingen > Onderhoud). Voor AEM als cloudservice is de onderhoudskaart niet meer beschikbaar, dus configuraties moeten worden toegewezen aan broncontrole en worden geïmplementeerd met gebruik van de cloudbeheer. Adobe zal onderhoudstaken beheren waarvoor geen beslissingen van de klant nodig zijn (bijvoorbeeld Gegevensopslag opschonen), terwijl andere onderhoudstaken door de klant kunnen worden geconfigureerd (zie de onderstaande tabel).

>[!CAUTION]
>
>Adobe behoudt zich het recht voor om de configuratie-instellingen voor onderhoudstaken van de klant te negeren om problemen zoals de verslechtering van de prestaties te beperken.

In de volgende tabel worden de onderhoudstaken weergegeven die beschikbaar zijn op het moment van de release van AEM als Cloud Service.

| Onderhoudstaken | Wie eigenaar is van de configuratie | Hoe te om (facultatief) te vormen |
|---|---|---|
| Afvalverzameling datastore | Adobe | N.v.t. - volledig eigendom van Adobe |
| Versie wissen | Adobe | Volledig eigendom van Adobe, maar in de toekomst kunnen klanten bepaalde parameters configureren. |
| Logboek controleren leegmaken | Adobe | Volledig eigendom van Adobe, maar in de toekomst kunnen klanten bepaalde parameters configureren. |
| Lucene Binaries Cleanup | Adobe | Ongebruikt en daarom door Adobe uitgeschakeld. |
| Ad-hoc taak wissen | Klant | Moet worden gedaan in de geest. <br> Overschrijf het de configuratieknooppunt van het venster van het Onderhoud onder `/libs` en `/apps` met `/conf/global/settings/granite/operations/maintenance/granite_weekly` of `granite_daily`. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails. <br> Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven (naam het `granite_TaskPurgeTask`) met de aangewezen eigenschappen toe te voegen. <br> Vorm de eigenschappen OSGI zie [AEM 6.5 documentatie van de Taak van het Onderhoud](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Werkstroom leegmaken | Klant | Moet worden gedaan in de geest. <br> Overschrijf het de configuratieknooppunt van het venster van het Onderhoud onder `/libs` en `/apps` met `/conf/global/settings/granite/operations/maintenance/granite_weekly` of `granite_daily`. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails. <br> Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven (naam het `granite_WorkflowPurgeTask`) met de aangewezen eigenschappen toe te voegen. <br> Vorm de eigenschappen OSGI zie [AEM 6.5 documentatie van de Taak van het Onderhoud](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Project wissen | Klant | Moet worden gedaan in de geest. <br> Overschrijf het de configuratieknooppunt van het venster van het Onderhoud onder `/libs` en `/apps` met `/conf/global/settings/granite/operations/maintenance/granite_weekly` of `granite_daily`. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails. <br> Laat de onderhoudstaak toe door een knoop onder de knoop hierboven (naam het `granite_ProjectPurgeTask`) met de aangewezen eigenschappen toe te voegen. <br> Vorm eigenschappen OSGI zie [AEM 6.5 documentatie van de Taak van het Onderhoud](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Klanten kunnen elk van de taken voor het opschonen van werkstromen, het opruimen van ad-hoctaken en het opruimen van projecten plannen die tijdens de dagelijkse, wekelijkse of maandelijkse onderhoudsperiode moeten worden uitgevoerd. Deze configuraties zouden direct in broncontrole moeten uitgeven. In de onderstaande tabel worden de configuratieparameters beschreven die beschikbaar zijn voor elk venster.

<table>
  <tr>
    <th>Configuratie van venster Onderhoud</th>
    <th>Wie eigenaar is van de configuratie</th>
    <th>Configuratietype</th>
    <th>Locatie</th>
    <th>Voorbeeld</th>
    <th>Parameters</th>
  </tr>
  <tr>
    <td>Dagelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_daily </code> (waarmee het knooppunt in <code>/apps</code> en <code>/libs</code>wordt overschreven)</td>
    <td>Zie voorbeeld 1 hieronder</td>
   <td>
    <ul>
    <li><strong>windowSchedule</strong> = day (deze waarde mag niet worden gewijzigd)</li>
    <li><strong>windowStartTime</strong> = HH:MM die als klok van 24 uur gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Dagelijkse Venster van het Onderhoud zouden moeten beginnen uitvoerend.</li>
    <li><strong>windowEndTime</strong> = HH:MM die als klok van 24 uur gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Dagelijkse Venster van het Onderhoud zouden moeten ophouden uitvoerend als zij nog niet hebben voltooid.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Wekelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_weekly</code> (waarmee het knooppunt in <code>/apps</code> en <code>/libs</code>wordt overschreven)</td>
    <td>Zie voorbeeld 2 hieronder</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = wekelijks (deze waarde mag niet worden gewijzigd)</li>
    <li><strong>windowStartTime</strong> = HH:MM die als klok van 24 uur gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het wekelijkse Venster van het Onderhoud zouden moeten beginnen uitvoerend.</li>
    <li><strong>windowEndTime</strong> = HH:MM die als klok van 24 uur gebruikt. Bepaalt wanneer de Taken van het Onderhoud verbonden aan het Wekelijkse Venster van het Onderhoud zouden moeten ophouden uitvoerend als zij nog niet hebben voltooid.</li>
    <li><strong>windowScheduleWeekdays = Array van 2 waarden van 1-7. bijv. [5,5].</strong> De eerste waarde van de array is de startdag waarop de taak is gepland en de tweede waarde is de einddag waarop de taak wordt gestopt. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Maandelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_monthly</code> (waarmee het knooppunt in <code>/apps</code> en <code>/libs</code>wordt overschreven)</td>
    <td>Zie codevoorbeeld 3 hieronder</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = day (deze waarde mag niet worden gewijzigd)</li>
    <li><strong>windowStartTime</strong> = HH:MM die als klok van 24 uur gebruikt. Definieert wanneer de onderhoudstaken die aan het Maandelijkse Onderhoudsvenster zijn gekoppeld, moeten worden uitgevoerd.</li>
    <li><strong>windowEndTime</strong> = HH:MM die als klok van 24 uur gebruikt. Definieert wanneer de onderhoudstaken die zijn gekoppeld aan het venster Maandelijks onderhoud niet meer worden uitgevoerd als deze nog niet zijn voltooid.</li>
    <li><strong>windowScheduleWeekdays = Array van 2 waarden van 1-7. bijv. [5,5].</strong> De eerste waarde van de array is de startdag waarop de taak is gepland en de tweede waarde is de einddag waarop de taak wordt gestopt. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</li>
    <li><strong>windowFirstLastStartDay - 0/1</strong> 0 aan planning op de eerste week van de maand of 1 aan planning op de laatste week van de maand. Het ontbreken van een waarde zou banen effectief plannen elke dag zoals die door windowScheduleWeekdays elke maand wordt geregeld.</li>
    </ul> </td> 
  </tr>
</table>

Codevoorbeeld 1

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

Codevoorbeeld 2

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

Codevoorbeeld 3

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
