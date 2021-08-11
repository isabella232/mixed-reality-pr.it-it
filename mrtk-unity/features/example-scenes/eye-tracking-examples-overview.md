---
title: Panoramica degli esempi di tracciamento oculare
description: Esempio di creazione di tracciamento oculare in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 32ae64a470572dda71578948d5091887bea9e0e084d97ede7f2f14af596b5a6b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223219"
---
# <a name="eye-tracking-examples-overview"></a>Panoramica degli esempi di tracciamento oculare

Questo argomento descrive come iniziare rapidamente a usare il tracciamento oculare in MRTK sulla base di esempi di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking).
Questi esempi consentono di sperimentare una delle nuove funzionalità di input magiche: **tracciamento oculare!**
La demo include diversi casi d'uso, da attivazioni implicite basate sugli occhi  a come combinare facilmente le informazioni su ciò che si sta esaminando con l'input vocale **e** manuale.
In questo modo gli utenti possono selezionare e spostare in modo semplice e rapido il contenuto olografico nella visualizzazione semplicemente osservando una destinazione e pronunciando _"Seleziona"_ o eseguendo un movimento della mano.
Le demo includono anche un esempio di scorrimento con sguardo fisso, panoramica e zoom di testo e immagini su uno slate.
Infine, viene fornito un esempio per la registrazione e la visualizzazione dell'attenzione visiva dell'utente su uno slate 2D.
Nella sezione seguente sono disponibili altri dettagli sui diversi esempi inclusi nel pacchetto di esempio di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking):

![Elenco di scene di tracciamento oculare](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

La sezione seguente è una rapida panoramica delle singole scene di demo di tracciamento oculare.
Le scene della demo di tracciamento oculare di MRTK vengono [caricate in](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)modo aggiuntivo, che verrà illustrato di seguito come configurare.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Panoramica degli esempi di demo di tracciamento oculare

### <a name="eye-supported-target-selection"></a>[**Selezione della destinazione supportata dagli occhi**](../input/eye-tracking/eye-tracking-target-selection.md)

Questa esercitazione illustra la facilità di accesso ai dati dello sguardo fisso per selezionare le destinazioni.
Include un esempio di feedback sottile ma potente per fornire all'utente la certezza che una destinazione sia incentrata senza essere troppo grande.
Esiste anche un semplice esempio di notifiche intelligenti che scompaiono automaticamente dopo essere state lette.

**Riepilogo:** selezioni di destinazione veloci e senza sforzo usando una combinazione di occhi, voce e input della mano.

### <a name="eye-supported-navigation"></a>[**Navigazione supportata dagli occhi**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine che si leggono alcune informazioni su uno schermo distante o sul lettore e-reader e quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per visualizzare più contenuto.
O che ne dite di eseguire uno zoom diretto verso la posizione in cui si stava guardando?
Di seguito sono riportati alcuni esempi presentati in questa esercitazione relativi alla navigazione con supporto oculare.
Esiste anche un esempio di rotazione a mani libere degli ologrammi 3D facendo in modo che ruotino automaticamente in base allo stato attivo corrente.

**Riepilogo:** scorrimento, panoramica, zoom, rotazione 3D usando una combinazione di occhi, voce e input della mano.

### <a name="eye-supported-positioning"></a>[**Posizionamento supportato dagli occhi**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

Questa esercitazione illustra uno scenario di input denominato [Put-That-There](https://youtu.be/CbIn8p4_4CQ) che torna alla ricerca del MIT Media Lab all'inizio degli anni '80 con input oculare, mano e voce.
L'idea è semplice: trarre vantaggio dagli occhi per la selezione e il posizionamento rapidi della destinazione.
È sufficiente esaminare un ologramma e pronunciare _"put this",_ osservare dove si vuole posizionarlo e pronunciare _"there!"._
Per un posizionamento più preciso dell'ologramma, è possibile usare un input aggiuntivo dalle mani, dalla voce o dai controller.

**Riepilogo:** posizionamento degli ologrammi con occhi, voce e input della mano *(trascinamento della selezione).* Dispositivi di scorrimento supportati dagli occhi con occhi e mani.

### <a name="visualization-of-visual-attention"></a>**Visualizzazione dell'attenzione visiva**

I dati basati sul punto di vista degli utenti sono uno strumento estremamente potente per valutare l'usabilità di una progettazione e identificare i problemi in flussi di lavoro efficienti.
Questa esercitazione illustra diverse visualizzazioni del tracciamento oculare e il modo in cui si adattano alle diverse esigenze.
Vengono forniti esempi di base per la registrazione e il caricamento di dati di tracciamento oculare ed esempi su come visualizzarli.

**Riepilogo:** mappa di attenzione bidimensionale (mappe termica) sugli slate. Registrazione & riproduzione dei dati di tracciamento oculare.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configurazione dei campioni di tracciamento oculare di MRTK

### <a name="prerequisites"></a>Prerequisiti

Si noti che l'uso degli esempi di tracciamento oculare nel dispositivo richiede un HoloLens 2 e un pacchetto di app di esempio compilato con la funzionalità "Input sguardo fisso" nell'AppXManifest del pacchetto.

Per usare questi esempi di tracciamento oculare [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) nel dispositivo, assicurarsi di seguire questa procedura prima di compilare l'app in Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Load EyeTrackingDemo-00-RootScene.unity

*EyeTrackingDemo-00-RootScene* è lascena di base (radice) che include tutti i componenti principali di MRTK.
Questa è la scena che è necessario caricare per prima e da cui si eseguiranno le demo di tracciamento oculare.
Include un menu della scena grafica che consente di passare facilmente tra i diversi campioni di tracciamento oculare che verranno caricati [in modo aggiuntivo.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)

![Menu della scena nell'esempio di tracciamento oculare](../images/eye-tracking/mrtk_et_scenemenu.jpg)

La scena radice include alcuni componenti principali che verranno mantenuti nelle scene caricate in modo aggiuntivo, ad esempio i profili configurati per MRTK e la fotocamera della scena.
_MixedRealityBasicSceneSetup_ (vedere lo screenshot seguente) include uno script che carica automaticamente la scena di riferimento all'avvio.
Per impostazione predefinita, si _tratta di EyeTrackingDemo-02-TargetSelection._  

![Esempio per lo script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Aggiunta di scene al menu di compilazione

Per caricare scene additive in fase di esecuzione, è necessario aggiungere prima queste scene al menu Build _Impostazioni -> Scenes in Build_ (Compila).
È importante che la scena radice sia visualizzata come prima scena nell'elenco:

![Compilare Impostazioni menu della scena per gli esempi di tracciamento oculare](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Riprodurre gli esempi di tracciamento oculare nell'editor di Unity

Dopo aver aggiunto le scene di tracciamento oculare al Impostazioni di compilazione e aver caricato _EyeTrackingDemo-00-RootScene,_ è possibile controllare un'ultima cosa: lo script _'OnLoadStartScene'_ collegato a _MixedRealityBasicSceneSetup_ GameObject è abilitato? Questo consente alla scena radice di sapere quale scena demo caricare per prima.

![Esempio per lo script OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

È possibile eseguire il roll-to-roll. Premere _"Play"_!
Verranno visualizzate diverse gemme e il menu della scena nella parte superiore.

![Screenshot di esempio dalla scena di selezione della destinazione ET](../images/eye-tracking/mrtk_et_targetselect.png)

Si noterà anche un piccolo cerchio semitrasparente al centro della visualizzazione del gioco.
Funge da indicatore (cursore) dello sguardo fisso _simulato:_ è sufficiente premere il pulsante destro del _mouse_ e spostare il mouse per modificarne la posizione.
Quando il cursore si posiziona sulle gemme, si noterà che verrà allineato al centro della gemma attualmente visualizzata.
Questo è un ottimo modo per verificare se gli eventi vengono attivati come previsto quando _si "esamina&quot;_ una destinazione.
Tenere presente che lo _sguardo fisso simulato_ tramite il controllo del mouse è un integratore piuttosto scarso dei movimenti oculari rapidi e non intenzionali.
Tuttavia, è ideale per testare le funzionalità di base prima di eseguire l'iterazione della progettazione distribuerla nel HoloLens 2 dispositivo.
Tornare alla scena di esempio del tracciamento oculare: la gemma ruota fino a quando viene guardata e può essere distrutta &quot;guardando&quot; e ...

- Premere _INVIO_ (che simula il pronunciare &quot;select")
- Pronunciare _"select"_ nel microfono
- Mentre si preme _BARRA SPAZIATRICE_ per visualizzare l'input della mano simulato, fare clic sul pulsante sinistro del mouse per eseguire un avvicinamento delle dita simulato

Nell'esercitazione Selezione destinazione supportata dagli occhi viene descritto in modo più dettagliato come ottenere [**queste**](../input/eye-tracking/eye-tracking-target-selection.md) interazioni.

Quando si sposta il cursore verso l'alto fino alla barra dei menu superiore nella scena, si noterà che l'elemento attualmente al passaggio del mouse verrà evidenziato in modo secondario.
È possibile selezionare l'elemento attualmente evidenziato usando uno dei metodi di commit descritti in precedenza, ad esempio premendo _INVIO._
In questo modo è possibile passare da una scena di esempio di tracciamento oculare all'altra.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Come testare sotto-scene specifiche

Quando si lavora a uno scenario specifico, è possibile che non si voglia scorrere ogni volta il menu della scena.
Al contrario, è possibile iniziare direttamente dalla scena su cui si sta lavorando quando si preme il _pulsante_ Riproduci.
non è un problema. Ecco cosa è possibile fare:

1. Caricare la _scena_ radice
2. Nella _scena radice_ disabilitare lo script _'OnLoadStartScene'_
3. _Trascinare e rilasciare_ una delle scene di test di tracciamento oculare descritte di seguito (o qualsiasi altra scena) nella visualizzazione _Gerarchia,_ come illustrato nello screenshot seguente.

    ![Esempio per la scena additiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Premere _Riproduci_

Si noti che il caricamento della scena secondaria come questo non è persistente: ciò significa che se si distribuisce l'app nel dispositivo HoloLens 2, verrà caricata solo la scena radice (presupponendo che venga visualizzata nella parte superiore del Impostazioni di compilazione).
Inoltre, quando si condivide il progetto con altri utenti, le scene secondarie non vengono caricate automaticamente.

---

Ora che si è in grado di usare le scene di esempio di tracciamento oculare di MRTK, è possibile continuare con un approfondimento su come selezionare gli ologrammi con gli occhi: selezione della destinazione supportata dagli [occhi.](../input/eye-tracking/eye-tracking-target-selection.md)

---
[Torna a "Tracciamento oculare in MixedRealityToolkit"](../input/eye-tracking/eye-tracking-Main.md)
