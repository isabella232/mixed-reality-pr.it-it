---
title: Navigazione tramite tracciamento oculare
description: Come usare il targeting oculare per la navigazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: d966bbe1d3a256e55c62532e8101c1f2846e1136
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145273"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navigazione con supporto oculare in MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Si supponga di leggere informazioni su uno slate e, quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per visualizzare più contenuto. In alternativa, è possibile fare zoom avanti nel punto in cui si sta guardando. La mappa regola automaticamente anche il contenuto per mantenere gli elementi di interesse all'interno del campo di visualizzazione. Un'altra applicazione interessante è l'osservazione senza mani degli ologrammi 3D portando automaticamente le parti dell'ologramma che si sta guardando in avanti. Questi sono alcuni degli esempi descritti in questa pagina nel contesto della navigazione supportata dagli occhi.

Le descrizioni seguenti presuppongono che si abbia già familiarità con la configurazione del tracciamento oculare nella [scena MRTK](eye-tracking-basic-setup.md) e con le nozioni di base sull'accesso ai dati di tracciamento oculare [in](eye-tracking-target-selection.md) MRTK Unity.
Gli esempi illustrati di seguito fanno tutti parte della `EyeTrackingDemo-03-Navigation` scena (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation).

**Riepilogo:** Scorrimento automatico del testo, panoramica supportata da sguardo fisso e zoom di una mappa virtuale, rotazione 3D diretta con sguardo fisso senza mani.

## <a name="auto-scroll"></a>Scorrimento automatico

Lo scorrimento automatico consente all'utente di scorrere i testi senza alzare un dito.
È sufficiente continuare a leggere e il testo scorrerà automaticamente verso l'alto o verso il basso a seconda della posizione in cui l'utente sta cercando.
È possibile iniziare dall'esempio fornito in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
Questo esempio usa un [componente TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) per consentire il caricamento e la formattazione flessibili del nuovo testo.
Per abilitare lo scorrimento automatico, è sufficiente aggiungere i due script seguenti al componente collisore della casella di testo:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Per scorrere un [oggetto TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) o più in generale un [componente RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) puoi usare lo script [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Se vuoi scorrere una trama anziché un [oggetto RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html)usa [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) invece di [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Di seguito sono illustrati in dettaglio i parametri di [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) disponibili nell'editor di Unity:

Parametri | Descrizione
:---- | :----
LimitPanning | Se abilitata, arresta il contenuto scorrevole al limite.
RectTransfToNavigate | Riferimento a [RectTransform in](https://docs.unity3d.com/ScriptReference/RectTransform.html) cui scorrere.
RefToViewport | Riferimento all'elemento [RectTransform padre](https://docs.unity3d.com/ScriptReference/RectTransform.html) del contenuto scorrevole per determinare l'offset e il limite corretti.
AutoGazeScrollIsActive | Se abilitata, il testo scorrerà automaticamente se l'utente esamina un'area *attiva(ad* esempio, la parte superiore e inferiore del pannello di scorrimento se la velocità di scorrimento verticale non è zero).
ScrollSpeed_x | Se impostato su un valore diverso da zero, verrà abilitato lo scorrimento orizzontale. I valori negativi significano una modifica nella direzione di scorrimento: da sinistra a destra e da destra a sinistra.
ScrollSpeed_y | Se impostato su un valore diverso da zero, verrà abilitato lo scorrimento verticale. I valori negativi significano una modifica nella direzione di scorrimento: dall'alto verso il basso o verso il basso verso l'alto.
MinDistFromCenterForAutoScroll | Distanza minima normalizzata in x e y dal centro della casella di selezione della destinazione (0, 0) per lo scorrimento. Pertanto, i valori devono essere compresi tra 0 (sempre scorrimento) e 0,5 (senza scorrimento).
UseSkimProofing | Se abilitata, impedisce improvvisi movimenti di scorrimento quando ci si guarda rapidamente. In questo modo, tuttavia, lo scorrimento potrebbe risultare meno reattivo. Può essere ottimizzato con il *valore SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Più basso è il valore, più lento sarà lo scorrimento dopo lo scorrimento. Valore consigliato: 5.

![Configurazione dello scorrimento supportata dagli occhi in Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

L'associazione _del componente EyeTrackingTarget_ consente di gestire in modo flessibile gli eventi correlati allo sguardo oculare.
L'esempio di scorrimento illustra lo  scorrimento del testo che inizia quando l'utente guarda il pannello e si arresta quando l'utente lo *sta* allontanando.
![Configurazione dello scorrimento supportata dagli occhi in Unity: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Panoramica e zoom supportati da sguardo fisso

Chi non ha mai usato una mappa virtuale prima per cercare la propria casa o per esplorare luoghi completamente nuovi? Il tracciamento oculare consente di approfondire direttamente le parti a cui si è interessati e, una volta ingranditi, è possibile seguire senza problemi il corso di una strada per esplorare il quartiere.
Ciò è utile non solo per esplorare le mappe geografiche, ma anche per verificare i dettagli nelle fotografie, nelle visualizzazioni dei dati o persino nelle immagini mediche in streaming live. Usare questa funzionalità nell'app è semplice. Per il contenuto sottoposto a rendering in [una trama]( https://docs.unity3d.com/ScriptReference/Texture.html) (ad esempio, una foto, dati trasmessi in streaming), è sufficiente aggiungere lo script [PanZoomTexture.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture)
Per [rectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) usare [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). Estendendo [la funzionalità Scorrimento](#auto-scroll) automatico, si abilita essenzialmente lo scorrimento verticale e orizzontale contemporaneamente e l'ingrandimento del contenuto intorno al punto attivo corrente dell'utente.

Parametri | Descrizione
:---- | :----
LimitPanning | Se abilitata, arresta il contenuto scorrevole al limite.
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
Pan_Speed_y | Se impostato su un valore diverso da zero, verrà abilitato lo scorrimento verticale. I valori negativi significano una modifica nella direzione di scorrimento: dall'alto verso il basso o verso il basso verso l'alto.
Pan_MinDistFromCenter | Distanza minima normalizzata in x e y dal centro della casella di selezione della destinazione (0, 0) per lo scorrimento. Pertanto, i valori devono essere compresi tra 0 (sempre scorrimento) e 0,5 (senza scorrimento).
UseSkimProofing | Se abilitata, impedisce movimenti improvvisi di scorrimento quando ci si guarda rapidamente. In questo modo, tuttavia, lo scorrimento potrebbe risultare meno reattivo. Può essere ottimizzato con il *valore SkimProofUpdateSpeed.*
SkimProofUpdateSpeed | Più basso è il valore, più lento sarà lo scorrimento dopo lo scorrimento. Valore consigliato: 5.

![Configurazione della panoramica e dello zoom supportate dagli occhi in Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotazione 3D basata sull'attenzione

Si immagini di guardare un oggetto 3D e che le parti che si vogliono vedere più da vicino si rivolvano verso di te, come se il sistema leggesse la tua mente e sappia di ruotare l'elemento verso di te.
Questa è l'idea per le rotazioni 3D basate sull'attenzione che consentono di analizzare tutti i lati di un ologramma senza elevare un dito.
Per abilitare questo comportamento, è sufficiente aggiungere lo script [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) alla parte di GameObject con un [componente Collider.](https://docs.unity3d.com/ScriptReference/Collider.html)
È possibile modificare diversi parametri elencati di seguito per limitare la velocità e le direzioni in cui verrà ruotato l'ologramma.

Come si può immaginare, l'attività di questo comportamento in qualsiasi momento può diventare rapidamente piuttosto distratta in una scena molto piena.
Questo è il motivo per cui è possibile iniziare con questo comportamento disabilitato e quindi abilitarlo rapidamente usando i comandi vocali.
In alternativa, è stato aggiunto un esempio in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) per usare [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) per cui è possibile selezionare un obiettivo mirato e che vola davanti a se stesso, semplicemente *pronunciando "Come to me".*

Una volta attivata la modalità near, la modalità di rotazione automatica viene abilitata automaticamente.
In questa modalità è possibile osservarlo da tutti i lati semplicemente chinandosi e osservandolo, aggirandosi o cercando di afferrarlo e ruotarlo con la mano. Quando si ignora la destinazione (si guarda & o si pronuncia *"Send back"),* la destinazione torna alla posizione originale e smette di reagire da lontano.

Parametri | Descrizione
:---- | :----
SpeedX | Velocità di rotazione orizzontale.
Veloce | Velocità di rotazione verticale.
InverseX | Per invertire la direzione di rotazione orizzontale.
Inversa | Per invertire la direzione di rotazione verticale.
RotationThreshInDegrees | Se l'angolo tra 'Gaze to Target' e 'Camera to Target' è minore di questo valore, non eseguire alcuna operazione. Ciò consente di evitare piccole rotazioni instabilità.
MinRotX | Angolo di rotazione orizzontale minimo. Ciò consente di limitare la rotazione in direzioni diverse.
MaxRotX | Angolo di rotazione orizzontale massimo. Ciò consente di limitare la rotazione in direzioni diverse.
MinRotY | Angolo di rotazione verticale minimo per limitare la rotazione intorno all'asse x.
MaxRotY | Angolo di rotazione verticale massimo per limitare la rotazione intorno all'asse y.

![Configurazione della rotazione 3D supportata dagli occhi in Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

In breve, gli script precedenti dovrebbero consentire di iniziare a usare lo sguardo fisso per varie attività di navigazione di input, ad esempio lo scorrimento di testo, lo zoom e la panoramica delle trame, nonché la rotazione dell'analisi degli ologrammi 3D.

### <a name="see-also"></a>Vedi anche

- [Configurazione di base di MRTK per l'uso del tracciamento oculare](eye-tracking-basic-setup.md)
- [Selezione della destinazione supportata dagli occhi](eye-tracking-target-selection.md)

---
[Torna a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)
