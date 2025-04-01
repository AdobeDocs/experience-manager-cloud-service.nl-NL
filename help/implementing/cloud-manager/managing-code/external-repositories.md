---
title: Externe opslagplaatsen toevoegen aan Cloud Manager - beperkte bèta
description: Leer hoe u een externe opslagplaats aan Cloud Manager kunt toevoegen. Cloud Manager ondersteunt integratie met GitHub Enterprise Server-, GitLab- en Bitbucket-opslagruimten.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: e18368b1f16033790c91038d746c96d04a05ba21
workflow-type: tm+mt
source-wordcount: '1928'
ht-degree: 0%

---

# Externe opslagplaatsen toevoegen in Cloud Manager - beperkte bèta {#external-repositories}

Leer hoe u een externe opslagplaats aan Cloud Manager kunt toevoegen. Cloud Manager ondersteunt integratie met GitHub Enterprise Server-, GitLab- en Bitbucket-opslagruimten.

>[!NOTE]
>
>Dit kenmerk is alleen beschikbaar via het programma voor vroegtijdige adoptie. Voor meer details en om omhoog als vroege adopter te ondertekenen, zie [ Uw Eigen Git - nu met steun voor GitLab en Bitbucket ](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md#gitlab-bitbucket) brengen.

## Een externe opslagplaats configureren

De configuratie van een externe opslagplaats in Cloud Manager bestaat uit drie stappen:

1. [ voeg een externe bewaarplaats ](#add-external-repo) aan een geselecteerd programma toe.
1. Geef een toegangstoken aan de externe opslagplaats.
1. Valideer eigendom van de privé bewaarplaats GitHub.



## Een externe opslagplaats toevoegen {#add-ext-repo}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma waaraan u een externe bewaarplaats wilt verbinden.

1. In het zijmenu, onder **Programma**, klik ![ het overzichtspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Bewaarplaatsen**.

   ![ de pagina van Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Vlak de hoger-juiste hoek van de **pagina van Bewaarplaatsen**, klik **toevoegen Bewaarplaats**.

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, selecteer **Privé Bewaarplaats** om een externe bewaarplaats van de Bewaarplaats van de Bewaarplaats aan uw programma te verbinden.

   ![ voeg eigen bewaarplaats ](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png) toe

1. Geef in elk veld de volgende gegevens over uw opslagplaats op:

   | Veld | Beschrijving |
   | --- | --- |
   | **Naam van de Bewaarplaats** | Vereist. Een expressieve naam voor uw nieuwe opslagplaats. |
   | **Repository URL** | Vereist. De URL van de gegevensopslagruimte.<br><br> als u een GitHub-ontvangen bewaarplaats gebruikt, moet de weg in `.git` beëindigen.<br> bijvoorbeeld, *`https://github.com/org-name/repo-name.git`* (De weg URL is slechts voor illustratiedoeleinden).<br><br> als u een externe bewaarplaats gebruikt, moet het het volgende URL wegformaat gebruiken:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> of <br>`https://self-hosted-domain/org-name/repo-name.git`<br> en past uw verkoper van het Git aan. |
   | **Uitgezochte Type van Bewaarplaats** | Vereist. Selecteer het type opslagplaats dat u gebruikt:<ul><li>**GitHub** (de Server van de Onderneming van GitHub en de zelf-ontvangen versie van GitHub)</li><li>**GitLab** (zowel `gitlab.com` als de zelf-ontvangen versie van GitLab) </li><li>**Bitbucket** (zowel `bitbucket.org` als de Server van de Bitmap, en de zelf-ontvangen versie van Bitbucket)</li></ul>Als het URL-pad van de repository hierboven de naam van de Git-leverancier bevat, zoals GitLab of Bitbucket, is het repository type al vooraf geselecteerd voor u. |
   | **Beschrijving** | Optioneel. Een gedetailleerde beschrijving van de gegevensopslagruimte. |

1. Selecteer **sparen** om de bewaarplaats toe te voegen.

1. In het **dialoogvakje van de Bevestiging van de Eigendom van de Bewaarplaats 0} Privé, verstrek een toegangstoken om eigendom van de externe bewaarplaats te bevestigen zodat kunt u tot het toegang hebben.**

   ![ Selecterend een bestaand toegangstoken voor een bewaarplaats ](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Selecterend een bestaand toegangstoken voor een bewaarplaats Bitbucket.*

   | Type token | Beschrijving |
   | --- | --- |
   | **het Bestaande Token van de Toegang van het Gebruik** | Als u al een toegangstoken voor de opslagplaats hebt opgegeven voor uw organisatie en toegang hebt tot meerdere opslagplaatsen, kunt u een bestaand token selecteren. Gebruik de **Symbolische Naam** drop-down lijst om het teken te kiezen u op de bewaarplaats wilt toepassen. Anders, voeg een nieuw toegangstoken toe. |
   | **voeg nieuw Token van de Toegang toe** | **type van Bewaarplaats: GitHub**<br><ul><li> Op het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<li>Creeer een persoonlijk toegangstoken door de instructies in de [ documentatie GitHub ](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) te volgen.<li>Stel het volgende in voor de vereiste machtigingen:<ul><li>**Vereiste toestemmingen voor het Token van de Toegang van GitHub Persoonlijke (KLOPJE)**<br> Deze toestemmingen verzekeren dat Cloud Manager trekverzoeken kan bevestigen, statuscontroles, en toegangsnoodzakelijke repo details beheert.<br> in GitHub, wanneer u het persoonlijke toegangstoken (KLOPJE) produceert, zorg ervoor het de volgende bewaarplaatstoestemmingen omvat:<ul><li>Pull request (lezen en schrijven)<li>Statussen vastleggen (lezen en schrijven)<li>Metagegevens opslagplaats (alleen-lezen)</li></li></ul><li>**Vereiste WebHaakgebeurtenissen (voor GitHub-Gehoste bewaarplaatsen)**<br> Deze gebeurtenissen staan Cloud Manager toe om aan activiteit te antwoorden GitHub, zoals trekverzoekbevestiging, op duw-gebaseerde trekkers voor pijpleidingen, of de codesynchronisatie van Edge Delivery Services.<br> wanneer u een Webhaak GitHub manueel vormt, zorg ervoor dat webhaak opstelling is om op de volgende vereiste webhgebeurtenissen teweeg te brengen:<ul><li>Pull-aanvragen<li>Penselen<li>Opmerkingen bij problemen</li></li></li></ul></ul></ul><ul><li>Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |
   | | **type van Bewaarplaats: GitLab**<ul><li>Op het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<li>Creeer een persoonlijk toegangstoken door de instructie in de [ documentatie GitLab ](https://docs.gitlab.com/user/profile/personal_access_tokens/) te volgen.<li>Stel het volgende in voor de vereiste machtigingen:<ul><li>**Vereiste toestemmingen voor het Token van de Toegang van GitLab Persoonlijke (KLOPJE)**<br> Deze werkingsgebieden staan Cloud Manager toe om tot gegevens van de gegevensopslagplaats en gebruikersinformatie zoals nodig voor bevestiging en Web-haintegratie toegang te hebben.<br> wanneer het creëren van het persoonlijke toegangstoken in GitLab, zorg ervoor het de volgende symbolische werkingsgebied omvat:<ul><li>api<li>read_user</li></li></ul><li>**Vereiste WebHaakgebeurtenissen (voor GitLab-Gehoste bewaarplaatsen)**<br> Deze webhgebeurtenissen staan Cloud Manager toe om pijpleidingen teweeg te brengen wanneer de code wordt geduwd of een fusieverzoek wordt voorgelegd. Zij volgen ook commentaren met betrekking tot trekverzoekbevestiging (door nota gebeurtenissen).<br> wanneer u een webhaak in GitLab manueel vormt, zorg ervoor om de volgende vereiste WebHaakgebeurtenissen te omvatten:<ul><li>Push-gebeurtenissen<li>Aanvraaggebeurtenissen samenvoegen<li>Notitie, gebeurtenissen</li></li></li></ul></ul></ul><ul><li>Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |
   | | **type van Bewaarplaats: Bitbucket**<ul><li>Op het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<li>Creeer een toegangstoken van de bewaarplaats gebruikend de [ documentatie Bitbucket ](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<li>Stel het volgende in voor de vereiste machtigingen:<ul><li>**Vereiste toestemmingen voor het Symbolische Token van de Toegang van de Bitmap Persoonlijke (KLOPJE)**<br> Deze toestemmingen staan Cloud Manager toe om tot bewaarplaats inhoud toegang te hebben, trekkingsverzoeken te beheren, en te vormen of op webhaakgebeurtenissen te reageren.<br> wanneer het creëren van het toepassingswachtwoord in Bitbucket, zorg ervoor het de volgende vereiste toestemmingen van het toepassingswachtwoord omvat:<ul><li>Opslagplaats (alleen-lezen)<li>Pull-aanvragen (lezen en schrijven)<li>Webhaken (lezen en schrijven)</li></li></ul><li>**Vereiste WebHaakgebeurtenissen (voor Bitbucket-ontvangen bewaarplaatsen)**<br> Deze gebeurtenissen zorgen ervoor dat Cloud Manager trekverzoeken kan bevestigen, op codeduwen, antwoorden en met commentaren voor pijpleidingscoördinatie in wisselwerking staan.<br> als vestiging de webhaak manueel in Bitbucket, het vormt om op de volgende vereiste WebHaakgebeurtenissen teweeg te brengen:<ul><li>Volledige aanvraag: gemaakt<li>Verzoek tot uittrekken: Bijgewerkt<li>Pull-verzoeken: Samengevoegd<li>Volledige aanvraag: opmerking<li>Repository: Push</li></li></li></ul></ul></ul><ul><li>Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |

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

## Een webhaak configureren voor een externe gegevensopslagruimte {#configure-webhook}

Met Cloud Manager kunt u webhaken configureren voor externe Git-opslagruimten die u hebt toegevoegd. Zie [ een externe bewaarplaats ](#add-ext-repo) toevoegen. Met deze websites kan Cloud Manager gebeurtenissen ontvangen die gerelateerd zijn aan verschillende acties binnen uw Git-leveranciersoplossing.

Met websites kan Cloud Manager bijvoorbeeld acties activeren op basis van gebeurtenissen zoals de volgende:

* Creatie van het volledige verzoek (PR) - initieert de functionaliteit voor PR-validatie.
* Push events - Start pijpleidingen wanneer de trigger &quot;On Git Commit&quot; is ingeschakeld (ingeschakeld).
* Toekomstige op opmerkingen gebaseerde acties - Hiermee worden workflows mogelijk, zoals directe implementatie van een PR, naar een Rapid Development Environment (RDE).

Webhaconfiguratie is niet vereist voor opslagruimten die op `GitHub.com` worden gehost, omdat Cloud Manager rechtstreeks via de GitHub-app integreert.
Voor alle andere externe bewaarplaatsen die met een toegangstoken, zoals de Server van de Onderneming GitHub, GitLab, en Bitbucket worden bezet, is de webhaakconfiguratie beschikbaar en moet opstelling manueel.

**om een webhaak voor een externe bewaarplaats te vormen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma waaraan u een webhaak voor een externe bewaarplaats van het Git wilt vormen.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.

1. In het linkerzijmenu, onder de **rubriek van het Programma**, klik ![ het overzichtspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Bewaarplaatsen**.

1. Op de **pagina van Bewaarplaatsen**, die de **kolom van het Type** gebruikt om u in uw selectie te begeleiden, van de bewaarplaats de plaats bepalen u wilt, dan klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast het.

   ![ de optie Webhaak van Config op drop-down menu voor een geselecteerde bewaarplaats ](/help/implementing/cloud-manager/managing-code/assets/repository-config-webhook.png)

1. Van het drop-down menu, klik **Config Webhaak**.

   ![ vorm de dialoogdoos van Webhaak ](/help/implementing/cloud-manager/managing-code/assets/config-webhook.png)

1. In het **de dialoogvakje van WebHaak van Config**, doe het volgende:

   1. Naast het **gebied van URL van de Webhaak**, klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Plak de URL in een tekstbestand zonder opmaak. De gekopieerde URL is vereist voor de WebHaak-instellingen van uw Git-leverancier.
   1. Naast het **Geheime 1} teken/zeer belangrijke gebied van Webhaak {, klik** **produceren, dan klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).**
Plak het geheim in een tekstbestand zonder opmaak. Het gekopieerde geheim wordt vereist voor de montages Webhaak van uw verkoper van het Git.
1. Klik **dicht**.
1. Navigeer naar uw Git-leveranciersoplossing (GitHub Enterprise, GitLab of Bitbucket).

   Alle details op de webshconfiguratie en de gebeurtenissen die voor elke verkoper worden vereist zijn beschikbaar in [ een externe bewaarplaats ](#add-ext-repo) toevoegen. Zie de tabel onder stap 8.

1. Bepaal de plaats van de sectie van de Montages van Webhaak **** van de oplossing.
1. Plak de URL van de Webhaak die u eerder hebt gekopieerd in het URL-tekstveld.
   1. Vervang de query-parameter `api_key` in de URL van de Webhaak door uw eigen echte API-sleutel.

      Als u een API-sleutel wilt genereren, moet u een integratieproject maken in Adobe Developer Console. Zie [ Creërend een Project van de Integratie API ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) voor volledige details.

1. Plak het Geheim WebHaak dat u vroeger in het **Geheime** (of **Geheime sleutel**, of **Geheime teken**) tekstgebied kopieerde.
1. Configureer de webhaak om de juiste gebeurtenissen te verzenden die Cloud Manager verwacht.


### Validatie van trekkingsverzoeken met webhaken

Nadat websites correct zijn geconfigureerd, activeert Cloud Manager automatisch pijpleidinguitvoeringen of PR-validatiecontroles voor uw opslagplaats.

De volgende gedragingen zijn van toepassing:

* **Server van de Onderneming GitHub**

  Wanneer de controle is gemaakt, lijkt deze op de onderstaande schermafbeelding. Het belangrijkste verschil van `GitHub.com` is dat `GitHub.com` een controle-looppas gebruikt, terwijl de Server van de Onderneming GitHub (die persoonlijke toegangstokens gebruikt) een begaat status produceert:

  ![ verbind status om op de Server van de Onderneming van GitHub het bevestigingsproces van PR te wijzen ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-github-pr-validation.png)

* **Bitbucket**

  Wanneer de validatie van de codekwaliteit wordt uitgevoerd:

  ![ Status terwijl de bevestiging van de codekwaliteit ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket1.png) loopt

  Gebruikt de status commit voor het volgen van voortgang van PR-validatie. In het volgende geval, toont het het schermschot wat gebeurt wanneer een bevestiging van de codekwaliteit wegens een klantenkwestie ontbreekt. Er wordt een opmerking toegevoegd met gedetailleerde foutinformatie en er wordt een commit check gemaakt, die de fout weergeeft (rechts zichtbaar):

  ![ Trek de status van de verzoekbevestiging voor Bitbucket ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket2.png)

* **GitLab**

  GitLab-interacties zijn uitsluitend gebaseerd op opmerkingen. Wanneer de validatie begint, wordt een opmerking toegevoegd. Wanneer de validatie is voltooid (of deze is gelukt of mislukt), wordt de eerste opmerking verwijderd en vervangen door een nieuwe opmerking met validatieresultaten of foutdetails.

  Wanneer de validatie van de codekwaliteit wordt uitgevoerd:

  ![ wanneer de bevestiging van de codekwaliteit ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab1.png) loopt

  Wanneer validatie van koude kwaliteit is voltooid:

  ![ wanneer de koude kwaliteitsbevestiging ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab2.png) wordt gebeëindigd

  Wanneer validatie van de codekwaliteit mislukt vanwege een fout:

  ![ wanneer de bevestiging van de codekwaliteit met een fout ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab3.png) ontbreekt

  Wanneer de validatie van de codekwaliteit mislukt als gevolg van problemen met de klant:

  ![ wanneer de bevestiging van de codekwaliteit wegens klantenkwesties ](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab4.png) ontbreekt


## Problemen met webhaken oplossen

* Zorg ervoor dat de Webhaak-URL een geldige API-sleutel bevat.
* Controleer of webhaakgebeurtenissen correct zijn geconfigureerd in de instellingen van uw Git-leverancier.
* Als de bevestiging van PR of pijpleidingstrekkers niet werken, verifieer dat het Geheime Geheime Web in zowel Cloud Manager als uw verkoper van het Git bijgewerkt is.








## Beperkingen

* Externe opslagplaatsen kunnen niet worden gekoppeld aan configuratiepijpleidingen.
* De pijpleidingen met externe bewaarplaatsen (niet die op GitHub worden ontvangen) en de &quot;Op Veranderingen van de Git&quot;trekker beginnen niet automatisch. Deze kunnen alleen handmatig worden gestart.


<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


