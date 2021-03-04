---
title: Profiles
description: Profili di documentazione in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profili,
ms.openlocfilehash: 58c58a8e244432333046543086cfd86279232247
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781757"
---
# <a name="profiles"></a>Profiles

Uno dei modi principali in cui è configurato il MRTK consiste nell'usare i molti profili disponibili nel pacchetto di base. L' [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) oggetto principale in una scena avrà il profilo attivo, che è essenzialmente un ScriptableObject. Il profilo di configurazione di MRTK di livello superiore contiene i dati di sottoprofilo per ogni core dei sistemi principali principali, ognuno dei quali è progettato per configurare il comportamento dei sottosistemi corrispondenti. Inoltre, questi sottoprofili sono anche oggetti gestibili tramite script e possono quindi contenere riferimenti ad altri oggetti profilo a un livello inferiore. Esiste essenzialmente un intero albero di profili connessi che costituiscono le informazioni di configurazione per l'inizializzazione dei sottosistemi e delle funzionalità di MRTK.

Il comportamento del sistema di input, ad esempio, è regolato da un profilo di sistema di input, ad esempio `DefaultMixedRealityInputSystemProfile` (assets/MRTK/SDK/Profiles). È consigliabile modificare sempre le risorse del profilo ScriptableObject tramite il controllo nell'editor.

<img src="../images/profiles/input_profile.png" width="650px" alt="Input Profile" style="display:block;">
<sup>Controllo profilo</sup>

> [!NOTE]
> Sebbene sia previsto che i profili possano essere scambiati in fase di esecuzione, [attualmente non funziona](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)

## <a name="default-profile"></a>Profilo predefinito

MRTK fornisce un set di profili predefiniti che coprono la maggior parte delle piattaforme e degli scenari supportati da MRTK. Ad esempio, quando si seleziona `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles), sarà possibile provare scenari in VR (OpenVR, WMR) e HoloLens (1 e 2).

Si noti che poiché si tratta di un profilo di utilizzo generale, non è ottimizzato per un particolare caso di utilizzo. Se si desidera disporre di impostazioni più efficienti/specifiche che siano migliori su altre piattaforme, vedere gli altri profili seguenti, che sono leggermente modificati per migliorare le rispettive piattaforme.

## <a name="hololens-2-profile"></a>Profilo HoloLens 2

MRTK fornisce anche un profilo predefinito ottimizzato per la distribuzione e il testing in HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (assets/MRTK/SDK/Profiles/HoloLens2).

Quando viene richiesto di scegliere un profilo per l'oggetto MixedRealityToolkit, usare questo profilo anziché il profilo selezionato predefinito.

Le differenze principali tra il profilo HoloLens2 e il profilo predefinito sono:

**Disabilitato** Funzionalità

- [Sistema di limiti](../boundary/BoundarySystemGettingStarted.md)
- [Sistema Teleport](../teleport-system/Overview.md)
- [Sistema di riconoscimento spaziale](../spatial-awareness/SpatialAwarenessGettingStarted.md)
- [Visualizzazione Mesh mano](../input/HandTracking.md) (a causa dell'overhead delle prestazioni)

**Abilitato** Sistemi

- Il [provider di rilevamento degli occhi](../eye-tracking/EyeTracking_Main.md)
- Simulazione dell'input oculare

Le impostazioni del profilo della fotocamera sono impostate in modo da corrispondere alla qualità dell'editor e alla qualità del lettore. Si tratta di un profilo diverso dal profilo della fotocamera predefinito, in cui le visualizzazioni opache sono impostate su una qualità superiore. Questa modifica significa che la qualità nell'Editor sarà inferiore, che corrisponderà più a quanto verrà visualizzato nel dispositivo.

> [!NOTE]
> Il sistema di riconoscimento spaziale è disattivato per impostazione predefinita in base ai commenti e suggerimenti dei client. si tratta di una visualizzazione interessante per vedere inizialmente, ma in genere è disattivata per evitare la distrazione visiva e l'ulteriore impatto sulle prestazioni. Il sistema può essere riabilitato seguendo le istruzioni riportate [qui](../spatial-awareness/SpatialAwarenessGettingStarted.md).
