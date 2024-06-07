---
title: Onderhoudstaken in AEM as a Cloud Service
description: Leer over onderhoudstaken in AEM as a Cloud Service en hoe te om hen te vormen.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
feature: Operations
role: Admin
source-git-commit: c7488b9a10704570c64eccb85b34f61664738b4e
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---

# Onderhoudstaken in AEM as a Cloud Service {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Onderhoudstaken"
>abstract="Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM as a Cloud Service, is de behoefte aan klanten om de operationele eigenschappen van onderhoudstaken te vormen minimaal. De klanten kunnen hun middelen op toepassing-vlakke zorgen concentreren, verlatend de infrastructuurverrichtingen aan Adobe."

Onderhoudstaken zijn processen die volgens een schema worden uitgevoerd om de opslagplaats te optimaliseren. Met AEM as a Cloud Service, is de behoefte aan klanten om de operationele eigenschappen van onderhoudstaken te vormen minimaal. De klanten kunnen hun middelen op toepassing-vlakke zorgen concentreren, verlatend de infrastructuurverrichtingen aan Adobe.

## Onderhoudstaken configureren {#maintenance-tasks-configuring}

In vorige versies van AEM kon u onderhoudstaken configureren met de onderhoudskaart (Opties > Bewerkingen > Onderhoud). Voor AEM as a Cloud Service, is de Kaart van het Onderhoud niet meer beschikbaar zodat zouden de configuraties aan broncontrole moeten worden geëngageerd en door de Manager van de Wolk worden opgesteld. De Adobe beheert die onderhoudstaken die montages hebben die niet door klanten (bijvoorbeeld, de Inzameling van de Schrapping van de Datastore) configureerbaar zijn. Andere onderhoudstaken kunnen door klanten worden geconfigureerd, zoals in de onderstaande tabel wordt beschreven.

>[!CAUTION]
>
>Adobe behoudt zich het recht voor om de configuratie-instellingen voor onderhoudstaken van een klant te negeren om problemen zoals prestatievermindering te beperken.

De volgende tabel illustreert de onderhoudstaken die beschikbaar zijn op het moment van de release van AEM as a Cloud Service.

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
    <td>Adobe</td>
    <td>Voor bestaande omgevingen (omgevingen die vóór een nog te bepalen datum in 2024 zijn gemaakt) is leegmaken uitgeschakeld en in de toekomst mogelijk met een standaard van 7 jaar. Klanten kunnen deze omgeving configureren met lagere, aangepaste waarden (zoals 30 dagen).<br><br> <!--Alexandru: leave the two line breaks in place, otherwise spacing won't render properly-->De nieuwe milieu's (die gecreeerd die een nog-aan-bepaalde datum in 2024 beginnen) zullen zuiverend toegelaten door gebrek met de hieronder waarden hebben, met klanten die met douanewaarden kunnen vormen.
     <ol>
       <li>Versies ouder dan 30 dagen worden verwijderd</li>
       <li>De meest recente vijf versies in de laatste 30 dagen worden bewaard</li>
       <li>Ongeacht de bovenstaande regels blijft de meest recente versie behouden.</li>
       <br>Aanbevolen wordt dat klanten die wettelijke vereisten hebben om sitepagina's precies te maken zoals zij op een specifieke datum verschenen, met gespecialiseerde, externe diensten integreren.
     </ol></td>
  </td>
  </tr>
  <tr>
    <td>Logboek controleren leegmaken</td>
    <td>Adobe</td>
    <td>Voor bestaande omgevingen (omgevingen die vóór een nog te bepalen datum in 2024 zijn gemaakt) is leegmaken uitgeschakeld en in de toekomst mogelijk met een standaard van 7 jaar. Klanten kunnen deze omgeving configureren met lagere, aangepaste waarden (zoals 30 dagen).<br><br> <!-- See above for the two line breaks -->In nieuwe omgevingen (die zijn gemaakt met een nog te bepalen datum in 2024) wordt de zuiveringsfunctie standaard ingeschakeld onder de <code>/content</code> knooppunt van de repository volgens het volgende gedrag:
     <ol>
       <li>Voor replicatiecontrole worden controlelogboeken ouder dan 3 dagen verwijderd</li>
       <li>Voor DAM-audits (Assets) worden auditlogboeken ouder dan 30 dagen verwijderd</li>
       <li>Voor pagina-controle worden logboeken ouder dan 3 dagen verwijderd.</li>
       <br>Aanbevolen wordt dat klanten die wettelijke vereisten hebben om onbewerkbare controlelogboeken te produceren, met gespecialiseerde, externe diensten integreren.
     </ol></td>
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
    <p>Moet in de put worden gedaan. Overschrijf de uit-van-de-doos knoop van de het vensterconfiguratie van het Onderhoud onder <code>/libs</code> door eigenschappen onder de map te maken <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> of <code>granite_monthly</code>.</p>
    <p>Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails. Schakel de onderhoudstaak in door een ander knooppunt onder het bovenstaande knooppunt toe te voegen. Naam geven <code>granite_TaskPurgeTask</code>, met kenmerk <code>sling:resourceType</code> instellen op <code>granite/operations/components/maintenance/task</code> en kenmerk <code>granite.maintenance.name</code> instellen op <code>TaskPurge</code>. Vorm de eigenschappen OSGI, zie <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code> voor de lijst met eigenschappen.</p>
  </td>
  </tr>
    <tr>
    <td>Werkstroom leegmaken</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf de uit-van-de-doos knoop van de het vensterconfiguratie van het Onderhoud onder <code>/libs</code> door eigenschappen onder de map te maken <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> of <code>granite_monthly</code>. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails.</p>
    <p>Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven toe te voegen (noem het) <code>granite_WorkflowPurgeTask</code>) met de juiste eigenschappen. De eigenschappen van OSGI configureren <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html#regular-purging-of-workflow-instances">AEM 6.5 Onderhoudstaken</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Project wissen</td>
    <td>Klant</td>
    <td>
    <p>Moet in de put worden gedaan. Overschrijf de uit-van-de-doos knoop van de het vensterconfiguratie van het Onderhoud onder <code>/libs</code> door eigenschappen onder de map te maken <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> of <code>granite_monthly</code>. Zie de lijst van het Venster van het Onderhoud hieronder voor extra configuratiedetails.</p>
    <p>Laat de onderhoudstaak toe door een andere knoop onder de knoop hierboven toe te voegen (noem het) <code>granite_ProjectPurgeTask</code>) met de juiste eigenschappen. Zie de lijst van eigenschappen OSGI onder "de Projecten van de Adobe zuiveren Configuratie".</p>
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
  <p>Een onderhoudstaak kan niet meer dan één keer tijdens dit tijdsbestek worden uitgevoerd.</p>
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
    <p>Een onderhoudstaak kan niet meer dan één keer tijdens dit tijdsbestek worden uitgevoerd.</p>
    <p><strong>windowScheduleWeekdays= Array van twee waarden van 1-7 (bijvoorbeeld [5,5])</strong> De eerste waarde van de array is de startdag waarop de taak is gepland en de tweede waarde is de einddag waarop de taak wordt gestopt. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</p>
    </td>
  </tr>
  <tr>
    <td>Maandelijks</td>
    <td>Klant</td>
    <td>JCR-knooppuntdefinitie</td>
    <td>
    <p><strong>windowSchedule=month</strong> (deze waarde mag niet worden gewijzigd)</p>
    <p><strong>windowStartTime=HH:MM</strong> gebruiken als 24-uurs klok. Definieert wanneer de onderhoudstaken die aan het Maandelijkse Onderhoudsvenster zijn gekoppeld, moeten worden uitgevoerd.</p>
    <p><strong>windowEndTime=HH:MM</strong> gebruiken als 24-uurs klok. Definieert wanneer de onderhoudstaken die zijn gekoppeld aan het venster Maandelijks onderhoud, niet meer moeten worden uitgevoerd als ze nog niet zijn voltooid.</p>
    <p>Een onderhoudstaak kan niet meer dan één keer tijdens dit tijdsbestek worden uitgevoerd.</p>
    <p><strong>windowScheduleWeekdays=Array van twee waarden van 1-7 (bijvoorbeeld [5,5])</strong> De eerste waarde van de array is de startdag waarop de taak is gepland en de tweede waarde is de einddag waarop de taak wordt gestopt. De exacte tijd van het begin en het einde wordt bepaald door respectievelijk windowStartTime en windowEndTime.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0 naar schema op de eerste week van de maand of 1 naar schema op de laatste week van de maand. Het ontbreken van een waarde zou banen effectief plannen op de dag die door windowScheduleWeekdays (elke maand) wordt geregeld.</p>
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
