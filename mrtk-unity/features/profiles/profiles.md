---
title: Profiles
description: Profili di documentazione in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profili,
ms.openlocfilehash: 384614f27c099af197ea8a9aedc72c711f0c099e
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881228"
---
# <a name="profiles"></a>Profiles

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

Uno dei modi principali in cui è configurato il MRTK consiste nell'usare i profili disponibili nel pacchetto di base. L' [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) oggetto principale in una scena avrà il profilo attivo, che è un ScriptableObject. Il profilo di configurazione di MRTK di livello superiore contiene i dati di sottoprofilo per ogni core dei sistemi principali principali, ognuno dei quali è progettato per configurare il comportamento dei sottosistemi corrispondenti. Inoltre, questi profili secondari sono ScriptableObjects e possono quindi contenere riferimenti ad altri oggetti profilo, un livello sotto di essi. Esiste essenzialmente un intero albero di profili connessi che compongono le informazioni di configurazione per l'inizializzazione dei sottosistemi e delle funzionalità di MRTK.

Il comportamento del sistema di input, ad esempio, è regolato da un profilo di sistema di input, ad esempio `DefaultMixedRealityInputSystemProfile` (assets/MRTK/SDK/Profiles).

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Controllo profilo</sup>

## <a name="background"></a>Sfondo

I profili sono destinati principalmente a supportare scenari specifici tra più dispositivi, che vengono gestiti tramite i provider di dati. In questo modo, un'app può essere progettata come il più possibile indipendentemente dal dispositivo e consentire a MRTK e ai provider di dati del profilo di gestire il supporto multipiattaforma.

Sono inoltre disponibili profili basati sulle funzionalità di input di dispositivi specifici, ad esempio il profilo HoloLens 1, per impostazione predefinita le interazioni di tipo GGV.

## <a name="xr-sdk"></a>SDK XR

Attualmente sono disponibili due profili per XR SDK, `DefaultXRSDKConfigurationProfile` e `DefaultHoloLens2XRSDKConfigurationProfile` . Di conseguenza, non tutte le scene di esempio sono completamente supportate a causa di configurazioni specifiche dello scenario e della scena. Tutti gli esempi che usano `DefaultMixedRealityToolkitConfigurationProfile` e `DefaultHoloLens2ConfigurationProfile` _possono_ essere scambiati con i corrispondenti profili XR SDK. Se si usa OpenXR con XR SDK, usare `DefaultOpenXRConfigurationProfile` invece.

Il lavoro aggiuntivo è stato intrapreso per semplificare la configurazione e supportare tutte le scene di esempio, consentendo di configurare side-by-side le versioni precedenti di XR e XR SDK. Vedere problemi [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) per il rilevamento.

Vedere [configurazione di MRTK per la pipeline di XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) per altre informazioni sulla conversione di profili tra le versioni precedenti di XR e XR SDK.

## <a name="default-profile"></a>Profilo predefinito

MRTK fornisce un set di profili predefiniti che coprono la maggior parte delle piattaforme e degli scenari supportati da MRTK. Ad esempio, quando si seleziona `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles), sarà possibile provare scenari in VR (OpenVR, WMR) e HoloLens (1 e 2).

Si noti che poiché si tratta di un profilo di utilizzo generale, non è ottimizzato per un particolare caso di utilizzo. Se si desidera disporre di impostazioni più efficienti/specifiche che siano migliori su altre piattaforme, vedere gli altri profili seguenti, che sono leggermente modificati per migliorare le rispettive piattaforme.

## <a name="hololens-2-profile"></a>Profilo HoloLens 2

MRTK fornisce anche un profilo predefinito ottimizzato per la distribuzione e il testing in HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (assets/MRTK/SDK/Profiles/HoloLens2).

Quando viene richiesto di scegliere un profilo per l'oggetto MixedRealityToolkit, usare questo profilo anziché il profilo selezionato predefinito.

Le differenze principali tra il profilo HoloLens2 e il profilo predefinito sono:

Funzionalità **disabilitate** :

- [Sistema di limiti](../boundary/boundary-system-getting-started.md)
- [Sistema Teleport](../teleport-system/teleport-system.md)
- [Sistema di riconoscimento spaziale](../spatial-awareness/spatial-awareness-getting-started.md)
- [Visualizzazione Mesh mano](../input/hand-tracking.md) (a causa dell'overhead delle prestazioni)

Sistemi **abilitati** :

- Il [provider di rilevamento degli occhi](../input/eye-tracking/eye-tracking-main.md)
- Simulazione dell'input oculare

Le impostazioni del profilo della fotocamera sono impostate in modo da corrispondere alla qualità dell'editor e alla qualità del lettore. Si tratta di un profilo diverso dal profilo della fotocamera predefinito, in cui le visualizzazioni opache sono impostate su una qualità superiore. Questa modifica significa che la qualità nell'Editor sarà inferiore, che corrisponderà più a quanto verrà visualizzato nel dispositivo.

> [!NOTE]
> Il sistema di riconoscimento spaziale è disattivato per impostazione predefinita in base ai commenti e suggerimenti dei client. si tratta di una visualizzazione interessante per vedere inizialmente, ma in genere è disattivata per evitare la distrazione visiva e l'ulteriore impatto sulle prestazioni. Il sistema può essere riabilitato seguendo le istruzioni riportate [qui](../spatial-awareness/spatial-awareness-getting-started.md).
