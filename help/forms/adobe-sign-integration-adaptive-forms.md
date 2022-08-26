---
title: Hoe kan Adobe Sign met AEM Forms worden geïntegreerd?
description: Leer hoe u Adobe Sign for configureert [!DNL AEM Forms] as a Cloud Service?
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 28bf3e1c33def6c8a17b39a6bd9abca10faa1bd8
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 0%

---

# Integreren [!DNL Adobe Sign] with [!DNL AEM Forms] as a Cloud Service  {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor Adaptive Forms. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

Normaal [!DNL Adobe Sign] en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Sign] om de goedgekeurde aanvraag te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u [!DNL Adobe Sign] with [!DNL AEM Forms].

Te gebruiken [!DNL Adobe Sign] with [!DNL AEM Forms], configureren [!DNL Adobe Sign] in AEM Cloud Services:

## Vereisten {#prerequisites}

U hebt het volgende nodig om te integreren [!DNL Adobe Sign] with [!DNL AEM Forms]:

* Een actief [Adobe Sign Developer Account](https://acrobat.adobe.com/us/en/sign/developer-form.html).
* An [Adobe Sign API-toepassing](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credentials (client-id en clientgeheim) van [!DNL Adobe Sign] API-toepassing.
* Gebruiken [identieke cryptosleutel](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=en#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur- en publicatieinstanties.
* (Alleen voor verificatie op basis van overheidsidentiteitskaart) [De verificatiemethode inschakelen](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport) voor verificatie met overheidsidentiteitskaart

## Configureren [!DNL Adobe Sign] with [!DNL AEM Forms] {#configure-adobe-sign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit om te vormen [!DNL Adobe Sign] with [!DNL AEM Forms] op de instanties Auteur.

1. Navigeer in AEM Forms-auteurinstantie naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, tikken **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en tikken **[!UICONTROL Create]**. Het leidt tot een configuratiecontainer om Cloud Services op te slaan. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** en open de configuratiecontainer u in de vorige stap creeerde.

   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.

1. Tik op de configuratiepagina op **[!UICONTROL Create]** om [!DNL Adobe Sign] in AEM Forms.
1. In de **[!UICONTROL General]** tabblad van het dialoogvenster **[!UICONTROL Create Adobe Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie en tik **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]** en blader om een **[!UICONTROL Thumbnail]** voor de configuratie.

1. Kopieer de URL in het huidige browservenster naar een laptop. De URL is vereist om te configureren [!DNL Adobe Sign] toepassing met [!DNL AEM Forms] in een latere stap. Tik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Settings]** de **[!UICONTROL OAuth URL]** bevat de standaard-URL. De opmaak van de URL is:

   `https://<shard>/public/oAuth/v2`

   Bijvoorbeeld:
   `https://secure.na1.echosign.com/public/oauth/v2`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   Als u een andere [!DNL Adobe Sign] configuratie voor een Adobe Experience Manager-functie of -component, moet u ervoor zorgen dat alle [!DNL Adobe Sign] Cloud Configurations verwijzen naar hetzelfde segment.

   >[!NOTE]
   >
   > De **Adobe Sign-configuratie maken** pagina geopend. Sluit het bestand niet. U kunt **Client-id** en **Clientgeheim** na het configureren van OAuth-instellingen voor de [!DNL Adobe Sign] zoals beschreven in volgende stappen.


1. OAuth-instellingen configureren voor de [!DNL Adobe Sign] toepassing:

   1. Een browservenster openen en aanmelden bij uw [!DNL Adobe Sign] ontwikkelaarsaccount.
   1. Selecteer de toepassing waarvoor [!DNL AEM Forms]en tikken **[!UICONTROL Configure OAuth for Application]**.
   1. In de **[!UICONTROL Redirect URL]** voegt u de URL toe die u in een vorige stap hebt gekopieerd (Stap 7) en klikt u op **[!UICONTROL Save]**.
   1. Het volgende bereik inschakelen voor de [!DNL Adobe Sign] toepassing en klik **[!UICONTROL Save]**.
   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Voor geleidelijke informatie om montages OAuth voor te vormen [!DNL Adobe Sign] en verkrijgen de toetsen, zie [Auteursinstellingen voor de toepassing configureren](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaarsdocumentatie.

   ![OAuth Config](assets/oauthconfig_new.png)

1. Ga terug naar de **[!UICONTROL Create Adobe Sign Configuration]** pagina. Geef de [**[!UICONTROL Client ID]** (ook toepassings-id genoemd) en **[!UICONTROL Client Secret]**]. Gebruik de [Client-id en clientgeheim van Adobe Sign-toepassing](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) die u in de vorige stap hebt gemaakt.

1. Selecteer **[!UICONTROL Enable Adobe Sign for attachments]** aan een adaptief formulier gekoppelde bestanden toevoegen aan de corresponderende [!DNL Adobe Sign] document verzonden voor ondertekening.

1. Tik op **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Sign] toepassing. Wanneer gevraagd om toegang te bevestigen voor `your developer account`, klik op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn en u [!DNL AEM Forms] om toegang te krijgen tot uw [!DNL Adobe Sign] ontwikkelaarsaccount, een succesbericht dat lijkt op het volgende:

   ![Adobe Sign Cloud-configuratie gelukt](assets/adobe-sign-cloud-configuration-success.png)

1. Tikken **[!UICONTROL Create]** om de [!DNL Adobe Sign] configuratie.

1. Selecteer de configuratie en klik op **[!UICONTROL Publish]**, selecteert u de configuratie en klikt u op **[!UICONTROL Publish]**. De configuratie wordt in overeenkomende publicatieomgevingen gerepliceerd.

1. Herhaal alle bovenstaande stappen op uw ontwikkelaar-, werkgebied- en productieinstanties (al naargelang wat er nog over is) om het configureren te voltooien [!DNL Adobe Sign] with [!DNL AEM Forms] voor uw omgeving.

Nu kunt u [Adobe Sign-velden toevoegen aan een adaptief formulier](working-with-adobe-sign.md). Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service wordt gebruikt toevoegt aan alle Adaptive Forms die voor [!DNL Adobe Sign]. U kunt een configuratiecontainer opgeven op basis van de eigenschappen van een adaptief formulier.

## (Alleen voor AEM workflows) Configureren [!DNL Adobe Sign] planner om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Wanneer u [!DNL Adobe Sign] Workflowstap voor het ondertekenen van een adaptief formulier: het formulier kan door ondertekenaars worden doorgegeven of tegelijkertijd naar alle ondertekenaars worden verzonden, afhankelijk van de configuratie van de workflowstap. [!DNL Adobe Sign] Aangepaste adaptieve Forms worden alleen naar Experience Manager Forms Server verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid.

Standaard worden de [!DNL Adobe Sign] De diensten van de planner controleren (opiniepeilingen) ondertekeningsreactie na om de 24 uur. U kunt het standaardinterval voor uw milieu veranderen.

Als u het standaardinterval wilt wijzigen, geeft u een [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) voor de **sign.status.exp** eigendom van de **Adobe Sign Configuration Service** configuratie.

Bijvoorbeeld, om de configuratieservice dagelijks bij 00:00 am in werking te stellen, plaats **sign.status.exp** eigendom van de **Adobe Sign Configuration Service** te specificeren configuratie `0 0 0 1/1 * ? *`. In het volgende JSON-bestand wordt het voorbeeld weergegeven waarmee de configuratieservice dagelijks om 00:00 uur wordt uitgevoerd:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.

<!-- , perform the following steps:

1. Log in to [!DNL AEM Forms] Server with admin credentials and navigate to **[!UICONTROL Tools]** &gt;**[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   You can also open the following URL in a browser window:
   `https://server/system/console/configMgr`

1. Locate and open the **[!UICONTROL Adobe Sign Configuration Service]** option. Specify a [cron expression](https://en.wikipedia.org/wiki/Cron#CRON_expression) in the **Status Update Scheduler Expression** field and click **Save**. For example, to run the configuration service daily at 00:00 am, specify `0 0 0 1/1 * ? *` in the **Status Update Scheduler Expression** field.

Default interval to sync status of [!DNL Adobe Sign] is now changed. -->

## Verwante artikelen {#related-articles}

* [Adobe Sign gebruiken in een adaptief formulier](working-with-adobe-sign.md)

* [Aanbevolen procedures voor het gebruik van Adobe Sign met Adaptive Forms](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
