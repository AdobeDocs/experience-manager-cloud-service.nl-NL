---
title: Site-verificatie configureren voor het schrijven van inhoud
description: Leer hoe AEM Live tokenverificatie ondersteunt en hoe u AEM kunt configureren voor het gebruik van verificatie met WYSIWYG-authoring.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: b2838da2-79c7-49b1-a101-15c21e80197e
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Site-verificatie configureren voor het schrijven van inhoud {#site-authentication}

Leer hoe AEM Live tokenverificatie ondersteunt en hoe u AEM kunt configureren voor het gebruik van verificatie met WYSIWYG-authoring.

## Overzicht {#overview}

AEM Live ondersteunt tokenverificatie. Siteverificatie wordt gewoonlijk toegepast op zowel de voorvertoning als de publicatiesites, maar kan ook worden geconfigureerd om alleen elke site afzonderlijk te beschermen.

>[!NOTE]
>
>Als u ervoor kiest om siteverificatie te activeren, moet u deze ook configureren in uw AEM-ontwerpomgeving

## Vereisten {#requirements}

Om plaatsauthentificatie voor gebruik met inhoud te vormen creeert, moet u de volgende taken eerst voltooien:

* Dit document veronderstelt dat u reeds een plaats voor uw project hebt gecreeerd dat op de [ Begonnen Gids van de Ontwikkelaar wordt gebaseerd die voor de Authoring van WYSIWYG met de gids van Edge Delivery Services.](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* U moet reeds [ toegelaten de repoless eigenschap voor uw project hebben.](/help/edge/wysiwyg-authoring/repoless.md)

## Siteverificatie configureren {#configure-authentication}

Gelieve te zien het document [ Vormende Authentificatie van de Plaats ](https://www.aem.live/docs/authentication-setup-site) voor details op hoe te om plaatsauthentificatie te vormen.

Neem nota van de volgende informatie aangezien u authentificatie vormt:

* De ID van de technische rekening
* Uw token voor siteverificatie

Deze items zijn vereist om de configuratie van siteverificatie voor uw AEM-ontwerpomgeving te voltooien.

## Ontwerpomgeving configureren {#authoring-environment}

Zodra de plaatsauthentificatie wordt gevormd, kunt u het in uw het auteursmilieu van AEM toelaten.

1. Teken in de auteursinstantie van AEM en ga naar **Hulpmiddelen** -> **de Diensten van de Wolk** -> **Configuratie van Edge Delivery Services** en selecteer de configuratie die automatisch voor uw plaats werd gecreeerd en tikken of **Eigenschappen** in de hulpmiddelbar klikken.
1. In het **venster van de Configuratie van Edge Delivery Services**, selecteer het **Authentificatie** lusje, verstrek het **Symbolische van de Authentificatie van de Plaats**, dat u eerder kopieerde.

   ![ Configuratie van Edge Delivery Services ](/help/edge/wysiwyg-authoring/assets/site-authentication/configure-aem-author.png)

1. Verifieer dat **technische rekeningidentiteitskaart** eerder gekopieerde aanpast.

   * Dit veld is alleen-lezen en vooraf gedefinieerd.
   * De technische account is hetzelfde voor alle sites in één AEM-auteuromgeving.

1. Tik of klik **sparen &amp; sluit**.
