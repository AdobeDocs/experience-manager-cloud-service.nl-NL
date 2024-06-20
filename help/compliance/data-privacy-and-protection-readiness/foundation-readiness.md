---
title: Data Protection and Data Privacy Regulations - Adobe Experience Manager as a Cloud Service Foundation Readiness
description: Meer informatie over Adobe Experience Manager as a Cloud Service Foundation-ondersteuning voor de verschillende Data Protection and Data Privacy Regulations. Dit artikel omvat de algemene gegevensbeschermingsverordening van de EU (GDPR), de California Consumer Privacy Act, en hoe te om te voldoen wanneer het uitvoeren van een nieuw AEM as a Cloud Service project.
exl-id: 3a4b9d00-297d-4b1d-ae57-e75fbd5c490c
feature: Compliance
role: Admin, Architect, Developer, Leader
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Adobe Experience Manager as a Cloud Service Foundation Readiness for Data Protection and Data Privacy Regulations {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Voor meer informatie over de reactie van de Adobe op privacykwesties, en wat het voor u als Adobe klant betekent, zie [Privacy Center van Adobe](https://www.adobe.com/privacy.html).

## Ondersteuning voor gegevensprivacy en -bescherming van AEM Stichting {#aem-foundation-data-privacy-and-protection-support}

Op het niveau van de AEM Stichting, wordt het Persoonlijke Gegevens die wordt opgeslagen gehouden in het Profiel van de Gebruiker. Daarom richt de informatie in dit artikel hoofdzakelijk hoe te om tot gebruikersprofielen toegang te hebben en te schrappen, zodat kunt u de toegang richten, en verzoeken schrappen, respectievelijk.

## Een gebruikersprofiel openen {#accessing-a-user-profile}

### Handmatige stappen {#manual-steps}

1. Open de gebruikersbeheerconsole door naar **[!UICONTROL Tools - Security - Users]** of door rechtstreeks te bladeren naar `https://<serveraddress>:<serverport>/security/users.html`

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. Zoek vervolgens naar de desbetreffende gebruiker door de naam in de zoekbalk boven aan de pagina te typen:

   ![zoeken naar account](assets/dpp-foundation-01.png)

1. Tot slot open het gebruikersprofiel door het te klikken, dan controle onder **[!UICONTROL Details]** tab.

   ![gebruikersprofiel](assets/dpp-foundation-02.png)

### HTTP-API {#http-api}

Zoals vermeld, verstrekt de Adobe APIs voor de toegang tot van gebruikersgegevens, om automatisering te vergemakkelijken. Er zijn verschillende typen API&#39;s die u kunt gebruiken:

**UserProperties-API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Verkopen-API**

**De startpagina van de gebruiker opzoeken:**

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Gebruikersgegevens ophalen:**

Gebruikend de knoopweg van het huisbezit van de nuttige lading JSON die van het bovengenoemde bevel is teruggekeerd:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Een gebruiker uitschakelen en de bijbehorende profielen verwijderen {#disabling-a-user-and-deleting-the-associated-profiles}

### Gebruiker uitschakelen {#disable-user}

1. Open de console van het Beleid van de Gebruiker en onderzoek naar de gebruiker in kwestie, zoals hierboven beschreven.
2. Houd de muisaanwijzer boven de gebruiker en klik op het pictogram Selecteren. Het profiel wordt grijs weergegeven om aan te geven dat het is geselecteerd.

3. Klik in het bovenste menu op **Uitschakelen** om de gebruiker uit te schakelen (uit):

   ![account uitschakelen](assets/dpp-foundation-03.png)

4. Ten slotte, bevestig de actie.

   De gebruikersinterface geeft aan dat de gebruikersaccount is gedeactiveerd door uit te schakelen en een vergrendeling toe te voegen aan de profielkaart:

   ![account uitgeschakeld](assets/dpp-foundation-04.png)

### Gebruikersprofielgegevens verwijderen {#delete-user-profile-information}

>[!NOTE]
>
>Voor AEM as a Cloud Service, is er geen handprocedure beschikbaar van UI voor de schrapping van een gebruikersprofiel, aangezien CRXDE niet toegankelijk is.

### HTTP-API {#http-api-1}

Bij de volgende procedures worden de `curl` opdrachtregelprogramma om te tonen hoe u de gebruiker kunt uitschakelen met de **[!UICONTROL cavery]** `userId` en verwijdert u de profielen die beschikbaar zijn op de standaardlocatie.

**De startpagina van de gebruiker opzoeken:**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**De gebruiker uitschakelen:**

Gebruikend de knoopweg van het huisbezit van de nuttige lading JSON die van het bovengenoemde bevel is teruggekeerd:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**Gebruikersprofielen verwijderen**

Het gebruiken van de knoopweg van het huisbezit van de nuttige lading JSON die van het bevel van de rekeningsontdekking en het gekende uit de knoopplaatsen van het kaderprofiel is teruggekeerd:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
