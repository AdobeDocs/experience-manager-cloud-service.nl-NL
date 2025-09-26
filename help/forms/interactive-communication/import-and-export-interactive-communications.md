---
title: Interactieve communicatie importeren en exporteren
description: De invoer en de Uitvoer Interactieve Communicatie laat gebruikers toe om, mededelingen over milieu's foutloos te migreren, opnieuw te gebruiken en te beheren.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Interactieve communicatie importeren en exporteren

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

Met de functie Importeren en exporteren in Interactieve communicatie (IC) kunnen gebruikers naadloos migreren, hergebruiken en communicatie beheren in verschillende omgevingen. Het staat u toe om een Interactieve Communicatie (IC) samen met zijn bijbehorende fragmenten en gegevensmodellen van één milieu uit te voeren en het in een andere in te voeren, die consistentie verzekeren en dubbel werk tijdens plaatsing verminderen.

## Belangrijkste voordelen

- Vereenvoudigt migratie van ICs over milieu&#39;s.
- Hiermee blijven fragmenten, gegevensmodellen en afhankelijkheden behouden.
- Vermindert inspanning in het ontspannen van ICs over projecten.

## Interactieve communicatie importeren en exporteren

Creeer een Interactieve Communicatie (IC) in één milieu en gebruik het in een andere door het uit te voeren en in te voeren door het onder stappen te volgen:

+++&#x200B;1. Interactieve communicatie exporteren

1.1. Selecteer a [ gecreeerd Interactieve Communicatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/interactive-communication/create-interactive-communication) (IC).
1.2. Klik de **optie van de Download** om het als dossier van het PIT uit te voeren.
1.3. Het gedownloade dossier van het PIT omvat IC samen met zijn geselecteerde **malplaatje**, **fragmenten**, en **gegevensmodel**.

![ vind IC Docu ](/help/forms/interactive-communication/assets/downloadic.png)
+++

+++&#x200B;2. Interactieve communicatie importeren

2.1. Ga naar de doelomgeving.
2.2. Navigeer aan **Forms > Forms en de Documenten > creëren > Dossier uploadt**.
2.3. Upload het dossier van het PIT aan **invoer** IC.

![ vind IC Docu ](/help/forms/interactive-communication/assets/uploadfile.png)

2.4. Na het uploaden wordt het IC weergegeven samen met de bijbehorende fragmenten en gegevensmodel.

![ vind IC Docu ](/help/forms/interactive-communication/assets/importfragment.png)
+++

+++&#x200B;3. Fragment importeren en exporteren

3.1. Om uit te voeren, selecteer het vereiste fragment van **Forms > Forms en Documenten**, dan klik **Download** om het als dossier van het PIT uit te voeren.

3.2. Om in te voeren, ga naar het doelmilieu, navigeer aan Forms > Forms en de Documenten > creëren > **Dossier uploadt**, en upload het uitgevoerde dossier van het PIT.

Dit maakt het mogelijk fragmenten in verschillende omgevingen opnieuw te gebruiken, waardoor de consistentie van het ontwerp wordt gegarandeerd en dubbel werk wordt verminderd.
+++
