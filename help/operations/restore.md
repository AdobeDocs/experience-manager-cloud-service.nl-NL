---
title: Herstel inhoud in AEM als een cloudservice
description: Leer hoe je de inhoud van je AEM als Cloud Service kunt herstellen vanuit een back-up met Cloud Manager.
exl-id: 921d0c5d-5c29-4614-ad4b-187b96518d1f
feature: Operations
role: Admin
source-git-commit: e6bd71cc56db766fcbab3a925baabb5901c97ee8
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 0%

---


# Herstel inhoud in AEM als een Cloud Service {#content-restore}

Je kunt de inhoud van je AEM als Cloud Service herstellen vanuit een back-up met Cloud Manager.



Het zelfbedieningsherstelproces van Cloud Manager kopieert gegevens van Adobe-systeemback-ups en herstelt deze naar de oorspronkelijke omgeving. Een herstel wordt uitgevoerd om gegevens die verloren, beschadigd of per ongeluk verwijderd zijn terug te brengen naar de oorspronkelijke staat.

Het herstelproces beïnvloedt alleen de inhoud, waardoor je code en versie van AEM ongewijzigd blijven. Je kunt op elk moment een hersteloperatie van individuele omgevingen starten.

Als je eerder geïmplementeerde broncode op een eenvoudige en snelle manier wilt herstellen, zonder een nieuwe pipeline-uitvoering te hoeven starten, kun je Restore the Previous Code Deployed[&#x200B; gebruiken](/help/operations/restore-previous-code-deployed.md).

Cloud Manager biedt twee soorten back-ups waarmee je content kunt herstellen.

* **Point-In-Time (PIT):** Deze optie herstelt continue back-ups die in de afgelopen 24 uur zijn gemaakt.
* **Vorige week:** Dit type herstelt van systeemback-ups in de afgelopen zeven dagen, exclusief de afgelopen 24 uur.

In beide gevallen blijven de versie van je aangepaste code en de AEM-versie ongewijzigd.

>[!TIP]
>
>Het is ook mogelijk om back-ups [te herstellen met behulp van de publieke API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/)

>[!WARNING]
>
>* Deze functie mag alleen worden gebruikt als er ernstige problemen zijn met code of content.
>* Het herstellen van een back-up verwijdert alle data die na die back-up is toegevoegd. De enscenering keert ook terug naar de vorige versie.
>* Voordat je een contentherstel start, overweeg andere selectieve contentherstelopties.

## Selectieve contentherstelopties {#selective-options}

Voordat u een volledige contentrestauratie herstelt, overweeg deze opties om uw inhoud gemakkelijker te herstellen.

* Als er een pakket voor het verwijderde pad beschikbaar is, installeer het pakket opnieuw met behulp van de [Package Manager](/help/implementing/developing/tools/package-manager.md).
* Als het verwijderde pad een pagina in Sites was, gebruik dan de [functie](/help/sites-cloud/authoring/sites-console/page-versions.md) Restore Tree.
* Als het verwijderde pad een asset-map was en de originele bestanden beschikbaar zijn, upload ze dan opnieuw via [de Assets-console](/help/assets/add-assets.md).
* Als de verwijderde inhoud assets waren, overweeg [dan het herstellen van eerdere versies van de assets](/help/assets/manage-digital-assets.md).

Als geen van bovenstaande opties werkt en de inhoud van het verwijderde pad significant is, voer dan een inhoudsherstel uit zoals beschreven in de volgende secties.

## Aanmaken van gebruikersrol {#user-role}

Standaard heeft geen enkele gebruiker toestemming om contentherstels uit te voeren in ontwikkel-, productie- of stagingomgevingen. Om deze toestemming te delegeren aan specifieke gebruikers of groepen, gebruik je de volgende algemene stappen.

1. Maak een productprofiel met een expressieve naam die verwijst naar contentherstel.
1. Geef de **Programmatoegangstoestemming** voor het vereiste programma.
1. Geef de **Environment Restore Create-toestemming** voor de vereiste omgeving of alle omgevingen van het programma, afhankelijk van je gebruikssituatie.
1. Wijs gebruikers toe aan dat profiel.

Voor details over het beheren van permissies, zie [Aangepaste Rechten](/help/implementing/cloud-manager/custom-permissions.md).

## Herstel de inhoud van een omgeving {#restoring-content}

>[!NOTE]
>
>Een gebruiker moet over de juiste rechten[&#x200B; beschikken om &#x200B;](#user-role)een hersteloperatie te starten.

**Om de inhoud van een omgeving te herstellen:**

1. Log in op Cloud Manager op [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteer de juiste organisatie.

1. Klik op het programma waarvoor je een herstel wilt starten.

1. Vermeld alle omgevingen voor het programma door een van de volgende te doen:

   * Klik in het linkermenu, onder Services, op **Data-icoon** ![Omgevingen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg).**&#x200B;**

     ![Tabblad Omgevingen](assets/environments-1.png)

   * Klik in het linkermenu, onder **Programma, op** Overzicht **, en klik vervolgens vanaf de** kaart Omgevingen **op het pictogram** Workflow Toon ![](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) Alles **.**

     ![Toon alle optie](assets/environments-2.png)

     >[!NOTE]
     >
     >De **Omgevingen-kaart** vermeldt slechts drie omgevingen. Klik op **&#39;Alles** weergeven&#39; op de kaart om alle *omgevingen van het programma te zien*.

1. In de tabel Omgevingen, rechts van een omgeving waarvan je de inhoud wilt herstellen, klik ![je op het pictogram Meer of het ellipsmenu-icoon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en vervolgens op **Inhoud herstellen**.

   ![Optie Inhoud herstellen vanuit het ellipsmenu](/help/operations/assets/environments-ellipsis-menu.png)

1. Op het **tabblad Inhoud herstellen** op de pagina van de omgeving, selecteer je in de **keuzelijst Tijd om te herstellen** het tijdsbestek van het herstel.

   ![Bestand Inhoud herstellen van een omgeving](/help/operations/assets/environments-content-restore-tab.png)

   * Als je Laatste 24 uur **kiest**, geef je in het aangrenzende **Tijdveld** de exacte tijd aan binnen de laatste 24 uur om te herstellen.
   * Als je Vorige week **kiest**, kies je in het aangrenzende **dagveld** een datum binnen de afgelopen zeven dagen, exclusief de voorgaande 24 uur.

1. Zodra je een datum hebt geselecteerd of een tijd hebt opgegeven, toont het **gedeelte Beschikbare** back-ups hieronder een lijst van beschikbare back-ups die kunnen worden hersteld

1. Klik op ![het Informatie-icoon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) naast een back-up om de codeversie en AEM-release te zien, en weeg vervolgens de impact op herstel af voordat je een back-up selecteert (zie [Kies de juiste back-up](#choosing-backup)).

   ![Back-upinformatie](assets/backup-info.png)

   De tijdstempel die wordt weergegeven voor de herstelopties is gebaseerd op de tijdzone van de gebruiker van de computer.

1. Aan het rechteruiteinde van de rij die de back-up vertegenwoordigt die je wilt herstellen, klik op ![Rotate CCW bold of restore](https://spectrum.adobe.com/static/icons/workflow_18/Smock_RotateCCWBold_18_N.svg) om het herstelproces te starten.

1. Bekijk de details in het **dialoogvenster Inhoud herstellen** en klik dan op **Herstellen**.

   ![Bevestig herstel](assets/backup-restore.png)

Het back-upproces wordt gestart. Je kunt de status bekijken in de **[lijst Activiteit](#restore-activity)** herstellen. De tijd die nodig is voor een hersteloperatie hangt af van de grootte en het profiel van de te herstellende inhoud.

Wanneer het herstel succesvol is voltooid, doet de omgeving het volgende:

* Voert dezelfde code en AEM-release uit als op het moment van het starten van de hersteloperatie.
* Het bevat dezelfde inhoud die beschikbaar was op het tijdstempel van de gekozen snapshot, waarbij de indexen zijn aangepast aan de huidige code.

## Kies de juiste back-up {#choosing-backup}

Het zelfbedieningsherstelproces van Cloud Manager herstelt alleen inhoud in AEM. Om deze reden moet je zorgvuldig rekening houden met codewijzigingen die zijn aangebracht tussen het gewenste herstelpunt en het huidige tijdstip. Bekijk de commitgeschiedenis tussen de huidige commit-ID en de account die wordt hersteld.

Er zijn verschillende scenario&#39;s.

* De aangepaste code van de omgeving en het herstel staan in dezelfde repository en dezelfde branch.
* De aangepaste code van de omgeving en de restore delen één repository, gebruiken een aparte branch en komen voort uit een gemeenschappelijke commit.
* De aangepaste code van de omgeving en het herstel bevinden zich in verschillende repositories.
   * In dit geval wordt geen commit-ID weergegeven.
   * Adobe raadt sterk aan om beide repositories te klonen en een verschillende tool te gebruiken om de takken te vergelijken.

Houd er ook rekening mee dat een herstel ervoor kan zorgen dat je productie- en stagingomgevingen uit elkaar raken. U bent verantwoordelijk voor de gevolgen van het herstellen van content.

## Herstelactiviteit {#restore-activity}

De **lijst met Herstelactiviteit** toont de status van de tien meest recente herstelverzoeken, inclusief alle actieve hersteloperaties.

![Herstelactiviteit](assets/backup-activity.png)

Door op het Informatie-icoon![&#x200B; te klikken &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg)voor een back-up, kun je logs van die back-up downloaden en de codedetails bekijken, inclusief de verschillen tussen de snapshot en de data op het moment dat het herstel werd gestart.

## Back-up buiten locatie {#offsite-backup}

Reguliere back-ups dekken het risico op per ongeluk verwijderingen of technische storingen binnen AEM Cloud Services, maar er kunnen extra risico&#39;s ontstaan door het falen van een regio. Naast beschikbaarheid is het grootste risico bij dergelijke regionale uitval het verlies van data.

AEM als Cloud Service beperkt dit risico voor alle AEM-productieomgevingen. Dat wil zeggen, het kopieert continu alle AEM-inhoud naar een afgelegen regio. Dit proces maakt de inhoud drie maanden beschikbaar voor herstel. Deze mogelijkheid staat bekend als een offsite back-up.

AEM Service Reliability Engineering herstelt staging- en productieomgevingen van AEM Cloud Service-omgevingen uit off-site back-ups tijdens dataregio-uitvallen.

## Principes van Dataregio-mapping {#data-region-mapping-principles}

Adobe volgt een reeks interne richtlijnen om dataregio-mappings voor AEM als Cloud Service **te** bepalen. Deze richtlijnen zijn ontworpen om operationele efficiëntie te ondersteunen, naleving van regionale regelgeving te waarborgen en een consistente klantervaring te bieden op wereldmarkten.

### Transparantie van regiomapping {#region-mapping-transparency}

Adobe maakt geen gedetailleerde regio-tot-regio kaartinformatie openbaar.\
Als klanten specifieke of gerechtvaardigde vragen hebben over regionale implementatie, gegevensresidentie of compliance-implicaties, wordt aanbevolen rechtstreeks contact op te nemen met Adobe via officiële support- of accountkanalen.

### Kernprincipes voor het toewijzen van dataregio&#39;s {#core-principles}

Bij het bepalen van een geschikte dataregio-mapping hanteert Adobe verschillende geprioriteerde criteria:

1. **Verlaat de wereldregio niet**\
   Uitzendingen blijven binnen een van de belangrijkste wereldregio&#39;s: **APAC,**&#x200B;**EMEA** en **de Amerika&#39;s**.

2. **Verlaat het continent niet.**\
   Waar mogelijk blijven datareplicatie en failover op hetzelfde continent.

3. **Verlaat het land niet**\
   Als het technisch mogelijk is, blijven gegevens binnen dezelfde nationale grenzen.

### Afhandelingsuitzonderingen {#handling-exceptions}

Wanneer aan bovenstaande criteria niet wordt voldaan vanwege technische of infrastructurele beperkingen, past Adobe aanvullende overwegingen toe:

* **Europa-specifieke richtlijn**\
  Back-up- of secundaire regio&#39;s mogen zich niet in niet-EU-landen bevinden.\
  (Het omgekeerde—een EU-land als backup gebruiken voor een niet-EU-voorverkiezing—kan acceptabel zijn als er geen betere optie voor hetzelfde land bestaat.)

* **Vermijd bepaalde regio&#39;s**\
  Regio&#39;s met beperkende databeleid of verhoogd regelgevingsrisico moeten worden vermeden als back-up- of failoverlocaties.

Als klanten verduidelijking nodig hebben of compliance-gedreven behoeften hebben, raadt Adobe aan contact op te nemen met het Adobe-accountteam of de supportorganisatie voor advies dat is afgestemd op hun specifieke situatie.

## Beperkingen {#limitations}

Het gebruik van het selfserviceherstelmechanisme is onderhevig aan de volgende beperkingen.

* Herstelbewerkingen zijn beperkt tot zeven dagen, wat betekent dat het niet mogelijk is om een snapshot ouder dan zeven dagen te herstellen.
* Maximaal tien succesvolle herstelopdrachten zijn toegestaan in alle omgevingen van een programma per kalendermaand.
* Na het aanmaken van de omgeving duurt het zes uur voordat de eerste back-upsnapshot wordt gemaakt. Totdat deze snapshot is gemaakt, kan er geen herstel worden uitgevoerd in de omgeving.
* Een hersteloperatie wordt niet gestart als er momenteel een full stack- of webtier-configuratiepijplijn draait voor de omgeving.
* Een herstel kan niet worden gestart als er al een andere restore op dezelfde omgeving draait.
* In zeldzame gevallen kan de geselecteerde back-up vanwege de 24 uur/zeven dagen limiet op back-ups onbeschikbaar worden door een vertraging tussen het moment waarop deze werd geselecteerd en het starten van het herstel.
* Gegevens uit verwijderde omgevingen gaan permanent verloren en kunnen niet worden hersteld.
