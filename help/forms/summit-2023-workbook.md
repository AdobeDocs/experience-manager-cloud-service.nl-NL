---
title: Forms inschakelen met behulp van kerncomponenten en zonder hoofd
seo-title: Build Engaging Forms Using Core Components and Headless
description: Forms inschakelen met behulp van kerncomponenten en zonder hoofd
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: 2f387d71fb5a099be1ec480c1122a475d56a0ebe
workflow-type: tm+mt
source-wordcount: '6796'
ht-degree: 0%

---


# Forms inschakelen met behulp van kerncomponenten en zonder hoofd

## Overzicht van Lab

In dit hands-on laboratorium, leert u:

Hoe u AEM Forms kunt gebruiken om gemakkelijk adaptieve formulieren te maken met de nieuwste kerncomponenten die consistent zijn met AEM Sites, waardoor het mogelijk wordt om gegevens op te halen door de adaptieve formulieren als headless formulieren aan het web, mobiele apparaten en chatten te leveren. U leert ook beste praktijken rond het stileren, aanpassingen, en front-end ontwikkeling.

## Toetsen

* **Bedrijfsflexibiliteit**: Als zakelijke gebruiker kan ik gemakkelijk Form Experience voor meerdere kanalen schrijven.

* **Kracht voor ontwikkelaar vooraf**: Als frontend ontwikkelaar, kan ik de eindgebruikerervaring controleren gebruikend koploze vormen.

* **Snelheid ontwikkelaar**: Als ontwikkelaar kan ik eenvoudig en consistent Sites en Forms-componenten aanpassen.

## Vereisten

+++ AEM Forms as Cloud Service Sandbox
| Name    | Program ID | Environment ID | Username | Pipeline trigger on commit | Repository URL                                                             | Front-end - branch and repo | Front-end repo name | Frontend-pipeline | Link                                              | Program URL                                                                           | Environment listing URL                                                                       | Front-end repo URL                                             | Toggles URL                                                                   |
|---------|------------|----------------|-----------------------|----------------------------|----------------------------------------------------------------------------|-----------------------------|---------------------|-------------------|---------------------------------------------------|---------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------|
| L716001 | 105303     | 986623         | L716+001@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716001-p105303-uk94266/ | yes                         | wknd                | yes               | https://author-p105303-e986623.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/105303 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/105303 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme    | https://author-p105303-e986623.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716002 | 106405     | 993047         | L716+002@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716002-p106405-uk30744/ | yes                         | wknd2               | yes               | https://author-p106405-e993047.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106405 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106405 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme2/  | https://author-p106405-e993047.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716003 | 106406     | 993049         | L716+003@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716003-p106406-uk82969/ | yes                         | wknd3               | yes               | https://author-p106406-e993049.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106406 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106406         | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme3/  | https://author-p106406-e993049.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716004 | 106398     | 993114         | L716+004@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716004-p106398-uk62851/ | yes                         | wknd4               | yes               | https://author-p106398-e993114.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106398 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106398 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme4/  | https://author-p106398-e993114.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716005 | 106407     | 993048         | L716+005@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716005-p106407-uk76414/ | yes                         | wknd5               | yes               | https://author-p106407-e993048.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106407 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106407 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme5/  | https://author-p106407-e993048.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716006 | 106408     | 993155         | L716+006@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716006-p106408-uk98879/ | yes                         | wknd6               | yes               | https://author-p106408-e993155.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106408 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106408 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme6/  | https://author-p106408-e993155.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716007 | 106343     | 993067         | L716+007@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716007-p106343-uk17215/ | yes                         | wknd7               | yes               | https://author-p106343-e993067.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106343 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106343 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme7   | https://author-p106343-e993067.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716008 | 106399     | 993108         | L716+008@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716008-p106399-uk50450/ | yes                         | wknd8               | yes               | https://author-p106399-e993108.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106399 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106399 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme8   | https://author-p106399-e993108.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716009 | 106344     | 993064         | L716+009@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716009-p106344-uk63538/ | yes                         | wknd9               | yes               | https://author-p106344-e993064.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106344 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106344 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme9/  | https://author-p106344-e993064.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716010 | 106409     | 993051         | L716+010@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716010-p106409-uk19656/ | yes                         | wknd10              | yes               | https://author-p106409-e993051.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106409 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106409 | https://git.cloudmanager.adobe.com/summit2023l716/wknd10       | https://author-p106409-e993051.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716011 | 106345     | 993060         | L716+011@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716011-p106345-uk54192/ | yes                         | wknd11              | yes               | https://author-p106345-e993060.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106345 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106345 | https://git.cloudmanager.adobe.com/summit2023l716/wknd11       | https://author-p106345-e993060.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716012 | 106346     | 993061         | L716+012@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716012-p106346-uk49638/ | yes                         | wknd12              | yes               | https://author-p106346-e993061.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106346 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106346 | https://git.cloudmanager.adobe.com/summit2023l716/wknd12       | https://author-p106346-e993061.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716013 | 106410     | 993153         | L716+013@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716013-p106410-uk94707/ | yes                         | wknd13              | yes               | https://author-p106410-e993153.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106410 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106410 | https://git.cloudmanager.adobe.com/summit2023l716/wknd13       | https://author-p106410-e993153.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716014 | 106502     | 993073         | L716+014@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716014-p106502-uk23328/ | yes                         | wknd14              | yes               | https://author-p106502-e993073.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106502 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106502 | https://git.cloudmanager.adobe.com/summit2023l716/wknd14       | https://author-p106502-e993073.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716015 | 106401     | 993112         | L716+015@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716015-p106401-uk94501/ | yes                         | wknd15              | yes               | https://author-p106401-e993112.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106401 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106401 | https://git.cloudmanager.adobe.com/summit2023l716/wknd15       | https://author-p106401-e993112.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716016 | 106452     | 993115         | L716+016@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716016-p106452-uk35087/ | yes                         | wknd16              | yes               | https://author-p106452-e993115.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106452 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106452 | https://git.cloudmanager.adobe.com/summit2023l716/wknd16       | https://author-p106452-e993115.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716017 | 106453     | 993113         | L716+017@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716017-p106453-uk55732/ | yes                         | wknd17              | yes               | https://author-p106453-e993113.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106453 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106453 | https://git.cloudmanager.adobe.com/summit2023l716/wknd17       | https://author-p106453-e993113.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716018 | 106411     | 993050         | L716+018@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716018-p106411-uk77613/ | yes                         | wknd18              | yes               | https://author-p106411-e993050.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106411 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106411 | https://git.cloudmanager.adobe.com/summit2023l716/wknd18       | https://author-p106411-e993050.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716019 | 106454     | 993116         | L716+019@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716019-p106454-uk19216/ | yes                         | wknd19              | yes               | https://author-p106454-e993116.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106454 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106454 | https://git.cloudmanager.adobe.com/summit2023l716/wknd19       | https://author-p106454-e993116.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716020 | 106347     | 993063         | L716+020@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716020-p106347-uk53952/ | yes                         | wknd20              | yes               | https://author-p106347-e993063.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106347 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106347 | https://git.cloudmanager.adobe.com/summit2023l716/wknd20       | https://author-p106347-e993063.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716021 | 106455     | 993109         | L716+021@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716021-p106455-uk24058/ | yes                         | wknd21              | yes               | https://author-p106455-e993109.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106455 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106455 | https://git.cloudmanager.adobe.com/summit2023l716/wknd21       | https://author-p106455-e993109.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716022 | 106456     | 993110         | L716+022@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716022-p106456-uk26793/ | yes                         | wknd22              | yes               | https://author-p106456-e993110.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106456 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106456 | https://git.cloudmanager.adobe.com/summit2023l716/wknd22       | https://author-p106456-e993110.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716023 | 106466     | 993291         | L716+023@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716023-p106466-uk93719/ | yes                         | wknd23              | yes               | https://author-p106466-e993291.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106466 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106466 | https://git.cloudmanager.adobe.com/summit2023l716/wknd23       | https://author-p106466-e993291.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716024 | 106413     | 993156         | L716+024@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716024-p106413-uk10856/ | yes                         | wknd24              | yes               | https://author-p106413-e993156.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106413 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106413 | https://git.cloudmanager.adobe.com/summit2023l716/wknd24       | https://author-p106413-e993156.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716025 | 106348     | 993066         | L716+025@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716025-p106348-uk76381/ | yes                         | wknd25              | yes               | https://author-p106348-e993066.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106348 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106348 | https://git.cloudmanager.adobe.com/summit2023l716/wknd25       | https://author-p106348-e993066.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716026 | 106414     | 993154         | L716+026@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716026-p106414-uk93983/ | yes                         | wknd26              | yes               | https://author-p106414-e993154.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106414 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106414 | https://git.cloudmanager.adobe.com/summit2023l716/wknd26       | https://author-p106414-e993154.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716027 | 106349     | 993065         | L716+027@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716027-p106349-uk75744/ | yes                         | wknd27              | yes               | https://author-p106349-e993065.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106349 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106349 | https://git.cloudmanager.adobe.com/summit2023l716/wknd27       | https://author-p106349-e993065.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716028 | 106415     | 993152         | L716+028@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716028-p106415-uk24248/ | yes                         | wknd28              | yes               | https://author-p106415-e993152.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106415 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106415 | https://git.cloudmanager.adobe.com/summit2023l716/wknd28       | https://author-p106415-e993152.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716029 | 106350     | 993068         | L716+029@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716029-p106350-uk06304/ | yes                         | wknd29              | yes               | https://author-p106350-e993068.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106350 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106350 | https://git.cloudmanager.adobe.com/summit2023l716/wknd29       | https://author-p106350-e993068.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716030 | 106351     | 993062         | L716+030@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716030-p106351-uk95707/ | yes                         | wknd30              | yes               | https://author-p106351-e993062.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106351 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106351 | https://git.cloudmanager.adobe.com/summit2023l716/wknd30       | https://author-p106351-e993062.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716031 | 106417     | 993158         | L716+031@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716031-p106417-uk50022/ | yes                         | wknd31              | yes               | https://author-p106417-e993158.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106417 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106417 | https://git.cloudmanager.adobe.com/summit2023l716/wknd31       | https://author-p106417-e993158.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716032 | 106418     | 993159         | L716+032@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716032-p106418-uk75663/ | yes                         | wknd32              | yes               | https://author-p106418-e993159.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106418 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106418 | https://git.cloudmanager.adobe.com/summit2023l716/wknd32       | https://author-p106418-e993159.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716033 | 106503     | 993080         | L716+033@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716033-p106503-uk29541/ | yes                         | wknd33              | yes               | https://author-p106503-e993080.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106503 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106503 | https://git.cloudmanager.adobe.com/summit2023l716/wknd33       | https://author-p106503-e993080.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716034 | 106457     | 993125         | L716+034@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716034-p106457-uk91438/ | yes                         | wknd34              | yes               | https://author-p106457-e993125.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106457 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106457 | https://git.cloudmanager.adobe.com/summit2023l716/wknd34       | https://author-p106457-e993125.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716035 | 106504     | 993081         | L716+035@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716035-p106504-uk46573/ | yes                         | wknd35              | yes               | https://author-p106504-e993081.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106504 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106504 | https://git.cloudmanager.adobe.com/summit2023l716/wknd35       | https://author-p106504-e993081.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716036 | 106458     | 993120         | L716+036@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716036-p106458-uk91382/ | yes                         | wknd36              | yes               | https://author-p106458-e993120.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106458 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106458 | https://git.cloudmanager.adobe.com/summit2023l716/wknd36       | https://author-p106458-e993120.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716037 | 106419     | 993160         | L716+037@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716037-p106419-uk99235/ | yes                         | wknd37              | yes               | https://author-p106419-e993160.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106419 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106419 | https://git.cloudmanager.adobe.com/summit2023l716/wknd37       | https://author-p106419-e993160.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716038 | 106420     | 993162         | L716+038@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716038-p106420-uk24222/ | yes                         | wknd38              | yes               | https://author-p106420-e993162.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106420 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106420 | https://git.cloudmanager.adobe.com/summit2023l716/wknd38       | https://author-p106420-e993162.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716039 | 106517     | 993235         | L716+039@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716039-p106517-uk88649/ | yes                         | wknd39              | yes               | https://author-p106517-e993235.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106517 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106517 | https://git.cloudmanager.adobe.com/summit2023l716/wknd39       | https://author-p106517-e993235.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716040 | 106506     | 993079         | L716+040@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716040-p106506-uk58481/ | yes                         | wknd40              | yes               | https://author-p106506-e993079.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106506 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106506 | https://git.cloudmanager.adobe.com/summit2023l716/wknd40       | https://author-p106506-e993079.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716041 | 106507     | 993074         | L716+041@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716041-p106507-uk39478/ | yes                         | wknd41              | yes               | https://author-p106507-e993074.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106507 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106507 | https://git.cloudmanager.adobe.com/summit2023l716/wknd41       | https://author-p106507-e993074.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716042 | 106508     | 993075         | L716+042@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716042-p106508-uk03034/ | yes                         | wknd42              | yes               | https://author-p106508-e993075.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106508 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106508 | https://git.cloudmanager.adobe.com/summit2023l716/wknd42       | https://author-p106508-e993075.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716043 | 106421     | 993163         | L716+043@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716043-p106421-uk19734/ | yes                         | wknd43              | yes               | https://author-p106421-e993163.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106421 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106421 | https://git.cloudmanager.adobe.com/summit2023l716/wknd43       | https://author-p106421-e993163.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716044 | 106459     | 993121         | L716+044@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716044-p106459-uk31012/ | yes                         | wknd44              | yes               | https://author-p106459-e993121.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106459 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106459 | https://git.cloudmanager.adobe.com/summit2023l716/wknd44       | https://author-p106459-e993121.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716045 | 106467     | 993292         | L716+045@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716045-p106467-uk08507/ | yes                         | wknd45              | yes               | https://author-p106467-e993292.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106467 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106467 | https://git.cloudmanager.adobe.com/summit2023l716/wknd45       | https://author-p106467-e993292.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716046 | 106518     | 993234         | L716+046@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716046-p106518-uk42276/ | yes                         | wknd46              | yes               | https://author-p106518-e993234.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106518 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106518 | https://git.cloudmanager.adobe.com/summit2023l716/wknd46       | https://author-p106518-e993234.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716047 | 106511     | 993076         | L716+047@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716047-p106511-uk14074/ | yes                         | wknd47              | yes               | https://author-p106511-e993076.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106511 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106511 | https://git.cloudmanager.adobe.com/summit2023l716/wknd47       | https://author-p106511-e993076.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716048 | 106512     | 993077         | L716+048@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716048-p106512-uk09248/ | yes                         | wknd48              | yes               | https://author-p106512-e993077.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106512 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106512 | https://git.cloudmanager.adobe.com/summit2023l716/wknd48       | https://author-p106512-e993077.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716049 | 106460     | 993124         | L716+049@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716049-p106460-uk30141/ | yes                         | wknd49              | yes               | https://author-p106460-e993124.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106460 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106460 | https://git.cloudmanager.adobe.com/summit2023l716/wknd49       | https://author-p106460-e993124.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716050 | 106519     | 993237         | L716+050@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716050-p106519-uk22660/ | yes                         | wknd50              | yes               | https://author-p106519-e993237.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106519 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106519 | https://git.cloudmanager.adobe.com/summit2023l716/wknd50       | https://author-p106519-e993237.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716051 | 106513     | 993084         | L716+051@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716051-p106513-uk50830/ | yes                         | wknd51              | yes               | https://author-p106513-e993084.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106513 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106513 | https://git.cloudmanager.adobe.com/summit2023l716/wknd51       | https://author-p106513-e993084.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716052 | 106461     | 993122         | L716+052@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716052-p106461-uk73956/ | yes                         | wknd52              | yes               | https://author-p106461-e993122.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106461 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106461 | https://git.cloudmanager.adobe.com/summit2023l716/wknd52       | https://author-p106461-e993122.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716053 | 106514     | 993082         | L716+053@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716053-p106514-uk25965/ | yes                         | wknd53              | yes               | https://author-p106514-e993082.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106514 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106514 | https://git.cloudmanager.adobe.com/summit2023l716/wknd53       | https://author-p106514-e993082.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716054 | 106462     | 993123         | L716+054@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716054-p106462-uk07017/ | yes                         | wknd54              | yes               | https://author-p106462-e993123.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106462 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106462 | https://git.cloudmanager.adobe.com/summit2023l716/wknd54       | https://author-p106462-e993123.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716055 | 106463     | 993127         | L716+055@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716055-p106463-uk94955/ | yes                         | wknd55              | yes               | https://author-p106463-e993127.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106463 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106463 | https://git.cloudmanager.adobe.com/summit2023l716/wknd55       | https://author-p106463-e993127.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716056 | 106515     | 993083         | L716+056@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716056-p106515-uk12658/ | yes                         | wknd56              | yes               | https://author-p106515-e993083.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106515 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106515 | https://git.cloudmanager.adobe.com/summit2023l716/wknd56       | https://author-p106515-e993083.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716057 | 106464     | 993126         | L716+057@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716057-p106464-uk13238/ | yes                         | wknd57              | yes               | https://author-p106464-e993126.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106464 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106464 | https://git.cloudmanager.adobe.com/summit2023l716/wknd57       | https://author-p106464-e993126.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716058 | 106520     | 993236         | L716+058@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716058-p106520-uk93785/ | yes                         | wknd58              | yes               | https://author-p106520-e993236.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106520 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106520 | https://git.cloudmanager.adobe.com/summit2023l716/wknd58       | https://author-p106520-e993236.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716059 | 106423     | 993161         | L716+059@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716059-p106423-uk31356/ | yes                         | wknd59              | yes               | https://author-p106423-e993161.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106423 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106423 | https://git.cloudmanager.adobe.com/summit2023l716/wknd59       | https://author-p106423-e993161.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716060 | 106516     | 993078         | L716+060@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716060-p106516-uk84089/ | yes                         | wknd60              | yes               | https://author-p106516-e993078.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106516 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106516 | https://git.cloudmanager.adobe.com/summit2023l716/wknd60       | https://author-p106516-e993078.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716061 | 106521     | 993240         | L716+061@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716061-p106521-uk14423/ | yes                         | wknd61              | yes               | https://author-p106521-e993240.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106521 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106521 | https://git.cloudmanager.adobe.com/summit2023l716/wknd61       | https://author-p106521-e993240.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716062 | 106424     | 993308         | L716+062@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716062-p106424-uk04070/ | yes                         | wknd62              | yes               | https://author-p106424-e993308.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106424 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106424 | https://git.cloudmanager.adobe.com/summit2023l716/wknd62       | https://author-p106424-e993308.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716063 | 106468     | 993295         | L716+063@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716063-p106468-uk65739/ | yes                         | wknd63              | yes               | https://author-p106468-e993295.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106468 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106468 | https://git.cloudmanager.adobe.com/summit2023l716/wknd63       | https://author-p106468-e993295.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716064 | 106425     | 993309         | L716+064@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716064-p106425-uk89411/ | yes                         | wknd64              | yes               | https://author-p106425-e993309.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106425 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106425 | https://git.cloudmanager.adobe.com/summit2023l716/wknd64       | https://author-p106425-e993309.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716065 | 106426     | 993314         | L716+065@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716065-p106426-uk38598/ | yes                         | wknd65              | yes               | https://author-p106426-e993314.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106426 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106426 | https://git.cloudmanager.adobe.com/summit2023l716/wknd65       | https://author-p106426-e993314.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716066 | 106469     | 993293         | L716+066@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716066-p106469-uk05356/ | yes                         | wknd66              | yes               | https://author-p106469-e993293.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106469 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106469 | https://git.cloudmanager.adobe.com/summit2023l716/wknd66       | https://author-p106469-e993293.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716067 | 106522     | 993238         | L716+067@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716067-p106522-uk44251/ | yes                         | wknd67              | yes               | https://author-p106522-e993238.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106522 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106522 | https://git.cloudmanager.adobe.com/summit2023l716/wknd67       | https://author-p106522-e993238.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716068 | 106470     | 993299         | L716+068@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716068-p106470-uk32462/ | yes                         | wknd68              | yes               | https://author-p106470-e993299.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106470 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106470 | https://git.cloudmanager.adobe.com/summit2023l716/wknd68       | https://author-p106470-e993299.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716069 | 106427     | 993311         | L716+069@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716069-p106427-uk83971/ | yes                         | wknd69              | yes               | https://author-p106427-e993311.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106427 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106427 | https://git.cloudmanager.adobe.com/summit2023l716/wknd69       | https://author-p106427-e993311.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716070 | 106428     | 993310         | L716+070@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716070-p106428-uk60835/ | yes                         | wknd70              | yes               | https://author-p106428-e993310.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106428 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106428 | https://git.cloudmanager.adobe.com/summit2023l716/wknd70       | https://author-p106428-e993310.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716071 | 106471     | 993298         | L716+071@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716071-p106471-uk86739/ | yes                         | wknd71              | yes               | https://author-p106471-e993298.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106471 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106471 | https://git.cloudmanager.adobe.com/summit2023l716/wknd71       | https://author-p106471-e993298.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716072 | 106429     | 993315         | L716+072@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716072-p106429-uk23084/ | yes                         | wknd72              | yes               | https://author-p106429-e993315.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106429 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106429 | https://git.cloudmanager.adobe.com/summit2023l716/wknd72       | https://author-p106429-e993315.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716073 | 106523     | 993239         | L716+073@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716073-p106523-uk23422/ | yes                         | wknd73              | yes               | https://author-p106523-e993239.adobeaemcloud.com/ | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106523 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106523 | https://git.cloudmanager.adobe.com/summit2023l716/wknd73       | https://author-p106523-e993239.adobeaemcloud.com//etc.clientlibs/toggles.json |
| L716074 | 106472     | 993300         | L716+074@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716074-p106472-uk38017/ | yes                         | wknd74              | yes               | https://author-p106472-e993300.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106472 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106472 | https://git.cloudmanager.adobe.com/summit2023l716/wknd74       | https://author-p106472-e993300.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716075 | 106430     | 993312         | L716+075@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716075-p106430-uk55913/ | yes                         | wknd75              | yes               | https://author-p106430-e993312.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106430 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106430 | https://git.cloudmanager.adobe.com/summit2023l716/wknd75       | https://author-p106430-e993312.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716076 | 106524     | 993241         | L716+076@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716076-p106524-uk94081/ | yes                         | wknd76              | yes               | https://author-p106524-e993241.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106524 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106524 | https://git.cloudmanager.adobe.com/summit2023l716/wknd76       | https://author-p106524-e993241.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716077 | 106431     | 993313         | L716+077@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716077-p106431-uk09241/ | yes                         | wknd77              | yes               | https://author-p106431-e993313.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106431 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106431 | https://git.cloudmanager.adobe.com/summit2023l716/wknd77       | https://author-p106431-e993313.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716078 | 106473     | 993294         | L716+078@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716078-p106473-uk84023/ | yes                         | wknd78              | yes               | https://author-p106473-e993294.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106473 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106473 | https://git.cloudmanager.adobe.com/summit2023l716/wknd78       | https://author-p106473-e993294.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716079 | 106474     | 993297         | L716+079@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716079-p106474-uk83600/ | yes                         | wknd79              | yes               | https://author-p106474-e993297.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106474 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106474 | https://git.cloudmanager.adobe.com/summit2023l716/wknd79       | https://author-p106474-e993297.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716080 | 106475     | 993296         | L716+080@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716080-p106475-uk94755/ | yes                         | wknd80              | yes               | https://author-p106475-e993296.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106475 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106475 | https://git.cloudmanager.adobe.com/summit2023l716/wknd80       | https://author-p106475-e993296.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716081 | 106476     | 993353         | L716+081@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716081-p106476-uk50558/ | yes                         | wknd81              | yes               | https://author-p106476-e993353.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106476 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106476 | https://git.cloudmanager.adobe.com/summit2023l716/wknd81       | https://author-p106476-e993353.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716082 | 106525     | 993247         | L716+082@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716082-p106525-uk92893/ | yes                         | wknd82              | yes               | https://author-p106525-e993247.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106525 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106525 | https://git.cloudmanager.adobe.com/summit2023l716/wknd82       | https://author-p106525-e993247.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716083 | 106526     | 993244         | L716+083@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716083-p106526-uk35635/ | yes                         | wknd83              | yes               | https://author-p106526-e993244.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106526 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106526 | https://git.cloudmanager.adobe.com/summit2023l716/wknd83       | https://author-p106526-e993244.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716084 | 106527     | 993243         | L716+084@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716084-p106527-uk33428/ | yes                         | wknd84              | yes               | https://author-p106527-e993243.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106527 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106527 | https://git.cloudmanager.adobe.com/summit2023l716/wknd84       | https://author-p106527-e993243.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716085 | 106477     | 993356         | L716+085@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716085-p106477-uk07483/ | yes                         | wknd85              | yes               | https://author-p106477-e993356.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106477 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106477 | https://git.cloudmanager.adobe.com/summit2023l716/wknd85       | https://author-p106477-e993356.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716086 | 106478     | 993355         | L716+086@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716086-p106478-uk19752/ | yes                         | wknd86              | yes               | https://author-p106478-e993355.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106478 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106478 | https://git.cloudmanager.adobe.com/summit2023l716/wknd86       | https://author-p106478-e993355.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716087 | 106528     | 993245         | L716+087@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716087-p106528-uk65196/ | yes                         | wknd87              | yes               | https://author-p106528-e993245.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106528 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106528 | https://git.cloudmanager.adobe.com/summit2023l716/wknd87       | https://author-p106528-e993245.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716088 | 106432     | 993316         | L716+088@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716088-p106432-uk71669/ | yes                         | wknd88              | yes               | https://author-p106432-e993316.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106432 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106432 | https://git.cloudmanager.adobe.com/summit2023l716/wknd88       | https://author-p106432-e993316.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716089 | 106529     | 993242         | L716+089@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716089-p106529-uk72336/ | yes                         | wknd89              | yes               | https://author-p106529-e993242.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106529 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106529 | https://git.cloudmanager.adobe.com/summit2023l716/wknd89       | https://author-p106529-e993242.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716090 | 106436     | 993320         | L716+090@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716090-p106436-uk96513/ | yes                         | wknd90              | yes               | https://author-p106436-e993320.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106436 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106436 | https://git.cloudmanager.adobe.com/summit2023l716/wknd90       | https://author-p106436-e993320.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716091 | 106480     | 993301         | L716+091@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716091-p106480-uk26189/ | yes                         | wknd91              | yes               | https://author-p106480-e993301.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106480 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106480 | https://git.cloudmanager.adobe.com/summit2023l716/wknd91       | https://author-p106480-e993301.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716092 | 106530     | 993246         | L716+092@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716092-p106530-uk21496/ | yes                         | wknd92              | yes               | https://author-p106530-e993246.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106530 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106530 | https://git.cloudmanager.adobe.com/summit2023l716/wknd92       | https://author-p106530-e993246.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716093 | 106481     | 993352         | L716+093@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716093-p106481-uk08136/ | yes                         | wknd93              | yes               | https://author-p106481-e993352.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106481 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106481 | https://git.cloudmanager.adobe.com/summit2023l716/wknd93       | https://author-p106481-e993352.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716094 | 106482     | 993354         | L716+094@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716094-p106482-uk12991/ | yes                         | wknd94              | yes               | https://author-p106482-e993354.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106482 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106482 | https://git.cloudmanager.adobe.com/summit2023l716/wknd94       | https://author-p106482-e993354.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716095 | 106531     | 993248         | L716+095@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716095-p106531-uk35835/ | yes                         | wknd95              | yes               | https://author-p106531-e993248.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106531 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106531 | https://git.cloudmanager.adobe.com/summit2023l716/wknd95       | https://author-p106531-e993248.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716096 | 106483     | 993357         | L716+096@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716096-p106483-uk62544/ | yes                         | wknd96              | yes               | https://author-p106483-e993357.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106483 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106483 | https://git.cloudmanager.adobe.com/summit2023l716/wknd96       | https://author-p106483-e993357.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716097 | 106433     | 993318         | L716+097@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716097-p106433-uk01013/ | yes                         | wknd97              | yes               | https://author-p106433-e993318.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106433 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106433 | https://git.cloudmanager.adobe.com/summit2023l716/wknd97       | https://author-p106433-e993318.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716098 | 106532     | 993249         | L716+098@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716098-p106532-uk23995/ | yes                         | wknd98              | yes               | https://author-p106532-e993249.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106532 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106532 | https://git.cloudmanager.adobe.com/summit2023l716/wknd98       | https://author-p106532-e993249.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716099 | 106434     | 993317         | L716+099@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716099-p106434-uk60991/ | yes                         | wknd99              | yes               | https://author-p106434-e993317.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106434 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106434 | https://git.cloudmanager.adobe.com/summit2023l716/wknd99       | https://author-p106434-e993317.adobeaemcloud.com/etc.clientlibs/toggles.json  |
| L716100 | 106435     | 993319         | L716+100@summitlab.us | yes                        | https://git.cloudmanager.adobe.com/summit2023l716/L716100-p106435-uk70663/ | yes                         | wknd100             | yes               | https://author-p106435-e993319.adobeaemcloud.com  | https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106435 | https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106435 | https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme100 | https://author-p106435-e993319.adobeaemcloud.com/etc.clientlibs/toggles.json  |

+++


## Les 1

### Doelstelling

Verken uzelf met de as a Cloud Service AEM Forms-omgeving.

### Lessencontext

In deze les, vertrouwt u zich met het as a Cloud Service milieu van AEM Forms door het gebruikersinterface te navigeren.

### Uitoefening

1. Open uw browser en ga URL van het auteursmilieu van de Cloud Service in. Bijvoorbeeld:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Meld u aan bij de ontwikkelomgeving van de Cloud Service volgens de gedeelde referenties. Bijvoorbeeld: Gebruikersnaam: [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
Wachtwoord: 
**Adobe123!**

1. Nadat u bent aangemeld, navigeert u naar de gebruikersinterface van AEM Forms. Klikken **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Klikken **Forms &amp; Documenten**. Pop-ups met betrekking tot voorkeuren of gegevens negeren.

   ![](/help/forms/assets/screenshot2028113929.png)

   Alle beschikbare formulieren worden weergegeven.

   ![](/help/forms/assets/screenshot2028114029.png)

## Les 2

### Doelstelling

Ontwerp een adaptief formulier met de nieuwste kerncomponenten, configureer het formulier en verzend het.

## Lessencontext

In deze les zult u als zakelijke gebruiker een adaptief formulier ontwerpen voor meerdere kanalen, zoals web, mobiel en chatten met behulp van adaptieve formulieren die zijn ontworpen met gestandaardiseerde OTB-kerncomponenten voor het vastleggen van gegevens.

## Uitoefening

1. Maak een verzendeindpunt voor het formulier:

   1. Openen <https://requestbin.com/> in een nieuw browsertabblad.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Klikken **Een openbare map maken** en kopieer de URL van het eindpunt.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Ontwerp een adaptief formulier met de wizard-interface:

   1. Navigeer in het browsertabblad dat wordt gebruikt in Les 1 naar AEM Forms als Cloud Service-webinterface en navigeer naar Forms en Documenten.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Klikken **Maken** en selecteer Adaptief formulier.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Selecteer **Leeg met kerncomponenten** sjabloon in het scherm Sjabloonselectie, zoals hieronder wordt weergegeven:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Klik op de knop **Stijl** en selecteert u de **wknd-thema** thema zoals hieronder getoond:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Klik op de knop **Indiening** en selecteert u de **Verzenden naar REST-eindpunt** en geeft u de openbare map op in het dialoogvenster
      **URL voor het verzoek van de POST** veld zoals hieronder weergegeven:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Klikken **Maken**. Geef een naam en titel op voor het formulier. Bijvoorbeeld: **contactus**. Klikken **Maken**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. De aangepaste formuliereditor wordt geopend. Pop-ups of dialoogvensters voor voorkeuren of informatie negeren. Klik op de componentenbrowser op de linkerrails en voeg de **Voettekst** onder aan het lege formulier.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. Voeg de **Koptekst** aan de bovenkant van het formulier.
      ![](/help/forms/assets/screenshot2028122029.png)

   1. Voeg een **Titel** in het midden van het formulier.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Voeg een **Tekstinvoer** na de titelcomponent.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Voeg een **Nummerinvoer** component.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Voeg een **Verzendknop** aan het formulier.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Klik op de knop **Titel** component zodat **pop-upmenu** wordt weergegeven. Klik op de knop **Pictogram Bewerken** in het menu om de label te bewerken.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Enter `Contact Us` als de titeltekst.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Klik op de knop **Tekstinvoer** zodat het pop-upmenu wordt weergegeven. Klik op de knop **Pictogram Bewerken** in het menu om de label te bewerken.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Enter **Volledige naam** als veldlabel.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Klik op de knop **Nummerinvoer** zodat het pop-upmenu wordt weergegeven. Klik op de knop **Pictogram Bewerken** in het menu om de label te bewerken.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Voer de **Telefoonnummer** als veldlabel.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Validaties toevoegen aan formulier:

   1. Klik op de knop **Telefoonnummer** zodat het pop-upmenu wordt weergegeven. Klik op de knop **Perictogram** in het menu om het veld te configureren.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Open de **validatie, tabblad** markeren **Vereist** en klik op **Gereed**. Het succesbericht wordt weergegeven.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Klikken **Voorvertoning** om een voorbeeld van het formulier te bekijken vanuit het perspectief van de eindgebruiker.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Het formulier vullen met dummygegevens
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Het formulier verzenden
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Controleer de verzonden gegevens op het tabblad Aanvraagvak.
      ![](/help/forms/assets/screenshot2028125829.png)

Gebruik nu voor de resterende bewerking een vooraf gemaakt registratieformulier.

1. Open bijvoorbeeld de AEM Forms-beheerinterface. `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`en selecteert u het registratieformulier.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Klikken **Publiceren**.

   ![](/help/forms/assets/screenshot2028115629.png)

   Het succesbericht wordt weergegeven.

   ![](/help/forms/assets/screenshot2028115729.png)

   De publicatie-URL van het formulier lijkt op `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Als u het gepubliceerde formulier wilt weergeven, vervangt u de programma-id (pXXXXXX) en de milieu-id (eXXXXXX) in de bovenstaande URL door id&#39;s van uw omgeving.

## Les 3

### Doelstelling

Werk stijlen bij met behulp van best practices voor ontwikkeling vooraf.

### Lessencontext

In deze les leert u als front-end ontwikkelaar hoe u de opmaak van het eerder gemaakte adaptieve formulier eenvoudig kunt bijwerken.

### Uitoefening

Stel de lokale opslagruimte van het thema in:

1. Open de Herinnering of shell van het Bevel met beheerderrechten:

   ![](/help/forms/assets/screenshot2028115829.png)

1. Voor de Herinnering van het Bevel, gebruik het volgende bevel om te navigeren aan **c:\git** map

   ```Shell
   cd c:\git
   ```

1. Gebruik de volgende opdracht om de themafrontend-code te klonen:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Gebruik de volgende opdracht in de vermelde volgorde om naar de **aem-forms-theme-canvas** directory en open de Code van Visual Studio.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Selecteren **De auteurs van alle bestanden in de bovenliggende map vertrouwen** en klik op **Ja, ik vertrouw de auteurs**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Als u het formulier wilt weergeven dat wordt gehost in de publicatieomgeving van uw cloudservice, wijzigt u de naam van de `env_template` bestand.  Als u de naam van het bestand wilt wijzigen, klikt u met de rechtermuisknop op de knop **env_template** en selecteer de **Naam wijzigen** optie.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Stel de volgende waarden in voor de variabelen in het .env-bestand en sla het bestand op:

   * **AEM_URL**: Geef uw publicatieomgeving voor de cloudservice op. Bijvoorbeeld, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Geef het pad van het formulier op. Als het formulierpad bijvoorbeeld `/content/forms/af/registration`de waarde van deze variabele `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Voer in het venster Opdrachtprompt de volgende opdracht uit:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Als u een bericht ontvangt waarin u wordt gevraagd om Npm bij te werken via het dialoogvenster `npm notice Run npm nstall -g npm@9.6.0`, negeert u het bericht.
   > * Stel geen andere npm bevelen in werking tenzij geïnstrueerd in het werkboek.


1. Voer nu de volgende opdracht uit om een voorbeeld van het formulier te bekijken.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Zodra het bovenstaande bevel wordt uitgevoerd, wacht op `webpack compiled` bericht. Het formulier wordt weergegeven op een browsertabblad.

   >[!NOTE]
   >
   >Als u een leeg scherm in browser ervaart nadat u de opdracht `npm run live` gebruiken voor meer dan 3-4 minuten, wijzigen `localhost` in browser URL naar 127.0.0.1 en druk op **Enter**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. In de Code van Visual Studio, open `PROJECT\src\site\_variables.scss` bestand. Let op: `$error` kleur is een kleur van RED.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Verstuur het formulier in de browser om de rode kleur in het dialoogvenster **Voornaam** veld.

   ![](/help/forms/assets/screenshot2028120829.png)

1. Stel de **$error** kleur naar **#5736eb** en sla het bestand op.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Vernieuw de browser en verzend het formulier. De kleur van de foutmelding in het veld Voornaam is dienovereenkomstig gewijzigd.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Druk in de opdrachtprompt op **CTRL+C**, enter **Y** en drukken **Enter** sleutel om het npm proces te beëindigen. Het is belangrijk om de npm server tegen te houden zodat strijdt het niet met de volgende reeks oefeningen.
1. Sluit de Code van Visual Studio en de Snelle vensters van het Bevel.

## Les 4

### Doelstelling

Het formulier weergeven op web/mobiele en andere interfaces als een headless-formulier.

### Lessencontext

In deze les leert u als ontwikkelaar vooraf hoe u het adaptieve formulier dat u eerder hebt gemaakt, kunt weergeven als een vorm zonder kop met behulp van het raamwerk voor het ontwerpen van het spectrum met reacties.

### Uitoefening

De lokale bewaarplaats van de opstelling gebruikend reactie starter project:

1. Open de Herinnering van het Bevel gebruikend beheerderrechten.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Voor de Herinnering van het Bevel, gebruik het volgende bevel om te navigeren aan **c:\git** map

   ```Shell
   cd c:\git
   ```

1. Gebruik de volgende opdracht om het aanpasbare formulier te klonen om te starten:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Gebruik de volgende opdrachten in de vermelde volgorde om naar de **response-starter-kit-aem-headless-forms** directory en open de Code van Visual Studio.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Het venster van de Code van Visual Studio opent.

   ![](/help/forms/assets/screenshot2028117429.png)

U kunt als volgt het formulier weergeven dat wordt gehost op uw cloudservice-publicatieomgeving:

1. Wijzig de naam van het env_template-bestand in .env-bestand. Als u de naam wilt wijzigen, klikt u met de rechtermuisknop op de knop **env_template** en selecteer de **Naam wijzigen** optie.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Stel de volgende waarden in voor de variabelen in het .env-bestand. Sla het bestand op nadat u de variabelen hebt bijgewerkt.

   * **AEM_URL**: Geef de URL van de publicatieomgeving van de cloudservice op. Bijvoorbeeld, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Geef het pad op van het adaptieve formulier dat in de vorige les is gemaakt. Bijvoorbeeld, `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Open het opdrachtvenster, controleer of u zich in de map met formulieren zonder hoofdletter en hoofdletter bevindt voor de reactie en voer de volgende opdracht uit:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Voer in het venster Opdrachtprompt de volgende opdracht uit:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   Met de bovenstaande opdracht start u een lokale ontwikkelingsserver waarmee de formulierdefinitie die is opgehaald van AEM, zonder kop wordt weergegeven met behulp van de frontend bibliotheek met het spectrum voor reacties.

   >[!NOTE]
   >
   > 
   > Als u een leeg scherm in browser ervaart nadat u de opdracht `npm start` gebruiken voor meer dan 3-4 minuten, wijzigen `localhost` in browser URL naar 127.0.0.1 en druk op **Enter**.

   ![](/help/forms/assets/screenshot2028118229.png)

Laten we de uitvoering van regels in deze vorm zonder kop controleren:

1. Selecteer **Schakel het selectievakje in als u 5% korting wilt ontvangen** optie. De volgende optie voor het toepassen van een creditcard is uitgeschakeld.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Uitschakelen **Schakel het selectievakje in als u 5% korting wilt ontvangen** om de optie creditcard in te schakelen.

   ![](/help/forms/assets/screenshot2028126329.png)

We brengen wijzigingen aan in het formulier op de server als een zakelijke gebruiker. Wijzigingen worden dan automatisch doorgevoerd in het formulier zonder kop.

1. Open de AEM Forms-beheerinterface in de browser. Bijvoorbeeld: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Selecteer **registratie** formulier en klik op **Bewerken.** Het formulier wordt geopend in de editor voor adaptieve formulieren.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Selecteer **Telefoonnummer** en klik op de knop **Bewerkingspictogram (potloodpictogram)** in de werkbalk. Als u de pop-upwerkbalk niet kunt zien, schakelt u over naar de modus Bewerken door op **Bewerken** knop rechtsboven, links naar **Voorvertoning** knop.

   ![](/help/forms/assets/screenshot2028119629.png)

1. Wijzig het label in Mobiel nummer. Klik op een lege ruimte in het formulier en de wijzigingen die in het formulier zijn aangebracht, worden opgeslagen.

   ![](/help/forms/assets/screenshot2028119729.png)

Laten we het bijgewerkte formulier publiceren om de wijzigingen in de publicatieomgeving door te geven.

1. Selecteer het registratieformulier op het tabblad AEM Forms-beheerinterface en klik op **Publiceren ongedaan maken**. Als u de **Publiceren ongedaan maken** gaat u naar stap 3 om de wijzigingen rechtstreeks te publiceren.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Klikken **Publiceren ongedaan maken**. Klikken **Sluiten** in de respectieve dialoog.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Nadat de browser is vernieuwd, selecteert u het registratieformulier en klikt u op **Publiceren**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Klikken **Publiceren**. Klikken **Sluiten** in de respectieve dialoog.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Vernieuw de browsertab met de koploze vorm. Het label Telefoonnummer is gewijzigd in Mobiel nummer.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Open het venster Opdrachtprompt waarmee het dialoogvenster **response-starter-kit-aem-headless-forms** project, pers **CTRL+C** en vervolgens voert u **Y** en druk op Enter om het npm-proces te beëindigen. Het is belangrijk om de npm server tegen te houden zodat strijdt het niet met de volgende reeks oefeningen.

1. Sluit de Code van Visual Studio en de Snelle vensters van het Bevel.


## Les 5

### Doelstelling

Het formulier weergeven als een formulier zonder kop met de gebruikersinterface voor Google-materiaal

### Lessencontext

In deze les leert u als ontwikkelaar aan de voorzijde hoe u het adaptieve formulier dat u eerder hebt gemaakt, kunt weergeven als een formulier zonder kop met de gebruikersinterface van Google Material.

### Uitoefening

Stel lokale opslagruimte in met een project voor het starten van een materiaalinterface:

1. Open de Herinnering van het Bevel gebruikend beheerderrechten.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Voor de Herinnering van het Bevel, gebruik het volgende bevel om te navigeren aan **c:\git** map:

   ```Shell
   cd c:\git
   ```

1. Voer de volgende opdrachten in de vermelde volgorde uit om een map met de naam mui te maken en naar de map mui te navigeren met de volgende opdrachten:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Gebruik de volgende opdracht om het aanpasbare formulier te klonen om te starten:

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Gebruik de volgende opdracht in de vermelde volgorde om naar de **response-starter-kit-aem-headless-forms** omslag en open de code in de Code van Visual Studio:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

U kunt als volgt het formulier weergeven dat wordt gehost op uw cloudservice-publicatieomgeving:

1. De naam van de **env_template** bestand naar **.env** bestand. Als u de naam wilt wijzigen, klikt u met de rechtermuisknop op de knop **env_template** bestand en selecteer **Naam wijzigen**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Stel de volgende waarden in voor de variabelen in het .env-bestand. Sla het bestand op nadat u de variabelen hebt bijgewerkt. Gebruik de **CTRL + S** overschakelen op een andere combinatie om het bestand op te slaan.

   * **AEM_URL**: Geef de URL van de publicatieomgeving van de cloudservice op. Bijvoorbeeld: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: Geef het pad op van het adaptieve formulier dat in de vorige les is gemaakt. Bijvoorbeeld: /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. Open het opdrachtvenster en zorg dat u zich bij de **response-starter-kit-aem-headless-forms** en voer de volgende opdracht uit:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Voer in het venster Opdrachtprompt de volgende opdracht uit:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   Met de opdracht wordt een lokale ontwikkelingsserver gestart en wordt de formulierdefinitie zonder kop opgehaald van AEM met behulp van de Google Material UI frontend-bibliotheek.

   >[!NOTE]
   >
   >Als u een leeg scherm in browser ervaart nadat u de opdracht `npm start` gebruiken voor meer dan 3-4 minuten, wijzigen `localhost` in browser URL naar 127.0.0.1 en druk op **Enter**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. U kunt als volgt de uitvoering van dezelfde bedrijfslogica in deze formulieruitvoering evalueren:

   Selecteren **Schakel het selectievakje in als u 5% korting wilt ontvangen**. De volgende optie **Wilt u een aanvraag indienen voor het formulier voor creditcard van bedrijven?** wordt uitgeschakeld.

   ![](/help/forms/assets/screenshot2028127329.png)

## Les 6

### Doelstelling

Een ander uiterlijk van de vorm zonder kop maken met behulp van variaties in de materiaalinterface

### Lessencontext

In deze les leert u als front-end ontwikkelaar hoe u een alternatieve representatie van verschillende componenten kunt maken met behulp van materiaalinterface voor het adaptieve formulier dat eerder door de zakelijke gebruiker is gemaakt.

### Uitoefening

Werk de variatie van componenten in het hoofdloze project bij. De variant van de materiaalinterface-tekstinvoercomponent wijzigen in `OutlinedInput`:

1. In Visuele Code, navigeer aan de component van de tekstinput door te openen `index.tsx` bestand bij `src/components/textinput/index.tsx`.

1. Toevoegen `//` aan het begin van coderegel 103. De regel wordt omgezet in een opmerking.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Voeg het volgende toe op regel 104 om een andere variant van component te gebruiken en het dossier op te slaan. Gebruik de **CTRL + S** overschakelen op een andere combinatie om het bestand op te slaan.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Het is essentieel om correcte kapitalisatie voor &quot;OutlinedInput&quot;variant anders te gebruiken zou compilatie ontbreken. De lokale compilatie van de ontwikkelomgeving begint automatisch in de Herinnering van het Bevel. Wacht tot u het volgende bericht ziet

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Vernieuw de browser als deze niet automatisch wordt vernieuwd om te zien hoe de component voor tekstinvoer een andere variant gebruikt.

   ![](/help/forms/assets/screenshot2028127729.png)


   Deze wijziging vindt plaats voor eindgebruikers zonder dat de formulierdefinitie wordt gewijzigd op AEM Forms Server en is specifiek voor het kanaal zonder kop in kwestie. Bijvoorbeeld, Webkanaal in dit laboratorium.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Sluit de Code van Visual Studio en de Snelle Vensters van het Bevel.

## Veelgestelde vragen

+++ Is de wizard Adaptief formulier openbaar?

Ja, het is beschikbaar bij AEM Forms als Cloud Service.

+++


+++ Zijn de kerncomponenten openbaar?

Ja, Adaptive Forms core-componenten zijn beschikbaar met AEM Forms als Cloud Service.

+++

+++ Zijn krantenloze formulieren openbaar?

Ja, koploze formulieren zijn beschikbaar met AEM Forms als Cloud Service.

+++

+++ Vereisen de Hoofdloze vormen een afzonderlijke vergunning?

Nee, voor Headless-formulieren wordt dezelfde licentiewaarde gebruikt, uitgedrukt in het aantal verzonden formulieren.

+++

+++ Zijn de componenten van de Kern en Zwaarloze vormen beschikbaar met AEM 6.5 Forms?

Ja, beide adaptieve formulieren bevatten kerncomponenten en headless formulieren die beschikbaar zijn met AEM Forms 6.5 Service Pack 16 en hoger.

+++


## Volgende stappen

Nu u hebt geleerd hoe u adaptieve formulieren kunt maken en deze op meerdere kanalen kunt aanbieden met behulp van headless-formulieren, moet u proberen uw nieuwe vaardigheden in werking te stellen. Maak plezier en ga door met het creëren en leveren van uitzonderlijke ervaringen voor het vastleggen van gegevens aan uw eindgebruikers, waar ze zich bevinden, op schaal!

## Bronnen

* [Inleiding van de kerncomponenten van Adaptive Form](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [Adaptief formulier maken met behulp van kerncomponenten](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Update styling voor kern op component-gebaseerde AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Hoofdloze adaptieve formulieren](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Startkit voor Headless React gebruiken](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)


