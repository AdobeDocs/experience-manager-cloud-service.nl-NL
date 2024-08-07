---
title: Adobe Analytics integreren met Experience Cloud Setup Automation
description: De Automatisering van de Opstelling van het Experience Cloud verstrekt een eenvoudige en geautomatiseerde manier om Experience Manager Sites met de Markeringen van het Experience Platform en Adobe Analytics met een eenvoudige interface van de tovenaar UI te integreren en te voorzien. Leer hoe u de automatische installatie kunt gebruiken met uw eigen site.
feature: Integration
role: Admin
exl-id: 351ead2c-7b0d-4bd9-a020-47516948d467
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Adobe Analytics integreren met Experience Cloud Setup Automation {#integrate-adobe-analytics-automation-setup}

De Automatisering van de Opstelling van het Experience Cloud verstrekt een eenvoudige en geautomatiseerde manier om Experience Manager Sites met de Markeringen van het Experience Platform en Adobe Analytics met een eenvoudige interface van de tovenaar UI te integreren en te voorzien.

Het is nooit eenvoudiger geweest om Adobe Analytics met AEM Sites te integreren. Met de Automatisering van de Opstelling van het Experience Cloud, vestiging, het integreren, en het van instrumenten voorzien van uw plaats om prestatiesanalyses te vangen om te begrijpen hoe goed uw klanten engaging en het omzetten allen behandeld met slechts een paar klikken.

In deze video wordt uitgelegd hoe een AEM site is geïntegreerd met Experience Platform Tags en Analytics met behulp van Experience Cloud Setup Automation:

>[!VIDEO](https://video.tv.adobe.com/v/345372/?quality=12)

## Vereisten

De automatiseringsopstelling wordt ontworpen om uit de doos met een AEMPlaats te werken die gebruikend [ AEM de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) met de [ toegelaten Gegevens van de Cliënt van de Adobe ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html) wordt gebouwd. U kunt een nieuwe plaats produceren die deze eigenschappen heeft die automatisch gebruikend het [ AEM Archieftype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) worden toegelaten of door een plaats te creëren gebruikend a [ malplaatje van de Plaats ](/help/journey-sites/quick-site/create-site.md).

## Vereisten {#prerequisites}

Voordat u deze functie gebruikt, is het belangrijk dat u deze instructies opvolgt om ervoor te zorgen dat de vereiste services op de juiste wijze zijn ingesteld in uw omgeving:

1. Log in bij Adobe Admin Console (https://adminconsole.adobe.com/).
1. Zorg ervoor dat de juiste IMS-organisatie-id in de rechterbovenhoek is geselecteerd.
1. Klik op de optie voor productnavigatie.
1. Controleer of &quot;Adobe Experience Manager as a Cloud Service&quot; is ingericht voor de IMS Org.
1. Controleer of &quot;Adobe Analytics&quot; is ingericht voor de IMS Org.
1. Ga naar Cloud Manager (https://experience.adobe.com/cloud-manager).
1. Selecteer het gewenste programma.
1. Controleer of de Cloud Service zich in de meest recente versie van de omgeving bevindt (als dit niet het geval is, selecteert u Bijwerken in de menuopties).
1. Stel een Volledige pijpleiding van de Stapel in Cloud Manager in werking.

De omgeving moet nu gereed zijn voor Experience Cloud Setup Automation.

## Hoe te Opstelling

1. Navigeer aan **Plaatsen** en selecteer de wortel van de plaats met Adobe Analytics te integreren.
1. Breid het zijspoormenu uit en selecteer **Analytics van de Opstelling**.

   Dit is een nieuwe optie in de zijspoorstaaf die een paneel opent dat controles en status voor de Automatisering van de Opstelling van het Experience Cloud verstrekt.
1. Selecteer **integreren Analytics** knoop.
1. In de resulterende dialoog, verstrek een naam voor **identiteitskaart van de Reeks van het Rapport**.

   Dit koord wordt gebruikt om identiteitskaart van de Reeks van het a [ Rapport ](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html) in Adobe Analytics als gegevensopslag voor de analysegegevens voor de geselecteerde plaats van de AEM te creëren. De opgegeven tekenreeks wordt toegevoegd met omgeving- en tier-id&#39;s om ervoor te zorgen dat deze uniek zijn.

1. Vernieuw de pagina en het paneel en selecteer **de Status van de Integratie van de Controle** om de status van de automatisering te controleren.

   De automatische opstelling komt asynchroon voor. De **Status van de Integratie van de Controle** zal de huidige status van de integratie tonen.

   * **lopend** - wijst erop dat de baan loopt.
   * **Volledige Integratie** - wijst erop dat de baan het integreren van Analytics en Markeringen, de uitbreidingen van de plaatstags en de regels van Markeringen, en het creëren van de nieuwe Reeks van het Rapport in Adobe Analytics heeft voltooid.
   * **Gebrek** - wijst erop dat de geautomatiseerde baan niet kon met succes voltooien. Controleer de logbestanden voor deze taak door op de koppeling Logs te klikken.

## AEM instellen valideren

Nadat de automatisering is voltooid, controleert u of uw site de Analytics-gebeurtenissen heeft geactiveerd.

1. Open omhoog een pagina in uw plaats gebruikend de **Redacteur van Plaatsen**.
1. Gebruik de **Mening zoals Gepubliceerde** optie om een gepubliceerde versie van de pagina te laden.
1. Gebruik de ontwikkelaarshulpmiddelen van browser om het netwerkverkeer te inspecteren en dat **de Markeringen** en `AppMeasurement.js` dossiers nu worden geladen.
1. Inspect de browser console om te zien dat de gebeurtenissen van het paginaniveau en componentenniveau door de Laag van de Gegevens van de Cliënt van de Adobe in brand worden gestoken en worden verzameld.

## Analytische instellingen valideren

Navigeer vervolgens naar Adobe Analytics om de gegevens weer te geven die afkomstig zijn van gebeurtenissen op de AEM site.

1. Navigeer naar Adobe Analytics in dezelfde IMS Org als uw AEM site.
1. Creeer een nieuw overzichtsrapport voor AEM Sites navigerend aan **Rapporten** > **Betrokkenheid** > **Adobe Experience Manager** > **het Overzicht van de Prestaties van de Plaats**.
1. Selecteer **Open Rapport**.
1. Selecteer **identiteitskaart van de Reeks van het Rapport** die de naam van de Reeks van het Rapport aanpast die in de vorige oefening wordt gebruikt.
1. De gegevensstroom van de meningsanalyse in de nieuwe malplaatje in tijd.

   >[!NOTE]
   >
   > Met een nieuwe integratie kan het een paar uur duren voordat het rapport wordt gevuld met gegevens.
