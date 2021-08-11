---
title: Configurazione del progetto Unreal
description: Informazioni su come configurare il progetto con la versione più recente di Unreal Engine e dello strumento di funzionalità di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realtà mista, sviluppo, funzionalità, nuovo progetto, emulatore, documentazione, guide, ologrammi, sviluppo di giochi, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 546dcbac09600402b50408e016507b4d15fac22c58be8c1b3d68331dc5320252
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225409"
---
# <a name="setting-up-your-unreal-project"></a>Configurazione del progetto Unreal

È consigliabile installare [Unreal Engine versione 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o versione successiva per sfruttare appieno il supporto di HoloLens incorporato.

Passare alla scheda **Libreria in Epic** Games Launcher, selezionare la freccia a discesa accanto a Launch **(Avvia)** e fare clic su **Options (Opzioni).** In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).
![Opzione di installazione unreal HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importare Toolkit realtà mista per Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. Il toolkit permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR.

Per l'installazione, è consigliabile completare la [sezione introduttiva](unreal-development-overview.md#1-getting-started) del nostro [percorso di sviluppo con Unreal](unreal-development-overview.md). Se si sta già seguendo il percorso di sviluppo con Unreal, completare il resto dei passaggi di configurazione elencati di seguito e proseguire con le [esercitazioni introduttive su HoloLens 2](tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Immagine del logo di Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se non si vuole usare MRTK per Unreal, sarà necessario creare personalmente script per tutti i comportamenti e le interazioni.