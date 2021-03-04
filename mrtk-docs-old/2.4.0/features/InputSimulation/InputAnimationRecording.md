---
title: InputAnimationRecording
description: Documentazione sul sistema di registrazione delle animazioni di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 161831f4ee4f7da7060bd7e67af4e2a06cef98e9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783147"
---
# <a name="input-animation-recording"></a>Registrazione dell'animazione di input

MRTK è dotato di un sistema di registrazione mediante il quale è possibile archiviare i dati di rilevamento della mano e del movimento Head nei file di animazione. I dati registrati possono quindi essere riprodotti usando il [sistema di simulazione di input](InputSimulationService.md).

La registrazione dell'input è uno strumento utile in diverse situazioni:

* Creazione di test automatizzati per l'interazione, le manipolazioni, i risolutori e così via. La creazione del movimento dei controller e delle mani per questi test può richiedere molto tempo. La registrazione diretta dell'input può velocizzare il processo e fornire dati reali.
* Insegnamento dell'uso di elementi UX tramite animazioni.
  Gli utenti che illustrano come interagire con i pulsanti e altri oggetti possono smussare la curva di apprendimento.
* Debug di un comportamento imprevisto che può verificarsi durante il normale utilizzo.
  Il sistema di registrazione supporta un concetto di "buffering in sequenza" che consente di registrare l'input recente in background.
  Vedere [servizio di registrazione input](#input-recording-service).

## <a name="recording-and-playback-services"></a>Servizi di registrazione e riproduzione

Vengono forniti due servizi di sistema di input per registrare e riprodurre input rispettivamente.

### <a name="input-recording-service"></a>Servizio registrazione input

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) preleva i dati dalla trasformazione della fotocamera principale e dai controller della mano attiva e li archivia in un buffer interno. Quando richiesto, questi dati vengono quindi serializzati in file binari per l'archiviazione e successivamente Riproduci.

<a target="_blank" href="../Images/InputSimulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../Images/InputSimulation/MRTK_InputAnimation_RecordingDiagram.png" title="Registrazione dell'animazione di input" width="80%" class="center" />
</a>

Per avviare la registrazione dell'input [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) , chiamare la funzione. [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) sospende la registrazione, ma non rimuove i dati registrati fino [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) a questo momento, se necessario, usare per eseguire questa operazione.

Per impostazione predefinita, le dimensioni del buffer di registrazione sono limitate a 30 secondi. In questo modo, il servizio di registrazione può registrare in background senza accumulare troppi dati, quindi salvare gli ultimi 30 secondi, se necessario. L'intervallo di tempo può essere modificato usando la [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) Proprietà oppure la registrazione può essere illimitata usando l' [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) opzione.

I dati nel buffer di registrazione possono essere salvati in un file binario usando la funzione [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) .

Per informazioni dettagliate sul formato di file binario, vedere [specifica del formato del file di animazione di input](InputAnimationFileFormat.md).

### <a name="input-playback-service"></a>Servizio di riproduzione input

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) legge un file binario con i dati di animazione di input, quindi applica tali dati tramite [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) per ricreare i movimenti registrati.

<a target="_blank" href="../Images/InputSimulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../Images/InputSimulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Riproduzione dell'animazione di input" width="80%" class="center" />
</a>

Per avviare la riproduzione dell'animazione di input, è necessario caricarla da un file usando la funzione [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) .

Chiamare [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)o [Stop](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) per controllare la riproduzione dell'animazione.

Il tempo di animazione corrente può anche essere controllato direttamente con la proprietà [localtime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) .

> [!WARNING]
> Il ciclo o la reimpostazione dell'animazione o [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) dell'impostazione dell'input direttamente tramite lo scrubbing della sequenza temporale può produrre risultati imprevisti durante la modifica della scena. Vengono registrati solo i movimenti di input, le eventuali modifiche aggiuntive, ad esempio lo spostamento di oggetti o la rotazione delle opzioni non verranno reimpostate. Assicurarsi di ricaricare la scena se sono state apportate modifiche irreversibili.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Strumenti Editor per la registrazione e la riproduzione dell'animazione di input

Nell'editor di Unity sono disponibili numerosi strumenti per la registrazione e l'analisi dell'animazione di input. È possibile accedere a questi strumenti nella [finestra degli strumenti di simulazione di input](InputSimulationService.md#input-simulation-tools-window), che può essere aperta da _mixed reality Toolkit > Utilities > menu di simulazione input_ .

> [!NOTE]
> La registrazione e la riproduzione di input funzionano solo in modalità di riproduzione.

La finestra di registrazione input presenta due modalità:

* _Registrazione_ per registrare l'input durante la modalità di riproduzione e salvarlo nei file di animazione.

  Quando si attiva il pulsante [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) di registrazione, è abilitato per registrare l'input.
  Quando si disattiva il pulsante registrazione, viene visualizzata una selezione di salvataggio file e l'animazione di input registrata viene salvata nella destinazione selezionata.

  Il limite di tempo del buffer può essere modificato anche in questa modalità.

* _Riproduzione_ per il caricamento di file di animazione e ricreazione dell'input tramite il sistema di simulazione di input.

  Prima di tutto è necessario caricare un'animazione in questa modalità. Dopo la registrazione dell'input in modalità di registrazione, l'animazione risultante viene caricata automaticamente. In alternativa, fare clic sul pulsante "carica" per selezionare un file di animazione esistente.

  I pulsanti di controllo dell'ora da sinistra a destra sono:

  * _Reimposta_ l'ora di riproduzione all'inizio dell'animazione.
  * _Riproduzione_ continua dell'animazione nel tempo.
  * Eseguire un _passaggio avanti una_ volta.

  Il dispositivo di scorrimento può essere usato anche per scorrere la sequenza temporale dell'animazione.

> [!WARNING]
> Il ciclo o la reimpostazione dell'animazione dell'input o la ripulitura della sequenza temporale possono produrre risultati imprevisti durante la modifica della scena. Vengono registrati solo i movimenti di input, le eventuali modifiche aggiuntive, ad esempio lo spostamento di oggetti o la rotazione delle opzioni non verranno reimpostate. Assicurarsi di ricaricare la scena se sono state apportate modifiche irreversibili.
