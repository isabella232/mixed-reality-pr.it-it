---
title: OpenXR
description: È possibile creare un motore usando lo standard dell'API OpenXR portatile e distribuirlo in una realtà mista di Windows e in HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware
ms.openlocfilehash: afb0627a0fb29ff63ea2174676fc2fdfbd252de6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496059"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR è uno standard API senza diritti d'autore aperto da <a href="https://www.khronos.org/" target="_blank">Khronos</a>, che fornisce motori con accesso nativo a una gamma di dispositivi attraverso lo [spettro di realtà mista](../../discover/mixed-reality.md).

È possibile sviluppare app usando OpenXR in un visore VR immersive di HoloLens 2 o Windows Mixed Reality sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

## <a name="why-openxr"></a>Perché OpenXR?

Con OpenXR è possibile creare motori destinati a entrambi i dispositivi olografici, ad esempio HoloLens 2 e dispositivi immersivi, come le cuffie di realtà mista di Windows per PC desktop. OpenXR consente di scrivere codice una volta trasportabile in un'ampia gamma di piattaforme hardware.

L'API OpenXR usa un caricatore per connettere l'applicazione direttamente al supporto della piattaforma nativa dell'auricolare. Gli utenti finali ottengono le massime prestazioni e la latenza minima, indipendentemente dal fatto che utilizzino una realtà mista di Windows o qualsiasi altro auricolare.

## <a name="what-is-openxr"></a>Che cos'è OpenXR?

L'API OpenXR fornisce le funzionalità di base per la stima, la tempistica dei frame e l'input spaziale necessari per compilare un motore che può essere destinato a dispositivi sia olografici che immersivi.

Per informazioni sull'API OpenXR, vedere la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica</a>OpenXR 1,0, informazioni di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">riferimento sulle API</a>e <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido</a>.  Per ulteriori informazioni, vedere la <a href="https://www.khronos.org/openxr/" target="_blank">pagina Khronos OpenXR</a>.

Per avere come destinazione il set completo di funzionalità di HoloLens 2, si useranno anche estensioni OpenXR specifiche del fornitore e dei fornitori che consentono funzionalità aggiuntive oltre al core OpenXR 1,0, ad esempio il rilevamento a mano articolato, il rilevamento degli occhi, il mapping spaziale e i ancoraggi spaziali. Per ulteriori informazioni, vedere la [sezione roadmap](#roadmap) riportata di seguito sulle estensioni riportate più avanti in questo anno.

OpenXR non è a sua volta un motore della realtà mista.  OpenXR consente invece ai motori come Unity e Unreal di scrivere codice portabile una volta che può accedere alle funzionalità della piattaforma nativa del dispositivo olografico o immersivo dell'utente, indipendentemente dal fornitore che ha creato tale piattaforma.

## <a name="roadmap"></a>Roadmap

La specifica OpenXR definisce un meccanismo di estensione che consente agli implementatori del runtime di esporre funzionalità aggiuntive oltre le [funzionalità](#what-is-openxr) di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">base definite nella specifica OpenXR 1,0 di base</a>.

Sono disponibili tre tipi di estensioni OpenXR:
* **Estensioni Fornitore (ad esempio, `MSFT` ):** Abilita l'innovazione per fornitore in funzionalità hardware o software.  Qualsiasi fornitore di runtime può introdurre e distribuire un'estensione del fornitore in qualsiasi momento.
  * **Estensioni del fornitore sperimentale (ad esempio, `MSFT_preview` ): estensioni del** fornitore sperimentali visualizzate in anteprima per raccogliere commenti e suggerimenti.  `MSFT_preview` le estensioni sono destinate solo ai dispositivi per sviluppatori e verranno rimosse quando l'estensione reale viene fornita.  Per sperimentarli, è possibile [abilitare le estensioni di anteprima nel dispositivo per sviluppatori](openxr-getting-started.md#using-preview-extensions).
* **Estensioni tra fornitori `EXT` :** estensioni tra più fornitori che definiscono e implementano più aziende.  I gruppi di società interessate possono introdurre estensioni EXT in qualsiasi momento.
* **`KHR` Estensioni ufficiali:** estensioni Khronos ufficiali ratificate come parte di una versione specifica di base.  Le estensioni KHR sono coperte dalla stessa licenza della specifica principale.

A partire da luglio 2020, il runtime di OpenXR per la realtà mista di Windows supporta un set di `MSFT` `EXT` estensioni e che offre il set completo di funzionalità di HoloLens 2 alle applicazioni OpenXR:

| Area funzionale | Disponibilità dell'estensione |
|--------------|------------------------|
| Sistemi e sessioni | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Spazi di riferimento (visualizzazione, locale, fase)](../../design/coordinate-systems.md) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Visualizza configurazioni (mono, stereo) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Le catene](../platform-capabilities-and-apis/rendering.md)  +  [temporizzazione frame](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Livelli di composizione<br />(proiezione, quad) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input e haptics](../../design/interaction-fundamentals.md) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integrazione di Direct3D 11 | **`KHR`Estensione ufficiale rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Integrazione con Direct3D 12 | **`KHR`Estensione ufficiale rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Spazio di riferimento senza limiti <br /> (esperienze su scala mondiale)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Ancoraggi nello spazio](../../design/spatial-anchors.md) | **`MSFT` estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Interazione della mano <br /> (grip/AIM, tocco, presa)](../../design/hands-and-tools.md)<p>*Solo HoloLens 2*</p> | **`MSFT` estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articolazione manuale + mesh mano](../../design/hands-and-tools.md)<p>*Solo HoloLens 2*</p> | <p>**`EXT` estensione rilasciata in fase di esecuzione 102:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` estensione rilasciata in fase di esecuzione 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Tracciamento oculare](../../design/eye-tracking.md)<p>*Solo HoloLens 2*</p> | **`EXT` estensione rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Interoperabilità con altri SDK di HoloLens<br />(ad esempio, [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*Solo HoloLens 2*</p> | <p>**`MSFT` estensione rilasciata in fase di esecuzione 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` estensione nel [runtime di anteprima 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_perception_anchor_interop_preview">XR_MSFT_perception_anchor_interop_preview</a></code></p> |
| [Acquisizione di realtà mista <br /> (terzo rendering dalla fotocamera FV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Solo HoloLens 2*</p> | **`MSFT` estensioni rilasciate in fase di esecuzione 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interoperabilità con l'API CoreWindow di UWP<br />(ad esempio, per tastiera/mouse) | **`MSFT` estensione rilasciata in fase di esecuzione 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Profili di interazione del controller di movimento (Samsung Odyssey e HP Reverb G2) | **`MSFT` estensioni rilasciate in fase di esecuzione 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Modelli di rendering del controller di movimento](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` estensione nel [runtime di anteprima 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Comprensione della scena (piani, mesh)](../../design/scene-understanding.md)<p>*Solo HoloLens 2*</p> | <p>**Nel [runtime di anteprima 102 o versione successiva](openxr-getting-started.md#using-preview-extensions):**<br />Usare <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> con l'SDK per la [comprensione della scena](../platform-capabilities-and-apis/scene-understanding-sdk.md)</p><p>**`MSFT_preview` estensione nel runtime di anteprima futuro** *(pianificato)*</p> |
| Altre estensioni tra fornitori | <p>**`KHR`Estensioni ufficiali rilasciate:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` estensioni rilasciate:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Sebbene alcune di queste estensioni possano iniziare come estensioni specifiche del fornitore `MSFT` , Microsoft e altri fornitori di runtime di OpenXR collaborano per progettare `EXT` le estensioni o il fornitore `KHR` per molte di queste aree di funzionalità. Le estensioni tra fornitori faranno il codice scritto per le funzionalità portabili tra i fornitori di runtime, come per la specifica di base.

## <a name="getting-started-with-openxr"></a>Informazioni di base su OpenXR

![Screenshot di Minecraft riprodotto da un utente che usa un headset a realtà mista](images/openxr-minecraft.jpg)

*Il nuovo motore RenderDragon di Minecraft sta creando il proprio supporto VR per desktop usando OpenXR*

Microsoft ha collaborato con Unity ed Epic Games per garantire che il futuro della realtà mista sia aperto, non solo per HoloLens 2, ma per tutta la gamma di PC VR, tra cui la [nuova cuffia G2 del riverbero di HP](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).  Per ulteriori informazioni sullo sviluppo di HoloLens (1a generazione), vedere le [Note sulla versione](/hololens/hololens1-release-notes).

Per informazioni su come iniziare a usare OpenXR in Unity, Unreal Engine o il proprio motore, leggere l'articolo.

### <a name="openxr-in-unity"></a>OpenXR in Unity

Attualmente, il percorso di sviluppo di Unity supportato per HoloLens 2, HoloLens (1st Gen) e auricolari per la realtà mista di Windows è **unity 2019 LTS** con il back-end dell'API WinRT esistente.  È possibile passare a [OpenXR con Unity](../unity/openxr-getting-started.md); Se la destinazione è il nuovo controller di HP Reverb G2 in un'app Unity 2019, vedere la [documentazione di input di HP reverbi G2](../unity/unity-reverb-g2-controllers.md).

A partire da **unity 2020 LTS**, [Unity fornirà un back-end OpenXR](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) che supporta le cuffie HoloLens 2 e Windows Mixed Reality.  Questo include il supporto per le estensioni OpenXR che evidenziano le [funzionalità complete di HoloLens 2 e auricolari per la realtà mista di Windows](#roadmap), tra cui il rilevamento mano/occhio, gli ancoraggi spaziali e i controller G2 di HP Reverb.  Il supporto MRTK-Unity per OpenXR è attualmente in fase di sviluppo nel [ramo di mrtk_development](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development) e sarà disponibile insieme al pacchetto di anteprima di OpenXR.

A partire da **unity 2021**, OpenXR si laurea in modo che sia l'unico back-end di Unity supportato per la definizione degli auricolari HoloLens 2 e Windows Mixed Reality.

### <a name="openxr-in-unreal-engine"></a>OpenXR in Unreal Engine

A partire da **Unreal Engine 4,23**, il supporto completo per HoloLens 2 e gli auricolari di realtà mista di Windows sono disponibili tramite il plug-in WinRT (Windows Mixed Reality).

Unreal Engine 4,23 è stata anche la prima versione principale del motore di gioco a fornire il supporto in anteprima per OpenXR 1,0!  Ora, in **Unreal engine 4,26**, il supporto per HoloLens 2, la realtà mista di Windows e altri auricolari Desktop VR saranno disponibili tramite [il plug-in OpenXR incorporato del motore Unreal Engine](https://github.com/microsoft/Microsoft-OpenXR-Unreal).  Unreal Engine 4,26 fornirà anche con il primo set di plug-in di estensione OpenXR che abilitano l'interazione della mano e il supporto del controller di HP Reverb G2, illuminando il [set completo di funzionalità di HoloLens 2 e di cuffie di realtà mista di Windows](#roadmap).  Unreal Engine 4,26 è attualmente disponibile in anteprima nell' [Epic Games Launcher](https://www.unrealengine.com/download/creators), con la versione ufficiale successiva di quest'anno.  Anche il supporto MRTK-Unreal per OpenXR sarà disponibile insieme a questa versione.


### <a name="openxr-for-native-development"></a>OpenXR per lo sviluppo nativo

È possibile sviluppare app usando OpenXR in un visore VR immersive di HoloLens 2 o Windows Mixed Reality sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2 o cuffie di realtà miste Windows immersive, vedere [come iniziare a usare lo sviluppo OpenXR](openxr-getting-started.md).

Per una presentazione di tutti i componenti principali dell'API OpenXR, insieme ad esempi di applicazioni reali che usano OpenXR oggi, vedere questo video di 60 minuti sulla procedura dettagliata:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Vedi anche

* <a href="https://www.khronos.org/openxr/" target="_blank">Altre informazioni su OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Specifica OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Informazioni di riferimento sull'API OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido per OpenXR 1,0</a>