---
title: Panoramica degli esempi di tracciamento oculare
description: Esempio di creazione di tracciamento oculare in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175545"
---
# <a name="eye-tracking-examples-overview"></a>Panoramica degli esempi di tracciamento oculare

Questo argomento descrive come iniziare rapidamente a usare il tracciamento oculare in MRTK compilando esempi di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking).
Questi esempi consentono di sperimentare una delle nuove funzionalità di input magiche: **Tracciamento oculare**!
La demo include diversi casi d'uso, dalle attivazioni implicite basate sugli occhi  a come combinare facilmente le informazioni su ciò che si sta esaminando con l'input vocale **e** manuale.
In questo modo gli utenti possono selezionare e spostare in modo semplice e rapido il contenuto olografico nella visualizzazione semplicemente osservando una destinazione e pronunciando _"Seleziona"_ o eseguendo un movimento della mano.
Le demo includono anche un esempio di scorrimento con sguardo rivolto verso gli occhi, panoramica e zoom di testo e immagini su uno slate.
Infine, viene fornito un esempio per registrare e visualizzare l'attenzione visiva dell'utente su uno slate 2D.
Nella sezione seguente sono disponibili altri dettagli sui diversi esempi inclusi nel pacchetto di esempio di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking):

![Elenco di scene di tracciamento oculare](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

La sezione seguente è una rapida panoramica delle singole scene della demo di tracciamento oculare.
Le scene demo di tracciamento oculare MRTK vengono caricate in modo [aggiuntivo,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)che verrà illustrato di seguito come configurare.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Panoramica degli esempi di demo di tracciamento oculare

### <a name="eye-supported-target-selection"></a>[**Selezione della destinazione supportata dagli occhi**](../input/eye-tracking/eye-tracking-target-selection.md)

Questa esercitazione illustra la facilità di accesso ai dati dello sguardo fisso per selezionare le destinazioni.
Include un esempio di feedback sottile ma potente per fornire all'utente la certezza che un obiettivo è incentrato senza essere eccessivo.
Esiste anche un semplice esempio di notifiche intelligenti che scompaiono automaticamente dopo la lettura.

**Riepilogo:** selezioni di destinazione veloci e senza sforzo usando una combinazione di occhi, voce e input manuale.

### <a name="eye-supported-navigation"></a>[**Navigazione supportata dagli occhi**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine che si leggono alcune informazioni su uno schermo distante o sul lettore e quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per visualizzare più contenuto.
O che ne dite di zoomare magicamente direttamente verso la posizione in cui si stava guardando?
Questi sono alcuni degli esempi presentati in questa esercitazione relativa alla navigazione con supporto oculare.
Esiste anche un esempio di rotazione senza mani degli ologrammi 3D facendoli ruotare automaticamente in base allo stato attivo corrente.

**Riepilogo:** scorrimento, panoramica, zoom, rotazione 3D usando una combinazione di occhi, voce e input manuale.

### <a name="eye-supported-positioning"></a>[**Posizionamento supportato dagli occhi**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

Questa esercitazione illustra uno scenario di input denominato [Put-That-There](https://youtu.be/CbIn8p4_4CQ) che risale alla ricerca del MIT Media Lab nei primi anni '80 con input oculare, mano e voce.
L'idea è semplice: trarre vantaggio dagli occhi per la selezione e il posizionamento rapidi del target.
È sufficiente esaminare un ologramma e pronunciare _"put this",_ esaminare la posizione in cui si vuole posizionarlo e pronunciare _"there!"._
Per un posizionamento più preciso dell'ologramma, è possibile usare input aggiuntivo dalle mani, dalla voce o dai controller.

**Riepilogo:** posizionamento di ologrammi con occhi, voce e input manuale (*trascinamento della selezione).* Dispositivi di scorrimento supportati dagli occhi con occhi e mani.

### <a name="visualization-of-visual-attention"></a>**Visualizzazione dell'attenzione visiva**

I dati basati sull'aspetto degli utenti rendono uno strumento estremamente potente per valutare l'usabilità di una progettazione e identificare i problemi in flussi di lavoro efficienti.
Questa esercitazione illustra le diverse visualizzazioni del tracciamento oculare e il modo in cui si adattano alle diverse esigenze.
Vengono forniti esempi di base per la registrazione e il caricamento di dati di tracciamento oculare ed esempi per visualizzarli.

**Riepilogo:** mappa di attenzione bidimensionale (mappa termica) su ardesia. Registrazione & riproduzione dei dati di tracciamento oculare.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configurazione dei campioni di tracciamento oculare MRTK

### <a name="prerequisites"></a>Prerequisiti

Si noti che l'uso degli esempi di tracciamento oculare nel dispositivo richiede un HoloLens 2 e un pacchetto di app di esempio compilato con la funzionalità "Input sguardo fisso" nell'app AppXManifest del pacchetto.

Per usare questi esempi di tracciamento oculare [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) nel dispositivo, assicurarsi di seguire questa procedura prima di compilare l'app in Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Caricare EyeTrackingDemo-00-RootScene.unity

*EyeTrackingDemo-00-RootScene* è la scena di base (_radice_) in cui sono inclusi tutti i componenti MRTK principali.
Questa è la scena che è necessario caricare per prima e da cui si eseguiranno le demo di tracciamento oculare.
È dotato di un menu della scena grafica che consente di passare facilmente tra i diversi campioni di tracciamento oculare che verranno [caricati in modo aggiuntivo.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)

![Menu Scena nell'esempio di tracciamento oculare](../images/eye-tracking/mrtk_et_scenemenu.jpg)

La scena radice include alcuni componenti principali che verranno mantenuti tra le scene caricate in modo aggiuntivo, ad esempio i profili configurati mrtk e la fotocamera della scena.
_MixedRealityBasicSceneSetup_ (vedere lo screenshot seguente) include uno script che carica automaticamente la scena di riferimento all'avvio.
Per impostazione predefinita, si _tratta di EyeTrackingDemo-02-TargetSelection._  

![Esempio per lo script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Aggiunta di scene al menu di compilazione

Per caricare le scene additive durante il runtime, è necessario aggiungere prima queste scene al menu Build _Impostazioni -> Scenes in Build_ (Crea).
È importante che la scena radice sia visualizzata come prima scena nell'elenco:

![Compilare Impostazioni menu della scena per i campioni di tracciamento oculare](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Riprodurre i campioni di tracciamento oculare nell'editor di Unity

Dopo aver aggiunto le scene di tracciamento oculare al Impostazioni di compilazione e aver caricato _EyeTrackingDemo-00-RootScene,_ è possibile controllare un'ultima cosa: lo script _'OnLoadStartScene'_ collegato a _MixedRealityBasicSceneSetup_ GameObject è abilitato? Ciò consente alla scena radice di sapere quale scena demo caricare per prima.

![Esempio per lo script OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Si passi ora. Premere _"Play"_!
Dovrebbero essere visualizzate diverse gemme e il menu della scena nella parte superiore.

![Screenshot di esempio dalla scena di selezione della destinazione ET](../images/eye-tracking/mrtk_et_targetselect.png)

Si noterà anche un piccolo cerchio semitrasparente al centro della visualizzazione del gioco.
Funge da indicatore (cursore) dello sguardo _fisso simulato:_ è sufficiente premere il pulsante destro del _mouse_ e spostare il mouse per modificarne la posizione.
Quando il cursore passa il mouse sulle gemme, si noterà che verrà allineato al centro della gemma attualmente visualizzata.
Questo è un ottimo modo per verificare se gli eventi vengono attivati come previsto quando _si esamina_ una destinazione.
Tenere presente che lo sguardo _fisso simulato_ tramite il controllo del mouse è un integratore piuttosto scarso per i movimenti oculari rapidi e non intenzionali.
Tuttavia, è ideale per testare le funzionalità di base prima di eseguire l'iterazione della progettazione distribuerla nel HoloLens 2 dispositivo.
Tornando alla scena del campione di tracciamento oculare: la gemma ruota fino a quando viene osservata e può essere distrutta "guardandola&quot; e ...

- Premendo _INVIO_ (che simula la pronuncia di &quot;select")
- Pronunciare _"select"_ nel microfono
- Mentre si preme _Spazio_ per visualizzare l'input manuale simulato, fare clic sul pulsante sinistro del mouse per eseguire un avvicinamento delle dita simulato

Viene descritto in modo più dettagliato come è possibile ottenere queste interazioni nell'esercitazione Selezione destinazione supportata [**dagli**](../input/eye-tracking/eye-tracking-target-selection.md) occhi.

Quando si sposta il cursore verso l'alto nella barra dei menu superiore della scena, si noterà che l'elemento attualmente selezionato verrà evidenziato in modo secondario.
È possibile selezionare l'elemento attualmente evidenziato usando uno dei metodi di commit descritti in precedenza, ad esempio premendo _INVIO._
In questo modo è possibile passare da una scena all'altra del campione di tracciamento oculare.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Come testare scene secondarie specifiche

Quando si lavora a uno scenario specifico, è possibile che non si voglia passare attraverso il menu della scena ogni volta.
È invece possibile iniziare direttamente dalla scena su cui si sta lavorando quando si preme il _pulsante_ Riproduci.
non è un problema. Ecco cosa è possibile fare:

1. Caricare la _scena_ radice
2. Nella scena _radice_ disabilitare lo script _'OnLoadStartScene'_
3. _Trascinare una_ delle scene di test di tracciamento oculare descritte di seguito (o qualsiasi altra scena) nella visualizzazione _Gerarchia,_ come illustrato nello screenshot seguente.

    ![Esempio di scena additiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Premere _Riproduci_

Si noti che il caricamento della scena secondaria come questa non è persistente: ciò significa che se si distribuisce l'app nel dispositivo HoloLens 2, verrà caricata solo la scena radice (presupponendo che venga visualizzata nella parte superiore del Impostazioni di compilazione).
Inoltre, quando si condivide il progetto con altri utenti, le scene secondarie non vengono caricate automaticamente.

---

Ora che si sa come usare le scene di esempio di tracciamento oculare MRTK, è possibile continuare a approfondire come selezionare gli ologrammi con gli occhi: selezione di destinazione supportata dagli [occhi.](../input/eye-tracking/eye-tracking-target-selection.md)

---
[Tornare a "Tracciamento oculare in MixedRealityToolkit"](../input/eye-tracking/eye-tracking-Main.md)
