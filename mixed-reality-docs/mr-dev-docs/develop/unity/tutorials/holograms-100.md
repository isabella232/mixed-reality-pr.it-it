---
title: HoloLens (prima generazione) Nozioni di base 100 - Introduzione a Unity
description: Informazioni su come creare la prima applicazione "hello world" di realtà mista di base per HoloLens e Windows Mixed Reality dispositivi.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, Windows Mixed Reality, HoloLens, immersive, vr, mr, get started, ologram, academy, tutorial, Mixed Reality Academy, unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196507"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>HoloLens (prima generazione) Nozioni di base 100: Introduzione a Unity

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate con HoloLens (prima generazione), Unity 2017 e Visori immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni **_non verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

Questa esercitazione illustra come creare un'app di realtà mista di base compilata con Unity.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Nozioni di base MR 100: Introduzione a Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati.](../../install-the-tools.md)

## <a name="chapter-1---create-a-new-project"></a>Capitolo 1: Creare una nuova Project

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Per compilare un'app con Unity, è prima necessario creare un progetto. Questo progetto è organizzato in alcune cartelle, la più importante delle quali è la cartella Assets. Si tratta della cartella che contiene tutti gli asset importati dagli strumenti di creazione di contenuto digitale, ad esempio Maya, Max Cinema 4D o Photoshop, tutto il codice creato con Visual Studio o l'editor di codice preferito e qualsiasi numero di file di contenuto creati da Unity durante la composizione di scene, animazioni e altri tipi di asset Unity nell'editor.

Per compilare e distribuire app UWP, Unity può esportare il progetto come soluzione Visual Studio che conterrà tutti i file di asset e di codice necessari.

1. Avviare Unity
2. Selezionare **Nuovo**
3. Immettere un nome di progetto ,ad esempio "MixedRealityIntroduction"
4. Immettere un percorso per salvare il progetto
5. Assicurarsi che **l'interruttore 3D** sia selezionato
6. Selezionare **Crea progetto**

Congrats, è possibile iniziare subito a usare le personalizzazioni di realtà mista.

## <a name="chapter-2---setup-the-camera"></a>Capitolo 2 - Configurare la fotocamera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La fotocamera principale unity gestisce il rilevamento della testa e il rendering stereoscopico. Esistono alcune modifiche da apportare alla fotocamera principale per usarla con la realtà mista.

1. Selezionare File > nuova scena

In primo luogo, sarà più facile impostare il posizionamento dell'app se si immagina la posizione iniziale dell'utente come (**X**: 0, **Y**: 0, **Z**: 0). Poiché la fotocamera principale traccia lo spostamento della testa dell'utente, la posizione iniziale dell'utente può essere impostata impostando la posizione iniziale della fotocamera principale.

1. Selezionare **Fotocamera principale** nel pannello **Gerarchia**
2. Nel pannello **Inspector** (Controllo) trovare il componente **Transform** (Trasforma) e modificare **Position** **(Posizione)** da ( X : 0, **Y**: 1, **Z**: -10) in (**X**: 0, **Y**: 0, **Z**: 0)

In secondo piano, lo sfondo predefinito della fotocamera richiede un po' di riflessione.

**Per HoloLens applicazioni**, il mondo reale dovrebbe apparire dietro tutto ciò che la fotocamera esegue il rendering, non una trama Skybox.

1. Con la fotocamera **principale** ancora selezionata nel  pannello **Gerarchia,** trovare il componente Camera nel pannello **Inspector** (Controllo) e modificare l'elenco a discesa **Clear Flags** (Cancella flag) da **Skybox** a **Solid Color (Colore a tinta unita).**
2. Selezionare il **selettore** colore sfondo e impostare i **valori RGBA** su (0, 0, 0, 0, 0)

**Per le applicazioni di realtà mista** destinate a visori immersive, è possibile usare la trama Skybox predefinita fornita da Unity.

1. Con la fotocamera **principale** ancora selezionata nel  pannello **Gerarchia,** trovare il componente Camera nel pannello **Inspector** (Controllo) e mantenere **l'elenco** a discesa Clear Flags **(Cancella flag) su Skybox**.

In terzo piano, prendere in considerazione il piano di ritaglio vicino in Unity e impedire il rendering degli oggetti troppo vicini agli occhi degli utenti quando un utente si avvicina a un oggetto o un oggetto si avvicina a un utente.

**Per HoloLens applicazioni**, il piano di ritaglio vicino può essere impostato HoloLens 0,85 metri consigliati. [](../camera-in-unity.md#using-clipping-planes)

1. Con **la** fotocamera principale  ancora selezionata nel  pannello Gerarchia, trovare il componente Fotocamera nel pannello Inspector (Controllo) e modificare il campo Near **Clip Plane** (Vicino al piano di ritaglio) dal valore predefinito **0,3** HoloLens **0,85** consigliato. 

**Per le applicazioni di realtà mista destinate a visori immersive,** è possibile usare l'impostazione predefinita fornita da Unity.

1. Con la **fotocamera principale**  ancora selezionata nel  pannello Gerarchia, trovare il componente Fotocamera nel pannello Inspector (Controllo) e mantenere il campo Near **Clip Plane** (Vicino al piano di ritaglio) sul valore **predefinito 0,3**. 

Infine, è possibile salvare lo stato di avanzamento fino a questo momento. Per salvare le modifiche alla scena, selezionare **File > Salva scena con** nome, assegnare alla scena il nome **Main** e selezionare **Salva**.

## <a name="chapter-3---setup-the-project-settings"></a>Capitolo 3: Configurare il Project Impostazioni

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

In questo capitolo verranno impostate alcune impostazioni del progetto Unity che consentono di scegliere come destinazione Windows Holographic SDK per lo sviluppo. Verranno anche impostate alcune impostazioni di qualità per l'applicazione. Infine, si garantirà che le destinazioni di compilazione siano impostate su Universal Windows Platform.

### <a name="unity-performance-and-quality-settings"></a>Impostazioni relative a prestazioni e qualità di Unity

**Impostazioni di qualità unity per HoloLens**

![Impostazioni di qualità unity per HoloLens](images/qualitysettings.png)

Poiché mantenere un framerate elevato HoloLens è così importante, è necessario ottimizzare le impostazioni di qualità per ottimizzare le prestazioni. Per informazioni più dettagliate sulle prestazioni, vedere [Raccomandazioni sulle prestazioni per Unity.](../performance-recommendations-for-unity.md)

1. Selezionare **Modifica > Project Impostazioni > qualità**
2. Selezionare **l'elenco** a discesa sotto il logo **di Universal Windows Platform** e selezionare Very Low **(Molto basso).** Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Universal Windows Platform e la riga **Very Low** è verde.

Per le applicazioni di realtà mista destinate a schermi **occluded,** è possibile lasciare le impostazioni di qualità ai valori predefiniti.

### <a name="target-windows-10-sdk"></a>SDK Windows 10 destinazione

**Target Windows Holographic SDK**

![Target Windows Holographic SDK](../images/xrsettings.png)

È necessario invii a Unity che l'app che si sta tentando di esportare deve creare una visualizzazione [immersiva](../../../design/app-views.md) anziché una visualizzazione 2D. A tale scopo, viene abilitato il supporto della realtà virtuale in Unity che ha come destinazione Windows 10 SDK.

1. Passare a **Modifica > Project Impostazioni > Lettore**.
2. Nel pannello **Inspector (Controllo)** per Player Impostazioni selezionare l'icona **Universal Windows Platform (Piattaforma** Windows universali).
3. Espandere il gruppo **Impostazioni XR**.
4. Nella sezione **Rendering** selezionare la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere un nuovo elenco di **SDK per la realtà virtuale**.
5. Verificare che **Realtà mista di Windows** sia visualizzato nell'elenco. In caso contrario, selezionare il pulsante **+** nella parte inferiore dell'elenco e scegliere **Realtà mista di Windows**.

>[!NOTE]
>Se l'icona **Universal Windows Platform** non è visualizzata, verificare di aver selezionato Universal Windows Platform Build Support durante l'installazione. In caso contrario, potrebbe essere necessario reinstallare Unity con la corretta installazione di Windows.

Processo straordinario per ottenere tutte le impostazioni del progetto applicate. Aggiungere quindi un ologramma.

## <a name="chapter-4---create-a-cube"></a>Capitolo 4 - Creare un cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

La creazione di un cubo nel progetto Unity è come la creazione di qualsiasi altro oggetto in Unity. Posizionare un cubo davanti all'utente è facile perché il sistema di coordinate di Unity è mappato al mondo reale, dove un contatore in Unity è circa un metro nel mondo reale.

1. Nell'angolo superiore sinistro del pannello  **Gerarchia** selezionare l'elenco a discesa Crea e scegliere **Oggetto 3D > cubo**.
2. Selezionare il cubo **appena creato** nel pannello **Gerarchia**
3. In **Inspector trovare** il **componente Transform** (Trasforma) e modificare **Position (Posizione)** in (**X**: 0, **Y**: 0, **Z**: 2). *In questo modo il cubo viene posizionato 2 metri davanti alla posizione iniziale dell'utente.*
4. Nel  componente Trasforma  modificare Rotazione in (**X**: 45, **Y**: 45, **Z**: 45) e modificare **Scala** in (**X**: 0,25, **Y**: 0,25, **Z**: 0,25). *In questo modo il cubo viene ridimensionato a 0,25 metri.*
5. Per salvare le modifiche alla scena, selezionare **File > Salva scena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capitolo 5 - Verificare nel dispositivo dall'editor di Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Ora che è stato creato il cubo, è possibile eseguire un controllo rapido del dispositivo. È possibile eseguire questa operazione direttamente dall'editor di Unity.

### <a name="initial-setup"></a>Configurazione iniziale

1. Nel PC di sviluppo, in Unity, aprire **file > build Impostazioni** finestra.
2. Impostare **Piattaforma su** Universal Windows Platform **e** fare clic su Cambia **piattaforma**

### <a name="for-hololens-use-unity-remoting"></a>Ad HoloLens usare Unity Remoting

1. Nel HoloLens installare ed eseguire [Holographic Remoting Player,](../../platform-capabilities-and-apis/holographic-remoting-player.md)disponibile da Windows Store. Avviare l'applicazione nel dispositivo e immettere uno stato di attesa e visualizzare l'indirizzo IP del dispositivo. Annotare l'indirizzo IP.
2. Aprire **La finestra > XR > emulazione olografica.**
3. Modificare **la modalità di emulazione** da **Nessuna** a Remota **a Dispositivo**.
4. In **Computer remoto** immettere l'indirizzo IP del HoloLens specificato in precedenza.
5. Fare clic su **Connetti**.
6. Verificare che **stato della connessione cambi** in verde **Connesso.**
7. A questo punto è possibile fare **clic su Play** (Riproduci) nell'editor di Unity.

A questo punto sarà possibile visualizzare il cubo nel dispositivo e nell'editor. È possibile sospendere, esaminare gli oggetti ed eseguire il debug esattamente come si esegue un'app nell'editor, perché è essenzialmente ciò che accade, ma con l'input video, audio e dispositivo trasmesso in avanti e indietro attraverso la rete tra il computer host e il dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Per altri visori VR supportati per la realtà mista

1. Connessione il visore VR al PC di sviluppo usando il cavo USB e il cavo HDMI o della porta video.
2. Avviare il **Portale realtà mista** e assicurarsi di aver completato la prima esperienza di esecuzione.
3. Da Unity è ora possibile premere il pulsante Play (Riproduci).

Sarà ora possibile visualizzare il rendering del cubo nel visore VR di realtà mista e nell'editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capitolo 6: Compilare e distribuire nel dispositivo da Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

A questo punto è possibile compilare il progetto per Visual Studio e distribuirlo nel dispositivo di destinazione.

### <a name="export-to-the-visual-studio-solution"></a>Esportare nella soluzione Visual Studio

1. Aprire **la finestra > file Impostazioni** compilazione.
1. Fare **clic su Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena.
1. Impostare **Platform (Piattaforma)** **su Universal Windows Platform (Piattaforma universale)** e fare clic **su Switch Platform (Cambia piattaforma).**
1. Nelle **impostazioni della Windows universali** verificare che **l'SDK** **sia Universal 10.**
1. Per Dispositivo di destinazione lasciare **Qualsiasi dispositivo** per gli schermi occluded o passare **a HoloLens**.
1. **Il tipo di compilazione UWP** deve **essere D3D.**
1. **L'SDK UWP** potrebbe essere lasciato in **Latest installed (Versione più recente installata).**
1. Fare clic su **Compila**.
1. In Esplora file fare clic su **Nuova cartella e** assegnare alla cartella il nome **"App".**
1. Con la **cartella App** selezionata, fare clic sul **pulsante Seleziona** cartella.
1. Al termine della compilazione di Unity, verrà Windows Esplora file finestra di dialogo.
1. Aprire la **cartella App** in Esplora file.
1. Aprire la soluzione Visual Studio generata (MixedRealityIntroduction.sln in questo esempio)

### <a name="compile-the-visual-studio-solution"></a>Compilare la Visual Studio soluzione

Infine, si compilerà la soluzione Visual Studio, la si distribuirà e la si proverà nel dispositivo.

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da **Debug** a **Release** e da **ARM** a **X86.**

Le istruzioni sono diverse per la distribuzione in un dispositivo rispetto all'emulatore. Seguire le istruzioni corrispondenti alla configurazione.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Eseguire la distribuzione in un dispositivo di realtà mista Wi-Fi

1. Fare clic sulla freccia accanto al **pulsante Computer** locale e modificare la destinazione della distribuzione in **Computer remoto**.
2. Immettere l'indirizzo IP del dispositivo  di realtà mista e impostare Modalità di autenticazione su Universale (protocollo non crittografato) per HoloLens e **Windows** per altri dispositivi.
3. Fare clic **su Debug > Avvia senza eseguire debug.**

**Per HoloLens**, se è la prima volta che si esegue la distribuzione nel dispositivo, è necessario eseguire l'associazione [usando Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Eseguire la distribuzione in un dispositivo di realtà mista tramite USB

Assicurarsi che il dispositivo sia collegato tramite il cavo USB.

1. **Per HoloLens**, fare clic sulla freccia accanto al pulsante **Computer** locale e modificare la destinazione della distribuzione in **Dispositivo**.
2. **Per impostare come destinazione i dispositivi occlud collegati al PC,** mantenere l'impostazione Computer locale. Assicurarsi che **l'Portale realtà mista** in esecuzione.
3. Fare clic **su Debug > Avvia senza eseguire debug.**

### <a name="deploy-to-emulator"></a>Distribuire in Emulator

1. Fare clic sulla freccia accanto al **pulsante Dispositivo** e nell'elenco a discesa **selezionare HoloLens Emulator**.
2. Fare clic **su Debug > Avvia senza eseguire debug.**

### <a name="try-out-your-app"></a>Provare l'app

Ora che l'app è stata distribuita, provare a spostarsi all'esterno del cubo e osservare che rimane nel mondo davanti all'utente.

## <a name="see-also"></a>Vedi anche

* [Panoramica dello sviluppo per Unity](../unity-development-overview.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](../best-practices-for-working-with-unity-and-visual-studio.md)
* [Nozioni di base MR 101](holograms-101.md)
* [Nozioni di base MR 101E](holograms-101e.md)