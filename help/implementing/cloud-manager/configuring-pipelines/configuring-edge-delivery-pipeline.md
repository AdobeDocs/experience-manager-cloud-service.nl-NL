---
title: Een Edge Delivery Pipeline toevoegen
description: Leer hoe u een Edge Delivery-pijplijn toevoegt om uw code te maken en te implementeren in productieomgevingen.
index: false
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Vroege adoptie" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: true
hidefromtoc: true
source-git-commit: acb919474bfe4285c889b8646f731285f5b759ba
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---



# Een Edge Delivery-pijpleiding toevoegen {#configure-production-pipeline}

Leer hoe u Edge Delivery-pijpleidingen configureert voor het maken en implementeren van uw code in productieomgevingen. Een productiepijpleiding stelt code eerst aan het werkgebiedmilieu op. Bij goedkeuring, stelt het de zelfde code aan het productiemilieu op.

Een gebruiker moet de [&#128279;](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)**rol hebben van de Manager van de Plaatsing 0&rbrace; om productiepijpleidingen te vormen.**

>[!NOTE]
>
>Een productiepijplijn kan pas worden aangelegd nadat het volgende is gebeurd:
>
>* Het programma wordt gemaakt.
>* De Git-opslagplaats heeft minstens één vertakking.
>* De productie- en staging-omgevingen worden gemaakt.

Alvorens u begint om uw code op te stellen, vorm uw pijpleidingsmontages van [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt [ pijpleidingsmontages ](managing-pipelines.md) na de aanvankelijke opstelling uitgeven.

## Een nieuwe Edge Delivery-pijpleiding toevoegen {#adding-production-pipeline}

Zodra u opstelling uw programma hebt en minstens één milieu gebruikend [!UICONTROL Cloud Manager] UI heeft, bent u bereid om een productiepijplijn toe te voegen door deze stappen te volgen.

>[!TIP]
>
>Alvorens u een front-end pijpleiding vormt, zie de [ Reis van de Aanmaak van de Plaats van AEM Snelle ](/help/journey-sites/quick-site/overview.md) voor een gids van begin tot eind door het makkelijk te gebruiken hulpmiddel van de Aanmaak van de Plaats van AEM Snelle. Deze reis kan u helpen de front-end ontwikkeling van uw Plaats van AEM stroomlijnen, die u uw plaats met geen AEM achterste-eindkennis laat snel aanpassen.

**om een nieuwe pijpleiding van Edge Delivery toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik **toevoegen** om **te selecteren voeg de Pijpleiding van de Productie** toe.

   ![ de kaart van Pijpleidingen op het overzicht van de Manager van het Programma ](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **voegt de vertoningen van de de dialoogdoos van de Pijpleiding van de Productie** toe. Verstrek de Naam van de a **Pijpleiding** om uw pijpleiding samen met de volgende opties te identificeren. Klik **verdergaan**.

   **Trigger van de Plaatsing** - u hebt de volgende opties wanneer het bepalen van de plaatsingstrekkers om de pijpleiding te beginnen.

   * **Handboek** - Begin manueel de pijpleiding.
   * **op de Veranderingen van het Git** - begint de pijpleiding CI/CD wanneer de bemoeienis aan de gevormde tak van het Git wordt toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

   **Belangrijk Metrisch Gedrag van Mislukt** - tijdens pijpleidingsopstelling of geef uit, heeft de **Manager van de Plaatsing** de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitspoorten wordt ontmoet. De beschikbare opties zijn:

   * **vraag telkens als** - Gebrek het plaatsen. Het vereist handmatige ingrepen in elke belangrijke mislukking.
   * **onmiddellijk het Eindigen** - als geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. Dit proces emuleert in wezen een gebruiker manueel die elke mislukking verwerpt.
   * **gaat onmiddellijk** - als geselecteerd voort, gaat de pijpleiding automatisch wanneer een belangrijke mislukking voorkomt. Dit proces emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

   ![ de pijpleidingsconfiguratie van de Productie ](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Op het **lusje van de Code van Source**, selecteer welk type van code de pijpleiding zou moeten verwerken.

   * **[vorm een volledige pijpleiding van de stapelcode](#full-stack-code)**
   * **[vorm een gerichte plaatsingspijpleiding](#targeted-deployment)**

Zie [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie over de types van pijpleidingen.

De stappen om de verwezenlijking van uw productiepijplijn te voltooien variëren afhankelijk van het type van broncode u selecteerde. Volg de verbindingen hierboven om aan de volgende sectie van dit document te springen zodat kunt u de configuratie van uw pijpleiding voltooien.

