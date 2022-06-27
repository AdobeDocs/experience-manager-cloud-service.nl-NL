---
title: Omgevingsvariabelen van Cloud Manager
description: De standaardmilieuvariabelen kunnen via de Manager van de Wolk worden gevormd en worden beheerd en aan het runtime milieu worden verstrekt, dat in configuratie OSGi moet worden gebruikt.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
source-git-commit: 7f8d6afdb5e3aecc90fdeb870eaaa0a5c5d29ca9
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 0%

---


# Omgevingsvariabelen van Cloud Manager {#environment-variables}

Standaardomgevingsvariabelen kunnen worden geconfigureerd en beheerd via Cloud Manager. Zij worden verstrekt aan het runtime milieu en kunnen in configuraties worden gebruikt OSGi. Omgevingsvariabelen kunnen milieuspecifieke waarden of omgevingsgeheimen zijn, op basis van wat wordt gewijzigd.

## Overzicht {#overview}

Omgevingsvariabelen bieden gebruikers van AEM as a Cloud Service:

* Ze stellen het gedrag van uw code en toepassing in staat te variëren op basis van context en omgeving. Ze kunnen bijvoorbeeld worden gebruikt om verschillende configuraties in de ontwikkelomgeving mogelijk te maken in vergelijking met de productie- of werkgebiedomgevingen om kostbare fouten te voorkomen.
* Ze hoeven slechts eenmaal te worden geconfigureerd en ingesteld en kunnen indien nodig worden bijgewerkt en verwijderd.
* Hun waarden kunnen op om het even welk punt in tijd worden bijgewerkt en onmiddellijk zonder de behoefte aan om het even welke codeveranderingen of plaatsingen van kracht worden.
* Zij kunnen code van configuratie scheiden en de behoefte verwijderen om gevoelige informatie in versiecontrole te omvatten.
* Zij verbeteren de veiligheid van de AEM as a Cloud Service toepassing aangezien zij buiten de code leven.

De meest gangbare gebruiksgevallen voor het gebruik van omgevingsvariabelen zijn:

* De AEM-toepassing verbinden met verschillende externe eindpunten
* Een verwijzing gebruiken bij het opslaan van wachtwoorden in plaats van rechtstreeks in de codebasis
* Wanneer er meerdere ontwikkelomgevingen in een programma voorkomen en sommige configuraties van de ene omgeving tot de andere verschillen

## Omgevingsvariabelen toevoegen {#add-variables}

1. Meld u aan bij Adobe Cloud Manager via [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Cloud Manager geeft een overzicht van de verschillende beschikbare programma&#39;s. Selecteer het bestand dat u wilt beheren.
1. Selecteer **Omgevingen** selecteert u vervolgens in het linkernavigatievenster de omgeving waarvoor u een omgevingsvariabele wilt maken.
1. Selecteer binnen de details van de omgeving de optie **Configuratie** dan selecteert u **Toevoegen** om de **Omgevingsconfiguratie** .
   * Als u een omgevingsvariabele voor het eerst toevoegt, ziet u een **Configuratie toevoegen** in het midden van de pagina. U kunt deze knop of **Toevoegen** om de **Omgevingsconfiguratie** .

   ![Tabblad Configuratie](assets/configuration-tab.png)

1. Voer de details van de variabele in.
   * **Naam**
   * **Waarde**
   * **Service toegepast** - Definieert waarvoor de dienst (Auteur/Publicatie/Voorproef) de variabele van toepassing is of als het op alle diensten van toepassing is
   * **Type** - Hiermee wordt gedefinieerd of de variabele een normale variabele of een geheim is

   ![Een variabele toevoegen](assets/add-variable.png)

1. Nadat u de nieuwe variabele hebt ingevoerd, moet u **Toevoegen** in de laatste kolom van de rij die de nieuwe variabele bevat.
   * U kunt meerdere variabelen tegelijk invoeren door een nieuwe regel in te voeren en **Toevoegen**.

   ![Variabelen opslaan](assets/save-variables.png)

1. Selecteren **Opslaan** om de variabelen te behouden.

Een indicator met de status **Bijwerken** wordt getoond bij de bovenkant van de lijst en naast de onlangs toegevoegde variabele om erop te wijzen dat het milieu met de configuratie wordt bijgewerkt. Wanneer de bewerking is voltooid, is de nieuwe omgevingsvariabele zichtbaar in de tabel.

![Variabelen bijwerken](assets/updating-variables.png)

>[!TIP]
>
>Als u meerdere variabelen wilt toevoegen, wordt u aangeraden de eerste variabele toe te voegen en vervolgens de **Toevoegen** in de **Omgevingsconfiguratie** om extra variabelen toe te voegen. Op deze manier kunt u ze met één update toevoegen aan de omgeving.

## Omgevingsvariabelen bijwerken {#update-variables}

Nadat u omgevingsvariabelen hebt gemaakt, kunt u deze bijwerken met de opdracht **Toevoegen/bijwerken** knop om het dialoogvenster **Omgevingsconfiguratie** .

1. Meld u aan bij Adobe Cloud Manager via [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Cloud Manager geeft een overzicht van de verschillende beschikbare programma&#39;s. Selecteer het bestand dat u wilt beheren.
1. Selecteer **Omgevingen** selecteert u vervolgens in het linkernavigatievenster de omgeving waarvoor u een omgevingsvariabele wilt maken.
1. Selecteer binnen de details van de omgeving de optie **Configuratie** dan selecteert u **Toevoegen/bijwerken** in de rechterbovenhoek **Omgevingsconfiguratie** .

   ![Knop Toevoegen/Bijwerken voor variabelen](assets/add-update-variables.png)

1. Selecteer met de knop Ovaal in de laatste kolom van de rij van de variabele die u wilt wijzigen de optie **Bewerken** of **Verwijderen**.

   ![Variabele bewerken of verwijderen](assets/edit-delete-variable.png)

1. Bewerk indien nodig de omgevingsvariabele.
   * Tijdens het bewerken verandert de knop voor ovaal in opties om terug te keren naar de oorspronkelijke waarde of om uw wijziging te bevestigen.
   * Als u geheimen bewerkt, kunnen de waarden alleen worden bijgewerkt en niet worden weergegeven.

   ![Variabele bewerken](assets/edit-variable.png)

1. Nadat u alle vereiste configuratiewijzigingen hebt aangebracht, selecteert u **Opslaan**.

[Zoals bij het toevoegen van variabelen](#add-variables) een indicator met de status **Bijwerken** boven aan de tabel en naast de nieuw bijgewerkte variabele(n) wordt weergegeven dat de omgeving wordt bijgewerkt met de configuratie. Na voltooiing zullen de bijgewerkte omgevingsvariabelen zichtbaar zijn in de tabel.

>[!TIP]
>
>Als u meerdere variabelen wilt bijwerken, kunt u het beste de opdracht **Omgevingsconfiguratie** om alle benodigde variabelen tegelijk bij te werken voordat u tikt of klikt **Opslaan**. Op deze manier kunt u ze met één update toevoegen aan de omgeving.

## Omgevingsvariabelen gebruiken {#using}

Omgevingsvariabelen kunnen `pom.xml` configuraties veiliger en flexibeler. Bijvoorbeeld, moeten de wachtwoorden niet hard worden gecodeerd en uw configuratie kan aanpassen gebaseerd op de waarden in omgevingsvariabelen.

U hebt als volgt toegang tot omgevingsvariabelen en geheimen via XML.

* `${env.VARIABLE_NAME}`
* `${secret.SECRET_NAME}`

Zie het document [Project instellen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repository-support-password-protected-maven-repositories) voor een voorbeeld van het gebruik van beide typen variabelen in een `pom.xml` bestand.
