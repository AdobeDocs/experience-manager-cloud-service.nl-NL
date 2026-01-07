---
Title: How to Connect AEM Adaptive Forms with Azure SQL Storage
Description: Learn how to configure an Azure SQL Database connection in AEM Forms and integrate it with your Adaptive Forms to store or retrieve data efficiently using JDBC.
Keywords: Azure SQL integration with AEM Forms, Connecting Adaptive Forms to Azure SQL Database, JDBC connection for Azure SQL in AEM Forms, Storing Adaptive Form data in Azure SQL
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 40193d89f2a4ef864a564eb9932403531eaf1ff7
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---

# Een adaptief formulier aansluiten op Azure SQL Storage

Adaptieve Forms in Adobe Experience Manager (AEM) kan integreren met externe databases om gegevens op te slaan of op te halen.
In dit artikel wordt beschreven hoe u een adaptief formulier via AEM as a Cloud Service kunt verbinden met een Azure SQL-database.

> 
> 
> Deze handleiding is van toepassing op AEM as a Cloud Service-omgevingen die geen sandbox zijn en waarvoor geavanceerde netwerkfuncties zijn ingeschakeld.

## Voordelen

De integratie van Adaptive Forms met Azure SQL biedt verschillende voordelen:

* **Realtime gegevensinteractie:** laat levend lezen en het schrijven van gegevens tussen vormen en het Azure gegevensbestand toe.
* **Schaalbaarheid:** Azure SQL verstrekt scalable gegevensbestandprestaties geschikt voor onderneming-vlakke toepassingen.
* **gecentraliseerde gegevensopslag:** houdt vormvoorlegging en opgehaalde gegevens veilig opgeslagen in één centrale plaats.
* **de naleving van de Veiligheid:** Hefboomt ingebouwde netwerk, firewall, en encryptieopties van Azure om veilige mededeling te verzekeren.
* **Cloud-inheemse integratie:** Ideaal voor moderne, wolken-eerste architecturen die AEM as a Cloud Service gebruiken.

## Vereisten

* Creeer [&#x200B; Azure SQL Gegevensbestand &#x200B;](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal) en verzeker **volmachtsverbinding** wordt toegelaten.

  >[!NOTE]
  >
  > Navigeer aan: `Azure Portal → SQL Server → Security → Networking → Connectivity` om **volmachtsverbinding** toe te laten.

  ![&#x200B; creeer Azure Db &#x200B;](/help/forms/assets/create-azure-db.png)

* Laat [&#x200B; Gevorderde voorzien van een netwerk toe dat gebruikend een specifiek uitgang IP &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/dedicated-egress-ip-address) voor het gecreeerde Azure gegevensbestand wordt gevormd.

  >[!NOTE]
  >
  >    Na het toelaten van specifieke uitgang IP. Ga naar `Azure Portal → SQL Server → Security → Networking → Public Access` en voeg IP van de uitgang aan de firewallregels toe.

  ![&#x200B; IP van de Eis &#x200B;](/help/forms/assets/cretae-azure-db-egress-ip.png)

* Plaats haven door:sturen in het wolkenmilieu met:
   * **portOrigin**: Tussen `30000–30999`
   * **portDest**: `1433` (standaardhaven voor Azure SQL)
Bijvoorbeeld: `portOrigin: 30433 → portDest: 1433`

     > 
     > 
     > U kunt contact opnemen met de ondersteuning van Adobe Cloud Manager om het door:sturen van poorten te configureren.


## Stappen voor Connect Adaptive Forms naar Azure SQL

**Step1: De Opslag van de it van AEM as a Cloud Service van de Kloon**

1. Open de opdrachtregel en kies een map waarin u de AEM as a Cloud Service-opslagplaats wilt opslaan, bijvoorbeeld `/cloud-service-repository/` .

1. Voer de onderstaande opdracht uit om de gegevensopslagruimte te klonen:

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **waar om deze informatie te vinden?**

   Voor geleidelijke instructies bij de plaats bepalen van deze details, verwijs naar het artikel van de Liga van de Ervaring van Adobe &quot;[&#x200B; Toegang tot Git &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)&quot;.

   Wanneer de opdracht met succes is voltooid, ziet u een nieuwe map die in uw lokale map is gemaakt. Deze map krijgt de naam van uw toepassing.

1. Open de opslagplaats map in een editor.

**Step2: Voeg Vereiste JARs** toe

Omvat het [&#x200B; SQL bestuurdersgebiedsdeel &#x200B;](https://central.sonatype.com/artifact/com.microsoft.sqlserver/mssql-jdbc/12.8.0.jre11?smo=true) aan het project van AEM via het `all` pakket.:

>[!NOTE]
>
> Om het SQL gebiedsdeel in uw project te omvatten, verwijs naar de [&#x200B; SQL sectie van bestuurdersgebiedsdelen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool#mysql-driver-dependencies).

**Stap 3: Voeg Configuratie JDBC** toe

1. Navigeer naar de volgende map in de `<application folder>` waar de OSGi-configuratie voor de JDBC-pool moet worden geplaatst:

   ```bash
   cd ui.config/src/jcr_root/apps/<application folder>/osgiconfig/config/
   ```

**Stap 4: Creeer het Azure SQL Dossier van de Configuratie van de Verbinding**

1. Maak het bestand:

   ```bash
   com.day.commons.datasource.jdbcpool.JdbcPoolService~<application folder>-sql.cfg.json
   ```

1. Voeg de volgende coderegels toe:

   ```json
   {
   "datasource.name": "azuredbshr",
   "jdbc.driver.class": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
   "jdbc.username": "<azureuser>",
   "jdbc.connection.uri": "jdbc:sqlserver://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30433;database=testdb;user=<azureuser>;password=<azurepassword>;encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;",
   "jdbc.password": "******",
   "jdbc.validation.query": "SELECT 1"
       }
   ```

   > 
   >
   > Vervang `jdbc.username` door de eigenlijke Azure-gebruikersnaam en `jdbc.password` door het werkelijk beveiligde wachtwoord.

**Stap 5: Leg en duw de Veranderingen** vast

Open de terminal en voer de onderstaande opdrachten uit:

```bash
git add .
git commit -m "<commit message>"
git push 
```

**Stap 6: Implementeer de Veranderingen via de Pijpleiding van Cloud Manager**

1. Login aan **AEM Cloud Manager**.
1. Navigeer aan uw project en stel de pijpleiding in werking om de veranderingen op te stellen.

**Stap 7: Creeer een Model van de Gegevens van de Vorm (FDM)**

Zodra de installatie van AEM en Azure is voltooid en de codewijzigingen zijn geïmplementeerd:

1. Ga naar AEM Author-instantie.
1. Navigeer aan **Hulpmiddelen** > **Forms** > **Integraties van Gegevens**.
1. Creeer nieuw **Model van de Gegevens van de Vorm**.
1. In het **lusje van Gegevensbronnen**, selecteer de gecreeerde configuratie JDBC.
1. Klik op **[!UICONTROL Create]** en controleer de verbinding.

![&#x200B; creeer het Model van de Gegevens van de Vorm &#x200B;](/help/forms/assets/create-azure-sql-fdm.png)

**Stap 8: Gebruik gecreeerde FDM in een Aangepaste Vorm**

1. Open een adaptief formulier in de bewerkingsmodus.
1. Selecteer de FDM die in de vorige stap als gegevensmodel is gemaakt.
1. De gegevensbindingen van het gebruik [&#x200B; om vormgebieden met de Azure SQL gegevensbron &#x200B;](/help/forms/work-with-form-data-model.md#add-data-model-objects-and-services) te verbinden en voorleggingsactie te vormen.

## Aanbevolen procedures

* Het geheime beheer van het gebruik **&#x200B;**&#x200B;om hardcoding wachtwoorden in configuratiedossiers te vermijden.
* Regelmatig roteer gegevensbestandgeloofsbrieven en werk veilig config bij.
* De verbindingslogboeken van JDBC van de monitor voor mislukkingen en latentie.
* Volg Azure beste praktijken voor het beveiligen van SQL gegevensbestanden en firewallconfiguraties.
* Gebruik geen databaserekeningen met hoge bevoegdheden voor toegang tot formulieren.

## Verwante artikelen

{{af-submit-action}}