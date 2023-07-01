---
title: Procedure voor het instellen van een [!DNL AEM Forms] as a Cloud Service omgeving?
description: Leer instellen en configureren van een [!DNL AEM Forms] as a Cloud Service omgeving
exl-id: 42f53662-fbcf-4676-9859-bf187ee9e4af
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Aan boord tot [!DNL AEM Forms] as a Cloud Service {#overview}

## Persoonlijke beslissingen nemen {#personas-aem-forms-project}

<!-- When you sign up for the service, Adobe creates an Organization identifier for your company in the Adobe Identity Management System (IMS), where your users and their permissions can be managed. So, --> Voordat u een [!DNL AEM Forms] as a Cloud Service omgeving, kunt u personen kiezen en een team voor uw project structureren. Een standaard [!DNL AEM Forms] projectteam heeft de volgende personen:

* **UX-ontwerper (User Experience)**: Een ontwerper van de Ervaring van de Gebruiker (UX) bepaalt stijl, lay-out, en branding voor [!DNL AEM Forms] activa.

* **Forms-expert**: Een Forms-expert maakt Adaptive Forms, thema&#39;s en sjablonen op basis van de stijl, lay-out en branding die door de UX-ontwerper worden geboden. De deskundige creeert en integreert ook Aangepast Vorm met een Model van de Gegevens van het Vorm en AEM Workflows. Een Forms Practitioner voert gewoonlijk aan de voorzijde gerelateerde taken uit.

* **Forms developer**: Een Forms-ontwikkelaar ontwikkelt een aangepaste formulieroplossing.  Een Forms-ontwikkelaar ontwikkelt zich doorgaans op de achtergrond, zoals het ontwikkelen van aangepaste componenten, AEM workflows, prefill-service en meer.

* **AEM**: Een AEM beheerder helpt bij de algemene configuratie, zoals het instellen van gebruikers, het verharden van de omgeving, het configureren van gegevensbronnen, het configureren van e-mail en software van derden. AEM beheerder helpt ook bij integratie met Adobe Analytics, Adobe Target en Adobe Sign.

* **Eindgebruiker**: Een eindgebruiker communiceert met en verzendt het gepubliceerde formulier, ondertekent ingediende formulieren, volgt ingediende toepassingen via het webportaal en ontvangt gepersonaliseerde communicatie.

<!-- While onboarding to the service, assign the following AEM groups to [!DNL AEM Forms] as a Cloud Service based on their role:

| User type | AEM group |
|---|---|
| Form Practitioner | forms-users (AEM Forms Users), template-authors, workflow-user, workflow-editors, and fdm-author  |
| UX Designer| forms-users, template-authors|
| End-User| <ul> <li>When a user must login to view and submit an Adaptive Form, add such users to forms-users group. </li> <li>When no user authentication is required to access Adaptive Forms, do not assign any group to such users. </li> </ul>| -->

## Aan boord van de service {#onboarding}

* [Aan boord](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html) aan de [!DNL Adobe Experience Manager] as a Cloud Service.

* (Alleen voor sandboxen) Na het instappen van de service [maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) en [run](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) zowel productiepijpleidingen als niet-productiepijpleidingen. De nieuwste functies van [!DNL AEM Forms] as a Cloud Service voor uw omgeving.

U kunt Forms as a Cloud Service gebruiken om een adaptief formulier (Digital Enrollment) te maken of een klantcommunicatie te genereren. Na voltooiing [Onboarding](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html) aan de [!DNL Adobe Experience Manager] as a Cloud Service, voer één van de volgende acties uit om Digitale Inschrijving of Communicatie van de Klant eigenschappen toe te laten. U kunt ook beide functies inschakelen:

1. Meld u aan bij Cloud Manager en open de as a Cloud Service AEM Forms-instantie.

1. Open de optie Programma bewerken, ga naar het tabblad Oplossingen en invoegtoepassingen en selecteer de optie **[!UICONTROL Forms - Communications]** optie.

   ![Communicatie](assets/communications.png)

   Als u al **[!UICONTROL Forms - Digital Enrollment]** en selecteert u vervolgens de optie **[!UICONTROL Forms - Communications Add-On]** optie.

   ![Addon](assets/add-on.png)

1. Klik op **[!UICONTROL Update]**.

1. Stel de bouwstijlpijpleiding in werking. Nadat de bouwstijlpijpleiding slaagt, Communicatie APIs wordt toegelaten voor uw milieu.

>[!NOTE]
>
> Als u API&#39;s voor documentmanipulatie wilt inschakelen en configureren, voegt u de volgende regel toe aan [Dispatcher-configuratie](setup-local-development-environment.md#forms-specific-rules-to-dispatcher):
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## Gebruikers configureren {#config-users}

Meld u aan bij uw [!DNL AEM Forms] as a Cloud Service omgeving, instanties voor auteurs en publiceren openen en gebruikers toevoegen aan Forms-specifieke [AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing), gebaseerd op hun persoonlijkheid. De volgende tabel bevat een lijst met Forms-specifieke AEM groepen, beschikbaar in het vak, en de bijbehorende gebruikerstypen. De tabel bevat ook AEM instantietype voor elk gebruikerstype:

| Gebruikerstypen (Persoonlijk) | Gebruikersgroepen | AEM |
|---|---|---|
| Formulierpraktiserer/Forms-ontwikkelaar | <ul> <li> [!DNL forms-users] </li><li> [!DNL template-author] </li><li> [!DNL workflow-users] </li><li> [!DNL workflow-editors] </li><li> [!DNL fdm-authors] </li></ul> | Instantie van auteur |
| UX-ontwerper (User Experience) | <ul> <li> [!DNL forms-users]</li><li> [!DNL template-author] </li></ul> | Instantie van auteur |
| AEM-beheerder | <ul> <li>[!DNL aem-administrators],</li> <li>[!DNL fd-administrators] </li> </ul> | Instantie Auteur en Publiceren |
| Eindgebruiker | <ul> <li>Wanneer een gebruiker zich moet aanmelden om een adaptief formulier te bekijken en te verzenden, voegt u deze gebruikers toe aan [!DNL forms-users] groep. </li> <li>Wanneer geen gebruikersverificatie is vereist voor toegang tot Adaptive Forms, wijst u geen groep toe aan dergelijke gebruikers. </li> </ul> | Instantie Auteur en Publiceren |

Zie voor meer informatie over Forms-specifieke AEM en bijbehorende machtigingen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

<!-- You can also create  [user groups](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) specific  to your organization, assign policies, and [users](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) to the groups. The policies help control permissions of the users that are part of the group. For information a -->

## Volgende stap {#next-steps}

[Een lokale ontwikkelomgeving instellen](setup-local-development-environment.md). U kunt de lokale ontwikkelomgeving gebruiken voor het maken van een adaptief formulier en gerelateerde elementen (thema&#39;s, sjablonen, aangepaste verzendacties, vooraf aanvulservice en meer) en [PDF forms converteren naar Adaptief Forms](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html) zonder aanmelding bij de ontwikkelomgeving van de cloud.

<!-- ### Business unit and end-users {#business-unit-and-end-users}

| Role| Organization| Description|
|-----|-------|-----|
| UX Designer                  | Customer/System Integrator/Partner | Defines user experience design (style, layout, branding) as per organizational requirements for Adaptive Forms to allow AEM Forms practitioners to design the corresponding themes and templates.                                     |
| Forms Practitioner           | Customer                           | Authors Adaptive Forms, creates Form Data Model integrations, and creates business workflows using the Experience Manager Workflows. Typically undertakes the front-end work.                                                         |
| Business Executive - Digital | Customer                           | Responsible for business unit’s product marketing strategy and revenues, main business stakeholders for digital use cases, solutions, and service offerings for the end-users, signs off on the use case implementation and delivery. |
| Customer Experience Lead     | Customer                           | Business user persona. Authors, personalizes and updates Adaptive Forms fields/rules/styling, identifies, and prioritizes business needs. Validates business use-case with SI/Partner developers/practitioners during UAT.            |
| Forms Back-Office User       | Customer                           | End-user internal to organization filling forms, participating in back-office Forms workflows such as review/approval of applications etc.                                                                                            |
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

[Onboard](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html) to the [!DNL Adobe Experience Manager] as a Cloud Service. 

After you onboard the service, configure a [local development environment](setup-local-development-environment.md). 

Administrators are responsible for managing Adobe software and services for their organization. Administrators grant access to developers in their organization to connect and use your [!DNL AEM Forms] as a Cloud Service program. When an administrator is provisioned for an organization, the administrator receives an email with title ‘You now have administrator rights to manage Adobe software and services for your organization’. If you are an administrator, check your mailbox for email with previously mentioned title and proceed to [add users](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) via IMS and assign [form-specific groups](forms-groups-privileges-tasks.md) to users based on their role.

## Next step {#next-steps} -->

<!-- ## Prerequisites {#prerequisites}

If you are new to AEM as a cloud service, contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS). Once Adobe has created an organization for your company, your designated administrator is added as the first member of the organization. The administrator can setup an [!DNL AEM Forms] as a Cloud Service instance. 

## Onboard and set up a new environment {#onboard-and-setup-a-new-environment}

Log in to Cloud Manager and create a program. After the program is ready, create environments, add developers or users to environments, and run the pipeline to get the latest version of [!DNL AEM Forms] as a Cloud Service and start developing for your environment. The detailed steps are:

1. Contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS) and provide access to an administrator in your organization.
1. Configure [Automated Forms Conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=en). After a configuration is complete, a profile for Automated Forms Conversion Service is available in [Admin Console](https://adminconsole.adobe.com/).

    If the service is not available, log in to [Admin Console](https://adminconsole.adobe.com/). Use Adobe ID of administrator provisioned to use Automated Forms Conversion Service to login. Do not use any other ID or Federated ID to login.
    1. Click **[!UICONTROL Automated Forms Conversion Service]** option.
    1. Click **[!UICONTROL New Profile]** in the Products tab.
    1. Specify **[!UICONTROL Name]**, **[!UICONTROL Display Name]**, and **[!UICONTROL Description]** for the profile. Click **[!UICONTROL Done]**. A profile is created. 
1. Log in to [Cloud Manager](https://experience.adobe.com/#/@marketinghub/experiencemanager) and [create a program](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) for your organization.
1. [Create environments](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#adding-environments) within your program.
1. Log in to [Admin console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html) and add developers or users to your organization.
1. Run the [build pipeline](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/deploying-code.html). It brings latest [!DNL Experience Manager Forms] as a Cloud Service features to your environment.
1. [Start developing](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) and creating Adaptive Forms on [!DNL Experience Manager Forms] as a Cloud Service environment.
1. Configure the [local development environment](setup-local-development-environment.md) for rapid development

## Configure dispatcher caching {#caching}

You can make dispatcher caching related configuration changes to code on your local development instance and deploy the changes to your [!DNL AEM Forms] as a Cloud Service instance. For details, see [update dispatcher configuration](setup-local-development-environment.md).
 -->
