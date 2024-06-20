---
title: Kanaal toewijzen aan een as a Cloud Service weergave in schermen
description: Op deze pagina wordt beschreven hoe u een kanaal toewijst aan een weergave in as a Cloud Service schermen.
exl-id: ba001c18-7b05-4ae2-aa7f-9ebb320fedd0
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Kanaal toewijzen aan een as a Cloud Service weergave in schermen {#assign-channel-displays-screens-cloud}

Nadat de projectopstelling volledig is, moet u het kanaal aan een vertoning toewijzen om de inhoud te bekijken.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe u een kanaal aan een vertoning kunt toewijzen, zodra uw vertoning klaar is en u inhoud aan uw kanaal hebt toegevoegd en het gepubliceerd. Na het lezen, zou u moeten kunnen begrijpen hoe te om een kanaal aan een vertoning van de Leverancier van de Diensten van het Scherm toe te wijzen.

## Vereisten {#prerequisites}

Voordat u de onderstaande stappen uitvoert om een kanaal toe te wijzen aan een weergave, moet u klaar zijn met het leren:

* Weergaven maken en beheren
* Kanalen maken en beheren

## Stappen om een Kanaal aan een Vertoning toe te wijzen {#assign-channel-to-display}

Voer de onderstaande stappen uit om een kanaal toe te wijzen aan een weergave:

1. Navigeer naar de Serviceverlener voor schermen en selecteer **Weergaven** in het navigatievenster aan de linkerkant.

1. Klikken **Kanaal toewijzen** op het scherm.

   ![afbeelding](/help/screens-cloud/assets/display/assignchannel-1.png)

1. De volgende velden vullen vanuit **Een kanaal toewijzen** in.

   ![afbeelding](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. Selecteer de kanaalnaam in de vervolgkeuzelijst.
   1. Kies de prioriteit.

      >[!NOTE]
      >Prioriteit wordt gebruikt om de toewijzingen te bestellen als meerdere toewijzingen voldoen aan de afspeelcriteria. De waarde met de hoogste waarde heeft altijd voorrang op lagere waarden. Bijvoorbeeld, als er twee kanalen A en B zijn. A heeft een prioriteit van 1 en B heeft een prioriteit van 2, dan wordt kanaal B getoond, aangezien het een hogere prioriteit dan A heeft.

   1. Selecteer de begin- en einddatum van **Activering**.

1. Klikken **+ Herhaling toevoegen** om een terugkerend programma voor uw kanaal toe te voegen.

   ![afbeelding](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >U kunt veelvoudige terugkomende programma&#39;s aan uw kanaal toevoegen. De programma&#39;s van de herhaling introduceren DayParting die u een globaal programma met veelvoudige kanalen laat plaatsen die op specifieke tijden van de dag lopen, en hergebruik die opstelling voor al uw vertoningen in één keer.

   U kunt de volgende opties instellen:

   * **Naam**: Titel van uw terugkerend schema.
   * **Herhalen**: Kies of de planning Dagelijks, Wekelijks, Maandelijks, of Jaarlijks loopt.
   * **Start**: De begintijd voor uw schema.
   * **Einde**: De eindtijd voor uw schema. U kunt de waarde instellen op tijd of duur.
   * **Tijd**: Het schema eindigt op een bepaald tijdstip.
   * **Duur**: De planning loopt gedurende een bepaalde tijdsduur in uren of minuten.

1. Klikken **Maken**. U kunt zien dat een kanaal voor die vertoning, zoals aangetoond in het hieronder cijfer wordt toegewezen.

   ![afbeelding](/help/screens-cloud/assets/display/assignchannel-3.png)


## Volgende functies {#whats-next}

Nu u het kanaal aan een vertoning hebt toegewezen, zou u uw as a Cloud Service reis van de Schermen door het document opnieuw te bekijken moeten voortzetten [Schermspeler voor AEM as a Cloud Service installeren en configureren](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md).
