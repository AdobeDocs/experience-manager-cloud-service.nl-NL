---
Title: How to configure a SharePoint Site with limited access using authorization scope?
Description: Learn how to configure SharePoint Site with limited access using the authorization scope.
keywords: Hoe te om de Plaats van SharePoint met beperkte toegang te vormen?, vorm SharePoint met beperkte toegang, Gebruikend vergunningswerkingsgebied om toegang voor de Plaats van SharePoint te beperken.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---


<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

# SharePoint-site configureren met beperkte toegang met behulp van machtigingsbereik

Beperkte of beperkte toegang heeft tot doel het beveiligingsbeheer te verbeteren door beheerders de toegang van gebruikers tot een bepaalde SharePoint-site of een groep SharePoint-sites te laten beheren. Het toestemmingsniveau is nuttig wanneer u een gebruiker of groepstoegang tot een specifieke Plaats moet verlenen zonder hen toe te staan om het even welke andere niet-toegestane Plaatsen van SharePoint te bekijken.

## Voordelen om SharePoint Site te configureren met beperkte toegang

Voordelen om beperkte toegang tot de SharePoint-site te bieden:

* **Verbeterde veiligheid**: Door toegang te beperken, kunt u ervoor zorgen dat slechts het gemachtigde personeel de capaciteit heeft om gevoelige informatie te bekijken of te manipuleren, die het risico van onbevoegde toegang verminderen.

* **Beginsel van minst voorrecht**: Het voorziet gebruikers van de minimumniveaus van toegang-of toestemmings-nodig om hun baanfuncties uit te voeren. Dit minimaliseert de blootstelling van elke gebruiker aan gevoelige delen van het netwerk, die tegen potentiële interne bedreigingen kunnen beschermen.

* **de bescherming van Gegevens**: De beperkte toegang helpt in het beschermen van kritieke gegevens tegen blootstelling. Het zorgt ervoor dat alleen gebruikers die de gegevens moeten zien, toegang hebben tot de gegevens, wat essentieel is voor de naleving van de gegevensbeschermingsvoorschriften.

* **Accidental de preventie van gegevensverlies**: Met minder mensen die inhoud kunnen wijzigen, wordt de kans op toevallige schrappingen of veranderingen van belangrijke gegevens beduidend verminderd.

* **Gecontroleerde Stroom van Gegevens**: Het helpt in het controleren van de stroom van informatie binnen en buiten de organisatie, die ervoor zorgt dat de gegevens niet omhoog in de verkeerde handen belanden.

## SharePoint configureren met beperkte toegang met behulp van machtigingsbereik

Voer de onderstaande stappen uit om SharePoint-sites met beperkte toegang te configureren met behulp van het machtigingsbereik:

1. [Maak een toepassing met de ](#create-an-application-with-the-limited-permission-in-the-azure-portal)
1. [Reeks vergunningswerkingsgebied in AEM geval](#set-the-authorization-scope-at-aem-instance)

### Een toepassing maken met de beperkte machtiging in de Azure-portal

Creeer een toepassing in [ Microsoft Azure portaal ](https://portal.azure.com/#home) met het `Sites.Selected` toestemmingswerkingsgebied in de Grafiek API van Microsoft.

![ SharePoint Geselecteerde Plaats ](/help/forms/assets/sharepoint-selected-site.png)

Voor informatie over hoe te om `Client ID` terug te winnen, `Client Secret` en `Tenant ID` voor `OAuth URL`, zie [ Documentatie Microsoft® ](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
* Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html` . Vervang `[author-instance]` door de URL van de instantie Auteur.
* Voeg het bereik voor `offline_access` - en `Sites.Selected` -machtigingen toe in de Microsoft Graph-API om beperkte toegang tot sites te bieden.
* Voor OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

Voor het gebruik van de API-machtiging `Sites.Selected` is een toepassing vereist die is geregistreerd in de Azure-portal en waarvoor de juiste machtigingen zijn ingesteld voor SharePoint Online-sites. Deze instelling zorgt ervoor dat de toepassing over de benodigde toestemming beschikt om te communiceren met de SharePoint-site binnen het gedefinieerde bereik, waardoor de vereiste beperkte toegang wordt geboden.

Verwijs naar het [ blogartikel - ontwikkelt Toepassingen die de toestemmingen Sites.Selected voor SPO plaatsen ](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/develop-applications-that-use-sites-selected-permissions-for-spo/ba-p/3790476) voor instructies bij het ontwikkelen van toepassingen gebruiken die `Sites.Selected` toestemmingen voor de Plaatsen van SharePoint Online gebruiken.

### Reeks vergunningswerkingsgebied in AEM geval

Om een beperkte toegang tot een Microsoft SharePoint-site mogelijk te maken, is het van essentieel belang de reikwijdte van de vergunning correct vast te stellen. Om het vergunningswerkingsgebied te plaatsen en AEM Forms aan uw opslag van Microsoft® SharePoint te verbinden:

1. Ga naar uw **1&rbrace; instantie van de Auteur van AEM Forms >**&#x200B;[!UICONTROL Tools]&#x200B;**>**&#x200B;[!UICONTROL Cloud Services]&#x200B;**>**&#x200B;[!UICONTROL Microsoft® SharePoint]&#x200B;**.**
1. Nadat u de **[!UICONTROL Microsoft® SharePoint]** hebt geselecteerd, wordt u omgeleid naar **[!UICONTROL SharePoint Browser]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]** > **[!UICONTROL SharePoint Document Library]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.

   ![ Toegang van de Plaats van SharePoint de Beperkte ](/help/forms/assets/sharepoint-doc-library-limited-scopes.png)

1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** op. Voor informatie over hoe te om identiteitskaart van de Cliënt en Geheim terug te winnen, zie [ Documentatie Microsoft® ](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).

1. Gebruik OAuth URL als `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

   >[!NOTE]
   >
   > Het **cliënt geheime** gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Voeg de waarde `offline_access Sites.Selected` toe in het veld `Authorization Scope` . Wanneer u het bereik `offline_access Sites.Selected` toevoegt in het tekstvak `Authorization Scope` , wordt het tekstvak `SharePoint Site ID` weergegeven op het scherm.

1. Geef de site-id van SharePoint op. Leren hoe te om identiteitskaart van de Plaats van SharePoint terug te winnen, verwijs naar [ Extra Bytes ](#extra-bytes) sectie.

1. Klik op **[!UICONTROL Check Site Connection]**. Bij een geslaagde verbinding wordt het bericht `Connection Successful` weergegeven.

1. Nu, uitgezochte **>** de Bibliotheek van het Document van SharePoint **>** de Omslag van SharePoint **, om de gegevens te bewaren.**

   >[!NOTE]
   >
   >* Standaard is `forms-ootb-storage-adaptive-forms-submission` aanwezig op geselecteerde SharePoint-site.
   >* Creeer een omslag als `forms-ootb-storage-adaptive-forms-submission`, als niet reeds aanwezig in de `Documents` bibliotheek van de geselecteerde Plaats van SharePoint door **te klikken creeer Omslag**.

Nu, kunt u deze [ configuratie van de Plaatsen van SharePoint voor de voorlegt actie in een Aanpassende Vorm ](/help/forms/configure-submit-action-sharepoint.md#use-sharepoint-document-library-configuration-in-an-adaptive-form-use-sharepoint-configuartion-in-af) gebruiken.

## Extra bytes

U kunt als volgt de waarde van `SharePoint Site ID` ophalen:
1. Ga naar [ de Grafiek APIs van de Ontdekkingsreiziger van Microsoft ](https://developer.microsoft.com/en-us/graph/graph-explorer).
1. Klik in het linkerdeelvenster onder de API&#39;s van `SharePoint Sites` op `Search for a SharePoint site by keyword` .
1. Vervang de tijdelijke aanduiding `contoso` door de werkelijke naam van uw SharePoint-site om de bijbehorende site-id op te halen.

   ![ identiteitskaart van de Bibliotheek van het Document van SharePoint ](/help/forms/assets/sharepoint-site-id.png)

Nadat u op de knop `Run Query` hebt geklikt, wordt de site-id op het scherm weergegeven.