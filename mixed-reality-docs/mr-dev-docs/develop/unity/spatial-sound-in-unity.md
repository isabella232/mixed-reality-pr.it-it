---
title: Audio spaziale in Unity
description: Viene illustrato come riprodurre e attenuare i suoni spaziali da uno specifico punto 3D nella scena Unity con esempi.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare realtà virtuale, MRTK, Toolkit realtà mista, Spatializer, Reverb
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009271"
---
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

Questa pagina contiene collegamenti a risorse per il suono spaziale in Unity.

## <a name="spatializer-options"></a>Opzioni di Spatializer

Le opzioni di Spatializer per le applicazioni di realtà mista includono:
* Unity fornisce il *HRTF MS Spatializer* come parte del pacchetto facoltativo di *realtà mista di Windows* .
  * Viene eseguito sulla CPU in un'architettura a più costi ' single-source '.
  * Fornito per la compatibilità con le versioni precedenti con le applicazioni HoloLens originali.
* *Microsoft Spatializer* è disponibile nel [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Usa un'architettura a più livelli di costo inferiore.
  * Offload a un acceleratore hardware in HoloLens 2. 

Per le nuove applicazioni, è consigliabile *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Abilita spazializzazione

Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft. SpatialAudio. Spatializer. Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto. Quindi:
* Alleghi un' **origine audio** a un oggetto nella gerarchia
* Selezionare la casella di controllo **Abilita spazializzazione**
* Spostare il dispositivo di scorrimento di **Blend spaziale** su "1"
* Verificare che l'audio spaziale sia abilitato nella workstation per sviluppatori. 
    * Fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni e verificare che l'audio spaziale sia impostato su un valore diverso da "off". 
    * Scegliere **Windows Sonic per le cuffie** per ottenere la migliore rappresentazione di ciò che verrà ascoltato in HoloLens 2.

>[!NOTE]
>Se si verifica un errore in Unity che non è in grado di caricare il plug-in Microsoft. SpatialAudio. Spatializer. Unity, perché una delle relative dipendenze non è presente, verificare di disporre della versione più recente di [Microsoft Visual C++ ridistribuibile](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installata nel computer.

Per altre informazioni, vedere:
* [Repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Esercitazione di Spatializer di Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentazione di Unity Spatializer](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Attenuazione basate sulla distanza

Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico. Queste impostazioni possono essere usate per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente. Per altre informazioni, vedere:
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

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista. Da qui, è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Testo](text-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Progettazione audio in realtà mista](../../design/spatial-sound-design.md)
* [Esercitazione di Spatializer di Microsoft](tutorials/unity-spatial-audio-ch1.md)
