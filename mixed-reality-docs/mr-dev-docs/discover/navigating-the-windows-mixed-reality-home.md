---
title: Esplorazione dello spazio iniziale di Windows Mixed Reality
description: Informazioni su come esplorare la Windows Mixed Reality home page HoloLens e Windows Mixed Reality visori VR.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell, sistema operativo, piattaforma, casa di casa, casa, casa, ambiente, start, menu Start, menu Home, pin, app, avviare app, posizionare app, teletrasporto, spostare, esplorare, visore VR di realtà mista, visore VR di realtà virtuale, che cos'è la realtà virtuale
ms.openlocfilehash: 39ca5e974e242019d7eb14fba0362151213c6558cce7f13328390712b3642901
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190274"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Esplorazione dello spazio iniziale di Windows Mixed Reality

Proprio come l Windows'esperienza pc inizia con il desktop, Windows Mixed Reality inizia con la home page. La Windows Mixed Reality usa la nostra innata capacità di comprendere ed esplorare le posizioni 3D. Con HoloLens, la casa è lo spazio fisico, ma con visori VR immersive, la casa è un luogo virtuale.

La home page è anche la posizione in cui si userà il menu Start per aprire e inserire app e contenuto. Puoi riempire la tua casa con contenuti di realtà mista e multitasking usando più app contemporaneamente. Gli elementi posizionati in casa rimangono in questa posizione, anche se si riavvia il dispositivo.

## <a name="start-menu"></a>Menu Start

![Menu Start Microsoft HoloLens](images/start-500px.png)

Il menu Start è costituito da:
* Informazioni di sistema (stato della rete, percentuale della batteria, ora corrente e volume)
* Cortana (nei visori VR immersive, un riquadro Start, nella HoloLens, nella parte superiore di Start)
* App aggiunte
* Pulsante Tutte le app (segno più)
* Pulsanti foto e video per [l'acquisizione di realtà mista](/hololens/holographic-photos-and-videos)

Passare dalle app aggiunte alle visualizzazioni Tutte le app selezionando i pulsanti più o meno. Per aprire il menu Start in HoloLens, usare il movimento di fiore. In un visore VR immersive premere il pulsante Windows sul controller.

## <a name="launching-apps"></a>Avvio di app

Per avviare un'app, selezionarla nel menu Start. Il menu Start scomparirà e l'app verrà aperta in modalità di posizionamento, come finestra 2D o come [modello 3D.](../distribute/implementing-3d-app-launchers.md)

Per eseguire l'app, è necessario posizionarla nell'home page:
1. Usare lo [sguardo fisso](../design/gaze-and-commit.md) o il controller per posizionare l'app nel punto desiderato. Si regola automaticamente (in dimensioni e posizione) in base allo spazio in cui viene posizionato.
2. Posizionare l'app usando il tocco (HoloLens) o il pulsante Seleziona (visori VR immersive). Per annullare e riportare il menu Start, usare il movimento a fiori o il Windows pulsante.

[Le app 2D](../develop/porting-apps/building-2d-apps.md)create per desktop, dispositivi mobili o Xbox possono essere modificate per l'esecuzione come app immersive di realtà mista usando [l'API HolographicSpace.](/uwp/api/Windows.Graphics.Holographic.HolographicSpace) Un'app immersiva consente all'utente di uscire da casa e di trasformarsi in un'esperienza immersiva. Gli utenti possono tornare a casa con il movimento di fiore (HoloLens) o premendo il pulsante Windows sul controller (visori VR immersive).

Le app possono essere avviate anche tramite un'API da app ad app o tramite Cortana.

![App nella home Windows Mixed Reality home](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Spostamento e modifica delle app

Selezionare **Regola sulla** barra dell'app per visualizzare i controlli che spostano, ridimensionano e ruotano il contenuto di realtà mista. Al termine, selezionare **Fine.**

![Lo slate del negozio in modalità di regolazione (cornice blu). Si noti che la barra dell'app (in alto) è stata modificata per includere i pulsanti "Fine" e "Rimuovi".](images/adjust-500px.png)

App diverse possono avere altre opzioni sulla barra dell'app. Ad esempio, Microsoft Edge opzioni *Scroll*, *Drag* *e Zoom.* 

![Barra delle app per app 2D in esecuzione in HoloLens](images/holobar-500px.png)

Il **pulsante** Indietro consente di tornare alle schermate visualizzate in precedenza nell'app. Si arresta quando si raggiunge l'inizio delle esperienze visualizzate nell'app e non si passa ad altre app.

## <a name="getting-around-your-home"></a>Spostarsi a casa

Con **HoloLens**, si passa attraverso lo spazio fisico per spostarsi all'interno della casa.

Con **i visori VR** immersive è possibile spostarsi all'interno di un'area simile nel mondo virtuale e spostarsi all'interno di un'area simile. Per spostarsi su distanze più lunghe, usare la levetta sul controller per "attraversare" virtualmente oppure è possibile usare il *teletrasporto* per saltare immediatamente distanze più lunghe.

![Teletrasporto nella Windows Mixed Reality home](images/teleportation-500px.png)

**Per teletrasportare:**
1. Visualizzare il reticolo di teletrasporto.
   * Uso [dei controller del](../design/motion-controllers.md)movimento: premere la levetta in avanti e posizionarla in tale posizione.
   * Usando un controller Xbox: premi la levetta sinistra in avanti e tienila in tale posizione.
   * Uso del mouse: tenere premuto il pulsante destro del mouse e usare la rotellina del mouse per ruotare la direzione da affrontare quando si teletrasporta.
2. Posizionare il reticolo nel punto in cui si vuole teletrasportarsi.
   * Uso [dei controller del](../design/motion-controllers.md)movimento: inclinare il controller (su cui si tiene la levetta in avanti) per spostare il reticolo.
   * Uso di un controller Xbox: usare lo [sguardo fisso](../design/gaze-and-commit.md) per spostare il reticolo.
   * Uso del mouse: spostare il mouse per spostare il reticolo.
3. Rilasciare il pulsante per teletrasportare il punto in cui è stato posizionato il reticolo.

**Per virtualmente "walk:"**
* Uso [dei controller del](../design/motion-controllers.md)movimento: fai clic sulla levetta e tieni premuto, quindi sposta la levetta nella direzione in cui vuoi "walk".
* Uso di un controller Xbox: fai clic sulla levetta sinistra e tieni premuto, quindi sposta la levetta nella direzione in cui vuoi "walk".

## <a name="immersive-headset-input-support"></a>Supporto per l'input del visore VR immersive

[Windows Mixed Reality visori VR immersive](immersive-headset-hardware-details.md) supportano più tipi di input per spostarsi nella Windows Mixed Reality home. HoloLens non supporta gli input degli accessori per la navigazione, perché si può spostarsi fisicamente e vedere l'ambiente. Tuttavia, HoloLens supporta [input per](hardware-accessories.md) l'interazione con le app.

### <a name="motion-controllers"></a>Controller del movimento

L'esperienza Windows Mixed Reality migliore sarà con i [](../design/motion-controllers.md) controller del movimento Windows Mixed Reality che supportano il rilevamento di sei gradi di libertà usando solo i sensori nel visore VR, senza fotocamere esterne o marcatori necessari.

I comandi di navigazione saranno presto disponibili.

### <a name="gamepad"></a>Game pad
* **Levetta sinistra:**
  * Tenere premuta la levetta sinistra in avanti per visualizzare il [reticolo di teletrasporto.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
  * Toccare la levetta a sinistra, a destra o indietro per spostarsi a sinistra, a destra o indietro in piccoli incrementi.
  * Fare clic sulla levetta sinistra e tenere premuta, quindi spostare la levetta nella direzione in cui si vuole [praticamente "andare".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Toccare la **levetta destra** verso sinistra o destra per ruotare di 45 gradi la direzione verso cui ci si trova.
* Premendo il **pulsante A** si seleziona e si comporta come il movimento di [tocco dell'aria.](../design/gaze-and-commit.md#composite-gestures)
* Premendo il **pulsante Guida** viene visualizzata la [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu) e si comporta come il movimento [di fiore.](../design/system-gesture.md#bloom)
* Premendo i **trigger sinistro e** destro è possibile fare zoom avanti e indietro di un'app desktop 2D con cui si interagisce nella home page.

### <a name="keyboard-and-mouse"></a>Tastiera e mouse

**Nota:** Usa **Windows tasto + Y** per spostare il mouse tra il controllo del desktop del PC e l'Windows Mixed Reality home.

All'interno Windows Mixed Reality home page:
* Premendo il **pulsante sinistro del** mouse si seleziona e si comporta come il movimento di tocco [dell'aria.](../design/gaze-and-commit.md#composite-gestures)
* Tenendo premuto **il pulsante destro del** mouse viene visualizzata la [ritirata del teletrasporto.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Premendo il **Windows** sulla tastiera, viene visualizzato il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu) e si comporta come il movimento [di fiore.](../design/system-gesture.md#bloom)
* Quando [si](../design/gaze-and-commit.md) guarda un'app desktop 2D, è possibile fare clic con il pulsante sinistro  del mouse per **selezionare,** fare clic con il pulsante destro del mouse per visualizzare i menu di scelta rapida e usare la rotellina di scorrimento per scorrere (proprio come sul desktop del PC). 

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) è l'assistente personale in Windows Mixed Reality, proprio come su PC e telefono. HoloLens ha un microfono incorporato, ma i visori VR immersive possono richiedere hardware aggiuntivo. Usare Cortana per aprire le app, riavviare il dispositivo, cercare elementi online e altro ancora. Gli sviluppatori possono anche scegliere [di integrare Cortana](https://dev.windows.com/cortana) nelle proprie esperienze.

È anche possibile usare i comandi vocali per spostarsi in casa. Ad esempio, posizionare il mouse su un pulsante (usando lo [sguardo fisso](../design/gaze-and-commit.md) o un controller, a seconda del dispositivo) e pronunciare "Seleziona". Altri comandi vocali includono "Vai alla pagina iniziale", "Bigger", "Smaller", "Close" e "Guardami".

## <a name="store-settings-and-system-apps"></a>Store, Impostazioni e app di sistema

Windows Mixed Reality include diverse app predefinite, ad esempio:
* **Microsoft Store** ottenere app e giochi
* **Hub di Feedback** inviare commenti e suggerimenti sul sistema e sulle app di sistema
* **Impostazioni configurare** le impostazioni di sistema [(inclusi gli aggiornamenti di rete](/hololens/hololens-network) e di sistema)
* **Microsoft Edge** esplorare i siti Web
* **Foto** visualizzare e condividere foto e video
* **Calibrazione** (HoloLens solo per la regolazione dell'esperienza HoloLens all'utente corrente
* **Informazioni su movimenti** (HoloLens) **o Esercitazione per la realtà mista** (visori VR immersive) per informazioni sull'uso del dispositivo
* **Visualizzatore 3D** decorare il tuo mondo con contenuti di realtà mista
* **Portale realtà mista** (desktop) per la configurazione e la gestione del visore VR immersive e lo streaming di un'anteprima live della visualizzazione nel visore VR per la visualizzazione da parte di altri utenti.
* **Film e TV per** la visualizzazione di video 360 e degli ultimi film e programmi tv
* **Cortana** tutte le esigenze dell'assistente virtuale
* **Desktop** (visori VR immersive) per la visualizzazione del monitor desktop in un visore VR immersive
* **Esplora file** Accedere a file e cartelle presenti nel dispositivo

## <a name="see-also"></a>Vedi anche
* [Visualizzazioni delle app](../design/app-views.md)
* [Controller del movimento](../design/motion-controllers.md)
* [Accessori hardware](hardware-accessories.md)
* [Considerazioni relative all'ambiente per HoloLens](/hololens/hololens-environment-considerations)
* [Implementazione di launcher di app 3D](../distribute/implementing-3d-app-launchers.md)
* [Creazione di modelli 3D da usare nella home Windows Mixed Reality home](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)