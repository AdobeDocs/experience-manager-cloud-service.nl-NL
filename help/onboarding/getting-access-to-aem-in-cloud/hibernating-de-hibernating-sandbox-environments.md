---
title: 'Sluiende en ontsmette zandbakomgevingen '
description: 'Sluiende en ontsmette zandbakomgevingen '
translation-type: tm+mt
source-git-commit: 213a7237abd4de75be43af430181f4aa914196f4
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---


# Sluiende en ontsmette zandbakomgevingen {#hibernating-introduction}

Sandbox Program-omgevingen voeren een *hibernatiemodus* in als gedurende een bepaalde periode geen activiteit wordt gedetecteerd.

>[!NOTE]
>De sluimerstand is uniek voor Sandbox-programmaomgevingen. Reguliere programmeeromgevingen houden geen hiberatie in.

## Sluimerstand {#hibernation-introduction}

Sluimerstand kan automatisch of handmatig plaatsvinden. Het kan tot een paar minuten voor de milieu&#39;s van het Programma van Sandbox duren om *hibernatiemodus* in te gaan. De gegevens blijven behouden tijdens de hibernatie.

Sluimerstand wordt gecategoriseerd als:

* **De milieu&#39;s van het Programma**  AutomaticSandbox worden automatisch hibernated na acht uren van inactiviteit, betekenend dat noch de auteur noch de publicatieservices verzoeken ontvangen.

* **Handmatig**: Als gebruiker kunt u handmatig een Sandbox-programmaomgeving herbergen, hoewel dit niet nodig is omdat de slaapstand automatisch zal plaatsvinden na een bepaalde periode (acht uur) van inactiviteit.

>[!CAUTION]
>In de meest recente versie kunt u een koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager niet gebruiken om een Sandbox-programmaomgeving te onderbreken. De oplossing bevindt zich eenmaal in de Developer Console. Voeg het volgende patroon toe aan het einde van de URL `#release-cm-p1234-e5678 where 1234` 1234 is uw *Programma-id* en 5678 is uw *Omgeving-id*.

### Handmatige slaapstand gebruiken {#using-manual-hibernation}

U kunt uw Sandbox-programma handmatig op twee verschillende manieren via de Developer Console herbergen:

* Detailscherm omgeving
* Omgevingsscherm

>[!NOTE]
>Alle gebruikers van Cloud Manager hebben toegang tot de ontwikkelaarsconsole voor een Sandbox-programma.

Voer de onderstaande stappen uit om uw Sandbox-programmaomgevingen handmatig te hiberneren:

1. Navigeer naar **Developer Console**.
Raadpleeg [Toegang tot ontwikkelaarsconsole](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) voor meer informatie over toegang tot de **Developer Console** via de **Environment**-kaart.
   >[!IMPORTANT]
   >Als u rechtstreeks vanuit Cloud Manager een koppeling maakt naar de **Developer Console**, kunt u een Sandbox-programmaomgeving niet herbergen. De oplossing bevindt zich eenmaal in de Developer Console. Voeg het volgende patroon toe aan het einde van de URL `#release-cm-p1234-e5678 where 1234` 1234 is uw *Programma-id* en 5678 is uw *Omgeving-id*.

1. Klik **Hibernate**, zoals aangetoond in het hieronder cijfer:

   ![](assets/hibernate-1.png)

   Of

   Klik op de koppeling **Omgevingen** linksboven om de lijst met omgevingen weer te geven en klik vervolgens op **Hibernate**, zoals in de onderstaande afbeelding wordt getoond:

   ![](assets/hibernate-1b.png)

1. Klik **Hibernate** om de stap te bevestigen.

   ![](assets/hibernate-2.png)

1. Wanneer de winterslaap succesvol is, zult u het hibernatieproces volledige bericht voor uw milieu in het **scherm van de Console van de Ontwikkelaar** zien.

   ![](assets/hibernate-4.png)


## De-hibernatie {#de-hibernation-introduction}

1. Navigeer naar **Developer Console**.
Raadpleeg [Toegang tot ontwikkelaarsconsole](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) voor meer informatie over toegang tot de **Developer Console** via de **Environment**-kaart.

   >[!IMPORTANT]
   >Als u rechtstreeks vanuit Cloud Manager een koppeling maakt naar de **Developer Console**, kunt u een Sandbox-programmaomgeving niet dehiberneren. De oplossing bevindt zich eenmaal in de Developer Console. Voeg het volgende patroon toe aan het einde van de URL `#release-cm-p1234-e5678 where 1234` 1234 is uw *Programma-id* en 5678 is uw *Omgeving-id*.

   >[!NOTE]
   >U kunt ook naar de **Developer Console** navigeren om de historie te verwijderen door toegang te proberen tot de auteur of de publicatieservice van een reeds gedownloade omgeving. in dat geval wordt een bestemmingspagina weergegeven met een koppeling naar de Developer Console. Zie de sectie Accessing a Hibernated Environment hieronder.

   >[!IMPORTANT]
   >Toegang tot de ontwikkelaarsconsole wordt gedefinieerd door de **Cloud Manager - Developer Role** in de **Admin Console**. Een gebruiker met een ontwikkelaarrol machtiging kan een Sandbox-programmaomgeving dehiberneren.

1. Klik op **De-hibernate**, zoals getoond in de hieronder figuur:

   ![](assets/de-hibernation-img1.png)

   Of

   Klik op de koppeling **Omgevingen** linksboven om de lijst met omgevingen weer te geven en klik vervolgens op **De-hibernate**, zoals in de onderstaande afbeelding wordt getoond

   ![](assets/de-hibernate-1b.png)


1. Klik **De Sluimerstand** om de stap te bevestigen.

   ![](assets/de-hibernation-img2.png)

1. U ontvangt het bericht dat het dehibernatieproces is gestart en u wordt bijgewerkt met de voortgang.

   ![](assets/de-hibernation-img3.png)

1. Zodra het proces voltooit, is het milieu van het Programma Sandbox opnieuw actief.

   ![](assets/de-hibernation-img4.png)

### Machtigingen om de-hibernate {#permissions-de-hibernate} te verwijderen

Elke gebruiker met een productprofiel dat hem toegang geeft tot AEM als Cloud Service, moet toegang hebben tot de **Developer Console**, zodat hij of zij de omgeving kan dehiberneren.

## Toegang tot een gegeneerde omgeving {#accessing-hibernated-environment}

Wanneer de gebruiker om het even welke browser verzoeken tegen of de auteur of publicatielaag van een hibernated milieu, zal de gebruiker een landende pagina ontmoeten die de geminimaliseerde status van het milieu beschrijft, zoals aangetoond in het hieronder cijfer beschrijft:

![](assets/de-hibernation-img5.png)

## Belangrijke overwegingen {#important-considerations}

Weinig belangrijke overwegingen met betrekking tot gehiberneerde en gedeshiberneerde milieu&#39;s zijn:

* Een gebruiker kan een pijpleiding gebruiken om douanecode aan gehiberneerde milieu&#39;s op te stellen. Het milieu zal gehiberneerd blijven en de nieuwe code zal in het milieu verschijnen zodra ontruimd-hibernated.

* AEM upgrades kunnen worden toegepast op gehiberde omgevingen, die klanten handmatig kunnen activeren via Cloud Manager. Het milieu zal gehiberneerd blijven en de nieuwe introductie zal in het milieu verschijnen zodra het wordt gedehiberneerd.

>[!NOTE]
>Cloud Manager geeft op dit moment niet aan of een omgeving is gehiberneerd.

## Updates AEM voor sandboxomgevingen {#aem-updates-sandbox}

Raadpleeg [AEM versie-updates](/help/implementing/deploying/aem-version-updates.md) voor meer informatie.

Een gebruiker kan handmatig AEM updates toepassen op de omgevingen in een Sandbox-programma.

Raadpleeg [Omgeving bijwerken](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) voor meer informatie over het bijwerken van een omgeving.

>[!NOTE]
>* Een handupdate kan slechts worden in werking gesteld wanneer het gerichte milieu een behoorlijk gevormde pijpleiding heeft.
>* Een handmatige update van *Production* of *Stage*-omgeving werkt automatisch de andere bij. De Production+Stage-omgeving moet zich op dezelfde AEM bevinden.






