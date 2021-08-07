---
title: Configurazione e profili
description: Modifica dei profili in MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profilo MRTK
ms.openlocfilehash: 1c6c909dcfd6f553419f050dd35a8fe7a3b82f2d56c761a55b184dc4d45d4cd2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187633"
---
# <a name="configuration-and-profiles"></a>Configurazione e profili

Non tutti i singoli consumer di MRTK vogliono che si comporti allo stesso modo. Alcuni vogliono che la mesh spaziale sia in esecuzione nei dispositivi AR che la supportano. Alcuni potrebbero volere la visualizzazione diagnostica in qualsiasi momento, mentre altri potrebbero volerla usare solo quando l'utente dice un comando vocale.

MrTK deve essere configurabile per supportare un'ampia gamma di tali requisiti e a tale scopo usa un concetto denominato "profili".

## <a name="what-is-a-profile"></a>Che cos'è un profilo?

I profili archiviano le impostazioni di configurazione per i servizi. Vengono usate per controllare quali servizi vengono eseguiti e come si comportano durante l'esecuzione. Vengono archiviati come asset [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) nel progetto. È possibile visualizzare e modificare un profilo selezionandolo nella finestra del progetto.

Ad esempio, MRTK ha un servizio di fotocamera, che applicherà proprietà diverse alla fotocamera principale, a seconda che lo schermo sia trasparente o meno (come nel caso di un HoloLens) o opaco (come nel caso di un visore VR). Al servizio fotocamera viene assegnato un [profilo di fotocamera](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Core/Definitions/CameraSystem/MixedRealityCameraProfile.cs), che contiene le diverse impostazioni trasparenti e opache.

Un esempio di profilo più complesso è [InputSystem.](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Core/Definitions/InputSystem/MixedRealityInputSystemProfile.cs)
Alcune delle proprietà del profilo,ad esempio le entità MixedRealityInputDataProviderConfiguration, controllano gli oggetti di cui verrà creata un'istanza in fase di esecuzione. Questo è il modo in cui il sistema di input sa come creare sottosistemi di input OpenVR, WMR e Unity. Questo profilo non è solo un set di proprietà che configura se una particolare funzionalità secondaria di input è abilitata o disabilitata. Si tratta anche di un meccanismo di inserimento che MRTK userà per "nuove" altre classi in fase di esecuzione (ad esempio, il profilo del sistema di input contiene un elenco di 'provider di dati di input' che contiene informazioni sul tipo serializzato. Tali oggetti vengono creati dal sistema di input in fase di esecuzione)

Le configurazioni del profilo sono inizialmente disattivate perché sono impostate con i profili predefiniti di MRTK.
Possono essere modificati solo dopo la clonazione per garantire che i profili personalizzati non andranno persi dopo un aggiornamento della versione di MRTK.

## <a name="modifying-profiles"></a>Modifica dei profili

Anche se i profili possono essere modificati singolarmente (passando all'asset serializzato di ScriptableObject), in genere sono accessibili tramite il controllo MRTK dell'oggetto scena MixedRealityToolkit radice.

![Profilo](../features/images/profiles/input_profile.png)

L'immagine precedente mostra il volume delle impostazioni. Si noti che ogni opzione a sinistra mostrerà la configurazione per il servizio corrispondente.

### <a name="camera"></a>Fotocamera

Contiene le impostazioni per tipo di visualizzazione. Usato per applicare diversi livelli di qualità, clip e impostazioni di rendering in base al tipo di visualizzazione in cui viene eseguita l'applicazione (ad esempio AR e VR).

### <a name="input"></a>Input

Il profilo più grande per il sottosistema più complesso di MRTK. I vari sottosistemi di input verranno trattati nella documentazione [del sistema di](../architecture/terminology.md) input.

### <a name="teleport"></a>Teletrasporto

Questo profilo controlla il funzionamento del sistema di teletrasporto, che è principalmente un concetto di realtà virtuale.

### <a name="spatial-mapping"></a>Mapping spaziale

Questo profilo controlla il funzionamento del sistema a mesh spaziale, ovvero questo sistema è responsabile dell'avvio del sistema che eseguirà il rendering delle mesh spaziali in un dispositivo AR. Principalmente un concetto ar.

### <a name="diagnostics"></a>Diagnostica

Controlla lo strumento per le prestazioni visive che mostra un contatore della frequenza dei fotogrammi, insieme all'utilizzo della memoria di base.

### <a name="scene-system"></a>Sistema della scena

Questo controllo controlla un sistema attualmente non abilitato per impostazione predefinita progettato per semplificare l'uso di scenari con più scene.

### <a name="extensions"></a>Estensioni

Questo profilo vuoto per impostazione predefinita è il punto di estensione in cui i consumer possono scrivere e quindi collegare i propri oggetti di cui verrà creata un'istanza ed eseguiti dal runtime MRTK.

### <a name="editor"></a>Editor

Contiene le impostazioni generali per i comportamenti solo editor di MRTK.
