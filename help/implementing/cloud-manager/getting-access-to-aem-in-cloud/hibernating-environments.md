---
title: Hibernate en de-Sluimerige zandbakmilieu's
description: Leer hoe de omgevingen van een sandboxprogramma automatisch overschakelen op een hibernatiemodus en hoe u deze kunt dehiberneren.
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 169de7971fba829b0d43e64d50a356439b6e57ca
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---


# Hibernate en de-Sluimerige zandbakmilieu&#39;s {#hibernating-introduction}

De omgevingen van een sandboxprogramma voeren een slaapstand in als er gedurende acht uur geen activiteit wordt gedetecteerd. Hibernatie is uniek in sandboxprogrammaomgevingen. Productieprogrammaomgevingen kunnen niet worden gehiberneerd.

## Sluimerstand {#hibernation-introduction}

Sluimerstand kan automatisch of handmatig plaatsvinden.

* **Automatisch** - De milieu&#39;s van het Sandbox programma worden automatisch gehiberneerd na acht uren van inactiviteit. Inactiviteit wordt gedefinieerd als het ontbreken van verzoeken aan de auteur, voorproef, en publicatieservices.
* **Handboek** - als gebruiker kunt u een milieu van het zandbakprogramma manueel hiberneren. Dit is niet verplicht, omdat er automatisch sprake is van een sluimerstand, zoals eerder beschreven.

Het kan een paar minuten duren voordat de slaapstand wordt geactiveerd in sandboxprogrammaomgevingen. De gegevens blijven behouden tijdens de winterslaap.

### Een sandboxprogrammaomgeving handmatig tuineren {#using-manual-hibernation}

U kunt uw sandboxprogramma handmatig via de Developer Console herbergen. Alle gebruikers van Cloud Manager hebben toegang tot de Developer Console voor een sandboxprogramma.

**om een milieu van het zandbakprogramma manueel te hiberneren:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, klik a *zandbakprogramma* dat u wilt hiberneren om zijn details te tonen.

1. Op de **kaart van Milieu&#39;s**, klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en klik **Developer Console**.

   * Zie [&#x200B; Toegang hebbend tot Developer Console &#x200B;](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) voor extra details over Developer Console.

   ![&#x200B; het menuoptie van Developer Console &#x200B;](/help/implementing/cloud-manager/assets/developer-console-menu-option.png)

1. Op de **Developer Console** pagina, klik **Sluimerstand**.

<!-- UPDATE THESE SCREENSHOTS WHEN NEW AEM DEVELOPER CONSOLE UI IS RELEASED. AS OF OCTOBER 14, 2024, NEW UI IS STILL IN PRIVATE BETA -->

![&#x200B; knoop van de Slaapsteen &#x200B;](assets/hibernate-1.png)

1. Klik **Sluimerstand** om de stap te bevestigen.

   ![&#x200B; Bevestig hibernatie &#x200B;](assets/hibernate-2.png)

Wanneer de hibernatie succesvol is, ziet u het volledige bericht van het hibernatieproces voor uw milieu in het **Developer Console** scherm.

![&#x200B; Bevestiging van de Slaapstand &#x200B;](assets/hibernate-4.png)

In Developer Console, klik de **verbinding van Milieu&#39;s** in de broodkruimels boven de **Peul** drop-down lijst aan meningsmilieu&#39;s beschikbaar voor hibernatie.

![&#x200B; Lijst van milieu&#39;s aan hibernate &#x200B;](assets/hibernate-1b.png)

## Een sandboxprogramma handmatig dehiberneren vanuit de Developer Console {#de-hibernation-introduction}

U kunt uw sandboxprogramma handmatig via de Developer Console herbergen.

>[!IMPORTANT]
>
>Een gebruiker met de rol van de a **Ontwikkelaar** kan een milieu van het zandbakprogramma ontruimen-onderbreken.

**om een zandbakprogramma van Developer Console manueel te ontruimen-te ontruimen:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, klik het programma u wilt dehibernate om zijn details te tonen.

1. Op de **kaart van Milieu&#39;s**, klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en klik **Developer Console**.

   * Zie [&#x200B; Toegang hebbend tot Developer Console &#x200B;](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) voor extra details over Developer Console.

1. Klik **de-hibernate**.

   ![&#x200B; De-hibernate knoop &#x200B;](assets/de-hibernation-img1.png)

1. Klik **de-Sluimerstand** om de stap te bevestigen.

   ![&#x200B; bevestigt de-hibernatie &#x200B;](assets/de-hibernation-img2.png)

1. U ontvangt een melding dat het dehibernatieproces is gestart en met de voortgang is bijgewerkt.

   ![&#x200B; bericht van de de vooruitgangsvooruitgang van de Slaapstand &#x200B;](assets/de-hibernation-img3.png)

1. Zodra het proces is voltooid, is de sandboxprogrammaomgeving weer actief.

   ![&#x200B; De-hibernatie voltooide &#x200B;](assets/de-hibernation-img4.png)

In Developer Console, klik de **verbinding van Milieu&#39;s** in de broodkruimels boven de **Peul** drop-down lijst aan toegangsomgevingen beschikbaar voor de-hibernatie.

![&#x200B; Lijst van hibernated pods &#x200B;](assets/de-hibernate-1b.png)

### Machtigingen om de-hibernate te verwijderen {#permissions-de-hibernate}

Om het even welke gebruiker met een productprofiel dat hen toegang tot AEM as a Cloud Service geeft zou tot **Developer Console** moeten kunnen toegang hebben, toestaand hen om het milieu te ontruimen-hiberneren.

## Toegang tot een gehiberde omgeving {#accessing-hibernated-environment}

Wanneer een gebruiker een browser vraagt aan de auteur, voorproef, of publicatieservice van een gehiberneerde milieu, ontmoeten zij een het landen pagina. Deze pagina geeft uitleg over de status van de omgeving met een hibernatie en bevat een koppeling naar de Developer Console voor het uit de vaart nemen van de omgeving.

![&#x200B; Gesamberneerde dienst die pagina &#x200B;](assets/de-hibernation-img5.png) landen

## Implementaties en AEM-updates {#deployments-updates}

In gesluimerde omgevingen kunnen nog implementaties en handmatige AEM-upgrades worden uitgevoerd.

* Een gebruiker kan een pijpleiding gebruiken om douanecode aan gehiberneerde milieu&#39;s op te stellen. Het milieu blijft gehiberneerd en de nieuwe code verschijnt in het milieu zodra het wordt ontruimd.

* AEM-upgrades kunnen worden toegepast op gehiberde omgevingen en kunnen handmatig worden geactiveerd vanuit Cloud Manager. Het milieu blijft gehiberneerd en de nieuwe introductie verschijnt in het milieu als de stof eenmaal is gedehiberneerd.

## Sluimerstand en verwijdering {#hibernation-deletion}

* De omgevingen in een sandboxprogramma worden na acht uur inactiviteit automatisch genummerd.
   * Inactiviteit wordt gedefinieerd als het ontbreken van verzoeken aan de auteur, voorproef, en publicatieservices.
   * Zodra hibernated, kunnen zij [&#x200B; manueel worden ontruimd-hibernated &#x200B;](#de-hibernation-introduction).
* Sandboxprogramma&#39;s worden verwijderd na zes maanden van continuhibernatiemodus, waarna ze opnieuw kunnen worden gemaakt.

>[!NOTE]
>
>Alleen sandboxomgevingen worden automatisch verwijderd na zes maanden doorlopende hibernatie. Het sandboxprogramma met de bijbehorende opslagplaats en code blijft behouden.
