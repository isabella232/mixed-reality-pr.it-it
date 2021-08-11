---
title: Creazione di contenuto dinamico tramite risolutori
description: In questo corso viene illustrato come usare i risolutori di Mixed Reality Toolkit (MRTK) per creare contenuto dinamico.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, risolutori
ms.localizationpriority: high
ms.openlocfilehash: 3060e6f6b1e04f356f2b9d7466c0f8f3481c53ba090f6d8a62405a4da3dc21a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221243"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5. Creazione di contenuto dinamico tramite risolutori

In questa esercitazione verrà analizzato come posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili in MRTK, noti come risolutori, per risolvere scenari complessi di posizionamento nello spazio. In MRTK i risolutori sono un sistema di script e comportamenti usati per consentire agli oggetti di seguire te, l'utente o altri oggetti gioco nella scena. Possono anche essere usati per l'ancoraggio a determinate posizioni, rendendo così più intuitiva l'app.

## <a name="objectives"></a>Obiettivi

* Illustrare i risolutori di MRTK
* Apprendere l'uso dei risolutori per indirizzare l'utente verso gli oggetti
* Apprendere l'uso dei risolutori per riposizionare gli oggetti

## <a name="location-of-solvers-in-the-mrtk"></a>Posizione dei risolutori in MRTK

 I risolutori di MRTK si trovano nella cartella MRTK SDK. Per visualizzare i risolutori disponibili nel progetto, nella finestra Project passare a **Packages**  >  **Mixed Reality Toolkit Foundation** SDK Features Utilities  >    >    >    >  **Solvers**(Risolutori di utilità per le funzionalità di Mixed Reality Toolkit Foundation SDK):

![Finestra Project di Unity con la cartella Solvers selezionata](images/mr-learning-base/base-05-section1-step1-1.png)

In questa esercitazione verrà esaminata l'implementazione dei risolutori Directional Indicator (Indicatore direzionale) e Tap To Place (Tocco per posizionamento). Per altre informazioni sull'intera gamma di risolutori disponibili in MRTK, puoi fare riferimento alla guida [Risolutori](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) nel [portale della documentazione di MRTK](/windows/mixed-reality/mrtk-unity).

> [!NOTE]
> Il risolutore indicatore direzionale non si trova nelle cartelle risolutori a cui si fa riferimento in precedenza, ma nelle cartelle Packages > Mixed Reality Toolkit Foundation > SDK > Experimental > Features > Utilities (Pacchetti > Mixed Reality Toolkit Foundation > SDK > Experimental > Features > Utilities), perché si tratta di una funzionalità sperimentale.

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Uso del risolutore Directional Indicator (Indicatore direzionale) per indirizzare l'utente verso gli oggetti

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab), fai clic sul prefab **Chevron** e trascinalo sulla finestra Hierarchy (Gerarchia), quindi nella sezione Transform (Trasformazione) imposta **Position** (Posizione) su X = 0, Y = 0, Z = 2 per posizionarlo accanto all'oggetto RoverExplorer:

![Unity con il prefab Chevron appena aggiunto selezionato](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> Se ritieni che la fotocamera o altre icone nella scena nascondano gli oggetti o siano elementi di distrazione, puoi nasconderli <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando il menu Gizmos</a> come illustrato nell'immagine precedente. Per altre informazioni sul menu Gizmos e su come è possibile usarlo per ottimizzare la vista della scena, puoi fare riferimento alla documentazione relativa al <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> di Unity.

Rinominare l'oggetto Chevron appena aggiunto in **Indicator,** quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere **DirectionalIndicator:**

![Unity con il componente risolutore DirectionalIndicator aggiunto](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> Quando aggiungi un risolutore, in questo caso il componente DirectionalIndicator, viene aggiunto automaticamente il componente SolverHandler perché è richiesto dai risolutori.

Configura i componenti DirectionalIndicator e SolverHandler nel modo seguente:

* Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) del componente **SolverHandler** sia impostato il valore **Head** (Testa)
* Assegna **RoverExplorer** a **Directional Target** (Destinazione direzionale) del componente **DirectionalIndicator** trascinandolo dalla finestra Hierarchy (Gerarchia) sul campo **None (Transform)** (Nessuna - Trasformazione)
* Modifica il valore di **View Offset** (Offset visualizzazione) impostandolo su 0,2

![Unity con il componente risolutore DirectionalIndicator configurato](images/mr-learning-base/base-05-section2-step1-3.png)

Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco e tieni premuto il pulsante destro del mouse mentre muovi il mouse verso sinistra o verso destra per ruotare la direzione dello sguardo. Potrai osservare quanto segue:

* Quando allontani lo sguardo dall'oggetto RoverExplorer, viene visualizzato l'oggetto Indicator (Indicatore) che punta verso l'oggetto RoverExplorer

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il risolutore DirectionalIndicator in uso](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> Se il raggio della fotocamera non è visibile nella finestra della scena, verifica che sia attivato il menu Gizmos, come mostrato nell'immagine precedente.

> [!TIP]
> Per informazioni sulla procedura di simulazione di input nell'editor, puoi fare riferimento alla guida [Uso della simulazione di input manuale nell'editor per testare una scena](/windows/mixed-reality/mrtk-unity/features/input-simulation/input-simulation-service) nel [portale della documentazione di MRTK](/windows/mixed-reality/mrtk-unity).

> [!TIP]
> Se il computer è dotato di un microfono, puoi impostare facilmente lo stato attivo del pannello di diagnostica visualizzato nella finestra di gioco usando il comando di riconoscimento vocale "toggle diagnostics" (Attiva/disattiva diagnostica). In alternativa, puoi disabilitarlo in MRTK Configuration Profile (Profilo di configurazione di MRTK) > Diagnostics (Diagnostica) > Enable Diagnostics System (Abilita sistema di diagnostica). Tuttavia, è consigliabile in genere lasciare il sistema di diagnostica attivo durante lo sviluppo.

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Uso del risolutore Tap to Place (Tocco per posizionamento) per riposizionare gli oggetti

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RoverExplorer > **RoverAssembly** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Tap To Place (Script)** (Tocco per posizionamento - Script) e configuralo come indicato di seguito:

* Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) del componente **SolverHandler** sia impostato il valore **Head** (Testa)
* Deselezionare **l'opzione Usa offset normale della superficie predefinito** e assicurarsi che **l'opzione Surface Normal Offset (Offset** normale superficie) sia impostata su 0
* Seleziona la casella di controllo **Keep Orientation Vertical** (Mantieni orientamento verticale)
* Dall'elenco a discesa **Magnetic Surfaces (Superfici magnetiche)**  > **Element 0 (Elemento 0)** deseleziona tutte le opzioni tranne **Spatial Awareness** (Consapevolezza spaziale)

![Unity con il componente risolutore TapToPlace aggiunto e configurato](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> L'impostazione Magnetic Surfaces (Superfici magnetiche) determina quali oggetti possono essere rilevati dal componente Tap To Place (Script) (Tocco per posizionamento - script) quando viene posizionato un oggetto. Modificando l'impostazione in modo da definire solo Spatial Awareness (Consapevolezza spaziale), il componente Tap To Place (Script) (Tocco per posizionamento - script) potrà posizionare Rover solo su oggetti del livello di Unity denominato Spatial Awareness (Consapevolezza spaziale), che per impostazione predefinita è la mesh di consapevolezza spaziale generata da HoloLens.
>
> Per altre informazioni sui livelli, puoi fare riferimento alla documentazione di Unity relativa ai <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">livelli</a>.

> [!TIP]
> Se vuoi visualizzare la mesh di consapevolezza spaziale quando testi la funzionalità Tap To Place (Tocco per posizionamento) in HoloLens, puoi impostare temporaneamente l'opzione di visualizzazione dell'osservatore della mesh spaziale come visibile. Per un promemoria su come modificare l'opzione di visualizzazione, puoi fare riferimento alle istruzioni [Modifica dell'opzione di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).

Con l'oggetto RoverAssembly ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) individua l'evento **On Placing Started ()** (All'avvio del posizionamento) e fai clic sull'icona **+** per aggiungere un nuovo evento:

![Unity con l'evento OnPlacingStarted di TapToPlace aggiunto](images/mr-learning-base/base-05-section3-step1-2.png)

Configura l'evento come indicato di seguito:

* Assegna l'oggetto **RoverAssembly** come listener per l'evento On Placing Started () (All'avvio del posizionamento) trascinandolo dalla finestra Hierarchy (Gerarchia) sul campo **None (Object)** (Nessuno - oggetto)
* Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **TapToPlace** > **float SurfaceNormalOffset** per aggiornare il valore della proprietà SurfaceNormalOffset quando viene attivato l'evento
* Verifica che l'argomento sia impostato su **0**

![Unity con l'evento OnPlacingStarted di TapToPlace configurato](images/mr-learning-base/base-05-section3-step1-3.png)

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse in un punto vuoto e scegli **3D Object (Oggetto 3D)**  > **Cube (Cubo)** per creare un oggetto temporaneo che rappresenta il terreno e configura il componente **Transform** (Trasformazione) come segue:

* **Position** (Posizione): X = 0, Y = -1,65, Z = 6
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scale** (Scala): X = 10, Y = 0,2, Z = 10

![Unity con oggetto cubo temporaneo del terreno aggiunto e posizionato](images/mr-learning-base/base-05-section3-step1-4.png)

Con il cubo temporaneo ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) usa l'elenco a discesa **Layers** (Livelli) per modificare l'impostazione del livello del cubo in modo da includere solo il livello **Spatial Awareness** (Consapevolezza spaziale):

![Unity con il livello dell'oggetto cubo temporaneo del terreno impostato su Spatial Awareness](images/mr-learning-base/base-05-section3-step1-5.png)

Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco, quindi tieni premuto il pulsante destro del mouse mentre muovi il mouse verso il basso finché lo sguardo non incontra l'oggetto RoverAssembly:

![Visualizzazione suddivisa della modalità di riproduzione in Unity con lo sguardo fisso che incontra l'oggetto RoverAssembly](images/mr-learning-base/base-05-section3-step1-6.png)

Fai clic con il pulsante sinistro del mouse per avviare il processo di tocco e posizionamento:

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il posizionamento TapToPlace avviato](images/mr-learning-base/base-05-section3-step1-7.png)

Tieni premuto il pulsante destro del mouse mentre muovi il mouse verso sinistra o verso destra per ruotare la direzione dello sguardo. Quando sei soddisfatto del posizionamento, fai clic con il pulsante sinistro del mouse:

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il posizionamento TapToPlace terminato](images/mr-learning-base/base-05-section3-step1-8.png)

Dopo aver testato la funzionalità in modalità di gioco, fai clic con il pulsante destro del mouse sull'oggetto Cube (Cubo) e scegli **Delete** (Elimina) per rimuoverlo dalla scena:

![Unity con cubo temporaneo del terreno selezionato e il menu popup contestuale Delete](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come usare il risolutore Directional Indicator (Indicatore direzionale) di MRTK per fare in modo che un elemento dell'interfaccia utente indirizzi intuitivamente l'utente verso gli oggetti. Hai appreso inoltre come usare il risolutore Tap To Place (Tocco per posizionamento) per riposizionare facilmente gli oggetti.

Per altre informazioni su questi e altri risolutori inclusi in MRTK, puoi fare riferimento alla guida [Risolutori](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) nel [portale della documentazione di MRTK](/windows/mixed-reality/mrtk-unity/).

> [!div class="nextstepaction"]
> [Esercitazione successiva: 6. Creazione delle interfacce utente](mr-learning-base-06.md)
