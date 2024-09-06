---
title: Persoonlijke opslagplaatsen toevoegen in Cloud Manager
description: Leer hoe te opstelling Cloud Manager om met uw eigen privé bewaarplaatsen te werken GitHub.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Persoonlijke opslagplaatsen toevoegen in Cloud Manager {#private-repositories}

Door Cloud Manager te vormen om met uw eigen privé bewaarplaatsen te werken GitHub, kunt u uw code direct binnen uw bewaarplaats GitHub door Cloud Manager bevestigen, die de behoefte elimineert om uw code met de bewaarplaats van de Adobe constant te synchroniseren.

>[!NOTE]
>
>Deze eigenschap is exclusief aan openbare GitHub. De steun voor zelf-ontvangen GitHub is niet beschikbaar.

## Configuratie {#configuration}

De configuratie bestaat uit twee hoofdstappen:

1. [Opslagplaats toevoegen](#add-repo)
1. [Eigendom van privéopslagplaats valideren](#validate-ownership)

### Opslagplaats toevoegen {#add-repo}

1. In Cloud Manager, van de **pagina van het Overzicht van het Programma**, selecteer het **lusje van Bewaarplaatsen** om aan de **pagina van Bewaarplaatsen** te schakelen en **te klikken voeg Bewaarplaats** toe.

1. In **voeg de dialoog van de Bewaarplaats** toe, selecteer **Privé Bewaarplaats** als bewaarplaatstype.

1. Geef de gegevens van uw opslagplaats op

   * **Naam van de Bewaarplaats** - een expressieve naam
   * **Repository URL** - URL van de bewaarplaats, die in `.git` moet beëindigen
   * **Beschrijving** (facultatief) - een langere beschrijving van de bewaarplaats zonodig

   ![ voeg eigen bewaarplaats ](/help/implementing/cloud-manager/assets/repos/add-own-github.png) toe

1. Selecteer **sparen**.

>[!TIP]
>
>Voor details over het beheren van bewaarplaatsen in Cloud Manager, zie [ Bewaarplaatsen van Cloud Manager ](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

### Eigendom van privéopslagplaats valideren {#validate-ownership}

Cloud Manager weet nu van uw bewaarplaats GitHub, maar het heeft nog toegang tot het nodig. Om toegang te verlenen, moet u de Adobe toepassing GitHub installeren en verifiëren dat u de gespecificeerde bewaarplaats bezit.

1. Na het toevoegen van uw eigen bewaarplaats, opent de **dialoog van de Bevestiging van de Eigendom van de Bewaarplaats 0} Privé {.**

   ![ Persoonlijke Bevestiging van de Eigendom van de Bewaarplaats van de Bewaarplaats ](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Cloud Manager gebruikt een GitHub-app om veilig te communiceren met uw opslagplaats.
   * Een eigenaar van uw GitHub-organisatie moet de toepassing in `https://github.com/apps/cloud-manager-for-aem` installeren en toegang verlenen tot de opslagplaats.
   * Zie de documentatie van GitHub voor details over hoe dit wordt gedaan.

1. Om de beveiliging te verbeteren, moet u een geheim bestand maken in de standaardvertakking van uw opslagplaats. Selecteer **produceren**.

1. Bevestig de generatie van het geheime dossier door te tikken of **te klikken bevestigt**.

   ![ bevestigt geheime generatie ](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. Terug in het **venster van de Bevestiging van de Eigenaar van de Bewaarplaats van de 1} Privé van de Bewaarplaats**, heeft Cloud Manager de inhoud van het privé dossier in het **Geheime gebied van de dossierinhoud** geproduceerd. Kopieer de inhoud van dat veld.

   * De inhoud van het geheime bestand wordt slechts eenmaal weergegeven. Als u de inhoud niet kopieert voordat u dit venster sluit, moet u het geheim opnieuw genereren.

   ![ het geheime dossierinhoud van het Exemplaar ](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. Maak een nieuw bestand in de standaardvertakking van uw GitHub-repo met de naam `.well-known/adobe/cloud-manager-challenge` en plak de geheime bestandsinhoud in dat bestand en sla dit op.

1. Zodra app wordt geïnstalleerd en het geheime dossier in de bewaarplaats bestaat, kunt u **selecteren bevestigt** in de **Privé dialoog van de Bevestiging van de Eigendom van de Bewaarplaats van de Bewaarplaats**.

De app kan worden geïnstalleerd en een geheim bestand kan in elke willekeurige volgorde worden gemaakt. Beide stappen moeten echter worden uitgevoerd voordat u de validatie kunt uitvoeren.

Tot de validatie wordt de repository weergegeven met een rood pictogram dat aangeeft dat het nog niet is gevalideerd en nog niet kan worden gebruikt.

![ Unvalidate repo ](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

De **kolom van het Type** {identificeert gemakkelijk Adobe-verstrekte bewaarplaatsen (**Adobe**) en uw eigen bewaarplaatsen GitHub (**GitHub**).

Als u aan de bewaarplaats op een recentere datum moet terugkeren om de bevestiging te voltooien, op de **pagina van Bewaarplaatsen**, selecteer de ellipsis knoop in de rij die de bewaarplaats vertegenwoordigt GitHub u enkel toevoegde en **Bevestiging van de Eigendom** van het drop-down menu selecteert.

## Persoonlijke opslagplaatsen gebruiken met Cloud Manager {#using}

Nadat de bewaarplaats GitHub in Cloud Manager wordt bevestigd wordt de integratie voltooid en u kunt de bewaarplaats met Cloud Manager gebruiken.

1. Wanneer u een trekkingsverzoek creeert, zal een controle GitHub automatisch beginnen.

   ![ controles GitHub ](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. Voor elk trektrekkingsverzoek, zal de a [ volledige pijpleiding van de kwaliteit van de stapelcode ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) automatisch worden gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

1. De controle GitHub blijft in een lopende staat tot de controles van de codekwaliteit volledig. De resultaten van de codekwaliteit zullen dan aan de controle worden verspreid GitHub.

   ![ GitHub de controles van de codekwaliteit ](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

Wanneer het trekkingsverzoek wordt gesloten of samengevoegd, wordt de volledige pijpleiding van de kwaliteit van de stapelcode gecreeerd automatisch geschrapt.

>[!TIP]
>
>Zie de Annotaties van de Controle van het document [ GitHub ](github-annotations.md) voor details over de informatie die via GitHub wordt verstrekt wanneer de controles van het trekkingsverzoek in werking worden gesteld.

>[!TIP]
>
>U kunt de pijpleidingen controleren die automatisch worden gecreeerd om elk trekkingsverzoek aan een privé bewaarplaats te bevestigen. Gelieve te zien de Configuratie van de Controle van het document [ GitHub voor Privé Bewaarplaatsen ](github-check-config.md) voor meer informatie.

## Particuliere opslagplaatsen koppelen aan pijpleidingen {#pipelines}

Gevalideerde privé bewaarplaatsen kunnen met [ volledig-stapel en frontend pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) worden geassocieerd.

>[!NOTE]
>
>De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen.

## Beperkingen {#limitations}

Bij het gebruik van persoonlijke opslagruimten met Cloud Manager gelden bepaalde beperkingen.

* U kunt niet de bevestiging van het trekkingsverzoek pauzeren gebruikend de controle GitHub van Cloud Manager.
   * Als de bewaarplaats GitHub in Cloud Manager wordt bevestigd, zal Cloud Manager altijd proberen om de trekkingsverzoeken te bevestigen die voor die bewaarplaats worden gecreeerd.
* Als de Adobe GitHub app wordt verwijderd uit uw organisatie GitHb, zal dit de trekrekverzoekbevestigingseigenschap voor alle bewaarplaatsen verwijderen.
* De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen.
* Er wordt geen tag git aangemaakt en geduwd wanneer particuliere opslagruimten worden gebruikt voor de productie van volledige stapelleidingen.
* De pijpleidingen die privé bewaarplaatsen gebruiken en de aanzetmachine op-verbind zijn niet automatisch begonnen wanneer nieuw verbindt in de geselecteerde tak wordt geduwd.
* [ functionaliteit van het Hergebruik van Artefact ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) is niet op privé bewaarplaatsen van toepassing.
