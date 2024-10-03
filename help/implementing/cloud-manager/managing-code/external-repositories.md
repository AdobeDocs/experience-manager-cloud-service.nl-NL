---
title: Externe opslagplaatsen toevoegen in Cloud Manager (Vroege adopter)
description: Leer hoe u een externe opslagplaats aan Cloud Manager kunt toevoegen. Cloud Manager ondersteunt integratie met GitHub-, GitLab- en Bitbucket-opslagruimten.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b90ace2250277005d8ac250c841104c93298a605
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---


# Externe opslagruimten toevoegen in Cloud Manager {#external-repositories}

Leer hoe u een externe opslagplaats aan Cloud Manager kunt toevoegen. Cloud Manager ondersteunt integratie met GitHub-, GitLab- en Bitbucket-opslagruimten.

>[!NOTE]
>
>Deze eigenschap is slechts beschikbaar aan [ het vroege adoptieprogramma ](/help/implementing/cloud-manager/release-notes/current.md#early-adoption).

## Een externe opslagplaats configureren

De configuratie van een externe opslagplaats in Cloud Manager bestaat uit drie stappen:

1. [ voeg een externe bewaarplaats ](#add-external-repo) aan een geselecteerd programma toe.
1. Geef een toegangstoken aan de externe opslagplaats.
1. Valideer eigendom van de privé bewaarplaats GitHub.


## Een externe opslagplaats toevoegen {#add-ext-repo}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma waaraan u een externe bewaarplaats wilt verbinden.

1. In het zijmenu, onder **Diensten**, uitgezochte ![ pictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Bewaarplaatsen**.

   ![ de pagina van Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Vlak de hoger-juiste hoek van de **pagina van Bewaarplaatsen**, klik **toevoegen Bewaarplaats**.

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, selecteer **Privé Bewaarplaats** om een externe bewaarplaats van de Bewaarplaats van de Bewaarplaats aan uw programma te verbinden.

   ![ voeg eigen bewaarplaats ](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png) toe

1. Geef in elk veld de volgende gegevens over uw opslagplaats op:

   | Veld | Beschrijving |
   | --- | --- |
   | **Naam van de Bewaarplaats** | Vereist. Een expressieve naam voor uw nieuwe opslagplaats. |
   | **Repository URL** | Vereist. De URL van de gegevensopslagruimte.<br><br> Als u een door GitHub gehoste gegevensopslagruimte gebruikt, moet het pad eindigen in `.git` .<br> bijvoorbeeld, *`https://github.com/org-name/repo-name.git`* (De weg URL is slechts voor illustratiedoeleinden).<br><br> als u een externe bewaarplaats gebruikt, moet het het volgende URL wegformaat gebruiken:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> of <br>`https://self-hosted-domain/org-name/repo-name.git`<br> en past uw verkoper van het Git aan. |
   | S **verkies het Type van Bewaarplaats** | Vereist. Selecteer het bewaarplaatstype dat u gebruikt: **GitHub**, **GitLab**, of **BitBucket**. Als het URL-pad van de repository hierboven de naam van de Git-leverancier bevat, zoals GitLab of Bitbucket, is het repository type al vooraf geselecteerd voor u. |
   | **Beschrijving** | Optioneel. Een gedetailleerde beschrijving van de gegevensopslagruimte. |

1. Selecteer **sparen** om de bewaarplaats toe te voegen.

1. In het **dialoogvakje van de Bevestiging van de Eigendom van de Bewaarplaats 0} Privé, verstrek een toegangstoken om eigendom van de externe bewaarplaats te bevestigen zodat kunt u tot het toegang hebben.**

   ![ Selecterend een bestaand toegangstoken voor een bewaarplaats ](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Selecterend een bestaand toegangstoken voor een bewaarplaats BitBucket.*

   | Type token | Beschrijving |
   | --- | --- |
   | **het Bestaande Token van de Toegang van het Gebruik** | Als u al een toegangstoken voor de opslagplaats hebt opgegeven voor uw organisatie en toegang hebt tot meerdere opslagplaatsen, kunt u een bestaand token selecteren. Gebruik de **Symbolische Naam** drop-down lijst om het teken te kiezen u op de bewaarplaats wilt toepassen. Anders, voeg een nieuw toegangstoken toe. |
   | **voeg nieuw Token van de Toegang toe** | **type van Bewaarplaats: GitHub**<br>・ In het **Symbolische 3} tekstgebied van de Naam {, typ een naam voor het toegangstoken u creeert.**<br>・ Creeer een persoonlijk toegangstoken door de instructies in de [ documentatie GitHub ](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) te volgen.<br>・ Vereiste machtigingen:<br>  ・ `Read access to metadata` .<br>  ・ `Read and write access to code and pull requests` .<br>・ Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |
   |  | **type van Bewaarplaats: GitLab**<br>・ In het **Symbolische 3} tekstgebied van de Naam van de Naam {, typ een naam voor het toegangstoken u creeert.**<br>・ creeer een persoonlijk toegangstoken door de instructie in de [ documentatie GitLab ](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) te volgen.<br>・ Vereiste machtigingen:<br>  ・ `api`<br>  ・ `read_api`<br>  ・ `read_repository`<br>  ・ `write_repository`<br>・ op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |
   |  | **type van Bewaarplaats: Bitbucket**<br>・ In het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<br>・ creeer een toegangstoken van de bewaarplaats gebruikend de [ documentatie Bitbucket ](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>・ Vereiste machtigingen:<br>  ・ `Read and write access to code and pull requests` . |

   >[!NOTE]
   >
   >De eigenschap **voegt nieuw Token van de Toegang toe** is momenteel in de Vroege fase van Goedkeuren. Er worden aanvullende functies gepland. Als gevolg hiervan kunnen de vereiste machtigingen voor toegangstokens worden gewijzigd. Bovendien kan de gebruikersinterface voor het beheren van tokens worden bijgewerkt, mogelijk met functies zoals de vervaldatums van tokens. En automatische controles om ervoor te zorgen dat tokens die aan bewaarplaatsen zijn gekoppeld geldig blijven.

1. Klik **Valideren**.

Na bevestiging, is de externe bewaarplaats klaar om aan een pijpleiding te gebruiken en te verbinden.

## Koppel een gevalideerde externe opslagruimte aan een pijpleiding {#validate-ext-repo}

1. Een pijplijn toevoegen of bewerken:
   * [Een productiepijplijn toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Niet-productiepijpleidingen toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [Een pijplijn bewerken](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   {de bron van de 0} Opslag van de code van de Pijpleiding en tak van het Git ](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)![
   *voeg de dialoogdoos van de Pijpleiding van de Niet-Productie met geselecteerde bewaarplaats en de tak van het Git toe,*

1. Wanneer het toevoegen van of het uitgeven van een pijpleiding, om de **plaats van de Code van Source** voor uw nieuwe of bestaande pijpleiding te specificeren, verkies de externe bewaarplaats u van de **drop-down lijst van de Bewaarplaats** wilt gebruiken.

1. In de **drop-down lijst van de Tak van 0} Git, selecteer de tak als bron voor de pijpleiding.**

1. Klik **sparen**.


>[!TIP]
>
>Voor details over het beheren van bewaarplaatsen in Cloud Manager, zie [ Bewaarplaatsen van Cloud Manager ](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


## Beperkingen

* Externe opslagplaatsen kunnen niet worden gekoppeld aan configuratiepijpleidingen.
* De pijpleidingen die externe bewaarplaatsen gebruiken (exclusief GitHub-ontvangen bewaarplaatsen) en de **optie[!UICONTROL ** van de Trigger van de Plaatsing **op de Veranderingen van het Git**], de trekkers zijn niet automatisch begonnen. Ze moeten handmatig worden gestart.




