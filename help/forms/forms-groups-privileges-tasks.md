---
title: Welke gebruikersgroepen zijn beschikbaar uit de doos in as a Cloud Service AEM Forms?
description: Lijst van uit de doos gebruikersgroepen en toestemmingen die aan elke groep worden toegewezen
role: Admin, Developer, User
feature: Adaptive Forms
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 3%

---

# Groepen en machtigingen {#aem-forms-on-osgi-groups-and-privileges}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html) |
| AEM as a Cloud Service | Dit artikel |

U kunt [groepen maken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) en beleid en [gebruikers](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) aan de groepen. Dit beleid controleert toestemmingen van de gebruikers die deel van de groep uitmaken.

Zodra u hebt ingesteld [!DNL AEM Forms] as a Cloud Service, de groepen die in onderstaande lijst worden vermeld, zoals [!DNL forms-users] en de gebruiker van de vorm-macht, zijn automatisch beschikbaar voor toewijzing:

<table>
 <tbody>
  <tr>
   <td>Groep</td> 
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
  <!-- <tr>
   <td>[!DNL forms-power-user]</td> 
   <td>
    <ul> 
     <li>Create, preview, publish, and submit Adaptive Forms</li> 
     <li>Create, preview, and publish interactive communications and document fragments</li> 
     <li>Create scripts for Adaptive Forms using code editor</li> 
     <li>Upload assets including scripts</li> 
     <li>Create themes</li> 
     <li>Import packages containing XDP</li> 
    </ul> </td> 
  </tr>
 <tr>
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

## Zie ook

* [Aan boord van een Cloud Service](/help/forms/setup-forms-cloud-service.md)
* [Een lokale ontwikkelomgeving instellen](/help/forms/setup-local-development-environment.md)
* [Migreren van AEM 6.5 Forms naar Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Een zelfstandig adaptief formulier maken](/help/forms/creating-adaptive-form-core-components.md)
* [Een adaptief formulier toevoegen aan de AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

<!--

>[!MORELIKETHIS]
>
>* [Use AEM Forms workflow for business process automation](/help/forms/aem-forms-workflow.md)

-->