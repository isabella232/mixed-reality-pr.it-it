---
title: Registrazione dell'animazione di input
description: Documentazione sul sistema di registrazione delle animazioni di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 81e49178a9f218e5d3be796ec6253ccabe5d44fc
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143917"
---
# <a name="input-animation-recording"></a>Registrazione dell'animazione di input

MRTK include un sistema di registrazione tramite il quale i dati di movimento della testa e tracciamento della mano possono essere archiviati in file di animazione. I dati registrati possono quindi essere riprodotti usando il sistema [di simulazione di input](input-simulation-service.md).

La registrazione dell'input è uno strumento utile in diverse situazioni:

* Creazione di test automatizzati per l'interazione, le manipolazioni, i risolutori e così via. La creazione dello spostamento di controller e mani per questi test può richiedere molto tempo. La registrazione diretta dell'input può velocizzare il processo e fornire dati reali.
* Apprendimento dell'uso di elementi dell'esperienza utente tramite animazioni.
  Mostrare agli utenti come interagire con i pulsanti e altri oggetti può smussare la curva di apprendimento.
* Debug di un comportamento imprevisto che può verificarsi durante l'uso regolare.
  Il sistema di registrazione supporta un concetto di "buffer in sequenza" che consente di registrare l'input recente in background.
  Vedere [Servizio di registrazione input.](#input-recording-service)

## <a name="recording-and-playback-services"></a>Servizi di registrazione e riproduzione

Vengono forniti due servizi di sistema di input per registrare e riprodurre rispettivamente l'input.

### <a name="input-recording-service"></a>Servizio di registrazione dell'input

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) accetta i dati dalla trasformazione principale della fotocamera e dai controller della mano attivi e li archivia in un buffer interno. Quando richiesto, questi dati vengono serializzati in file binari per l'archiviazione e la riproduzione successiva.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Animazione di input di registrazione" width="80%" alt="Recording diagram" class="center" />
</a>

Per avviare la registrazione dell'input, chiamare la [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) funzione . [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) sospende la registrazione(ma non rimuove i dati registrati finora, usare [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) per eseguire questa operazione, se necessario).

Per impostazione predefinita, le dimensioni del buffer di registrazione sono limitate a 30 secondi. In questo modo il servizio di registrazione può continuare a registrare in background senza accumulare troppi dati e quindi salvare gli ultimi 30 secondi quando necessario. L'intervallo di tempo può essere modificato usando la [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) proprietà oppure la registrazione può essere illimitata usando l'opzione [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) .

I dati nel buffer di registrazione possono essere salvati in un file binario usando la [funzione SaveInputAnimation.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*)

Per informazioni dettagliate sul formato di file binario, vedere Specifica del formato [del file di animazione di input](input-animation-file-format.md).

### <a name="input-playback-service"></a>Servizio di riproduzione di input

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) legge un file binario con dati di animazione di input e quindi applica questi dati tramite [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) per ricreare i movimenti registrati.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Riproduzione dell'animazione di input" width="80%" alt="Play Back diagram" class="center" />
</a>

Per avviare la riproduzione dell'animazione di input, è necessario caricarla da un file usando la [funzione LoadInputAnimation.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*)

Chiamare [Play,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [Pause o](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)Stop [per](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) controllare la riproduzione dell'animazione.

Il tempo di animazione corrente può anche essere controllato direttamente con la [proprietà LocalTime.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime)

> [!WARNING]
> La ripetizione a ciclo continuo o la reimpostazione diretta dell'animazione o dell'impostazione di input tramite lo scrubbing della sequenza temporale possono produrre risultati imprevisti [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) durante la modifica della scena. Vengono registrati solo i movimenti di input, eventuali modifiche aggiuntive, ad esempio lo spostamento di oggetti o l'inversione di interruttori, non verranno reimpostate. Assicurarsi di ricaricare la scena se sono state apportate modifiche irreversibili.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Strumenti dell'editor per la registrazione e la riproduzione dell'animazione di input

Nell'editor di Unity sono disponibili diversi strumenti per la registrazione e l'analisi dell'animazione di input. È possibile accedere a questi strumenti nella finestra degli strumenti di simulazione [dell'input,](input-simulation-service.md#input-simulation-tools-window)che può essere aperta dal menu _Mixed Reality Toolkit > Utilities > Input Simulation( Simulazione input)._

> [!NOTE]
> La registrazione e la riproduzione di input funzionano solo durante la modalità di riproduzione.

La finestra di registrazione di input ha due modalità:

* _Registrazione per_ la registrazione dell'input durante la modalità di riproduzione e salvataggio nei file di animazione.

  Quando si attiva il pulsante di registrazione, è abilitato [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) per registrare l'input.
  Quando si disattiva il pulsante di registrazione, viene visualizzata una selezione di salvataggio file e l'animazione di input registrata viene salvata nella destinazione selezionata.

  Il limite di tempo del buffer può essere modificato anche in questa modalità.

* _Riproduzione per_ il caricamento dei file di animazione e la ricreazione dell'input tramite il sistema di simulazione di input.

  Un'animazione deve essere caricata prima in questa modalità. Dopo la registrazione dell'input in modalità di registrazione, l'animazione risultante viene caricata automaticamente. In alternativa, fare clic sul pulsante "Carica" per selezionare un file di animazione esistente.

  I pulsanti di controllo dell'ora da sinistra a destra sono:

  * _Reimpostare_ l'ora di riproduzione all'inizio dell'animazione.
  * _Riprodurre_ l'animazione in modo continuo nel tempo.
  * _Eseguire un_ passaggio successivo.

  Il dispositivo di scorrimento può essere usato anche per eseguire lo scrubbing della sequenza temporale dell'animazione.

> [!WARNING]
> Il ciclo o la reimpostazione dell'animazione di input o lo scrubbing della sequenza temporale possono produrre risultati imprevisti durante la modifica della scena. Vengono registrati solo i movimenti di input, eventuali modifiche aggiuntive, ad esempio lo spostamento di oggetti o il capovolgimento degli interruttori, non verranno reimpostate. Assicurarsi di ricaricare la scena se sono state apportate modifiche irreversibili.
