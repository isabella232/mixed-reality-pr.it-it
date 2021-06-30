---
title: OpenXR
description: Creare un motore usando lo standard dell'API OpenXR portatile e distribuirlo nei Windows Mixed Reality e HoloLens 2 visori VR.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, roadmap, estensioni, Khronos, BasicXRApp, DirectX, app nativa, nativa, motore personalizzato, middleware
ms.openlocfilehash: e9071f8b15f19be564b7c246244a5b7561aa5968
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042242"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR è uno standard API open realty free di <a href="https://www.khronos.org/" target="_blank">Khronos,</a>che offre ai motori l'accesso nativo a una gamma di dispositivi nello spettro [della realtà mista.](../../discover/mixed-reality.md)

È possibile sviluppare usando OpenXR in un dispositivo HoloLens 2 o Windows Mixed Reality visore VR immersive sul desktop.  Se non si ha accesso a un visore VR, è possibile usare l'emulatore HoloLens 2 o il simulatore Windows Mixed Reality dispositivo.

## <a name="why-openxr"></a>Perché OpenXR?

Con OpenXR è possibile creare motori per dispositivi olografici, ad esempio HoloLens 2, e dispositivi VR immersive, ad esempio visori VR Windows Mixed Reality per PC desktop. OpenXR consente di scrivere codice una volta che viene quindi portabile su un'ampia gamma di piattaforme hardware.

L'API OpenXR usa un caricatore per connettere l'applicazione direttamente al supporto della piattaforma nativa del visore VR. Gli utenti finali ottengono le massime prestazioni e la latenza minima, indipendentemente dal fatto che Windows Mixed Reality o qualsiasi altro visore VR.

## <a name="what-is-openxr"></a>Che cos'è OpenXR?

L'API OpenXR fornisce la stima della posizione di base, la tempistica dei fotogrammi e le funzionalità di input spaziale necessarie per creare un motore in grado di avere come destinazione dispositivi olografici e immersive.

Per informazioni sull'API OpenXR, vedere la specifica di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank"></a>OpenXR 1.0, le informazioni di riferimento <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">sulle API</a>e la guida di <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">riferimento rapido</a>.  Per altre informazioni, vedere la <a href="https://www.khronos.org/openxr/" target="_blank">pagina di Khronos OpenXR.</a>

Per usare come destinazione il set completo di funzionalità di HoloLens 2, si useranno anche estensioni OpenXR tra fornitori e fornitori che abilitano funzionalità aggiuntive oltre al core OpenXR 1.0, ad esempio il tracciamento delle mani articolato, il tracciamento oculare, il mapping spaziale e gli ancoraggi nello spazio. Per altre informazioni, vedere la sezione [Roadmap di](#roadmap) seguito sulle estensioni disponibili più avanti quest'anno.

OpenXR non è un motore di realtà mista.  OpenXR consente invece a motori come Unity e Unreal di scrivere codice portabile una volta che può accedere alle funzionalità della piattaforma nativa del dispositivo olografico o immersive dell'utente, indipendentemente dal fornitore che ha creato tale piattaforma.

## <a name="roadmap"></a>Roadmap

La specifica OpenXR definisce un meccanismo di estensione che consente [](#what-is-openxr) agli implementatori di runtime di esporre funzionalità aggiuntive oltre alle funzionalità di base definite nella specifica <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">di base di OpenXR 1.0.</a>

Esistono tre tipi di estensioni OpenXR:
* **Estensioni del fornitore (ad esempio, `MSFT` ): consente** l'innovazione per fornitore nelle funzionalità hardware o software.  Qualsiasi fornitore di runtime può introdurre e spedire un'estensione del fornitore in qualsiasi momento.
  * **Estensioni sperimentali del fornitore (ad esempio, `MSFT_preview` ): estensioni** del fornitore sperimentali in anteprima per raccogliere commenti e suggerimenti.  `MSFT_preview` Le estensioni sono solo per i dispositivi di sviluppo e verranno rimosse quando viene fornita l'estensione reale.  Per sperimentarle, è possibile abilitare [le estensioni di anteprima nel dispositivo di sviluppo.](openxr-getting-started.md#using-preview-extensions)
* **Estensioni tra `EXT` fornitori:** estensioni tra fornitori definite e implementate da più aziende.  I gruppi di società interessate possono introdurre estensioni EXT in qualsiasi momento.
* **Estensioni `KHR` ufficiali:** estensioni ufficiali di Khronos, come parte di una versione specifica di base.  Le estensioni KHR sono coperte dalla stessa licenza della specifica di base stessa.

Il runtime Windows Mixed Reality OpenXR supporta un set di estensioni e che offre il set completo di funzionalità HoloLens 2 per `MSFT` `EXT` le applicazioni OpenXR:

| Area funzionale | Disponibilità delle estensioni |
|--------------|------------------------|
| Sistemi e sessioni | **Specifica di base di OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Spazi di riferimento (visualizzazione, locale, fase)](../../design/coordinate-systems.md) | **Specifica di base di OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Visualizzare le configurazioni (mono, stereo) | **Specifica di base di OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchain](../platform-capabilities-and-apis/rendering.md)  +  [temporizzazione dei frame](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **Specifica di base di OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Livelli di composizione<br />(proiezione, quad) | **Specifica di base di OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input e attico](../../design/interaction-fundamentals.md) | **Specifica di base di OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integrazione di Direct3D 11 | **Versione `KHR` ufficiale dell'estensione:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Integrazione di Direct3D 12 | **Versione `KHR` ufficiale dell'estensione:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Spazio di riferimento illimitato <br /> (esperienze su scala globale)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` Estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Ancoraggi nello spazio](../../design/spatial-anchors.md) | <p>**`MSFT` Estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code></p><p>**`MSFT_preview`estensione nel [runtime di anteprima 107:](openxr-getting-started.md#using-preview-extensions)**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_anchor_persistence_preview">XR_MSFT_spatial_anchor_persistence_preview</a></code></p> |
| [Interazione con la <br /> mano (afferrare/puntare la posizione, tasto d'aria, afferrare)](../../design/hands-and-tools.md)<p>*HoloLens 2 solo*</p> | **`MSFT` Estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articazione della mano + mesh mano](../../design/hands-and-tools.md)<p>*HoloLens 2 solo*</p> | <p>**`EXT` Estensione rilasciata:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` Estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Tracciamento oculare](../../design/eye-tracking.md)<p>*HoloLens 2 solo*</p> | **`EXT` Estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| [Acquisizione realtà mista <br /> (terzo rendering dalla fotocamera PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2 solo*</p> | **`MSFT` Estensioni rilasciate:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interoperabilità con altri SDK di realtà mista<br />(ad esempio, [QR)](../platform-capabilities-and-apis/qr-code-tracking.md) | <p>**`MSFT` Estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` Estensione rilasciata in runtime 105:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| Interoperabilità con l'API CoreWindow UWP<br />(ad esempio, per tastiera/mouse) | **`MSFT` Estensione rilasciata in runtime 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Profili di interazione del controller del movimento<br />(Samsung Odyssey e HP Reverb G2) | **`MSFT` Estensioni rilasciate in runtime 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Modelli di rendering del controller del movimento](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` Estensione rilasciata in runtime 104:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Comprensione della scena (piani, mesh)](../../design/scene-understanding.md)<p>*HoloLens 2 solo*</p> | <p>**`MSFT` Estensione rilasciata in runtime 106:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding">XR_MSFT_scene_understanding</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding_serialization">XR_MSFT_scene_understanding_serialization</a></code></p> |
| [Modalità di riproiezione del livello di composizione <br /> (riproiezione planare automatica o solo orientamento)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` Estensione rilasciata in runtime 106:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_composition_layer_reprojection">XR_MSFT_composition_layer_reprojection</a></code> |
| Altre estensioni tra fornitori | <p>**Estensioni `KHR` ufficiali rilasciate:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code></p><p>**`EXT` Estensioni rilasciate:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code></p> |

Anche se alcune di queste estensioni possono iniziare come estensioni specifiche del fornitore, Microsoft e altri fornitori di runtime OpenXR collaborano per progettare estensioni o più fornitori per molte di queste aree `MSFT` `EXT` di `KHR` funzionalità. Le estensioni tra fornitori renderanno portabile il codice scritto per tali funzionalità tra fornitori di runtime, come con la specifica di base.

## <a name="getting-started-with-openxr"></a>Informazioni di base su OpenXR

![Screenshot di Screenshot riprodotto da un utente che indossa un visore VR di realtà mista](images/openxr-minecraft.jpg)

*Il nuovo motore RenderDragon di Draft ha creato il supporto per la realtà virtuale desktop usando OpenXR.*

Microsoft ha lavorato con Unity e Epic Games per garantire che il futuro della realtà mista sia aperto, non solo per HoloLens 2, ma per tutta la gamma di PC VR, incluso il nuovo visore VR [Reverb G2](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)di HP.  OpenXR supporta la realtà virtuale tra fornitori per i titoli principali attualmente in distribuzione, ad esempio Il simulatore di volo Microsoft e Il simulatore di volo Microsoft.  Per altre informazioni sullo sviluppo per HoloLens (prima generazione), vedere le note [sulla versione](/hololens/hololens1-release-notes).

Per informazioni su come iniziare a usare OpenXR in Unity, Unreal Engine o il proprio motore, continua a leggere.

### <a name="openxr-in-unity"></a>OpenXR in Unity

L'attuale configurazione di Unity consigliata da Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality **è Unity 2020.3 LTS** con il plug-in OpenXR di Realtà mista più recente.  Questo plug-in include il supporto per le estensioni OpenXR che accerta le funzionalità complete dei [visori VR HoloLens 2](#roadmap)e Windows Mixed Reality, tra cui il tracciamento della mano/occhio, gli ancoraggi nello spazio e i controller HP Reverb G2.  MRTK-Unity supporta OpenXR a livello [di MRTK 2.7.](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)  Per altre informazioni su come iniziare a usare Unity 2020 e OpenXR, vedere [Scelta di una versione di Unity.](../unity/choosing-unity-version.md)

Se stai sviluppando per HoloLens (prima generazione), dovrai continuare a usare **Unity 2019.4 LTS** con il back-end dell'API WinRT legacy.  Se la destinazione è il nuovo controller HP Reverb G2 in un'app Unity 2019, vedere la documentazione di input di [HP Reverb G2](../unity/unity-reverb-g2-controllers.md).

A partire **da Unity 2021.2,** OpenXR sarà l'unico back-end Unity supportato per la destinazione HoloLens 2 e Windows Mixed Reality visori VR.

### <a name="openxr-in-unreal-engine"></a>OpenXR in Unreal Engine

Unreal Engine 4.23 è stata la prima versione principale del motore di gioco a rilasciare il supporto di anteprima per OpenXR 1.0.  Ora in **Unreal Engine 4.26** il supporto per HoloLens 2, Windows Mixed Reality e altri visori VR desktop è disponibile tramite il supporto OpenXR predefinito di Unreal Engine.  Unreal Engine 4.26 supporta anche il [plug-in dell'estensione OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)di Microsoft, che consente l'interazione manuale e il supporto del controller HP Reverb G2, accendendo il set completo di funzionalità di [visori HoloLens 2 e Windows Mixed Reality.](#roadmap)  Unreal Engine 4.26 è attualmente disponibile in [Epic Games Launcher,](https://www.unrealengine.com/download/creators)con MRTK-Unreal 0.12 che supporta i progetti OpenXR.

### <a name="openxr-for-native-development"></a>OpenXR per lo sviluppo nativo

È possibile sviluppare usando OpenXR in un dispositivo HoloLens 2 o Windows Mixed Reality visore VR immersive sul desktop.  Se non si ha accesso a un visore VR, è possibile usare l'emulatore HoloLens 2 o il simulatore Windows Mixed Reality dispositivo.

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2 o Windows Mixed Reality VR, vedere come iniziare a sviluppare [openxr.](openxr-getting-started.md)

Per una presentazione di tutti i componenti principali dell'API OpenXR, insieme ad esempi di applicazioni reali che usano OpenXR oggi stesso, vedere questo video della procedura dettagliata di 60 minuti:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Vedere anche

* <a href="https://www.khronos.org/openxr/" target="_blank">Altre informazioni su OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Specifica di OpenXR 1.0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Informazioni di riferimento sulle API OpenXR 1.0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido di OpenXR 1.0</a>