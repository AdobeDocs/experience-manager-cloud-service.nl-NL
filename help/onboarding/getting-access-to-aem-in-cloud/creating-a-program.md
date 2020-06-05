---
title: Een programma maken - Cloud Service
description: Een programma maken - Cloud Service
translation-type: tm+mt
source-git-commit: 02160a9fa713b3758698aa3330a5ccaef8b830fb
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Een programma maken {#create-a-program}

De cloud-native oplossing biedt de gebruiker de vereiste machtigingen en de mogelijkheid om een programma te maken op basis van een zelfservicemodel.

Een tovenaar van de programmaverwezenlijking zal de gebruiker vragen om details, afhankelijk van het doel van de gebruiker in het creëren van het programma binnen de grenzen van wat aan de specifieke klant of de organisatie beschikbaar is voor te leggen.

In het geval van eerste toegang tot de Manager van de Wolk of als geen programma&#39;s in de huurder bestaan, zal de gebruiker uw eerste scherm van het Programma **zien** creëren. Als de gebruiker *Esc* selecteert of uit de dialoogdoos klikt, toont het volgende scherm:

![](assets/create-program1.png)


## De wizard Programma maken gebruiken {#using-create-program-wizard}

Afhankelijk van het doel van de gebruiker bij het creëren van het programma binnen de grenzen van wat aan de specifieke klant/organisatie beschikbaar is, zal een tovenaar van de programmaverwezenlijking de gebruiker vragen om één of meerdere details voor te leggen.

![](assets/create-sandbox.png)

>[!NOTE]
>If a program already exists, then you will see **Add Program** on the top right of the landing page, as shown in the figure below.

![](assets/create-program-add.png)

## Sandboxprogramma&#39;s maken {#create-sandbox-program}

Voer de onderstaande stappen uit om een sandboxprogramma te maken:

1. Selecteer in de wizard Programma maken een **sandbox** instellen. Gebruiker verzendt de naam van het programma voordat u **Maken** selecteert.

   ![](assets/create-sandbox.png)

1. De gebruiker ziet de nieuwe sandbox-programmakaart op de bestemmingspagina en kan de muisaanwijzer boven de nieuwe sandbox plaatsen om het pictogram Cloud Manager te selecteren en naar de overzichtspagina van Cloud Manager te navigeren. De kaart informeert de gebruiker over de status van automatische installatie van het nieuwe sandboxprogramma. De gebruiker zal progressie zien.

   ![](assets/program-create-setupdemo2.png)

1. Nadat het programma is ingesteld en het project is gemaakt, heeft de gebruiker toegang tot de koppeling **Git** beheren, zoals in de onderstaande afbeelding wordt getoond:

   ![](assets/create-program4.png)

   >[!NOTE]
   >
   >Als u meer wilt weten over toegang tot en beheer van uw Git-opslagplaats via Self-Service Git-accountbeheer vanuit de interface van Cloud Manager, raadpleegt u [Toegang tot Git](/help/implementing/cloud-manager/accessing-git.md).


1. Zodra het ontwikkelmilieu wordt gecreeerd, kan de gebruiker tot verbinding **toegang hebben AEM** , zoals aangetoond in het hieronder cijfer:

   ![](assets/create-program-5.png)

1. Zodra de niet productiepijplijn die aan ontwikkeling opstelt volledig is, leidt de tovenaar de gebruiker aan of toegang tot AEM (op ontwikkeling) of code aan ontwikkelomgeving op te stellen:

   ![](assets/create-program-setup-deploy.png)

   >[!NOTE]
   >U kunt een programma ook bewerken, overschakelen of toevoegen via de overzichtspagina van Cloud Manager, zoals hieronder wordt getoond:

   ![](assets/create-program-a1.png)

## Een Sandbox-programma verwijderen {#delete-sandbox-program}

Een gebruiker van het Sandbox-programma in de rol van *bedrijfseigenaar* of *implementatiebeheerder* in Cloud Manager kan zijn productie- en werkgebiedomgeving verwijderen die is ingesteld via de interface van Cloud Manager.

>[!NOTE]
>Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

De verwijderoptie is beschikbaar op de bestemmingspagina, zoals hieronder wordt getoond:

![](assets/delete-sandbox1.png)

Of

Selecteer Programma **** verwijderen op de pagina *Overzicht* om uw Sandbox-programma te verwijderen.

![](assets/delete-sandbox2.png)


## Een regulier programma maken {#create-regular-program}

Een *regulier* programma is bedoeld voor een gebruiker die bekend is met AEM en Cloud Manager en klaar is om code te schrijven, te bouwen en te testen met als doel deze te implementeren in Production.

Voer de volgende stappen uit om een regulier programma te maken:

1. Selecteer **Opstelling voor Productie** in de Create tovenaar van het Programma om een regelmatig programma tot stand te brengen. De gebruiker kan de standaardprogrammanaam accepteren of deze bewerken voordat hij of zij **Doorgaan** selecteert.

   ![](assets/create-prod1.png)

1. De gebruiker zal oplossingen selecteren die in het programma in het scherm moeten worden opgenomen dat na het bovenstaande scherm zal worden voorgesteld.



   >[!NOTE]
   >
   >Het onderstaande scherm wordt alleen weergegeven voor het segment klanten die meerdere oplossingen hebben aangeschaft. Voor klanten die slechts één oplossing hebben aangeschaft, wordt het onderstaande scherm voor de selectie van de oplossing niet weergegeven.

   ![](assets/set-up-prod2.png)

1. Als u de oplossingen hebt geselecteerd, klikt u op **Maken**.

   ![](assets/set-up-prod3.png)

1. Zodra u de programmacode op de bestemmingspagina ziet, beweegt u de muisaanwijzer over het pictogram Cloud Manager om naar de pagina **Overzicht** van Cloud Manager te gaan.

   ![](assets/set-up-prod4.png)

1. De belangrijkste vraag-aan-actie kaart zal de gebruiker begeleiden om een milieu tot stand te brengen, een niet productiepijpleiding, en tenslotte een productiepijpleiding tot stand te brengen.
   ![](assets/set-up-prod5.png)


   >[!NOTE]
   >
   >A regular program does not have **Auto-setup** feature.





