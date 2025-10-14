---
title: Het gereedschap Inhoud overbrengen uitvoeren op een Publish-instantie
description: Het gereedschap Inhoud overbrengen uitvoeren op een Publish-instantie
exl-id: 01faab94-a939-4004-b094-e9eb8f67b96e
feature: Migration
role: Admin
source-git-commit: 4408f15ef85d0fc2c6a0e2b45038dc900d212187
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Het gereedschap Inhoud overbrengen uitvoeren op een Publish-instantie {#run-content-transfer-tool-publish-instance}

## Inleiding {#introduction}

Met het gereedschap Inhoud overbrengen (CTT) kunt u geen inhoudanalyse uitvoeren voordat u inhoud van de broninstantie naar de doelinstantie overbrengt. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een Publish-omgeving. De inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. Een gebruiker heeft de mogelijkheid om een migratieset in te voeren in een Author-instantie, een Publish-instantie of beide.

>[!NOTE]
>Het wordt aanbevolen om tijdens het verplaatsen van inhoud naar een instantie Production Content Transfer Tool te installeren op de instantie van de bronauteur om inhoud naar de instantie van de doelauteur te verplaatsen en op dezelfde manier Content Transfer Tool op de Publish-broninstantie te installeren om inhoud naar de Publish-doelinstantie te verplaatsen. Zie [&#x200B; Aanbevolen Benadering &#x200B;](#recommended-approach) hieronder sectie voor meer details.

## Aanbevolen aanpak {#recommended-approach}

Volg de onderstaande aanbevolen aanpak:

* Gebruik dezelfde versie van het gereedschap Inhoud overbrengen die ook voor de instantie Auteur is gebruikt.

* Er mag slechts één publicatieknooppunt worden gemigreerd. Deze moet uit het taakverdelingsmechanisme worden verwijderd voordat de extractie wordt gestart.

* Tijdens het publiceren wordt de publicatielaag niet verkleind (in tegenstelling tot de auteur).

  >[!IMPORTANT]
  >Als voorzorgsmaatregel, vermijd om het even welke gebruiker in werking gestelde schrijven verrichtingen, zoals:
  > * Distributie van inhoud van AEM as a Cloud Service Author naar Publish in die omgeving
  > * Gebruikerssynchronisatie tussen publicatie-instanties
