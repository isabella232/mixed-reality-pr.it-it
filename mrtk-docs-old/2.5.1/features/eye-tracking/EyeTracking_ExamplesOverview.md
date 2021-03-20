---
title: EyeTracking_ExampleOverview
description: Esempio per compilare eyetracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 2b9d373363bee8d7ad3482fc234c8966f6258706
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682444"
---
# <a name="eye-tracking-examples"></a>Esempi di rilevamento degli occhi

Questo argomento descrive come iniziare rapidamente a usare la gestione degli occhi in MRTK tramite la compilazione degli esempi di rilevamento degli occhi di MRTK (assets/MRTK/examples/Demos/EyeTracking).
Questi esempi consentono di sperimentare una delle nuove funzionalità di input magiche: **rilevamento degli occhi**
La demo include diversi casi d'uso, che vanno da attivazioni basate sugli sguardi implicite a come combinare facilmente le informazioni relative a ciò che si sta osservando con l'input **vocale** e **manuale** .
Ciò consente agli utenti di selezionare e spostare in modo rapido e semplice il contenuto olografico attraverso la visualizzazione semplicemente esaminando una destinazione e pronunciando _' Select '_ o eseguendo un gesto manuale.
Le demo includono anche un esempio di scorrimento con sguardo diretto, panning e zoom del testo e delle immagini in uno Slate.
Infine, viene fornito un esempio per la registrazione e la visualizzazione dell'attenzione visiva dell'utente su uno Slate 2D.
Nella sezione seguente sono disponibili ulteriori informazioni su tutti i diversi esempi nel pacchetto di esempio MRTK Eye Tracking (assets/MRTK/examples/Demos/EyeTracking):

![Elenco di scene di rilevamento degli occhi](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

La sezione seguente è una rapida panoramica delle informazioni sulle singole scene demo di rilevamento degli occhi.
Le scene demo di MRTK Eye Tracking vengono [caricate in modo additivo](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), che verrà illustrato di seguito come configurare.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Panoramica degli esempi di demo per la verifica degli occhi

### <a name="eye-supported-target-selection"></a>[**Selezione della destinazione supportata dagli occhi**](EyeTracking_TargetSelection.md)

In questa esercitazione viene illustrata la facilità di accesso ai dati degli occhi per selezionare le destinazioni.
Include un esempio di commenti impercettibili ma potenti per fornire all'utente la certezza che una destinazione sia concentrata senza sopraffare.
Inoltre, è disponibile un semplice esempio di notifiche intelligenti che scompaiono automaticamente dopo la lettura.

**Riepilogo**: selezioni di destinazione rapide e veloci con una combinazione di occhi, input vocale e manuale.

### <a name="eye-supported-navigation"></a>[**Navigazione con supporto oculistico**](EyeTracking_Navigation.md)

Si supponga di leggere alcune informazioni su una visualizzazione distante o sull'e-Reader e quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per rivelare altro contenuto.
O come ingrandire lo zoom direttamente verso la posizione in cui si è cercato?
Di seguito sono riportati alcuni esempi illustrati in questa esercitazione sulla navigazione con supporto oculistico.
Inoltre, è disponibile un esempio per la rotazione senza mani di ologrammi 3D, facendo in modo che ruotino automaticamente in base allo stato attivo corrente.

**Riepilogo**: scorrimento, panoramica, zoom, rotazione 3D con una combinazione di occhi, input vocale e manuale.

### <a name="eye-supported-positioning"></a>[**Posizionamento con supporto per gli occhi**](EyeTracking_Positioning.md)

Questa esercitazione illustra uno scenario di input denominato [put-that-](https://youtu.be/CbIn8p4_4CQ) here risalendo alla ricerca dal MIT Media Lab nel primo 1980 con input Eye, hand e Voice.
L'idea è semplice: trarre vantaggio dagli occhi per la selezione e il posizionamento rapidi delle destinazioni.
Basta osservare un ologramma e pronunciare _"put this"_, esaminare il punto in cui si vuole posizionarlo e pronunciare _"There!"_.
Per posizionare con maggiore precisione l'ologramma, è possibile usare input aggiuntivi da Hands, Voice o Controllers.

**Riepilogo**: posizionamento degli ologrammi con gli occhi, input vocale e mano (*trascinamento della selezione*). Dispositivi di scorrimento supportati dagli occhi con occhi e mani.

### <a name="visualization-of-visual-attention"></a>**Visualizzazione dell'attenzione visiva**

I dati basati sul punto in cui gli utenti appaiono rendono uno strumento estremamente potente per valutare l'usabilità di una progettazione e identificare i problemi nei flussi di lavoro efficienti.
Questa esercitazione illustra diverse visualizzazioni di rilevamento degli occhi e il modo in cui si adattano a esigenze diverse.
Sono disponibili esempi di base per la registrazione e il caricamento di dati di rilevamento degli occhi ed esempi su come visualizzarli.

**Riepilogo**: mappa di attenzione bidimensionale (heatmaps) in slate. Registrazione & la riproduzione dei dati di rilevamento degli occhi.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configurazione degli esempi di rilevamento degli occhi di MRTK

### <a name="prerequisites"></a>Prerequisiti

Si noti che l'uso degli esempi di rilevamento degli occhi sul dispositivo richiede un HoloLens 2 e un pacchetto dell'app di esempio compilato con la funzionalità di "input dello sguardo" nel AppXManifest del pacchetto.

Per usare questi esempi di monitoraggio degli occhi nel dispositivo, assicurarsi di seguire [questi passaggi](EyeTracking_BasicSetup.md#testing-your-unity-app-on-a-hololens-2) prima di compilare l'app in Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. caricare EyeTrackingDemo-00-RootScene. Unity

*EyeTrackingDemo-00-RootScene* è la scena di base (_radice_) con tutti i componenti di MRTK principali inclusi.
Questa è la scena che è necessario caricare per prima e da cui verrà eseguita la demo di rilevamento degli occhi.
È disponibile un menu di scena grafica che consente di passare facilmente tra i diversi esempi di rilevamento degli occhi, che verranno caricati in modo [additivo](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).

![Menu scene nell'esempio di monitoraggio degli occhi](../images/eye-tracking/mrtk_et_scenemenu.jpg)

La scena radice include alcuni componenti di base che vengono mantenuti tra le scene caricate in modo additivo, ad esempio i profili configurati per MRTK e la fotocamera della scena.
Il _MixedRealityBasicSceneSetup_ (vedere la schermata riportata di seguito) include uno script che caricherà automaticamente la scena a cui si fa riferimento all'avvio.
Per impostazione predefinita, il valore è _EyeTrackingDemo-02-TargetSelection_.  

![Esempio per lo script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. aggiunta di scene al menu Compila

Per caricare le scene additive durante la fase di esecuzione, è necessario aggiungere prima di tutto le scene _nelle impostazioni di compilazione, > nel menu Compila_ .
È importante che la scena radice venga visualizzata come prima scena nell'elenco:

![Menu della scena delle impostazioni di compilazione per gli esempi di rilevamento degli occhi](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. riprodurre gli esempi di rilevamento degli occhi nell'editor di Unity

Dopo aver aggiunto le scene di rilevamento degli occhi alle impostazioni di compilazione e aver caricato _EyeTrackingDemo-00-RootScene_, è possibile verificare che sia lo script _' OnLoadStartScene '_ collegato al _MixedRealityBasicSceneSetup_ GameObject abilitato? In questo modo, la scena radice sa quale scena demo caricare per prima.

![Esempio per lo script OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Eseguiamo il roll Premere _"Play"_.
Verranno visualizzate diverse gemme e il menu della scena nella parte superiore.

![Schermata di esempio dalla scena Select di ET target](../images/eye-tracking/mrtk_et_targetselect.png)

Si noti anche un piccolo cerchio semitrasparente al centro della visualizzazione del gioco.
Questo funge da indicatore (cursore) dello _sguardo simulato_: è sufficiente premere il _pulsante destro del mouse_ e spostare il mouse per modificarne la posizione.
Quando si passa il cursore sulle gemme, si noterà che il cursore si blocca al centro della gemma attualmente visualizzata.
Questo è un ottimo modo per verificare se gli eventi vengono attivati come previsto quando si esegue la _ricerca_ in una destinazione.
Tenere presente che l' _occhio simulato_ tramite il controllo del mouse è un supplemento piuttosto scarso ai nostri movimenti oculari rapidi e non intenzionali.
Tuttavia, è ideale per testare la funzionalità di base prima di eseguire l'iterazione sulla progettazione distribuendo il dispositivo nel dispositivo HoloLens 2.
Tornando alla scena di esempio di analisi degli occhi: la gemma ruota fino a quando non viene analizzata e può essere distrutta "cercando" e...

- Premere _invio_ (che simula la dicitura "Select")
- Dicitura _"Seleziona"_ nel microfono
- Quando si preme _spazio_ per visualizzare l'input della mano simulata, fare clic con il pulsante sinistro del mouse per eseguire un pizzico simulato

Viene descritto in dettaglio come è possibile ottenere queste interazioni nell'esercitazione sulla [**selezione di destinazioni supportata dagli occhi**](EyeTracking_TargetSelection.md) .

Quando si sposta il cursore verso l'alto sulla barra dei menu superiore della scena, si noterà che l'elemento attualmente spostato viene evidenziato in modo impercettibile.
È possibile selezionare l'elemento attualmente evidenziato usando uno dei metodi di commit descritti sopra (ad esempio, premendo _invio_).
In questo modo è possibile passare tra le diverse scene di esempio di tracking degli occhi.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. come testare le sottoscene specifiche

Quando si lavora in uno scenario specifico, è possibile che non si desideri eseguire ogni volta il menu della scena.
In alternativa, è possibile iniziare direttamente dalla scena in cui si sta lavorando quando si preme il pulsante _Riproduci_ .
non è un problema. Ecco cosa è possibile fare:

1. Caricare la scena _radice_
2. Nella scena _radice_ disabilitare lo script _' OnLoadStartScene '_
3. _Trascinare e rilasciare_ una delle scene di test di rilevamento degli occhi descritte di seguito (o qualsiasi altra scena) nella visualizzazione _gerarchia_ , come illustrato nella schermata seguente.

    ![Esempio di scena additiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Premere _Play_

Si noti che il caricamento della scena secondaria come questa non è persistente: ciò significa che se si distribuisce l'app nel dispositivo HoloLens 2, viene caricata solo la scena radice (presupponendo che venga visualizzata nella parte superiore delle impostazioni di compilazione).
Inoltre, quando si condivide il progetto con altri utenti, le scene secondarie non vengono caricate automaticamente.

---

Ora che si è appreso come usare le scene di esempio di MRTK Eye Tracking, procedere con l'approfondimento su come selezionare gli ologrammi con gli occhi: [selezione della destinazione supportata dagli occhi](EyeTracking_TargetSelection.md).

---
[Torna a "Eye Tracking in the MixedRealityToolkit"](EyeTracking_Main.md)
