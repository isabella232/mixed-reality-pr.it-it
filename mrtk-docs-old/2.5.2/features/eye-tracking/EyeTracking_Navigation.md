---
title: EyeTracking_Navigation
description: Come usare la destinazione degli occhi per la navigazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 6ab29fc9c1775f66328b09669f7c632f5ac4bed3
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683284"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navigazione con supporto oculistico in MRTK

![MRTK](../images/eye-tracking/mrtk_et_navigation.png)

Si supponga di leggere le informazioni in uno Slate e quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per rivelare altro contenuto. In alternativa, è possibile ingrandire il percorso in cui si sta esaminando. Anche la mappa regola automaticamente il contenuto per tenere gli elementi di interesse all'interno del campo di visualizzazione. Un'altra applicazione interessante è l'osservazione senza mani degli ologrammi 3D, portando automaticamente le parti dell'ologramma che si sta osservando in primo piano. Di seguito sono riportati alcuni esempi descritti in questa pagina nel contesto della navigazione con supporto oculistico.

Le descrizioni seguenti presuppongono che si abbia già familiarità con le procedure per [configurare la verifica degli occhi nella scena MRTK](EyeTracking_BasicSetup.md) e con le nozioni di base sull' [accesso ai dati di rilevamento degli occhi](EyeTracking_TargetSelection.md) in MRTK Unity.
Gli esempi illustrati in questo argomento sono tutti parte della `EyeTrackingDemo-03-Navigation` scena (assets/MRTK/examples/Demos/eyetracking/Scenes/EyeTrackingDemo-03-Navigation).

**Riepilogo:** Scorrimento automatico del testo, panoramica e zoom supportati con lo sguardo di una mappa virtuale, rotazione 3D indirizzata a sguardi senza contatto.

## <a name="auto-scroll"></a>Scorrimento automatico

Scorrimento automatico consente all'utente di scorrere i testi senza sollevare un dito.
È sufficiente continuare la lettura e il testo scorrerà automaticamente verso l'alto o verso il basso a seconda del punto in cui l'utente sta cercando.
È possibile iniziare dall'esempio fornito in `EyeTrackingDemo-03-Navigation` (assets/MRTK/examples/Demos/eyetracking/scenes).
Questo esempio usa un componente [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) per consentire il caricamento e la formattazione flessibili del nuovo testo.
Per abilitare lo scorrimento automatico, aggiungere semplicemente i due script seguenti al componente Collider della casella di testo:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Per scorrere un [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) o più in generale un componente [oggetto recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) è possibile usare lo script [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) .
Se si desidera scorrere una trama anziché una [oggetto recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html), utilizzare [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) anziché [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf).
Di seguito sono illustrati in modo più dettagliato i parametri di [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) disponibili nell'editor di Unity.

Parametri | Descrizione
:---- | :----
LimitPanning | Se abilitata, arresterà il contenuto scorrevole al limite.
RectTransfToNavigate | Riferimento al [oggetto recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) di scorrimento.
RefToViewport | Riferimento al [oggetto recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) padre del contenuto scorrevole per determinare l'offset e il limite corretti.
AutoGazeScrollIsActive | Se abilitata, il testo scorrerà automaticamente se l'utente esamina un' *area attiva* (ad esempio, la parte superiore e inferiore del pannello di scorrimento se la velocità di scorrimento verticale non è zero).
ScrollSpeed_x | Se il valore è impostato su un valore diverso da zero, verrà abilitato lo scorrimento orizzontale. I valori negativi indicano una modifica nella direzione di scorrimento, da sinistra a destra rispetto a destra a sinistra.
ScrollSpeed_y | Se il valore è impostato su un valore diverso da zero, verrà abilitato lo scorrimento verticale. I valori negativi indicano una modifica nella direzione di scorrimento: fino a verso il basso e verso l'alto.
MinDistFromCenterForAutoScroll | Distanza minima normalizzata in x e y dal centro della casella di hit della destinazione (0,0) per scorrere. Pertanto, i valori devono essere compresi tra 0 (scorrimento sempre) e 0,5 (nessun scorrimento).
UseSkimProofing | Se abilitata, impedisce spostamenti improvvisi di scorrimento quando si esamina rapidamente. In questo modo lo scorrimento potrebbe essere meno sensibile. Può essere ottimizzato con il valore *SkimProofUpdateSpeed* .
SkimProofUpdateSpeed | Più basso è il valore, più lento sarà la velocità di scorrimento dopo lo skimming. Valore consigliato: 5.

![Configurazione di scorrimento con supporto oculistico in Unity](../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

Il fissaggio del componente _EyeTrackingTarget_ consente di gestire in modo flessibile gli eventi correlati agli sguardi.
Nell'esempio Scroll viene illustrato lo scorrimento del testo che inizia quando l'utente *osserva* il pannello e si interrompe quando l'utente sta *cercando* .
![Configurazione di scorrimento con supporto oculistico in Unity: EyeTrackingTarget](../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Panoramica e zoom supportati

Chi non ha usato una mappa virtuale prima di cercare la propria abitazione o esplorare i posti completamente nuovi? Il rilevamento degli occhi consente di esaminare direttamente le parti a cui si è interessati e, una volta ingrandita, è possibile seguire in modo semplice il corso di una strada per esplorare il quartiere.
Questa operazione non è utile solo per l'esplorazione delle mappe geografiche, ma anche per l'estrazione di dettagli in fotografie, visualizzazioni dei dati o persino immagini mediche con flusso live. Per usare questa funzionalità nell'app è facile. Per il rendering del contenuto in una [trama]( https://docs.unity3d.com/ScriptReference/Texture.html) (ad esempio, una foto e i dati trasmessi), è sufficiente aggiungere lo script [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) .
Per un [oggetto recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) usare [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). Estendendo la funzionalità di [scorrimento automatico](#auto-scroll) , abbiamo essenzialmente lo scorrimento verticale e orizzontale allo stesso tempo per ingrandire il contenuto intorno al punto di messa a fuoco corrente dell'utente.

Parametri | Descrizione
:---- | :----
LimitPanning | Se abilitata, arresterà il contenuto scorrevole al limite.
HandZoomEnabledOnStartup | Indica se i movimenti della mano vengono abilitati automaticamente per eseguire un movimento di zoom. Potrebbe essere necessario disabilitarlo inizialmente per evitare l'attivazione accidentale di azioni di zoom.
RendererOfTextureToBeNavigated | Renderer di riferimento della trama da esplorare.
Zoom_Acceleration | Accelerazione zoom che definisce la ripidezza del mapping della funzione di velocità logistica.
Zoom_SpeedMax | Velocità massima dello zoom.
Zoom_MinScale | Scala minima della trama per lo zoom avanti, ad esempio 0,5 f (metà delle dimensioni originali).
Zoom_MaxScale | Scala massima della trama per lo zoom indietro, ad esempio 1F (dimensioni originali) o 2.0 f (doppia le dimensioni originali).
Zoom_TimeInSecToZoom | Zoom temporizzato: una volta attivato, viene eseguito uno zoom avanti/indietro per il periodo di tempo specificato in secondi.
Zoom_Gesture | Tipo di movimento della mano da usare per eseguire lo zoom avanti o indietro.
--- | ---
Pan_AutoScrollIsActive | Se abilitata, il testo scorrerà automaticamente se l'utente esamina un' *area attiva* (ad esempio, la parte superiore e inferiore del pannello di scorrimento se la velocità di scorrimento verticale non è zero).
Pan_Speed_x | Se il valore è impostato su un valore diverso da zero, verrà abilitato lo scorrimento orizzontale. I valori negativi indicano una modifica nella direzione di scorrimento, da sinistra a destra rispetto a destra a sinistra.
Pan_Speed_y | Se il valore è impostato su un valore diverso da zero, verrà abilitato lo scorrimento verticale. I valori negativi indicano una modifica nella direzione di scorrimento: fino a verso il basso e verso l'alto.
Pan_MinDistFromCenter | Distanza minima normalizzata in x e y dal centro della casella di hit della destinazione (0,0) per scorrere. Pertanto, i valori devono essere compresi tra 0 (scorrimento sempre) e 0,5 (nessun scorrimento).
UseSkimProofing | Se abilitata, impedisce spostamenti improvvisi di scorrimento quando si esamina rapidamente. In questo modo lo scorrimento potrebbe essere meno sensibile. Può essere ottimizzato con il valore *SkimProofUpdateSpeed* .
SkimProofUpdateSpeed | Più basso è il valore, più lento sarà la velocità di scorrimento dopo lo skimming. Valore consigliato: 5.

![Panoramica e configurazione di zoom supportati da Eye in Unity](../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotazione 3D basata sull'attenzione

Si supponga di esaminare un oggetto 3D e le parti che si desidera visualizzare in modo più accurato si rivolgono a te, come se il sistema fosse in grado di leggere e sapere di trasformare l'elemento verso l'utente.
Si tratta dell'idea per le rotazioni 3D basate sull'attenzione che consentono di esaminare tutti i lati di un ologramma senza sollevare un dito.
Per abilitare questo comportamento, è sufficiente aggiungere lo script [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) alla parte di GameObject con un componente [Collider](https://docs.unity3d.com/ScriptReference/Collider.html) .
È possibile modificare diversi parametri elencati di seguito per limitare la velocità e le direzioni in cui l'ologramma girerà.

Come si può immaginare, l'attivazione di questo comportamento in qualsiasi momento potrebbe diventare rapidamente molto dispersiva in una scena affollata.
Questo è il motivo per cui è consigliabile iniziare con questo comportamento disabilitato e quindi abilitarlo rapidamente usando i comandi vocali.
In alternativa, è stato aggiunto un esempio in `EyeTrackingDemo-03-Navigation` (assets/MRTK/examples/Demos/eyetracking/scenes) per usare [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) per il quale è possibile selezionare una destinazione con lo stato attivo e il suo volo è davanti all'utente .

Una volta nella modalità near, la modalità di rotazione automatica viene abilitata automaticamente.
In tale modalità, è possibile osservarla da tutti i lati, semplicemente inclinando il sistema e visualizzandola, cercandola per spostarla e ruotarla con la mano. Quando si ignora la destinazione (si osservi & pizzicare o *"rinviare"*), viene ripristinata la posizione originale e si smette di reagire all'utente da Afar.

Parametri | Descrizione
:---- | :----
SpeedX | Velocità di rotazione orizzontale.
Veloce | Velocità di rotazione verticale.
InverseX | Per invertire la direzione di rotazione orizzontale.
Inversa | Per invertire la direzione di rotazione verticale.
RotationThreshInDegrees | Se l'angolo tra' sguardo a destinazione ' è fotocamera a destinazione ' è inferiore a questo valore, non eseguire alcuna operazione. Ciò consente di evitare piccole rotazioni nervose.
MinRotX | Angolo di rotazione orizzontale minimo. Questo consente di limitare la rotazione in direzioni diverse.
MaxRotX | Angolo di rotazione orizzontale massimo. Questo consente di limitare la rotazione in direzioni diverse.
MinRotY | Angolo di rotazione verticale minimo per limitare la rotazione intorno all'asse x.
MaxRotY | Angolo di rotazione verticale massimo per limitare la rotazione intorno all'asse y.

![Configurazione della rotazione 3D con supporto oculare in Unity](../images/eye-tracking/mrtk_et_nav_rotate.jpg)

In sintesi, gli script precedenti dovrebbero consentire di iniziare a usare gli occhi per le varie attività di esplorazione di input, ad esempio lo scorrimento dei testi, lo zoom e la panoramica delle trame, nonché la rotazione dell'analisi degli ologrammi 3D.

### <a name="see-also"></a>Vedi anche

- [Configurazione di base di MRTK per l'uso di Eye Tracking](EyeTracking_BasicSetup.md)
- [Selezione della destinazione supportata dagli occhi](EyeTracking_TargetSelection.md)

---
[Torna a "Eye Tracking in the MixedRealityToolkit"](EyeTracking_Main.md)
