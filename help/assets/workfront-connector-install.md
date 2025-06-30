---
title: Installeren  [!DNL Workfront for Experience Manager enhanced connector]
description: Installeren  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Installeren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html) |
| AEM as a Cloud Service | Dit artikel |

Een gebruiker met beheerderstoegang in [!DNL Adobe Experience Manager] als [!DNL Cloud Service] installeert de verbeterde schakelaar. Alvorens u installeert, herzie de platformsteun en andere [ eerste vereisten voor de schakelaar ](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Vanaf juni 2022 heeft Adobe een nieuwe native integratie uitgebracht voor de aansluiting van Workfront op Adobe Experience Manager Assets as a Cloud Service. Deze integratie is de vereiste methode geworden om deze twee oplossingen aan te sluiten. Elke toekomstige nieuwe implementatie van de verbeterde connector (1.9.8 en hoger) voor de verbinding van Workfront met AEM Assets as a Cloud Service wordt geblokkeerd. Voor meer informatie over hoe te opstelling deze integratie, zie [ de integratie van Experience Manager Assets as a Cloud Service ](workfront-connector-configure.md) vormen.

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] . Indien geïmplementeerd en geconfigureerd zonder een gecertificeerde partner of [!DNL Adobe Professional Services] , wordt dit niet ondersteund door Adobe.
>
>* Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze connector redundant maken. Als dit gebeurt, kunnen klanten worden gevraagd over te stappen van het gebruik van deze connector.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, zie stap 5 (a) van [ verbeterde instructies van de schakelaarinstallatie ](workfront-connector-install.md).
>
>* Zie [ de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar ](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen ](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).[

Volg de volgende stappen voordat u de aansluiting installeert:

1. Als uw AEM as a Cloud Service-programma Advanced Networking heeft geconfigureerd en IP Allow-Listing heeft ingeschakeld, moet u de Workfront IP&#39;s toevoegen aan deze allow-list om het verzenden van abonnementen voor gebeurtenissen en verschillende API-aanroepen toe te staan om door te gaan naar AEM.

   * [ de Cluster IPs van Workfront ](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/get-started-administration/configure-your-firewall.html?lang=en#ip-addresses-to-allow-for-clusters-1-2-3-5-7-8-and-9). Navigeer naar **[!UICONTROL Setup]** > **[!UICONTROL System]** > **[!UICONTROL Customer Info]** om het IP-cluster in [!DNL Workfront] te kennen.

   * [ Abonnement API IPs van de Gebeurtenis van Workfront ](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-api/event-subscriptions/event-subs-api.html)

   >[!IMPORTANT]
   >
   >* Als u Geavanceerde netwerken hebt geconfigureerd voor uw programma en IP Allow Listing gebruikt, moet u vanwege een beperking met de verbeterde Workfront Connector-architectuur ook de IP van de programmaegress toevoegen aan de allow-list in Cloud Manager.
   >
   >* p{PROGRAM_ID} .external.adobeaemcloud.com
   >
   >* Om IP van uw programma te vinden, open een eindvenster en stel een bevel in werking, zoals:
   >
   >    ```
   >    dscacheutil -q host -a name p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >    ```

1. Zorg ervoor dat de volgende overlays niet bestaan in de [!DNL Experience Manager] -opslagplaats. Als u bestaande overlays op deze paden hebt, moet u de overlays verwijderen of de delta van wijzigingen tussen de twee overlays samenvoegen:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`
   * `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`

1. Deze installatie vereist de kennis om een Maven-project in [!DNL Experience Manager] in te stellen als een [!DNL Cloud Service] . Gebruik de volgende bronnen om te begrijpen hoe u een pakket van derden kunt opnemen in uw Maven-project:

   * [ omvat derdepakket in uw Gemaakt project ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [ opstellen met  [!DNL Cloud Manager] ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html).

Voer de volgende stappen uit om de invoegtoepassing in [!DNL Experience Manager] als een [!DNL Cloud Service] te installeren:

1. Download de verbeterde schakelaar van [ de Distributie van de Software van Adobe ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [ Toegang ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) en kloon uw bewaarplaats van AEM as a Cloud Service van Cloud Manager.

1. Open de gekloonde AEM as a Cloud Service-opslagplaats met een IDE van uw keuze.

1. Plaats het verbeterde gedownloade schakelaar zip dossier in Stap 1 bij de volgende weg:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Als de map `resources` niet bestaat, maakt u de map.


1. `pom.xml` afhankelijkheden toevoegen:

   1. Voeg een gebiedsdeel in ouder toe `pom.xml`.

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
      >Zorg ervoor dat u het versienummer van de verbeterde connector bijwerkt voordat u de afhankelijkheid naar het bovenliggende element `pom.xml` kopieert.

   1. Voeg een afhankelijkheid toe in `all module pom.xml`.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. Voeg `pom.xml` insluitingen toe. Voeg de [!DNL Workfront for Experience Manager enhanced connector] pakketten aan `embeddeds` sectie van `pom.xml` van al uw subproject toe. Moet zijn ingesloten in de module all `pom.xml` .

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   Het doel van de ingesloten sectie wordt ingesteld op `/apps/<path-to-project-install-folder>/install` . Dit JCR-pad `/apps/<path-to-project-install-folder>` moet worden opgenomen in de filterregels in het `all/src/main/content/META-INF/vault/filter.xml` -bestand. De filterregels voor de gegevensopslagruimte worden gewoonlijk afgeleid van de naam van het programma. Gebruik de naam van de map als doel in de bestaande regels.

1. Breng de wijzigingen aan in de repository.

1. Stel de pijpleiding in werking om [ de veranderingen in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html) op te stellen.

1. Als u een systeemgebruikersconfiguratie wilt maken, maakt u `wf-workfront-users` in [!DNL Experience Manager] Gebruikersgroep en wijst u de machtiging `jcr:all` toe aan `/content/dam` . Er wordt automatisch een systeemgebruiker `workfront-tools` gemaakt en de vereiste machtigingen worden automatisch beheerd. Alle gebruikers van [!DNL Workfront] die de verbeterde connector gebruiken, worden automatisch toegevoegd als onderdeel van deze groep.

Voor informatie om [!DNL Workfront for Experience Manager enhanced connector] van een vorige versie aan de recentste versie bij te werken, klik [ hier ](update-workfront-enhanced-connector.md).

## De verbinding configureren tussen [!DNL Experience Manager] als een [!DNL Cloud Service] en [!DNL Workfront] {#configure-connection}

Ga als volgt te werk om een verbinding met [!DNL Workfront] te maken:

1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** in [!DNL Experience Manager] .

1. Selecteer `workfront-tools` in het linkerpaneel en selecteer **[!UICONTROL Create]** optie in het hoger-juiste gebied van de pagina.

1. Geef in het dialoogvenster **[!UICONTROL Workfront Connection]** de vereiste details van de [!DNL Workfront] -implementatie op en selecteer de optie **[!UICONTROL Connect to Workfront]** . Zodra de verbinding is gelukt, wordt de aangepaste integratie van het [!DNL Workfront] -document automatisch gemaakt in de [!DNL Workfront] -omgeving.

   ![ Verbinden [!DNL Experience Manager] en [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Navigeer naar het tabblad **[!UICONTROL Advanced]** en selecteer de optie **[!UICONTROL Is the Server AEM as a Cloud Service]** .
