---
title: Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie
description: Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie
source-git-commit: 27e68cd282414da4cc23c3ba276b0fb3c330d49c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Het gereedschap Inhoud overbrengen uitvoeren op een publicatie-instantie {#run-content-transfer-tool-publish-instance}

## Inleiding {#introduction}

Met het CTT-hulpprogramma (Content Transfer Tool) wordt geen inhoudanalyse uitgevoerd voordat inhoud van de broninstantie naar de doelinstantie wordt overgebracht. CTT maakt bijvoorbeeld geen onderscheid tussen gepubliceerde en niet-gepubliceerde inhoud wanneer inhoud wordt ingesloten in een publicatieomgeving. Alle inhoud die in de migratieset wordt opgegeven, wordt in de gekozen doelinstantie opgenomen. De gebruiker heeft de capaciteit om een migratie in te voeren die in een instantie Auteur of Publish of beide wordt geplaatst. Men adviseert dat terwijl het bewegen van inhoud naar een instantie van de Productie, CTT op de instantie van de bronauteur moet worden geïnstalleerd om inhoud naar de instantie van de doelauteur te verplaatsen en zo ook, CTT op de bron te installeren publiceer instantie om inhoud naar het doel te verplaatsen publiceer instantie.

>[!NOTE]
>Het wordt aanbevolen dat tijdens het verplaatsen van inhoud naar een instantie Publish het gereedschap Content Transfer op de instantie source Publish wordt geïnstalleerd om inhoud naar de instantie target Publish te verplaatsen. Zie [Aanbevolen aanpak](#recommended-approach) hieronder voor meer informatie.

## Aanbevolen aanpak {#recommended-approach}

Volg de onderstaande aanbevolen aanpak:

* Gebruik dezelfde versie van de CTT die op de instantie Auteur is gebruikt.

* Er hoeft slechts één publicatieknooppunt te worden gemigreerd. Deze moet uit het taakverdelingsmechanisme worden verwijderd voordat de extractie wordt gestart.

* Gebruik bij het maken van de migratieset de URL van de auteur-AEMaaCS-omgeving.

* Tijdens het publiceren wordt de publicatielaag NIET verkleind (in tegenstelling tot de auteur). Als voorzorgsmaatregel, gelieve te vermijden om het even welke gebruiker in werking gestelde schrijfverrichtingen zoals:

   * Distributie van inhoud van AEM as a Cloud Service auteur naar Publiceren in die omgeving
   * Gebruikerssynchronisatie tussen publicatie-instanties
