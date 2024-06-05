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

De automatiseringsinstelling is ontworpen om uit de verpakking te werken met een AEM site die is gemaakt met [AEM kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) met de [Gegevenslaag client-Adobe](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html) ingeschakeld. U kunt een nieuwe site maken waarvoor deze functies automatisch zijn ingeschakeld met de functie [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) of door een site te maken met een [Sitesjabloon](/help/journey-sites/quick-site/create-site.md).

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
1. Voer een pijplijn naar volledige stapel uit in Cloud Manager.

De omgeving moet nu gereed zijn voor Experience Cloud Setup Automation.

## Hoe te Opstelling

1. Navigeren naar **Sites** en selecteert u de hoofdmap van de site die u wilt integreren met Adobe Analytics.
1. Vouw het menu voor de zijbalk uit en selecteer **Analyses instellen**.

   Dit is een nieuwe optie in de zijspoorstaaf die een paneel opent dat controles en status voor de Automatisering van de Opstelling van het Experience Cloud verstrekt.
1. Selecteer de **Analyse integreren** knop.
1. Geef in het dialoogvenster dat wordt weergegeven een naam op voor het dialoogvenster **ID van rapportsuite**.

   Deze tekenreeks wordt gebruikt om een [ID van rapportsuite](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html) in Adobe Analytics als de gegevensopslagruimte voor de analysegegevens voor de geselecteerde AEM. De opgegeven tekenreeks wordt toegevoegd met omgeving- en tier-id&#39;s om ervoor te zorgen dat deze uniek zijn.

1. Pagina en deelvenster vernieuwen en selecteren **Integratiestatus controleren** de status van de automatisering te controleren.

   De automatische opstelling komt asynchroon voor. De **Integratiestatus controleren** zal de huidige status van de integratie aantonen.

   * **In uitvoering** - geeft aan dat de taak wordt uitgevoerd.
   * **Integratie voltooid** - Hiermee wordt aangegeven dat de taak is voltooid met het integreren van Analytics en Tags, het instellen van Tags-extensies en -regels en het maken van de nieuwe rapportsuite in Adobe Analytics.
   * **Mislukt** - geeft aan dat de automatische taak niet kan worden voltooid. Controleer de logbestanden voor deze taak door op de koppeling Logs te klikken.

## AEM instellen valideren

Nadat de automatisering is voltooid, controleert u of uw site de Analytics-gebeurtenissen heeft geactiveerd.

1. Open een pagina op uw site met de **Sites-editor**.
1. Gebruik de **Weergeven als gepubliceerd** om een gepubliceerde versie van de pagina te laden.
1. Gebruik de ontwikkelaarshulpmiddelen van browser om het netwerkverkeer te inspecteren en dat **Tags** en `AppMeasurement.js` bestanden worden nu geladen.
1. Inspect de browser console om te zien dat de gebeurtenissen van het paginaniveau en componentenniveau door de Laag van de Gegevens van de Cliënt van de Adobe in brand worden gestoken en worden verzameld.

## Analytische instellingen valideren

Navigeer vervolgens naar Adobe Analytics om de gegevens weer te geven die afkomstig zijn van gebeurtenissen op de AEM site.

1. Navigeer naar Adobe Analytics in dezelfde IMS Org als uw AEM site.
1. Een nieuw overzichtsrapport maken waarin AEM Sites navigeert naar **Rapporten** > **Betrokkenheid** > **Adobe Experience Manager** > **Overzicht van siteprestaties**.
1. Selecteren **Rapport openen**.
1. Selecteer de **ID van rapportsuite** die overeenkomt met de naam van de rapportsuite die in de vorige exercitie is gebruikt.
1. De gegevensstroom van de meningsanalyse in de nieuwe malplaatje in tijd.

   >[!NOTE]
   >
   > Met een nieuwe integratie kan het een paar uur duren voordat het rapport wordt gevuld met gegevens.
