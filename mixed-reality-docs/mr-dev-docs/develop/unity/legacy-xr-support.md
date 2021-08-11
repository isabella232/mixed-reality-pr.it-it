---
title: Uso del supporto XR incorporato legacy
description: Informazioni su come configurare i progetti Unity con e senza MRTK usando il supporto XR incorporato legacy.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, introduzione, nuovo progetto, Windows Mixed Reality, UWP, XR, prestazioni, legacy, mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192060"
---
# <a name="using-legacy-built-in-xr-support"></a>Uso del supporto XR incorporato legacy

## <a name="setting-up-your-project-with-mrtk"></a>Configurazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Provare le esercitazioni su MRTK](./tutorials/mr-learning-base-02.md?tabs=wsa)

Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>Configurazione manuale senza MRTK

Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:

![Screenshot della finestra build Impostazioni aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

Se la destinazione è HoloLens 2, è necessario passare alla piattaforma Windows universali:

1.  Selezionare **File > Compilazione Impostazioni...**
2.  Selezionare **Universal Windows Platform nell'elenco** Platform (Piattaforma) e selezionare Switch Platform **(Cambia piattaforma)**
3.  Impostare **Architecture (Architettura)** **su ARM 64**
4.  Impostare **Dispositivo di destinazione** su **HoloLens**
5.  Impostare **Tipo di compilazione** su **D3D**
6.  Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**
7.  Impostare **La configurazione della build** su **Rilascio** perché sono presenti problemi di prestazioni noti con debug

![Screenshot della finestra Build Impostazioni aperta nell'editor di Unity con universal Windows Platform evidenziato](images/wmr-config-img-4.png)

Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.

> [!CAUTION]
> XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.

1. Aprire **Player Impostazioni...** dalla finestra **di Impostazioni... ed** espandere il **gruppo di Impostazioni XR**
2. Nella sezione **XR Impostazioni** selezionare **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)
3. Impostare **Depth Format (Formato profondità)** su **Depth (Profondità) a 16 bit** e abilitare Depth Buffer Sharing **(Condivisione buffer di profondità)**
4. Impostare **La modalità di rendering stereo** su Istanza a passaggio **singolo**
5. Selezionare **WSA Holographic Remoting Supported** se si desidera usare holographic remoting 

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con la sezione Player settings evidenziata](images/wmr-config-img-9.png)