---
title: Funzionalità supportate per il plug-in OpenXR in Unity
description: Scopri le funzionalità supportate da OpenXR per lo sviluppo di realtà miste in Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: 1c9e185c63d3efef66cdc2782d8d8d4e3692c705
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623631"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Realtà mista OpenXR le funzionalità supportate in Unity

Il pacchetto di plug-in OpenXR per la **realtà mista** è un'estensione del plug-in **OpenXR** di Unity e supporta una suite di funzionalità per gli auricolari per la realtà mista HoloLens 2 e Windows. Prima di continuare, assicurarsi di avere installato **unity 2020,2** o versione successiva, la versione del plug-in **OpenXR 0.1.3 o versione** successiva e che il progetto Unity sia [configurato per OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>Attività supportate

Attualmente sono supportate le funzionalità seguenti:

* Supporta le applicazioni UWP per HoloLens 2 e l'ottimizzazione per il modello di applicazione HoloLens 2.
* Supporta le applicazioni Win32 VR per l'auricolare di realtà mista Windows con i profili controller più recenti e la comunicazione remota delle app olografiche
* Rilevamento della scalabilità globale tramite ancoraggi e spazio non vincolato.
* [API di archiviazione di ancoraggio per salvare](spatial-anchors-in-unity.md) in modo permanente gli ancoraggi nell'archivio locale HoloLens 2.
* [Motion controller e Hand Interactions](#motion-controller-and-hand-interactions), incluso il nuovo controller HP Reverb G2.
* Tracciatura manuale articolata con 26 giunzioni e input RADIUS Uniti.
* Interazione con gli occhi su HoloLens 2.
* Individuazione della fotocamera Photo/video (PV) in HoloLens 2.
* Acquisizione di realtà mista tramite il rendering di 3 occhi attraverso la fotocamera FV.
* Supporta ["Play" in HoloLens 2 con l'app di comunicazione remota olografica](#holographic-remoting-in-unity-editor-play-mode), consentendo agli sviluppatori di eseguire il debug degli script senza compilare e distribuire nel dispositivo.
* Compatibile con MRTK Unity 2.5.3 e versioni successive tramite il [supporto del provider OpenXR MRTK](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatibile con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o versione successiva.
* (Aggiunto in 0.1.3) Supporta la [comunicazione remota olografica dell'app desktop](holographic-remoting-desktop.md) da un'app autonoma Windows compilata e distribuita.
* (Aggiunto in 0.1.4) Supporta il [rilevamento del codice](#qr-codes) a matrice in HoloLens2 tramite SpatialGraphNode

## <a name="holographic-remoting-setup"></a>Configurazione della comunicazione remota olografica

1. Per prima cosa, è necessario [installare l'app del lettore di comunicazione remota olografica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2
2. Eseguire l'app del lettore di comunicazione remota olografica in HoloLens 2 per visualizzare il numero di versione e l'indirizzo IP per la connessione
    * Per usare il plug-in OpenXR, è necessario usare la versione 2.4 o successiva.

    ![Screenshot del lettore di comunicazione remota olografico in esecuzione in HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Comunicazione remota olografica in modalità di riproduzione dell'editor Unity

La creazione di un progetto Unity UWP nel progetto di Visual Studio e quindi la creazione del pacchetto e la distribuzione in un dispositivo HoloLens 2 possono richiedere del tempo. Una soluzione consiste nell'abilitare la funzionalità di comunicazione remota dell'editor olografica, che consente di eseguire il debug dello script C# usando la modalità "Play" direttamente in un dispositivo HoloLens 2 sulla rete. Questo scenario consente di evitare il sovraccarico dovuto alla creazione e alla distribuzione di un pacchetto UWP nel dispositivo remoto.

1. Seguire i passaggi dell' [installazione di comunicazione remota olografica](#holographic-remoting-setup)
2. Aprire la finestra di dialogo **modifica-> impostazioni progetto**, passare alla **Gestione plug-in XR** e selezionare la casella **set di funzionalità di realtà mista di Windows** :

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-features-img-02.png)

3. Espandere la sezione **funzionalità** in **OpenXR** e selezionare **Mostra tutto**
4. Controllare la casella di controllo **Remote editor olografico** e immettere l'indirizzo IP ottenuto dall'app di comunicazione remota olografica:

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con le funzionalità evidenziate](images/openxr-features-img-03.png)

A questo punto è possibile fare clic sul pulsante "Riproduci" per riprodurre l'app Unity nell'app per la comunicazione remota olografica nella HoloLens. È anche possibile [aggiungere Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) per eseguire il debug degli script C# in modalità Play.

> [!NOTE]
> A partire dalla versione 0.1.0, il runtime di comunicazione remota olografica non supporta ancoraggi e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.  Questa funzionalità è disponibile nelle versioni future.

## <a name="motion-controller-and-hand-interactions"></a>Interazioni tra controller di movimento e mano

Per apprendere le nozioni di base sulle interazioni tra realtà mista in Unity, vedere il [Manuale di Unity per Unity XR input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Questa documentazione di Unity riguarda i mapping da input specifici del controller a **InputFeatureUsage** più generalizzabili, il modo in cui possono essere identificati e categorizzati gli input XR disponibili, come leggere i dati da questi input e altro ancora.

Il plug-in OpenXR per la realtà mista fornisce profili di interazione di input aggiuntivi, mappati a **InputFeatureUsage** standard, come descritto di seguito:

| InputFeatureUsage | Controller HP Reverb G2 (OpenXR) | Mano HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Joystick-fare clic | |
| trigger | Trigger  | |
| ridimensionamento | Ridimensionamento | Toccare o fare pressione |
| primaryButton | [X/A]-premere | Simulazione del tocco |
| secondaryButton | [S/B]-premere | |
| gripButton | Pressione del pulsante | |
| triggerButton | Trigger-premere | |
| menuButton | Menu | |

### <a name="aim-and-grip-poses"></a>Pose AIM e grip

È possibile accedere a due set di pose tramite interazioni di input OpenXR:

* Il grip si pone per il rendering degli oggetti a mano
* L'obiettivo si pone per puntare al mondo.

Altre informazioni su questa progettazione e sulle differenze tra le due pose sono reperibili nella [specifica OpenXR-sottopercorsi di input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Le pose fornite da InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** rappresentano tutti la postura del **grip** OpenXR. InputFeatureUsages correlate alle pose del grip sono definite in [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)di Unity.

Le pose fornite da InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** rappresentano tutti il OpenXR **AIM** pose. Questi InputFeatureUsages non sono definiti in alcun file C# incluso, quindi è necessario definire il proprio InputFeatureUsages come indicato di seguito:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

Per informazioni sull'uso di haptics nel sistema di input XR di Unity, è possibile trovare la documentazione nel [Manuale di Unity per Unity XR input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>Codici QR

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice. Per ulteriori informazioni, vedere la documentazione relativa al [rilevamento del codice](../platform-capabilities-and-apis/qr-code-tracking.md) a matrice.  Quando si usa il plug-in OpenXR, estrarre l' [ `SpatialGraphNodeId` dall'API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e usare l' `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API per individuare il codice a matrice.

Per riferimento, abbiamo un progetto di esempio di rilevamento a matrice [su GitHub](https://github.com/yl-msft/QRTracking) con una spiegazione dettagliata dell'utilizzo dell' [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="whats-coming-soon"></a>Presto disponibile

I problemi e le funzionalità mancanti seguenti sono noti con la versione del plug-in OpenXR della realtà mista **0.1.0**. Stiamo lavorando a questi e verranno rilasciate correzioni e nuove funzionalità nelle prossime versioni.

* **ARPlaneSubsystem** non è ancora supportato. Le API **ARPlaneManager**, **ARRaycastManager** e related, ad esempio **ARAnchorManager. AttachAnchor** , non sono supportate in HoloLens 2.
* La **persistenza di ancoraggio** non è ancora supportata dalla comunicazione remota olografica, ma sarà disponibile a breve.
* Il rilevamento della **mesh della mano** e **XRMeshSubsystem** non sono ancora supportati.
* Il supporto di **ancoraggi spaziali di Azure** è disponibile in una versione futura.
* **Arm64** è l'unica piattaforma supportata per le app HoloLens 2. La piattaforma **ARM** sarà disponibile in una versione futura.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Quando si sospende e si riprende un'app Unity in HoloLens 2, l'app non può essere ripresa correttamente, il che comporta 4 puntini di rotazione nella visualizzazione HoloLens.

* Impostare la **modalità di invio di profondità** su **None** nelle impostazioni del progetto OpenXR come soluzione alternativa
