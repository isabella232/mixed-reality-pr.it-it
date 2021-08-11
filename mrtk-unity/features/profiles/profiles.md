---
title: Profiles
description: Profili di documentazione in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profili,
ms.openlocfilehash: b3ba5aa9ac08dcfe0eecdb479db075b39b43a0e376239822432df872b0775d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225658"
---
# <a name="profiles"></a>Profiles

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

Uno dei modi principali in cui è configurato MRTK è tramite i profili disponibili nel pacchetto di base. [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)L'oggetto principale in una scena avrà il profilo attivo, ovvero uno ScriptableObject. Il profilo di configurazione mrTK di primo livello contiene dati di sottoprogetto per ogni core dei sistemi principali, ognuno dei quali è progettato per configurare il comportamento dei sottosistemi corrispondenti. Inoltre, questi sottoprogetti sono anche ScriptableObject e pertanto possono contenere riferimenti ad altri oggetti profilo un livello al di sotto di essi. Esiste essenzialmente un intero albero di profili connessi che costituiscono le informazioni di configurazione per l'inizializzazione dei sottosistemi e delle funzionalità di MRTK.

Ad esempio, il comportamento del sistema di input è regolato da un profilo di sistema di input, ad esempio `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Profile Inspector</sup>

## <a name="background"></a>Sfondo

I profili sono destinati principalmente a supportare scenari specifici in più dispositivi, che vengono gestiti tramite i provider di dati. In questo modo, un'app può essere progettata in modo indipendente dal dispositivo e consentire a MRTK e ai provider di dati del profilo di gestire il supporto multipiattaforma.

Sono disponibili anche profili creati in base alle funzionalità di input di dispositivi specifici, ad esempio il profilo HoloLens 1, che per impostazione predefinita è basato sulle interazioni di tipo GGV.

## <a name="xr-sdk"></a>XR SDK

::: moniker range=">= mrtkunity-2021-05"
Usare uno dei profili MRTK predefiniti, che sono tutti configurati nelle pipeline XR di Unity. I precedenti "DefaultOpenXRConfigurationProfile" e "DefaultXRSDKConfigurationProfile" sono ora etichettati come obsoleti.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Attualmente sono disponibili due profili per XR SDK, `DefaultXRSDKConfigurationProfile` e `DefaultHoloLens2XRSDKConfigurationProfile` . Di conseguenza, non tutte le scene di esempio sono completamente supportate a causa di configurazioni specifiche della scena e dello scenario. Tutti gli esempi che `DefaultMixedRealityToolkitConfigurationProfile` usano e `DefaultHoloLens2ConfigurationProfile` _possono_ essere scambiati con i profili XR SDK corrispondenti. Se si usa OpenXR con XR SDK, usare invece `DefaultOpenXRConfigurationProfile` .

Sono in corso ulteriori operazioni per semplificare la configurazione e supportare tutte le scene di esempio, consentendo la configurazione side-by-side di XR SDK e XR SDK legacy. Per il [rilevamento, #9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) problema.
::: moniker-end

Per altre informazioni sulla conversione dei profili tra XR legacy e XR SDK, vedere [Configuring MRTK for the XR SDK pipeline](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) (Configurazione di MRTK per la pipeline di XR SDK).

## <a name="default-profile"></a>Profilo predefinito

MRTK fornisce un set di profili predefiniti che coprono la maggior parte delle piattaforme e degli scenari supportati da MRTK. Ad esempio, quando si seleziona `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) sarà possibile provare scenari in VR (OpenVR, WMR) e HoloLens (1 e 2).

Si noti che poiché si tratta di un profilo di utilizzo generale, non è ottimizzato per un caso d'uso specifico. Se si vogliono avere impostazioni più performanti/specifiche che siano migliori in altre piattaforme, vedere gli altri profili seguenti, che sono leggermente modificati per migliorare le rispettive piattaforme.

## <a name="hololens-2-profile"></a>HoloLens 2 profilo

MRTK fornisce anche un profilo predefinito ottimizzato per la distribuzione e il test nel HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).

Quando viene richiesto di scegliere un profilo per l'oggetto MixedRealityToolkit, usare questo profilo anziché il profilo selezionato predefinito.

Le differenze principali tra il profilo HoloLens2 e il profilo predefinito sono:

**Funzionalità** disabilitate:

- [Sistema di limiti](../boundary/boundary-system-getting-started.md)
- [Sistema di teletrasporto](../teleport-system/teleport-system.md)
- [Sistema di consapevolezza spaziale](../spatial-awareness/spatial-awareness-getting-started.md)
- [Visualizzazione della mesh manuale](../input/hand-tracking.md) (a causa dell'overhead delle prestazioni)

**Sistemi** abilitati:

- Provider [di tracciamento oculare](../input/eye-tracking/eye-tracking-main.md)
- Simulazione dell'input oculare

Le impostazioni del profilo della fotocamera sono impostate in modo da corrispondere in modo che la qualità dell'editor e la qualità del lettore siano uguali. Questo comportamento è diverso dal profilo predefinito della fotocamera in cui gli schermi opachi sono impostati su una qualità superiore. Questa modifica significa che la qualità nell'editor sarà inferiore, che corrisponderà maggiormente a ciò che verrà visualizzato nel dispositivo.

> [!NOTE]
> Il sistema di consapevolezza spaziale è disattivato per impostazione predefinita in base ai commenti e suggerimenti dei client. Si tratta di una visualizzazione interessante da visualizzare inizialmente, ma in genere è disattivata per evitare la distrazione visiva e l'ulteriore impatto sulle prestazioni di tale sistema. Il sistema può essere ri abilitato seguendo le [istruzioni riportate qui.](../spatial-awareness/spatial-awareness-getting-started.md)
