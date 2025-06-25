---
title: Functie in-/uitschakelen inschakelen om functies voor vroege adoptie en pre-release te integreren
description: Functieschakeloptie is een functionaliteit in AEM waarmee beheerders nieuwe functies kunnen inschakelen in een runtimeomgeving.
feature: Adaptive Forms, Foundation Components, Core Components
role: User, Developer
source-git-commit: cc4fccc51f487170bf6c14e4b302a8d5912c33a0
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# De functie in-/uitschakelen op de Adobe Experience Software Development Kit (AEM SDK)

Met de functie in AEM kunnen beheerders functies tijdens runtime in- of uitschakelen. Dit is ideaal voor het beheer van functies voor vroege adoptie en pre-release zonder wijzigingen in de code. De functie ondersteunt geleidelijke rollouts, A/B-tests en snelle deactivering van onstabiele functies.

In dit artikel wordt beschreven hoe u functieschakelingen kunt inschakelen in de AEM Local SDK Setup, die AEM as a Cloud Service simuleert met de SDK en Dispatcher. Deze opstelling helpt teams in een productie-als milieu testen alvorens aan de wolk op te stellen.

## Waarom Functietogboeken gebruiken in AEM SDK Setup?

Als u werkt in een AEM SDK-configuratie, kunt u met de functie schakelen naar:

* Het testen van experimentele functies veilig.

* Nieuwe onderdelen in fasen implementeren.

* Eén codebase behouden in meerdere omgevingen.

* Risico&#39;s verminderen tijdens implementaties en upgrades.

## Vereisten

Controleer het volgende voordat u functieschakelingen inschakelt in uw AEM SDK-configuratie:

* Gebruiker is lid van de `forms-users` -groep.

* Navigeer naar `http://<author-instance-url>:portnumber/system/console/bundles` en controleer of **(com.adobe.granite.toggle.impl.dev-1.1.2.jar)** bundel aanwezig is of niet. Voor het geval dat het niet aanwezig [ is download de bundel van de verbinding ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/com.adobe.granite.toggle.impl.dev-1.1.2%20.jar).

  ![ Toggle van de Eigenschap ](/help/forms/assets/aem-web-console-bundle.png)

### Functie in-/uitschakelen

Ga als volgt te werk om functieschakelingen in te schakelen in uw AEM SDK-exemplaar:

1. Meld u aan bij uw AEM Forms-exemplaar.

1. Navigeer naar `http://author-instance-url:portnumber/system/console/configMgr` .

1. Zoek naar Adobe Granite Dynamic Toggle Provider in Configuration Manager.

   ![ Toggle van de Eigenschap ](/help/forms/assets/aem-web-console-confi.png)

1. Klik op het pictogram ✏️ .
1. Klik in de sectie Ingeschakelde schakelopties op ➕ .
1. Voeg de functie-schakelings-id toe voor de functie, zoals in de onderstaande afbeelding wordt getoond.
   ![ Toggle van de Eigenschap ](/help/forms/assets/feature-toggle.png)

1. Klik op Opslaan

>[!NOTE]
>
> U kunt de functie-schakelfunctie vinden in de id in het document die specifiek is voor de functie voor vroege adoptie.


### Functie in-/uitschakelen

Voer de onderstaande stappen uit om de functieschakeloptie(s) uit te schakelen voor functies waarvan de schakeloptie(s) is ingeschakeld:

1. Meld u aan bij uw AEM Forms-exemplaar.
1. Navigeer naar `http://author-instance-url:portnumber/system/console/configMgr` .
1. Zoek naar Adobe Granite Dynamic Toggle Provider in Configuration Manager.
1. Klik op het pictogram ✏️ .
1. Klik in de sectie Uitgeschakelde schakelingen op ➕ .
1. Voeg het wisselnummer toe voor de functie die moet worden uitgeschakeld.

   ![ Toggle van de Eigenschap ](/help/forms/assets/disable-toggle-feature.png)

### Technische overweging

De knevels van de eigenschap zijn runtime-beheerd en het meest geschikt voor ontwikkeling of testmontages. Zorg ervoor dat in een AEM SDK-configuratie de schakelopties versiegestuurd en gesynchroniseerd zijn met CI/CD. Pagina vernieuwen of cache wissen is mogelijk nodig om wijzigingen door te voeren.

>[!NOTE]
>
> Neem contact op met het Adobe-ondersteuningsteam om de functieknop in te schakelen voor de productieomgeving.

