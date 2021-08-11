---
title: Modello applicazioni
description: Windows Mixed Reality usa il modello di app fornito da Universal Windows Platform, un modello e un ambiente per le app Windows moderne.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modello di app, ciclo di vita, sospensione, ripresa, riquadro, visualizzazioni, contratti, visore per la realtà mista, visore windows di realtà mista, visore di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 5f15f0a2516a21cd6432e7f09df7950f8d832acc77ac77056f5bf1382500024e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221937"
---
# <a name="app-model"></a>Modello applicazioni

Windows Mixed Reality usa il modello di app fornito dalla [piattaforma UWP (Universal Windows Platform),](/windows/uwp/get-started/) che è un modello e un ambiente per le app Windows moderne. Il modello di app UWP definisce il modo in cui le app vengono installate, aggiornate, con controllo delle versioni e rimosse completamente. Determina anche il ciclo di vita dell'applicazione, come le app vengono eseguite, sos sospensione e arresto, e come possono mantenere lo stato. Infine, il modello di app illustra l'integrazione e l'interazione con il sistema operativo, i file e altre app.

![App 2D disposte nella Windows Mixed Reality in una zona per la prima colazione](images/20160112-055908-hololens-500px.jpg)<br>
*App con una visualizzazione 2D disposta nella Windows Mixed Reality home*

## <a name="app-lifecycle"></a>Ciclo di vita dell'app

Il ciclo di vita di un'app di realtà mista prevede concetti di app standard, ad esempio posizionamento, avvio, terminazione e rimozione.

### <a name="placement-is-launch"></a>Il posizionamento è in avvio

Ogni app inizia in realtà mista inserendo un riquadro dell'app (solo un Windows [secondario)](/uwp/api/Windows.UI.StartScreen.SecondaryTile)nella Windows Mixed Reality [home](../discover/navigating-the-windows-mixed-reality-home.md). Questi riquadri dell'app, nel posizionamento, inizieranno a eseguire l'app. Questi riquadri dell'app vengono mantenuti e rimangono nella posizione in cui si trova, fungendo da utilità di avvio per qualsiasi momento in cui si vuole tornare all'app.

![Il posizionamento inserisce un riquadro secondario nel mondo](images/slide1-600px.png)<br>
*Il posizionamento inserisce un riquadro secondario nel mondo*

Non appena il posizionamento viene completato (a meno che il posizionamento non sia stato avviato da un'app per l'avvio [dell'app),](app-model.md#protocols) l'app viene avviata. Windows Mixed Reality possibile eseguire un numero limitato di app contemporaneamente. Non appena si posiziona e si avvia un'app, altre app attive potrebbero essere sospese. Le app sospese lasciano uno screenshot dell'ultimo stato dell'app nel riquadro dell'app in qualsiasi posizione. Per altre informazioni sulla gestione del curriculum e di altri eventi del ciclo di vita, Windows 10 ciclo [di vita dell'app UWP.](/windows/uwp/launch-resume/app-lifecycle)

![Dopo aver posizionato un riquadro, l'app avvia l'esecuzione del diagramma di stato per ](images/slide2-500px.png) ![ l'app in esecuzione, sospesa o non in esecuzione](images/ic576232-500px.png)<br>
*A sinistra: dopo aver posizionato un riquadro, viene avviata l'esecuzione dell'app. Destra: diagramma di stato per l'app in esecuzione, sospesa o non in esecuzione.*

### <a name="remove-is-closeterminate-process"></a>Remove è un processo di chiusura/terminazione

Quando si rimuove un riquadro dell'app posizionato dal mondo, i processi sottostanti si chiudono. Ciò può essere utile per assicurarsi che l'app venga arrestata o riavviata da un'app problematica.

### <a name="app-suspensiontermination"></a>Sospensione/terminazione dell'app

Nella home [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)l'utente può creare più punti di ingresso per un'app avviando l'app dal menu Start e inserendo il riquadro dell'app nel mondo. Ogni riquadro dell'app si comporta come un punto di ingresso diverso e ha un'istanza del riquadro separata nel sistema. Una query per [SecondaryTile.FindAllAsync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) comporterà **un secondarytile** per ogni istanza dell'app.

Quando un'app UWP viene sospesa, viene eseguita una schermata dello stato corrente.

![Screenshot visualizzati per le app sospese](images/slide9-800px.png)<br>
*Screenshot visualizzati per le app sospese*

Una differenza chiave rispetto ad altre shell Windows 10 è il modo in cui l'app viene informata dell'attivazione di un'istanza dell'app tramite gli [eventi CoreApplication.Resuming](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) e [CoreWindow.Activated.](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)

|  Scenario |  Resuming  |  Attivato | 
|----------|----------|----------|
|  Avviare una nuova istanza dell'app dal menu Start  |   |  **Attivato** con un nuovo [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Avviare la seconda istanza dell'app dal menu Start  |   |  **Attivato** con un nuovo **TileId** | 
|  Selezionare l'istanza dell'app che non è attualmente attiva  |   |  **Attivato** con **tileId associato** all'istanza | 
|  Selezionare un'app diversa, quindi selezionare l'istanza attiva in precedenza  |  **Ripresa dell'evento** generato  |  | 
|  Selezionare un'app diversa, quindi selezionare l'istanza precedentemente inattiva  |  **Ripresa dell'evento** generato  |  Attivato **con** **tileId associato** all'istanza | 

### <a name="extended-execution"></a>Esecuzione estesa

A volte l'app deve continuare a lavorare in background o riprodurre l'audio. [Le attività in](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) background sono disponibili HoloLens.

![Le app possono essere eseguite in background](images/slide10-800px.png)<br>
*Le app possono essere eseguite in background*

## <a name="app-views"></a>Visualizzazioni delle app

Quando l'app viene attivata, è possibile scegliere il tipo di visualizzazione da visualizzare. Per **CoreApplication** di un'app, è sempre presente una visualizzazione [dell'app](/uwp/api/Windows.UI.ViewManagement.ApplicationView) primaria e un numero qualsiasi di altre visualizzazioni dell'app che si vuole creare. Sul desktop è possibile pensare a una visualizzazione dell'app come a una finestra. I modelli di app di realtà mista creano un progetto Unity in cui la visualizzazione dell'app primaria è [immersiva.](app-views.md) 

L'app può creare una visualizzazione di app 2D aggiuntiva usando una tecnologia come XAML per usare Windows 10 funzionalità quali l'acquisto in-app. Se l'app è stata avviata come app UWP per altri Windows 10, la visualizzazione primaria è 2D. Tuttavia, è possibile "illuminarsi" in realtà mista aggiungendo un'altra visualizzazione dell'app immersiva per mostrare un'esperienza volumetricamente. Imagine un'app visualizzatore di foto in XAML in cui il pulsante della presentazione è passata a una visualizzazione dell'app immersiva che ha portato le foto dall'app in tutto il mondo e le superfici.

![L'app in esecuzione può avere una visualizzazione 2D o una visualizzazione immersiva](images/slide3-800px.png)<br>
*L'app in esecuzione può avere una visualizzazione 2D o una visualizzazione immersiva*

### <a name="creating-an-immersive-view"></a>Creazione di una visualizzazione immersiva

Le app di realtà mista creano una visualizzazione immersiva, ottenuta con il [tipo HolographicSpace.](/uwp/api/windows.graphics.holographic.holographicspace)

Un'app puramente immersiva deve sempre creare una visualizzazione immersiva all'avvio, anche se avviata dal desktop. Le visualizzazioni immersive vengono sempre mostrate nel visore, indipendentemente dalla posizione da cui sono state create. L'attivazione di una visualizzazione immersiva visualizza il Portale realtà mista e guida l'utente a mettere il visore.

Un'app che inizia con una visualizzazione 2D sul monitor desktop può creare una visualizzazione immersiva secondaria per visualizzare il contenuto nel visore. Un esempio è una finestra 2D Edge sul monitor che visualizza un video a 360 gradi nel visore.

![Le app in esecuzione nella visualizzazione immersiva sono le uniche visibili](images/slide4-800px.png)<br>
*Un'app in esecuzione in una visualizzazione immersiva è l'unica visibile*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Visualizzazione 2D nella home page Windows Mixed Reality 2D

Qualsiasi elemento diverso da una visualizzazione immersiva viene visualizzato come visualizzazione 2D nel mondo.

Un'app può avere visualizzazioni 2D sia sul monitor desktop che sul visore. Una nuova visualizzazione 2D verrà posizionata nella stessa shell della vista che la ha creata, sul monitor o nel visore. Attualmente non è possibile per un'app o un utente spostare una visualizzazione 2D tra la home page di Realtà mista e il monitoraggio.

![Le app in esecuzione nella visualizzazione 2D condividono lo spazio nel mondo misto con altre app](images/slide5-800px.png)<br>
*Le app in esecuzione in una visualizzazione 2D condividono lo spazio con altre app*

### <a name="placement-of-additional-app-tiles"></a>Posizionamento di riquadri aggiuntivi dell'app

È possibile inserire tutte le app con una visualizzazione 2D nel mondo desiderato con le [API riquadro secondario](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Questi riquadri "aggiunti" verranno visualizzati come schermate iniziali che gli utenti devono inserire e quindi potranno usare in un secondo momento per avviare l'app. Windows Mixed Reality attualmente non supporta il rendering del contenuto del riquadro 2D come riquadri animati.

![Le app possono avere più posizionamenti usando riquadri secondari](images/slide6-800px.png)<br>
*Le app possono avere più posizionamenti usando riquadri secondari*

### <a name="switching-views"></a>Passaggio da una visualizzazione all'altra

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Passaggio dalla visualizzazione XAML 2D alla visualizzazione immersiva

Se l'app usa XAML, [L'oggetto IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) XAML controlla la prima visualizzazione dell'app. L'app dovrà passare alla visualizzazione immersiva prima di attivare **CoreWindow** per assicurarsi che l'app venga avviata direttamente nell'esperienza immersiva.

Usare [CoreApplication.CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) e [ApplicationViewSwitcher.SwitchAsync](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) per renderla la visualizzazione attiva.

> [!NOTE]
>* Non specificare il flag [ApplicationViewSwitchingOptions.ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) su **SwitchAsync** quando si passa dalla visualizzazione XAML alla visualizzazione immersiva oppure lo slate che ha avviato l'app verrà rimosso dal mondo.
>* **È necessario** chiamare SwitchAsync usando [il Dispatcher](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) associato alla visualizzazione a cui si sta passando.
>* È necessario tornare **alla** visualizzazione XAML se è necessario avviare una tastiera virtuale o attivare un'altra app.

![Le app possono passare da visualizzazioni 2D a visualizzazioni immersive Quando un'app passa a una visualizzazione immersiva, il mondo misto e ](images/slide7-600px.png) ![ altre app scompaiono](images/slide8-600px.png)<br>
*A sinistra: le app possono passare dalla visualizzazione 2D alla visualizzazione immersiva. A destra: quando un'app entra in una visualizzazione immersiva, la Windows Mixed Reality e altre app scompaiono.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Passaggio dalla visualizzazione immersiva a una visualizzazione XAML da tastiera

Un motivo comune per passare da una visualizzazione all'altra è la visualizzazione di una tastiera in un'app di realtà mista. La shell è in grado di visualizzare la tastiera di sistema solo se l'app visualizza una visualizzazione 2D. Se l'app deve ottenere l'input di testo, può fornire una visualizzazione XAML personalizzata con un campo di input di testo, passare a esso e quindi tornare indietro al termine dell'input.

Come nella sezione precedente, è possibile usare **ApplicationViewSwitcher.SwitchAsync** per tornare a una visualizzazione XAML dalla visualizzazione immersiva.

## <a name="app-size"></a>Dimensioni dell'app

Le visualizzazioni delle app 2D vengono sempre visualizzate in uno slate virtuale fisso. In questo modo tutte le visualizzazioni 2D mostrano esattamente la stessa quantità di contenuto. Di seguito sono riportati altri dettagli sulle dimensioni della visualizzazione 2D dell'app:
* Le proporzioni dell'app vengono mantenute durante il ridimensionamento.
* La [risoluzione dell'app e il fattore](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) di scala non vengono modificati ridimensionando.
* Le app non sono in grado di eseguire query sulle dimensioni effettive nel mondo.

![Le app 2D vengono visualizzate con dimensioni fisse delle finestre](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Le app con una visualizzazione 2D vengono visualizzate con dimensioni fisse delle finestre*

## <a name="app-tiles"></a>Riquadri dell'app

Il menu Start usa il riquadro di piccole dimensioni standard e il riquadro medio per i segnaposto e **l'elenco Tutte le** app in realtà mista. 

![Il menu Start per Windows Mixed Reality](images/start-500px.png)<br>
*Il menu Start per Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Interazioni da app a app

Quando si compilano app, si ha accesso all'app ricca per i meccanismi di comunicazione delle app disponibili in Windows 10. Molte delle nuove API del protocollo e delle registrazioni di file funzionano perfettamente HoloLens per consentire l'avvio e la comunicazione dell'app. 

Per i visori per desktop, l'app associata a una determinata estensione di file o protocollo può essere un'app Win32 che può essere visualizzata solo nel monitor desktop o nello slate del desktop.

### <a name="protocols"></a>Protocolli

HoloLens supporta l'avvio dell'app tramiteWindows.Sys[tem. API dell'utilità di avvio](/uwp/api/Windows.System.Launcher).

Quando si avvia un'altra applicazione, è necessario considerare alcuni aspetti:

* Quando si esegue un avvio non modale, ad esempio [LaunchUriAsync,](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)l'utente deve posizionare l'app prima di interagire con essa.

* Quando si esegue un avvio modale, ad esempio tramite [LaunchUriForResultsAsync,](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)l'app modale viene posizionata nella parte superiore della finestra.

* Windows Mixed Reality possibile sovrapporre le applicazioni alle visualizzazioni esclusive. Per visualizzare l'app avviata, Windows l'utente torna al mondo per visualizzare l'applicazione.

### <a name="file-pickers"></a>Selettori file

HoloLens supporta entrambi [i contratti FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) e [FileSavePicker.](/uwp/api/Windows.Storage.Pickers.FileSavePicker) Tuttavia, nessuna app viene preinstallato che soddisfa i contratti di selezione file. Queste app, OneDrive, ad esempio, possono essere installate dal Microsoft Store.

Se sono installate più app di selezione file, non verrà visualizzata alcuna interfaccia utente disambiguation per la scelta dell'app da avviare. Verrà invece scelta la prima selezione file installata. Quando si salva un file, viene generato il nome file che include il timestamp. Non può essere modificato dall'utente.

Per impostazione predefinita, le estensioni seguenti sono supportate in locale:

|  App  |  Estensioni | 
|----------|----------|
|  Foto  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Contratti di app ed estensioni Windows Mixed Reality app

I contratti di app e i punti di estensione consentono di registrare l'app per sfruttare funzionalità del sistema operativo più approfondite, ad esempio la gestione di un'estensione di file o l'uso di attività in background. Questo è un elenco dei contratti e dei punti di estensione supportati e non supportati HoloLens.

|  Contratto o estensione  |  Supportata | 
|----------|----------|
| [Provider di immagini account (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | Non supportato | 
| [Allarme](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | Non supportato | 
| [Servizio app](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | Supportato ma non completamente funzionante | 
| [Provider di appuntamenti](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | Non supportato | 
| [AutoPlay (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | Non supportato | 
| [Attività in background (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | Parzialmente supportato (non tutti i trigger funzionano) | 
| [Attività di aggiornamento (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | Supportato | 
| [Contratto di aggiornamento file memorizzato nella cache](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | Supportato | 
| [Impostazioni fotocamera (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | Non supportato | 
| [Dial protocol](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | Non supportato | 
| [Attivazione file (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | Supportato | 
| [contratto Selezione apertura file](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | Supportato | 
| [contratto Selezione salvataggio file](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | Supportato | 
| [Chiamata alla schermata di blocco](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | Non supportato | 
| [Riproduzione multimediale](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | Non supportato | 
| [Contratto Play To](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | Non supportato | 
| [Attività di configurazione preinstallata](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | Non supportato | 
| [Stampa 3D flusso di lavoro](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | Supportato | 
| [Impostazioni attività di stampa (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | Non supportato | 
| [Attivazione URI (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | Supportato | 
| [Avvio con restrizioni](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | Non supportato | 
| [Contratto di ricerca](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | Non supportato | 
| [Impostazioni contratto](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | Non supportato | 
| [Condividere il contratto](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | Non supportato | 
| [SSL/certificates (estensione)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | Supportato | 
| [Provider di account Web](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | Supportato | 

## <a name="app-file-storage"></a>Archiviazione file dell'app

Tutte le risorse di archiviazione vengono [Windows.Archiviazione spazio dei nomi](/uwp/api/Windows.Storage). HoloLens non supporta la sincronizzazione/roaming dell'archiviazione delle app. Per altre informazioni, vedere la documentazione seguente:

* [File, cartelle e raccolte](/windows/uwp/files/index)
* [Archiviare e recuperare le impostazioni e altri dati dell'app](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Cartelle note

Per informazioni dettagliate complete sulle app UWP, vedere [KnownFolders.](/uwp/api/Windows.Storage.KnownFolders)

<table>
<tr>
<th> Proprietà</th><th> Supportato in HoloLens</th><th> Supportato in visori immersivi</th><th> Descrizione</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella App Captures.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella Rullino.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta Documenti. La raccolta Documenti non è destinata all'uso generale.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la Musica di dati.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Oggetti3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella Objects 3D.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la raccolta Immagini.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Playlist</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella degli elenchi di riproduzione.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la cartella Immagini salvate.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ottiene la libreria Video.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Gruppo Home</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella HomeGroup.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella dei dispositivi DLNA (Digital Living Network Alliance) del server multimediale.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella delle chiamate registrate.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ottiene la cartella dei dispositivi rimovibili.</td>
</tr>
</table>

## <a name="app-package"></a>Pacchetto dell'app

Con Windows 10, non si ha più come destinazione un sistema operativo, ma l'app viene invece impostata come destinazione [per una o più famiglie di dispositivi.](/windows/uwp/get-started/universal-application-platform-guide#device-families) Una famiglia di dispositivi identifica le API, le caratteristiche del sistema e i comportamenti che ti aspetti dai dispositivi che appartengono a quella famiglia di dispositivi. Determina anche il set di dispositivi in cui l'app può essere installata [dal](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)Microsoft Store .

* Per scegliere come destinazione sia i visori desktop che HoloLens, impostare come destinazione l'app **Windows. Famiglia di** dispositivi universali.
* Per impostare come destinazione solo i visori desktop, impostare come destinazione l'app **Windows. Famiglia** di dispositivi desktop.
* Per impostare come destinazione HoloLens, impostare come destinazione l'app **Windows. Famiglia di dispositivi olografici.**

## <a name="see-also"></a>Vedi anche

* [Visualizzazioni delle app](app-views.md)
* [Aggiornamento di app UWP 2D per la realtà mista](../develop/porting-apps/building-2d-apps.md)
* [Linee guida per la progettazione di utilità di avvio di app 3D](../distribute/3d-app-launcher-design-guidance.md)
* [Implementazione di launcher di app 3D](../distribute/implementing-3d-app-launchers.md)