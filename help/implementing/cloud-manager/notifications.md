---
title: Meldingen
description: Leer hoe te om informatie over pijpleidingsplaatsingen te ontvangen gebruikend het het berichtsysteem van Adobe Experience Cloud.
exl-id: c1c740b0-c873-45a8-9518-a856db2be75b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---


# Meldingen {#notifications}

Leer hoe Cloud Manager u op de hoogte brengt van belangrijke gebeurtenissen.

## Meldingen in Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] stuurt u meldingen wanneer een productiepijplijn begint en (met succes of zonder succes) wordt voltooid, aan het begin van een productieimplementatie.

Deze berichten worden verzonden door het [!UICONTROL Experience Cloud] berichtsysteem naar gebruikers in **BedrijfsEigenaar**, **Manager van het Programma**, en **de rollen van de Manager van de Plaatsing**.

De meldingen worden weergegeven in een zijbalk binnen [!UICONTROL Cloud Manager] en in de hele Adobe [!UICONTROL Experience Cloud] . Het belpictogram in de koptekst is gemarkeerd wanneer u nieuwe meldingen hebt.

![ pictogram van Meldingen ](assets/notifications-bell-badged.png)

Klik op het belpictogram om de zijbalk te openen en de meldingen weer te geven. Het **lusje van Meldingen** in sidebar maakt een lijst van de meest recente berichten zoals plaatsingsbevestigingen. Meldingen betreffen uw omgeving.

![ Notifications sidebar ](assets/notifications-activities.png)

Het **lusje van Mededelingen** omvat de aankondigingen van het het productproduct van de Adobe. Aankondigingen betreffen het product.

![ Notifications sidebar ](assets/notificaitons-announcements.png)

Klik op een melding of aankondiging om de details weer te geven. De berichten verbonden aan activiteiten zoals pijpleidingsplaatsingen nemen u aan het detail van die activiteit zoals het venster van de pijpleidingsuitvoering.

Klik de **Mening allen** optie bij de bodem van het paneel om alle aankondigingen in uw inbox te bekijken.

Klik het **Teken allen als gelezen** optie bij de bodem van het paneel om alle ongelezen berichten als gelezen te merken en het belpictogram te ontruimen.

## Configuratie van melding {#configuration}

U kunt aanpassen hoe u meldingen ontvangt en welke meldingen u ontvangt.

Klik op het tandwielpictogram boven aan de zijbalk met meldingen.

![ pictogram van de montages van het Bericht ](assets/notifications-configuration.png)

Dit opent het **venster van de voorkeur van het Experience Cloud**, waar u uw berichtabonnementen kunt bepalen en hoe u uw berichten ontvangt.

### Abonnementen {#subscriptions}

In abonnementen wordt gedefinieerd voor welke producten u meldingen ontvangt en welke meldingen.

![ abonnementen van het Bericht ](assets/notifications-subscriptions.png)

Standaard ontvangt u alle meldingen voor alle producten, zowel in de toepassing als via e-mail. Klik op het pictogram naast een productnaam om de gedetailleerde opties weer te geven en de typen meldingen te definiëren die u voor dat product ontvangt. U kunt ook de opties op productniveau in- of uitschakelen om alle opties voor het product in of uit te schakelen.

![ aanpassing van het abonnement van het Bericht ](assets/notifications-subscriptions-customize.png)

### Prioriteit {#priority}

Het prioritaire alarm wordt duidelijk met a **HOGE** markering en kan worden gevormd om als alarm uitsluitend worden ontvangen. In de **Prioriteit** sectie, kunt u bepalen welke categorieën als prioritaire berichten kwalificeren.

![ prioriteit van het Bericht ](assets/notifications-priority.png)

Gebruik de vervolgkeuzelijst om aan de lijst met categorieën toe te voegen die als prioriteit worden aangemerkt. Klik op de X naast de categorienamen om deze te verwijderen.

### Waarschuwingen {#alerts}

Er worden enkele seconden waarschuwingen weergegeven in de rechterbovenhoek van het venster. Gebruik de **sectie van Alarm** om te bepalen voor welke berichten u alarm ontvangt.

![ alarm van het Bericht ](assets/notifications-alerts.png)

U kunt het gedrag van de waarschuwingen definiëren.

* **toon alarm voor** - bepaalt de soorten berichten die alarm teweegbrengen
* **Alarm zou op het scherm moeten blijven tot ik hen** ontvang - Controles als het alarm zou moeten voortbestaan tenzij u hen actief ontslaat
* **Duur** - bepaalt hoe lang het alarm op het scherm zou moeten blijven als u niet hebt gekozen dat zij op het scherm zouden moeten blijven.

### E-mails {#emails}

Meldingen zijn beschikbaar in de webgebruikersinterface voor alle Adobe [!UICONTROL Experience Cloud] -oplossingen. U kunt voor deze berichten ook kiezen om door e-mail in de **E-mail** sectie worden verzonden.

![ E-mails van het Bericht ](assets/notifications-emails.png)

Standaard worden geen e-mails verzonden. U kunt e-mails ontvangen als:

* Meteen
* Dagelijks
* Wekelijks

Wanneer **Onmiddellijke berichten** wordt gekozen, worden de e-mails verzonden onmiddellijk voor elk bericht. Voor **Dagelijkse samenvatting** en **Weekse samenvatting** kunt u kiezen wanneer uw dagelijkse samenvatting wordt verzonden en op welke dag en wanneer uw wekelijkse samenvatting wordt verzonden.