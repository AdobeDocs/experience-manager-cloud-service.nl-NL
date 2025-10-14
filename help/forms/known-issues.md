---
title: Wat zijn de bekende problemen en beperkingen van de as a Cloud Service omgeving van AEM Forms?
description: Bekende kwesties en beperkingen van  [!DNL AEM Forms]  as a Cloud Service milieu.
contentOwner: khsingh
role: Admin, Developer, User
feature: Adaptive Forms
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Bekende problemen en beperkingen {#known-issues-and-limitations}

Voordat u [!DNL AEM Forms] as a Cloud Service gaat gebruiken, moet u de volgende bekende problemen en beperkingen controleren:

## Bekende problemen {#known-issues}

* Voeg geen test toe en voer geen test uit die een Aangepast Formulier van een publicatie-instantie naar een AEM Werkstroom verzendt die op een instantie van de Auteur loopt tot verder bericht.

* Wanneer u een adaptief formulier importeert dat gebruikmaakt van een sjabloon met de knop **[!UICONTROL Save]** , wordt de knop **[!UICONTROL Save]** nog steeds weergegeven in het adaptieve formulier nadat deze is verwijderd uit de bijbehorende sjabloon. Verwijder de knop **[!UICONTROL Save]** uit uw Adaptieve Forms voordat u deze publiceert. Houd de releaseopmerkingen in de gaten voor de beschikbaarheid van de Forms Portal en de conceptfunctie Opslaan als om de knop te herstellen en te gebruiken.

* De **[!UICONTROL Set variable]** -stap van AEM Workflows ondersteunt geen variabelen van het type arraylijst. U kunt de processtap gebruiken om variabelen van het type arraylijst in te stellen.

* Wanneer u een adaptief formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 bytes ontvangen. De kwestie komt met tussenpozen en slechts bij het gebruiken van synchrone voorlegging voor. Dit is a [&#x200B; gekende kwestie &#x200B;](https://feedbackassistant.apple.com/feedback/9117687) in Apple iOS.

* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan het andere uiteinde een bestand van 0 bytes ontvangen. Dit is een bekend probleem in Apple iOS. [&#x200B; FB9117687 &#x200B;](https://feedbackassistant.apple.com/feedback/9117687)

* AEM Forms as a Cloud Service genereert geen miniaturen voor XDP- en JSON-schemabestanden. De service geeft standaardpictogrammen weer in plaats van miniaturen.

  ![&#x200B; Bekende kwestie van de Miniatuur van Forms &#x200B;](/help/forms/assets/forms-tumbnail-known-issue.png)

* Wanneer u een schema met herhaalbare elementen gebruikt om een op kerncomponenten gebaseerde adaptieve vorm te maken, werkt de optie om herhaalbare elementen uit gegevensmodelstructuur te slepen en neer te zetten in de Adaptieve Forms Editor niet.

## Beperkingen {#limitations}

* Ondersteuning voor adaptieve Forms op basis van XFA is niet beschikbaar in de verpakking. Als u van plan bent om op XFA-Gebaseerde Aangepaste Forms te gebruiken, contacteer de Steun van de Adobe met details van uw gebruiksgeval en specifieke vereisten.

