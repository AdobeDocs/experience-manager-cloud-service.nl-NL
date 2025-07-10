---
title: Inhoud herstellen in AEM as a Cloud Service
description: Leer hoe u uw AEM as a Cloud Service-inhoud kunt herstellen vanaf een back-up met Cloud Manager.
exl-id: 921d0c5d-5c29-4614-ad4b-187b96518d1f
feature: Operations
role: Admin
source-git-commit: f5dcf76b662e8bec9248ca11f133f9a82142d877
workflow-type: tm+mt
source-wordcount: '1323'
ht-degree: 0%

---


# Inhoud herstellen in AEM as a Cloud Service {#content-restore}

U kunt uw AEM as a Cloud Service-inhoud vanaf een back-up herstellen met Cloud Manager.

## Overzicht {#overview}

Cloud Manager-proces voor het terugzetten van zelfbediening kopieert gegevens van Adobe-systeemback-ups en herstelt deze in de oorspronkelijke omgeving. Herstel wordt uitgevoerd om gegevens terug te keren die zijn verloren, beschadigd of per ongeluk verwijderd.

Het herstelproces heeft alleen invloed op inhoud, zodat uw code en versie van AEM ongewijzigd blijven. U kunt op elk gewenst moment een herstelbewerking van afzonderlijke omgevingen starten.

Cloud Manager biedt twee typen back-ups waarvan u de inhoud kunt herstellen.

* **punt-in-tijd (PIT):** Deze optie herstelt ononderbroken steunen die binnen de afgelopen 24 uren worden gevangen.
* **Vorige week:** Dit type herstelt van systeemsteunen in de laatste zeven dagen exclusief vorige 24 uren.

In beide gevallen blijven de versie van uw aangepaste code en de AEM-versie ongewijzigd.

>[!TIP]
>
>Het is ook mogelijk om steunen [ te herstellen gebruikend openbare API ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/).

>[!WARNING]
>
>* Deze functie mag alleen worden gebruikt bij ernstige problemen met code of inhoud.
>* Bij het herstellen van een back-up worden alle gegevens verwijderd die na de back-up zijn toegevoegd. Staging wordt ook teruggezet naar de vorige versie.
>* Overweeg andere selectieve herstelopties voor inhoud voordat u begint met het herstellen van inhoud.

## Opties voor het herstellen van selectieve inhoud {#selective-options}

Overweeg deze opties om de inhoud eenvoudiger te herstellen voordat u de inhoud volledig herstelt.

* Als een pakket voor de geschrapte weg beschikbaar is, installeer opnieuw het pakket gebruikend de [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md).
* Als de geschrapte weg een pagina in Plaatsen was, gebruik [ herstellen de functie van de Boom ](/help/sites-cloud/authoring/sites-console/page-versions.md).
* Als de geschrapte weg een activa omslag was en de originele dossiers beschikbaar zijn, herupload hen via [ de console van Assets ](/help/assets/add-assets.md).
* Als de schrappingsinhoud activa was, overweeg [ terugstellend vorige versies van de activa ](/help/assets/manage-digital-assets.md).

Als geen van de bovenstaande opties werkt en de inhoud van het verwijderde pad significant is, voert u een inhoudsherstel uit zoals in de volgende secties wordt beschreven.

## Gebruikersrol maken {#user-role}

Standaard heeft geen enkele gebruiker toestemming om inhoud te herstellen in ontwikkelings-, productie- of staging-omgevingen. Gebruik de volgende algemene stappen om deze machtiging te delegeren aan specifieke gebruikers of groepen.

1. Maak een productprofiel met een expressieve naam die verwijst naar het herstellen van inhoud.
1. Verstrek de **toestemming van de Toegang van het Programma 0} {op het vereiste programma.**
1. Verstrek het **Milieu herstellen creeert** toestemming op het vereiste milieu of alle milieu&#39;s van het programma, afhankelijk van uw gebruiksgeval.
1. Wijs gebruikers toe aan dat profiel.

Voor details bij het beheren van toestemmingen, zie [ de Toestemmingen van de Douane ](/help/implementing/cloud-manager/custom-permissions.md).

## De inhoud van een omgeving herstellen {#restoring-content}

>[!NOTE]
>
>Een gebruiker moet [ aangewezen toestemmingen ](#user-role) hebben om in werking te stellen herstelt verrichting.

**om de inhoud van een milieu te herstellen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik op het programma waarvoor u een herstelbewerking wilt starten.

1. Maak een lijst van alle milieu&#39;s voor het programma door één van het volgende te doen:

   * Van het linkerzijmenu, onder **Diensten**, klik ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

     ![ Milieu&#39;s tabel ](assets/environments-1.png)

   * Van het linkerzijmenu, onder **Programma**, klik **Overzicht**, dan van de **Milieu** kaart, klik ![ pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **tonen allen**.

     ![ toon alle optie ](assets/environments-2.png)

     >[!NOTE]
     >
     >De **kaart van milieu&#39;s** {maakt een lijst van slechts drie milieu&#39;s. Klik **tonen allen** in de kaart om *alle* milieu&#39;s van het programma te zien.

1. In de lijst van Milieu&#39;s, rechts van een milieu waarvan inhoud u wilt herstellen, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), dan klik **herstellen Inhoud**.

   ![ herstelt inhoudsoptie van het ellipsmenu ](/help/operations/assets/environments-ellipsis-menu.png)

1. Op het **herstellen Inhoud** lusje van de pagina van het milieu, in de **Tijd om** drop-down lijst te herstellen, selecteer het tijdkader van herstellen.

   ![ herstelt het lusje van de Inhoud van een milieu ](/help/operations/assets/environments-content-restore-tab.png)

   * Als u **Laatste 24 uren** koos, op het aangrenzende **gebied van de Tijd**, specificeer de nauwkeurige tijd binnen de laatste 24 te herstellen uren.
   * Als u **Vorige week** koos, op het aangrenzende **gebied van de Dag**, selecteer een datum binnen de afgelopen zeven dagen, exclusief de vorige 24 uren.

1. Zodra u een datum selecteert of een tijd specificeert, toont de **beschikbare Steunen** sectie hieronder een lijst van beschikbare steunen die kunnen worden hersteld

1. Klik ![ pictogram van de Informatie ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) naast een steun om zijn codeversie en versie van AEM te zien, dan wegen terugzeteffect alvorens een steun te selecteren (zie [ kiezen de juiste steun ](#choosing-backup)).

   ![ Steun info ](assets/backup-info.png)

   De tijdstempel die voor de terugzetopties wordt weergegeven, is gebaseerd op de tijdzone van de computer van de gebruiker.

1. Aan het rechtereind van de rij die de steun vertegenwoordigen u wilt herstellen, ![ roteren gewaagd CCW, of herstellen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_RotateCCWBold_18_N.svg) om te beginnen herstelt proces.

1. Herzie de details in **herstellen Inhoud** dialoogdoos, dan klik **herstellen**.

   ![ bevestigt herstel ](assets/backup-restore.png)

Het back-upproces wordt gestart. U kunt zijn status in de **[bekijken herstelt Activiteit](#restore-activity)** lijst. De tijd die nodig is om een terugzetbewerking te voltooien, is afhankelijk van de grootte en het profiel van de inhoud die wordt teruggezet.

Wanneer de herstelbewerking met succes is voltooid, doet de omgeving het volgende:

* Hiermee worden dezelfde code en AEM-release uitgevoerd als op het moment dat de herstelbewerking wordt gestart.
* Deze heeft dezelfde inhoud die beschikbaar was op het tijdstempel van de gekozen opname, waarbij de indexen opnieuw zijn samengesteld en overeenkomen met de huidige code.

## Kies de juiste reservekopie {#choosing-backup}

Cloud Manager-proces voor zelfherstel herstelt alleen inhoud naar AEM. Daarom moet u zorgvuldig rekening houden met wijzigingen in de code die zijn aangebracht tussen het gewenste herstelpunt en de huidige tijd. Controleer de commit geschiedenis tussen huidige begaat identiteitskaart en terug te zetten aan.

Er zijn verschillende scenario&#39;s.

* De omgevingsaangepaste code en de terugzetbewerking bevinden zich in dezelfde opslagplaats en dezelfde vertakking.
* De milieu douanecode en herstellen delen één bewaarplaats, gebruiken een afzonderlijke tak, en komen van gemeenschappelijk voort.
* De aangepaste code voor de omgeving en het terugzetten bevinden zich in verschillende opslagruimten.
   * In dit geval wordt een id voor vastleggen niet weergegeven.
   * Adobe raadt u ten zeerste aan beide opslagruimten te klonen en een hulpprogramma voor bestandsdeling te gebruiken om de vertakkingen te vergelijken.

Houd er ook rekening mee dat een herstelbewerking ertoe kan leiden dat uw productie- en testomgevingen niet meer synchroon zijn. U bent verantwoordelijk voor de gevolgen van het herstellen van inhoud.

## Herstelactiviteit {#restore-activity}

De **herstel de lijst van de Activiteit** toont het statuut van tien meest recente herstelt verzoeken met inbegrip van om het even welke actieve herstelt verrichtingen.

![ herstel activiteit ](assets/backup-activity.png)

Door ![ het pictogram van de Informatie ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) voor een steun te klikken, kunt u logboeken voor die steun downloaden en de codedetails met inbegrip van de verschillen tussen de momentopname en gegevens inspecteren op het ogenblik in werking werd gesteld herstelt.

## Offsite back-up {#offsite-backup}

Regelmatige back-ups dekken het risico van onopzettelijke verwijderingen of technische storingen in AEM Cloud Services, maar extra risico&#39;s kunnen het gevolg zijn van een fout in een regio. Naast beschikbaarheid is het grootste risico in dergelijke regionale uitvallen een gegevensverlies.

AEM as a Cloud Service beperkt dit risico voor alle AEM-productieomgevingen. Dat wil zeggen dat alle AEM-inhoud voortdurend wordt gekopieerd naar een extern gebied. Met dit proces wordt de inhoud drie maanden beschikbaar voor herstel. Deze mogelijkheid wordt een externe back-up genoemd.

AEM Service Reliability Engineering herstelt de AEM Cloud Service-omgeving voor opslag en productie van externe back-ups tijdens uitval in gegevensregio.

## Beperkingen {#limitations}

Het gebruik van het mechanisme voor zelfherstel is onderworpen aan de volgende beperkingen.

* Herstelbewerkingen zijn beperkt tot zeven dagen, wat betekent dat het niet mogelijk is om een momentopname ouder dan zeven dagen te herstellen.
* In een programma per kalendermaand zijn maximaal tien succesvolle herstelbewerkingen toegestaan in alle omgevingen.
* Nadat de omgeving is gemaakt, duurt het zes uur voordat de eerste back-upmomentopname is gemaakt. Totdat deze momentopname is gemaakt, kan geen herstel worden uitgevoerd op de omgeving.
* Een terugzetbewerking wordt niet geïnitieerd als er een volledige stack of web tier config-pijplijn is die momenteel voor de omgeving wordt uitgevoerd.
* Een terugzetprocedure kan niet worden gestart als een andere terugzetbewerking al op dezelfde omgeving wordt uitgevoerd.
* In zeldzame gevallen kan de geselecteerde back-up vanwege de limiet van 24 uur/7 dagen voor het maken van back-ups niet langer beschikbaar zijn vanwege een vertraging tussen de datum waarop deze is geselecteerd en het moment waarop de terugzetprocedure wordt gestart.
* Gegevens uit verwijderde omgevingen gaan permanent verloren en kunnen niet worden hersteld.
