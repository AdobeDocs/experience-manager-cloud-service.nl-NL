---
title: Vorige Source-code die is geïmplementeerd herstellen
description: Leer hoe te om een milieu aan zijn laatste succesvolle bouw&amp te herstellen;ndash; geen vereiste pijpleiding.
feature: Operations
role: Admin
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: 8f804f55-a66d-47ad-a48d-61b861cef4f7
source-git-commit: 7968668766ae4c8a966bbde93aa2f2ac0c401659
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# De vorige broncode herstellen die in AEM as a Cloud Service is geïmplementeerd {#restore-previous-code-deployed}

>[!NOTE]
>
>De functie die in dit artikel wordt beschreven, is alleen beschikbaar via het bètaprogramma. Om omhoog voor bèta te ondertekenen, zie [&#x200B; Één-klik terugschroeven van prijzen voor pijpleidingsplaatsingen &#x200B;](/help/implementing/cloud-manager/release-notes/current.md##one-click-rollback).

Het gebruik **herstelt vorige code die** wordt opgesteld om een milieu terug onmiddellijk aan zijn laatste succesvolle bouwstijl-geen vereiste pijpleidingslooppas terug te rollen.

U opent eenvoudig het geselecteerde milieu ![&#x200B; Meer pictogram van het pictogram of het pictogram van het ellipsmenu &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) menu en kiest **herstel** > **Vorige code opgesteld** om de onlangs opgestelde broncode in seconden terug te rollen.

>[!TIP]
>
>U kunt de actieve bron-code versie in gebruik in de de detailmening van het milieu bekijken, onder het **Algemene** lusje. Zie [&#x200B; details van de Mening van een milieu &#x200B;](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).
>
>![&#x200B; de codeversie van Source in gebruik &#x200B;](/help/operations/assets/environments-view-details-sourcecodeversion.png)

**herstel vorige code die** wordt opgesteld beschikbaar slechts wanneer de volgende voorwaarden worden vervuld:

* Slechts één wordt toegestaan herstellen per succesvolle pijpleidingsuitvoering; om opnieuw te herstellen, voltooi een andere succesvolle pijpleidingslooppas.
* U houdt **Milieu herstellen creeert** toestemmingen. Voor details bij het beheren van toestemmingen, zie [&#x200B; de Toestemmingen van de Douane &#x200B;](/help/implementing/cloud-manager/custom-permissions.md).
* Uw organisatie is ingeschreven voor het bètaprogramma en de functiemarkering is ingeschakeld.
* Het programma loopt op AEM as a Cloud Service.
* De laatste pijpleiding voor dat milieu eindigde met succes en liep **minder dan 30 dagen** geleden.
* De milieustatus is *Lopend* en geen pijpleiding is lopend.

**herstel vorige code die** wordt opgesteld werkt in `Production` milieu, naast `Development` milieu, `Stage` milieu, en `Specialized Testing Environment`. Nadat u hebt bevestigd, start Cloud Manager het terugzetten en wordt een pushmelding verzonden bij het starten en bij het voltooien.

>[!IMPORTANT]
>
>Adobe adviseert hoogst het bevestigen van de procedure in `Stage` ** gebruikend het in `Production` om risico te verminderen en stabiliteit te verzekeren.


Als om het even welke controle ontbreekt, opent Cloud Manager de volgende dialoogdoos die van één of meerdere onvervulde voorwaarden een lijst maakt en **bevestigt** onbruikbaar, verhinderend herstellen.

![&#x200B; herstel vorige code opgezette de mislukkingsdialoogdoos &#x200B;](/help/operations/assets/restore-previous-code-deployment-not-allowed.png).

Als u enkel gegevens wilt herstellen, die zijn verloren, beschadigd, of toevallig geschrapt, aan zijn originele voorwaarde, kunt u [&#x200B; gebruiken herstellen Inhoud in AEM as a Cloud Service &#x200B;](/help/operations/restore.md). Dit herstelproces heeft alleen invloed op inhoud, waarbij de broncode en -versie van AEM ongewijzigd blijven.

**om de vorige opgestelde code te herstellen:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik op het programma waarvoor u een herstelbewerking wilt starten.

1. Maak een lijst van alle milieu&#39;s voor het programma door één van het volgende te doen:

   * Van het linkerzijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van Gegevens &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Milieu&#39;s**.

     ![&#x200B; Milieu&#39;s tabel &#x200B;](assets/environments-1.png)

   * Van het linkerzijmenu, onder **Programma**, klik **Overzicht**, dan van de **Milieu** kaart, klik ![&#x200B; pictogram van het Werkschema &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **tonen allen**.

     ![&#x200B; toon alle optie &#x200B;](assets/environments-2.png)

     >[!NOTE]
     >
     >De **kaart van milieu&#39;s** &lbrace;maakt een lijst van slechts drie milieu&#39;s. Klik **tonen allen** in de kaart om *alle* milieu&#39;s van het programma te zien.

1. In de lijst van Milieu&#39;s, rechts van een milieu waarvan broncode u wilt herstellen, klik ![&#x200B; Meer pictogram of ellipse menupictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), dan klik **herstellen** > **Vorige opgestelde code**.

   ![&#x200B; herstelt vorige code die optie van het ellipsmenu wordt opgesteld &#x200B;](/help/operations/assets/restore-previous-code-deployed-menu.png)

1. In **herstel vorige code opgesteld** dialoogdoos, herzie de momenteel opgestelde versie en de versie u wilt herstellen, dan **bevestigen** klikken.

   ![&#x200B; herstel vorige code opgesteld dialoogdoos &#x200B;](/help/operations/assets/restore-previous-code-deployed-dialogbox.png)

1. Cloud Manager rolt het milieu terug naar de vroegere bouwstijl, houdt inhoud en configuratie intact, en merkt het milieu **Herstellend** op de pagina van Milieu tot de plaatsing voltooit.

   ![&#x200B; Herstellend activering &#x200B;](/help/operations/assets/restore-previous-code-deployed-restoring.png)
