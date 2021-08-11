---
title: EyeTracking_Navigation
description: Come usare il targeting oculare per la navigazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: c5134f20275183d48af13f44255ca25e8d29ee44edf7c54054e56881e07b5f60
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218531"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navigazione supportata dagli occhi in MRTK

![MRTK](../images/eye-tracking/mrtk_et_navigation.png)

Imagine si leggono informazioni su uno slate e quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per visualizzare più contenuto. In alternativa, è possibile ingrandire fluentemente il punto in cui si sta esaminando. La mappa regola automaticamente anche il contenuto per mantenere gli elementi di interesse all'interno del campo di visualizzazione. Un'altra applicazione interessante è l'osservazione senza mani degli ologrammi 3D portando automaticamente le parti dell'ologramma che si sta osservando in primo piano. Questi sono alcuni degli esempi descritti in questa pagina nel contesto della navigazione supportata dagli occhi.

Le descrizioni seguenti presuppongono che si abbia già familiarità con la configurazione del tracciamento oculare nella scena [MRTK](eye-tracking-basic-setup.md) e con le nozioni di base sull'accesso ai dati di tracciamento oculare [in](eye-tracking-target-selection.md) MRTK Unity.
Gli esempi illustrati di seguito fanno tutti parte della `EyeTrackingDemo-03-Navigation` scena (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation).

**Riepilogo:** Scorrimento automatico del testo, panoramica e zoom supportati dall'occhio di una mappa virtuale, rotazione 3D diretta verso lo sguardo libero.

## <a name="auto-scroll"></a>Scorrimento automatico

Lo scorrimento automatico consente all'utente di scorrere i testi senza alzare un dito.
È sufficiente continuare a leggere e il testo scorrerà automaticamente verso l'alto o verso il basso a seconda della posizione in cui l'utente sta cercando.
È possibile iniziare dall'esempio fornito in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
In questo esempio viene utilizzato [un componente TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) per consentire il caricamento e la formattazione flessibili del nuovo testo.
Per abilitare lo scorrimento automatico, è sufficiente aggiungere i due script seguenti al componente collisore della casella di testo:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Per scorrere un [textMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) o più in generale un [componente RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) è possibile usare lo script [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Se si vuole scorrere una trama invece di [RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html)usare [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) anziché [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf).
Di seguito sono illustrati in dettaglio i parametri di [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) disponibili nell'editor di Unity:

Parametri | Descrizione
:---- | :----
LimitPanning | Se abilitata, arresterà il contenuto scorrevole al limite.
RectTransfToNavigate | Riferimento a [RectTransform in](https://docs.unity3d.com/ScriptReference/RectTransform.html) cui scorrere.
RefToViewport | Riferimento all'elemento [RectTransform padre](https://docs.unity3d.com/ScriptReference/RectTransform.html) del contenuto scorrevole per determinare l'offset e il limite corretti.
AutoGazeScrollIsActive | Se abilitata, il testo scorrerà automaticamente se l'utente esamina un'area *attiva(ad* esempio, la parte superiore e inferiore del pannello di scorrimento se la velocità di scorrimento verticale non è zero).
ScrollSpeed_x | Se impostato su un valore diverso da zero, verrà abilitato lo scorrimento orizzontale. I valori negativi significano una modifica nella direzione di scorrimento: da sinistra a destra e da destra a sinistra.
ScrollSpeed_y | Se impostato su un valore diverso da zero, lo scorrimento verticale verrà abilitato. I valori negativi significano una modifica nella direzione di scorrimento: dall'alto verso il basso o verso il basso verso l'alto.
MinDistFromCenterForAutoScroll | Distanza minima normalizzata in x e y dal centro della casella di selezione della destinazione (0, 0) per scorrere. Pertanto, i valori devono essere compresi tra 0 (sempre scorrimento) e 0,5 (senza scorrimento).
UseSkimProofing | Se abilitata, impedisce improvvisi movimenti di scorrimento quando ci si guarda rapidamente. In questo modo, tuttavia, lo scorrimento potrebbe risultare meno reattivo. Può essere ottimizzato con il *valore SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Più basso è il valore, più lento sarà lo scorrimento dopo lo scorrimento. Valore consigliato: 5.

![Configurazione dello scorrimento supportata dagli occhi in Unity](../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

L'associazione _del componente EyeTrackingTarget_ consente di gestire in modo flessibile gli eventi correlati allo sguardo oculare.
L'esempio di scorrimento illustra lo  scorrimento del testo che inizia quando l'utente guarda il pannello e si arresta quando l'utente lo *sta* allontanando.
![Configurazione dello scorrimento supportata dagli occhi in Unity: EyeTrackingTarget](../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Panoramica e zoom con supporto dello sguardo

Who non ha mai usato una mappa virtuale per cercare la propria casa o per esplorare luoghi completamente nuovi? Il tracciamento oculare consente di approfondire direttamente le parti a cui si è interessati e, dopo aver ingrandito, è possibile seguire senza problemi il corso di una strada per esplorare il proprio quartiere.
Ciò è utile non solo per esplorare le mappe geografiche, ma anche per verificare i dettagli nelle fotografie, nelle visualizzazioni dei dati o persino nelle immagini mediche in streaming live. Usare questa funzionalità nell'app è semplice. Per il contenuto sottoposto a rendering in [una trama]( https://docs.unity3d.com/ScriptReference/Texture.html) (ad esempio, una foto, dati trasmessi in streaming), è sufficiente aggiungere lo script [PanZoomTexture.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture)
Per [rectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) usare [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). Estendendo [la funzionalità Scorrimento](#auto-scroll) automatico, si abilita essenzialmente lo scorrimento verticale e orizzontale contemporaneamente e l'ingrandimento del contenuto intorno al punto attivo corrente dell'utente.

Parametri | Descrizione
:---- | :----
LimitPanning | Se abilitata, arresterà il contenuto scorrevole al limite.
HandZoomEnabledOnStartup | Indica se i movimenti della mano sono abilitati automaticamente per eseguire un movimento di zoom. È possibile disabilitarla in un primo momento per evitare di attivare accidentalmente azioni di zoom.
RendererOfTextureToBeNavigated | Renderer di riferimento della trama da esplorare.
Zoom_Acceleration | Accelerazione dello zoom che definisce la pendenza del mapping delle funzioni di velocità logistica.
Zoom_SpeedMax | Velocità massima dello zoom.
Zoom_MinScale | Scala minima della trama per lo zoom avanti, ad esempio 0,5f (metà delle dimensioni originali).
Zoom_MaxScale | Scala massima della trama per lo zoom indietro, ad esempio 1f (dimensione originale) o 2,0f (il doppio delle dimensioni originali).
Zoom_TimeInSecToZoom | Zoom a tempo: dopo l'attivazione, verrà eseguito uno zoom avanti/indietro per la quantità di tempo specificata in secondi.
Zoom_Gesture | Tipo di movimento manuale da usare per eseguire lo zoom avanti/indietro.
--- | ---
Pan_AutoScrollIsActive | Se abilitata, il testo scorrerà automaticamente se l'utente esamina un'area *attiva(ad* esempio, la parte superiore e inferiore del pannello di scorrimento se la velocità di scorrimento verticale non è zero).
Pan_Speed_x | Se impostato su un valore diverso da zero, verrà abilitato lo scorrimento orizzontale. I valori negativi significano una modifica nella direzione di scorrimento: da sinistra a destra e da destra a sinistra.
Pan_Speed_y | Se impostato su un valore diverso da zero, lo scorrimento verticale verrà abilitato. I valori negativi significano una modifica nella direzione di scorrimento: dall'alto verso il basso o verso il basso verso l'alto.
Pan_MinDistFromCenter | Distanza minima normalizzata in x e y dal centro della casella di selezione della destinazione (0, 0) per scorrere. Pertanto, i valori devono essere compresi tra 0 (sempre scorrimento) e 0,5 (senza scorrimento).
UseSkimProofing | Se abilitata, impedisce improvvisi movimenti di scorrimento quando ci si guarda rapidamente. In questo modo, tuttavia, lo scorrimento potrebbe risultare meno reattivo. Può essere ottimizzato con il *valore SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Più basso è il valore, più lento sarà lo scorrimento dopo lo scorrimento. Valore consigliato: 5.

![Configurazione dello zoom e della panoramica supportata dagli occhi in Unity](../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotazione 3D basata sull'attenzione

Imagine guardare un oggetto 3D e le parti che si vuole vedere più da vicino si voltano verso di te, come se il sistema leggesse la tua mente e sappia ruotare l'elemento verso di te.
Questa è l'idea per le rotazioni 3D basate sull'attenzione che consentono di analizzare tutti i lati di un ologramma senza elevare un dito.
Per abilitare questo comportamento, è sufficiente aggiungere lo script [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) alla parte del GameObject con un [componente Collider.](https://docs.unity3d.com/ScriptReference/Collider.html)
È possibile modificare diversi parametri elencati di seguito per limitare la velocità e le direzioni in cui verrà ruotato l'ologramma.

Come si può immaginare, l'attività di questo comportamento in qualsiasi momento può diventare rapidamente piuttosto distrazione in una scena piena.
Questo è il motivo per cui è possibile iniziare con questo comportamento disabilitato e quindi abilitarlo rapidamente usando i comandi vocali.
In alternativa, è stato aggiunto un esempio in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) per usare [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) per il quale è possibile selezionare una destinazione mirata che si sposta davanti all'utente, semplicemente pronunciando *"Come to me".*

Una volta attivata la modalità near, la modalità di rotazione automatica viene abilitata automaticamente.
In questa modalità, è possibile osservarlo da tutti i lati semplicemente chinandosi indietro e osservandolo, aggirandosi o cercando di afferrarlo e ruotarlo con la mano. Quando si ignora la destinazione (cercare & avvicinare le dita o *pronunciare "Invia indietro"),* tornerà alla posizione originale e smetterà di reagire da lontano.

Parametri | Descrizione
:---- | :----
SpeedX | Velocità di rotazione orizzontale.
Veloce | Velocità di rotazione verticale.
InverseX | Per invertire la direzione di rotazione orizzontale.
Inversa | Per invertire la direzione di rotazione verticale.
RotationThreshInDegrees | Se l'angolo tra "Sguardo fisso su destinazione" e "Da fotocamera a destinazione" è minore di questo valore, non eseguire alcuna operazione. Ciò consente di evitare piccole rotazioni di instabilità.
MinRotX | Angolo di rotazione orizzontale minimo. Ciò consente di limitare la rotazione in direzioni diverse.
MaxRotX | Angolo di rotazione orizzontale massimo. Ciò consente di limitare la rotazione in direzioni diverse.
MinRotY | Angolo di rotazione verticale minimo per limitare la rotazione intorno all'asse x.
MaxRotY | Angolo di rotazione verticale massimo per limitare la rotazione intorno all'asse y.

![Configurazione della rotazione 3D supportata dagli occhi in Unity](../images/eye-tracking/mrtk_et_nav_rotate.jpg)

In breve, gli script precedenti dovrebbero consentire di iniziare a usare lo sguardo fisso per varie attività di navigazione di input, ad esempio lo scorrimento di testo, lo zoom e la panoramica delle trame, nonché la rotazione dell'analisi degli ologrammi 3D.

### <a name="see-also"></a>Vedi anche

- [Configurazione di base di MRTK per l'uso del tracciamento oculare](eye-tracking-basic-setup.md)
- [Selezione della destinazione supportata dagli occhi](eye-tracking-target-selection.md)

---
[Torna a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)
