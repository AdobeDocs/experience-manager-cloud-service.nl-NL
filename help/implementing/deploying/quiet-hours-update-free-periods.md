---
title: Stil uur en gratis perioden bijwerken
description: Leer hoe u de operationele impact van automatische updates van AEM as a Cloud Service minimaliseert met Quiet Hours en Update-Free Periods.
feature: Deploying
role: Admin
badge: label="Beperkte beschikbaarheid" type="Positive"
exl-id: 54f86a58-eb56-43e6-ab51-7af7466a2d40
source-git-commit: 350b288d30b3fb8d9d308dbd279f579cec0b292c
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---

# Gratis uren en perioden bijwerken {#quiet-hours-update-free-periods}

>[!NOTE]
>Deze eigenschap zal als a **Beperkte eigenschap van de Beschikbaarheid** beschikbaar zijn die met 25th September begint. E-mail [ aemcs-update-free@adobe.com ](mailto:aemcs-update-free@adobe.com) om de eigenschap te hebben geactiveerd op uw programma&#39;s.

De AEM as a Cloud Service [ automatische onderhoudsupdates ](/help/implementing/deploying/aem-version-updates.md) zorgen ervoor dat uw instanties veilig en bijgewerkt met de recentste onderhoudsversies blijven. Dat gezegd hebbende, in sommige gevallen (zoals go-live gebeurtenissen) zou u die kritieke werkuren tegen om het even welke potentiële verstoringen kunnen &quot;beschermen&quot;moeten. AEM as a Cloud Service biedt daarom de mogelijkheid om een tijdsperiode in te stellen waarin automatische updates niet worden uitgevoerd voor lopende programma&#39;s.

U kunt deze tijdkaders vormen door twee het plannen opties te gebruiken:

* **stille uren** - u kunt een dagelijks tijdinterval (tot 8 uren) bepalen waar de updates niet zullen voorkomen.
* **Werk vrije periodes** bij - u kunt een periode van 7 dagtijd bepalen waar de updates niet zullen voorkomen. U kunt maximaal drie gratis updateperioden binnen een tijdsperiode van 12 maanden gebruiken.

De functies voor vrije perioden en stille uren voor updates zijn geconfigureerd op basis van &quot;per programma&quot;.

Bovendien, voor informatie over geplande automatische onderhoudsperiodes van AEM as a Cloud Service, gelieve te verwijzen naar de [ Uitgeven Roadmap van Experience Manager ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pagina.

## Stil uur {#quiet-hours}

Met de functie voor stille uren kunt u een tijdsvenster gedurende de dag definiëren zonder automatische updates. Alle onderhoudsupdates zullen verschuiven om buiten het gevormde tijdvenster voor te komen. Als bijvoorbeeld een update wordt gepland tijdens de opgegeven stille uren, wordt deze automatisch gestart nadat het stille interval is beëindigd. Het gevormde tijdinterval kan 8 uren niet overschrijden zodat de updates nog dagelijks kunnen voorkomen.

U kunt deze stille uren **per programma** bepalen, gebruikend uw lokale timezone.

### Hoe te om het rustige ureninterval te vormen {#configure-quiet-hours}

Het stille ureninterval kan worden gevormd door de interface van AEM Cloud Manager als volgt te gebruiken:

Ga naar **Activiteiten>Automatische Updates>de Opties van de Update**.

![ Configuratie ](assets/main-config.png)

1. Zorg ervoor **automatische updates tijdens specifieke uren** optie verhindert van een knevel wordt voorzien.
2. Klik **uitgeven**.
3. Plaats het stille ureninterval in het configuratievenster.

![ Configuratie van QuietUren ](assets/quiet-hours.png)

Wanneer u deze hebt ingesteld, worden de opgegeven begin- en einduren toegepast op elke kalenderdag die zich voorwaarts verplaatst. U kunt of onbruikbaar maken of de stille tijdwaarde van uren opnieuw vormen zoals nodig.

## Vrije perioden bijwerken {#update-free-periods}

Met de functie voor gratis updates kunt u een tijdsperiode van 7 dagen definiëren waarin geen updates worden uitgevoerd. Zodra gevormd, zullen alle onderhoudsupdates automatisch verschuiven om buiten het bepaalde tijdkader voor te komen. U kunt tot drie updates vrije periodes binnen een interval van 12 maanden hebben. Daarnaast kunnen gratis updateperioden maximaal één jaar van tevoren worden aangewezen.

Houd er bij het configureren van deze optie rekening mee dat (ten minste) een tijdsinterval van een week tussen perioden verplicht is om automatische updates te vergemakkelijken. Als dusdanig, wordt dit interval van een week automatisch afgedwongen en zal aan de kalender tussen de update vrije periodes worden toegevoegd u vormde. Hierdoor kunnen sommige kalenderdagen niet beschikbaar zijn voor selectie.

U kunt de update vrije periodes **per programma** bepalen.

### Hoe te om de update vrije periodes te vormen {#configure-update-free-periods}

De functie voor gratis updateperiodes kan als volgt worden geconfigureerd met de AEM Cloud Manager-interface:

Ga naar **Activiteiten>Automatische Updates>de Opties van de Update**.

![ Configuratie ](assets/main-config.png)

1. Ga naar de sectie Vrije perioden bijwerken.
2. Klik **toevoegen vrije periode van de Update**.
3. Selecteer een periode van een week gratis voor bijwerken vanuit de kalender.

![ de Vrije Configuratie van Punten van de Update ](assets/update-free-periods.png)

Een **Actief** pictogram zal dichtbij de momenteel actieve update vrije periode en a **Volledige** pictogram dichtbij de voltooide update vrije periodes worden getoond.
