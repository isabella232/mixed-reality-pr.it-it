---
title: Audio spaziale in Unity
description: Riprodurre un suono spaziale da uno specifico punto 3D nella scena Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684612"
---
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

Questa pagina contiene collegamenti a risorse per il suono spaziale in Unity.

## <a name="spatializer-options"></a>Opzioni di Spatializer
Le opzioni di Spatializer per le applicazioni di realtà mista includono:
* *SPATIALIZER HRTF MS* . Unity fornisce questo elemento come parte del pacchetto facoltativo di *realtà mista di Windows* .
  * Questa operazione viene eseguita sulla CPU in un'architettura a "singola origine" con costi più elevati.
  * Questa operazione viene fornita per garantire la compatibilità con le versioni precedenti delle applicazioni HoloLens originali.
* *Microsoft Spatializer* . Questa operazione è disponibile dal [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Questa operazione usa un'architettura a più livelli di costo inferiore.
  * In HoloLens 2 questa operazione viene scaricata in un acceleratore hardware.

Per le nuove applicazioni, è consigliabile *Microsoft Spatializer* .

## <a name="enable-spatialization"></a>Abilita spazializzazione

Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft. SpatialAudio. Spatializer. Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto. Quindi:
* Alleghi un' **origine audio** a un oggetto nella gerarchia
* Selezionare la casella di controllo **Abilita spazializzazione**
* Spostare il dispositivo di scorrimento di **Blend spaziale** su "1"
* Verificare che l'audio spaziale sia abilitato nella workstation per sviluppatori. Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni e verificare che l'audio spaziale sia impostato su un valore diverso da "off". Per ottenere la migliore rappresentazione delle informazioni su HoloLens 2, scegliere **Windows Sonic per le cuffie** .

>[!NOTE]
>Se si verifica un errore in Unity che non è in grado di caricare il plug-in Microsoft. SpatialAudio. Spatializer. Unity, perché una delle relative dipendenze non è presente, verificare di disporre della versione più recente di [Microsoft Visual C++ ridistribuibile](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installata nel computer.

Per informazioni dettagliate, vedere:
* [Repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Esercitazione di Spatializer di Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentazione di Unity Spatializer](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Attenuazione basate sulla distanza
Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico. Queste impostazioni possono essere usate per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente. Per informazioni dettagliate, vedere:
* [Progettazione audio in realtà mista](../../design/spatial-sound-design.md) per le impostazioni consigliate.
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per istruzioni sull'impostazione di queste curve.

## <a name="reverb"></a>Riverbero
_Microsoft Spatializer_ Disabilita gli effetti post-Spatializer per impostazione predefinita. Per abilitare il riverbero e altri effetti per le origini spaziali:
* Alleghi il componente del **livello di invio dell'effetto chat** a ogni origine
* Modificare la curva del livello di invio per ogni origine, per controllare il guadagno sull'audio restituito al grafico per l'elaborazione degli effetti

Per informazioni dettagliate, vedere [il capitolo 5 dell'esercitazione su Spatializer](tutorials/unity-spatial-audio-ch5.md) .

## <a name="unity-spatial-sound-examples"></a>Esempi di suoni spaziali Unity
Per esempi di suoni spaziali in Unity, vedere:
* [Demo di MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Progetto di esempio Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Checkpoint di sviluppo successivo

Se si sta seguendo il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai checkpoint per [lo sviluppo di Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Progettazione audio in realtà mista](../../design/spatial-sound-design.md)
* [Esercitazione di Spatializer di Microsoft](tutorials/unity-spatial-audio-ch1.md)
