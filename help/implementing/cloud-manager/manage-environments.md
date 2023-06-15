---
title: Omgevingen beheren
description: Leer meer over de typen omgevingen die u kunt maken en hoe u deze kunt maken voor uw Cloud Manager-project.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: e5142052423abee7a2e2ed64affb2b04a93bf0d1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Omgevingen beheren {#managing-environments}

Leer meer over de typen omgevingen die u kunt maken en hoe u deze kunt maken voor uw Cloud Manager-project.

## Omgevingstypen {#environment-types}

Een gebruiker met de vereiste toestemmingen kan de volgende milieutypes (binnen de grenzen van wat aan de specifieke huurder beschikbaar is) tot stand brengen.

* **Productie + werkgebied** - De productie- en testomgevingen zijn als twee beschikbaar en worden respectievelijk voor productie- en testdoeleinden gebruikt.

* **Ontwikkeling** - Er kan een ontwikkelomgeving worden gecreëerd voor zowel ontwikkelings- als testdoeleinden en deze kan alleen worden geassocieerd met niet-productiepijpleidingen.

* **Snelle ontwikkeling** - Een snelle ontwikkelomgeving (RDE) stelt een ontwikkelaar in staat snel wijzigingen te implementeren en te evalueren, waardoor de tijd die nodig is om functies te testen waarvan is aangetoond dat ze werken in een lokale ontwikkelomgeving, tot een minimum wordt beperkt. Zie [documentatie over de snelle ontwikkelomgeving](/help/implementing/developing/introduction/rapid-development-environments.md) voor details over hoe te om RDE te gebruiken.

De mogelijkheden van individuele omgevingen zijn afhankelijk van de oplossingen die in de [programma](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) van het milieu.

* [Sites](/help/sites-cloud/home.md)
* [Assets](/help/assets/home.md)
* [Forms](/help/forms/home.md)
* [Schermen](/help/screens-cloud/home.md)

>[!NOTE]
>
>De productie en het opvoeren milieu&#39;s worden slechts gecreeerd als paar. U kunt niet alleen een testomgeving of alleen een productieomgeving maken.

## Een omgeving toevoegen {#adding-environments}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik op het programma waaraan u een omgeving wilt toevoegen.

1. Van de **Programmaoverzicht** pagina, klik op **Omgeving toevoegen** op de **Omgevingen** kaart om een omgeving toe te voegen.

   ![Milieukaart](assets/no-environments.png)

   * De **Omgeving toevoegen** deze optie is ook beschikbaar op de **Omgevingen** tab.

     ![Het tabblad Omgevingen](assets/environments-tab.png)

   * De **Omgeving toevoegen** Deze optie kan worden uitgeschakeld bij gebrek aan machtigingen of afhankelijk van de gelicentieerde bronnen.

1. In de **Omgeving toevoegen** dialoogvenster dat wordt weergegeven:

   * Selecteer een [**omgevingstype**.](#environment-types)
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes achter de naam van het omgevingstype weergegeven.
   * Een omgeving bieden **Naam**.
   * Een omgeving bieden **Beschrijving**.
   * Als u een **Productie + werkgebied** -omgeving, moet u een omgevingsnaam en -beschrijving opgeven voor zowel uw productie- als staging-omgeving.
   * Selecteer een **Primair gebied** in de vervolgkeuzelijst.
      * Dit kan na het maken niet meer worden gewijzigd.
      * Afhankelijk van uw beschikbare rechten, kunt u kunnen vormen [meerdere gebieden.](#multiple-regions)

   ![Omgevingsdialoogvenster toevoegen](assets/add-environment2.png)

1. Klikken **Opslaan** om de opgegeven omgeving toe te voegen.

De **Overzicht** het scherm toont nu uw nieuwe milieu in **Omgevingen** kaart. U kunt nu pijpleidingen instellen voor uw nieuwe omgeving.

## Meerdere publicatieregio&#39;s {#multiple-regions}

Een gebruiker met de **Zakelijke eigenaar** Met Rol kunt u prod- en staging-omgevingen zodanig configureren dat er naast het primaire gebied maximaal drie extra publicatiegebieden worden opgenomen. Aanvullende publicatiegebieden kunnen de beschikbaarheid verbeteren. Zie de [Aanvullende documentatie voor publicatiegebieden](/help/operations/additional-publish-regions.md) voor meer informatie .

>[!TIP]
>
>U kunt de [Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/api-usage/creating-programs-and-environments/#creating-aem-cloud-service-environments) om een huidige lijst van beschikbare gebieden te vragen.

### Meerdere publicatiegebieden toevoegen aan een nieuwe omgeving {#add-regions}

Wanneer u een nieuwe omgeving toevoegt, kunt u ervoor kiezen om naast het primaire gebied ook andere gebieden te configureren.

1. Selecteer **Primair gebied**.
   * Dit kan niet worden gewijzigd nadat de omgeving is gemaakt.
1. Selecteer de optie **Extra publicatiegebieden toevoegen** en een nieuwe **Aanvullende publicatiegebieden** wordt weergegeven.
1. In de **Aanvullende publicatiegebieden** selecteert u een extra gebied.
1. Het geselecteerde gebied wordt onder de vervolgkeuzelijst toegevoegd om de selectie ervan aan te geven.
   * Tik of klik op de X naast het geselecteerde gebied om de selectie ongedaan te maken.
1. Selecteer een ander gebied in het menu **Aanvullende publicatiegebieden** vervolgkeuzelijst om een ander gebied toe te voegen.
1. Tik of klik op **Opslaan** als u klaar bent om uw omgeving te maken.

![Meerdere gebieden selecteren](assets/select-multiple-regions.png)

De geselecteerde gebieden zijn van toepassing op zowel productie- als testomgevingen.

Als u geen extra gebieden opgeeft, [dat kunt u later doen nadat de omgevingen zijn gemaakt.](#edit-regions)

Indien u een voorziening wenst [geavanceerde netwerken](/help/security/configuring-advanced-networking.md) voor het programma is het raadzaam dit te doen voordat u aanvullende publicatiegebieden toevoegt aan de omgevingen met de API voor Cloud Manager. Anders zal het extra publicatiegebiedsverkeer door de volmacht van het primaire gebied gaan.

### Meerdere publicatiegebieden bewerken {#edit-regions}

Als u in eerste instantie geen extra gebieden hebt opgegeven, kunt u dat doen nadat de omgevingen zijn gemaakt als u over de benodigde rechten beschikt.

U kunt ook extra publicatiegebieden verwijderen. U kunt echter slechts gebieden in één transactie toevoegen of verwijderen. Als u één gebied wilt toevoegen en één gebied wilt verwijderen, voegt u eerst de wijziging toe, slaat u deze op en verwijdert u (of vice versa).

1. Van de console van het Overzicht van het Programma van uw programma, klik de ellipsknoop voor uw productiemilieu en selecteer **Bewerken** in het menu.

   ![Omgeving bewerken](assets/select-edit-environment.png)

1. In de **Productieomgeving bewerken** de benodigde wijzigingen aanbrengen in de aanvullende publicatiegebieden.
   * Gebruik de **Aanvullende publicatiegebieden** vervolgkeuzelijst om extra gebieden te selecteren.
   * Klik op de X naast de geselecteerde aanvullende publicatiegebieden om deze te desselecteren.

   ![Omgeving bewerken](assets/edit-environment.png)

1. Tik of klik op **Opslaan** om de wijzigingen op te slaan.

Wijzigingen in de productieomgeving zijn van toepassing op zowel de productie- als de testomgeving. Wijzigingen in meerdere publicatiegebieden kunnen alleen worden bewerkt in de productieomgeving.

Indien u een voorziening wenst [geavanceerde netwerken](/help/security/configuring-advanced-networking.md) voor het programma is het raadzaam dit te doen voordat u aanvullende publicatiegebieden aan de omgevingen toevoegt . Anders zal het extra publicatiegebiedsverkeer door de volmacht van het primaire gebied gaan.

## Omgevingsdetails {#viewing-environment}

U kunt de **Omgevingen** kaart op de overzichtspagina om op twee manieren toegang te krijgen tot de details van een omgeving.

1. Van de **Overzicht** pagina, klikt u op de **Omgevingen** aan de bovenkant van het scherm.

   ![Het tabblad Omgevingen](assets/environments-tab2.png)

   * U kunt ook op de knop **Alles tonen** op de knop **Omgevingen** kaart om rechtstreeks naar de **Omgevingen** tab.

     ![Alle opties tonen](assets/environment-showall.png)

1. De **Omgevingen** wordt geopend en worden alle omgevingen voor het programma weergegeven.

   ![Het tabblad omgevingen](assets/environment-view-2.png)

1. Klik op een omgeving in de lijst om de details weer te geven.

   ![Omgevingsdetails](assets/environ-preview1.png)

U kunt ook op de knop voor weglatingsteken van de gewenste omgeving klikken en vervolgens **Details weergeven**.

![Omgevingsdetails weergeven](assets/view-environment-details.png)

>[!NOTE]
>
>De **Omgevingen** kaart bevat slechts drie omgevingen. Klik op de knop **Alles tonen** zoals eerder beschreven om alle omgevingen van het programma te zien.

### De voorbeeldservice openen {#access-preview-service}

Cloud Manager biedt een voorbeeldservice (geleverd als een aanvullende publicatieservice) voor elke AEM as a Cloud Service omgeving.

Met de service kunt u de uiteindelijke ervaring van een website voorvertonen voordat deze de daadwerkelijke publicatieomgeving bereikt en openbaar is.

Op verwezenlijking, zal de voorproefdienst een standaardIP lijst van gewenste personen hebben op het wordt toegepast, geëtiketteerd `Preview Default [<envId>]`, die al verkeer aan de voorproefdienst blokkeert. U moet de standaardIP lijst van gewenste personen van de voorproefdienst actief opheffen-toepassen om toegang toe te laten.

![De dienst van de voorproef en zijn lijst van gewenste personen](assets/preview-ip-allow.png)

Een gebruiker met de vereiste machtigingen moet de volgende stappen uitvoeren voordat de URL van de voorbeeldservice wordt gedeeld om ervoor te zorgen dat deze toegankelijk is.

1. Creeer een aangewezen IP lijst van gewenste personen, pas het op de voorproefdienst toe, en unapply onmiddellijk `Preview Default [<envId>]` lijst van gewenste personen.

   * Raadpleeg het document [IP-Lijsten van gewenste personen toepassen en niet toepassen](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) voor meer informatie .

1. De update gebruiken **IP-Lijst van gewenste personen** werkschema om standaardIP te verwijderen en IPs toe te voegen zoals aangewezen. Zie [IP-Lijsten van gewenste personen beheren](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md) voor meer informatie.

Wanneer de toegang tot de voorvertoningsservice is ontgrendeld, wordt het vergrendelingspictogram vóór de naam van de voorvertoningsservice niet meer weergegeven.

Nadat de functie is geactiveerd, kunt u inhoud publiceren naar de voorbeeldservice met behulp van de interface Publicatie beheren in AEM. Raadpleeg het document [Inhoud voorvertonen](/help/sites-cloud/authoring/fundamentals/previewing-content.md) voor meer informatie .

>[!NOTE]
>
>Uw omgeving moet zijn AEM versie `2021.05.5368.20210529T101701Z` of hoger om de voorvertoningsservice te gebruiken. Zorg ervoor dat er een updatepijpleiding op uw omgeving is uitgevoerd om dit te doen.

## Omgevingen bijwerken {#updating-dev-environment}

Als cloudservice worden updates van uw testomgeving en productieomgevingen binnen productieprogramma&#39;s automatisch beheerd door Adobe.

Updates van ontwikkelomgevingen en van omgevingen in sandboxprogramma&#39;s worden echter binnen de programma&#39;s beheerd. Wanneer een dergelijke omgeving niet de meest recente openbaar beschikbare AEM versie uitvoert, wordt de status op de **Omgevingen** kaart op **Overzicht** scherm van het programma wordt weergegeven **Update beschikbaar**.

![Status van update van omgeving](assets/environ-update.png)

### Updates en pijpleidingen {#updates-pipelines}

Pijpleidingen zijn de enige manier om [code in te voeren aan de milieu&#39;s van AEM as a Cloud Service.](deploy-code.md) Om deze reden, wordt elke pijpleiding geassocieerd met een bepaalde AEM versie.

Als de Manager van de Wolk ontdekt dat er een nieuwere versie van AEM beschikbaar is dan die die het laatst met de pijpleiding werd opgesteld, toont het **Update beschikbaar** status voor het milieu.

Het proces van actualisering bestaat daarom uit twee stappen:

1. De pijpleiding bijwerken met de recentste AEM versie
1. De pijpleiding in werking stellen om de nieuwe versie van AEM aan een milieu op te stellen

### Uw omgevingen bijwerken {#updating-your-environments}

De **Bijwerken** Deze optie is beschikbaar via de **Omgevingen** -kaart voor ontwikkelomgevingen en -omgevingen in sandboxprogramma&#39;s door op de knop voor ovaal van de omgeving te klikken.

![Optie bijwerken vanaf de kaart met omgevingen](assets/environ-update2.png)

Deze optie is ook beschikbaar als u op de knop **Omgevingen** van het programma en selecteert u vervolgens de ovaalknop van de omgeving.

![Optie bijwerken op het tabblad Omgevingen](assets/environ-update3.png)

Een gebruiker met de **Implementatiebeheer** rol kan deze optie gebruiken om de pijpleiding verbonden aan dit milieu aan de recentste AEM versie bij te werken.

Zodra de pijpleidingsversie aan de recentste openbaar beschikbare AEM versie wordt bijgewerkt, wordt de gebruiker ertoe aangezet om de bijbehorende pijpleiding in werking te stellen om de recentste versie aan het milieu op te stellen.

![Vragen om pijpleiding in werking te stellen om milieu bij te werken](assets/update-run-pipeline.png)

De **Bijwerken** het gedrag van de optie is afhankelijk van de configuratie en de huidige status van het programma.

* Als de pijpleiding reeds is bijgewerkt, **Bijwerken** de optie zet de gebruiker ertoe aan om de pijpleiding uit te voeren.
* Als de pijpleiding reeds wordt bijgewerkt, **Bijwerken** wordt de gebruiker geïnformeerd dat een update al wordt uitgevoerd.
* Als een geschikte pijpleiding niet wordt gesloten, **Bijwerken** vraagt de gebruiker om er een te maken.

## Ontwikkelomgeving verwijderen {#deleting-environment}

De gebruiker met de vereiste toestemmingen zal een ontwikkelomgeving kunnen schrappen.

Van de **Overzicht** scherm van het programma op het **Omgevingen** -kaart, klikt u op de knop voor weglatingen van de ontwikkelomgeving die u wilt verwijderen.

![De optie Verwijderen](assets/environ-delete.png)

De optie Verwijderen is ook beschikbaar via het dialoogvenster **Omgevingen** tabblad van het dialoogvenster **Overzicht** venster van het programma. Klik op de knop voor weglatingsteken van de omgeving en selecteer **Verwijderen**.

![De verwijderoptie op het tabblad Omgevingen](assets/environ-delete2.png)

>[!NOTE]
>
>* De productie en het opvoeren milieu&#39;s die in een productieprogramma worden gecreeerd kunnen niet worden geschrapt.
>* Productie- en staging-omgevingen in een sandboxprogramma kunnen worden verwijderd.

## Toegang beheren {#managing-access}

Selecteren **Toegang beheren** in het ovaalmenu van de omgeving op het **Omgevingen** kaart. U kunt rechtstreeks naar de instantie van de auteur navigeren en de toegang voor uw omgeving beheren.

![Toegangsoptie beheren](assets/environ-access.png)

>[!TIP]
>
>Zie het document [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md) om te leren hoe AEM as a Cloud Service team en productprofielen toegang tot uw vergunning gegeven oplossingen van de Adobe kunnen verlenen en beperken.

## Toegang tot de ontwikkelaarsconsole {#accessing-developer-console}

Selecteren **Ontwerpconsole** in het ovaalmenu van de omgeving op het **Omgevingen** kaart. Hiermee wordt een nieuw tabblad in uw browser geopend met de aanmeldingspagina voor de **Ontwerpconsole**.

![](assets/environ-devconsole.png)

Alleen een gebruiker met de **Ontwikkelaar** de rol zal toegang hebben tot **Ontwerpconsole**. Voor sandboxprogramma&#39;s heeft elke gebruiker met toegang tot het sandboxprogramma echter toegang tot **Ontwerpconsole**.

Raadpleeg het document [Sluiende en ontsmette zandbakomgevingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html#hibernating-introduction) voor meer informatie .

Deze optie is ook beschikbaar via de **Omgeving** tabblad van het dialoogvenster **Overzicht** venster wanneer u op het ellipsmenu van een afzonderlijke omgeving klikt.

## Lokaal aanmelden {#login-locally}

Selecteren **Lokale aanmelding** in het ovaalmenu van de omgeving in de **Omgevingen** om zich lokaal aan te melden bij Adobe Experience Manager.

![Lokaal aanmelden](assets/environ-login-locally.png)

Bovendien kunt u zich lokaal aanmelden via de **Omgevingen** tabblad van het dialoogvenster **Overzicht** pagina.

![Lokaal aanmelden via tabblad omgevingen](assets/environ-login-locally-2.png)

## Aangepaste domeinnamen beheren {#manage-cdn}

Aangepaste domeinnamen worden ondersteund in de programma&#39;s Cloud Manager for Sites voor zowel publicatie- als voorvertoningsservices. Elke Cloud Manager-omgeving kan maximaal 250 aangepaste domeinen hosten.

Als u aangepaste domeinnamen wilt configureren, navigeert u naar de **Omgevingen** en klik op een omgeving om de omgevingsdetails weer te geven.

![Omgevingsdetails](assets/domain-names.png)

De volgende acties kunnen op de publicatieservice voor uw milieu worden uitgevoerd.

* [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

* [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

* [Status van aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) of [SSL-certificaat](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn).

* [IP-Lijsten van gewenste personen beheren](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn)


## IP-Lijsten van gewenste personen beheren {#manage-ip-allow-lists}

IP-lijsten van gewenste personen worden ondersteund in Cloud Manager voor auteur-, publicatie- en voorvertoningsservices voor Sites-programma&#39;s.

Om IP lijsten van gewenste personen te beheren, navigeer aan **Omgevingen** tabblad van het dialoogvenster **Overzicht** pagina van uw programma. Klik op een afzonderlijke omgeving om de details ervan te beheren.

### Een IP-Lijst van gewenste personen toepassen {#apply-ip-allow-list}

Het toepassen van een IP lijst van gewenste personen associeert alle IP waaiers inbegrepen in de definitie van de lijst van gewenste personen met een auteur of publiceer de dienst in een milieu. Een gebruiker in de **Zakelijke eigenaar** of **Implementatiebeheer** de rol moet worden het programma geopend om een IP lijst van gewenste personen kunnen toepassen.

De IP lijst van gewenste personen moet in de Manager van de Wolk bestaan om het op een milieu toe te passen. Raadpleeg het document voor meer informatie over IP-lijsten van gewenste personen in Cloud Manager[Inleiding tot IP-Lijsten van gewenste personen in Cloud Manager.](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)

Voer de volgende stappen uit om een IP-lijst van gewenste personen toe te passen.

1. Navigeer naar de specifieke omgeving vanuit de **Omgevingen** tabblad van het programma **Overzicht** en navigeer naar het **IP-Lijsten van gewenste personen** tabel.
1. Gebruik de inputgebieden bij de bovenkant van de IP lijst van de lijst van gewenste personen om de IP lijst van gewenste personen en de auteur of de publicatiedienst te selecteren u het wilt toepassen op.
1. Klikken op **Toepassen** en bevestig uw inzending.

### Een IP-Lijst van gewenste personen niet toepassen {#unapply-ip-allow-list}

Wanneer u een IP-lijst van gewenste personen niet toepast, worden alle IP-bereiken die zijn opgenomen in de definitie van de lijst van gewenste personen losgekoppeld van een auteur- of uitgeversservice in een omgeving. Een gebruiker in de **Zakelijke eigenaar** of **Implementatiebeheer** de rol moet worden het programma geopend om een IP lijst van gewenste personen niet-toe te passen.

Voer de volgende stappen uit om een IP-lijst van gewenste personen niet toe te passen.

1. Navigeer naar de specifieke omgeving vanuit de **Omgevingen** tabblad van het programma **Overzicht** en navigeer naar het **IP-Lijsten van gewenste personen** tabel.
1. Identificeer de rij waar de IP regel van de lijst van gewenste personen u wenst om niet-van toepassing te zijn vermeld is.
1. Selecteer de ellipsknop vanaf het einde van de rij.
1. Selecteren **Toepassen ongedaan maken** en bevestig uw inzending.
