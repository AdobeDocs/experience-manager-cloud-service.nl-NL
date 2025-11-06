---
title: Aangepaste domeinnamen beheren
description: Leer hoe u met Cloud Manager aangepaste domeinnamen kunt weergeven, bijwerken, vervangen en verwijderen.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---


# Aangepaste domeinnamen beheren {#managing-custom-domain-names}

Met Cloud Manager kunt u aangepaste domeinnamen bewerken, bijwerken, vervangen, verifiëren en verwijderen.

## Een aangepaste domeinnaamconfiguratie bewerken {#view-and-update}

In Adobe Cloud Manager kunt u om de volgende redenen een aangepaste domeinnaamconfiguratie bewerken:

* **Omschakelende milieu&#39;s**: Om de correcte configuratie toe te passen afhankelijk van of u inhoud aan eind - gebruikers (publiceren) of interne gebruikers (Auteur) dient.
* **de updates van de Veiligheid**: Om aan een nieuwer SSL certificaat voor verbeterde veiligheid of nalevingsdoeleinden te bevorderen.
* **Veranderende plaatsingsstrategie**: Om ervoor te zorgen dat het correcte SSL certificaat op een specifiek milieu voor juiste encryptie en plaatstoegang wordt toegepast.

**om een configuratie van de douanedomeinnaam uit te geven:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.

1. Onder de **rubriek van de Diensten**, klik ![ Sociale netwerkpictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Toewijzingen van het Domein**.

1. Op de **pagina van de Toewijzingen van het Domein**, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) aan het eind van een rij waarvan CDN u wilt uitgeven.

1. Klik **uitgeven**.

1. In **geef de configuratiedoos van het Domein** uit, doe het volgende:

   * In de **lijst van de Rij** drop-down lijst, selecteer de rij (publiceer of Voorproef) u wilt gebruiken.
   * In de **SSL certificaat** drop-down lijst, selecteer het SSL certificaat dat u wilt gebruiken.

1. Klik **Update**.


## Het SSL-certificaat van een aangepaste domeinnaam bijwerken {#update-cert}

Voer dezelfde stappen hierboven uit om het SSL-certificaat van een aangepaste domeinnaam bij te werken.

>[!NOTE]
>
>Het SSL certificaat moet geldig zijn, [ reeds gevormd ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), en bevat de naam van het douanedomein u bijwerkt.


## Een aangepaste domeinnaam verifiëren {#verify-custom-domain-name}

Zie ook [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **pagina van de Montages van het Domein** van het **scherm van het Overzicht**.

1. Identificeer de rij van de naam van het douanedomein die u wilt verifiëren.

1. Klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij het uiterst juiste eind van de rij.

1. In het drop-down menu, klik **verifieer**.

1. In **verifieer domein** dialoogdoos, in **welk certificaattype u op het gebruiken van dit domein van plan bent?** selecteert u een van de volgende opties in de vervolgkeuzelijst:

   | Certificaattype, optie | Beschrijving |
   | --- | --- |
   | Adobe managed (DV) SSL-certificaat | Selecteer dit certificaattype als u een DV-certificaat (Domain Validation) wilt gebruiken. Deze optie is ideaal voor de meeste gevallen, die basisdomeinbevestiging verstrekken. Adobe beheert en vernieuwt het certificaat automatisch. |
   | Door de klant beheerd SSL-certificaat (OV/EV) | Selecteer dit certificaattype als u een EV/OV SSL-certificaat wilt gebruiken om het domein te beveiligen. Deze optie biedt uitgebreide beveiliging met OV (Organisation Validation) of EV (Extended Validation). Gebruik deze optie als u strengere controles, hogere vertrouwensniveaus of aangepaste controle over de certificaten nodig hebt. |

1. In **verifieer domein** dialoogdoos, die op het certificaattype wordt gebaseerd u selecteerde, doe één van het volgende:

   | Als u het certificaattype hebt geselecteerd | Beschrijving |
   | --- | ---  |
   | Door Adobe beheerd certificaat | a. Voltooi de [ Adobe beheerde certificaatstappen ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-steps). Wanneer u de stappen in **voltooit verifieer domein** dialoogdoos, **verifieert**.<ul><li>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.</li><li>Cloud Manager verifieert uiteindelijk het bezit van de domeinnaam en werkt de status in de **lijst van de Montages van het Domein** bij. Zie [ de status van de naam van het douanedomein van de Controle ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.</li>![ verifieer domeinstatus ](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. U bent nu klaar om [ een Adobe geleid (DV) SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert) toe te voegen.</li></ul> |
   | Door de klant beheerd certificaat | a. Klik **OK**.<br> b. U bent nu klaar om [ een klant beheerde (OV/EV) SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert) toe te voegen.<br> nadat u het certificaat toevoegt, wordt uw domeinnaam duidelijk zoals geverifieerd in de **2} lijst van de Montages van het Domein {.** Zie [ de status van de naam van het douanedomein van de Controle ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.</li></ul><br>![ verifieer domein voor een klant beheerd EV/OV- certificaat ](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |


## Een aangepaste domeinnaam uit alle bijbehorende omgevingen verwijderen {#deleting}

Een gebruiker met de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan Cloud Manager gebruiken om een naam van het douanedomein te schrappen.

### Een aangepaste domeinnaam uit alle bijbehorende omgevingen verwijderen {#delete-cdn-all}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **pagina van de Montages van het Domein** van het **scherm van het Overzicht**.

1. Identificeer de rij van de naam van het douanedomein die u wilt schrappen.

1. Klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij het uiterst juiste eind van de rij.

1. Selecteer **Schrapping**.

1. Bevestig je verzending.


### Een aangepaste domeinnaam uit een specifieke omgeving verwijderen {#delete-cdn-specific}

>[!WARNING]
>
>Verwijder DNS van het domein verslagen met uw DNS leverancier *alvorens* het domein in Cloud Manager te schrappen. Verlaten (gevaarlijk) DNS-vermeldingen kunnen worden gekaapt en vormen een beveiligingsrisico.

**om een naam van het douanedomein van een specifiek milieu te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Van de **pagina van Milieu&#39;s**, navigeer aan een detailsscherm van het milieu van belang.

1. Van de lijst van Toewijzingen van het Domein, identificeer de rij van de naam van het douanedomein u wilt schrappen.

1. Klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) bij het uiterst juiste eind van de rij.

1. Selecteer **Schrapping**.

1. Bevestig je verzending.
