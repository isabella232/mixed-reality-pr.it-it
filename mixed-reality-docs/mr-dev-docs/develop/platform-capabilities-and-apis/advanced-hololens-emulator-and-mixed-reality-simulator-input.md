---
title: Simulatore HoloLens Emulator e realtà mista
description: Istruzioni dettagliate sull'uso della tastiera, del mouse e del controller Xbox per simulare l'input HoloLens Emulator e Windows Mixed Reality simulatore.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens, Emulator, simulazione, Windows Mixed Reality, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217127"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Emulatore HoloLens avanzato e input per il simulatore di realtà mista

La maggior parte degli utenti dell'emulatore dovrà usare solo i controlli di input di base per il [HoloLens Emulator](using-the-hololens-emulator.md#basic-emulator-input) o [il simulatore Windows Mixed Reality.](using-the-windows-mixed-reality-simulator.md#basic-simulator-input) I dettagli seguenti sono per gli utenti avanzati che hanno riscontrato la necessità di simulare tipi di input più complessi.

## <a name="concepts"></a>Concetti

Per iniziare a controllare l'input virtuale HoloLens Emulator e Windows Mixed Reality simulatore, è necessario innanzitutto comprendere alcuni concetti.

Il movimento si riferisce al controllo e alla modifica della posizione e dell'orientamento di un elemento nella scena. Per un oggetto controllabile di destinazione, il movimento viene controllato con rotazione e traslazione (spostamento) lungo tre assi.
* **Yaw:** ruota a sinistra o a destra.
* **Pitch**: attivare o disattivare.
* **Roll**: roll side-to-side.
* **X:** spostarsi a sinistra o a destra.
* **Y:** spostarsi verso l'alto o verso il basso.
* **Z:** spostarsi avanti o indietro.

L'input del controller di movimento e movimento viene mappato in modo stretto ai dispositivi fisici:
* **Azione:** simula l'azione di pressione del forefinger sul pollice o del pull del pulsante di azione su un controller. Ad esempio, l'input azione può essere usato per simulare il movimento di tocco dell'aria, scorrere il contenuto e premere e tenere premuto.
* **[Movimento Bloom/System](../../design/system-gesture.md#bloom)** o Home: il movimento HoloLens bloom/system o il pulsante Home di un controller viene usato per tornare alla shell e per eseguire azioni di sistema.

Le mani hanno una rappresentazione HoloLens 2.  Oltre a essere rilevate/non rilevate e utilizzabili per i movimenti di guida, le mani hanno ora un modello scheletro articolato adattato ed esposto allo sviluppatore.  Lo scheletro del modello ha 26 punti tracciati su ogni mano.  
* **Joint**: una delle 20 posizioni rilevate per una determinata mano tracciata con un punto associato nello spazio 3D.
* **Pose**: raccolta completa di tutte le giunzioni in una mano tracciata, 26 giunzioni in tutto. 

Attualmente non viene esposto il controllo diretto delle singole posizioni congiunte tramite l'emulatore, ma è possibile impostarle tramite l'API di simulazione. È stato creato un set di pose rappresentative utili che l'emulatore consente di alternare.

È anche possibile controllare lo stato dell'input del sensore simulato:
* **Reimposta**: restituisce tutti i sensori simulati ai valori predefiniti.  A partire dalla HoloLens 2 Emulator, è possibile impostare l'ambito di una reimpostazione su una o entrambe le mani. Attivare le mani desiderate usando i tasti di modifica o i pulsanti (Alt sinistro e/o Destro o il paraurti sinistro e/o destro sul gamepad).
* **Rilevamento:** consente di scorrere le modalità di rilevamento posizionale, tra cui:
  * **Impostazione** predefinita: il sistema operativo sceglie la modalità di rilevamento migliore in base alle richieste effettuate dal sistema.
   * **Orientamento:** forza il rilevamento solo dell'orientamento, indipendentemente dalle richieste del sistema.
   * **Posizionale:** forza il rilevamento posizionale, indipendentemente dalle richieste del sistema.

## <a name="types-of-input"></a>Tipi di input

La tabella seguente illustra come ogni tipo di input viene mappato alla tastiera, al mouse e al controller Xbox. Ogni tipo ha un mapping diverso a seconda della modalità di controllo di input. Altre informazioni sulle modalità di controllo di input sono disponibili più avanti in questo documento.

| Input |  Tastiera |  Mouse |  Controller Xbox | 
|----------|----------|----------|----------|
|  Imbardata |  Frecce sinistra/destra |  Trascinare a sinistra/a destra |  Levetta destra sinistra/destra | 
|  Tonalità |  Frecce su/giù |  Trascinare verso l'alto/verso il basso |  Levetta destra verso l'alto/verso il basso | 
|  Rotolo |  Q/E |  |  DPad a sinistra/a destra | 
|  X |  A/D |  |  Levetta sinistra sinistra/destra | 
|  S |  Pagina precedente/pagina giù |  |  DPad su/giù | 
|  Z |  W/S |  |  Levetta sinistra verso l'alto/verso il basso | 
|  Azione |  Invio o spazio |  Pulsante destro |  Un pulsante o uno dei trigger | 
|  Bloom/System |  F2 o Windows chiave |  |  Pulsante B | 
|  Pulsante di presa del controller/Mano stretta |  G  |  |  | 
|  Pulsante di menu Controller |  M  |  |  | 
|  Tocco del touchpad del controller |  U  |  |  | 
|  Pressione del touchpad del controller |  P  |  |  | 
|  Pressione della levetta del controller |  K  |  |  | 
|  Stato di rilevamento del controller a sinistra |  F9 |  |  | 
|  Stato di rilevamento del controller destro |  F10 |  |  | 
|  Pose "Close" (Chiudi) della mano | 7 |  |  |
|  Hand 'Open' Pose (Impostazione predefinita) | 8 |  |  |
|  Posizione "Punto" della mano | 9 |  |  |
|  Posizione "Pizzica" della mano | 0 |  |  |
|  Reset |  Tasto di escape |  |  Pulsante Avvia | 
|  Rilevamento |  T o F3 |  |  Pulsante X | 


Nota: i pulsanti del controller possono essere indirizzati a una mano/controller o all'altra usando i modificatori di destinazione della mano.

## <a name="targeting"></a>Targeting 

Alcuni dei concetti di input precedenti si distinguono autonomamente.  Action, Bloom/System, Reset e Tracking sono concetti completi, non sono necessari e non sono interessati da modificatori aggiuntivi per la destinazione.  I concetti rimanenti possono essere applicati a una di più destinazioni. Sono stati introdotti modi per specificare la destinazione prevista a cui deve essere applicato il comando.  In tutti i casi, è possibile specificare tramite l'interfaccia utente o le pressione della tastiera, l'oggetto di destinazione.  In alcuni casi, è anche possibile specificare direttamente con il controller Xbox. 

Nella tabella seguente vengono descritte le opzioni per la destinazione e il modo in cui attivare ognuna di esse.

| Oggetto | Modificatore tastiera | Modificatore controller | Emulator Modificatore dell'interfaccia utente |
|----------|----------|----------|----------|
| Corpo | (predefinito) | (predefinito) | (predefinito) |
| Head | Hold H | (Non disponibile) | (Non disponibile) |
| Mano sinistra/Controller | Tenere premuto il pulsante ALT di sinistra | Tenere premuto il pulsante a freccia sinistra | Left-Hand puntina da disegno | 
| Mano destra/Controller | Tenere premuto il pulsante ALT di destra | Tenere premuto il pulsante destro del mouse | Right-Hand puntina da disegno |
| Occhi | Hold Y | (Non disponibile) | Puntina da disegno per gli occhi |
  
La tabella seguente illustra in che modo ogni modificatore di destinazione esegue il mapping di ognuno dei concetti di base relativi all'input di spostamento

| Input | Predefinito (corpo) |  Mano/controller (tenere premuto ALT, tenere premuto il pulsante della tastiera del game pad o attivare o disattivare la puntina da disegno dell'interfaccia utente) |  Head (Hold H)  |  Occhi (tenere premuto Y o attivare o disattivare la puntina da disegno dell'interfaccia utente) |
|----------|----------|----------|----------|----------|
|  Imbardata |  Ruotare il corpo a sinistra/a destra |  Sposta la mano a sinistra/a destra |  Ruotare la testa a sinistra/destra | Sguardo fisso a sinistra/destra |
|  Tonalità |  Ruotare la testa verso l'alto o verso il basso |  Spostare la mano verso l'alto o verso il basso |  Ruotare la testa verso l'alto o verso il basso | Sguardo fisso cerca in alto/in basso | 
|  Rotolo |  Testa a sinistra/destra |  |  Testa a sinistra/destra | (Nessuna azione) |
|  X |  Corpo della diapositiva a sinistra/a destra |  Sposta mano/controller a sinistra/a destra |  Ruotare la testa a sinistra/destra | (Nessuna azione) |
|  S |  Spostare il corpo verso l'alto o verso il basso |  Spostare la mano/controller verso l'alto o verso il basso |  Ruotare la testa verso l'alto o verso il basso | (Nessuna azione) |
|  Z |  Sposta il corpo avanti/indietro |  Sposta mano/controller in avanti/indietro |  Ruotare la testa verso l'alto o verso il basso | (Nessuna azione) |
 
 
## <a name="controlling-an-app"></a>Controllo di un'app

Il set di controlli seguente è consigliato per l'uso quotidiano:

|  Operazione |  Tastiera e mouse |  Controller | 
|----------|----------|----------|
|  Corpo X |  A/D |  Levetta sinistra sinistra/destra | 
|  Corpo Y |  Pagina precedente/pggi giù |  DPad su/giù | 
|  Corpo Z |  W/S |  Levetta sinistra verso l'alto o verso il basso | 
|  S yaw del corpo |  Trascinare il mouse verso sinistra/destra |  Levetta destra sinistra/destra | 
|  Sbarrare la testa |  H + trascinamento del mouse verso sinistra/destra |  H (sulla tastiera) + levetta destra sinistra/destra | 
|  Head Pitch |  Trascinare il mouse verso l'alto o verso il basso |  Levetta destra verso l'alto o verso il basso | 
|  Head Roll |  Q/E |  DPad a sinistra/a destra | 
|  Mano/Controller X |  ALT+A/D |  Levetta sinistra / freccia sinistra a sinistra / destra | 
|  Mano/Controller Y |  ALT +Pagina precedente/pggi in basso |  Pede e DPad su/giù | 
|  Mano/Controller Z |  ALT+W/S |  Levette + levetta sinistra verso l'alto/verso il basso | 
|  Hand/Controller Yaw |  ALT + trascinamento del mouse verso sinistra/destra |  Levetta a sinistra/destra +freccia destra | 
|  Passo mano/controller |  ALT+ trascinare il mouse verso l'alto o verso il basso |  Levetta + levetta destra verso l'alto o verso il basso | 
|  Rullo mano/controller |  ALT+Q/E |  A sinistra/destra della tastiera + DPad | 
|  Azione |  Pulsante destro del mouse |  Trigger | 
|  Bloom/System/Home |  F2 o Windows chiave |  Pulsante B | 
|  Reset |  Carattere speciale di escape |  Pulsante Avvia | 
|  Rilevamento |  T |  Pulsante X | 
|  Scorrimento |  ALT+ pulsante destro del mouse + trascinamento del mouse verso l'alto o verso il basso |  Levetta + trigger + levetta destra verso l'alto o verso il basso | 
|  Spostamento/rotazione più veloce | Tasto MAIUSC sinistro o destro | Tenere premuta la levetta destra |
|  Spostamento/rotazione lenta | Tasto CTRL sinistro o destro | Tenere premuta la levetta sinistra |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Uso di un visore VR immersive di Windows Mixed Reality e di controller del movimento con l'emulatore HoloLens 2

Quando si usa un visore VR Windows Mixed Reality immersive con HoloLens 2 Emulator, il movimento e la rotazione vengono mappati automaticamente al movimento e alla rotazione del visore VR.  La posizione e l'orientamento del controller del movimento vengono mappati automaticamente alla posizione e all'orientamento della mano nell'emulatore.  La tabella seguente elenca le azioni aggiuntive disponibili quando si usa un controller del movimento.

> [!NOTE]
> Quando si usa un visore VR, i controlli standard della tastiera, del mouse e del game pad vengono ignorati automaticamente.

|  Operazione |  Azione |  Note | 
|----------|----------|----------|
|  Corpo X |  Levetta da sinistra/destra |   | 
|  Corpo Z |  Thumbstick Forward/Back |   | 
|  Corpo Y |  Pagina tastiera su/giù | Assicurarsi che Windows Mixed Reality lo stato attivo.  Premere Win+Y se lo stato attivo è sul Windows Desktop per ripristinare lo stato attivo Windows Mixed Reality. |
|  Gli occhi guardano a sinistra/a destra |  DPad a sinistra/a destra | |
|  Occhi che guardano in alto/in basso | DPad su/giù | |
|  Tocco | Trigger | |
|  Avvicinamento delle dita/afferramento | Pulsante di controllo | |
|  Movimento di sistema | Pulsante Menu | |
|  Reimposta posizione | Clic con le levette | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Simulazione della percezione Pannello di controllo tasti di scelta rapida

È possibile accedere al pannello di controllo Simulazione percezione e abilitare o disabilitare i dispositivi di input del PC con i tasti di scelta rapida seguenti.

| Operazione | Tasto di scelta rapida | Descrizione/Note |
|-----------|----------|-------------|
| Attiva/Disattiva "Usa tastiera per simulazione" | F4 | Quando è disattivata, l'input da tastiera viene HoloLens o Windows Mixed Reality app Windows Mixed Reality tastiera. |
| Attiva/Disattiva 'Usa mouse per simulazione' | F5 | Quando è disattivato, l'input del mouse passa all'ambiente di realtà mista (Windows Mixed Reality solo) |
| Attiva/Disattiva 'Usa game pad per la simulazione' | F6 | Se disattivata, l'input del game pad viene ignorato dalla simulazione |
| Mostrare o nascondere il pannello di controllo | F7 | |
| Impostare lo stato attivo della tastiera sul pannello di controllo | F8 | Se il pannello non è attualmente visibile, verrà visualizzato per primo. |
| Ancorare o disanciare il pannello da e verso l'emulatore o Portale realtà mista finestra | F9 | Se la finestra viene chiusa quando è disancosata, viene ancorata e nascosta. |

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](../install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso del simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
