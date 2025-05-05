---
title: Bulk uploaden van Principals naar IMS na gebruik van CTT
description: Overzicht van Bulk uploadt dossiers voor groepen en gebruikers, en hoe te om hen op Admin Console te gebruiken om groepen en gebruikers in IMS tot stand te brengen.
exl-id: 43ebd6f1-1492-461a-8d9b-2b55dcde9052
source-git-commit: b9c739a03b358de7c011e50ddbdd609c90f86b6f
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 0%

---

# Bulk uploaden van Principals naar IMS na gebruik van CTT {#bulk-principal-uploading}

>[!CONTEXTUALHELP]
>id="bulk-principal-uploading"
>title="Bulk uploaden van Principals"
>abstract="Overzicht van Bulk uploadt dossiers voor groepen en gebruikers, en hoe te om hen op Admin Console te gebruiken om groepen en gebruikers in IMS tot stand te brengen."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console-documentatie"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

## Inleiding {#introduction}

Door inhoud naar de cloud te migreren met behulp van CTT en CAM worden groepen gemaakt op de AEM-cloud-instantie, maar kunnen groepen of gebruikers niet in IMS worden geplaatst. Zij moeten in IMS bestaan om behoorlijk door klanten worden beheerd. Gelukkig beschikt de Admin Console over functionaliteit om IMS-groepen en gebruikers in bulk te maken. De CAM-opname helpt dit proces door invoerbestanden op te slaan voor dit bulksgewijze ontwerp, zodat klanten deze Admin Console-actie kunnen voltooien als onderdeel van hun algehele migratieproces. Er worden twee soorten bulkuploadbestanden gemaakt: een voor groepen en een voor gebruikers.

Zie ook [ gebruikers ](https://helpx.adobe.com/enterprise/using/users.html) voor extra details over het beheren van de gebruikers van AEM as a Cloud Service leiden.

## Algemene regels voor het uploaden van bestanden {#rules}

Er zijn een paar algemene richtlijnen voor het bewerken en gebruiken van beide soorten uploadbestanden:

* Beheerders moeten eerst toegang krijgen tot de Admin Console voordat deze instructies kunnen worden opgevolgd.
* Houd er rekening mee dat er verschillende manieren zijn om gebruikers en groepen te maken in IMS.  Zie [ Steun IMS voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/ims-support) om over alle beschikbare opties te leren.  Alleen de Admin Console bulkuploadmethoden worden hier beschreven.
* Er zijn drie mogelijke identiteitstypen in IMS: Adobe ID, Enterprise ID en Federated ID.  De instructies op deze pagina worden verstrekt voor **slechts Adobe ID**.  Als u Enterprise ID of Federated ID moet gebruiken, gelieve te verwijzen naar de volledige [ documentatie van Admin Console ](https://helpx.adobe.com/ca/enterprise/using/admin-console.html) en ook de specifieke documentatie voor [ de BulkGroep van Admin Console uploadt ](https://helpx.adobe.com/ca/enterprise/using/user-groups.html) en [ BulkGebruiker van Admin Console uploadt ](https://helpx.adobe.com/ca/enterprise/using/bulk-upload-users.html).  De specificaties voor de uploadbestanden verschillen enigszins voor deze twee identiteitstypen.
* Als in één CSV-veld meerdere items zijn toegestaan (zoals meerdere productprofielen, meerdere groepen of meerdere beheerders), moeten de items worden opgenomen met dubbele aanhalingstekens en worden gescheiden door een komma, d.w.z. `"profile 1,profile 2"` .

   * Voor dit geval kunnen enkele aanhalingstekens worden gebruikt in plaats van dubbele aanhalingstekens, maar het bewerken van het bestand in Microsoft Excel kan problemen bij het parseren tot gevolg hebben. Als u Excel gebruikt om deze bestanden te bewerken, moet u dubbele aanhalingstekens gebruiken in plaats van enkele aanhalingstekens.

## Bulkgroep uploaden {#group-upload}

#### Gebruik hoofdletters/kleine letters: groepen zijn gemigreerd naar AEM as a Cloud Service, maar deze groepen zijn niet aanwezig in IMS/Admin Console, zodat ze via de Admin Console naar IMS moeten worden geüpload.

Voer de volgende stappen uit om de Admin Console-functionaliteit voor het uploaden van bulkgroepen te gebruiken na het uitvoeren van een CTT/CAM-migratie:
1. Download het bulkgroepsbestand van CAM

   1. In CAM, ga naar **Overdracht van de Inhoud** en selecteer **IngestieBanen**.
   1. Klik de ellips (...) op de lijn van de Opname in kwestie, en kies **belangrijkste samenvatting van de Mening**.
   1. Op de dialoog die verschijnt, selecteert het uitgezochte **Dossier van de Groep van de Bulk** van de dropdown lijst onder **Download een dossier...** en klikt de **Download** knoop.
   1. Sla het CSV-bestand op.

1. Het bulkgroepsbestand bewerken

   * Elke regel vertegenwoordigt een groep die moet worden geüpload en heeft vier velden (de namen van de velden vormen de eerste regel van het bestand):

      * _Naam van de Groep van de Gebruiker_ - de groepsnaam wordt vereist, en kan een maximum van 255 karakters bevatten.  Deze groepsnaam moet gelijk zijn in IMS en AEM
      * _Beschrijving_ - Dit gebied is facultatief, en kan een maximum van 255 karakters bevatten
      * _Admins van de Groep van de Gebruiker_ - minstens één groep admin moet op dit gebied worden omvat. U kunt meerdere beheerders toewijzen door elke beheerder te scheiden met een komma en de lijst binnen aanhalingstekens te plaatsen. De vermelding voor elke beheerder moet het identiteitstype van de gebruiker bevatten, gevolgd door een afbreekstreepje en vervolgens het e-mailadres.  Bijvoorbeeld

        `"Adobe ID-myAdmin@example.com,Adobe ID-myOtherAdmin@example.com"`. Plaats geen spatie na de komma-scheidingsbeheerders. U kunt geen gebruikers (als beheerders) opnemen die momenteel geen deel uitmaken van de organisatie in de Admin Console
      * _Toegewezen Profielen van het Product_ - Dit gebied is facultatief. U kunt meerdere productprofielen toewijzen door elk profiel te scheiden met een komma en de lijst tussen aanhalingstekens te plaatsen. De door u opgenomen productprofielen moeten echter al zijn ingesteld voor de organisatie. Zorg ervoor dat u de naam van het productprofiel opgeeft en niet de naam van het product.  Lidmaatschap van productprofielen die aan een groep zijn toegewezen, wordt overgenomen door alle gebruikers die in die groep zijn geplaatst.  Een productprofiel zoeken:

         1. Ga naar Admin Console
         1. Zoek je product (bijvoorbeeld Adobe Experience Manager as a Cloud Service) en klik erop
         1. Uw omgeving zoeken (instantie) en erop klikken
         1. Maak een lijst met de productprofielen en klik op de profielen voor uw AEM-versie. Het productprofiel is bij de bovenkant, d.w.z., &quot;_de Gebruikers van AEM - auteur - Programma 12345 - Milieu 012345_&quot;.

   * Bij het bewerken van de CSV kunnen sommige toepassingen extra aanhalingstekens toevoegen bij het opslaan, waardoor de verwerking mislukt. Het is een goede gewoonte om de onbewerkte CSV te inspecteren in een eenvoudige teksteditor om ervoor te zorgen dat elk veld slechts één openings- en één afsluitend aanhalingsteken heeft (en dat het geen &quot;slimme aanhalingstekens&quot; mogen zijn).

1. Het bulkgroepsbestand uploaden in de Admin Console

   1. In Admin Console, ga naar **Gebruikers**, toen **Groepen van de Gebruiker**
   1. Klik rechts op de knop &quot;...&quot;. Kies **gebruikersgroepen door CSV** van het menu toevoegen, en kies uw CSV om te uploaden. Klik **uploaden**
   1. U krijgt een antwoord dat CSV wordt geüpload (naar de Admin Console), maar dat nog niet is geïmporteerd naar IMS
   1. Ga naar zelfde &quot;...&quot;menu en kies **de resultaten van de Bulkverrichting**. Het zal u een lijst van bulkupload pogingen tonen, en u vertellen (onder **Status**) of bulkupload verwerking, succesvol is, of ontbroken

      * Eerst wordt de verwerking weergegeven, wat aangeeft dat deze nog niet is voltooid
      * Zodra met succes voltooid, klik op de Verbinding **gebruikersgroepen** toevoegen om een eenvoudig statusbericht voor elke lijn te zien.
      * Als in plaats daarvan het heeft ontbroken, klik op het kleine pictogram onder **Dossier** en het zal een beetje meer informatie over verstrekken waarom het ontbrak.  Er wordt verwezen naar de regelnummers van de groep vanaf rij 1.
1. Gebruik Admin Console om uw wijzigingen te verifiëren.

## Bulksgewijs uploaden en bewerken {#bulk-user}

De Admin Console bevat twee afzonderlijke handelingen voor het uploaden en bewerken van gebruikersgegevens. Hieronder vindt u instructies voor het toevoegen van nieuwe gebruikers aan IMS. De instructies voor het uitgeven van bestaande gebruikers IMS zijn in de volgende sectie genoemd [ BulkGebruiker geeft ](#user-edit) uit.

### Bulkgebruiker uploaden {#user-upload}

#### Hoofdlettergebruik: groepen zijn gemigreerd naar AEM as a Cloud Service en geüpload via Bulk-upload of een andere methode.  Gebruikers zijn mogelijk niet aanwezig in IMS/Admin Console en moeten daarom via de Admin Console worden geüpload en gekoppeld aan hun groepen in IMS.

>[!NOTE]
>
>Een gebruiker zal in het **BulkGebruiker verschijnen uploadt** dossier als het in een groep is die tijdens de zelfde opname wordt opgenomen het dossier van wordt gecreeerd. Het kan ook verschijnen als de gebruiker direct op ACL of KUG van gemigreerde inhoud is, of een lid van een ingebouwde groep of een lokale groep is die op ACL of KUG van de gemigreerde inhoud is. Zie [&#128279;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) van de Migratie van de Groep 0&rbrace; voor meer informatie over deze gevallen.

Voer de volgende stappen uit om de Admin Console-functionaliteit voor bulkupload van gebruikers te gebruiken:

1. Het bulkgebruikersbestand downloaden van CAM
   1. In CAM, ga naar **Overdracht van de Inhoud** en selecteer **IngestieBanen**.
   1. Klik de ellips (...) op de lijn van de Opname in kwestie, en kies **belangrijkste samenvatting van de Mening**.
   1. Op de dialoog die verschijnt, selecteert het **BulkDossier van de Gebruiker** van de dropdown lijst onder **Download een dossier...** en klikt de **Download** knoop.
   1. Het resulterende CSV-bestand opslaan
1. Het bulkgebruikersbestand bewerken
   * Elke regel vertegenwoordigt een gebruiker die moet worden geüpload en heeft vijftien velden (de namen van de velden vormen de eerste regel van het bestand). Sommige velden zijn optioneel en worden hier niet beschreven. Verwijs naar {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format).    De velden zijn:

      * _Type van Identiteit_ - Facultatief.  Indien niet opgegeven, wordt deze gemaakt als een Adobe ID
      * _Gebruikersnaam_ - Facultatief, en niet gebruikt voor uploads van Adobe ID
      * _Domein_ - Facultatief, en niet gebruikt voor uploads van Adobe ID
      * _E-mail_ - Vereist.  Het e-mailadres wordt gebruikt voor verificatie de eerste keer dat de gebruiker zich aanmeldt
      * _Voornaam_ - Facultatief.  Moet worden gebruikt omdat het, met Achternaam, op meerdere plaatsen wordt weergegeven
      * _Familienaam_ - Facultatief.  Moet worden gebruikt omdat het op meerdere plaatsen voorkomt
      * _Code van het Land_ - Facultatief, en niet gebruikt voor uploads van Adobe ID
      * _identiteitskaart_ - Facultatief, en niet gebruikt voor uploads van Adobe ID
      * _Configuraties van het Product_ - Facultatief. Dit veld wordt ook overgenomen van groepen waarvan de gebruiker lid is
      * _Admin Roles_ - Facultatief. Gebruik dit veld als de gebruiker een beheerder is. Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details
      * {de configuraties van 0} Product die _worden beheerd - Facultatief._  Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details.  Dit veld wordt ook overgenomen van groepen waarvan de gebruiker lid is
      * _Groepen van de Gebruiker_ - Facultatief. Een lijst met groepen waaraan de gebruiker als lid moet worden toegewezen. Elke groep moet een bestaande IMS-groep zijn. Wanneer het bulkgebruikersdossier van CAM wordt gedownload, is dit gebied vooraf bevolkt met namen van IMS-Toegelaten groep de gebruiker (direct of indirect) lid van vóór de migratie was
      * _Beheerde Groepen van de Gebruiker_ - Facultatief.  Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details.  Dit veld wordt ook overgenomen van groepen waarvan de gebruiker lid is
      * _Beheerde Producten_ - Facultatief.  Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details.  Dit veld wordt ook overgenomen van groepen waarvan de gebruiker lid is
      * _Geleide Contracten_ - Facultatief.  Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details
      * _Toegang van de Ontwikkelaar_ - Facultatief.  Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details
      * _Auto Toegewezen Producten_ - Facultatief.  Zie {het formaat van 0} BulkGebruiker CSV [&#128279;](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) voor details

   * Bij het bewerken van de CSV kunnen sommige toepassingen extra aanhalingstekens toevoegen bij het opslaan, waardoor de verwerking mislukt. Het is een goede gewoonte om de onbewerkte CSV te inspecteren in een eenvoudige teksteditor om ervoor te zorgen dat elk veld slechts één openings- en één afsluitend aanhalingsteken heeft (en dat dit geen &quot;slimme aanhalingstekens&quot; mogen zijn).

1. Admin Console gebruiken om het bulkgebruikersbestand te importeren

   1. Ga in de Admin Console naar Gebruikers
   1. Klik **toevoegen gebruikers door CSV** knoop
   1. Slepen en neerzetten of Een CSV-bestand voor bulkgebruikers selecteren dat is gedownload van CAM
   1. Klik **uploaden** knoop
   1. U krijgt een antwoord dat CSV (aan Admin Console) wordt geupload, maar het wordt nog niet ingevoerd aan IMS.
   1. Ga naar &quot;...&quot;menu op het recht en kies **de resultaten van de Bulkverrichting**.  Het zal een lijst van bulkupload pogingen, en vertoning (onder **Status**) tonen of bulkupload verwerking, succesvol is, of ontbroken.

      * Eerst wordt de verwerking weergegeven, wat aangeeft dat deze nog niet is voltooid
      * Zodra met succes voltooid, klik op de Verbinding **voegt gebruikers** toe om een eenvoudig statusbericht voor elke lijn te zien
      * Als in plaats daarvan het heeft ontbroken, klik op het kleine pictogram onder **Dossier** en het zal u een beetje meer informatie over geven waarom het ontbrak. Er wordt verwezen naar de nummers van de gebruikersregels vanaf rij 1.

1. Gebruik de Admin Console om uw wijzigingen te verifiëren.

>[!NOTE]
>
>Na een niet-sluiteropname is het mogelijk dat gebruikers die eerder zijn gemigreerd en vervolgens in IMS zijn gemaakt, worden weergegeven in het uploadbestand voor bulkgebruikers. Dat kan om vele redenen. In dit geval mislukt het uploaden van de gebruiker. Probeer in plaats daarvan de gebruiker uit het bestand voor het uploaden van bulkgebruikers te verwijderen en gebruik het bestand voor het bewerken van bulkgebruikers als de gebruiker aan verschillende groepen moet worden toegevoegd, zoals hieronder wordt beschreven.

### Bulkgebruiker bewerken {#user-edit}

#### Hoofdlettergebruik: groepen en gebruikers zijn gemigreerd naar AEM as a Cloud Service en geüpload via uploaden in bulk of op een andere manier. Nu moeten enkele wijzigingen worden aangebracht in meerdere gebruikers tegelijk, zoals ze toevoegen aan een bestaande IMS-groep.

Voer de volgende stappen uit om de Admin Console-functionaliteit voor bulkbewerking te gebruiken:

1. Het bulkgebruikersbestand downloaden vanaf de beheerconsole

   1. Ga in de Admin Console naar Gebruikers
   1. Klik rechts op de knop &quot;...&quot;.  Kies **gebruikersdetails door CSV** van het menu uitgeven
   1. Klik **Malplaatje CSV van de Download** en kies **Huidige Gebruikers**.  Er moet een CSV-bestand worden weergegeven in de map met lokale downloads.

1. Het bulkgebruikersbestand bewerken

   1. Ga in de Admin Console naar Gebruikers
   1. Bewerk het CSV-bestand met een teksteditor (aanbevolen) of een spreadsheettoepassing zoals Excel. Als u een toepassing gebruikt, kunnen onvoorspelbare wijzigingen in de gegevens worden aangebracht. Het wordt daarom aanbevolen dat na alle bewerkingen een teksteditor wordt gebruikt om de opmaak van het bestand te controleren
   1. De beschrijvingen van de velden in dit bestand zijn gelijk aan de bovenstaande, onder Bulk User Upload
   1. Alle gebruikers verwijderen die niet worden bewerkt
   1. Als u het veld Gebruikersgroepen wijzigt, laat u de huidige groepen staan en voegt u zo nodig nieuwe toe. Als u een bestaande groep verwijdert, wordt de gebruiker uit die groep verwijderd in IMS
   1. Bij het bewerken van de CSV kunnen sommige toepassingen extra aanhalingstekens toevoegen bij het opslaan, waardoor de verwerking mislukt. Het is een goede gewoonte om het onbewerkte CSV-bestand te inspecteren in een eenvoudige teksteditor om ervoor te zorgen dat elk veld slechts één aanhalingsteken voor openen en sluiten heeft (en dat dit geen &quot;slimme aanhalingstekens&quot; mogen zijn)

1. Het bulkgebruikersbestand uploaden in de Admin Console

   1. Ga in de Admin Console naar Gebruikers
   1. Klik rechts op de knop &quot;...&quot;. Kies **gebruikersdetails door CSV** van het menu uitgeven
   1. Slepen en neerzetten of het bewerkte CSV-bestand voor bulkgebruikers selecteren
   1. Klik op de knop Uploaden
   1. U krijgt een antwoord dat CSV wordt geüpload (naar de Admin Console), maar dat nog niet is geïmporteerd naar IMS
   1. Ga naar &quot;...&quot;menu op het recht en kies **de resultaten van de Bulkverrichting**. U ziet hier een lijst met uploadpogingen voor grote hoeveelheden en u ziet (onder Status) of de bulkupload is verwerkt, gelukt of mislukt.

      * Eerst wordt de verwerking weergegeven, wat aangeeft dat deze nog niet is voltooid
      * Zodra met succes voltooid, klik op **geef gebruikersdetails** verbinding uit om een eenvoudig statusbericht voor elke lijn te zien
      * Als in plaats daarvan het heeft ontbroken, klik op het kleine pictogram onder **Dossier** en het zal een beetje meer informatie over tonen waarom het ontbrak. Er wordt verwezen naar de nummers van de gebruikersregels vanaf rij 1.

1. Gebruik Admin Console om uw wijzigingen te verifiëren.
