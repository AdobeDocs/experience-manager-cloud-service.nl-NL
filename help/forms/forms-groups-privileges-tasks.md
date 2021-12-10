---
title: 'Ingebouwd [!DNL AEM Forms] as a Cloud Service groepen '
seo-title: [!DNL AEM Forms] as a Cloud Service User Groups
description: 'Lijst van uit de doos gebruikersgroepen en toestemmingen die aan elke groep worden toegewezen '
seo-description: List of out of the box user groups and permissions assigned to each group
exl-id: bd66ce92-14d9-47fe-b5d3-022e3e468d25
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: 139
ht-degree: 2%

---

# Groepen en machtigingen {#aem-forms-on-osgi-groups-and-privileges}

U kunt [groepen maken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) en beleid en [gebruikers](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) aan de groepen. Dit beleid controleert toestemmingen van de gebruikers die deel van de groep uitmaken.

Zodra u hebt ingesteld [!DNL AEM Forms] as a Cloud Service, de groepen die in onderstaande lijst worden vermeld, zoals [!DNL forms-users] en de gebruiker van de vorm-macht, zijn automatisch beschikbaar voor toewijzing:

<table>
 <tbody>
  <tr>
   <td>Groeperen</td> 
   <td>Machtigingen</td> 
  </tr>
  <tr>
   <td>[!DNL forms-users] <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Adaptieve Forms maken, voorvertonen, publiceren en verzenden</li> 
    <!-- <li>Create, preview, and publish interactive communications and document fragments</li> -->
     <li>Elementen uploaden naar een AEM-instantie</li> 
     <li>Thema's maken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL forms-power-user]</td> 
   <td>
    <ul> 
     <li>Adaptieve Forms maken, voorvertonen, publiceren en verzenden</li> 
     <!-- <li>Create, preview, and publish interactive communications and document fragments</li> 
     <li>Create scripts for Adaptive Forms using code editor</li> -->
     <li>Elementen uploaden, inclusief scripts</li> 
     <li>Thema's maken</li> 
     <li>Pakketten importeren die XDP bevatten</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Review submissions</li> 
     <li>Approve or reject submissions</li> 
    </ul> </td> 
  </tr> -->
  <tr>
   <td>[!DNL template-authors] <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Adaptieve Forms maken en voorvertonen <!-- or interactive communications --> sjablonen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>[!DNL fdm-authors]</p> </td> 
   <td>
    <ul> 
     <li>Een formuliergegevensmodel maken en wijzigen</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>cm-agent-users</td> 
   <td>
    <ul> 
     <li>Access Correspondence Management letters or interactive communications using Agent UI</li> 
    </ul> </td> 
  </tr> --> 
  <!-- <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> -->
    <!-- <li>Create an inbox application</li>  -->
    <!-- <li>Create a workflow model</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL workflow-users]</td> 
   <td>
    <ul> 
     <li>Use AEM inbox applications<br /> -->
     <!-- 
     <strong>Note: </strong>You must have cm-agent-users and [!DNL workflow-users] group assignments to access Interactive Communications Agent UI in AEM inbox.</li>  -->
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL fd-administrators]</td> 
   <td>
    <ul> 
     <!-- <li>Configure PDF Generator</li> --> 
     <!-- <li>Configure Watched folder</li> -->
     <li>Workflowtoepassingen beheren</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>
