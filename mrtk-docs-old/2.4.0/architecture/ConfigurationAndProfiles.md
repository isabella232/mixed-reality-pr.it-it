---
title: Configurazione e profili
description: Modifica dei profili in MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, profilo MRTK
ms.openlocfilehash: 3c2c76e60fd6f8ad8b09ea5e4f6bea6bde78b132
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782299"
---
# <a name="configuration-and-profiles"></a>Configurazione e profili

Non tutti i singoli consumer di MRTK vorranno comportarsi nello stesso modo, ad alcuni desideri che la mesh spaziale venga eseguita nei dispositivi AR che la supportano. In alcuni casi potrebbe essere necessario visualizzare la visualizzazione diagnostica in qualsiasi momento e in alcuni casi può essere utile solo quando l'utente dice un comando Voice.

Il MRTK deve essere configurabile per supportare un'ampia gamma di tali requisiti e usa un concetto denominato "Profiles" a tale scopo.

## <a name="what-is-a-profile"></a>Che cos'è un profilo?

I profili archiviano le impostazioni di configurazione per i servizi. Vengono usati per controllare quali servizi vengono eseguiti e come si comportano durante l'esecuzione di tali servizi. Sono archiviati come asset [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) nel progetto. È possibile visualizzare e modificare un profilo selezionandola nella finestra del progetto.

Ad esempio, il MRTK ha un servizio della fotocamera, che applicherà proprietà diverse alla fotocamera principale, a seconda che lo schermo sia o meno trasparente (come nel caso di un HoloLens) o opaco (come nel caso di un auricolare VR). Al servizio della fotocamera viene assegnato un [profilo della fotocamera](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/MixedRealityCameraProfile.cs), che contiene le diverse impostazioni trasparenti e opache.

Un esempio di profilo più complesso è il [InputSystem](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/InputSystem/MixedRealityInputSystemProfile.cs).
Alcune delle proprietà di tale profilo, ad esempio le entità MixedRealityInputDataProviderConfiguration, controllano gli oggetti di cui verrà creata un'istanza in fase di esecuzione. questo è il modo in cui il sistema di input sa come creare sottosistemi di input OpenVR, WMR e Unity. Questo profilo non è solo un set di proprietà che configura se una particolare funzionalità secondaria di input è abilitata o disabilitata, ma è anche un meccanismo di inserimento che MRTK userà per "nuove" altre classi in fase di esecuzione, ad esempio il profilo di sistema di input contiene un elenco di "provider di dati di input" con informazioni sul tipo serializzato. questi oggetti vengono creati dal sistema di input in fase di esecuzione.

Le configurazioni del profilo sono inizialmente disattivate perché sono configurate con i profili predefiniti di MRTK.
Possono essere modificati solo dopo la clonazione per assicurarsi che i profili personalizzati non vadano perduti dopo un aggiornamento della versione di MRTK.

## <a name="modifying-profiles"></a>Modifica di profili

Sebbene i profili possano essere modificati singolarmente (passando all'asset serializzato di ScriptableObject), sono generalmente accessibili tramite il controllo MRTK dell'oggetto scena MixedRealityToolkit radice.

![Profilo](../features/Images/Profiles/input_profile.png)

L'immagine precedente Mostra il volume delle impostazioni. si noti che ogni opzione a sinistra mostrerà la configurazione per il servizio corrispondente.

### <a name="camera"></a>Fotocamera

Contiene le impostazioni del tipo per visualizzazione. Usato per applicare diversi livelli di impostazioni di qualità, clip e rendering in base al tipo di visualizzazione in cui viene eseguita l'applicazione (ad esempio, AR vs VR).

### <a name="input"></a>Input

Profilo più grande del sottosistema più complesso del MRTK. I vari sottosistemi di input verranno trattati nella documentazione del [sistema di input](InputSystem/Terminology.md) .

### <a name="teleport"></a>Teletrasporto

Questo profilo controlla il funzionamento del sistema di teleportation, che è principalmente un concetto VR.

### <a name="spatial-mapping"></a>Mapping spaziale

Questo profilo controlla il funzionamento del sistema Mesh spaziale (ad esempio, questo sistema è responsabile dell'avvio del sistema che eseguirà il rendering delle mesh spaziali in un dispositivo AR). Principalmente un concetto AR.

### <a name="diagnostics"></a>Diagnostica

Consente di controllare lo strumento prestazioni visive che mostra un contatore di framerate, insieme all'utilizzo di memoria di base.

### <a name="scene-system"></a>Sistema di scena

Questo controlla un sistema attualmente non abilitato per impostazione predefinita progettato per semplificare l'uso di scenari multiscena.

### <a name="extensions"></a>Estensioni

Questo profilo vuoto per impostazione predefinita è il punto di estensione in cui i consumer possono scrivere e quindi inserire i propri oggetti di cui verrà creata un'istanza ed eseguiti dal runtime di MRTK.

### <a name="editor"></a>Editor

Contiene le impostazioni generali per i comportamenti solo dell'editor di MRTK.
