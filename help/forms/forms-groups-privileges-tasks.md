---
title: Welke gebruikersgroepen zijn beschikbaar uit de doos in AEM Forms as a Cloud Service?
description: Lijst van uit de doos gebruikersgroepen en toestemmingen die aan elke groep worden toegewezen
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: bd66ce92-14d9-47fe-b5d3-022e3e468d25
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 3%

---

# Groepen en machtigingen {#aem-forms-on-osgi-groups-and-privileges}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

U kunt [&#x200B; groepen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=nl-NL#accessing) tot stand brengen en beleid en [&#x200B; gebruikers &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=nl-NL#accessing) aan de groepen toewijzen. Dit beleid controleert toestemmingen van de gebruikers die deel van de groep uitmaken.

Nadat u [!DNL AEM Forms] as a Cloud Service hebt ingesteld, zijn de groepen in de onderstaande tabel, zoals [!DNL forms-users] en gebruikers die het formulierbeheer gebruiken, automatisch beschikbaar voor toewijzing:

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
     <li>Adaptieve Forms-sjablonen maken en voorvertonen <!-- or interactive communications --></li> 
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
