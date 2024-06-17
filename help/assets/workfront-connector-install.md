---
title: Installeren [!DNL Workfront for Experience Manager enhanced connector]
description: Installeren [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Installeren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html) |
| AEM as a Cloud Service | Dit artikel |

Een gebruiker met beheerdertoegang in [!DNL Adobe Experience Manager] als [!DNL Cloud Service] installeert de verbeterde schakelaar. Lees de platformondersteuning en andere informatie voordat u de installatie uitvoert [eerste vereisten voor de aansluiting](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Vanaf juni 2022 heeft Adobe een nieuwe native integratie uitgebracht voor de aansluiting van Workfront op Adobe Experience Manager Assets as a Cloud Service. Deze integratie is de vereiste methode geworden om deze twee oplossingen aan te sluiten. Elke toekomstige nieuwe implementatie van de verbeterde connector (1.9.8 en hoger) voor het aansluiten van Workfront op AEM Assets as a Cloud Service wordt geblokkeerd. Voor meer informatie over hoe te om deze integratie te plaatsen, zie [De as a Cloud Service integratie met Experience Manager Assets configureren](workfront-connector-configure.md).

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services]. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt het niet ondersteund door Adobe.
>
>* Adobe kan updates vrijgeven voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] die deze schakelaar overtollig maken; als dit voorkomt, kunnen de klanten aan overgang van het gebruik van deze schakelaar worden vereist.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Zie stap 5(a) van [Uitgebreide installatie-instructies](workfront-connector-install.md).
>
>* Zie [Partnercertificatieexamen voor Workfront voor verbeterde connector voor Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie [Handleiding voor Examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

Volg de volgende stappen voordat u de aansluiting installeert:

1. Als uw AEM as a Cloud Service Programma Geavanceerde Voorzien van een netwerk heeft gevormd en IP toe:staan-Lijst toegelaten, dan moet u Workfront IPs aan dit toestaan-lijst toevoegen om de Abonnementen van de Gebeurtenis en diverse API vraag toe te laten om in AEM over te gaan.

   * [Workfront Cluster IP&#39;s](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/get-started-administration/configure-your-firewall.html?lang=en#ip-addresses-to-allow-for-clusters-1-2-3-5-7-8-and-9). Om de IP cluster binnen te kennen [!DNL Workfront], navigeer naar **[!UICONTROL Setup]** > **[!UICONTROL System]** > **[!UICONTROL Customer Info]**.

   * [API&#39;s voor Workfront Event Subscription](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-api/event-subscriptions/event-subs-api.html)

   >[!IMPORTANT]
   >
   >* Als u Geavanceerde netwerken hebt geconfigureerd voor uw programma en IP Allow Listing gebruikt, moet u vanwege een beperking met de verbeterde Workfront Connector-architectuur ook de IP van de programmaegress toevoegen aan de allow-list in Cloud Manager.
   >
   >* p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >* Om IP van uw programma te vinden, open een eindvenster en stel een bevel in werking, zoals:
   >
   >    ```
   >    dscacheutil -q host -a name p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >    ```

1. Zorg ervoor dat de volgende overlays niet bestaan in [!DNL Experience Manager] opslagplaats. Als u bestaande overlays op deze paden hebt, moet u de overlays verwijderen of de delta van wijzigingen tussen de twee overlays samenvoegen:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`
   * `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`

1. Deze installatie vereist de kennis om een Maven-project in te stellen [!DNL Experience Manager] als [!DNL Cloud Service]. Gebruik de volgende bronnen om te begrijpen hoe u een pakket van derden kunt opnemen in uw Maven-project:

   * [Een pakket van derden opnemen in uw Maven-project](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [Implementeren met [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html).

De invoegtoepassing installeren in [!DNL Experience Manager] als [!DNL Cloud Service]Voer de volgende stappen uit:

1. Download de verbeterde connector van [Softwaredistributie Adoben](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [Toegang](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) en kloon uw AEM as a Cloud Service opslagplaats uit Cloud Manager.

1. Open de gekloonde AEM as a Cloud Service opslagplaats met behulp van een IDE van uw keuze.

1. Plaats het verbeterde gedownloade schakelaar zip dossier in Stap 1 bij de volgende weg:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Als de `resources` de map bestaat niet. Maak de map.


1. Toevoegen `pom.xml` afhankelijkheid:

   1. Afhankelijkheid in bovenliggend element toevoegen `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
      ```

      >[!NOTE]
      >
      >Zorg ervoor dat u het versienummer van de verbeterde connector bijwerkt voordat u de afhankelijkheid naar de bovenliggende toepassing kopieert `pom.xml`.

   1. Afhankelijkheid toevoegen in `all module pom.xml`.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. Toevoegen `pom.xml` worden ingesloten. Voeg de [!DNL Workfront for Experience Manager enhanced connector] pakketten naar `embeddeds` van de `pom.xml` van al uw subproject. Moet zijn ingesloten in de all-module `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   Het doel van de ingesloten sectie is ingesteld op `/apps/<path-to-project-install-folder>/install`. Dit JCR-pad `/apps/<path-to-project-install-folder>` moet worden opgenomen in de filterregels in de `all/src/main/content/META-INF/vault/filter.xml` bestand. De filterregels voor de gegevensopslagruimte worden gewoonlijk afgeleid van de naam van het programma. Gebruik de naam van de map als doel in de bestaande regels.

1. Breng de wijzigingen aan in de repository.

1. De pijplijn in werking stellen aan [Wijzigingen in Cloud Manager implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

1. Als u een systeemgebruikersconfiguratie wilt maken, maakt u `wf-workfront-users` in [!DNL Experience Manager] Gebruikersgroep en de machtiging toewijzen `jcr:all` tot `/content/dam`. Een systeemgebruiker `workfront-tools` wordt automatisch gemaakt en de vereiste machtigingen worden automatisch beheerd. Alle gebruikers van [!DNL Workfront] die de verbeterde aansluiting gebruiken, worden automatisch toegevoegd als onderdeel van deze groep.

Voor informatie over het bijwerken van de [!DNL Workfront for Experience Manager enhanced connector] van een vorige versie naar de meest recente versie, klikt u op [hier](update-workfront-enhanced-connector.md).

## De verbinding configureren tussen [!DNL Experience Manager] als [!DNL Cloud Service] en [!DNL Workfront] {#configure-connection}

Verbinding maken met [!DNL Workfront]Voer de volgende stappen uit:

1. In [!DNL Experience Manager], selecteert u **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]**.

1. Selecteren `workfront-tools` in het linkerdeelvenster en selecteer **[!UICONTROL Create]** rechtsboven op de pagina.

1. In de **[!UICONTROL Workfront Connection]** de vereiste gegevens over uw [!DNL Workfront] implementatie en selecteer **[!UICONTROL Connect to Workfront]** -optie. Wanneer de verbinding is gelukt, wordt de [!DNL Workfront] aangepaste documentintegratie wordt automatisch gemaakt in het dialoogvenster [!DNL Workfront] milieu.

   ![Verbinden [!DNL Experience Manager] en [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Ga naar de **[!UICONTROL Advanced]** en selecteert u de optie **[!UICONTROL Is the Server AEM as a Cloud Service]**.
