---
title: Uso del supporto di XR incorporato legacy
description: Informazioni su come configurare i progetti Unity con e senza MRTK usando il supporto integrato per la versione precedente di XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni, legacy, MRTK
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938138"
---
# <a name="using-legacy-built-in-xr-support"></a>Uso del supporto di XR incorporato legacy

## <a name="setting-up-your-project-with-mrtk"></a>Impostazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Prova le nostre esercitazioni su MRTK](tutorials/mr-learning-base-01.md)

Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](/windows/mixed-reality/mrtk-unity) .

## <a name="manual-setup-without-mrtk"></a>Installazione manuale senza MRTK

Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):

1.  Seleziona **File > impostazioni di compilazione...**
2.  Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )
3.  Impostare l' **architettura** su **ARM 64**
4.  Impostare il **dispositivo di destinazione** su **HoloLens**
5.  Imposta **tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK** sull' **ultima versione installata**
7.  Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

> [!CAUTION]
> La versione precedente di XR è deprecata in Unity 2019 ed è stata rimossa in Unity 2020.

1. Apri **Impostazioni lettore...** dalle **impostazioni di compilazione... ed espandere il gruppo di** **impostazioni di XR**
2. Nella sezione **impostazioni di XR** selezionare **realtà virtuale supportata** per aggiungere l'elenco dispositivi della realtà virtuale
3. Imposta la profondità del **formato** a **16 bit** e Abilita la **condivisione del buffer di profondità**
4. Impostare la **modalità di rendering stereo** su **istanza Single Pass**
5. Selezionare la **comunicazione remota per WSA olografica supportata** se si vuole usare la comunicazione remota olografica 

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione delle impostazioni del lettore evidenziata](images/wmr-config-img-9.png)