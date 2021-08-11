---
title: Profiles
description: Profili di documentazione in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profili,
ms.openlocfilehash: d71b29b04cc83cc469c57356733c7804ff71dfabb2ec59d7b663eca3a12c509a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222747"
---
# <a name="profiles"></a>Profiles

Uno dei modi principali in cui è configurato MRTK è tramite i numerosi profili disponibili nel pacchetto di base. [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)L'oggetto principale in una scena avrà il profilo attivo, che è essenzialmente uno ScriptableObject. Il profilo di configurazione MRTK di primo livello contiene i dati del profilo secondario per ogni core dei sistemi principali primari, ognuno dei quali è progettato per configurare il comportamento dei relativi sottosistema corrispondenti. Inoltre, questi sottoprogetti sono anche oggetti scriptable e possono quindi contenere riferimenti ad altri oggetti profilo a un livello inferiore. Esiste essenzialmente un intero albero di profili connessi che costituiscono le informazioni di configurazione per l'inizializzazione dei sottosistema e delle funzionalità MRTK.

Ad esempio, il comportamento del sistema di input è regolato da un profilo di sistema di input, ad esempio `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles). È consigliabile modificare sempre gli asset ScriptableObject del profilo tramite il controllo nell'editor.

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Controllo profilo</sup>

> [!NOTE]
> Sebbene sia previsto che i profili possano essere scambiati in fase di esecuzione, [attualmente non funziona](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)

## <a name="default-profile"></a>Profilo predefinito

MrTK fornisce un set di profili predefiniti che riguardano la maggior parte delle piattaforme e degli scenari supportati da MRTK. Ad esempio, quando si seleziona `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) sarà possibile provare scenari in VR (OpenVR, WMR) e HoloLens (1 e 2).

Si noti che poiché si tratta di un profilo di utilizzo generale, non è ottimizzato per un caso d'uso specifico. Se si vogliono avere impostazioni più performanti/specifiche che siano migliori in altre piattaforme, vedere gli altri profili seguenti, che sono leggermente modificati per migliorare le rispettive piattaforme.

## <a name="hololens-2-profile"></a>HoloLens 2 profilo

MrTK fornisce anche un profilo predefinito ottimizzato per la distribuzione e i test nel HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).

Quando viene richiesto di scegliere un profilo per l'oggetto MixedRealityToolkit, usare questo profilo anziché il profilo selezionato predefinito.

Le differenze principali tra il profilo HoloLens2 e il profilo predefinito sono:

**Disabilitato** Caratteristiche:

- [Sistema di limiti](../boundary/boundary-system-getting-started.md)
- [Sistema di teletrasporto](../teleport-system/teleport-system.md)
- [Sistema di consapevolezza spaziale](../spatial-awareness/spatial-awareness-getting-started.md)
- [Visualizzazione della mesh manuale](../input/hand-tracking.md) (a causa del sovraccarico delle prestazioni)

**Abilitato** Sistemi:

- Provider [di tracciamento oculare](../eye-tracking/eye-tracking-main.md)
- Simulazione dell'input oculare

Le impostazioni del profilo della fotocamera sono impostate in modo che corrispondano la qualità dell'editor e la qualità del giocatore. Questa impostazione è diversa dal profilo predefinito della fotocamera in cui gli schermi Opachi sono impostati su una qualità superiore. Questa modifica significa che la qualità nell'editor sarà inferiore, che corrisponderà più strettamente a ciò che verrà visualizzato nel dispositivo.
  
> [!NOTE]
> Il sistema di consapevolezza spaziale è disattivato per impostazione predefinita in base al feedback del client. Si tratta di una visualizzazione interessante da visualizzare inizialmente, ma in genere è disattivata per evitare la distrazione visiva e l'ulteriore impatto sulle prestazioni di averlo attivato. Il sistema può essere ri-abilitato seguendo le [istruzioni riportate qui.](../spatial-awareness/spatial-awareness-getting-started.md)
