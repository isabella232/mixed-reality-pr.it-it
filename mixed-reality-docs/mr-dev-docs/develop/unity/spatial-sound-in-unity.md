---
title: Audio spaziale in Unity
description: Informazioni su come riprodurre e attenuare i suoni spaziali da un punto 3D specifico all'interno della scena Unity con esempi.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, MRTK, Toolkit realtà mista, spazializzatore, riverbero
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228227"
---
# <a name="spatial-sound-in-unity"></a>Audio spaziale in Unity

Questa pagina contiene collegamenti alle risorse per l'audio spaziale in Unity.

## <a name="spatializer-options"></a>Opzioni dell'spazializzatore

Le opzioni di spazializzatore per le applicazioni di realtà mista includono:
* Unity fornisce lo *spazializzatore MS HRTF* come parte del *Windows Mixed Reality* pacchetto facoltativo.
  * Viene eseguito sulla CPU in un'architettura a "origine singola" a costi più elevati.
  * Fornito per la compatibilità con le versioni precedenti HoloLens applicazioni.
* *L'spazializzatore Microsoft* è disponibile nel [repository microsoft spatializer GitHub](https://github.com/microsoft/spatialaudio-unity).
  * Usa un'architettura "multi-origine" a basso costo.
  * Offloaded in un acceleratore hardware nel HoloLens 2. 

Per le nuove applicazioni, è consigliabile usare *microsoft spatializer.*

## <a name="enable-spatialization"></a>Abilitare la spazializzazione

Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft.SpatialAudio.Spatializer.Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto. Quindi:
* Collegare **un'origine audio** a un oggetto nella gerarchia
* Selezionare la casella **di controllo Abilita spazializzazione**
* Spostare il dispositivo **di scorrimento spatial blend** su "1"
* Verificare che l'audio spaziale sia abilitato nella workstation per sviluppatori. 
    * Fare clic con il pulsante destro del mouse sull'icona del volume nella barra delle applicazioni e assicurarsi che Audio spaziale sia impostato su un valore diverso da "Disattivato". 
    * Scegliere **Windows Sonic per cuffie** per ottenere la migliore rappresentazione di ciò che si HoloLens 2.

>[!NOTE]
>Se si verifica un errore in Unity che indica che non è possibile caricare il plug-in Microsoft.SpatialAudio.Spatializer.Unity perché manca una delle relative dipendenze, verificare che nel PC sia installata la versione più recente di [Microsoft Visual C++ Redistributable.](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)

Per altre informazioni, vedere:
* [Repository di dati GitHub microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Esercitazione dello spazializzatore Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentazione dello spazializzatore di Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Attenuazione basate sulla distanza

Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un rolloff logaritmico. Queste impostazioni possono funzionare per il proprio scenario o si potrebbe scoprire che le origini si attenuano troppo rapidamente o troppo lentamente. Per altre informazioni, vedere:
* [Progettazione del suono nella realtà mista per](../../design/spatial-sound-design.md) le impostazioni consigliate.
* [Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per istruzioni sull'impostazione di queste curve.

## <a name="reverb"></a>Riverbero

Microsoft _Spatializer disabilita_ gli effetti post-spazializzatore per impostazione predefinita. Per abilitare il riverbero e altri effetti per le origini spazializzate:
* Collegare il **componente Livello di invio effetto** stanza a ogni origine
* Regolare la curva del livello di invio per ogni origine, per controllare il guadagno sull'audio inviato al grafico per l'elaborazione degli effetti

Per [informazioni dettagliate, vedere il capitolo 5 dell'esercitazione sull'spazializzatore.](tutorials/unity-spatial-audio-ch5.md)

## <a name="unity-spatial-sound-examples"></a>Esempi di suoni spaziali unity

Per esempi di audio spaziale in Unity, vedere:
* [Demo di MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* Progetto [di esempio dello spazializzatore Microsoft](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se stai seguendo il percorso di sviluppo di Unity che abbiamo stabilito, stai esplorando i blocchi predefiniti principali della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Progettazione del suono in realtà mista](../../design/spatial-sound-design.md)
* [Esercitazione dello spazializzatore Microsoft](tutorials/unity-spatial-audio-ch1.md)
