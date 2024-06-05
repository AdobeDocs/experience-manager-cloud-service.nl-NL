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

[!UICONTROL Cloud Manager] verzendt u berichten wanneer een productiepijplijn (met succes of met succes), bij het begin van een productieleiding begint en voltooit.

Deze meldingen worden verzonden via de [!UICONTROL Experience Cloud] meldingssysteem voor gebruikers in de **Zakelijke eigenaar**, **Programmabeheerder**, en **Implementatiebeheer** rollen.

De meldingen worden weergegeven in een zijbalk in [!UICONTROL Cloud Manager] en gedurende de gehele Adobe [!UICONTROL Experience Cloud]. Het belpictogram in de koptekst is gemarkeerd wanneer u nieuwe meldingen hebt.

![Meldingspictogram](assets/notifications-bell-badged.png)

Klik op het belpictogram om de zijbalk te openen en de meldingen weer te geven. De **Meldingen** in de zijbalk worden de meest recente meldingen weergegeven, zoals bevestigingen voor de implementatie. Meldingen betreffen uw omgeving.

![Zijbalk voor meldingen](assets/notifications-activities.png)

De **Aankondigingen** bevat productmededelingen voor Adoben. Aankondigingen betreffen het product.

![Zijbalk voor meldingen](assets/notificaitons-announcements.png)

Klik op een melding of aankondiging om de details weer te geven. De berichten verbonden aan activiteiten zoals pijpleidingsplaatsingen nemen u aan het detail van die activiteit zoals het venster van de pijpleidingsuitvoering.

Klik op de knop **Alles weergeven** onder in het deelvenster om alle aankondigingen in uw Postvak IN weer te geven.

Klik op de knop **Alles markeren als gelezen** onder aan het deelvenster kunt u alle ongelezen meldingen markeren als gelezen en de badge voor het belpictogram wissen.

## Configuratie van melding {#configuration}

U kunt aanpassen hoe u meldingen ontvangt en welke meldingen u ontvangt.

Klik op het tandwielpictogram boven aan de zijbalk met meldingen.

![Pictogram Meldingsinstellingen](assets/notifications-configuration.png)

Hierdoor wordt het **Voorkeuren voor Experience Cloud** , waarin u uw berichtabonnementen kunt definiëren en kunt aangeven hoe u uw meldingen ontvangt.

### Abonnementen {#subscriptions}

In abonnementen wordt gedefinieerd voor welke producten u meldingen ontvangt en welke meldingen.

![Abonnementen op meldingen](assets/notifications-subscriptions.png)

Standaard ontvangt u alle meldingen voor alle producten, zowel in de toepassing als via e-mail. Klik op het pictogram naast een productnaam om de gedetailleerde opties weer te geven en de typen meldingen te definiëren die u voor dat product ontvangt. U kunt ook de opties op productniveau in- of uitschakelen om alle opties voor het product in of uit te schakelen.

![Aanpassing van berichtabonnement](assets/notifications-subscriptions-customize.png)

### Prioriteit {#priority}

Prioritaire waarschuwingen worden gemarkeerd met een **HOOG** -tag en kan worden geconfigureerd om uitsluitend als waarschuwing te worden ontvangen. In de **Prioriteit** kunt u opgeven welke categorieën als prioritaire meldingen worden beschouwd.

![Meldingsprioriteit](assets/notifications-priority.png)

Gebruik de vervolgkeuzelijst om aan de lijst met categorieën toe te voegen die als prioriteit worden aangemerkt. Klik op de X naast de categorienamen om deze te verwijderen.

### Waarschuwingen {#alerts}

Er worden enkele seconden waarschuwingen weergegeven in de rechterbovenhoek van het venster. Gebruik de **Waarschuwingen** in deze sectie om te definiëren voor welke meldingen u waarschuwingen ontvangt.

![Waarschuwingen](assets/notifications-alerts.png)

U kunt het gedrag van de waarschuwingen definiëren.

* **Waarschuwingen weergeven voor** - Definieert de typen meldingen die waarschuwingen activeren
* **Waarschuwingen moeten op het scherm blijven staan totdat ik ze afsluit** - Controleert of de waarschuwingen zouden moeten voortbestaan tenzij u hen actief ontslaat
* **Duur** - Hiermee bepaalt u hoe lang de waarschuwing op het scherm moet blijven als u niet hebt gekozen dat deze op het scherm moet blijven.

### E-mails {#emails}

Meldingen zijn beschikbaar in de webgebruikersinterface in de hele Adobe [!UICONTROL Experience Cloud] oplossingen. U kunt ervoor kiezen deze meldingen via e-mail te verzenden in het dialoogvenster **E-mails** sectie.

![E-mailberichten](assets/notifications-emails.png)

Standaard worden geen e-mails verzonden. U kunt e-mails ontvangen als:

* Meteen
* Dagelijks
* Wekelijks

Wanneer **Directe meldingen** wordt gekozen, worden e-mails onmiddellijk verzonden voor elke melding. Voor **Dagelijks overzicht** en **Wekelijks overzicht** U kunt kiezen wanneer uw dagelijkse samenvatting wordt verzonden en op welke dag en wanneer uw wekelijkse samenvatting wordt verzonden.