---
title: Installeren [!DNL Workfront for Experience Manager enhanced connector]
description: Installeren [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
source-git-commit: 8ca25f86a8d0d61b40deaff0af85e56e438efbdc
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Installeren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Een gebruiker met beheerdertoegang in [!DNL Adobe Experience Manager] als [!DNL Cloud Service] installeert de verbeterde schakelaar. Bekijk voordat u gaat installeren de platformondersteuning en andere [eerste vereisten voor de aansluiting](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe vereist plaatsing en configuratie van [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services]. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt deze niet ondersteund door Adobe.
>
>Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] die deze aansluiting overbodig maken; als dit voorkomt, kunnen de klanten worden vereist om van het gebruik van deze schakelaar over te gaan.

Volg de volgende stappen voordat u de aansluiting installeert:

1. [De firewall configureren](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html). Om de IP cluster binnen te kennen [!DNL Workfront], navigeer naar [!UICONTROL Setup] > [!UICONTROL System] > [!UICONTROL Customer Info].

1. Toestaan dat in de verzender HTTP-headers met de naam `authorization`, `username`, en `apikey`. Toestaan `GET`, `POST`, en `PUT` verzoeken om `/bin/workfront-tools`.

1. Controleer of de volgende paden niet bestaan in [!DNL Experience Manager] opslagplaats:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Deze installatie vereist de kennis om een Maven-project in te stellen [!DNL Experience Manager] als [!DNL Cloud Service]. Gebruik de volgende bronnen om te begrijpen hoe u een pakket van derden kunt opnemen in uw Maven-project:

   * [Een pakket van derden opnemen in uw Maven-project](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [Implementeren met [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html).

De invoegtoepassing installeren in [!DNL Experience Manager] als [!DNL Cloud Service]Voer de volgende stappen uit:

1. Toevoegen `pom.xml` afhankelijkheden:

   1. Afhankelijkheid in bovenliggend element toevoegen `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>1.7.4</version>
      </dependency>
      ```

   1. Een afhankelijkheid toevoegen in alle module [!DNL pom.xml].

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
         </dependency>
      ```

1. Toevoegen `pom.xml` verificatie.

   1. Neem de configuratie van de onderstaande opslagplaats op in de pom.xml in het adobe-public profiel, zodat de verbindingsafhankelijkheden (boven) tijdens de build kunnen worden opgelost (zowel lokaal als door Cloud Manager). Credentials for repository access will be provided when the purchase of a license. De referenties moeten worden toegevoegd aan het bestand settings.xml in de sectie Servers.

      ```XML
      <repository>
         <id>hoodoo-maven</id>
         <name>Hoodoo Repository</name>
         <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
      </repository>
      ```

   1. Een bestand met de naam `./cloudmanager/maven/settings.xml` in de hoofdmap van het project. Voor ondersteuning van een met wachtwoord beveiligde Maven-opslagplaats raadpleegt u [hoe te opstelling uw project](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md). Een voorbeeld `settings.xml` bestand ter referentie. Ten slotte moet u uw lokale `settings.xml` om lokaal te compileren.

      ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
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

1. Als u een systeemgebruikersconfiguratie wilt maken, maakt u `wf-workfront-users` in [!DNL Experience Manager] Gebruikersgroep en de machtiging toewijzen `jcr:all` tot `/content/dam`. Een systeemgebruiker `workfront-tools` wordt automatisch gemaakt en de vereiste machtigingen worden automatisch beheerd. Alle gebruikers van [!DNL Workfront] die de verbeterde aansluiting gebruiken, worden automatisch toegevoegd als onderdeel van deze groep.

## De verbinding configureren tussen [!DNL Experience Manager] als [!DNL Cloud Service] en [!DNL Workfront] {#configure-connection}

Verbinding maken met [!DNL Workfront]Voer de volgende stappen uit:

1. In [!DNL Experience Manager] selecteert u **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]**.

1. Selecteren `workfront-tools` in het linkerdeelvenster en selecteer **[!UICONTROL Create]** in de rechterbovenhoek van de pagina.

1. In de **[!UICONTROL Workfront Connection]** de vereiste gegevens over uw [!DNL Workfront] implementatie en selecteer **[!UICONTROL Connect to Workfront]** optie. Wanneer de verbinding is gelukt, wordt de [!DNL Workfront] aangepaste documentintegratie wordt automatisch gemaakt in het dialoogvenster [!DNL Workfront] milieu.

   ![Verbinden [!DNL Experience Manager] en [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Ga naar de **[!UICONTROL Advanced]** en selecteert u de optie **[!UICONTROL Is the Server AEM as a Cloud Service]**.
