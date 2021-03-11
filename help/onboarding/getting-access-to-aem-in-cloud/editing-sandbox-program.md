---
title: 'Een Sandbox-programma bewerken '
description: 'Een Sandbox-programma bewerken '
translation-type: tm+mt
source-git-commit: 751f611ecccc39ef4650a1c7a9941655a6b2aedd
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Een sandboxprogramma bewerken {#create-sandbox-program}

Gebruikers met de vereiste machtigingen kunnen nu een productieprogramma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:

* Voeg de oplossing van Plaatsen aan een bestaand programma met Activa (of vice versa) toe.
* Sites (of Middelen) verwijderen uit een bestaand programma met zowel Sites als Middelen.
* Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

   >[!NOTE]
   >Een gebruiker in de rol Bedrijfs van de Eigenaar moet worden het programma geopend om het programma met succes uit te geven.

Voer de onderstaande stappen uit om een Sandbox-programma te bewerken:

1. Navigeer naar de pagina **Program** bewerken van de pagina *Overview* van Cloud Manager.

1. Op de pagina **Programma bewerken** worden twee tabbladen (Algemeen en Oplossingen) weergegeven voor zowel productie- als sandboxprogramma&#39;s.
   ![](assets/edit-program.png)


## Overwegingen bij het bewerken van een programma {#considerations-editing}

Enkele overwegingen moeten worden herzien tijdens het bewerken van een programma:

* Er moet ten minste één oplossing zijn geselecteerd voor een programma dat de selectie van alle oplossingen tijdens de workflow van het programma Bewerken mogelijk maakt.

* Als u op de knop **Opslaan** klikt en de geselecteerde oplossingen zijn gewijzigd, worden de updates van de oplossing voor omgevingen van kracht na de volgende implementatie.