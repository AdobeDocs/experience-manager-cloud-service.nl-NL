---
title: CI/CD Pipeline configureren - Cloud Services
description: CI/CD Pipeline configureren - Cloud Services
translation-type: tm+mt
source-git-commit: e9514d2ba625a7df8a8126f5b0ab74b975eeda51

---


# Het vormen van uw CI-CD Pijpleiding {#configure-ci-cd-pipeline}


## De stroom begrijpen {#understanding-the-flow}

U kunt uw pijpleiding van de **Stegel van Montages** van de Pijpleiding in de UI van de Manager [!UICONTROL van de] Wolk vormen.

De Manager van de Plaatsing is verantwoordelijk voor vestiging de pijpleiding. Als u dit doet, selecteert u eerst een vertakking in de **Git Repository**.

Om uw pijpleiding te vormen, moet de gebruiker:

* bepaal de trekker die de pijpleiding zal beginnen.
* de parameters voor de implementatie van de productie te definiëren.
* de testparameters voor de prestaties configureren.

## De pijplijn instellen {#setting-up-the-pipeline}

>[!CAUTION]
>
>De pijplijn kan niet worden ingesteld tot één programma volledig is gemaakt en de opslagplaats van Git heeft minstens één tak.

Voordat u begint met het implementeren van uw code, moet u de pijpleidinginstellingen configureren vanuit [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt de pijpleidingsmontages na aanvankelijke opstelling veranderen.

## Instellingen voor de pijplijn configureren vanuit [!UICONTROL Cloudinbeheer]{#configuring-the-pipeline-settings-from-cloud-manager}

Als u uw programma hebt ingesteld en minstens één omgeving hebt met [!UICONTROL Cloud Manager] UI, kunt u uw implementatiepijplijn instellen.

Voer de volgende stappen uit om het gedrag en de voorkeuren voor uw pijplijn te configureren:

1. Klik de Pijpleiding **van de** Opstelling aan opstelling en vorm uw pijpleiding.

   ![](assets/set-up-pipeline1.png)

1. De het schermvertoningen van de Pijpleiding van de **Opstelling** . Selecteer de vertakking en klik op **Volgende**.

   ![](assets/set-up-pipeline2.png)

1. Configureer uw implementatieopties.

   ![](assets/set-up-pipeline3.png)

   U kunt de trekker bepalen om de pijpleiding te beginnen:

   * **Handmatig** - de UI gebruikt manueel begint de pijpleiding.
   * **Bij de Veranderingen** van het Git - begint de pijpleiding CI/CD wanneer er toezeggingen aan de gevormde git tak worden toegevoegd. Zelfs als u deze optie selecteert, kunt u de pijpleiding altijd manueel beginnen.
   Tijdens pijpleidingsopstelling of geef uit, heeft de Manager van de Plaatsing de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitshates wordt ontmoet.

   Dit is handig voor klanten die meer geautomatiseerde processen willen. De beschikbare opties zijn:

   * **Telkens** vragen - Dit is de standaardinstelling en u moet handmatig ingrijpen bij elke belangrijke fout.
   * **Onmiddellijk** afbreken - Als deze optie is geselecteerd, wordt de pijplijn geannuleerd wanneer een belangrijke fout optreedt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
   * **Ga onmiddellijk** verder - als geselecteerd, zal de pijpleiding automatisch te werk wanneer een Belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.


1. Klik op **Volgende** om het tabblad **Testen** te openen en de testcriteria voor uw programma te definiëren.

   ![](assets/set-up-pipeline4.png)

1. Click **Save**. Op de pagina *Overzicht* wordt nu de **Programmakaart** implementeren weergegeven. Klik op de knop **Implementeren** om uw programma te implementeren.

   ![](assets/configure-pipeline5.png)


## Uitsluitend pijplijnen zonder productie en codekwaliteit

Naast de hoofdpijpleiding die zich naar het stadium en de productie ontwikkelt, kunnen klanten extra pijpleidingen opzetten, die **niet-productiepijpleidingen** worden genoemd. Deze pijpleidingen voeren altijd de bouw en de stappen van de codekwaliteit uit. Ze kunnen optioneel ook worden geïmplementeerd in de omgeving van Adobe Managed Services.

Op het thuisscherm worden deze pijpleidingen op een nieuwe kaart vermeld:

1. Open de tegel **Niet-productiepijplijnen** vanuit het startscherm van Cloud Manager.

   ![](assets/configure-pipeline6.png)

1. Klik op de knop **Toevoegen** om de naam van de pijpleiding, het type pijpleiding en de tussenruimte van de it op te geven.

   Bovendien, kunt u de Trigger van de Plaatsing van de opstelling en Belangrijk Gedrag van de Mislukking van de Opties van de Pijpleiding ook plaatsen.

   ![](assets/non-prod-pipe1.png)

1. Klik **sparen** en de pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   ![](assets/configure-pipeline8.png)

   * **Bewerken** - hiermee kunt u de pijpleidinginstellingen bewerken
   * **Build** - navigeert aan de uitvoeringspagina, waarvan de pijpleiding kan worden uitgevoerd
   * **Git** beheren - Hiermee kan de gebruiker de benodigde informatie ophalen voor toegang tot de Git-opslagplaats van Cloud Manager

## De volgende stappen {#the-next-steps}

Zodra u de pijpleiding hebt gevormd, moet u uw code opstellen.

Zie [Uw code](deploy-code.md) implementeren voor meer informatie.
