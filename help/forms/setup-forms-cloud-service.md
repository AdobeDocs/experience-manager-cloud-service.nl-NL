---
title: Hoe opstelling I a [!DNL AEM Forms]  als milieu van de wolkendienst?
description: Leer aan opstelling en vorm een  [!DNL AEM Forms]  as a Cloud Service milieu.
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 42f53662-fbcf-4676-9859-bf187ee9e4af
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 1%

---

# Aan boord tot [!DNL AEM Forms] as a Cloud Service {#overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |


## Persoonlijke beslissingen nemen {#personas-aem-forms-project}

<!-- When you sign up for the service, Adobe creates an Organization identifier for your company in the Adobe Identity Management System (IMS), where your users and their permissions can be managed. So, --> Voordat u een Adobe Experience Manager (AEM) Forms as a Cloud Service-omgeving kunt instappen, moet u zelf bepalen wie u wilt en een team voor uw project structureren. Een typisch [!DNL AEM Forms] projectteam heeft de volgende persona&#39;s:

* **Ervaring van de Gebruiker (UX) Designer**: Een Ervaring van de Gebruiker (UX) Designer bepaalt stijl, lay-out, en branding voor [!DNL AEM Forms] activa.

* **de praktijk van Forms**: Een deskundige van Forms leidt tot Aangepaste Forms, thema&#39;s, en malplaatjes zoals de stijl, lay-out, en branding die door UX Designer wordt verstrekt. De deskundige creeert en integreert ook Aangepast Vorm met een Model van de Gegevens van het Vorm (FDM) en AEM Workflows. Een Forms Practitioner voert gewoonlijk aan de voorzijde gerelateerde taken uit.

* **de ontwikkelaar van Forms**: Een ontwikkelaar van Forms ontwikkelt een oplossing van de douanevormen. Een Forms-ontwikkelaar ontwikkelt zich doorgaans op de achtergrond, zoals het ontwikkelen van aangepaste componenten, AEM workflows, services die vooraf zijn ingevuld en nog veel meer.

* **AEM beheerder**: Een AEM beheerder helpt met algemene configuratie zoals vestiging gebruikers, het verharden van het milieu, het vormen van gegevensbronnen, het vormen van e-mail, en derdesoftware. AEM beheerder helpt ook bij integratie met Adobe Analytics, Adobe Target en Adobe Sign.

* **Eind - gebruiker**: Een gebruiker wisselt met en legt de gepubliceerde vorm voor, ondertekent voorgelegde vormen, volgt voorgelegde toepassingen door een Webportaal, en ontvangt gepersonaliseerde mededelingen.

<!-- While onboarding to the service, assign the following AEM groups to [!DNL AEM Forms] as a Cloud Service based on their role:

| User type | AEM group |
|---|---|
| Form Practitioner | forms-users (AEM Forms Users), template-authors, workflow-user, workflow-editors, and fdm-author  |
| UX Designer| forms-users, template-authors|
| End-User| <ul> <li>When a user must login to view and submit an Adaptive Form, add such users to forms-users group. </li> <li>When no user authentication is required to access Adaptive Forms, do not assign any group to such users. </li> </ul>| -->

## Aan boord van de service {#onboarding}

* [ Onboard ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/overview.html?lang=nl-NL) aan [!DNL Adobe Experience Manager] as a Cloud Service.

* (Alleen voor zandbakken) Na het instappen van de dienst, [ creeer ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/pipelines/production-pipelines.html?lang=nl-NL) en [ stel ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-deployment.html?lang=nl-NL) zowel productie als niet productiepijpleidingen in werking. De nieuwste functies van [!DNL AEM Forms] zijn as a Cloud Service voor uw omgeving.

U kunt Forms as a Cloud Service gebruiken om een adaptief formulier te maken (Digital Enrollment) of om klantcommunicatie te genereren. Na het voltooien van [ onboarding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/overview.html?lang=nl-NL) aan [!DNL Adobe Experience Manager] as a Cloud Service, voer de volgende acties uit om Forms - Digitale Inschrijving of Communicatie van de Klant eigenschappen toe te laten. <!--You can also enable both the features--> :

1. Meld u aan bij Cloud Manager en open AEM Forms as a Cloud Service Instance.
1. Open de optie Programma bewerken en ga naar het tabblad Oplossingen en invoegtoepassingen:

   * Als u een productieomgeving hebt, selecteert u de optie **[!UICONTROL Forms - Communications]** om Forms - Digital Enrollment en Forms - Communications Add-On in te schakelen.

     ![ Mededelingen ](assets/communications.png)

   <!-- If you have already enabled the **[!UICONTROL Forms - Digital Enrollment]** option, then select the **[!UICONTROL Forms - Communications Add-On]** option. ![Addon](assets/add-on.png) -->

   * Als u een sandboxomgeving hebt, selecteert u **[!UICONTROL Forms]** om Forms - Digital Enrollment en Forms - Communications Add-On in te schakelen.

     ![ vorm-Digitale selectie van de Inschrijving ](assets/forms-digital-enrollment1.png)


1. Klik op **[!UICONTROL Update]**.
1. Stel de bouwstijlpijpleiding in werking. Nadat de bouwstijlpijpleiding slaagt, wordt de geselecteerde oplossing toegelaten voor uw milieu.

>[!NOTE]
>
> Om documentmanipulatie APIs toe te laten en te vormen, voeg de volgende regel aan de [ configuratie van Dispatcher ](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) toe:
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## Gebruikers configureren {#config-users}

Nadat u aan de dienst voltooit, login aan uw [!DNL AEM Forms] as a Cloud Service milieu, open de instanties van de Auteur en van Publish, en voegt gebruikers aan Forms-specifieke [ AEM groepen ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=nl-NL#accessing) toe, die op hun persoon worden gebaseerd. De volgende tabel bevat een lijst met Forms-specifieke AEM groepen, beschikbaar in het vak, en de bijbehorende gebruikerstypen. De tabel bevat ook AEM instantietype voor elk gebruikerstype:

| Gebruikerstypen (Persoonlijk) | Gebruikersgroepen | AEM |
|---|---|---|
| Formulierpraktiserer/Forms-ontwikkelaar | <ul> <li> [!DNL forms-users] </li><li> [!DNL template-author] </li><li> [!DNL workflow-users] </li><li> [!DNL workflow-editors] </li><li> [!DNL fdm-authors] </li></ul> | Instantie van auteur |
| Gebruikerservaring (UX) Designer | <ul> <li> [!DNL forms-users]</li><li> [!DNL template-author] </li></ul> | Instantie van auteur |
| AEM-beheerder | <ul> <li>[!DNL aem-administrators] ,</li> <li>[!DNL fd-administrators] </li> </ul> | Auteur- en Publish-instantie |
| Eindgebruiker | <ul> <li>Wanneer een gebruiker zich moet aanmelden om een adaptief formulier te bekijken en te verzenden, voegt u deze gebruikers toe aan de groep [!DNL forms-users] . </li> <li>Wanneer geen gebruikersverificatie is vereist voor toegang tot Adaptive Forms, wijst u geen groep toe aan dergelijke gebruikers. </li> </ul> | Auteur- en Publish-instantie |

Voor meer informatie over Forms-Specifieke AEM groepen en overeenkomstige toestemmingen, zie [ Groepen en toestemmingen ](forms-groups-privileges-tasks.md).

<!-- You can also create  [user groups](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=nl-NL#accessing) specific  to your organization, assign policies, and [users](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=nl-NL#accessing) to the groups. The policies help control permissions of the users that are part of the group. For information a -->

## Volgende stap {#next-steps}

[ opstelling een lokale ontwikkelomgeving ](setup-local-development-environment.md). U kunt een lokale ontwikkelomgeving gebruiken om een adaptief formulier en gerelateerde elementen te maken (thema&#39;s, sjablonen, aangepaste verzendhandelingen, vooraf ingevulde service en meer). En, [ zet PDF forms in AanpassingsForms ](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html?lang=nl-NL) zonder het programma te openen aan een milieu van de wolkenontwikkeling om.

<!-- ### Business unit and end-users {#business-unit-and-end-users}

| Role| Organization| Description|
|-----|-------|-----|
| UX Designer                  | Customer/System Integrator/Partner | Defines user experience design (style, layout, branding) as per organizational requirements for Adaptive Forms to allow AEM Forms practitioners to design the corresponding themes and templates.                                     |
| Forms Practitioner           | Customer                           | Authors Adaptive Forms, creates Form Data Model integrations, and creates business workflows using the Experience Manager Workflows. Typically undertakes the front-end work.                                                         |
| Business Executive - Digital | Customer                           | Responsible for business unit's product marketing strategy and revenues, main business stakeholders for digital use cases, solutions, and service offerings for the end-users, signs off on the use case implementation and delivery. |
| Customer Experience Lead     | Customer                           | Business user persona. Authors, personalizes and updates Adaptive Forms fields/rules/styling, identifies, and prioritizes business needs. Validates business use-case with SI/Partner developers/practitioners during UAT.            |
| Forms Back-Office User       | Customer                           | End-user internal to organization filling forms, participating in back-office Forms workflows such as review/approval of applications and so on.                                                                                            |
| Forms End-User               | External to customer               | Interacts with and submits the published form as end customer or citizen, signs submitted forms, tracks her applications through web portal, receives personalized interactive communications.                                        |

### Project team {#project-team}

| Role | Org | Description|
|-----|-----|-----|
| Experience Manager Administrator | System Integrator /Partner/Customer | Helps with overall installation, configures SSL certificates, configures data sources, email, and other third-party software, integrations like Adobe Analytics, Adobe Target, Automated Forms Conversion Services with Experience Manager instance. |
| Project Manager                  | System Integrator /Partner/Customer | Converts customer use-case into technical requirements, manages schedule/cost/scope for overall project.                                                                                                                                             |
| Product Owner                    | System Integrator /Partner/Customer | Prioritizes and evaluates scrum team's work for high-quality delivery on time.                                                                                                                                                                       |
| Scrum Master                     | System Integrator /Partner/Customer | Ensures agile values and processes in place to deliver on defined requirements as per prioritization by PO.                                                                                                                                          |
| Infrastructure / security expert | System Integrator /Partner/Customer | Provisions and configures best possible infrastructure, security controls and infra processes to address current and projected RASP requirements.                                                                                                    |
| Technical Architect              | System Integrator /Partner/Customer | Provides best high-level architecture and infrastructure guidance for use-case implementation and address RASP (Reliability, Availability, Scalability, and Performance) and security challenges.                                                    | -->

<!-- ## Onboard to the service {#onboarding}

[Onboard](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=nl-NL) to the [!DNL Adobe Experience Manager] as a Cloud Service. 

After you onboard the service, configure a [local development environment](setup-local-development-environment.md). 

Administrators are responsible for managing Adobe software and services for their organization. Administrators grant access to developers in their organization to connect and use your [!DNL AEM Forms] as a Cloud Service program. When an administrator is provisioned for an organization, the administrator receives an email with title 'You now have administrator rights to manage Adobe software and services for your organization'. If you are an administrator, check your mailbox for email with previously mentioned title and proceed to [add users](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=nl-NL#onboarding-users-in-admin-console) by way of IMS and assign [form-specific groups](forms-groups-privileges-tasks.md) to users based on their role.

## Next step {#next-steps} -->

<!-- ## Prerequisites {#prerequisites}

If you are new to AEM as a cloud service, contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS). Once Adobe has created an organization for your company, your designated administrator is added as the first member of the organization. The administrator can setup an [!DNL AEM Forms] as a Cloud Service instance. 

## Onboard and set up a new environment {#onboard-and-setup-a-new-environment}

Log in to Cloud Manager and create a program. After the program is ready, create environments, add developers or users to environments, and run the pipeline to get the latest version of [!DNL AEM Forms] as a Cloud Service and start developing for your environment. The detailed steps are:

1. Contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS) and provide access to an administrator in your organization.
1. Configure [Automated Forms Conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=nl-NL). After a configuration is complete, a profile for Automated Forms Conversion Service is available in [Admin Console](https://adminconsole.adobe.com/).

    If the service is not available, log in to [Admin Console](https://adminconsole.adobe.com/). Use Adobe ID of administrator provisioned to use Automated Forms Conversion Service to login. Do not use any other ID or Federated ID to login.
    1. Click **[!UICONTROL Automated Forms Conversion Service]** option.
    1. Click **[!UICONTROL New Profile]** in the Products tab.
    1. Specify **[!UICONTROL Name]**, **[!UICONTROL Display Name]**, and **[!UICONTROL Description]** for the profile. Click **[!UICONTROL Done]**. A profile is created. 
1. Log in to [Cloud Manager](https://experience.adobe.com/#/@marketinghub/experiencemanager) and [create a program](https://docs.adobe.com/content/help/nl-NL/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) for your organization.
1. [Create environments](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=nl-NL#adding-environments) within your program.
1. Log in to [Admin console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html) and add developers or users to your organization.
1. Run the [build pipeline](https://docs.adobe.com/content/help/nl-NL/experience-manager-cloud-manager/using/how-to-use/deploying-code.html). It brings latest [!DNL Experience Manager Forms] as a Cloud Service features to your environment.
1. [Start developing](https://docs.adobe.com/content/help/nl-NL/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) and creating Adaptive Forms on [!DNL Experience Manager Forms] as a Cloud Service environment.
1. Configure the [local development environment](setup-local-development-environment.md) for rapid development

## Configure dispatcher caching {#caching}

You can make dispatcher caching related configuration changes to code on your local development instance and deploy the changes to your [!DNL AEM Forms] as a Cloud Service instance. For details, see [update dispatcher configuration](setup-local-development-environment.md).
 -->
