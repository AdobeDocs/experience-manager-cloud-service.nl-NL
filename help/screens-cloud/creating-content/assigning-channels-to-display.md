---
title: Kanaal toewijzen aan een weergave in Screens as a Cloud Service
description: Op deze pagina wordt beschreven hoe u een kanaal toewijst aan een weergave in Screens as a Cloud Service.
exl-id: ba001c18-7b05-4ae2-aa7f-9ebb320fedd0
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Kanaal toewijzen aan een weergave in Screens as a Cloud Service {#assign-channel-displays-screens-cloud}

Nadat de projectopstelling volledig is, moet u het kanaal aan een vertoning toewijzen om de inhoud te bekijken.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe u een kanaal aan een vertoning kunt toewijzen, zodra uw vertoning klaar is en u inhoud aan uw kanaal hebt toegevoegd en het gepubliceerd. Na het lezen, zou u moeten kunnen begrijpen hoe te om een kanaal aan een vertoning van de Leverancier van de Diensten van Screens toe te wijzen.

## Vereisten {#prerequisites}

Voordat u de onderstaande stappen uitvoert om een kanaal toe te wijzen aan een weergave, moet u klaar zijn met het leren:

* Weergaven maken en beheren
* Kanalen maken en beheren

## Stappen om een Kanaal aan een Vertoning toe te wijzen {#assign-channel-to-display}

Voer de onderstaande stappen uit om een kanaal toe te wijzen aan een weergave:

1. Navigeer aan de Leverancier van de Diensten van Screens en selecteer **Vertoningen** van het linkernavigatievenster.

1. Klik **toewijzen Kanaal** aan de vertoning.

   ![afbeelding](/help/screens-cloud/assets/display/assignchannel-1.png)

1. Vul de volgende gebieden van **toewijzen een kanaal** dialoogdoos.

   ![afbeelding](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. Selecteer de kanaalnaam in de vervolgkeuzelijst.
   1. Kies de prioriteit.

      >[!NOTE]
      >Prioriteit wordt gebruikt om de toewijzingen te bestellen als meerdere toewijzingen voldoen aan de afspeelcriteria. De waarde met de hoogste waarde heeft altijd voorrang op lagere waarden. Bijvoorbeeld, als er twee kanalen A en B zijn. A heeft een prioriteit van 1 en B heeft een prioriteit van 2, dan wordt kanaal B getoond, aangezien het een hogere prioriteit dan A heeft.

   1. Selecteer de begindatum en einddatum van **Activering**.

1. Klik op **+ Herhaling toevoegen** om een herhalingsschema voor uw kanaal toe te voegen.

   ![afbeelding](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >U kunt veelvoudige terugkomende programma&#39;s aan uw kanaal toevoegen. De programma&#39;s van de herhaling introduceren DayParting die u een globaal programma met veelvoudige kanalen laat plaatsen die op specifieke tijden van de dag lopen, en hergebruik die opstelling voor al uw vertoningen in één keer.

   U kunt de volgende opties instellen:

   * **Naam**: Titel van uw herhalingsprogramma.
   * **Herhaal**: Kies of de programma&#39;s Dagelijks, Wekelijks, Maandelijks, of Jaarlijks lopen.
   * **Begin**: De begintijd voor uw programma.
   * **Eind**: De beëindigende tijd voor uw programma. U kunt de waarde instellen op tijd of duur.
   * **Tijd**: Het programma beëindigt bij een gespecificeerde tijd.
   * **Duur**: De programmalooppas voor een bepaalde duur van tijd in uren of notulen.

1. Klik **creëren**. U kunt zien dat een kanaal voor die vertoning, zoals aangetoond in het hieronder cijfer wordt toegewezen.

   ![afbeelding](/help/screens-cloud/assets/display/assignchannel-3.png)


## Volgende functies {#whats-next}

Nu, dat u het kanaal aan een vertoning hebt toegewezen, zou u uw as a Cloud Service reis van Screens moeten voortzetten door het document [&#x200B; te herzien Installing en het Vormen de Speler van Screens voor AEM as a Cloud Service &#x200B;](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md).
