---
title: Opmerkingen bij de release voor  [!DNL Workfront for Experience Manager enhanced connector]
description: Opmerkingen bij de release voor  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
feature: Release Information
role: Admin
source-git-commit: 346f36a476a11dc7fe022df8b7b8df7aff06a2ba
workflow-type: tm+mt
source-wordcount: '1621'
ht-degree: 0%

---

# Opmerkingen bij de release voor [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Workfront for Experience Manager enhanced connector] beschreven.

De releasedatum voor de meest recente versie 1.9.20 van [!DNL Workfront for Experience Manager enhanced connector] is 6 september 2024.

## Geen hooglichten {#release-highlights}

De meest recente versie van [!DNL Workfront for Experience Manager enhanced connector] bevat de volgende foutopsporing:

* Het MIME-type gaat verloren tijdens het uploaden en maken van een nieuwe versie van een bestaand element.

>[!NOTE]
>
>AEM 6.4 is het einde van de uitgebreide steun bereikt. Zie onze [ technische steunperiodes ](https://helpx.adobe.com/support/programs/eol-matrix.html). Vind de gesteunde versies [ hier ](https://experienceleague.adobe.com/docs/?lang=en).

>[!IMPORTANT]
>
>De Adobe adviseert u [ verbetering aan recentste versie 1.9.20 ](/help/assets/workfront-connector-install.md) van [!DNL Workfront for Experience Manager enhanced connector].

## Bekende problemen {#known-issues}

* Tijdens het configureren van aan projecten gekoppelde mappen met AEM 6.4 slaat Experience Manager de waarden voor **[!UICONTROL sub-folders]** - en **[!UICONTROL Create linked folder in projects with portfolio]** -velden niet op. De waarde voor het veld **[!UICONTROL sub-folders]** wordt automatisch bijgewerkt naar **[!UICONTROL undefined]** en de waarde voor het veld **[!UICONTROL Create linked folder in projects with portfolio]** wordt automatisch bijgewerkt naar **[!UICONTROL Default Portfolio]** nadat de configuratie is opgeslagen.

* Wanneer u de klassieke Workfront-ervaring gebruikt, kunt u met de optie **[!UICONTROL Send to]** in de vervolgkeuzelijst **[!UICONTROL More]** geen doelbestemming in de Experience Manager selecteren. De optie **[!UICONTROL Send to]** werkt correct met de vervolgkeuzelijst **[!UICONTROL Document Actions]** . De optie **[!UICONTROL Send to]** werkt correct voor de vervolgkeuzelijst **[!UICONTROL More]** en de vervolgkeuzelijst **[!UICONTROL Document Actions]** die beschikbaar is in de nieuwe Workfront-ervaring.

## Eerdere versies {#previous-releases}

### Release van april 2024 {#april-2024-release}

* Het niet sluiten van HTTP-clients veroorzaakt problemen met onvoldoende geheugen.


### Release van maart 2024 {#march-2024-release}

* Bij de verwerking van uploads van meerdere bedrijfsmiddelen vanuit Workfront treden problemen op.
* Als u geen afsluitend aanhalingsteken toevoegt wanneer u Workfront gebruikt om naar mappen in Experience Manager te zoeken, resulteert dit in `SERVER_ERROR` .

### Release van februari 2024 {#february-2024-release}

* Schakel schakelfunctie in om AEM Cloud-klanten in staat te stellen een connector te configureren en in te stellen.

* Als u de `resourceResolver` sluit zonder de onderliggende sessie expliciet te sluiten, treedt er een sessilek op in AEM instanties. Het is essentieel om de zitting uitdrukkelijk te sluiten, aangezien auto-sluit de Resolver van het Middel impliciet niet de zitting sluit.

### Release januari 2024 {#january-2024-release}

* In de [!DNL Workfront] -configuratie in [!DNL CRX DE] wordt de `project ID` momenteel niet opgeslagen. Dit leidt tot fouten bij het toepassen van alleen-lezen bevoegdheden. Leer meer over hoe te [ toestemmingen ](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/integrations/workfront-connector-configure.html#linked-folders) vormen.

* Geen openbare documentatie over hoe te om douanebezit aan uit de definitie van de kaderindex toe te voegen. Leer meer over [ toevoegend douanebezit ](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/integrations/workfront-connector-configure.html#metadata-schema-mapping).

* Het verwijderen van verbindingsconfiguraties op de verbeterde connector heeft een aanzienlijke invloed op gebeurtenisabonnementen en andere opgeslagen configuraties, waardoor deze naar een oude URL verwijzen.

* Als u het pakket Formulieren add-on installeert, wordt de **[!UICONTROL Toggle Router]** niet geïnstalleerd, wat leidt tot de fout van de functie [!DNL WFEC AMS environment Toggle] .

* Als u gebeurtenisabonnementen inschakelt op EWC-installatie, treedt er een herhaling van API-aanroepfouten op met `HTTP 400` error wanneer u voor de eerste keer een [!DNL Workfront] verbeterde connector instelt.

* Als u opmerkingen verwijdert over gekoppelde mapelementen in Workfront, wordt het gekoppelde mappad niet AEM.

* Onvoldoende ondersteuning voor grote bestandsmiddelen in AEM resulteert in een probleem met 4-byte bestandsgrootte.

* Geen tijdsverwerking voor aanvragen voor kritieke stromen in gekoppelde map, documentupdate en notitie-update.

### Release november 2023 {#nov-2023-release}

* Wanneer u de lijst met AEM mappen weergeeft, duurt het langer dan een minuut om het dialoogvenster te laden.
* Gemachtigde [!DNL Workfront] -gebruikers ontvangen consistent logboeken met fouten in de verificatie.

### Release oktober 2023 {#october-2023-release}

* Wanneer de gebeurtenisabonnementen onder Geavanceerde Montages onbruikbaar worden gemaakt, kunt u nog de opties selecteren om **aan de gebeurtenissen van de documentupdate toe te wijzen om AEM activa meta-gegevens** bij te werken, **Publish alle projectactiva aan Brand Portal op projectvoltooiing**, en **toe te laten de Synchronisatie van de Commentaar**.

* Sommige elementen die in Experience Manager zijn opgeslagen, worden niet correct gerenderd wanneer u deze in Workfront bekijkt.

* Tijdens het opnieuw configureren van de Experience Manager-verbinding met Workfront, worden gebeurtenisabonnementen zoals synchronisatie van opmerkingen, verwijderen en documentupdate niet gemaakt.

* Belangrijke verbeteringen in de API-prestaties voor het maken, bijwerken, inschakelen van gekoppelde map, inschakelen van synchronisatie met opmerkingen, in- en uitschakelen, instellingen van te voren opslaan op aansluiting.

### Release september 2023 {#september-2023-release}

* De Experience Manager verbeterde schakelaar haalt alle gebeurtenisabonnementen van Workfront terwijl het schrappen van een gebeurtenisabonnement voor een project, dat tot een prestatieseffect op de toepassing leidt.

* Wanneer een element van Workfront naar Experience Manager wordt verzonden, wordt het MIME-type van het element niet ingesteld op `dc:format` -kenmerk binnen de Experience Manager.

* Het project IDs van Workfront die op Experience Manager verbeterde schakelaar wordt opgeslagen omvat duplicaten.

### Release van augustus 2023 {#august-2023-release}

* Kan geen gekoppelde mappen maken in Experience Manager, omdat er geen gebruikersaccount is gekoppeld aan de gekoppelde map.

* De omstandigheden van de ruimte tijdens meta-gegevensupdates voor activa in Experience Manager.

### Release juni 2023 {#june-2023-release}

* Wanneer u geavanceerde netwerken hebt geconfigureerd, zijn er problemen bij het verzenden van inhoud van Adobe Workfront naar AEM as a Cloud Service.


### Release mei 2023 {#may-2023-release}

* Workfront retourneert een 409 HTTP-reactie voor dubbele gebeurtenisabonnementen op basis van een REST-aanroep van Experience Manager naar Workfront. Dit leidt tot een null pointer-uitzondering.

### Release van april 2023 {#april-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.9, die op 10 april 2023 is uitgebracht, bevat de volgende updates:

* Experience Manager geeft een `DateTimeParseException` -uitzondering weer wanneer deze de datum van de laatste wijziging van Workfront ontvangt tijdens het maken van een gekoppelde map.

* Problemen tijdens het maken van meerdere gekoppelde projectmappen binnen een korte periode.

* Kan geen drempellimiet configureren voor het aantal nieuwe set met projectgekoppelde mappen.

### Release van maart 2023 {#march-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.8, uitgebracht op 3 maart 2023, bevat de volgende updates:

* Prestatieverbeteringen in Experience Manager tijdens het maken van projectgekoppelde mappen in Workfront.

* Verwijderingen van opmerkingen in Workfront worden nu weergegeven in de Experience Manager.

* Capability om het blokkeren van net-nieuwe klanten op Experience Manager as a Cloud Service van het vormen van de schakelaar te beheren.

### Release januari 2023 {#january-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.7, uitgebracht op 2 februari 2023, bevat de volgende updates:

* In de metagegevenseditor worden de eigenschappen van aangepaste Workfront-formulieren niet vermeld nadat de versie 1.9.6 is geïnstalleerd.

* Op de Dev-console wordt `/content/dam/jcr:content/metadata/wfProjectURL not found` foutbericht weergegeven nadat de Workfront Enhanced Connector is geïnstalleerd en de startpagina van Assets is geopend.

### Release december 2022 {#december-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.6, uitgebracht op december 2009, bevat de volgende updates:

**Verbetering**

<!--

* Workfront enhanced connector now lets you use new search parameters to be more specific while defining folder names on large repositories.

-->

* Workfront Enhanced Connector ondersteunt nu het uitvoeren van full-text zoekopdrachten op middelen en mappen.

**Bugfixes**

* De metagegevens van de documentversie worden niet correct gesynchroniseerd tussen Workfront en Experience Manager.
* Problemen tijdens het maken van een map die is gekoppeld aan Experience Manager in Workfront wanneer de map een schema gebruikt waarvoor geen definitie in de algemene configuratie beschikbaar is.
* Het schema-editorformulier voor metagegevens reageert niet meer wanneer u op een veld klikt vanwege een laadtijd die langer is dan verwacht. Toegevoegde specifieke configuratie OSGi voor douaneformulieren om de kwestie op te lossen. De namen van de aangepaste formulieren die u toevoegt aan de schema-editor voor metagegevens zijn beschikbaar in de logbestanden.

### Release november 2022 {#november-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.5, die op 11 november is uitgebracht, bevat de volgende updates:

* Wanneer u in Workfront slechts één waarde definieert voor een veld met meerdere waarden, wordt de veldwaarde niet correct toegewezen aan Experience Manager.

* Experience Manager geeft de `SERVER_ERROR` op het **[!UICONTROL Link External Files and Folders]** -scherm weer terwijl de mappen met elementen worden geopend vanwege ongeldige machtigingen voor `/content/dam/collections` .

* Als u de optie **[!UICONTROL Publish Assets to Brand Portal]** inschakelt op de configuratiepagina van de Workfront Enhanced Connector, wordt een onjuiste gebeurtenis gemaakt. De gebeurtenis wordt niet verwijderd, zelfs niet nadat de optie is uitgeschakeld.

  U lost het probleem als volgt op:

   1. Voer een upgrade uit naar versie 1.9.5 van de verbeterde connector.

   1. Schakel de optie **[!UICONTROL Publish Assets to Brand Portal]** uit onder geavanceerde instellingen.

   1. Schakel de optie **[!UICONTROL Publish Assets to Brand Portal]** in.

   1. Verwijder de onjuiste gebeurtenisabonnementen.

      1. Aanroepen van GET uitvoeren naar `/attask/eventsubscription/api/v1/subscriptions?page=<page-number>`

         Eén API-aanroep voor elk paginanummer uitvoeren.

      1. Zoek naar de volgende tekst om gebeurtenisabonnementen te vinden die volgende URL aanpassen en geen `objId` hebben:

         ```
              "objId": "",
             "url": "<your-aem-domain>/bin/workfront-tools/events/linkedfolderprojectupdate<your-aem-domain>/
         ```

         Zorg ervoor dat de inhoud tussen `"objId": "",` en `"url"` overeenkomt met het JSON-antwoord. De geadviseerde methode om dit te doen is van om het even welk Abonnement van de Gebeurtenis te kopiëren dat `objId` heeft en dan het aantal te schrappen.

      1. Noteer de abonnements-id.

      1. Verwijder het verkeerde gebeurtenisabonnement. Maak een Delete API-aanroep aan `<your-aem-domain>/attask/eventsubscription/api/v1/subscriptions/<event-subscription-ID-from-previous-step>`

         `200` als de antwoordcode aangeeft dat onjuiste gebeurtenisabonnementen met succes zijn verwijderd.
  >[!NOTE]
  >
  >Als u reeds de verkeerde gebeurtenisabonnementen vóór het uitvoeren van de stappen hebt geschrapt die in deze procedure worden vermeld, kunt u de laatste stap van deze procedure overslaan.

### Release oktober 2022 {#october-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.4, die in oktober 2007 is uitgebracht, bevat de volgende updates:

* Kan tabblad Gebeurtenisabonnementen niet weergeven op de verbeterde pagina voor schakelaarconfiguratie vanwege vele gebeurtenissen.

* Workfront kan de lijst met bestaande mappen in een project niet ophalen. Dit leidt tot het maken van dubbele mappen.

### Release september 2022 {#september-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.3, uitgebracht op 16 september, bevat de volgende updates:

* Kan geen bestand van meer dan 8 GB uploaden.
* Problemen bij het automatisch publiceren van middelen die van Workfront naar AEM worden verzonden.
* Het veld Basispad is niet beschikbaar voor het veld Codes tijdens het bewerken van een standaardformulier voor een metagegevensschema.
* Problemen tijdens het toevoegen van nieuwe versies in Workfront via AEM workflows.
* Als u een AEM zoekopdracht uitvoert naar middelen die beschikbaar zijn in Workfront, AEM er een foutbericht wordt weergegeven.
* Wanneer u een AEM werkstroom maakt voor het maken van taken op basis van een element en geen bovenliggende taaknaam definieert, wordt de taak niet in Workfront gemaakt.

### Release van augustus 2022 {#august-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.2, die in augustus 2003 is uitgebracht, bevat de volgende updates:

* In de workflowstap **[!UICONTROL Upload Document]** kan geen document aan Workfront worden gekoppeld.

* In de workflowstap **[!UICONTROL Upload Document]** kan geen document worden gekoppeld aan Taken en problemen in Workfront. De werkstroomstap koppelt een document aan Projecten met succes.

### Release juli 2022 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] versie 1.9.1 bevat de volgende updates:

* Toegevoegde ondersteuning voor verificatie tussen Experience Manager- en Workfront-toepassingen met Workfront API-sleutel voor instanties die naar Adobe IMS zijn gemigreerd.

* Wanneer u externe bestanden of mappen koppelt, geeft de Workfront-toepassing het foutbericht `SERVER_ERROR` weer. Het foutbericht verwijst naar een niet-geautoriseerde uitzondering vanwege een onjuiste combinatie van API-sleutels.

* Wanneer u een Create werkstroom van de Taak voor activa uitvoert, toont de Null uitzondering van de Wijzer in de logboekberichten.

* Wanneer u de configuratieoptie `Replace Spaces with DASH` inschakelt onder Geavanceerde instellingen in Experience Manager, resulteert dit in het maken van dubbele mappen in Workfront.

### Release juni 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] bevat nu de volgende updates:

* Wanneer u uploadt via een gekoppelde map of de `Send To` -actie gebruikt die beschikbaar is in Workfront om elementen te uploaden naar Experience Manager as a Cloud Service, worden de elementen beschadigd en kunnen ze niet worden geopend in Adobe Photoshop.

### Release van maart 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] bevat nu de volgende updates:

* U kunt nu gekoppelde mappen maken tussen Adobe Workfront en AEM Assets as a Cloud Service, zelfs als er meerdere aan een project gekoppelde mapconfiguraties zijn.

* Extra ondersteuning voor paginering van abonnementen voor gebeurtenissen.

* Toegevoegde ondersteuning voor AEM 6.4.x.

* Extra ondersteuning voor proxyomgevingen.

* Verscheidene insectenmoeilijke situaties die op partner en klant worden gebaseerd terugkoppelen.

>[!MORELIKETHIS]
>
>* [ integreer  [!DNL Workfront for Experience Manager enhanced connector]  met Experience Manager 6.5 ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
