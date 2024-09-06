---
title: Sluiende en ontsmette zandbakomgevingen
description: Leer hoe omgevingen van een sandboxprogramma automatisch overschakelen op een hibernatiemodus en hoe u deze kunt deorganiseren.
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# Sluimerende en Sluimerende zandbakomgevingen {#hibernating-introduction}

De omgevingen van een sandboxprogramma gaan in op een slaapstand als er gedurende acht uur geen activiteit wordt gedetecteerd. De slaapstand is uniek in sandboxprogrammaomgevingen. In productieprogrammaomgevingen vindt geen hiberatie plaats.

## Sluimerstand {#hibernation-introduction}

Sluimerstand kan automatisch of handmatig plaatsvinden.

* **Automatisch** - De milieu&#39;s van het Sandbox programma worden automatisch gehiberneerd na acht uren van inactiviteit. Inactiviteit wordt gedefinieerd als het ontvangen van aanvragen door de auteurservice of door voorvertonings- of publicatieservices.
* **Handboek** - als gebruiker kunt u een milieu van het zandbakprogramma manueel hiberneren. Dit is niet verplicht, aangezien de herberging automatisch plaatsvindt, zoals eerder beschreven.

Het kan een paar minuten duren voordat de slaapstand wordt geactiveerd in sandboxprogrammaomgevingen. De gegevens blijven behouden tijdens de winterslaap.

### Handmatige slaapstand gebruiken {#using-manual-hibernation}

U kunt uw sandboxprogramma handmatig via de Developer Console herbergen. Alle gebruikers van Cloud Manager hebben toegang tot Developer Console voor een sandboxprogramma.

Voer de volgende stappen uit om de omgevingen van uw sandboxprogramma handmatig te hiberneren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, tik of klik het programma u wilt hiberneren om zijn details te tonen.

1. Op de **kaart van Milieu&#39;s**, klik de elliptische knoop en selecteer **Developer Console**.

   * Zie [ Toegang hebbend tot Developer Console ](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) voor extra details over Developer Console.

   ![ het menuoptie van Developer Console ](assets/developer-console-menu-option.png)

1. In Developer Console, klik **Sluimerstand**.

   ![ knoop van de Slaapsteen ](assets/hibernate-1.png)

1. Klik **Sluimerstand** om de stap te bevestigen.

   ![ Bevestig hibernatie ](assets/hibernate-2.png)

Wanneer de hibernatie succesvol is, ziet u het volledige bericht van het hibernatieproces voor uw milieu in het **Developer Console** scherm.

![ Bevestiging van de Slaapstand ](assets/hibernate-4.png)

In Developer Console kunt u ook de **Milieu** verbinding in de broodkruimels boven de **Peul** drop-down lijst voor een lijst van milieu&#39;s aan hibernate klikken.

![ Lijst van milieu&#39;s aan hibernate ](assets/hibernate-1b.png)

## De-Hibernatie {#de-hibernation-introduction}

U kunt uw Sandbox-programma handmatig van de Developer Console voorzien.

>[!IMPORTANT]
>
>Een gebruiker met de rol van de a **Ontwikkelaar** kan een milieu van het zandbakprogramma ontruimen-onderbreken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, ontruim of klik het programma u zijn details wilt tonen.

1. Op de **kaart van Milieu&#39;s**, klik de elliptische knoop en selecteer **Developer Console**.

   * Zie [ Toegang hebbend tot Developer Console ](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) voor extra details over Developer Console.

1. Klik **de-hibernate**.

   ![ De-hibernate knoop ](assets/de-hibernation-img1.png)

1. Klik **de-Sluimerstand** om de stap te bevestigen.

   ![ bevestigt de-hibernatie ](assets/de-hibernation-img2.png)

1. U ontvangt een melding dat het dehibernatieproces is gestart en met de voortgang is bijgewerkt.

   ![ bericht van de de vooruitgangsvooruitgang van de Slaapstand ](assets/de-hibernation-img3.png)

1. Zodra het proces is voltooid, is de sandboxprogrammaomgeving weer actief.

   ![ De-hibernatie voltooide ](assets/de-hibernation-img4.png)


In Developer Console kunt u ook de **Milieu** verbinding in de broodkruimels boven de **Peul** drop-down lijst voor een lijst van milieu&#39;s aan dehibernate klikken.

![ Lijst van hibernated pods ](assets/de-hibernate-1b.png)

### Machtigingen om de-Slaapstand te verwijderen {#permissions-de-hibernate}

Om het even welke gebruiker met een productprofiel dat hen toegang tot AEM as a Cloud Service geeft zou tot **Developer Console** moeten kunnen toegang hebben, toestaand hen om het milieu te ontruimen-hiberneren.

## Een gedownloade omgeving openen {#accessing-hibernated-environment}

Wanneer de gebruiker om het even welke browser verzoeken tegen de auteur, voorproef, of publicatieservice van een gehiberneerde milieu, zal de gebruiker een landende pagina ontmoeten die de gehiberneerde status van het milieu samen met een verbinding aan Developer Console beschrijft waar de dienst kan worden ontruimd-hibernated.

![ Gesamberneerde dienst die pagina ](assets/de-hibernation-img5.png) landen

## Implementaties en AEM updates {#deployments-updates}

In gesluimerde omgevingen zijn implementaties en handmatige AEM nog steeds mogelijk.

* Een gebruiker kan een pijpleiding gebruiken om douanecode aan gehiberneerde milieu&#39;s op te stellen. Het milieu zal gehiberneerd blijven en de nieuwe code zal in het milieu verschijnen zodra ontruimd-hibernated.

* AEM upgrades kunnen worden toegepast op gehiberde omgevingen en kunnen handmatig worden geactiveerd vanuit Cloud Manager. Het milieu zal gehiberneerd blijven en de nieuwe introductie zal in het milieu verschijnen zodra het wordt gedehiberneerd.

## Sluimerstand en verwijdering {#hibernation-deletion}

* De omgevingen in een sandboxprogramma worden na acht uur inactiviteit automatisch genummerd.
   * Inactiviteit wordt gedefinieerd als het ontvangen van aanvragen door de auteurservice of door voorvertonings- of publicatieservices.
   * Zodra hibernated, kunnen zij [ manueel worden ontruimd-hibernated ].(#de-hibernation-Introduction)
* Sandboxprogramma&#39;s worden verwijderd na zes maanden van continuhibernatiemodus, waarna ze opnieuw kunnen worden gemaakt.

>[!NOTE]
>
>Alleen sandboxomgevingen worden automatisch verwijderd na zes maanden doorlopende hibernatie. Het sandboxprogramma met de bijbehorende opslagplaats en code blijft behouden.
