---
title: Een persoonlijke GitHub-opslagplaats toevoegen in Cloud Manager
description: Leer hoe te opstelling Cloud Manager om met uw eigen privé bewaarplaatsen te werken GitHub.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 0%

---

# Een persoonlijke GitHub Cloud-opslagplaats toevoegen in Cloud Manager {#private-repositories}

Door Cloud Manager in te stellen om te integreren met uw persoonlijke GitHub Cloud (repositories die worden gehost op `github.com` ), kunt u uw code direct binnen GitHub valideren met behulp van Cloud Manager. Deze configuratie verwijdert de vereiste om uw code regelmatig te synchroniseren met de Adobe-opslagplaats.

>[!NOTE]
>
>U kunt ook de volgende typen opslagplaatsen toevoegen met webhaken:
>
>* GitHub Enterprise Server (zelfgehoste versie van GitHub)-opslagruimten.
>* GitLab-opslagruimten (zowel `gitlab.com` als zelfgehoste versies van GitLab).
>* Bitbucket (zowel `bitbucket.org` als Bitbucket Server, de zelfgehoste versie van BitBucket) repositories.
>* Azure DevOps (zowel [&#x200B; dev.azure.com &#x200B;](http://dev.azure.com) als zelf-ontvangen versies van Azure DevOps) bewaarplaatsen.
>
>Zie [&#x200B; Externe Bewaarplaatsen in Cloud Manager toevoegen - privé bèta &#x200B;](/help/implementing/cloud-manager/managing-code/external-repositories.md).

<!-- CONSIDER ADDING MORE DETAIL... THE WHY. Some key points about this capability include the following:

* **Direct Integration**: With this setup, you can directly link your private GitHub repositories to Cloud Manager, allowing for seamless code validation, deployment, and CI/CD (Continuous Integration/Continuous Deployment) pipelines without needing to maintain a separate sync process with Adobe's default Git repository.

* **Customization and Autonomy**: Companies often prefer managing their own source code repositories for security, control, and integration purposes. "Build your own GitHub" allows organizations to maintain their internal development processes while leveraging the full functionality of Cloud Manager for building, testing, and deploying AEM (Adobe Experience Manager) applications.

* **Simplified Workflow**: It reduces the overhead of synchronizing code between multiple repositories by allowing Cloud Manager to access the organization's private repository directly, making the development cycle faster and more efficient.

* **CI/CD Pipelines**: Teams can still benefit from Adobe Cloud Manager's automated build, test, and deployment processes, as the integration allows the CI/CD pipelines to pull code from the organization's own GitHub repository.

In essence, a "Build your own GitHub" in Adobe Cloud Manager empowers teams to manage their own GitHub repositories while still using the robust deployment and validation capabilities of Cloud Manager.

>[!NOTE]
>
>This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available. -->

## Configuratie {#configuration}

De configuratie van een persoonlijke GitHub Cloud-opslagplaats in Cloud Manager bestaat uit twee stappen:

1. [&#x200B; voeg een privé bewaarplaats van de Wolk GitHub &#x200B;](#add-repo) aan een geselecteerd programma toe.
1. Dan, [&#x200B; bevestigt eigendom van de privé bewaarplaats van de Wolk GitHub &#x200B;](#validate-ownership).



### Een persoonlijke GitHub Cloud-opslagplaats toevoegen aan een programma {#add-repo}

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma waaraan u een privé bewaarplaats van het Git wilt verbinden.

1. In het zijmenu, onder **Diensten**, uitgezochte ![&#x200B; pictogram van de Omslag &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Bewaarplaatsen**.

   ![&#x200B; de pagina van Bewaarplaatsen &#x200B;](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. Vlak de hoger-juiste hoek van de **pagina van Bewaarplaatsen**, klik **toevoegen Bewaarplaats**.

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, uitgezochte **Privé Bewaarplaats** als bewaarplaatstype.

   ![&#x200B; voeg eigen bewaarplaats &#x200B;](/help/implementing/cloud-manager/assets/repos/add-own-github.png) toe

1. Geef in elk veld de volgende gegevens over uw opslagplaats op:

   | Veld | Beschrijving |
   | --- | --- |
   | Naam opslagplaats | Een expressieve naam voor uw nieuwe opslagplaats. |
   | URL opslagplaats | De URL van de privéopslagplaats, die moet eindigen in `.git`.<br> bijvoorbeeld, *`https://github.com/org-name/repo-name.git`* (De weg URL is slechts voor illustratiedoeleinden). |
   | Beschrijving (optioneel) | Een gedetailleerde beschrijving van de gegevensopslagruimte. |

1. Selecteer **sparen**.
Nu, kunt u [&#x200B; eigendom van de privé bewaarplaats &#x200B;](#validate-ownership) bevestigen.

>[!TIP]
>
>Voor details over het beheren van bewaarplaatsen in Cloud Manager, zie [&#x200B; Bewaarplaatsen van Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/managing-repositories.md).


### Eigendom van een persoonlijke GitHub-opslagplaats valideren {#validate-ownership}

Cloud Manager weet nu van uw bewaarplaats GitHub, maar het heeft nog toegang tot het nodig. Om toegang te verlenen, moet u de toepassing van Adobe GitHub installeren en verifiëren dat u de gespecificeerde bewaarplaats bezit.

**om eigendom van een privé bewaarplaats te bevestigen GitHub:**

1. Na het toevoegen van uw eigen bewaarplaats, volg de resterende stappen in het **Privé de dialoogvakje van de Bevestiging van de Eigendom van de Bewaarplaats van de Bewaarplaats**.

   ![&#x200B; Persoonlijke Bevestiging van de Eigendom van de Bewaarplaats van de Bewaarplaats &#x200B;](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

   |  | Beschrijving |
   | --- | --- |
   | **Stap 1: App GitHub** | Cloud Manager gebruikt een GitHub-app om veilig te communiceren met uw persoonlijke opslagplaats.<br>・ Een eigenaar van uw GitHub-organisatie moet de toepassing in `https://github.com/apps/cloud-manager-for-aem` installeren en toegang verlenen tot de opslagplaats.<br>・ Voor details bij het installeren van en het verlenen van toegang wordt gedaan, zie de documentatie van GitHub. |
   | **Stap 2: Geheime Dossier** | Om de beveiliging te verbeteren, moet u een geheim bestand maken in de standaardvertakking van uw opslagplaats.<br>・ Klik **produceren**, dan klik **bevestigen**. Cloud Manager produceert de inhoud van het privé dossier in het **Geheime dossier inhoud** tekstgebied.<br>・ Klik ![&#x200B; pictogram van het Exemplaar &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) om de inhoud van dat gebied te kopiëren. De inhoud van het geheime bestand wordt slechts eenmaal weergegeven. Als u de inhoud niet kopieert voordat u dit dialoogvenster sluit, moet u het geheim opnieuw genereren. |

1. Creeer een nieuw dossier in de standaardtak van uw geroepen reactie GitHub:

   `.well-known/adobe/cloud-manager-challenge`

1. Plak de geheime bestandsinhoud in het nieuwe bestand dat u zojuist hebt gemaakt en sla het bestand op.

   Als de app is geïnstalleerd en het geheime bestand in de opslagplaats aanwezig is, gaat u verder met de stap.

1. In het **dialoogvakje van de Bevestiging van de Eigendom van de Bewaarplaats 0&rbrace; Privé, klik** Valideren **.**

De app kan worden geïnstalleerd en een geheim bestand kan in elke willekeurige volgorde worden gemaakt. Beide stappen moeten echter zijn voltooid voordat u de validatie kunt uitvoeren.

Tot de validatie wordt de repository weergegeven met een rood pictogram dat aangeeft dat deze nog niet is gevalideerd en nog niet kan worden gebruikt.

![&#x200B; Unvalidate repo &#x200B;](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

De **kolom van het Type** &lbrace;in de lijst op de **pagina van Bewaarplaatsen** identificeert Adobe-Verstrekte bewaarplaatsen (**Adobe**) en uw eigen privé bewaarplaatsen (**GitHub**).

Als u aan de bewaarplaats moet terugkeren later om de bevestiging, op de **pagina van Bewaarplaatsen** te voltooien, klik ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) in de rij die de bewaarplaats vertegenwoordigt GitHub u enkel toevoegde. In de drop-down lijst, uitgezochte **Bevestiging van de Eigendom**.



## Gebruik persoonlijke GitHub Cloud-opslagruimten met Cloud Manager {#using}

Nadat de bewaarplaats GitHub in Cloud Manager wordt bevestigd, is de integratie volledig. U kunt de repository gebruiken met Cloud Manager.

**om privé GitHub Cloud bewaarplaatsen met Cloud Manager te gebruiken:**

1. Wanneer u een trekkingsverzoek creeert, begint een controle GitHub automatisch.

   ![&#x200B; controles GitHub &#x200B;](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Voor elk trekkingsverzoek, wordt de a [&#x200B; volledige pijpleiding van de kwaliteit van de stapelcode &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) automatisch gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

1. De controle GitHub blijft in een lopende staat tot de controle van de codekwaliteit volledig is. De resultaten van de codekwaliteit worden dan verspreid aan de controle GitHub.

   ![&#x200B; GitHub de controles van de codekwaliteit &#x200B;](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wanneer het trekkingsverzoek wordt samengevoegd of gesloten, wordt de volledige pijpleiding van de kwaliteit van de stapelcode gecreeerd automatisch geschrapt.

>[!TIP]
>
>Zie [&#x200B; Annotaties van de Controle GitHub &#x200B;](github-annotations.md) voor details over de informatie die als GitHub wordt verstrekt wanneer de controles van het trekkingsverzoek in werking worden gesteld.

>[!TIP]
>
>U kunt de pijpleidingen controleren die automatisch worden gecreeerd om elk trekkingsverzoek aan een privé bewaarplaats te bevestigen. Zie {de Configuratie van de Controle van 0} GitHub voor Privé Opslagplaatsen [&#x200B; voor meer informatie.](github-check-config.md)



## Private GitHub Cloud-opslagruimten koppelen aan pijpleidingen {#pipelines}

Gevalideerde privé bewaarplaatsen kunnen met [&#x200B; volledig-stapel en frontend pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) worden geassocieerd.



## Beperkingen {#limitations}

Bij het gebruik van persoonlijke opslagruimten met Cloud Manager gelden bepaalde beperkingen.

* Er wordt geen tag Git gemaakt en geduwd wanneer u privéopslagruimten gebruikt bij de productie van volledige stapelleidingen.
* Als Adobe GitHub app wordt verwijderd uit uw organisatie GitHub, verwijdert het de trekrekverzoekbevestigingseigenschap voor alle bewaarplaatsen.
* De pijpleidingen die privé GitHub Cloud-bewaarplaatsen gebruiken en &quot;on-commit&quot;bouwen trekker zijn niet automatisch begonnen wanneer nieuw begaan in de geselecteerde tak wordt geduwd.
* [&#x200B; functionaliteit van het Hergebruik van Artefact &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) is niet op privé bewaarplaatsen van toepassing.
* U kunt niet de bevestiging van het trekkingsverzoek pauzeren gebruikend de controle GitHub van Cloud Manager. Als de bewaarplaats GitHub in Cloud Manager wordt bevestigd, probeert Cloud Manager altijd om de trekkingsverzoeken te bevestigen die voor die bewaarplaats worden gecreeerd.
* Als uw organisatie GitHub IP beperkingen afdwingt, open een steungeval om de lijst van IP adressen te verkrijgen die moeten worden toegestaan.
