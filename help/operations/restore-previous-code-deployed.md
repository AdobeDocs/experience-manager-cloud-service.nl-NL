---
title: De vorige Source-code die in AEM as a Cloud Service is geïmplementeerd herstellen
description: Leer hoe te om een milieu aan zijn laatste succesvolle bouw&amp te herstellen;ndash; geen vereiste pijpleiding.
feature: Operations
role: Admin
badge: label="Alpha" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
source-git-commit: d5a740aa3133504f394933bc77a735f7d14230ba
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# De vorige broncode herstellen die in AEM as a Cloud Service is geïmplementeerd {#restore-previous-code-deployed}

>[!NOTE]
>
>&#x200B;>De functie die in dit artikel wordt beschreven, is alleen beschikbaar via het alfakanaalprogramma voor vroege adoptie. Om omhoog voor alpha te ondertekenen, zie [ Één-klik terugschroeven van prijzen voor pijpleidingsplaatsingen ](/help/implementing/cloud-manager/release-notes/current.md##one-click-rollback).

Het gebruik **herstelt vorige code die** wordt opgesteld om een milieu terug onmiddellijk aan zijn laatste succesvolle bouwstijl-geen vereiste pijpleidingslooppas terug te rollen.

U opent eenvoudig het geselecteerde milieu ![ Meer pictogram van het pictogram of het pictogram van het ellipsmenu ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) menu en kiest **herstel** > **Vorige code opgesteld** om de onlangs opgestelde broncode in seconden terug te rollen.

>[!TIP]
>
>U kunt de actieve bron-code versie in gebruik in de de detailmening van het milieu bekijken, onder het **Algemene** lusje. Zie [ details van de Mening van een milieu ](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).
>
>![ de codeversie van Source in gebruik ](/help/operations/assets/environments-view-details-sourcecodeversion.png)

**herstelt vorige code die** wordt opgesteld eigenschap beschikbaar slechts wanneer **elke** voorwaarde hieronder waar is:

* U houdt **Milieu herstellen creeert** toestemming. Voor details bij het beheren van toestemmingen, zie [ de Toestemmingen van de Douane ](/help/implementing/cloud-manager/custom-permissions.md).
* Uw organisatie is ingeschreven voor het programma Early adopter en de markering feature is ingeschakeld.
* Het programma loopt op **AEM as a Cloud Service**.
* Het gekozen milieu is a **DEV** milieu (de tijdelijke grens van Alpha).
* De laatste pijpleiding voor dat milieu eindigde **met succes** en liep **minder dan 10 dagen** geleden.
* De milieustatus is **Lopend** en geen pijpleiding is lopend.
* De versie van de doelbroncode die u wilt herstellen werd opgesteld **binnen 30 dagen**.

Als om het even welke controle ontbreekt, opent Cloud Manager de volgende dialoogdoos die van één of meerdere onvervulde voorwaarden een lijst maakt en **bevestigt** onbruikbaar, verhinderend herstellen.

![ herstel vorige code opgezette de mislukkingsdialoogdoos ](/help/operations/assets/restore-previous-code-deployment-not-allowed.png).

Als u enkel gegevens wilt herstellen, die zijn verloren, beschadigd, of toevallig geschrapt, aan zijn originele voorwaarde, kunt u [ gebruiken herstellen Inhoud in AEM as a Cloud Service ](/help/operations/restore.md). Dit herstelproces heeft alleen invloed op inhoud, waarbij de broncode en -versie van AEM ongewijzigd blijven.

**om de vorige opgestelde code te herstellen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik op het programma waarvoor u een herstelbewerking wilt starten.

1. Maak een lijst van alle milieu&#39;s voor het programma door één van het volgende te doen:

   * Van het linkerzijmenu, onder **Diensten**, klik ![ het pictogram van Gegevens ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

     ![ Milieu&#39;s tabel ](assets/environments-1.png)

   * Van het linkerzijmenu, onder **Programma**, klik **Overzicht**, dan van de **Milieu** kaart, klik ![ pictogram van het Werkschema ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **tonen allen**.

     ![ toon alle optie ](assets/environments-2.png)

     >[!NOTE]
     >
     >De **kaart van milieu&#39;s** &lbrace;maakt een lijst van slechts drie milieu&#39;s. Klik **tonen allen** in de kaart om *alle* milieu&#39;s van het programma te zien.

1. In de lijst van Milieu&#39;s, rechts van een milieu waarvan broncode u wilt herstellen, klik ![ Meer pictogram of ellipse menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), dan klik **herstellen** > **Vorige opgestelde code**.

   ![ herstelt vorige code die optie van het ellipsmenu wordt opgesteld ](/help/operations/assets/restore-previous-code-deployed-menu.png)

1. In **herstel vorige code opgesteld** dialoogdoos, herzie de momenteel opgestelde versie en de versie u wilt herstellen, dan **bevestigen** klikken.

   ![ herstel vorige code opgesteld dialoogdoos ](/help/operations/assets/restore-previous-code-deployed-dialogbox.png)

1. Cloud Manager rolt het milieu terug naar de vroegere bouwstijl, houdt inhoud en configuratie intact, en merkt het milieu **Herstellend** op de pagina van Milieu tot de plaatsing voltooit.

   ![ Herstellend activering ](/help/operations/assets/restore-previous-code-deployed-restoring.png)
