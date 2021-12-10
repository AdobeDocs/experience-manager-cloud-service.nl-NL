---
title: Bekende problemen en beperkingen
description: Bekende problemen en beperkingen van  [!DNL AEM Forms] as a Cloud Service omgeving
contentOwner: khsingh
role: User, Developer
level: Intermediate
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Bekende problemen en beperkingen {#known-issues-and-limitations}

Voordat u begint met [!DNL AEM Forms] as a Cloud Service, herzie de volgende bekende kwesties en de beperkingen:

## Bekende problemen {#known-issues}

* Voeg geen test toe en voer geen test uit die een Aangepast Formulier van een publicatie-instantie naar een AEM Werkstroom verzendt die op een instantie van de Auteur loopt tot verder bericht.

* Wanneer u een adaptief formulier importeert dat gebruikmaakt van een sjabloon met de **[!UICONTROL Save]** de **[!UICONTROL Save]** verschijnt nog steeds in het adaptieve formulier nadat het uit de bijbehorende sjabloon is verwijderd. Verwijder de **[!UICONTROL Save]** van uw Adaptive Forms voordat u deze publiceert. Houd de releaseopmerkingen in de gaten voor de beschikbaarheid van de Forms Portal en de conceptfunctie Opslaan als om de knop te herstellen en te gebruiken.

* De **[!UICONTROL Set variable]** stap van AEM Workflows ondersteunt geen variabelen van het type arraylijst. U kunt de processtap gebruiken om variabelen van het type arraylijst in te stellen.

* Wanneer u een adaptief formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 bytes ontvangen. De kwestie komt met tussenpozen en slechts bij het gebruiken van synchrone voorlegging voor. Dit is een [bekende kwestie](https://feedbackassistant.apple.com/feedback/9117687) in Apple iOS.

* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan het andere uiteinde een bestand van 0 bytes ontvangen. Dit is een bekend probleem in Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)


## Beperkingen {#limitations}

* Ondersteuning voor adaptieve Forms op basis van XFA is niet beschikbaar in de verpakking. Als u van plan bent om op XFA-Gebaseerde AanpassingsForms te gebruiken, contacteer de Steun van de Adobe met details van uw gebruiksgeval en specifieke vereisten.

