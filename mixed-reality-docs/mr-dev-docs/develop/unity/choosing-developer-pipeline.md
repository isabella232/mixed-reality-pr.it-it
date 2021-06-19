---
title: Scelta della pipeline di sviluppo
description: Rimanere aggiornati sulle raccomandazioni più recenti sulla pipeline di sviluppo unity per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394555"
---
# <a name="choosing-your-developer-pipeline"></a>Scelta della pipeline di sviluppo

![Banner con logo di Unity](../images/unity_logo_banner.png)<br>

Anche se attualmente è consigliabile installare **Unity 2019.4 LTS** e usare XR incorporato legacy per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.

## <a name="mixed-reality-toolkit-recommended"></a>Mixed Reality Toolkit (scelta consigliata)

La configurazione di Unity consigliata di Microsoft per HoloLens 2 è Mixed Reality Toolkit...

### <a name="install-the-mixed-reality-feature-tool"></a>Installare lo strumento di funzionalità di realtà mista

Lo [strumento funzionalità realtà mista](welcome-to-mr-feature-tool.md) è un nuovo modo per consentire agli sviluppatori di individuare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity. 

È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a>Importazione di Mixed Reality Toolkit per Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. 

* Installare il pacchetto Mixed Reality Toolkit seguendo le istruzioni di installazione e [utilizzo](welcome-to-mr-feature-tool.md#system-requirements) e selezionando il **pacchetto Mixed Reality Toolkit Foundation.**

È consigliabile completare la sezione introduttiva nei percorsi di [sviluppo di HoloLens](unity-development-overview.md#1-getting-started) o [VR](unity-development-wmr-overview.md#1-getting-started) curati. Se si sta già seguendo il percorso di sviluppo con Unity per HoloLens, completare i rimanenti passaggi di configurazione elencati di seguito e proseguire con le [esercitazioni introduttive su HoloLens 2](tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Si noti che le istruzioni di installazione sono destinate alla più recente combinazione stabile di versioni di MRTK e Unity, ovvero **MRTK 2.6.1** e **Unity 2019.4 LTS.**

> [!NOTE]
> Se non si vuole usare MRTK per Unity, è necessario creare uno script di tutte le interazioni [e i comportamenti manualmente.](configure-unity-project.md)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Banner di Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a>Manuale 

Tbd...